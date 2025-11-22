# Configuring Application Load Balancing and High Availability
Source: https://help.zscaler.com/unified/configuring-application-load-balancing-and-high-availability
PDF: https://help.zscaler.com/pdf/com/en/1529606.pdf

When you bring new application environments online, you need to validate them at a reduced scale and capacity until a certain confidence level is achieved. When proven, you can gradually redirect traffic to the new environments without large architectural shifts or cutovers. This allows a non-conflicting way to mitigate any issues that arise during a migration in a controlled way. Using load balance to rank your [server groups](/unified/about-server-groups) by weight is a way to ensure application access requests are sent to the [App Connectors](/unified/about-app-connectors) with server groups that can support their traffic.
This feature is only available for Public Service Edges for Private Applications. Any configuration done for application load balancing will not be honored for the transactions originating from Private Service Edges.
After the route selection for a load balancing transaction is made, the same App Connector is served for the next 30 minutes to maintain the user session. Each time the same user accesses the same application again, the expiration time is reset. This stickiness is invalidated before the expiration time in the following cases:
- Disabling load balancing.
- Removal of a server group from the application segment containing the sticky connector.
- The weight of the server group has the sticky connector set to zero.
- Disabling a server group that has the sticky connector.
- The sticky connector is inactive (i.e., disconnected, disabled, or in an App Connector group that is disabled).
Transactions routed via load balancing do not consider application health. For on-access health monitoring applications routed via load balancing, application health is not generated, and those applications are not shown in the Health dashboard. To learn more, see [Viewing the Health Dashboard](/unified/viewing-health-dashboard).
Prerequisites
Before you configure application load balancing, make sure the following prerequisites are met:
- When used for passive failover: Less than 50% of active group connectors are healthy, and more than 50% of passive group connectors are healthy.
- When used for switching back to an active group: Less than 50% of passive group connectors are healthy, and more than 50% of active group connectors are healthy.
Configuring Load Balance
Application access requests should be routed to the App Connectors based on the weights defined for the server groups for an [application segment](/unified/configuring-defined-application-segments). All other Geo-IP and health-based path selection modes are ignored for the application segment configured with this option. Path Selection using Closer to User and Closer to App are not applicable.
Ensure that App Connector groups do not overlap within the server groups. If they do overlap, the same App Connector can be selected as active and passive groups per weights and mode of selection.
To configure load balance for your server groups:
- Go to **Policies **> **Access Control **> **Private Applications** > **App Segments**.
- Locate the application segment you want to configure, and click the **Load Balance** icon.
The **Load Balance Server Groups** window appears.
-
In the **Load Balance Server Groups** window:
- **Load Balancing Server Groups**: Select **Enabled**.
- **Server Groups**: Select server groups from the drop-down menu that host the application segments you want ranked.
- **Weight**: Enter a value for the numeric weight to rank each server group, with 0 being the lightest and 1,000 being the heaviest.
- **Passive**: Select the checkbox for each server group that you want to be passive. This means that traffic requests are routed to the App Connectors in the passive group when the active group has failed to pass the health monitoring threshold (i.e., 50% unhealthy connectors in the active group). Additionally, passive connectors should have greater than 50% of healthy connectors along with 50% of unhealthy connectors in the active group.
[See image.](#WLB-window)
- Click **Save.**
If you move a server group to a new Microtenant, be aware that you have to reassign the load balancing weight for those server groups. To learn more, see [About Private App Microtenants](/unified/about-private-app-microtenants).
[]![A view of the Load Balance Server Groups window. ](/downloads/zpa/documentation-knowledgebase/servers/server-groups/configuring-application-load-balancing-high-availability/load-balance-window_2.png)