# Monitoring the Performance Dashboard
Source: https://help.zscaler.com/unified/monitoring-performance-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1493876.pdf

The Performance Dashboard (Analytics > Digital Experience Management > Dashboard > Performance Dashboard) provides an overview about Zscaler Digital Experience Monitoring.
[See image.](#About_ZDXDashboard)
Dashboard Tools
The Performance Dashboard allows you to:
- **View performance data over time**: Use the Time Range filter to choose a specific time range to view data. The selected period applies to all data within the dashboard. The default time range is** 2 Hours**.
- **Current**: View the most current ZDX Score captured within the previous 30 minutes.
- **2 Hours** to **48 Hours**: Specify a time interval between 2 hours and 48 hours as shown in the drop-down menu.
- **Custom**: Specify a custom time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
-
**Filter data**: Click the filters to select options for Departments, Zscaler Locations, User Groups, Geolocations, Location Groups, Last Mile ISPs, and Operating System. Each filter allows you to include or exclude individual options. Click **Select All Displayed** to select all options at once.
[See image.](#AllDisplayed)
Click the drop-down menu option to choose locations in the **Geolocations** filter. This hierarchical display includes the continent, country, states, and cities within the US, while non-US geolocations show the continent, countries, and then cities. Click **Reset** on the right side of the page to reset your selection.
[See image.](#ActiveGeolocationFilter)
Filtering
To configure filters:
- Determine which options to include or exclude from each of the filter drop-down menus:
- **Departments**: Your departments, as defined in Internet & SaaS. To learn more, see [About Departments](/unified/about-departments).
- **Zscaler Locations**: Your locations, as defined in Internet & SaaS. To learn more, see [About Locations](/unified/about-locations).
- **User Groups**: The names of user groups in your organization.
- **Geolocations**: The geographic areas where your users are located.
- **Location Groups**: The names of groups based on location in your organization.
- **Last Mile ISPs**: The Internet Service Providers (ISPs) to which your users are connecting.
- **Operating System**: The operating system versions installed on user devices in your organization.
- Click **Apply** after completing your selections.
You can adjust the filters as needed or remove all of your filter selections by clicking **Reset**.
Widgets
The Performance Dashboard provides the following widgets:
- [Most Impacted Applications](#impactedapp)
- [Regions by ZDX Score Map](#geozdx)
- [ZDX Score Graph](#score-graph)
- [Page Fetch Time](#pagefetch)
- [End-to-End Latency](#ee-latency)
[]The Most Impacted Applications are the applications with the lowest score for the selected time period. If there are more than three applications, scroll left or right to see more.
The dashboard preselects the application with the lowest score, and the rest of the page automatically tracks information based on that application. By selecting another application, the page adjusts to reflect information based on the newly selected application.
Each application shows:
- **ZDX Score**: The score represents the total experience of all users in your organization for all locations during the selected time period. The score is based on a scale of 1 (lowest) to 100 (highest), with the lowest numbers indicating a poor score and highest numbers indicating a good score. To learn more, see [About the ZDX Score](/unified/about-zdx-score).
- **Most Impacted Location**: The location with the worst digital experience for that application during the selected time period.
- **Total Users**: The number of users interacting with the application during the selected time period.
Any disabled applications are shown in gray, and deleted applications are indicated with a strikethrough on the application name:
![Examples of disabled and deleted applications](/downloads/zdx/analytics/about-zdx-dashboard/zdx-dd-app-cards.png)
You can investigate what is causing a low score through the Applications Overview by clicking the name of the application. To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
[]The **Regions by ZDX Score** map takes the geographic locations of all users accessing the selected application and organizes the data for the score down to the city level for major cities around the world. This information is displayed in a map. You can zoom in and out of the map to better view regions of interest.
Digital Experience Monitoring uses a device's location service to determine a user's location. It takes the longitude and latitude coordinates from the location service and compares it to Zscaler's geographic IP database. That information is then displayed in the Admin Portal in a map with major cities and towns.
If a user's latitude and longitude are closer to the center of another city, instead of their own city, the user's location might be misidentified as connecting from the neighboring city. If the location service is not enabled on the device, then Digital Experience Monitoring uses the device's IP address to determine the location.
Digital Experience Monitoring currently supports Windows, macOS, Android, and Chrome devices only (e.g., desktop, laptop).
For each marked location on the map, you can see the name of the city, the ZDX Score, and the number of users while hovering the mouse over the marked spot. Click the **Details **icon (![Details icon within tooltip](/downloads/zdx/analytics/about-zdx-dashboard-draft-b/zdx-map-location-details-icon.png)
) to view user information in the Users Overview specific to the location.
![City information in tooltip of the Regions by ZDX Score map](/downloads/zdx/analytics/about-zdx-dashboard/zdx-map-location-tooltip.png)
The ZDX Score falls into one of [three classifications](#three-class): Good, Okay, or Poor.
To see more about a city or a set of cities, you can set up a fence on the map. To learn more, see [Drawing a Fence](#draw).
[]Drawing a Fence
Within the **Regions by ZDX Score** map, you can filter the data seen on the map by creating a fence.
To draw a fence:
- Adjust the map to an area you want to view, and click **Draw Fence**.
- Select a portion of the map. A window with the number of locations selected appears.
[See image.](#fence_filter)
- Click **Filter Selection**. A list of the locations within the fence appears at the bottom of the map.
- (Optional) Deselect any locations in the **Custom fence** table you do not want to use in a filter.
- Click **View in Users Page** to see data filtered by these locations. The [Users Overview](/unified/monitoring-users-overview) appears with data relevant only to those locations.
After applying the fence, you can also go to the [Applications Overview](/unified/monitoring-applications-overview) or return to the Performance Dashboard and the location fence remains as part of your filters.
To redraw the fence, click **Clear Selection** in the map or **Clear Fence** at the bottom of the **Regions by ZDX Score **map. To move the map and select another region, click **Reset** above the map.
[See image.](#clear_fence)
Unknown Locations
[]The Unknown Locations widget is visible in the bottom-left corner of the map when a user location is determined to be unknown. Use this widget to filter the users from unknown locations and view their details. If there are no users from unknown locations, this widget is not visible.
![Map shows widget for Unknown Locations](/downloads/zdx/analytics/about-zdx-dashboard/zdx-map-location-unknown2.png)
To use the Unknown Locations widget:
- Click **Filter Unknown Locations**. A **Custom fence** table appears that lists the unknown locations, the users, and their ZDX Scores. Click **Clear Fence **to clear the filter.
- Select the unknown locations as desired and then click **View in Users Page** to apply the **Unknown Locations** filter.
- The number of users from unknown locations and their ZDX Scores are visible in the Users Overview and Applications Overview.
Map Functionality
The following is the functionality in the **Regions by ZDX Score **map in the Performance Dashboard:
![Details icon within tooltip](/downloads/zdx/analytics/about-zdx-dashboard-draft-b/zdx-map-location-details-icon.png)
| Map Interaction | Results |
| --------------- | ------- |
| Mouse over a pin | View a tooltip that shows the geolocation, ZDX Score, and number of users. Click the **Details **icon () to view user and location information in the Users Overview. |
| Zoom in/out on a pin | Zoom closer to or farther from the city/region/state/country. |
| Double-click a pin | Zoom into the city level of a region/state/country. |
| Drag the map | Data is displayed per the map boundary. No additional interaction or data is loaded. |
| Draw a fence around a pin and then click **Filter Selection** | View a table that shows the location, users, and ZDX Score. |
[]The **ZDX Score **graph shows how the ZDX Score trends over the selected time period.
[]The overall score tracks as a line across the graph. Scores fall into three classifications:
- **Good**: The score is above an acceptable threshold and ranges from 66–100. The color for this range is green.
- **Okay**: The score is acceptable and ranges from 34–65. The color for this range is amber.
- **Poor**: The score is below an acceptable threshold and ranges from 0–33. The color for this range is red.
The graph also tracks the score of the most impacted application, as determined by the applied filters, for comparison. This lets you view the application's impact on the overall score.
For comparison, you can select up to four additional applications by clicking **Add Another Application** in the application selector below the graph. In the drop-down menu, select the additional applications to view. The ZDX Score for the selected applications is displayed. Clicking a point in the graph displays the ZDX Score for the selected applications at that time; you can also click the arrow within the display to go to that application page. To remove an application, deselect it in the application selector. Selections made in the application selector for the ZDX Score are also reflected in the Page Fetch Time graph.
![Example of ZDX Score graph](/downloads/zdx/analytics/monitoring-zdx-dashboard/zdx-score-add-another-application3.png)
[]The **Page Fetch Time** graph tracks how long it takes the selected application to transfer the fetched page to the user during the selected time period. The time is tracked in milliseconds.
A line runs across the graph that indicates the 95th percentile, as identified by **P95**. It indicates that 95 percent of the fetch time is below this amount.
You can select a point on the graph to see the exact date and time, the application's fetch time at that point, and the 95th percentile fetch time for comparison. To explore more about the application, click **Analyze** to view the Applications Overview and filter by the application. To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
For comparison, you can select up to four additional applications by clicking **Add Another Application** in the application selector below the graph. In the drop-down menu, select the additional applications to view. The Page Fetch Time for the selected applications is displayed. Clicking a point in the graph displays the Page Fetch Time for the selected applications at that time; you can also click the arrow within the display to go to that application page. To remove an application, deselect it in the application selector. Selections made in the application selector for the Page Fetch Time are also reflected in the ZDX Score graph.
[See image.](#ZDXDashboard_PageFetchTime)
[]The **End-to-End Latency **graph captures the average latency for probes in the Cloud Path within the selected time range. This graph replaces the Page Fetch Time graph if you've selected a Network application under [Most Impacted Applications](#impactedapp). Network applications do not have a web front end, and therefore, ZDX Scores are calculated using latency with only a single Cloud Path probe.
You can view additional Network applications within the graph by selecting **Add Another Application**. However, you cannot add other custom applications or predefined applications.
[See image.](#ZDXDashboard_eelatency)
[]![Performance Dashboard](/downloads/zdx/analytics/monitoring-zdx-dashboard/zdx-os-filter-perf-overview3.png)
[]![Example of drawing a fence on the ZDX Score map](/downloads/zdx/analytics/monitoring-zdx-dashboard/zdx-map-draw-fence2.png)
[]![Shows buttons to clear fence in a Regions by ZDX Score map](/downloads/zdx/analytics/about-zdx-dashboard/zdx-map-location-fence2.png)
[]![Example of Page Fetch Time graph](/downloads/zdx/analytics/about-zdx-dashboard/ZDX_PageFetchtime2.png)
[]![End-to-End Latency graph on Performance Dashboard](/downloads/zdx/analytics/monitoring-performance-dashboard/zdx-cp-scoring-perf-latency.png)
[]![Example of Geolocations filter drop-down in Performance Dashboard](/downloads/zdx/analytics/monitoring-performance-dashboard/zdx-geo-filter-flatlist5.png)
[]![Filter drop-down in Performance Dashboard](/downloads/zdx/analytics/monitoring-zdx-dashboard/zdx-perf-overview-select-all-options5.png)