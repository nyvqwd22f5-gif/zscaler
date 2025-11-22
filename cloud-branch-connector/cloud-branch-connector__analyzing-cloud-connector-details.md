# Analyzing Cloud Connector Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-cloud-connector-details
PDF: https://help.zscaler.com/pdf/com/en/1420706.pdf

The Cloud Connector details page provides general, management, and forwarding information for a selected Cloud Connector. You can access the Cloud Connector details page by clicking the **View** icon (![View Icon in the Cloud & Branch Connector Monitoring Table](/downloads/cloud-connector/analytics-monitoring/about-cloud-connector-details/View%20icon%20C%26B%20Connector.jpg)
) in the [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) table for a selected Cloud Connector.
Analyzing the Cloud Connector Details Page
In the General Information section:
- [Deployment Details](#deployment-details)
- [Operational Status](#health-status)
- [Gateway Details](#gateway-details)
[]
- **Deployment Type**: The Cloud Service Provider used to deploy the selected Cloud account. The Cloud Service Provider is either Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).
- **Group**: The name of the group to which the Cloud Connector virtual machine (VM) is assigned.
- **Location**: The location of the Cloud Connector Group.
- **Geo Location**: The physical location of the Cloud Connector when deployed.
- **VM Size**: The size of the VM, which is set to **Small **by default and is the only size currently supported.
- **Version**: The version of the Cloud Connector.
- **Auto Scaling**: The status of auto scaling (i.e., **True** or **False**).
- **AWS Account ID**: The account ID of the Cloud Connector deployed with AWS.
- **Azure Subscription ID**: The subscription ID of the Cloud Connector deployed with Azure.
- **GCP Project ID**: The project ID of the Cloud Connector deployed with GCP.
[]The Operational Status shows the deployed Cloud Connector as Active or Inactive.
[]
- **Management Default Gateway**: The default gateway IP address.
- **ZIA Gateway**: The ZIA proxy gateway IP address.
- **ZPA Broker**: The default ZPA (Public or Private Service Edge) IP address.
- **Internal Gateway IP Address**: The internal gateway IP address.
In the Forwarding Information section:
- [DNS Details](#dns-details2)
- [Ingress Details](#ingress-details)
- [Egress Details](#egress-details)
[]
- **DNS Server 1**: The primary DNS Server IP address.
- **DNS Server 2**: The secondary DNS Server IP address.
[]The Ingress Details table shows the Virtual IP address. This option is currently not supported.
[]
- **Service IP Address 1**: The primary service IP address.
- **NAT IP Address**: The NAT IP address.
- **Outgoing Gateway IP Address**: The outgoing gateway IP address.
In the Management Information section:
- [Management Details](#management-details)
- [DNS Details](#dns-details)
[]
- **Management IP Address**: The management gateway IP address.
- **NAT IP Address**: The NAT IP address.
- **Default Gateway IP Address**: The default gateway IP address.
[]The DNS Details table lists the primary DNS server.
![About Cloud Connector Details in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/analyzing-cloud-connector-details-draft-doc-49014/ASG%20Cloud%20Connector%20Details.png)