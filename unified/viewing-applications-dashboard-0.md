# Viewing the Applications Dashboard
Source: https://help.zscaler.com/unified/viewing-applications-dashboard-0
PDF: https://help.zscaler.com/pdf/com/en/1498746.pdf

The Applications dashboard provides an overview of application performance in your organization.
Filtering
-
**Time Range**: Use the Time Range filter in the upper right to choose a specific time range between 2 hours and 48 hours in which to view data. Select **Custom** to select a specific time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
The selected period applies to all data within the dashboard. The default time range is **2 Hours**.
-
**Filter data**: Click the filters in the top left to limit the data shown. Each filter allows you to include or exclude individual options.
- **Applications**: Applications used in your organization.
- **Departments**: Your departments. To learn more, see [About Departments](/unified/about-departments).
- **Zscaler Locations**: Your locations. To learn more, see [About Locations](/unified/about-locations).
- **User Groups**: The names of user groups in your organization.
- **Geolocations**: The geographic areas where your users are located.
- **Location Groups**: The names of groups based on location in your organization.
- **Last Mile ISPs**: The Internet Service Providers (ISPs) to which your users are connecting.
- **Operating System**: The operating system versions installed on user devices in your organization.
Click **Apply** to update the dashboard with your selections. To remove all filter selections, click **Reset**.
Dashboard Widgets
- [Application Experience Trend](#app-experience)
- [Applications](#app-list)
[]This widget shows the trend of the digital experience score for all applications in your organization. Initially, the score represents applications across your organization for the default time range of 2 hours. Depending on the time period and filters selected within the dashboards, the score adjusts accordingly. The score represents all users in your organization, across all applications, all locations, and all cities. Depending on the time period and filters selected within the dashboards, the score adjusts accordingly.
The score falls into one of three categories:
- **Good**: The score is above an acceptable threshold and ranges from 66-100. The color for this range is green.
- **Okay**: The score is acceptable and ranges from 34-65. The color for this range is amber.
- **Poor**: The score is below an acceptable threshold and ranges from 0-33. The color for this range is red.
Click **View Activity** to view more detail about the users, devices, and applications that contribute to the score on the Activity dashboard.
To learn more about the Digital Experience score, see [About the Digital Experience Score](/unified/about-zdx-score).
[See image.](#app-experience-image)
[]This table provides a detailed list of the applications being used in your organization for the selected filters.
- **Application Name**: The name of the application.
- **Type**: The type of application, either Internet or Private.
- **Score**: The ZDX score of the application.
- **Departments**: The number of departments where the application is used.
- **Regions**: The number of regions where the application is used.
- **Locations**: The number of locations where the application is used.
Click any application row in the table to see additional detail about that application:
- [ZDX Score](#scoretrend)
- [Page Fetch Time](#pagefetch)
- [Regions by ZDX Score](#RegionsbyZDXScoreMap)
- [Impacted Departments](#impacted_departments)
- [Impacted Regions](#impacted_regions)
- [Impacted Zscaler Locations](#impacted_locations)
- [Probe Status](#monitors)
[See image.](#app-list-image)
[]The **ZDX Score Trend** column shows the application's ZDX Score from 1–100, with 1 being the lowest and 100 being the highest. To learn more, see [About the ZDX Score](/unified/about-zdx-score).
[]The **Page Fetch Time** graph tracks how long it takes the selected application to transfer the fetched page to the user during the selected time period. The time is tracked in milliseconds.
A line runs across the graph that indicates the 95th percentile, as identified by **P95**. It indicates that 95 percent of the fetch time is below this amount.
You can select a point on the graph to see the exact date and time, the application's fetch time at that point, and the 95th percentile fetch time for comparison. If there is a Web probe error at that time, it is also displayed in the tooltip. To learn more about Web probe errors, see [Web Probe Errors](/unified/web-probe-errors).
[]The **Regions by ZDX Score** map takes the geographic locations of all users accessing the selected application and organizes the data for the score down to the city level for major cities around the world. This information is displayed in a map. You can zoom in and out of the map to better view regions of interest.
For each marked location on the map, you can see the name of the city, the ZDX Score, and the number of users while hovering the mouse over the marked spot. Click the **Details **icon (![Details icon within tooltip](/downloads/zdx/analytics/applications/about-applications-dashboard-draft-b/zdx-map-location-details-icon.png)
) to view user information in the Users Overview specific to the location.
[]The **Impacted Departments** table shows the departments with the lowest ZDX Score for this application.
The departments are listed by score with the lowest score on top. This allows you to compare how different departments are scoring in relation to each other with use of the application.
[]The **Impacted Regions **widget shows the regions with the lowest ZDX Score for this application.
The regions are listed in a chart by score with the lowest score at the top. This allows you to compare how different regions are scoring in relation to each other with use of the application.
[]The **Impacted Locations** widget shows the Zscaler locations with the lowest ZDX Score for this application.
The Zscaler locations are listed in a chart by score with the lowest score at the top. This allows you to compare how different Zscalerlocations are scoring in relation to each other with use of the application. To learn more, see [About Locations](/unified/about-locations).
[]For each application, you can see the metrics that previously configured probes are tracking. Each probe has the parameters it uses to evaluate the application with the relevant data. Minimum, average, and maximum values are provided for all the users in a given timeframe. To learn more, see [Configuring a Probe](/unified/configuring-probe).
The Probe Status shows metrics for either a Web probes or a Cloud Path probe.
[]![Bar graph showing Application Experience Trend on the Applications dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-applications-dashboard-0/apps-exp-trend.png)
[]![Table showing Applications on the Applications dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-applications-dashboard-0/apps-list.png)