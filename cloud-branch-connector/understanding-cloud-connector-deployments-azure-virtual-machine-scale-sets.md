# Understanding Cloud Connector Deployments with Azure Virtual Machine Scale Sets
Source: https://help.zscaler.com/cloud-branch-connector/understanding-cloud-connector-deployments-azure-virtual-machine-scale-sets
PDF: https://help.zscaler.com/pdf/com/en/1528441.pdf

An Azure Virtual Machine Scale Sets (VMSS) deployment dynamically adds Cloud Connector virtual machines (VMs) to a scale set to meet the current load when it increases, and it removes Cloud Connector VMs from the scale set when the load decreases. For example, consider an Azure Virtual Desktop deployment, where users log in to their own virtual workstations at the beginning of the work day and log out at the end of the day. This causes fluctuations in the number of users and the amount of traffic flow during these periods.
VMSS also constantly monitors the health of each VM in the scale set. It removes unhealthy VMs from the scale set and replaces them with healthy ones. If someone manually terminates a VM that is part of a scale set from the Azure Console, the VMSS likewise replaces the VM.
Stopping or rebooting a VM that is part of a scale set from the Azure Portal could cause the VM to be terminated.
VMSS provides the following benefits:
- Dynamically scales the number of VMs in the scale set to match demand.
- Automatically removes unhealthy VMs and replaces them with healthy ones.
- Deploys VMs across availability zones for high availability. The Internal Load Balancer (ILB) distributes traffic among the VMs.
This article describes VMSS and how it works in a Cloud Connector deployment. The deployment template prompts you to configure certain VMSS settings mentioned in this article. For information about the deployment template and the deployment steps, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#azure-terraform) and [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure). For comprehensive VMSS information, refer to the [Azure product documentation](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/).
Topology
The following sections provide a diagram depicting the topology of a VMSS deployment and a description of its components and flow.
- [Topology diagram](#topologydiagram)
- [Topology details](#topologydetails)
[]![Diagram showing a Cloud Connector Virtual Machine Scale Sets (VMSS) deployment in Azure](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/diagram_cloud-conn_azure_vmss.png)
- []The security stack is deployed into its own Security Resource Group to simplify the management of resources. Zscaler recommends that you deploy the security stack into its own Security VNet and that you peer Workload VNets with it. After the security stack is deployed, route tables in the Workload VNets should have a user-defined route steering traffic to the ILB in front of the Cloud Connectors.
- An Internal Load Balancer (ILB) is deployed in front of the Cloud Connectors and is the entry point for the security stack.
- A VMSS is created in each configured zone to provide high availability across zones.
- A NAT Gateway (NATGW) used for outbound traffic from the Cloud Connectors is deployed in each configured zone and has a dedicated IP address associated with it.
-
There are two Azure functions:
- **Health Monitoring**: Uses the custom metrics published by each Cloud Connector to determine whether there are any unhealthy Cloud Connectors that need to be replaced. The function terminates an unhealthy instance and immediately replaces it with a new one. This function runs at one-minute intervals.
- **Resource Sync**: Ensures that the VMs in a Cloud Connector Group on the Cloud & Branch Connector Admin Portal match the VMs in your VMSS. If the function finds a Cloud Connector in the Cloud Connector Group that is not in the VMSS, it cleans up that instance in the Cloud Connector Group to ensure that the two entities are in sync. This function runs at 30-minute intervals.
The Azure Functions communicate with the Cloud Connector API server via REST APIs. Azure Functions do not communicate directly with Cloud Connectors.
The Azure Function app contains Azure Functions and runs a ZIP file to start them. It finds the ZIP file in a new storage account that is created at runtime or from an existing storage account that you specify during deployment.
Scale-Out and Scale-In
Each Cloud Connector independently reports custom CPU utilization metrics to the Azure Monitor Service at one-minute intervals to advertise the load it is handling. VMSS uses the aggregate CPU utilization of all VMs in the scale set to determine when to trigger scale-out and scale-in events and how aggressively to do so.
Custom CPU metrics provide more detailed information about CPU usage, so Cloud Connector publishes them instead of VM-level metrics.
- [Scaling Rules](#scalingrules)
- [Scheduled Scaling](#scheduledscaling)
[]Scaling rules define the parameters for triggering scale-out and scale-in events. Zscaler recommends the following default thresholds and values:
| Parameter | Description | Scale-Out Rule | Scale-In Rule |
| --------- | ----------- | -------------- | ------------- |
| CPU utilization threshold | The aggregate percentage of CPU utilization for the VMs in the scale set. | 70% | 50% |
| Duration | The number of consecutive minutes after the threshold is crossed before a scale-out or scale-in event is triggered. | 10 | 10 |
| Cooldown | The number of minutes to wait before triggering another scale-out or scale-in event. Metrics continue to be monitored and reported during the cooldown period. This gives the VMSS time to stabilize and determine how the updated number of VMs impacts the CPU utilization. | 15 | 15 |
| Instance count | The number of VMs to remove or add for a single scale-out or scale-in event. | 1 | 1 |
Examples:
- There are 4 VMs in a scale set. The VMs report CPU utilization of 80%, 60%, 75%, and 90%, so the aggregated CPU utilization for the scale set is 79.5%. The CPU utilization remains higher than the scale-out threshold for 10 consecutive minutes, so a scale-out event adds one VM to the scale set, bringing the number of VMs to 5.
- There are three VMs in a scale set. The VMs report CPU utilization of 50%, 40%, and 35%, so the aggregated CPU utilization for the scale set is 41.7%. The aggregate CPU utilization remains lower than the scale-in threshold for 10 consecutive minutes, so a scale-in event removes one VM from the scale set, bringing the number to two. During the cooldown period, a traffic spike brings the aggregated CPU utilization to 83%, so when the cooldown period ends, a scale-out event adds one VM to the scale set, bringing the number of VMs back to three.
- There are two VMs in a scale set. The VMs report CPU utilization of 65% and 55%, so the aggregated CPU utilization for the VMSS is 60%. No scale-out or scale-in event is triggered because the aggregated CPU utilization remains within the scale-out and scale-in thresholds for 10 consecutive minutes.
In logs and reports, the CPU utilization metric is displayed as `smedge_cpu_utilization`.
[]If you have predictable load patterns, you can define a schedule for scale-out and scale-in events. This ensures that enough VMs are provisioned before the predicted spike. For example, if a batch job runs every Saturday at 6:00 PM, you could preemptively schedule a scale-out event for 5:45 PM. You can define the following parameters during deployment:
- **Minimum instances**: The minimum number of VMs in the scaling set during the scheduled scaling event.
- **Days of week**: The days of the week when the schedule takes effect.
- **Start time**: The time in hours and minutes to start the scheduled scaling event.
- **End time**: The time in hours and minutes to end the scheduled scaling event.
Cloud Connector Health Monitoring
Health monitoring includes the following entities:
- **Custom Metric Publishing**: Each Cloud Connector publishes a VM-level custom health metric at one-minute intervals. This metric value is 0 for an unhealthy VM or 100 for a healthy VM.
- **Health Monitoring**: The Health Monitoring function consumes the health metric at one-minute intervals and initiates the termination of a VM that it determines is unhealthy.
In logs and reports, the health metric is displayed as `cloud_connector_aggr_health`.
- [Grace Period](#graceperiod)
- [Terminating Unhealthy VMs](#termination)
[]A grace period allows a Cloud Connector to boot up before its health is evaluated, and it is potentially terminated. The grace period lasts until one of the following events occurs:
- The VM has been alive for more than 30 minutes.
- The VM reports at least one healthy metric.
After the grace period ends, a Cloud Connector is considered unhealthy if the custom health metric is reported as either:
- **None **or **0** for 7 out of the last 10 samples, starting with the first healthy sample
- **None **or **0** for 5 consecutive samples, starting with the first healthy sample
[]The Health Monitoring function determines whether a VM is unhealthy. This function terminates an unhealthy VM after the grace period ends and the unhealthy criteria are met. The VM is replaced immediately.
Unhealthy instances are terminated in iterations. In a single iteration, a VMSS can terminate 20% of the instances, or one instance, whichever is greater. The instance to terminate is based on which instance has the most healthy statuses over a 10-sample stretch. If multiple instances have the same number of unhealthy statuses, the instances to terminate are chosen randomly.
Viewing Metrics and Logs
You can view the following metrics and logs in the [Azure Portal](https://portal.azure.us/).
- [Metrics](#Metrics)
- [Function App Logs](#FunctionAppLogs)
- [][Cloud Connector Metrics](#CCMetrics)
- [VMSS Metrics](#VMSSMetrics)
- []
- [Recent Invocations](#RecentInvocations)
- [Log Streaming in Real Time](#RealTimeLogStreaming)
- [Application Insights](#ApplicationInsights)
[]Cloud Connectors publish health metrics at one-minute intervals and are managed by Application Insights.
To display the metrics:
- Navigate to **Resource Groups** > <Resource Group> > <VMSS> > <VM> > **Monitoring **> **Metrics**.
- On the **Metrics **page, click **Add metric**.
- Select the following parameters:
- Scope: <VM name>
- Metric Namespace: **zscaler/cloudconnectors**
- Metric: **cloud_connector_aggr_health**
- Aggregation: **Avg** (average)
![Graph showing query for Cloud Connector metrics where you use the Scope, Metric Namespace, Metric, and Aggregation drop-down menus to specify query parameters](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/CCMetrics.png)
[]Cloud Connectors in a scale set publish scaling metrics to the Health Monitoring function at one-minute intervals. VMSS consumes metrics from Azure Monitor for scaling decisions. The scaling metrics include `smedge_cpu_utilization`, `smedge_mem_utilization`, `smedge_bytes_in`, and `smedge_bytes_out`. The scaling rules compare the `smedge_cpu_utilization` value with the defined threshold.
To display the VMSS metrics:
- Navigate to **Resource groups** > <Resource Group> > <VMSS> > <VM> > **Monitoring **> **Metrics**.
- On the **Metrics **page, click **Add metric**.
- Select the following parameters:
- **Scope**: VMSS name
- **Metric Namespace**: **zscaler/cloudconnectors**
- **Metric**: **smedge_metrics**
- **Aggregation**: **Avg** (average)
- Click **Add filter**.
- Select the following parameters:
- **Property**: **metric_name**
- **Operator**:** =**
- **Values**: **smedge_cpu_utilization**
![Graph showing query for VMSS metrics where you use the Scope, Metric Namespace, Metric, and Aggregation drop-down menus to specify query parameters](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/VMSS_Metrics.png)
[]An Azure invocation is logged each time an Azure function is executed.
To view recent invocations:
- Go to **Resource groups** > <Resource Group>. The **Resource group** page appears.
- In the **Name **column on the **Resource **tab, find the Function App and click it. The **Function App** page appears.
- On the **Functions **tab, click the function in the **Name **column. The details page for the function app appears.
- Click the **Invocations **tab and then click the invocation in the **Date **column.
![Viewing recent App Function Invocations in Azure Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/AppFuncInvocations.png)
[]You can view logs in real time for functions that are executing.
To view real-time logs:
- Go to **Resource groups** > <Resource Group>. The **Resource group** page appears.
- In the **Name **column on the **Resources **tab, find the Function App and click it in the **Name **column. The **Function App** page appears.
- On the **Functions **tab, click the function in the **Name **column. The details page for the function app appears.
- Click the **Logs **tab.
![Viewing real-time App Function logs in the Azure Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/RealTimeLogs.png)
[]The Application Insights feature allows you to perform queries to view specific log messages, executions, time frames, and so on. For example, you can view Health Monitoring function logs that report that the VMSS found no instances to terminate. A specific message is defined when querying the logs, which allows you to refine your search instead of manually going through each invocation or continuously watching the real-time streaming of logs.
To view logs through Application Insights:
- Go to **Resource groups** > <Resource Group>.
- On the **Application Insights** page, click **Logs**.
-
Enter a query and then click **Run**.
For example, the following query would show you when there are no instances to terminate.
`union traces
| union exceptions
| where timestamp > ago(1d)
| where customDimensions['Category'] == 'Function.healthMonitor.User' or customDimensions['Category'] == 'Function.healthMonitor'
| where message contains "No instances to terminate on this iteration."
| order by timestamp asc
| project
timestamp,
message = iff(message != '', message, iff(innermostMessage != '', innermostMessage, customDimensions.['prop__{OriginalFormat}']))
`
![Viewing Health Monitor function logs through Application Insights ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-azure-virtual-machine-scale-sets-draft-doc-54950/ApplicationInsights.png)
Access to Azure Resources
Managed identities provide granular access control for Azure resources, which eliminates the need to explicitly store secret credentials within the Azure environment.
Azure Key Vault securely manages credentials for external services such as the Cloud & Branch Connector Admin Portal.
Two user-assigned managed identities are required to perform Azure operations:
- [Cloud Connector](#CCIdentity)
- [Function App](#FunctionAppIdentity)
[]This managed identity allows Cloud Connectors to perform Azure operations such as network interface discovery and metric publishing. It needs the following roles:
- Network Contributor
- Monitoring Metrics Publisher
[]This managed identity allows the Azure Function App to make API calls to perform operations such as instance termination, instance replacement, and metric reading. It needs the following roles:
- Network Contributor
- Virtual Machine Contributor
- Monitoring Contributor
- Managed Identity Operator
- Storage Blob Data Reader
User-assigned managed identities allow access to different entities in a VMSS deployment. Ensure that Cloud Connector is not assigned an Azure System Managed Identity, because that identity overrides the deployment requirements.
For information about creating managed identities and assigning roles, see [Deploying Zscaler Cloud Connector with Microsoft Azure](/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure).