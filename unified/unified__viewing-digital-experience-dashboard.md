# Viewing the Digital Experience Dashboard
Source: https://help.zscaler.com/unified/viewing-digital-experience-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1497891.pdf

The Digital Experience dashboard provides an overview of your organization's digital experience in terms of user, devices, applications, and unified communication experience, as well as overall network activity and latency.
Filtering
-
**Time Range**: Use the Time Range filter in the upper right to choose a specific time range between 2 hours and 48 hours in which to view data. Select **Custom** to select a specific time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
The selected period applies to all data within the dashboard. The default time range is **2 Hours**.
-
**Filter data**: Click the filters in the top left to limit the data shown. Each filter allows you to include or exclude individual options.
- **Departments**: Your departments. To learn more, see [About Departments](/unified/about-departments).
- **Zscaler Locations**: Your locations. To learn more, see [About Locations](/unified/about-locations).
- **User Groups**: The names of user groups in your organization.
- **Geolocations**: The geographic areas where your users are located.
Click **Apply** to update the dashboard with your selections. To remove all filter selections, click **Reset**.
Dashboard Widgets
- [How is My Overall Digital Experience?](#digital-experience)
- [Network Latency Geoview](#network-latency)
- [Application Experience](#app-experience)
- [Unified Communication Experience](#comm-experience)
- [What is Impacting My User Experience?](#impact)
- [End Point Self Service](#self-service)
[]This bar graph indicates how many of the applications in your organization are in each of the Digital Experience score categories. Initially, the score represents all users in your organization, across all applications, all locations, and all cities. Depending on the time period and filters selected within the dashboards, the score adjusts accordingly.
The digital experience score categories are:
- **Good**: The score is above an acceptable threshold and ranges from 66-100. The color for this range is green.
- **Okay**: The score is acceptable and ranges from 34-65. The color for this range is amber.
- **Poor**: The score is below an acceptable threshold and ranges from 0-33. The color for this range is red.
Click **View Activity** to view more detail about the users, devices, and applications that contribute to the score on the [Activity Dashboard](/unified/viewing-activity-dashboard).
To learn more about the Digital Experience score (also called the ZDX Score), see [About the Digital Experience Score](/unified/about-zdx-score).
[See image.](#digital-experience-image)
[]This widget shows the average network latency from user locations to one of three locations on the network. You can toggle among:
- **Zscaler**: Latency to Zscaler data center
- **DNS Resolution**: Latency to the DNS server
- **Last Mile ISP**: Latency to the closest ISP node
Click a dot on the map to filter latency to that location. The dot colors correspond to the digital experience scores of good (green), okay (amber), and poor (red).
[See image.](#network-latency-image)
[]This table shows the performance of applications in your organization. The most commonly used applications are shown in the list. Click **View All Applications** to see a list of all applications on the [Applications Dashboard](/unified/viewing-applications-dashboard-0).
[See image.](#app-experience-image)
[]This widget shows the performance of meeting applications in your organization. The circle graph shows the overall Digital Experience score for all meetings. The most recent meetings are shown in the list. Click **View All Meetings** to see a list of all meetings on the [Meetings Dashboard](/unified/viewing-meetings-dashboard).
[See image.](#comm-experience-image)
[]This widget shows the impact of incidents that have affected digital experience, including the total number of incidents, the number of users affected, and the devices, networks, and applications affected. The most recent incidents are shown in the list. Click the link in the Networking box to expand to show all areas in your network (Wi-Fi, DNS, ISP, etc.) Click **View All Incidents **to see a list of all incidents on the [Incidents Dashboard](/unified/viewing-incidents-dashboard).
[See image.](#impact-image)
[]This widget shows the total number of notifications sent, the number of unique users notified, and the types of notificaations sent to your users about issues requiring attention. Click **View Self Service** to see more information about user notifications on the [Self Service Dashboard](/unified/viewing-self-service-dashboard).
[See image.](#self-service-image)
[]![Bar graph showing How is My Digital Experience on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-overall.png)
[]![Network Latency map on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-nw-latency.png)
[]![Application Experience table on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-application-exp.png)
[]![Unified Communication Experience widget on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-unicomm-exp.png)
[]![What is Impacting my User Experience? widget on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-impact.png)
[]![End Point Self Service table on the Digital Experience dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-digital-experience-dashboard/digital-exp-endpoint-ss.png)