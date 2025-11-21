# Viewing the Private Service Edge Dashboard
Source: https://help.zscaler.com/zpa/viewing-private-service-edge-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1485151.pdf

The ZPA Private Service Edge dashboard provides information about the ZPA Private Service Edges for your organization.
Dashboard Tools
The Private Service Edge dashboard displays the following information and functionality:
- **Time Period Filter**: View user data over a period between **30 Mins** to **14 Days**, or you can select **Custom Range** to specify a custom start and end date. If you use Custom Range, the start date can be within the last 14 days. This filter applies to all widgets on the dashboard. By default, the dashboard displays information for events that occurred in the past 30 minutes.
Due to the way data is aggregated for different time period filters, the same point in time in an Activity Monitor widget might show slightly different values depending on the time chosen. For example, the data with the **30 Mins** time period filter at 3:00 PM might not match the data with the **14 Days** time period filter for the same date at 3:00 PM.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information. The page displays the most recent information from the last 5 minutes.
![Viewing the Private Service Edge dashboard tools](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/Private%20Service%20Edges.png)
Top Private Service Edge Widgets
The Top Private Service Edge widgets provide an overview of the peak or top metrics for the relevant Private Service Edges in the selected time range.
Four widgets are selected automatically when you access the dashboard. At least 4 widgets must be selected for the widgets to display, and no more than 8 widgets are available to view at one time.
- [View the widgets:](#TopWidgets)
Click on any of the Private Service Edges in the widgets to view the [User Activity Diagnostic logs](/zpa/about-user-activity-diagnostics) page filtered for this Private Service Edge.
- []**Top Errors**: Displays up to the top 100 ZPA Private Service Edges that had the most errors in the selected time range. This widget displays automatically when first accessing the dashboard.
- **Minimum Available Disk Space**: Displays up to the top 10 ZPA Private Service Edges that have the least disk space available in the selected time range. This is not the average disk space used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak CPU Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most CPU in the selected time range. This is not the average CPU used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak File Descriptor Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most file descriptors in relation to their maximum number of file descriptors.
- **Peak Memory Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most memory in the selected time range. This is not the average memory used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak System File Descriptor Utilization**: Displays up to the top 10 ZPA Private Service Edges in the entire system using the most file descriptors in the selected time range.
- **Peak TCP IPv6 Port Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most TCP ports for IPv6 in the selected time range. This is not the average number of TCP ports used over the time range, and it does not show ZPA Private Service Edges using TCP ports for IPv4.
- **Peak TCP Port Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most TCP ports for IPv4 in the selected time range. This is not the average number of TCP ports used over the time range, and it does not show ZPA Private Service Edges using TCP ports for IPv6.
- **Peak UDP IPv6 Port Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most UDP ports for IPv6 in the selected time range. This is not the average number of UDP ports used over the time range, and it does not show ZPA Private Service Edges using UDP ports for IPv4.
- **Peak UDP Port Utilization**: Displays up to the top 10 ZPA Private Service Edges using the most UDP ports for IPv4 in the selected time range. This is not the average number of UDP ports used over the time range, and it does not show ZPA Private Service Edges using UDP ports for IPv6.
[]Activity Monitor Widgets
The Activity Monitor widgets provide trend information about selected Private Service Edges in the selected time range. If no Private Service Edges are selected, the top Private Service Edges from the Peak Memory Utilization widget are selected by default.
Three widgets are selected automatically when you access the dashboard. At least three widgets must be selected for the widgets to display, and no more than 6 widgets are available to view at one time.
- [View the widgets:](#MonitorWidgets)
Widgets can show solid lines or dashed lines. Solid lines represent actual data for the time period. Dashed lines indicate the expected trajectory of the data, but it isn't actual data. You can select a point on the lines in a widget to see the exact date, time, and relevant numbers for the Private Service Edges as related to the particular widget. You can also click **View Logs** to see the [User Activity Diagnostic logs](/zpa/about-user-activity-diagnostics) page filtered for the ZPA Private Service Edges in the widget.
[See image.](#monitorWidgetPoint)
A (**+**) icon appears as you move over the widgets. Use this icon to select the time period to zoom in for greater detail. A blue box shows the chosen portion of the widget, and the widget shows this selected smaller time period.
[See image.](#partOfMonitorWidget)
Click **Zoom Out** to view the original widget.
[See image.](#zoomInTheMonitorWidgets)
For each widget, you can deselect the listed Private Service Edges to change what items are tracked within the widget. You can also search within the widget to reduce the listed Private Service Edges that appear in the widget. To search, enter part or all of a Private Service Edge name, or use the following search query options with >, <, or = operators:
- name: The name of the Private Service Edge (e.g., name = MyPrivateServiceEdge).
- value: A numerical value specific to the widget (e.g., value < 40).
[See image.](#SearchDeselect)
- []**Available Disk Space**: Displays the amount of disk space that is available to a ZPA Private Service Edge at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **CPU Utilization**: Displays the amount of CPU used by a ZPA Private Service Edge at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **File Descriptor Utilization**: Displays the number of file descriptors used by a ZPA Private Service Edge at different points during the selected time range.
- **Memory Utilization**: Displays the amount of memory used by a ZPA Private Service Edge at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **System File Descriptor Utilization**: Displays the number of file descriptors used by the entire system running the ZPA Private Service Edges in the selected time range.
- **TCP IPv6 Port Utilization**: Displays the number of TCP ports for IPv6 used by a ZPA Private Service Edge at different points during the selected time range. It does not show ZPA Private Service Edges using TCP ports for IPv4.
- **TCP Port Utilization**: Displays the number of TCP ports for IPv4 used by a ZPA Private Service Edge at different points during the selected time range. It does not show ZPA Private Service Edges using TCP ports for IPv6.
- **UDP IPv6 Port Utilization**: Displays the number of UDP ports for IPv6 used by a ZPA Private Service Edge at different points during the selected time range. It does not show ZPA Private Service Edges using UDP ports for IPv4.
- **UDP Port Utilization**: Displays the number of UDP ports for IPv4 used by a ZPA Private Service Edge at different points during the selected time range. It does not show ZPA Private Service Edges using UDP ports for IPv6.
Filtering Private Service Edges
You can filter the Activity Monitor charts and Private Service Edge Details table by selecting the Private Service Edges you want to review. The filters available are Private Service Edge and Private Service Edge Groups.
[See image.](#filters)
When filtering by Private Service Edges and Private Service Edge Groups, the selected Private Service Edges and Private Service Edges within the selected Private Service Edge Groups are shown.
The filters between Private Service Edges and Private Service Edge Groups use the OR operator, instead of AND, to help compare Private Service Edges in Private Service Edge Groups.
There is a limit of 25 Private Service Edges you can select at one time. If you haven't selected any Private Service Edges and have selected a Private Service Edge Group that contains more than 25 Private Service Edges, then the first 25 Private Service Edges for the selected Private Service Edge Group are used in the filter. If you select Private Service Edges and then select Private Service Edge Groups in a way that exceeds the limit, an error message appears and you must adjust your selection.
Within the Private Service Edge Group filter, you can see the number of Private Service Edges associated with the Private Service Edge Group.
[See image.](#filterGroup)
If no Private Service Edges are selected, the top Private Service Edges from the Peak Memory Utilization chart are selected by default.
Private Service Edge Details
The Private Service Edge Details table provides information about the ZPA Private Service Edge selected in the Activity Monitor section. If no ZPA Private Service Edges are selected, the top ZPA Private Service Edges from the Peak Memory Utilization widget are selected by default.
The table covers:
- **Private Service Edges**: The name of the ZPA Private Service Edges.
- **Private Service Edge Group**: The name of the group the ZPA Private Service Edge is included in.
- **Location**: The city and country that the ZPA Private Service Edge is connecting from.
- **Actions**:
- **View**: Click to view the Private Service Edge Details page and Private Service Edge Latency pages.
- **Edit**: Click to edit the ZPA Private Service Edge.
- **Logs**: Click to view the [User Activity Diagnostic logs](/zpa/about-user-activity-diagnostics) page filtered for this ZPA Private Service Edge.
[See image.](#PrivateServiceEdgeDetailsActions)
Evaluating Individual Private Service Edge Details and Latency
For each ZPA Private Service Edge, you can click the **View **icon for a ZPA Private Service Edge in the Private Service Edge Details table. For each ZPA Private Service Edge, you can view:
- [Details](#Details)
- [Latency](#Latency)
The **Details** tab is automatically selected.
[See image.](#DetailsTab)
- [][General Information](#GeneralInformation)
- [Private Service Edge Information](#PrivateServiceEdgeInformation)
- [Activity Monitor Widgets](#DetailsActivityMonitor)
[]The general information available about the Private Service Edge:
- **Private Service Edge Group**: The name of the group the Private Service Edge is included in.
- **Location**: The city and country that the Private Service Edge is connecting from.
- **Enabled**: Identifies if the Private Service Edge is enabled or disabled.
- **Session Status**: The status of the Private Service Edge session during the time range. The potential session statuses are:
- **Authenticated**: The Private Service Edge successfully authenticated.
- **Authentication Failed**: The Private Service Edge was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The Private Service Edge successfully disconnected.
- **Periodic Software Update On**: The date and time of the next periodic software update for the Private Service Edge.
- **Last Software Update On**: The date and time of the last software update for the Private Service Edge.
- **Scheduled Software Version**: The next Private Service Edge software version that the Private Service Edge upgrades to.
- **Current** **Software** **Version**: The current Private Service Edge software version during the time range.
- **Connection Status**: The connection status of the Private Service Edge during the time range. The potential session statuses are:
- **Connected**: The Private Service Edge is up during the time range.
- **Disconnected**: The Private Service Edge is down during the time range.
![General information for a Private Service Edge on the Private Service Edge dashboard](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-private-service-ege-general-information.png)
[]The values and percentages for each item in this section are initially based on the most recent data available as noted by the point in time listed on the right side of this section.
![Time Selection for Individual ZPA Private Service Edge Details](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-details-private-service-edge-information.png)
The information available about the ZPA Private Service Edge is:
- **Active Application Tunnel Count**: The number of active connections the ZPA Private Service Edge had to applications for the point in time listed.
- **Active Connections to App Connectors**: The number of active connections the ZPA Private Service Edge had to App Connectors for the point in time listed.
- **Active Connections to Public Service Edges**: The active connection the ZPA Private Service Edge had to ZPA Public Service Edges for the point in time listed.
- **Available Disk Space**: The number of available disk space for the ZPA Private Service Edge at the point in time listed.
- **Bytes Received from the App Connector**: The number of received bytes from App Connectors to the ZPA Private Service Edge in the selected time range.
- **Bytes Transmitted to the App Connector**: The number of transmitted bytes to App Connectors from the ZPA Public Service Edges in the selected time range.
- **Configured Application Count**: The number of applications configured for access via the ZPA Private Service Edge at different points during the selected time range.
- **CPU Utilization**: The highest CPU used by the ZPA Public Service Edge for the time range selected.
- **Disconnected Connections to App Connectors**: The number of disconnected connections to App Connectors in the selected time range for a ZPA Private Service Edge.
- **Disconnected Connections to Public Service Edges**: The number of disconnected connections to ZPA Public Service Edges in the selected time range for a ZPA Private Service Edge.
- **File Descriptor Maximum Limit**: The maximum limit of file descriptors used by a ZPA Private Service Edge at different points during the selected time range.
- **File Descriptor Utilization**: The file descriptors used by the ZPA Public Service Edge for the point in time listed.
- **Number of Usable Ports**: The number of usable ports for a ZPA Private Service Edge at different points during the selected time range.
- **Memory Utilization**: The highest memory used by the ZPA Private Service Edge for the selected time range.
- **Rate of Bits Received from Public Service Edge**: The number of bits received per second by the ZPA Private Service Edge from the ZPA Public Service Edge for the point in time listed.
- **Rate of Bits Transmitted to Public Service Edges**: The number of bits transmitted per second by the ZPA Private Service Edge to ZPA Public Service Edges for the point in time listed.
- **TCP IPv6 Port Utilization: **The number of TCP ports for IPv6 used by the ZPA Private Service Edge for the point in time listed. It does not show ZPA Private Service Edges using TCP ports for IPv4.
- **TCP Port Utilization**: The number of TCP ports for IPv4 used by the ZPA Private Service Edge for the point in time listed. It does not show ZPA Private Service Edges using TCP ports for IPv6.
- **Total Transactions Completed**: The total number of completed connections to applications on a ZPA Private Service Edge.
- **UDP IPv6 Port Utilization: **The number of UDP ports for IPv6 used by the ZPA Private Service Edge for the point in time listed. It does not show ZPA Private Service Edges using TCP ports for IPv4.
- **UDP Port Utilization**: The number of UDP ports for IPv4 used by the ZPA Private Service Edges for the point in time listed. It does not show ZPA Private Service Edges using UDP ports for IPv6.
[]The Activity Monitor section displays the same widgets with the same functionality as seen in the [Activity Monitor](#ActivityMonitorWidgets) section. Three widgets are selected automatically. They are:
- Active Application Tunnel Count
- CPU Utilization
- Memory Utilization
[]The latency monitor widgets on the Latency tab show the latency trend from a ZPA Public Service Edge to a ZPA Private Service Edge in the selected time range. The time range for the Latency tab is different from the rest of the App Connector Dashboard. It is limited to data over a period between **30 Mins** to **24 Hours**, or you can select **Custom Range** to specify a custom start and end date. If you use Custom Range, the start date can be within the last 24 hours. This filter applies to all widgets in the Latency tab, and the default time is 30 minutes.
The widgets available are:
- Private Service Edge to Default Gateway TCP Latency
- Private Service Edge to Public Service Edge Latency
Each widget shows the ZPA Public Service Edges that interact with the selected ZPA Private Service Edge during the time range. The widgets have the same functionality as seen in the [Activity Monitor](#ActivityMonitorWidgets) section.
For each widget, you can search by entering part or all of a ZPA Private Service Edge name, or by using the following search query options with >, <, or = operators:
- location: The location of the ZPA Private Service Edge (e.g., location = San Jose).
- name: The name of the ZPA Private Service Edge (e.g., name = sj_serviceedge).
- value: A numerical value specific to the widget (e.g., value < 40).
![Latency Tab on the Private Service Edge Dashboard](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-latency-tab.png)
[]![Select a point in time or view the logs](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-monitor-widgets.png)
[]![Select a part of the chart](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-prtofwidget.png)
[]![Zoom Out of a chart on the Private Service Edge Dashboard](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-widget-zoomOut.png)
[]![Search and Deselect Private Service Edges in Widgets](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-deselect-search-in-widgets.png)
[]![Filter Private Service Edges on the Private Service Edge Dashboard in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-filtering.png)
[]![Number of Private Service Edge Groups in the Private Service Edge Group filter](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-filtering-private-service-edge-groups.png)
[]![Actions for the Private Service Edge Details table](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-detailsActions.png)
[]![Details and Latency Tabs for Private Service Edges in the Private Service Edge Dashboard](/downloads/zpa/dashboard-diagnostics/about-private-service-edge-dashboard/zpa-private-service-edge-dashboard-details-and-latency-tabs.png)