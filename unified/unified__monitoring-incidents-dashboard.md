# Monitoring the Incidents Dashboard
Source: https://help.zscaler.com/unified/monitoring-incidents-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1493881.pdf

The Incidents Dashboard displays incidents in 6 area types: Device, Wi-Fi, Last Mile ISP, Internet & SaaS Public Service Edge, Private Applications, or Application. Incidents are issues that impact the device performance of multiple users. Digital Experience Monitoring uses AI and machine learning (ML) to detect and identify incidents using the best metrics that correlate to the issues. The incidents displayed are based on the selected time frame range in the UI and show incidents over time, impacted users, and where on the map they occur.
Prerequisites
To access the Incidents Dashboard (Analytics > Digital Experience Management > Dashboard > Incidents Dashboard), you must have the following:
- Your Digital Experience Monitoring subscription level supports Incidents. To learn more, see [Ranges and Limitations](/unified/ranges-limitations#analytics).
- View Only permission level for Incidents Dashboard. To learn more, see [About Digital Experience Monitoring Role-Based Administration](/unified/about-digital-experience-monitoring-role-based-administration).
Incidents Dashboard
Use the filters on the Incidents Dashboard page to narrow your scope of Incidents information.
- **Type**: Select the type for incidents. The types are Device, Wi-Fi, Last Mile ISP, ZIA Public Service Edge, ZPA, or Application.
- **Time Range**: Select a time range to view when incidents occurred. The default is 14 days.
You can view the total incidents and the total counts across the key metrics and impacted users.
- **Total Incidents**: The total number of incidents detected within a time range.
- **Impacted Users**: The number of impacted users from the total incidents within a time range.
-
**Incidents Across Key Areas**: The distribution of incidents across the key areas.
You can click the number, icon, or text under each key area to filter specifically for the selected Incident type.
[See image.](#Incidents-Overview-Summary)
If no incidents are found, try one of the following actions:
- Select a different time range.
- Remove filters.
- Apply different filters.
Incidents Over Time
The Incidents Over Time section displays data for incidents and impacted users to provide the following information:
- **Incidents Over Time**: The number of incidents that have occurred based on the impacted devices within a time range.
- **Impacted Users Over Time**: The number of impacted users from the incident over time. If there are no impacted users, no data is shown.
[See image.](#IncidentsTime)
Incidents By Epicenters
The Incidents By Epicenters displays all incidents that have occurred within the time range on a map. Different types of incidents: Device, Wi-Fi, Last Mile ISP, ZIA Public Service Edge, Private Applications, or Application are displayed using a different icon to represent the types of incidents occurring. After an incident is positioned on the map in an area, an epicenter is defined at the center of the incident.
You can review the Incidents by Epicenters list with the following information:
- **Type**: The types are Device, Wi-Fi, Last Mile ISP, ZIA Public Service Edge, ZPA, or Application.
- **Epicenter**: Represents the center of the incident. Depending on the type, the epicenter is displayed as:
- **Device**: The geographical area of impacted Windows devices with system software hangs and crashes.
- **Wi-Fi**: The geographical area of impacted service set identifiers (SSIDs).
-
**Last Mile ISP**: The geographical area of impacted users with the ISP.
- **Blackout**: A subtype of Last Mile ISP. The area of impacted users with connectivity issues on the Last Mile ISP.
- **Brownout**: A subtype of Last Mile ISP. The area of impacted users with a performance degradation on the Last Mile ISP.
Click **Last Mile ISP** under **Incidents Across Key Areas** or the **View** icon underneath the **Incidents by Epicenter** map to view what subtype of Last Mile ISP Incident occurred.
- **ZIA Public Service Edge**: The location of the Internet & SaaS Public Service Edge at the Zscaler Data Center.
- **ZPA**: The geographical area of impacted users with Private Applications.
- **ZPA App Connector**: The location of the Private Applications App Connector at the Zscaler Data Center.
- **ZPA Public Service Edge**: The location of the Private Applications Public Service Edge at the Zscaler Data Center.
- **Application**: The area of impacted users and can go across multiple countries.
- **Total User(s)**: The total number of users within the incident.
- **Impacted Users**: The number of impacted users within the incident.
- **Started On**: The date and time this incident started.
- **Ended On**: The date and time this incident ended.
- **View**: You view the selected incident for more granular details.
[See image.](#IncidentsEpicenter)
Viewing Incident Details
The Incident Details page provides granular information about a specific incident:
- [Incident Details](#IncidentDetails)
- [Impact](#Impact)
- [Impacted Users by Geolocations](#ImpactedUsersbyGeolocations)
- [Top Impacted Users](#TopImpactedUsers)
- [Key Metrics](#KeyMetrics)
Click Set Up Alert (![zdx-incidents-setup-alert.png](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-incidents-setup-alert.png)
) if you want to configure an alert rule for an incident. To learn more, see [Configuring an Alert Rule](/unified/configuring-alert-rule).
[See image.](#IndividualIncidentExample)
[]Provides an overview of the selected incident with the following details:
- **Type**: The type of incident.
- **Severity**: The level of severity of the incident.
- **Epicenter**: Represents the center of the incident depending on the type. Depending on the type, the epicenter is displayed as:
- **Device**: The geographical area of impacted Windows devices with system software hangs and crashes.
- **System Software Hangs**: A subtype of Device. The area of impacted Windows devices with system software hangs.
- **System Software Crashes**: A subtype of Device. The area of impacted Windows devices with system software crashes.
- **Wi-Fi**: The geographical area of impacted SSIDs. A Wi-Fi incident includes the selection of Wi-Fi Access Point information.
- **Last Mile ISP**: The geographical area of impacted users with the ISP.
- **Blackout**: A subtype of Last Mile ISP. The area of impacted users with connectivity issues on the Last Mile ISP.
- **Brownout**: A subtype of Last Mile ISP. The area of impacted users with a performance degradation on the Last Mile ISP.
- **ZIA Public Service Edge**: The location of the Internet & SaaS Public Service Edge at the Zscaler Data Center.
- **ZPA**: The geographical area of impacted users with Private Applications.
- **ZPA App Connector**: The location of the Private Applications App Connector at the Zscaler Data Center.
- **ZPA Public Service Edge**: The location of the Private Applications Public Service Edge at the Zscaler Data Center.
- **Application**: The area of impacted users and can go across multiple countries.
- **Started On**: The date and time the incident started.
- **Ended On**: The date and time the incident ended.
- **Duration**: The duration of the incident.
[See image.](#incidentDetails)
[]Displays the number of users, geolocations, and applications impacted.
- ![zdx-users.png](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-users.png)
: The number of impacted users.
- ![zdx-geolocations.png](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-geolocations.png)
: The number of impacted geolocations.
- ![zdx-application.png](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-application.png)
: The number of applications.
[]A map of the impacted users' geolocations. You can zoom in and out of the map to better view regions of interest.
[]A list of the Top Impacted Users. Click **View All Impacted Users** to view and verify more impacted users.
The Top Impacted Users list displays up to 11 impacted users.
[][]Displays key metrics based on the Incident type.
- [Device](#KeyMetrics-Device)
- [Wi-Fi](#KeyMetrics-Wi-Fi)
- [Last Mile ISP](#KeyMetrics-ISP)
- [ZIA Public Service Edge](#KeyMetrics-ZIAPublicServiceEdge)
- [ZPA](#KeyMetrics-ZPA)
- [Application](#KeyMetrics-Application)
[]There are two types of device incidents with different key metrics that provide analytical data of impacted Windows devices with anomalous behaviors that are caused by system software hangs or crashes:
- [System Software Hangs](#KeyMetrics-Device-System-Software-Hangs)
- [System Software Crashes](#KeyMetrics-Device-System-Software-Crash)
[]System Software Crashes key metrics provide analytical data of where impacted Windows devices experience no computer activity because the software has crashed.
- **Impacted OSs**: The distribution of impacted operating systems.
- **Impacted Software**: The distribution of impacted software.
- **CPU Usage**: The percentage of CPU usage for impacted Windows devices.
- **Memory Usage**: The percentage of memory usage for impacted Windows devices.
- **Event Trend**: The number of system software crashes for impacted Windows devices that occur over time.
[]System Software Hangs key metrics provide analytical data on where impacted Windows devices have become unresponsive to user input on applications despite ongoing computer activity.
- **Impacted OSs**: The distribution of impacted operating systems.
- **Impacted Software**: The distribution of impacted software.
- **CPU Usage**: The percentage of CPU usage for impacted Windows devices.
- **Memory Usage**: The percentage of memory usage for impacted Windows devices.
- **Event Trend**: The number of system software hangs for impacted Windows devices that occur over time.
[]Application Key Metrics provide an overview of an application and its impacted users.
- **ZDX Score**: The ZDX Score of the application.
- **HTTP Errors**: The number of HTTP errors the application has encountered over time.
- **TTFB-PFT Ratio**: The ratio between the server response time (time to first byte) and the time to load the page (page fetch time).
- **Last Server Leg Latency**: The latency from the Public Service Edge to the application.
- **Number of Redirects**: The number of redirections going through the application over time.
[]Depending on if it's a Blackout or Brownout, you get different key metrics.
- [Blackout](#KeyMetrics-Blackout)
- [Brownout](#KeyMetrics-Brownouts)
[]Wi-Fi Key Metrics provide an overview of the signal strength and latency of Wi-Fi access points.
- **ZDX Score Drop**: The ZDX Score variation through the Wi-Fi access point.
- **Maximum Wi-Fi Access Point Latency**: The maximum Wi-Fi Access Point Latency.
- **Average Wi-Fi Access Point Latency**: The average Wi-Fi Access Point Latency.
- **Packet Loss at Wi-Fi Access Point (Hop 1)**: The packet loss at the first Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 2)**: The packet loss after the 1st Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 3)**: The packet loss after the 2nd Wi-Fi Access Point.
- **Packet Loss after Wi-Fi Access Point (Hop 4)**: The packet loss after the 3rd Wi-Fi Access Point.
- **Wi-Fi Signal Strength**: The average signal strength of users going through the Wi-Fi Access Point.
[]Internet & SaaS Public Service Edge provides an overview on Internet & SaaS transactions, connectivity, and latency for impacted users.
- **ZDX Score for Impacted Users**: The ZDX Score for Impacted Users is calculated across each impacted user and their aggregated ZDX Score from all their configured applications.
- **First Hop Latency around PSE**: The time calculated, from the Public Service Edge (PSE) perspective, across all the users going through the affected Zscaler Data Center.
- **Second Hop Latency around PSE**: The average Second Hop Latency, from the PSE perspective, across all the users going through the affected Zscaler Data Center.
- **ZIA Transactions**: Displays the number of Internet & SaaS transactions going through the affected Zscaler Data Center.
- **ZIA Connectivity Errors**: Displays the number of Internet & SaaS errors connecting to the affected Zscaler Data Center.
- **Cloud Path Probe Errors**: The number of Cloud Path probe errors at the Zscaler Data Center.
- **Web Probe Errors**: The number of Web probe errors at the Zscaler Data Center.
[]Depending on the Service Edge, you get different key metrics.
- [ZPA App Connector](#KeyMetrics-ZPAAppConnector)
- [ZPA Public Service Edge](#KeyMetrics-ZPAPublicServiceEdge)
[]ZPA App Connector key metrics provides an overview of Private Applications App Connector traffic, connectivity, and latency for impacted users.
- **ZDX Score**: The ZDX Score is calculated across each impacted user and their aggregated ZDX Score from all their configured applications.
- **First Hop Latency Around ZPA**: The average First Hop Latency across all the users going through Private Applications.
- **Second Hop Latency Around ZPA**: The average Second Hop Latency across all the users going through Private Applications.
- **ZPA App Connector Cloud Path Probe Errors**: The number of Cloud Path probe errors at the Zscaler Data Center.
[]Private Applications Public Service Edge provides an overview of Private Applications Public Service Edge traffic, connectivity, and latency for impacted users.
- **ZDX Score**: The ZDX Score is calculated across each impacted user and their aggregated ZDX Score from all their configured applications.
- **First Hop Latency around ZPA**: The average First Hop Latency, from the Public Service Edge perspective, across all the users going through Private Applications.
- **Second Hop Latency around ZPA**: The average Second Hop Latency, from the Public Service Edge perspective, across all the users going through Private Applications.
- **ZPA Public Service Edge Cloud Path Probe Errors**: The number of Cloud Path probe errors at the Zscaler Data Center.
- **ZPA Public Service Edge Web Probe Errors**: The number of Private Applications Public Service Edge Web probe errors at the Zscaler Data Center.
[]Blackouts Key Metrics provides an overview of connectivity issues with an ISP.
- **Application Score**: The ZDX Score of the application.
- **All Probe Errors**: The total number of probe errors.
- **DNS Resolution Time**: The amount of time it takes for a DNS to resolve DNS entries.
- **Cloud Path Probe Errors**: The number of Cloud Path probe errors.
[]Brownouts Key Metrics provides an overview of performance degradation with an ISP.
- **ZDX Score Drop**: The shaded region indicates the ZDX Score Drop for the Last Mile ISP incident.
- **DNS Latency**: The amount of time DNS takes to resolve for impacted users from the Last Mile ISP incident.
- **Leg Latency**: The latency for impacted legs from the Last Mile ISP incident.
- **Packet Loss**: The number of packets lost from the Last Mile ISP incident.
[]![Incidents Overview Summary](/downloads/zdx/analytics/monitoring-incidents-dashboard/Incidents%20Overview%20Summary.png)
[]![Incidents over Time](/downloads/zdx/analytics/monitoring-incidents-dashboard/Incidents%20Over%20Time%20-%20mock-up.png)
[]![Incidents by Epicenter](/downloads/zdx/analytics/monitoring-incidents-dashboard/Incidents%20by%20Epicenter%20-%20mock-up.png)
[]
Depending on the type of incident you have, you have different key metrics. The following is an example of a selected Device incident with a subtype of System Software Crashes.
![Application Incident](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-incidents-devices-systemsoftwarecrashes.png)
[]
![Incident Details](/downloads/zdx/analytics/monitoring-incidents-dashboard/zdx-incidents-individual-incident-details.png)
[]Understanding Incident Type Metrics and Thresholds
Each incident type has a different set of metrics and thresholds to monitor specific device behaviors. These metrics and thresholds are predetermined to provide insights into your organization's impacted devices.
In order to be considered an incident, the following must be considered to categorize the event as an incident:
- Incident: The incident type or subtype.
- Minimum Devices: The minimum number of impacted devices with bad scores.
- Dimensions: The dimensions that determine an impacted area.
- Key Metrics: The [key metrics](#UnderKeyMetrics) to describe the incident's digital experience.
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Type - Subtype | Minimum Devices | Dimensions | Key Metrics |
| -------------- | --------------- | ---------- | ----------- |
| Application | 50 | CountryApplication | ZDX ScoreHTTP errorsTTFB-PFT RatioLast Server Leg LatencyNumber of redirectsTTFB:PFT ratio |
| Last Mile ISP - Blackout | 20 | GeohashISP | Application ScoreAll Probe ErrorsDNS Resolution TimeCloud Path Probe Errors |
| Last Mile ISP - Brownout | Minimum 10 across all customersMinimum 5 per customer | GeohashISP | ZDX Score DropDNS LatencyLeg LatencyPacket Loss |
| ZIA Public Service Edge | Minimum 100 across all customersMinimum 10 per customer | ZIA Data Center | ZDX Score for Impacted UsersFirst Hop Latency around SMESecond Hop Latency around SMEZIA TransactionsZIA Connectivity ErrorsCloud Path Probe ErrorsWeb Probe Errors |
| Wi-Fi | 4 | ZIA LocationSSID | ZDX ScoreFirst Hop Latency around ZPASecond Hop Latency around ZPAZPA App Connector Cloud Path Probe Errors |
| ZPA - App Connector | Minimum 10 per customer per App Connector | App Connector | ZDX ScoreFirst Hop Latency around ZPASecond Hop Latency around ZPAZPA App Connector Cloud Path Probe Errors |
| ZPA - Public Service Edge | Minimum 100 across all customersMinimum 10 per customer | ZPA Data Center | ZDX ScoreFirst Hop Latency around ZPASecond Hop Latency around ZPAZPA Public Service Edge Cloud Path Probe ErrorsZPA Public Service Edge Web Probe Errors |
| Device - System Software Crash | 50 | Devices | Impacted OSsImpacted SoftwareCPU UsageMemory UsageEvent Trend |
| Device - System Software Hang | 50 | Devices | Impacted OSsImpacted SoftwareCPU UsageMemory UsageEvent Trend |