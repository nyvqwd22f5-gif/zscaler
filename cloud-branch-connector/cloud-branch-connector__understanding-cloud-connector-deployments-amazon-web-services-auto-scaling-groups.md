# Understanding Cloud Connector Deployments with Amazon Web Services Auto Scaling Groups
Source: https://help.zscaler.com/cloud-branch-connector/understanding-cloud-connector-deployments-amazon-web-services-auto-scaling-groups
PDF: https://help.zscaler.com/pdf/com/en/1529197.pdf

An AWS Elastic Compute Cloud (EC2) Auto Scaling deployment dynamically adds Cloud Connector virtual machines (VMs), which are EC2 instances, to an Auto Scaling group to meet the current load, and removes Cloud Connector VMs from the group when the load decreases. You define the desired capacity and the minimum and maximum number of VMs in the group.
Auto Scaling also constantly monitors the health of each VM in the group. It removes unhealthy VMs from the group and replaces them with healthy ones. If someone manually terminates a VM that is part of an Auto Scaling group from the Amazon EC2 Console, the VM is likewise replaced.
Stopping or rebooting a VM that is part of an Auto Scaling group from the Amazon E2 Console could cause the VM to be terminated.
AWS Auto Scaling provides the following benefits:
- Dynamically scales the number of VMs in the Auto Scaling group to match demand.
- Automatically removes unhealthy VMs and replaces them with healthy ones.
- Deploys VMs across availability zones for high availability. A Gateway Load Balancer (GWLB) distributes traffic among the VMs.
This article describes AWS Auto Scaling and how it works in a Cloud Connector deployment. The deployment template prompts you to configure certain Auto Scaling settings mentioned in this article. After deployment, you can modify the settings in the [Amazon EC2 Console](https://console.aws.amazon.com/ec2/). For information about the deployment template and the deployment steps, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector) and [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services). For comprehensive Auto Scaling information, refer to the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html).
Topology
The following sections provide a diagram depicting the topology of an Auto Scale deployment and a description of its components and flow.
- [Topology diagram](#topology_diagram)
- [Topology details](#topology_details)
[]![Diagram showing a Cloud Connector Auto Scaling deployment in AWS](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/diagram_cloud-branch-connector_aws-auto-scaling_v2.png)
[]
-
The workload servers and the Auto Scaling group are deployed in separate subnets in the VPC. They are deployed into a single regional Availability Zone to simplify the management of resources.
Alternatively, you can deploy multiple Auto Scaling groups in multiple Availability Zones to provide additional reliability and redundancy.
- A GWLB is deployed in front of the Cloud Connectors. It is the entry point for traffic from the endpoints to the security stack. After the security stack is deployed, in the route tables in the workload subnets, you define a route that steers traffic to the GWLB. To learn more, see [Deploying Zscaler Cloud Connector with Amazon Web Services](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services).
- A NAT gateway used for outbound traffic from the Cloud Connectors is deployed in a public subnet in the Availability Zone. The NAT gateway has a dedicated IP address associated with it.
-
The following services run in the AWS Namespace associated with your account.
- [Zscaler Lambda](#Lambda)
- [CloudWatch](#CloudWatch)
- [EventBridge](#EventBridge)
- After a termination event, Lambda initiates a REST API call to the Cloud & Branch Connector Admin Portal so the terminated VM can be removed from the Cloud Connector Group.
[]The Zscaler Lambda function does the following:
-
Evaluates custom health metrics published by each VM.
If the VM does not publish health metrics, Lambda treats missing data points as unhealthy by default. If you want Lambda to ignore missing data points, change the value of the `MISSING_DATAPOINTS_UNHEALTHY` environment variable in the Lambda console (Functions > <Auto Scaling group function> > Configuration > Environment variables).
- Cleans up the Zscaler cloud resources associated with the VM when the VM is terminated. This includes resources allocated to Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA).
- Ensures smooth termination of Auto Scaling lifecycle events after cleaning up the cloud resources.
- Manages the termination of VMs in a warm pool.
The following conditions trigger Lambda via AWS EventBridge:
- **Periodic execution**: Triggered every minute to check VM health.
- **EC2 instance termination events**: Triggered asynchronously after a VM termination event completes.
- **EC2 lifecycle termination events**: Triggered asynchronously after a lifecycle termination event completes.
After any of these events triggers the Zscaler Lamba function, it runs for a maximum of three minutes and then terminates automatically.
[]Amazon CloudWatch monitors your AWS resources and security stack in real time. CloudWatch collects and stores logs, displays data on the CloudWatch dashboard, and triggers alarms based on specific metrics identified in the logs.
For additional information about CloudWatch, refer to the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html).
- [Metrics](#Metrics)
- [Alarms](#Alarms)
- [Logs](#Logs)
[]A metric is a time-ordered set of data points that is published to CloudWatch. The metric is the entity being monitored, and the data points are evaluation periods during which metric values change over time. Amazon EC2 Auto Scaling metrics that collect information about Auto Scaling groups are in the `AWS/AutoScaling` namespace. Amazon EC2 instance metrics that collect CPU and other usage data from VMs in Auto Scaling groups are in the `Zscaler/Cloud Connectors` namespace.
[]CloudWatch enables you to create the following types of alarms:
-
**Metric Alarm**: Monitors a single CloudWatch metric or the result of a math expression based on CloudWatch metrics. The alarm performs one or more actions based on a metric and target value during a number of data points. By default, the number of data points is 10, so if the metric value reaches the threshold for 10 consecutive minutes, the alarm is triggered. An alarm's possible actions include performing an Amazon EC2 Auto Scaling action, performing an Amazon EC2 action, and sending a notification to EventBridge.
The Target Tracking Policy automatically configures the CloudWatch alarms for scale-out and scale-in events. A high alarm triggers a scale-out event, and a low alarm triggers a scale-in event.
- **Composite Alarm**: Includes a rule expression that considers the status of other alarms you created. The composite alarm goes into an Alarm state if all the rule conditions are met. The rule expression can include metric alarms or other composite alarms.
[]The AWS CloudWatch Logs service allows you to monitor, store, and access logs from Amazon EC2 instances and other systems, applications, and AWS services in a centralized way. The CloudWatch Logs service presents all your logs from any source as a single and consistent flow of events sorted by date and time. This makes it easy to view logs, search logs for specific error codes or patterns, filter logs based on specific fields, and archive logs securely for future analysis.
You can also query your logs with a powerful query language, audit and mask sensitive information in logs, and use filters or an embedded log format to generate metrics from logs. For more information, refer to the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html).
[]This EC2 service generates events based on state changes, such as the termination of a VM. Amazon EventBridge listens for the events and routes them from sources to targets based on predefined rules. For example, the EC2 Lifecycle Termination rule sends a termination event to the Lambda function that handles lifecycle termination.
Scale-Out and Scale-In
Each Cloud Connector independently reports custom CPU utilization metrics to Amazon CloudWatch at one-minute intervals to advertise the load it is handling. AWS Auto Scaling uses the aggregate CPU utilization of all VMs in the Auto Scaling group to determine when to trigger scale-out and scale-in events and how aggressively to do so.
Auto Scaling uses custom CPU metrics instead of VM-level metrics because custom metrics provide more detailed and precise information about CPU usage.
- [Scaling Policy](#ScalingPolicy)
- [Cooldown Period and Tolerance](#CooldownPeriod)
- [Capacity and Sizing](#Parameters)
- [Examples](#ScalingExamples)
[]A Target Tracking Scaling Policy, which is a type of Dynamic Scaling Policy, manages scale-out and scale-in events. The policy defines when to increase or decrease the *desired capacity* of the group based on the aggregate custom CPU utilization metric for all VMs in the group and a target value defined in the policy. The policy defines what action to take when an Alarm-level CloudWatch alarm is triggered. You can view the policy on the details page for the Auto Scaling group in the EC2 Portal.
The Target Tracking Policy has a default target value of 80%. The policy automatically configures the CloudWatch alarms for scale-out and scale-in events:
- **Scale-Out**: A scale-out event is triggered automatically if the aggregate CPU utilization is more than 80% for 180 seconds (three minutes).
- **Scale-In**: A scale-in event is triggered automatically if the aggregate CPU utilization is less than 80% for 900 seconds (15 minutes).
In logs and reports, the CPU utilization metric is displayed as `smedge_cpu_utilization`.
[]Target Tracking provides the following safeguards:
- **Cooldown Period:** When a scale-out or scale-in event occurs, Auto Scaling automatically applies a cooldown period, during which it ignores new metric changes to give the system time to stabilize. By default, the cooldown period is 300 seconds (5 minutes).
- **Tolerance Level**: Auto Scaling adds *error bands* around the target level. This margin prevents small fluctuations from triggering scale-out or scale-in actions. For example, with the 80% target level, Auto Scaling does not act immediately when the metric reaches 80.1% or 79.9%.
[]During deployment, you configure the maximum size, minimum size, and desired capacity for an Auto Scaling group. When a scaling event happens, Auto Scaling automatically determines the number of VMs to add or remove to bring the metric closer to the target value. The Auto Scaling group adjusts the desired capacity based on that target level.
The desired capacity cannot exceed the maximum size or fall below the minimum size defined for the group. For example, suppose the desired capacity is two VMs, the minimum size is one, and the maximum size is 10. Eight scale-out events bring the desired capacity to the maximum size of 10 VMs. Scale-out actions stop. If another spike occurs, traffic responses could be delayed or random traffic could be dropped.
[]The following examples show how an Auto Scaling group with a Target Tracking Policy can change the desired capacity of an Auto Scaling group:
- **Initial State (3 VMs)**
- The VMs report CPU utilizations of 80%, 90%, and 85%, so the aggregate CPU utilization is 85%.
- Because the aggregate is slightly above the 80% target, the system waits through the cooldown period to see whether the condition persists.
- The condition persists for a few minutes after the cooldown period ends, so a scale-out action is triggered, increasing the desired capacity to 4 VMs.
- **State After Scale-Out (4 VMs)**
- The VMs report CPU utilizations of 50%, 40%, 25%, and 35%, so the aggregate CPU utilization is 37.5%.
- The aggregate is well below the 80% target, but Auto Scaling does not immediately scale in. Instead, it waits through the cooldown period and checks whether the low utilization remains consistent and significantly below target.
- If the low utilization is confirmed, a scale-in event reduces the desired capacity back to 3 VMs.
- **Stable State (2 VMs)**
- The VMs report CPU utilizations of 65% and 55%, so the aggregate CPU utilization is 60%.
- Although the aggregate is below the 80% target, it is close enough that Auto Scaling considers the system stable.
- No scale-out or scale-in action is triggered, because this level of utilization efficiently uses the current capacity.
Health Monitoring
Auto Scaling uses health checks to determine the status of a VM in the InService state.
- [Health Checks](#HealthChecks)
- [Grace Period](#GracePeriod)
[]
- Amazon EC2 Status Checks evaluate whether the VM is running and look for underlying hardware or software issues that might compromise the VM. Auto Scaling performs these status checks at one-minute intervals. If all checks pass, the overall status of the VM is **OK**. If one or more checks fail, the overall status is **Impaired**.
-
Custom Health Checks expand the scope of health monitoring.** **Each Cloud Connector posts an individual custom health metric at one-minute intervals to the `Zscaler/Cloud Connectors` custom namespace in CloudWatch. The custom metric value is 0 for an unhealthy VM or 100 for a healthy VM. The Lambda function evaluates recent health data using sliding window logic with the following configurable environment variables:
- The size of the sliding window. The default value is 10 consecutive minutes.
- The amount of time the VM was in an unhealthy state. The default value for defining a VM as unhealthy is 5 consecutive minutes.
- The tolerance for flapping values in the sliding window. The default value is 7 unhealthy counts in 10 consecutive minutes.
If either the 5- or 7-minute threshold is crossed, the VM is determined to be unhealthy.
In logs and reports, the custom health metric is displayed as `cloud_connector_aggr_health`.
[]A new Cloud Connector has a specific amount of time after it is in service before AWS Auto Scaling checks its health status. This gives the VM time to boot up and become healthy before Auto Scaling can determine it to be unhealthy and terminate it. This amount of time is called a grace period. By default, the grace period is 900 seconds (15 minutes). If the VM is healthy after the grace period ends, it remains in service. Otherwise, Auto Scaling makes an API call to remove the VM from the Cloud & Branch Connector Admin Portal and it is then terminated.
Lifecycle Management
- [Warm Pool](#WarmPool)
- [Lifecycle Hooks](#LifecycleHooks)
[]A warm pool contains pre-initialized VMs that are ready to start handling traffic. This reduces latency caused by situations such as long boot times. When a scale-out event happens, the Auto Scaling group draws from its warm pool to meet the new desired capacity. VMs that leave the warm pool count toward the desired capacity of the group. This process is called a warm start.
The VMs in the warm pool are in either the **Stopped **or **Running **state, based on your selection during deployment. Keeping the VMs in a **Stopped **state saves on cost, because you only pay for VMs that are running. In the Cloud & Branch Connector Admin Portal, stopped VMs are shown as inactive (red).
- [Warm Pool Sizing Options](#SizingOptions)
- [Warm Pool Reuse Policy](#ReusePolicy)
[]The following warm pool sizing options are available:
- By default, the size of a warm pool is dynamic, being calculated as the difference between the Auto Scaling group's maximum capacity and its desired capacity. For example, if the desired capacity of your Auto Scaling group is 5 and the maximum capacity is 8, the initial size of the warm pool is 3.
- During deployment, you can use the `MaxGroupPreparedCapacity` option to specify a custom value that is greater than the current capacity for the group. In this case, the warm pool size is the difference between the custom value and the desired capacity of the group. For example, if the desired capacity of your Auto Scaling group is 6, the maximum capacity is 18, and the custom value is 8, the size of the warm pool is 2. This option is useful for managing the cost-effectiveness of warm pools for large Auto Scaling groups.
- To set the warm pool size to a static value, set a warm pool minimum size during deployment. This ensures that a certain number of warmed VMs are always available to handle traffic. No minimum size is set by default.
[]By default, when a scale-in event happens, AWS Auto Scaling terminates a VM and then launches a new VM into the warm pool to replace it. You can instead enable the reuse policy during deployment. The reuse policy returns VMs that are already configured and able to handle traffic to the warm pool.
[]An Auto Scaling group takes custom actions to keep a VM in a wait state due to a lifecycle hook. There are two types of lifecycle hooks available for VMs in Auto Scaling groups:
- **Launch Lifecycle Hook**:** **Triggered when a new VM in an Auto Scaling group is about to be launched. The custom actions perform any necessary initialization or configuration steps before the VM goes into service.
- **Termination Lifecycle Hook**: Triggered when a VM in an Auto Scaling group is about to be terminated. The custom actions perform any necessary cleanup or data backup steps before the VM is terminated.
The lifecycle depends on whether the VM is active or in a warm pool.
- [Active VM Lifecycle](#ActiveLifecycle)
- [Warm VM Lifecycle](#WarmLifecycle)
[]The following sections describe the lifecycle of an active VM during its launch and termination.
- [Launch Lifecycle](#Launch)
- [Termination Lifecycle](#Termination)
[]Auto Scaling launches a VM into an Auto Scaling group in response to any of the following events:
- An increase in demand triggers a scale-out action.
- An unhealthy VM is terminated and needs replacing.
- You manually increase the size of the group.
The launch lifecycle proceeds as follows:
- The Auto Scaling group starts to launch the VM and puts it into the **Pending **state.
- The launch lifecycle hook puts the VM in the **Pending:Wait** state and performs the custom actions associated with the hook, including registering the VM and reporting that the VM is healthy. The VM remains in that state for 30 minutes (the Zscaler default value). If it completes the custom actions before 30 minutes elapse, the Auto Scaling group continues the launch process.
- The VM enters the **Pending:Proceed** state.
- The Auto Scaling group moves the VM into the **InService **state.
[]Auto Scaling terminates a VM in response to any of the following events:
- A decrease in demand triggers a scale-in action.
- Lambda determines that a VM is unhealthy.
- You manually decrease the size of the group.
The termination lifecycle proceeds as follows:
- The Auto Scaling group starts to terminate the VM and puts it into the **Terminating **state.
- The termination lifecycle hook puts the VM into the **Terminating:Wait** state and performs the custom actions associated with the hook. These actions include making an API call to remove the VM from the Cloud Connector Group in the Cloud & Branch Connector Admin Portal and notifying the Auto Scaling group that the VM is ready to be terminated. The VM remains in that state for 15 minutes (the Zscaler default value). If the custom actions complete before 15 minutes elapse, the Auto Scaling group continues the termination process.
- When the Auto Scaling group receives the notification from the lifecycle hook that the custom actions are complete, it moves the VM into the **Terminating:Proceed** state.
- The Auto Scaling group moves the VM into the **Terminated** state.
[]You can use lifecycle hooks with warm pools. Reasons for using them include ensuring there is enough time for VMs entering the warm pool to initialize and for VMs leaving the warm pool to become ready to handle traffic.
The lifecycle of a VM in a warm pool is as follows:
This description applies to warm pools where VMs are configured to be in a **Stopped **state. If VMs are configured to be in a **Running **state, the state is **Warmed:Running** instead of **Warmed:Stopped**.
- The new VM in the warm pool starts up and enters the **Warmed:Pending** state.
- After the VM enters the **Warmed:Pending:Wait** state, it pauses to perform a custom action.
- The VM waits for the custom action to complete before the VM stops and enters the **Warmed:Stopped** state.
- A launch event such as a scale-out action occurs.
- After the VM reaches the **Pending:Wait** state, it pauses to perform a custom action.
- When the custom action completes, the VM restarts and enters the **InService** state.
If traffic is high enough to deplete the warm pool, the Auto Scaling group can launch a VM directly into itself, if the group is not at its maximum capacity. If the Auto Scaling group launches a VM directly, the VM pauses only to perform a custom action when it enters the **Pending:Wait** state.
Viewing Metrics and Logs
- [Auto Scaling group details](#ASG)
- [Activity History](#Activity)
- [CloudWatch Metrics](#CloudWatchMetrics)
- [CloudWatch Logs](#CloudWatchLogs)
- [Cloud & Branch Connector Admin Portal](#AdminPortal)
[]The details page for an Auto Scaling group contains comprehensive information about the group, such as the capacity overview, configuration settings, scaling policy, instance management, activity history, metrics, and so on.
To view Auto Scaling group details:
- Open the [Amazon EC2 console](https://console.aws.amazon.com/ec2/).
- In the navigation pane, click **Auto Scaling Groups**.
- Select the Auto Scaling group for which you want to view activity.
[See image.](#ASG_EC2)
[]![Capacity overview section in the Amazon EC2 Console showing sections for Desired capacity, Scaling limits, Desired capacity type, and Status. Below this section, the Details, Integrations, Automatic scaling, Instance management, Instance refresh, Activity, and Monitoring tabs provide additional details.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/ASGDetailsPage.png)
[]You can see the current status of a scaling action that is in progress and whether it was successful.
To view activity history:
- Open the [Amazon EC2 console](https://console.aws.amazon.com/ec2/).
- In the navigation pane, click **Auto Scaling Groups**.
- Select the Auto Scaling group for which you want to view activity.
- On the details page for the Auto Scaling group, click the **Activity **tab.
- Scroll to the **Activity history** section.
[]You can view Auto Scaling group metrics in the Amazon EC2 Console and the CloudWatch console.
To view the metrics from the details page of an Auto Scaling group:
- Open the [Amazon EC2 console](https://console.aws.amazon.com/ec2/).
- In the navigation pane, click **Auto Scaling Groups**.
- Select the Auto Scaling group for which you want to view metrics.
- On the Auto Scaling group details page, click the **Monitoring **tab.
- (Optional) If you want to see monitoring graphs of aggregated VM metrics for the group, click the **EC2 **tab.
[See image.](#EC2Metrics)
[]![Viewing Auto Scaling group metrics from the Amazon EC2 Console](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/ASGMetricsCW.png)
To view metrics on the CloudWatch dashboard:
- Open the [CloudWatch console](https://console.aws.amazon.com/cloudwatch/).
- Do one of the following:
- Go to **Dashboards **> **Custom dashboards** > <Your Dashboard>.
- Go to **Dashboards **> **Automatic dashboards** > **AutoScaling**.
[See image.](#CWDash)
[]![Viewing Auto Scaling metrics from the CloudWatch Dashboard](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/CloudWatchDash.png)
![Image]()
[]Lambda writes logs to Amazon CloudWatch in a designated log group that contains log streams for each invocation of the Lambda function.
To view the logs:
- In the Lambda console, open the **Functions **page.
- Locate and then select the Lambda function.
- Click the **Monitor **tab and scroll to the **CloudWatch Logs** section.
[See image.](#LambdaLogs)
[]![Tables in the Lambda console listing invocations, with columns for #, Timestamp, Request ID, Log Stream, Billed duration, and Memory.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/CloudWatchLambdaFunctionLogs.png)
By default, CloudWatch retains the logs for three days. You can change the retention period via the **Actions **menu on the Log groups page in the CloudWatch console.
[]The Auto Scaling group name and instance IDs in the Amazon EC2 Console map to the Cloud Connector Group name and VM names in the Cloud & Branch Connector Admin Portal. You can view the status of each VM in the Cloud & Branch Connector Admin Portal.
To view the status:
-
Go to **Administration **> **Cloud Connector Groups**.
The value of the **Auto Scaling** column is **true **if the Cloud Connector Group maps to an AWS Auto Scaling group.
-
Select **Dashboard > Cloud & Branch Connector Monitoring **and scroll to the **Geo View** section.
Active VMs in the group are displayed in green. Inactive VMs in the group are displayed in red. You can watch the status of the VMs change as they are added to or removed from an Auto Scaling group. Click a VM to see its details.
[See image.](#Geo)
[]![The Geo View section of the Monitoring page in the Admin Portal, where inactive VMs are red and active VMs are green. This gives a visual display of VMs in an Auto Scaling group as their status changes due to Auto Scaling events. A pop-up window shows details about a VM whose image is hovered over.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/understanding-auto-scaling-groups-draft-doc-57352/GeoCCPortal.png)