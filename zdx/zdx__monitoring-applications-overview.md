# Monitoring the Applications Overview
Source: https://help.zscaler.com/zdx/monitoring-applications-overview
PDF: https://help.zscaler.com/pdf/com/en/1355811.pdf

The Applications Overview provides information about the applications users are accessing and the impact of those applications on your organization's digital experience.
[See image.](#image-appdashboard)
Overview Tools
The Applications Overview allows you to:
- **View performance data over time**: Use the Time Range filter to choose a specific time range to view data. The selected period applies to all data within the overview. The default time range is **2 Hours**.
- **Current**: View the most current ZDX Score captured within the previous 30 minutes.
- **2 Hours** to **48 Hours**: Specify a time interval between 2 hours and 48 hours as shown in the drop-down menu.
- **Custom**: Specify a custom time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
-
**Filter data**: Click the filters to select options for Departments, Zscaler Locations, User Groups, Geolocations, Location Groups, Last Mile ISPs, and Operating System. Each filter allows you to include or exclude individual options. Click **Select All Displayed** to select all options at once.
[See image.](#AllDisplayed)
- **Share a ZDX Snapshot**: Click **Share Snapshot **to capture a snapshot of the current state of the Applications Overview page. Share it with other ZDX users or admins for view-only access. To learn more, see [Sharing ZDX Snapshots](/zdx/sharing-zdx-snapshots).
- **Compare Applications**: Click the **Open in a New Tab** icon next to the application name to open the application page in a new tab. You can use this icon to open multiple applications and compare their details.
Filtering
To configure filters:
- Determine which options to include or exclude from each of the filter drop-down menus:
- **Departments**: Your departments, as defined in ZIA. To learn more, see [About Departments](/zia/about-departments).
- **Zscaler Locations**: Your locations, as defined in ZIA. To learn more, see [About Locations](/zia/about-locations).
- **User Groups**: The names of user groups in your organization.
- **Geolocations**: The geographic area where users accessed the applications.
- **Location Groups**: The names of groups based on location in your organization.
- **Last Mile ISPs**: The Internet Service Providers (ISPs) to which your users are connecting.
- **Operating System**: The operating system versions installed on user devices in your organization.
- Click **Apply** after completing your selections.
You can adjust the filters as needed, or remove all of your filter selections by clicking **Reset**.
Applications List
The table displays the following information about applications and the impact they have to the digital experience:
- [Applications](#apps)
- [ZDX Score Trend](#scoretrend)
- [Most Impacted Location](#impacted_location)
- [Most Impacted Region](#impacted_region)
- [Most Impacted Department](#impacted_department)
[]Evaluating Individual Application Details
For each application, you can click the name in the table to view more information about it. This includes the application score over time, the impact it has for different groups (e.g., regions, departments), and the probes that are tracking the status of the application. For Network applications that use a single Cloud Path probe, End-to-End Latency information is provided in place of Page Fetch Time to calculate the ZDX Score. To add a Network application, see [Adding a Custom Application](/zdx/adding-custom-application).
Any filters you select on the Applications Overview page remain in place after selecting an application. You can adjust the filters or remove all of your filter selections by clicking **Reset**. Similar to the Applications Overview page, you can also click **Share Snapshot **to capture a snapshot of the current state of the details page to share with other ZDX users or admins. To learn more, see [Sharing ZDX Snapshots](/zdx/sharing-zdx-snapshots).
[See image.](#Evaluating_Individual_Application_Details)
- [ZDX Score Over Time](#score_graph)
- [Page Fetch Time](#pagefetch)
- [End-to-End Latency](#netapp-latency)
- [Regions by ZDX Score](#RegionsbyZDXScoreMap)
- [Impacted Departments](#impacted_departments)
- [Impacted Regions](#impacted_regions)
- [Impacted Zscaler Locations](#impacted_locations)
- [Probe Status](#monitors)
[]The **Application** column provides a list of applications. These names are defined when you configure the application. To learn more, see [About Applications](/zdx/about-applications).
Any disabled applications are shown in gray, and deleted applications are indicated with a strikethrough on the application name.
Click a name to see more information about each application. To learn more, see [Evaluating Individual Application Details](/zdx/about-applications-dashboard#indivapp).
[]The **ZDX Score Trend** column shows the application's ZDX Score from 1–100, with 1 being the lowest and 100 being the highest. To learn more, see [About the ZDX Score](/zdx/about-zdx-score).
Along with the score is a small graph showing the rise and fall of the score for the selected time period. To see more information for a particular application, click the application name. To learn more, see [Evaluating Individual Application Details](/zdx/about-applications-dashboard#indivapp).
[]The **Page Fetch Time** graph tracks how long it takes the selected application to transfer the fetched page to the user during the selected time period. The time is tracked in milliseconds.
A line runs across the graph that indicates the 95th percentile, as identified by **P95**. It indicates that 95 percent of the fetch time is below this amount.
You can select a point on the graph to see the exact date and time, the application's fetch time at that point, and the 95th percentile fetch time for comparison. If there is a Web probe error at that time, it is also displayed in the tooltip. To learn more about Web probe errors, see [Web Probe Errors](/zdx/web-probe-errors).
![View Page Fetch Time in the Applications Dashboard](/downloads/zdx/analytics/applications/about-applications-dashboard/ZDX_PFT_weberrors2.png)
[]For custom Network applications that rely only on a single Cloud Path probe, the Page Fetch Time graph is replaced with the **End-to-End Latency** graph. This graph captures the average latency for probes in the Cloud Path within the selected time range, including a **P95 **line that measures the 95th percentile in milliseconds.
![End-to-End Latency graph for network applications](/downloads/zdx/analytics/applications/monitoring-applications-overview/zdx-cp-scoring-app-latency2.png)
[]The **Regions by ZDX Score** map takes the geographic locations of all users accessing the selected application and organizes the data for the score down to the city level for major cities around the world. This information is displayed in a map. You can zoom in and out of the map to better view regions of interest.
For each marked location on the map, you can see the name of the city, the ZDX Score, and the number of users while hovering the mouse over the marked spot. Click the **Details **icon (![Details icon within tooltip](/downloads/zdx/analytics/applications/about-applications-dashboard-draft-b/zdx-map-location-details-icon.png)
) to view user information in the Users Overview specific to the location.
![Location tooltip in the Regions by ZDX Score map](/downloads/zdx/analytics/applications/about-applications-dashboard/zdx-map-location-tooltip.png)
[]Drawing a Fence
Within the **Regions by ZDX Score** map, you can filter the data seen on the map by creating a fence.
To draw a fence:
- Adjust the map to an area you want to view, and click **Draw Fence**.
- Select a portion of the map. A window with the number of locations selected appears.
[See image.](#fence_filter)
- Click **Filter Selection**. The impacted departments, regions, and Zscaler locations are updated accordingly at the bottom of the map.
To redraw the fence, click **Clear Selection** in the map. To move the map and select another region, click **Reset** above the map.
[See image.](#clear_fence)
Map Functionality
The following is the functionality in the **Regions by ZDX Score** map in the Applications details page:
![Details icon within tooltip](/downloads/zdx/analytics/applications/about-applications-dashboard-draft-b/zdx-map-location-details-icon.png)
| Map Interaction | Results |
| --------------- | ------- |
| Hover over a pin | View a tooltip that shows the geolocation, ZDX Score, and number of users. Click the **Details **icon () to view user and location information in the Users Overview. |
| Double-click a pin | Zoom into the city level of a region/state/country. |
| Draw a fence around a pin and then click **Filter Selection** | View a table that shows the location, users, and ZDX Score. |
| Zoom in/out on a pin | Zoom closer to or farther from the city/region/state/country. |
| Drag the map | Data is displayed per the map boundary. No additional interaction or data is loaded. |
| Click **Filter Unknown Locations** | The impacted departments, regions, and Zscaler locations are updated for unknown locations. |
[]The **Most Impacted Location** column lists the location most impacted by the application. Locations are ones your organization defined in ZIA. To learn more, see [About Locations](/zia/about-locations).
[]The **Most Impacted Region** column lists the region most impacted by the application. These areas are where users are accessing the application.
ZDX uses a device's location service to determine a user's location. It takes the longitude and latitude coordinates from the location service and compares them to Zscaler's geographic IP database. That information is then listed, by corresponding major cities and towns, in the ZDX Admin Portal.
If a user's latitude and longitude are closer to the center of another city, instead of their own city, the user's location might be misidentified as connecting from the neighboring city. If the location service is not enabled on the device, then ZDX uses the device's IP address to determine the location.
ZDX currently supports Windows, macOS, Android, Android on ChromeOS, and iOS devices only.
[]The **Most Impacted Department** column lists the department most impacted by the application. Departments are ones your organization defined in ZIA. To learn more, see [About Departments](/zia/about-departments).
[]The **ZDX Score Over Time** graph shows how the ZDX Score trends over the selected time period for the chosen application. To learn more, see [About the ZDX Score](/zdx/about-zdx-score).
The overall score tracks as a line across the graph. Scores fall into three classifications:
- **Good**: The score is above an acceptable threshold and ranges from 66–100. The color for this range is green.
- **Okay**: The score is acceptable and ranges from 34–65. The color for this range is amber.
- **Poor**: The score is below an acceptable threshold and ranges from 0–33. The color for this range is red.
You can select a point on the graph to see the exact date, time, and ZDX Score for that period.
A **Zoom In **(+) icon appears as you hover over the **ZDX Score Over Time** graph. Use this icon to select the time period to zoom in for greater detail. This shows the ZDX Score graph over that smaller time period and the Page Fetch Time graph also reflects the same period of time.
The time limit to zoom in is 5 minutes. Click **Zoom out** to view the original graphs.
![View ZDX Score Over Time Graph in the Applications Dashboard](/downloads/zdx/analytics/applications/about-applications-dashboard/ZDX_zdxscoreovertime_Zoomout2.png)
[]The departments with the lowest ZDX Score in relation to the application are listed in a chart by score with the lowest score at the top.
This allows you to compare how different departments are scoring in relation to each other with use of the application. When you click a department, the Users Overview page is displayed where you can view more granular details such as the total number of active devices, ZDX score distribution, and more.
[]The regions with the lowest ZDX Score in relation to the application are listed in a chart by score with the lowest score at the top.
This allows you to compare how different regions are scoring in relation to each other with use of the application.
[]The Zscaler locations with the lowest ZDX Score in relation to the application are listed in a chart by score with the lowest score at the top.
This allows you to compare how different locations are scoring in relation to each other with use of the application.
[]For each application, you can see the metrics that previously configured probes are tracking. Each probe has the parameters it uses to evaluate the application with the relevant data. Minimum, average, and maximum values are provided for all the users in a given timeframe. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
The Probe Status shown is unique to either Web probes or Cloud Path probes:
- [Probe Status for Web Probes](#probe-status-web)
- [Probe Status for Cloud Path Probes](#probe-status-cp)
[]The following image shows metrics calculated for a Web probe:
![Probe Status for Web probes](/downloads/zdx/analytics/applications/about-applications-dashboard/zdx-app-overview-app-probe-status-web-details.png)
[]The following image shows metrics calculated for a Cloud Path probe:
![Probe Status for Cloud Path probes](/downloads/zdx/analytics/applications/about-applications-dashboard/zdx-app-overview-app-probe-status-cp-details.png)
[]![Applications Overview page](/downloads/zdx/analytics/applications/monitoring-applications-dashboard/zdx-application-overview-generic-list6.png)
[]![Example of application details page](/downloads/zdx/analytics/applications/monitoring-applications-dashboard/zdx-application-overview-app-details-page6.png)
[]![Example of drawing a fence on the ZDX Score map](/downloads/zdx/analytics/applications/about-applications-dashboard/zdx-map-draw-fence2.png)
[]![Redraw a fence in the Regions by ZDX Score map](/downloads/zdx/analytics/applications/about-applications-dashboard/zdx-app-overview-redraw-fence.png)
[]![Filter drop-down in the Applications Dashboard](/downloads/zdx/analytics/applications/monitoring-applications-dashboard/zdx-app-overview-filter-location-groups4.png)