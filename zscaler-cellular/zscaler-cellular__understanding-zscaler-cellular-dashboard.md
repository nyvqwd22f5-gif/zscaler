# Understanding the Zscaler Cellular Dashboard
Source: https://help.zscaler.com/zscaler-cellular/understanding-zscaler-cellular-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1518151.pdf

The Zscaler Cellular Dashboard provides a centralized view of your organization's SIM card usage, network activity, and connectivity metrics. It offers a graphical representation of key metrics and real-time insights into your deployed SIM cards and their connection to the Zscaler cloud.
To view the Zscaler Cellular Dashboard, log in to the Zscaler Cellular Admin Portal, and click **Dashboard **in the left-side navigation.
[See image.](#full-dashboard-view-image)
Widgets
The Zscaler Cellular Dashboard provides the following widgets:
- [Total SIMs](#total-sims-widget)
- [Used SIMs](#used-sims-widget)
- [SIMs State Overview](#sim-statuses)
- [Global Map](#global-map-widget)
- [Total Usage Graph](#usage-graph-widget)
- [Usage by top 10 SIMs](#top-10-sims-usage)
- [Usage by top 20 Countries](#top-20-country-usage)
[]This widget displays the total number of SIM cards provisioned for your organization. You can click the numerical value representing the number of SIMs to go the [SIMs page](/zscaler-cellular/about-sims) and see all SIM cards provisioned for the organization.
[See image.](#total-sims-widget-image)
[]This widget shows the number of SIM cards that are actively transmitting data. You can click the numerical value representing the number of used SIMs to go the [SIMs page](/zscaler-cellular/about-sims) with appropriate filters applied. When you click the numerical value, the SIMs page displays with the Status parameter set to Active, ensuring that only the SIMs cards that are active are displayed.
[See image.](#used-sims-widget-image)
[]This widget provides an overview of the current state of the SIM cards in the network. It categorizes SIMs into the following statuses:
- **Activated**: The number of SIM cards currently active and in use. You can click the numerical value representing the number of active SIMs to go the [SIMs page](/zscaler-cellular/about-sims) to see all SIM cards that are currently active. When you click the numerical value, the SIMs page is displayed by applying the filter with the Status parameter set to Active, ensuring that only the SIMs cards that are active are displayed.
- **Inactive**: The number of SIM cards that are not in use or have been deactivated. You can click the numerical value representing the number of inactive SIMs to go the [SIMs page](/zscaler-cellular/about-sims) to see all SIM cards that are currently inactive. When you click the numerical value, the SIMs page is displayed by applying the filter with the Status parameter set to Inactive, ensuring that only the SIMs cards that are inactive are displayed.
[See image.](#sim-status-widget-image)
[]This widget displays the geographical distribution of active SIM cards on a world map with country granularity. Each blue dot represents active connections in a specific region, providing a global view of your SIM deployments.
[See image.](#global-map-widget-widget)
[]This widget shows data usage as a line and bar graph showing daily data usage trends over the selected period. The graph provides both a visual breakdown of usage spikes and a view of overall trends. In the top-left corner of this widget, the cumulative data usage for all SIM cards within the selected date range is shown. You can customize the date range by selecting a default range (**Today**, **Yesterday**, **Last 7 Days**, **Last 30 Days**, **This Month**, or **Last** **Month**) or selecting start and end dates for a custom range.
To download the graph data for the specified date range, click the **Menu **icon in the top-right corner of the graph, and select a download option based on the preferred format (**Download as SVG**, **Download as PNG**, or **Download as CSV**).
[See image.](#usage-graph-widget-image)
[]This widget displays the top 10 SIMs with the highest data consumption within the selected date range. Each SIM is identified by its unique number, and its corresponding data usage is visualized as a bar chart. You can customize the date range by selecting a default range (**Today**, **Yesterday**, **Last 7 Days**, **Last 30 Days**, **This Month**, or **Last** **Month**) or selecting start and end dates for a custom range.
To download the graph data for the specified date range, click the **Menu **icon in the top-right corner of the graph, and select a download option based on the preferred format (**Download as SVG**, **Download as PNG**, or **Download as CSV**).
[See image.](#top-10-sims-widget-image)
[]This widget presents data consumption by country, highlighting the top 20 countries where the SIMs have consumed the most data within the selected period. It helps in identifying regions with high network activity. You can customize the date range by selecting a default range (**Today**, **Yesterday**, **Last 7 Days**, **Last 30 Days**, **This Month**, or **Last** **Month**) or selecting start and end dates for a custom range.
To download the graph data for the specified date range, click the **Menu **icon in the top-right corner of the graph, and select a download option based on the preferred format (**Download as SVG**, **Download as PNG**, or **Download as CSV**).
[See image.](#top-20-countries-widget)
[]![Complete view of the Zscaler Cellular dashboard](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-dashboard_0.png)
[]![Widget showing total number of SIMs](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-total-sims-widget.png)
[]![Widget showing total number of used SIMs](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-used-sims-widget.png)
[]![Widget showing total number of SIMs across different statuses](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-sim%20-status-overview.png)
[]![Widget showing global distribution of SIMs](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-global-map-widget.png)
[]![Widget showing data usage trend](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-usage-grapgh-widget.png)
[]![Widget showing top 10 SIMs by usage](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-top-10-sims-widget.png)
[]![Widget showing top 20 countries by usage](/downloads/zscaler-cellular/dashboard-deployment-and-configuration/understanding-zscaler-cellular-dashboard/zscaler-cellular-top-20-country-widget.png)