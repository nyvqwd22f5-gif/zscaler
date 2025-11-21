# About Data Center Exclusion Based on Traffic Forwarding Method
Source: https://help.zscaler.com/zia/about-data-center-exclusion-based-traffic-forwarding-method
PDF: https://help.zscaler.com/pdf/com/en/1474516.pdf

To enable the DC Exclusion for Traffic Forwarding option for your tenant, submit a support ticket from your Admin Portal.
If a Zscaler data center (DC) is having an issue that affects the service, admins can disable all IPSec VPN tunnels terminating at a virtual IP (VIP) address of the affected DC directly from the ZIA Admin Portal. With this action, admins trigger a failover from primary to secondary tunnels at the endpoint on their organization’s premises in the event of service disruptions, [Zscaler Trust Portal](https://trust.zscaler.com/) incidents, disasters, etc. Tunnel failover is then performed according to the VPN endpoint device configuration.
This capability is supported by excluding DCs from service based on the traffic forwarding method. In the ZIA Admin Portal, an admin selects the DC and the duration (up to 15 days) of the DC exclusion. You can renew the exclusion after it expires or edit it as needed. When an admin saves and activates the configured DC exclusion:
- The admin’s action of disabling the tunnels is logged in the [Audit Logs](/zia/about-audit-logs) in the ZIA Admin Portal.
- A notification from the Zscaler Central Authority (CA) is sent to the DC indicating that the DC is excluded from service to the organization.
- Any existing tunnels to the DC are brought down immediately, and no new tunnels to the DC from the organization can be established during the exclusion.
- The status of the tunnels and the reason they are down are logged in the [Tunnel Insights Logs](/zia/tunnel-insights-logs-columns) in the ZIA Admin Portal.
The DC is restored to service when the configured exclusion expires, or if an admin takes action before the expiration. When a DC is restored for service, a new notification from the Zscaler CA is sent indicating that the DC is restored for service to the organization. At this point, existing tunnels can be re-established to the DC and new tunnels can be established.
DC exclusion based on the traffic forwarding method provides the following benefits and enables you to:
- Ensure business continuity and connectivity resilience during service-affecting events.
- Initiate a failover from primary to secondary tunnels more quickly and easily, without relying on multiple managed service providers.
- Disable and enable tunnels according to your organization’s evolving requirements, without needing to delete credentials.
About the Traffic Forwarding Method Page
On the Traffic Forwarding Method page (Administration > Resources > Traffic Forwarding Method), you can do the following:
- [Add a DC exclusion](/zia/excluding-data-center-based-traffic-forwarding-method).
- View a list of all DC exclusions. For each DC exclusion, you can view the following information:
- **Data Center**: The name of the DC.
- **Traffic Forwarding Method**: The traffic forwarding method (e.g., IPSec VPN tunnels) disabled for the DC.
- **Begin Time**: The beginning date and time of the DC exclusion.
- **Expiration Time**: The expiration date and time of the DC exclusion. A warning icon appears when the exclusion is expired.
- **Description**: (Optional) A description of the DC exclusion.
- Search for a configured DC exclusion.
- [Modify the table and its columns](/zia/using-tables).
- [Edit a configured DC exclusion](/zia/editing-deleting-duplicating-items).
- [Delete a configured DC exclusion](/zia/editing-deleting-duplicating-items).
![Screenshot of the Traffic Forwarding Method page in the ZIA Admin Portal](/downloads/zia/traffic-forwarding/about-data-center-exclusion-based-traffic-forwarding-method/zia-traffic-forwarding-page.png)