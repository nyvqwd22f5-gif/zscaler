# Analyzing Cloud Connector Details
Source: https://help.zscaler.com/unified/analyzing-cloud-connector-details
PDF: https://help.zscaler.com/pdf/com/en/1516836.pdf

The Cloud Connector details page provides general, management, and forwarding information for a selected Cloud Connector. You can access the Cloud Connector details page by clicking the **View** icon in the [Cloud Connector monitoring](/unified/accessing-cloud-branch-connector-monitoring) table for a selected Cloud Connector.
Analyzing the Cloud Connector Details Page
In the General Information section:
- [Deployment Details](#deployment-details)
- [Operational Status](#health-status)
- [Gateway Details](#gateway-details)
[]
- **Deployment Type**: The cloud service provider used to deploy the selected Cloud account. The cloud service provider is either Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).
- **Group**: The name of the group to which the Cloud Connector virtual machine (VM) is assigned.
- **Location**: The location of the Cloud Connector Group.
- **Geo Location**: The physical location of the Cloud Connector when deployed.
- **VM Size**: The size of the VM.
- **Version**: The version of the Cloud Connector.
[]The Operational Status shows the deployed Cloud Connector as **Active** or **Inactive**.
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
[]The Ingress Details table shows the **Virtual IP Address**. This option is currently not supported.
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