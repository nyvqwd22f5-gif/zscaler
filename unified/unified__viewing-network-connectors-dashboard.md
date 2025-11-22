# Viewing the Network Connectors Dashboard
Source: https://help.zscaler.com/unified/viewing-network-connectors-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1530929.pdf

The Network Connectors dashboard (Infrastructure > Private Access > Component > VPN (for Legacy Apps) > Network Connectors Dashboard) provides information about the Network Connectors for your organization.
Dashboard Tools
The Network Connectors dashboard displays the following information and functionality:
-
**Time Period Filter**: View Network Connector data over a period between 1 Hour to 14 Days, or you can select **Custom Range**. If you use a custom range, the start and end dates must be within the last 14 days. The end date can be configured to the selected time in hours and minutes. This filter applies to all widgets on the dashboard. By default, the dashboard displays information about events that occurred in the last hour.
Due to the way data is aggregated for different time period filters, the same point in time in an Activity Monitor widget might show slightly different values depending on the time chosen. For example, the data with the 30 Mins time period filter at 3:00 PM might not match the data with the 14 Days time period filter for the same date at 3:00 PM.
- **Refresh icon**: Refresh the dashboard to reflect the most current information. The dashboard displays the most recent information from the last 5 minutes.
![View of the Network Connectors dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-network-connector-dashboard-updated.png)
Top Network Connectors Widgets
The Top Network Connectors widgets provide an overview of the peak or top metrics for the relevant Network Connectors in the selected time range.
Four widgets are selected automatically when you access the dashboard. At least 4 widgets must be selected for the widgets to display, and no more than 8 widgets are available to view at one time.
[View the widgets](#top-widgets)
Activity Monitor Widgets
The Activity Monitor widgets provide trend information about selected Network Connectors in the selected time range. If no Network Connectors are selected, the top Network Connectors from the Minimum Available Disk Space widget are selected by default.
Three widgets are selected automatically when you access the dashboard. At least three widgets must be selected for the widgets to display, and no more than 6 widgets are available to view at one time.
[View the widgets](#actvmntr-widgets)
[]Widgets might show solid lines or dashed lines. Solid lines represent actual data for the time period. Dashed lines indicate the expected trajectory of the data, but it isn't actual data. You can select a point on the lines in a widget to see the exact date, time, and relevant numbers for the Network Connectors as related to the particular widget.
[See image.](#img-widgetpt)
A plus icon (+) appears as you move over the widgets. Use this icon to select the time period to zoom in for greater detail. A blue box shows the chosen portion of the widget, and the widget shows this selected smaller time period.
[See image.](#img-prtofwidget)
Click **Zoom Out** to view the original widget.
[See image.](#img-zoomout)
For each widget, you can deselect the listed Network Connectors to change what items are tracked within the widget. You can also search within the widget to reduce the listed Network Connectors that appear on the widget. To search, enter part or all of a Network Connector name or use the following search query options with >, <, or = operators:
- **name**: The name of the Network Connector (e.g., name = MyConnector).
- **value**: A numerical value specific to the widget (e.g., value < 40).
[See image.](#img-search)
Filtering Network Connectors
You can filter the Activity Monitor charts and the Network Connector Details table by selecting the Network Connectors you want to review. The filters available are **Network Connectors** and **Network Connector Groups**.
[See image.](#img-filters)
When filtering, if you select a Network Connector group, the Network Connector associated with the Network Connector group is also shown.
The filters between Network Connectors and Network Connector groups use the OR operator, instead of AND, to help compare Network Connectors in Network Connector groups.
There is a limit of 25 Network Connectors you can select at one time. If you select Network Connectors and then select Network Connector groups in a way that exceeds the limit, you see an error message and need to adjust your selection.
[See image.](#img-filtergrp)
If no Network Connectors are selected, the top Network Connectors from the Minimum Available Disk Space widget are selected by default.
Network Connector Details
The Network Connector Details table provides information about the Network Connectors selected in the Activity Monitor section. If no Network Connectors are selected, the top Network Connectors from the Minimum Available Disk Space widget are selected by default.
The table includes:
- **Network Connectors**: The name of the Network Connector.
- **Network Connector Group**: The name of the group the Network Connector is included in.
- **Location**: The city and country that the Network Connector is connecting from.
- **Actions**: Click the Edit icon to edit the Network Connector.
[]![Actions for the VPN Connector Details table](/downloads/zpa/viewing-network-connectors-dashboard/zpa-vpn-connector-dashboard-detailstable_0.png)
- []**Minimum Available Disk Space**: Displays up to the top 10 Network Connectors that have the least disk space available in the selected time frame. This is not the average disk space used over the time frame.
- **Peak CPU Utilization**: Displays up to the top 10 Network Connectors using the most CPU in the selected time frame. This is not the average CPU used over the time frame.
- **Peak Memory Utilization**: Displays up to the top 10 Network Connectors using the most memory in the selected time frame. This is not the average memory used over the time frame.
- **Peak System File Descriptor Utilization**: Displays up to the top 10 Network Connectors using the most system file descriptors in the selected time frame. This is not the average file descriptors used over the time frame.
- **Peak TCP Port Utilization**: Displays up to the top 10 Network Connectors using the most TCP ports for IPv4 in the selected time frame. This is not the average TCP ports used over the time frame.
- **Peak UDP Port Utilization**: Displays up to the top 10 Network Connectors using the most UDP ports for IPv4 in the selected time frame. This is not the average UDP ports used over the time frame.
- []**Available Disk Space**: Displays the amount of disk space that is available to a Network Connector at different points during the selected time range.
- **CPU Utilization**: Displays the amount of CPU used by a Network Connector at different points during the selected time range.
- **Memory Utilization**: Displays the amount of memory used by a Network Connector at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **System File Descriptor Utilization**: Displays the number of file descriptors used by a Network Connector at different points during the selected time range.
- **TCP Port Utilization**: Displays the number of TCP ports for IPv4 used by a Network Connector at different points during the selected time range.
- **UDP Port Utilization**: Displays the number of UDP ports for IPv4 used by a Network Connector at different points during the selected time range.
[]
![Select a point or view logs for part of a chart on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-network-connector-dashboard-disk-space-details.png)
[]![Select a part of a chart on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-vpn-connectors-dashboard/zpa-vpn-connector-dashboard-selectbluebox_1.png)
[]![Zoom Out of a chart on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-vpn-connector-zoom-out_0.png)
[]![Search and Deselect Network Connectors in Widgets on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-vpn-connector-dashboard-searchdeselect_0.png)
[]![Filter Network Connectors on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-vpn-connector-dahboard-filters.png)
[]
![Number of Network Connectors in an Network Connector Group in the Network Connector Group filter on the Network Connector Dashboard in the Admin Portal](/downloads/zpa/viewing-network-connectors-dashboard/zpa-vpn-connector-filter_0.png)