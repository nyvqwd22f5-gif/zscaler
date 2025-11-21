# About Dedicated IP Gateways
Source: https://help.zscaler.com/zia/about-dedicated-ip-gateways
PDF: https://help.zscaler.com/pdf/com/en/1499506.pdf

To enable the Dedicated IP feature for your ZIA tenant, contact your Zscaler Account team.
You can create gateway objects to forward traffic through a dedicated IP address provisioned to the organization. These gateways are used in Zscaler [forwarding policies](/zia/configuring-forwarding-policy) to forward traffic that matches the criteria in the forwarding rule.
When dedicated IP addresses are allocated to your organization, the Zscaler service creates a default gateway that can neither be edited nor deleted. When selected in forwarding policies, this gateway ensures that the optimal data center is selected when forwarding traffic through the dedicated IP addresses. For example, when a tenant selects the default gateway in their dedicated IP forwarding policy, the Zscaler service directs the traffic to the geographically nearest data center that has a dedicated IP address assigned.
The following examples explain traffic routing for different geographic locations with the default gateway selected in the forwarding policy:
- [Example 1](#example1)
- [Example 2](#example2)
- [Example 3](#example3)
[]Consider an organization with a tenant in San Francisco forwarding traffic to the San Jose Zscaler data center. In this case:
- The egress source IP address for the tenant's traffic is the dedicated IP address assigned to the tenant at the San Jose data center.
- If the San Jose data center does not have a dedicated IP address assigned to the tenant, the default gateway forwards the traffic to the geographically nearest data center with a dedicated IP address, such as the Los Angeles data center.
[]Consider an organization with a tenant in Los Angeles. The tenant does not have a dedicated IP address provisioned for them in the Los Angeles Zscaler data center, but only in the San Jose Zscaler data center. In this case:
- The traffic is serviced at the Los Angeles data center, but it egresses from the San Jose data center, the geographically nearest data center, for which the dedicated IP addresses are assigned for the organization.
- The user does not need to explicitly forward the traffic to the San Jose data center. The data center is automatically selected based on the default gateway configuration in the forwarding rules.
[]Consider an organization with a dedicated IP address assigned to both the London Zscaler data center and the Manchester Zscaler data center. In this case:
- If a user is located in London, traffic egresses from the London data center based on the default gateway configuration in the forwarding rules.
- If the same user moves to Manchester and their traffic is serviced by the Manchester data center, the default gateway configuration automatically selects the Manchester data center to forward traffic to the destination, as it is now the closest data center with a dedicated IP address.
The Gateways page provides the following benefits and enables you to:
- Create gateway objects using the data centers that have been provisioned with IP addresses dedicated to your organization.
- Configure two data centers, primary and secondary, for a gateway object to support failover to the secondary data center when the dedicated IP addresses in the primary data center are unreachable.
About Gateways
On the Gateways (Administration > Dedicated IP > Gateways) page, you can do the following:
- [Add a dedicated IP gateway](/zia/configuring-dedicated-ip-gateways).
- View the list of all configured gateways. For each gateway, you can view:
- **Name**: The name of the gateway.
- **Primary Data Center**: The location of the primary data center for the gateway.
-
**Secondary Data Center**: The location of the secondary data center for the gateway. If you have selected **Auto**, the Zscaler service automatically selects a data center based on geographical proximity to the Zscaler Public Service Edge servicing the traffic.
The secondary data center location is used when the dedicated IP addresses at the primary data center are unreachable.
- **Description**: Additional notes or information about the gateway.
- Search for a gateway.
- Edit a configured gateway.
- Delete a configured gateway.
- View the default gateway data center details.
- Go to the [Dedicated IP Addresses](/zia/about-dedicated-ip-addresses) page.
![The Gateways page displaying the list of configured gateways with assigned dedicated IPs and the Default gateway](/downloads/zia/policies/forwarding-control/dedicated-ip/zscaler-managed-dedicated-ip/about-dedicated-ip-gateways/zia-about-dedicated-ip-gateways-main-page.png)