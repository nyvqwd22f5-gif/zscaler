# Analyzing Branch Connector Details
Source: https://help.zscaler.com/unified/analyzing-branch-connector-details
PDF: https://help.zscaler.com/pdf/com/en/1516826.pdf

The Branch Connector details page provides general, management, and forwarding information for a selected Branch Connector. You can access the Branch Connector details page by clicking the **View** icon in the [Branch Connector monitoring](/unified/accessing-cloud-branch-connector-monitoring) table for a selected Branch Connector.
Analyzing the Branch Connector Details Page
In the General Information section:
- [Deployment Details](#deployment-details)
- [Operational Status](#operational-status)
- [Gateway Details](#gateway-details)
[]
- **Deployment Type**: The Branch Service Provider (i.e., Branch Cloud) used to deploy the selected Branch account.
- **Group**: The name of the group to which the Branch Connector virtual machine (VM) is assigned.
- **Location**: The location of the Branch Connector Group.
- **Geo Location**: The physical location of the Branch Connector when deployed.
- **VM Size**: The size of the VM, which is set to **Small **by default. Small and Medium VM sizes are supported.
- **Version**: The version of the Branch Connector.
- []**Status**: The Operational Status shows the deployed Branch Connector as **Active** or **Inactive**.
- **HA Status**: The High Availability status of the deployed Branch Connector.
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
[]The Ingress Details table shows the load balancer IP address. This option is currently not supported.
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
[]The DNS Details table lists the primary DNS server IP address.