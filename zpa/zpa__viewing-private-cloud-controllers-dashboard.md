# Viewing the Private Cloud Controllers Dashboard
Source: https://help.zscaler.com/zpa/viewing-private-cloud-controllers-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1506341.pdf

The Private Cloud Controllers dashboard provides information about the Private Cloud Controllers for your organization.
Dashboard Tools
The Private Cloud Controllers dashboard displays the following information and functionality:
- **Time Period Filter**: View user data over a period between **30 Mins** to **14 Days**, or you can select **Custom Range** to specify a custom start and end date. If you use Custom Range, the start date can be within the last 14 days. This filter applies to all widgets on the dashboard. By default, the dashboard displays information for events that occurred in the past 30 minutes.
Due to the way data is aggregated for different time period filters, the same point in time in an Activity Monitor widget might show slightly different values depending on the time chosen. For example, the data with the **30 Mins** time period filter at 3:00 PM might not match the data with the **14 Days** time period filter for the same date at 3:00 PM.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information. The page displays the most recent information from the last 5 minutes.
[See image.](#PrivateCloudControllerTools)
Top Private Cloud Controller Widgets
The Top Private Cloud Controller widgets provide an overview of the peak or top metrics for the relevant Private Cloud Controllers in the selected time range.
Four widgets are selected automatically when you access the dashboard. At least 4 widgets must be selected for the widgets to display, and no more than 8 widgets are available to view at one time.
- [View the widgets:](#TopWidgets)
Click on any of the Private Cloud Controllers in the widgets to view the [User Activity Diagnostic logs](/zpa/about-user-activity-diagnostics) page filtered for this Private Cloud Controller.
- []**Minimum Available Disk Space**: Displays up to the top 10 Private Cloud Controllers that have the least disk space available in the selected time range. This is not the average disk space used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak CPU Utilization**: Displays up to the top 10 Private Cloud Controllers using the most CPU in the selected time range. This is not the average CPU used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak File Descriptor Utilization**: Displays up to the top 10 Private Cloud Controllers using the most file descriptors in relation to their maximum number of file descriptors.
- **Peak Memory Utilization**: Displays up to the top 10 Private Cloud Controllers using the most memory in the selected time range. This is not the average memory used over the time range. This widget displays automatically when first accessing the dashboard.
- **Peak TCP IPv6 Port Utilization**: Displays up to the top 10 Private Cloud Controllers using the most TCP ports for IPv6 in the selected time range. This is not the average number of TCP ports used over the time range, and it does not show Private Cloud Controllers using TCP ports for IPv4.
- **Peak TCP Port Utilization**: Displays up to the top 10 Private Cloud Controllers using the most TCP ports for IPv4 in the selected time range. This is not the average number of TCP ports used over the time range, and it does not show Private Cloud Controllers using TCP ports for IPv6.
- **Peak UDP IPv6 Port Utilization**: Displays up to the top 10 Private Cloud Controllers using the most UDP ports for IPv6 in the selected time range. This is not the average number of UDP ports used over the time range, and it does not show Private Cloud Controllers using UDP ports for IPv4.
- **Peak UDP Port Utilization**: Displays up to the top 10 Private Cloud Controllers using the most UDP ports for IPv4 in the selected time range. This is not the average number of UDP ports used over the time range, and it does not show Private Cloud Controllers using UDP ports for IPv6.
- **Total Bytes Received from Public Service Edges**: Displays up to the top 10 Private Cloud Controllers and the number of bytes received by each from the ZPA Public Service Edges.
- **Total Bytes Transmitted to Public Service Edges**: Displays up to the top 10 Private Cloud Controllers and the number of bytes transmitted by each to the ZPA Public Service Edges.
- **Total App Connectors Connected to the Private Cloud Controller**: Displays up to the top 10 Private Cloud Controllers and the total number of App Connectors connected to each.
- **Total Private Service Edges Connected to the Private Cloud Controller**: Displays up to the top 10 Private Cloud Controllers and the total number of ZPA Private Service Edges connected to each.
- **Peak Zscaler Client Connector Redirections to Private Service Edges**: Displays up to the top 10 Zscaler Client Connector redirects to the ZPA Private Service Edges.
- **Logs Successfully Transmitted to SIEM**: The total number of successful logs transmitted to the SIEM. This is a cumulative count of all diagnostic log types (i.e., User Status, User Activity, App Connector Status, Private Service Edge Status, etc.).
- **Logs Failed to be Transmitted to SIEM**: The total number of logs that failed to be transmitted to the SIEM. This is a cumulative count of all diagnostic log types (i.e., User Status, User Activity, App Connector Status, Private Service Edge Status, etc.).
[]Activity Monitor Widgets
The Activity Monitor widgets provide trend information about selected Private Cloud Controllers in the selected time range. If no Private Cloud Controllers are selected, the top Private Cloud Controllers from the Peak Memory Utilization widget are selected by default.
Three widgets are selected automatically when you access the dashboard. At least three widgets must be selected for the widgets to display, and no more than 6 widgets are available to view at one time.
- [View the widgets:](#MonitorWidgets)
Widgets show solid lines that represent actual data for the time period. You can select a point on the lines in a widget to see the exact date, time, and relevant numbers for the Private Cloud Controllers as related to the particular widget. You can also click **Show All Labels** to show or hide the particular labels for the Private Cloud Controllers in the widget.
[See image.](#monitorWidgetPoint)
A (**+**) icon appears as you move over the widgets. Use this icon to select the time period to zoom in for greater detail. A blue box shows the chosen portion of the widget, and the widget shows this selected smaller time period.
[See image.](#partOfMonitorWidget)
Click **Zoom Out** to view the original widget.
[See image.](#zoomInTheMonitorWidgets)
For each widget, you can deselect the listed Private Cloud Controllers to change what items are tracked within the widget. You can also search within the widget to reduce the listed Private Cloud Controllers that appear in the widget. To search, enter part or all of a Private Cloud Controller name, or use the following search query options with >, <, or = operators:
- Name: The name of the Private Cloud Controller (e.g., name = MyPrivateCloudController).
- Value: A numerical value specific to the widget (e.g., value < 40).
[See image.](#SearchDeselect)
- []**Available Disk Space**: Displays the amount of disk space that is available to a Private Cloud Controller at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **CPU Utilization**: Displays the amount of CPU used by a Private Cloud Controller at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **File Descriptor Utilization**: Displays the number of file descriptors used by a Private Cloud Controller at different points during the selected time range.
- **Memory Utilization**: Displays the amount of memory used by a Private Cloud Controller at different points during the selected time range. This widget displays automatically when first accessing the dashboard.
- **TCP IPv6 Port Utilization**: Displays the number of TCP ports for IPv6 used by a Private Cloud Controller at different points during the selected time range. It does not show Private Cloud Controllers using TCP ports for IPv4.
- **TCP Port Utilization**: Displays the number of TCP ports for IPv4 used by a Private Cloud Controller at different points during the selected time range. It does not show Private Cloud Controllers using TCP ports for IPv6.
- **UDP IPv6 Port Utilization**: Displays the number of UDP ports for IPv6 used by a Private Cloud Controller at different points during the selected time range. It does not show Private Cloud Controllers using UDP ports for IPv4.
- **UDP Port Utilization**: Displays the number of UDP ports for IPv4 used by a Private Cloud Controller at different points during the selected time range. It does not show Private Cloud Controllers using UDP ports for IPv6.
- **Bytes Received from Public Service Edges**: Displays the number of bytes received by the Private Cloud Controller from the ZPA Public Service Edges.
- **Bytes Transmitted to Public Service Edges**: Displays the number of bytes transmitted by the Private Cloud Controller from the ZPA Public Service Edges.
- **App Connectors Connected to the Private Cloud Controller**: Displays the number of App Connectors connected to the Private Cloud Controller.
- **Private Service Edges Connected to the Private Cloud Controller**: Displays the number of Private Service Edges connected to the Private Cloud Controller.
- **Zscaler Client Connector Redirections to Private Service Edges**: Displays the number of Zscaler Client Connector redirects to the ZPA Private Service Edges.
- **Logs Successfully Transmitted to SIEM**: Displays the number of successful logs that are transmitted to the SIEM.
- **Logs Failed to be Transmitted to SIEM**: Displays the number of logs that failed to be transmitted to the SIEM.
Filtering Private Cloud Controllers
You can filter the Activity Monitor charts and Private Cloud Controller Details table by selecting the Private Cloud Controllers you want to review. The filters available are **Private Cloud Controllers** and **Private Cloud Controller Groups**.
[See image.](#filters)
When filtering by Private Cloud Controllers and Private Cloud Controller groups, the selected Private Cloud Controllers and Private Cloud Controllers within the selected Private Cloud Controller groups are shown.
The filters between Private Cloud Controllers and Private Cloud Controller groups use the OR operator, instead of AND, to help compare Private Cloud Controllers in Private Cloud Controller groups.
There is a limit of 25 Private Cloud Controllers you can select at one time. If you haven't selected any Private Cloud Controllers and have selected a Private Cloud Controller group that contains more than 25 Private Cloud Controllers, then the first 25 Private Cloud Controllers for the selected Private Cloud Controller group are used in the filter. If you select Private Cloud Controllers and then select Private Cloud Controller groups in a way that exceeds the limit, an error message appears and you must adjust your selection.
Within the **Private Cloud Controller Groups** filter, you can see the number of Private Cloud Controllers associated with the Private Cloud Controller group.
[See image.](#filterGroup)
If no Private Cloud Controllers are selected, the top Private Cloud Controllers from the **Peak Memory Utilization chart** are selected by default.
Private Cloud Controller Details
The Private Cloud Controller Details table provides information about the Private Cloud Controller selected in the Activity Monitor section. If no Private Cloud Controllers are selected, the top Private Cloud Controllers from the **Peak Memory Utilization** widget are selected by default.
The table covers:
- **Private Cloud Controllers**: The name of the Private Cloud Controllers.
- **Private Cloud Controller Group**: The name of the group the Private Cloud Controller is included in.
- **Location**: The city and country that the Private Cloud Controller is connecting from.
- **Actions**: The following actions are available:
- **View**: Click to view the Private Cloud Controller Details page and Private Cloud Controller Latency pages.
- **Edit**: Click to edit the Private Cloud Controller.
- **Logs**: Click to view the [User Activity Diagnostic logs](/zpa/accessing-user-activity-diagnostics) page filtered for this Private Cloud Controller.
[See image.](#PrivateCloudControllerDetailsActions)
Evaluating Individual Private Cloud Controller Details and Latency
For each Private Cloud Controller, you can click the **View **icon for a Private Cloud Controller in the Private Cloud Controller Details table. For each Private Cloud Controller, you can view:
- [Details](#Details)
- [Latency](#Latency)
The **Details** tab is automatically selected.
[See image.](#DetailsTab)
- [][General Information](#GeneralInformation)
- [Private Cloud Controller Information](#PrivateCloudControllerInformation)
- [Activity Monitor Widgets](#DetailsActivityMonitor)
[]The general information available about the Private Cloud Controller:
- **Private Cloud Controller Group**: The name of the group the Private Cloud Controller is included in.
- **Location**: The city and country that the Private Cloud Controller is connecting from.
- **Enabled**: Identifies if the Private Cloud Controller is enabled or disabled.
- **Session Status**: The status of the Private Cloud Controller session during the time range. The potential session statuses are:
- **Authenticated**: The Private Cloud Controller successfully authenticated.
- **Authentication Failed**: The Private Cloud Controller was unable to authenticate to the Zscaler cloud.
- **Disconnected**: The Private Cloud Controller successfully disconnected.
- **Periodic Software Update On**: The date and time of the next periodic software update for the Private Cloud Controller.
- **Last Software Update On**: The date and time of the last software update for the Private Cloud Controller.
- **Scheduled Software Version**: The next Private Cloud Controller software version that the Private Cloud Controller upgrades to.
- **Current** **Software** **Version**: The current Private Cloud Controller software version during the time range.
- **Connection Status**: The connection status of the Private Cloud Controller during the time range. The potential session statuses are:
- **Connected**: The Private Cloud Controller is up during the time range.
- **Disconnected**: The Private Cloud Controller is down during the time range.
![General information for a Private Cloud Controller on the Private Cloud Controllers dashboard](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-details-general-info.jpg)
[]The values and percentages for each item in this section are initially based on the most recent data available as noted by the point in time listed on the right side of this section.
![Time Selection for Individual Private Cloud Controller Details](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-details-date-info.jpg)
The information available about the Private Cloud Controller includes:
- **Active Connections to App Connectors**: The number of active connections the Private Cloud Controller had to App Connectors for the point in time listed.
- **Active Connections to Public Service Edges**: The active connection the Private Cloud Controller had to ZPA Public Service Edges for the point in time listed.
- **Available Disk Space**: The size of available disk space for the Private Cloud Controller at the point in time listed.
- **Bytes Received from the Public Service Edge**: The number of received bytes from Public Service Edges to the Private Cloud Controller in the selected time range.
- **Bytes Transmitted to the Public Service Edge**: The number of transmitted bytes to Public Service Edges from the Private Cloud Controller in the selected time range.
- **CPU Utilization**: The highest CPU used by the ZPA Public Service Edge for the time range selected.
- **Logs Failed to be Transmitted to SIEM**: The total number of logs that failed to be transmitted to the SIEM.
- **File Descriptor Utilization**: The file descriptors used by the ZPA Public Service Edge for the point in time listed.
- **Memory Utilization**: The highest memory used by the Private Cloud Controller for the selected time range.
- **Logs Successfully Transmitted to SIEM**: The total number of logs successfully transmitted to the SIEM.
- **TCP IPv6 Port Utilization: **The number of TCP ports for IPv6 used by the Private Cloud Controller for the point in time listed. It does not show Private Cloud Controllers using TCP ports for IPv4.
- **TCP Port Utilization**: The number of TCP ports for IPv4 used by the Private Cloud Controller for the point in time listed. It does not show Private Cloud Controllers using TCP ports for IPv6.
- **UDP IPv6 Port Utilization: **The number of UDP ports for IPv6 used by the Private Cloud Controller for the point in time listed. It does not show Private Cloud Controllers using TCP ports for IPv4.
- **UDP Port Utilization**: The number of UDP ports for IPv4 used by the Private Cloud Controllers for the point in time listed. It does not show Private Cloud Controllers using UDP ports for IPv6.
- **Zscaler Client Connector Redirections to Private Service Edges**: The number of Zscaler Client Connector redirects to the ZPA Private Service Edges.
[]The Activity Monitor section displays the same widgets with the same functionality as seen in the [Activity Monitor](#ActivityMonitorWidgets) section. Three widgets are selected automatically:
- Available Disk Space
- CPU Utilization
- Memory Utilization
[]The latency monitor widgets on the Latency tab show the latency trend from a ZPA Public Service Edge to a Private Cloud Controller in the selected time range. The time range for the Latency tab is different from the rest of the Private Cloud Controllers dashboard. It is limited to data over a period between **30 Mins** to **24 Hours**, or you can select **Custom Range** to specify a custom start and end date. If you use Custom Range, the start date can be within the last 24 hours. This filter applies to all widgets in the Latency tab, and the default time is 30 minutes.
The widgets available are:
- Private Cloud Controller to Default Gateway TCP Latency
- Private Cloud Controller to Public Service Edge Latency
Each widget shows the ZPA Public Service Edges that interact with the selected Private Cloud Controller during the time range. The widgets have the same functionality as seen in the [Activity Monitor](#ActivityMonitorWidgets) section.
For each widget, you can search by entering part or all of a Private Cloud Controller name, or by using the following search query options with >, <, or = operators:
- Location: The location of the Private Cloud Controller (e.g., location = San Jose).
- Name: The name of the Private Cloud Controller (e.g., name = sj_serviceedge).
- Value: A numerical value specific to the widget (e.g., value < 40).
![Latency Tab on the Private Controllers Dashboard](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-latency-tab-tools.jpg)
[]![Viewing the labels for each data point within the Activity Monitor widgets](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-monitor-widget.jpg)
[]![Select a part of a chart ](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-select-part-of-monitor-widget.jpg)
[]![Zoom Out of a chart on the Private Cloud Controllers Dashboard](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-zoom-out.jpg)
[]![Search and Deselect Private Cloud Controllers in Widgets](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-search-and-select-monitor-widget.jpg)
[]![Filter Private Cloud Controllers on the Private Cloud Controllers Dashboard in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-filters.jpg)
[]![Number of Private Cloud Controller Groups in the Private Cloud Controller Group filter](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-groups-filter.jpg)
[]![Actions for the Private Cloud Controller Details table](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-details.jpg)
[]![Details and Latency Tabs for Private Cloud Controllers in the Private Cloud Controllers Dashboard](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-details-view-default.jpg)
[]![Private Cloud Controller Tools](/downloads/zpa/dashboard-diagnostics/private-cloud-controller-monitoring/viewing-private-cloud-controllers-dashboard/zpa-pcc-dashboard-tools.jpg)