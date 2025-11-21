# Viewing the Extranet Dashboard
Source: https://help.zscaler.com/zpa/viewing-extranet-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1510081.pdf

The Extranet dashboard uses information gathered from Zscaler Internet Access (ZIA) to display extranet resources and locations with the lowest health score for overall performance and reliability in your organization.
The health score represents the health of an IPSec connection between the extranet resource's (partner) data center and the Zscaler cloud. It is a cumulative score of all the components and functions for that connection. You can have multiple connections between an extranet resource and the Zscaler cloud. Each extranet resource can have multiple locations, and each location can have multiple tunnels to the Zscaler cloud.
To learn more, see [About Extranet](/zia/about-extranet).
![Extranet dashboard and widgets in the Zscaler Private Access (ZPA) Admin Portal.](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-extranet-dashboard/zpa-extranet-dashboard_0.png)
Dashboard Tools
The Extranet dashboard displays the following information and functionality:
- **Time Range Filter**: View Source IP Anchoring data over a period between **30 Minutes** to **14 Days**, or you can select **Custom Range**. This filter applies to all widgets on the dashboard. By default, the dashboard displays information about events that occurred in the last hour.
- **Refresh icon**: Refresh the dashboard to reflect the most current information.
Widgets
The Extranet dashboard provides the following widgets:
- [Health Score for Extranet Resources](#resource-health)
- [Health Score for Extranet Locations](#location-health)
- [Health Score for Tunnels](#tunnel-health)
[]This score is the minimum of all the tunnels between the extranet resource and the Zscaler cloud via all possible locations. The score for both the VPN and IPSec tunnel ranges from 0 (unhealthy) to 100 (optimal health) for a maximum possible combined score of 200. The 5 lowest health scores appear in this widget.
![Extranet Resource Health Score Widget in the Zscaler Private Access (ZPA) Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-extranet-dashboard/zpa-extranet-dashboard-resource-score_2.png)
- Hover over a value to view the individual VPN and tunnel scores for that resource.
- Click **View Analytics** to open the Diagnostics page with a filter for the extranet resource applied to the table.
[]This score is the minimum of all the tunnels from the location to the extranet resource. The score for both the VPN and IPSec tunnel ranges from 0 (unhealthy) to 100 (optimal health) for a maximum possible combined score of 200. The 5 lowest health scores appear in this widget.
![Extranet Location Health Score Widget in the Zscaler Private Access (ZPA) Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-extranet-dashboard/zpa-extranet-dashboard-location-score_1.png)
- Hover over a value to view the individual VPN and tunnel scores for that location.
- Click **View Analytics** to open the Diagnostics page with a filter for the extranet location applied to the table.
[]This widget displays the IPSec tunnels connected to extranet resources with the lowest health scores. The score for the IPSec tunnel ranges from 0 (unhealthy) to 100 (optimal health). The 5 lowest health scores appear in this widget.
![Tunnel Health Score Widget in the Zscaler Private Access (ZPA) Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-extranet-dashboard/zpa-extranet-dashboard-tunnel-score_1.png)
- Hover over a value to view the tunnel score for that location.
- Click **View Analytics** to open the Diagnostics page with a filter for the extranet location applied to the table.