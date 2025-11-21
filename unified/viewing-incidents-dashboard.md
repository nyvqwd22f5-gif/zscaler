# Viewing the Incidents Dashboard
Source: https://help.zscaler.com/unified/viewing-incidents-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1498766.pdf

The Incidents dashboard provides an overview of incidents affecting your organization.
Filtering
-
**Time Range**: Use the Time Range filter in the upper right to choose a specific time range between 2 hours and 48 hours in which to view data. Select **Custom** to select a specific time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
The selected period applies to all data within the dashboard. The default time range is **2 Hours**.
- **Type**: Filter incidents by type. Available types are **Device**, **Wi-Fi**, **DNS**, **Last Mile ISP**, **Intermediate ISP**, **Zscaler**, and **Application**.
Dashboard Widgets
- [Total Incidents/Incidents Across Key Areas](#incidents-total)
- [Incidents Over Time/Impacted Users Over Time](#incidents-over-time)
- [Incidents by Epicenters](#incidents-epicenters)
- [Incidents](#incidents-list)
[]You can view the total incidents and the total counts across the key metrics and impacted users.
- **Total Incidents**: The total number of incidents detected within a time range.
- **Impacted Users**: The number of impacted users from the total incidents within a time range.
-
**Incidents Across Key Areas**: The distribution of incidents in critical parts of the infrastructure.
Click the number, icon, or text under each key area to filter specifically for the selected incident type.
[See image.](#incidents-total-image)
[]This widget contains bar charts showing the number of incidents for the specified time range and type and the number of impacted users from the incidents for the specified time range and type. If there are no impacted users, no data is shown.
[See image.](#incidents-over-time-image)
[]This map displays the incidents that have occurred for the specified time range and type. Incidents are displayed using icons to represent the types of incident. After an incident is positioned on the map in an area, an epicenter is defined at the center of the incident. Click an icon to view more information.
[See image.](#incidents-epicenters-image)
[]This table provides a detailed list of incidents for the specified time range and type.
- **Incident Type**: The type of incident.
- **Epicenter**: Represents the center of the incident depending on the type.
- **Users Impacted**: The number of users impacted by the incident.
- **Start Time**: The date and time the incident started.
- **End Time**: The date and time the incident ended.
- **Duration**: The duration of the incident.
[See image.](#incidents-list-image)
Click any incident row in the table to see additional detail about that incident:
- [Incident Details/Impact](#incident-details)
- [Impacted Users by Geolocations](#impacted-geo)
- [Top Impacted Users](#impacted-users)
- [Key Metrics](#key-metrics)
[]Provides an overview of the selected incident with the following details:
- **Type**: The type of incident.
- **Severity**: The level of severity of the incident.
- **Epicenter**: Represents the center of the incident depending on the type.
- **Started On**: The date and time the incident started.
- **Ended On**: The date and time the incident ended.
- **Duration**: The duration of the incident.
The Impact section shows the number of users, geolocations, and applications impacted.
[See image.](#incident-details-image)
[]A map showing the geolocations of impacted users. You can zoom in and out of the map to better view regions of interest.
[See image.](#impacted-geo-image)
[]A list of the Top Impacted Users. Click **View All Impacted Users** to view and verify more impacted users.
The Top Impacted Users list displays up to 11 impacted users.
[See image.](#impacted-users-image)
[]Displays key metrics based on the Incident type.
- [Wi-Fi](#key-metrics-wifi)
- [Last Mile ISP](#key-metrics-isp)
- [Internet & SaaS Public Service Edge](#key-metrics-ispse)
- [Private Applications Public Service Edge](#key-metrics-papse)
- [Application](#key-metrics-application)
[See image.](#key-metrics-image)
[]Application Key Metrics provide an overview of an application and its impacted users.
- **ZDX Score**: The Digital Experience score (also called the ZDX Score) of the application.
- **HTTP Errors**: The number of HTTP errors the application has encountered over time.
- **TTFB-PFT Ratio**: The ratio between the server response time (time to first byte) and the time to load the page (page fetch time).
- **Last Server Leg Latency**: The latency from the Public Service Edge to the application.
- **Number of Redirects**: The number of redirections going through the application over time.
[]Depending on if it's a Blackout or Brownout, you get different key metrics.
- [Blackout](#key-metrics-blackout)
- [Brownout](#key-metrics-brownout)
[]Wi-Fi key metrics provide an overview of the signal strength and latency of Wi-Fi access points.
- **ZDX Score Drop**: The Digital Experience score variation through the Wi-Fi access point.
- **Maximum Wi-Fi Access Point Latency**: The maximum Wi-Fi Access Point Latency.
- **Average Wi-Fi Access Point Latency**: The average Wi-Fi Access Point Latency.
- **Packet Loss at Wi-Fi Access Point (Hop 1)**: The packet loss at the first Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 2)**: The packet loss after the 1st Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 3)**: The packet loss after the 2nd Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 4)**: The packet loss after the 3rd Wi-Fi Access Point.
- **Wi-Fi Signal Strength**: The average signal strength of users going through the Wi-Fi Access Point.
[]Internet and SaaS Public Service Edge key metrics provide an overview on ZIA transactions, connectivity, and latency for impacted users.
- **ZDX Score for Impacted Users**: The Digital Experience score for Impacted Users is calculated across each impacted user and their aggregated score from all their configured applications.
- **First Hop Latency around PSE**: The time calculated, from the Public Service Edge (PSE) perspective, across all the users going through the affected Zscaler Data Center.
- **Second Hop Latency around PSE**: The average Second Hop Latency, from the PSE perspective, across all the users going through the affected Zscaler Data Center.
- **ZIA Transactions**: Displays the number of Zscaler Internet Access (ZIA) transactions going through the affected Zscaler Data Center.
- **ZIA Connectivity Errors**: Displays the number of errors connecting to the affected Zscaler Data Center.
- **Cloud Path Probe Errors**: The number of Cloud Path probe errors at the Zscaler Data Center.
- **Web Probe Errors**: The number of Web probe errors at the Zscaler Data Center.
[]Private Applications Public Service Edge key metrics provide an overview on ZPA traffic, connectivity, and latency for impacted users.
- **ZDX Score**: The Digital Experience score (also called the ZDX Score) is calculated across each impacted user and their aggregated score from all their configured applications.
- **First Hop Latency around ZPA**: The average First Hop Latency, from the Public Service Edge perspective, across all the users going through Private Applications.
- **Second Hop Latency around ZPA**: The average Second Hop Latency, from the Public Service Edge perspective, across all the users going through Private Applications.
- **Private Applications Public Service Edge Cloud Path Probe Errors**: The number of Public Service Edge errors at the Zscaler Data Center.
- **Private Applications Traffic for Current Week**: The number of Private Applications transactions that create Private Applications traffic for the current week.
- **Private Applications Traffic for Previous Week**: The number of Private Applications transactions that create Private Applications traffic for the previous week.
- **Private Applications Traffic for 2 Weeks Ago**: The number of Private Applications transactions that create Private Applications traffic for 2 weeks before the current week, excluding the current week.
- **Private Applications Traffic for 3 Weeks Ago**: The number of Private Applications transactions that create Private Applications traffic for 3 weeks before the current week, excluding the current week.
- **Private Applications Traffic for 4 Weeks Ago**: The number of Private Applications transactions that create Private Applications traffic for 4 weeks before the current week, excluding the current week.
- **Private Applications Public Service Edge Web Probe Errors**: The number of Private Applications Public Service Edge Web probe errors at the Zscaler Data Center.
[]Blackouts Key Metrics provides an overview of connectivity issues with an ISP.
- **Application Score**: The Digital Experience score of the application.
- **All Probe Errors**: The total number of probe errors.
- **DNS Resolution Time**: The amount of time it takes for a DNS to resolve DNS entries.
- **Cloud Path Probe Errors**: The number of Cloud Path probe errors.
[]Brownouts Key Metrics provides an overview of performance degradation with an ISP.
- **ZDX Score Drop**: The shaded region indicates the Digital Experience score drop for the Last Mile ISP incident.
- **DNS Latency**: The amount of time DNS takes to resolve for impacted users from the Last Mile ISP incident.
- **Leg Latency**: The latency for impacted legs from the Last Mile ISP incident.
- **Packet Loss**: The number of packets lost from the Last Mile ISP incident.
[]![Total Incidents/Incidents Across Key Areas widget on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-total.png)
[]![Incidents Over Time bar graph on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-over-time.png)
[]![Incidents by Epicenter map on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-epicenters.png)
[]![Table of Incidents on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-list.png)
[]![Incident Details widget on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-details.png)
[]![Impacted Users by Geolocation map on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-geolocation.png)
[]![Impacted Users widget on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-impacted-users.png)
The following is an example of a selected Wi-Fi Incident. Depending on the type of incident you have, different key metrics will be shown. []![Wi-Fi Key Metrics on the Incidents dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-incidents-dashboard/incidents-key-metrics.png)