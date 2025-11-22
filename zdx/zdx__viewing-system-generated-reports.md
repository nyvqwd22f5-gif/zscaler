# Viewing System-Generated Reports
Source: https://help.zscaler.com/zdx/viewing-system-generated-reports
PDF: https://help.zscaler.com/pdf/com/en/1456566.pdf

System-generated reports allow you to view user data across your organization that can reveal distinctive patterns among various metrics and applications. Details for each report are aggregated day-to-day and most reports are captured in a rolling 14-day cycle.
Prerequisites
To access and view system-generated reports, ensure:
- Your ZDX subscription level supports viewing system-generated reports. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- Your admin role is configured to view system-generated reports. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Accessing Reports
You can access the reports from the left-side navigation of the ZDX Admin Portal:
- Go to **Analytics **>** System-Generated Reports**.
- Select the report name or click the **View **icon to access a report.
Use the search field to find a specific report. Search for any character string that might be part of the report name.
The report table provides the following information:
- **Name**: The name of the system-generated report.
- **Type**: Indicates the report is predefined.
- **Application**: Indicates either a particular application or all applications.
- **Data Source**: Specifies which data is captured (**All Cloud Path**, **All Web Probes**, **All Devices**).
- **Metrics**: Identifies the type of metrics reflected in the report.
- **Last Updated On**: Indicates the date and time when the report was revised.
![View a list of predefined system-generated reports](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-1.png)
Viewing Report Details
View details for each of the following system-generated reports:
- [Cloud Path: End-to-End](#sgr-cp)
- [Last Mile ISP Performance](#sgr-isp)
- [DNS Performance](#sgr-dns)
- [Application Performance](#sgr-app)
- [ZDX Score by Application](#sgr-score)
- [Wi-Fi Distribution](#sgr-wifi)
- [Active Users by Zscaler Destination](#sgr-active-users)
- [Top Users with Poor ZDX Scores](#sgr-top-users)
- [Probe Assignments](#sgr-probe-assignments)
[]The Cloud Path: End-to-End report captures the average latency in the Cloud Path within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, **Geolocations**, or **Applications**. You can hide the filters or reset your selection.
Similar to other system-generated reports, you can view a more granular time range:
- Select a point in the graph. A tooltip displays the latency metrics for the selected locations.
- Drag your mouse from left-to-right to capture your time range. The graph automatically adjusts to show the latency within the new timeline.
- Click **Zoom Out** to reset the graph back to the original view.
Up to 20 device locations are displayed at a time within the legend on the right side of the graph, based on user device information. Each location is color-coded to correspond to its trend line within the graph, with the number of devices per location included in parentheses. A minimum of one location is always displayed. The P95 line is calculated based on the latency of the selected locations.
![Example report for end-to-end latency in the Cloud Path](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-End-End-Latency.png)
[]The Last Mile ISP Performance report captures ISP latency within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, or **Geolocations**. You can hide the filters or reset your selection.
Similar to other system-generated reports, you can view a more granular time range:
- Select a point in the graph. A tooltip displays the latency metrics for the selected ISPs.
- Drag your mouse from left-to-right to capture your time range. The graph automatically adjusts to show the latency within the new timeline.
- Click **Zoom Out** to reset the graph back to the original view.
Up to 20 ISPs are displayed at a time within the legend on the right side of the graph, based on the ISPs to which your users are connecting. Each ISP is color-coded to correspond to its trend line within the graph. A minimum of one ISP is always displayed.
![Example report for ISP latency](/downloads/zdx/analytics/viewing-system-generated-reports/zdx-static-reports-isp2.png)
[]The DNS Performance report captures the average DNS latency within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, **Geolocations**, or **Applications**. You can hide the filters or reset your selection.
Similar to other system-generated reports, you can view a more granular time range:
- Select a point in the graph. A tooltip displays the latency metrics for the selected locations.
- Drag your mouse from left-to-right to capture your time range. The graph automatically adjusts to show the latency within the new timeline.
- Click **Zoom Out** to reset the graph back to the original view.
Up to 20 device locations are displayed at a time within the legend on the right side of the graph, based on user device information. Each location is color-coded to correspond to its trend line within the graph, with the number of devices per location included in parentheses. A minimum of one location is always displayed.
![Example report for average DNS latency](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-DNS-Performance.png)
[]The Application Performance report captures the daily distribution of ZDX Scores within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, **Geolocations**, or **Applications**. You can hide the filters or reset your selection.
On hover, the graph shows the count and percentage of users with a corresponding ZDX Score level for the selected application. To learn more about the range of ZDX Scores, see [About the ZDX Score](/zdx/about-zdx-score).
![Example report for Application Performance](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Application-Performance.png)
[]The ZDX Score by Application report captures the average ZDX Score per application within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, or **Geolocations**. You can hide the filters or reset your selection.
Similar to other system-generated reports, you can view a more granular time range:
- Select a point in the graph. A tooltip displays the ZDX Scores for all active applications selected on the right-side of the graph.
- Drag your mouse from left-to-right to capture your time range. The graph automatically adjusts to show the latency within the new timeline.
- Click **Zoom Out** to reset the graph back to the original view.
Up to 20 applications are displayed at one time on the right side of the graph, based on available applications. Each application is color-coded to correspond to its trend line within the graph. A minimum of one application is always displayed. To learn more about the range of ZDX Scores, see [About the ZDX Score](/zdx/about-zdx-score).
![Report for ZDX Score by Application](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-ZDX-Score-Application.png)
[]The Wi-Fi Distribution report captures the daily distribution of ZDX Scores within a 14-day time range.
Filter by **Departments**, **Zscaler Locations**, or **Geolocations**. You can hide the filters or reset your selection.
On hover, the graph shows the device count per Wi-Fi band and its percentage from the total number of user devices across your organization.
![Report that shows the device distribution per Wi-Fi band](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Wi-Fi-Distribution-0.png)
[]The Active Users by Zscaler Destination report captures the current distribution of active users and devices per Zscaler destination.
Filter by **Departments**, **Zscaler Locations**, or **Geolocations**. You can hide the filters or reset your selection.
On hover, the graph shows the user and device counts within a 2-hour time range.
![Example report for Active Users by Zscaler Destination](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Active-Users-Distribution.png)
Switch views between the graph or list view. You can view up to 100 destinations within the table.
![Example report for Active Users by Zscaler Destination in table format](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Active-Users-List.png)
[]The Top Users with Poor ZDX Scores report captures the top 100 users within a 14-day time range who have the lowest Poor ZDX Scores, based on the selected application.
Filter by **Departments**, **Zscaler Locations**, **Geolocations** or **Applications**. You can hide the filters or reset your selection.
The report provides the following information:
- **User**: Click the user to view details. To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
- **ZDX Score**: The value of the user's Poor ZDX Score.
- **Zscaler Location**: The location of the user. To learn more, see [About Locations](/zdx/about-locations).
- **Geolocations**: The geographic area where the user is located.
- **Device**: The user device.
- **# Probe Runs**: The number of times probes were run for the selected application within the 14-day timeline.
![View the top users with poor ZDX Scores](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Top-Users.png)
[]The Probe Assignments report captures the number of enabled probes assigned to a given user in a 24-hour time range based on probe usage.
To access Probe Assignments, ensure you have the [appropriate permission](/zdx/adding-zdx-roles#ProbeAssignments).
The report provides the following:
- Filter by **User Name**, **User Groups**, **Location Groups**, **Departments**, **Zscaler Locations**, or **Geolocations**. You can hide the filters or reset your selection.
- In the summary section, you can view:
- **Total Enabled Probes**: The total number of enabled probes with an active application.
- **Total User**: The total number of impacted users assigned to enabled probes. You can also view the percentage of impacted users and a trend chart of total users.
- **Probe Usage**: The number of devices assigned to a number of enabled probes. You can click one of the sections of the bar to filter for the report. The probe ranges are **0-10**, **11-20**, **21-25**,** **or **>25**. The default filter is **>25**.
- In the **Users** list, you can:
- Download a CSV file of impacted users.
- Search for an impacted user.
- View a list of impacted users with the following details:
- **User Name**: The impacted username.
- **Department**: The department associated with the username. To learn more, see [About Departments](/zdx/about-departments).
- **Zscaler Location**: The location of the impacted user. To learn more, see [About Locations](/zdx/about-locations).
- **Geolocation**: The geographical location of the impacted user.
- **Device Count**: The number of impacted devices.
- **Active Probes**: The number of active probes assigned to the impacted user.
If the report query finds more than 1,000 impacted users, then the report displays the first 1,000 users. Use filters to narrow down your results or download a CSV file to view all impacted users.
![View Probe Assignments report to identify number probes assigned to a user](/downloads/zdx/analytics/viewing-system-generated-reports/ZDX-System-Generated-Reports-Probe-Assignments.png)