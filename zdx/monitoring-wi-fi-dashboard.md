# Monitoring the Wi-Fi Dashboard
Source: https://help.zscaler.com/zdx/monitoring-wi-fi-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1503411.pdf

The Wi-Fi Dashboard utilizes existing user and device Wi-Fi data in your organization to monitor device performance. This data can help identify specific locations in which users might have issues with their Wi-Fi access points.
Prerequisites
To monitor Wi-Fi performance within the Wi-Fi Dashboard, ensure:
- Your ZDX subscription level supports monitoring the Wi-Fi Dashboard. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your ZDX role has the proper permission level. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Viewing the Wi-Fi Dashboard
To access the Wi-Fi Dashboard, go to **Dashboard **> **Wi-Fi Dashboard**. Time range options are available in increments from the previous **2 Hours** to **48 Hours**, or a **Custom Range** within the last 14 Days. Use the time range filter and page filters to help narrow your scope of information:
- **Wi-Fi SSID**: The network Service Set Identifier. You can select up to 5 SSIDs from the drop-down menu. The SSID associated with the highest number of devices is selected by default.
- **Departments**: See [About Departments](/zdx/about-departments).
- **Zscaler Locations**: See [About Locations](/zdx/about-locations).
- **Geolocations**: The geographic areas where your users are located.
- **Operating System**: The operating system versions installed on user devices in your organization.
- **Vendors**: Supported Wi-Fi vendors.
- **AP Prefix**: Enter up to 6 prefixed characters to filter access points.
Certain OSs (i.e., macOS, Windows 11), with the latest updates, do not enable [Zscaler Client Connector's privacy settings](/zscaler-client-connector/configuring-zscaler-client-connector-collect-zdx-location-information) by default. When Zscaler Client Connector's **Collection Location Info for ZDX** is not enabled, privacy information for Wi-Fi details, such as SSID and BSSID, are not captured in the Wi-Fi Dashboard.
![View an overview about Wi-Fi access points on the Wi-Fi Dashboard](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/ZDX-Wi-Fi-Dashboard-1.png)
View details about the distribution and performance of Wi-Fi access points and connected devices:
- **Total Access Points**: The current number of active access points with a percentage increase or decrease over the selected time period.
- **Wi-Fi Performance of Access Points**: A performance distribution based on Good, Okay, and Poor ZDX Scores. Hover over the bar chart to view the performance distribution.
- **Total Devices Connected**: The current number of active devices with a percentage increase or decrease over the selected time period.
- **ZDX Score Distribution**: The distribution of Good, Okay, and Poor ZDX Scores for all connected devices. Hover over the bar chart to view the device count distribution.
- **Wi-Fi Band Distribution**: The estimated number of total active devices delineated by Wi-Fi band percentage. The device count is duplicated for any device using more than one Wi-Fi band at a given time.
- **Top Geolocations by Devices Connected**: The top 5 geolocations with the highest device counts, along with the distribution of their respective ZDX Scores.
- Click an individual location to launch a [consolidated view](#consolidated-ap) of its Wi-Fi access points.
- Hover over the **Score Distribution** bar chart to view a device count per ZDX Score.
- **Wi-Fi Performance by Geolocation**: The SSID performance distribution via location. You can switch between **Map View** or **List View**. The **Map View** is the default view.
- On the **Map View**, you can:
- View color-coded locations to reflect the Wi-Fi performance of devices in that location.
- Hover over a Wi-Fi location to launch a tooltip with Wi-Fi and device details.
- Click **View Access Points** within the tooltip to launch a [consolidated view](#consolidated-ap) of Wi-Fi access points within the location.
-
On the **List View**, you can see the following information:
- **Name**: The name of the Wi-Fi access point.
- **Wi-Fi Performance**: The category of Wi-Fi performance for the Wi-Fi access point (**Good**, **Poor**).
- **Access Points**: The number of access points at the location.
- **Connected Devices**: The total number of connected devices at the location.
- **Poor ZDX Score Devices**: The number of poor ZDX Score devices at the location.
- **% Poor ZDX Score Devices**: The percentage of poor ZDX Score devices at the location.
[See image.](#wi-fi-perf-location-list-view)
Optionally, you can configure your Wi-Fi data collection to use signal strength and retransmission rate to identify low-performing Wi-Fi devices instead of ZDX Score. To learn more, see [Configuring Inventory Settings](/zdx/configuring-inventory-settings#Wi-Fi).
To learn more about ZDX Score categories, see [About the ZDX Score](/zdx/about-zdx-score).
[]Viewing Wi-Fi Access Points
You have the option to display a consolidated view of access points in either a **Tree View** or **List View**.
Access Points in Tree View
The default Tree View of a location's access points is color-coded according to Wi-Fi performance, with each tile color based on a ZDX Score. The size of each tile is based on user volume, with the largest user count shown on the left side of the page, and the lowest user count shown towards the right side of the page.
[See image.](#ap-color-tree)
Hover over an access point tile to view the following information:
- The number of users and devices connected to the access point.
- The latency and jitter metrics for the access point.
- A link to [view granular details](#ap-details-page-view) about the access point.
-
A link to optionally customize the access point info.
[See image.](#customize-ap)
Access Points in List View
Click **List View** to display the Wi-Fi access points in a tabular format that provides the following information:
[See image.](#ap-list-view)
- **MAC Address**: The access point identifier.
- **Custom Name**: If applicable, the customized name for the access point.
- **Wi-Fi Performance**: The ZDX Score rating as Good, Okay, or Poor.
- **Number of Users**: The total count of active users connected to the access point.
- **Number of Devices**: The total count of active devices connected to the access point.
- **Avg Latency**: The average latency of the access point, measured in milliseconds.
- **Avg Jitter**: The average jitter of the access point, measured in milliseconds.
Click an access point to view its details. You can also click the **Edit **icon to customize the access point info.
[]Viewing Access Point Details
The access point details page provides a brief summary of a selected access point:
- **SSID**: The network Service Set Identifier for the access point.
- **Location**: The geographic location of the access point.
- **Wi-Fi Performance**: The ZDX Score rating as Good, Okay, or Poor.
- **AP MAC**: The MAC address of the access point.
- **Access Point Info**: The renamed or customized access point, or the link to add info to customize the access point.
- **Devices**: The number of devices within the access point location.
[See image.](#ap-details-page)
Key Metrics
Salient metrics are provided for the access point in the following charts:
- **Source to Gateway Latency**: The average time for a data packet to travel from the source device to the gateway within the selected time range.
- **Source to Gateway Jitter**: The average variation in latency between data packets traveling from the source device to the gateway within the selected time range.
- **Active Users**: The number of active users and devices connected to the access point within the selected time range.
A table that identifies each user connected to the access point provides additional Wi-Fi information. Click a user or device name within the table to view details about each entry.
- **Device**: A user's device connected to the access point.
- **User**: A user connected to the access point.
- **BSSID**: The Basic Service Set Identifier.
- **Wi-Fi Adapter**: The adapter brand of the access point.
- **ZDX Score**: The score for the device connected to the access point.
- **Signal Strength**: The average Wi-Fi signal strength of the device.
- **Wi-Fi Type**: The wireless communication standard of the access point.
- **Wi-Fi Channel**: The channel number associated with the band frequency.
- **OS**: The device's operating system.
[]![Access point details page](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/ZDX-Wi-Fi-Details.png)
[]![Tree view of access points](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/zdx-wifi-dash-tree-view.png)
[]![Customizing an access point](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/zdx-wifi-dash-customize-ap.png)
[]![View a list of Wi-Fi access points](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/zdx-wifi-dash-list-view.png)
[]
![View details about the Wi-Fi Performance by Locations in List View](/downloads/zdx/analytics/monitoring-wi-fi-dashboard/ZDX-Wi-Fi-Dashboard-ListView_0.png)