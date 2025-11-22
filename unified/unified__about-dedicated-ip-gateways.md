# About Dedicated IP Gateways
Source: https://help.zscaler.com/unified/about-dedicated-ip-gateways
PDF: https://help.zscaler.com/pdf/com/en/1530627.pdf

To enable the Dedicated IP feature for your Internet & SaaS tenant, contact your Zscaler Account team.
You can create gateway objects to forward traffic through a dedicated IP address provisioned to the organization. These gateways are used in Zscaler [forwarding policies](/unified/configuring-forwarding-policy) to forward traffic to destinations that require a dedicated source IP address of the organization.
When dedicated IP addresses are allocated to your organization, the Zscaler service creates a Default gateway that can neither be edited nor deleted. When selected in forwarding policies, this gateway ensures that the optimal data center is selected when forwarding traffic through the dedicated IP address. For example, if a user in San Francisco has traffic being forwarded to the San Jose Zscaler data center, the egress source IP address for that traffic is the dedicated IP address assigned to that user at the San Jose data center. If there is no dedicated IP address assigned to the user at the San Jose data center, then the geographically nearest data center that has a dedicated IP address assigned is selected to forward the traffic.
The Gateways page provides the following benefits and enables you to:
- Create gateway objects using the dedicated IP addresses provisioned for your organization to forward traffic to destinations that require a preregistered unique source IP address for their traffic.
- Leverage Internet & SaaS forwarding policies to selectively forward traffic to a dedicated egress source IP address based on location, users, network service, applications, destination, etc.
- Configure two data centers, primary and secondary, for a gateway object to support failover to the secondary data center when the primary data center is unreachable.
About Gateways
On the Gateways (Infrastructure > Internet & SaaS > Network Policies > Dedicated IP) page, you can do the following:
- [Add a dedicated IP gateway](/zia/configuring-dedicated-ip-gateways).
- View the list of all configured gateways. For each gateway, you can view:
- **Name**: The name of the gateway.
- **Primary Data Center**: The location of the primary data center for the gateway.
-
**Secondary Data Center**: The location of the secondary data center for the gateway. If you have selected Auto, the Zscaler service automatically selects a data center based on geographical proximity to the Zscaler Public Service Edge servicing the traffic.
The secondary data center location is used when the primary data center is unreachable.
- **Description**: Additional notes or information about the gateway.
- Search for a gateway.
- View the default gateway.
- Edit a configured gateway.
- Delete a configured gateway.
- Go to the [Dedicated IP Addresses](/unified/about-dedicated-ip-addresses) page.
![The Gateways page displaying the list of configured gateways with assigned dedicated IPs and the Default gateway](/downloads/zia/policies/forwarding-control/dedicated-ip/about-dedicated-ip-gateways/zia-about-dedicated-ip-gateways-page.png)