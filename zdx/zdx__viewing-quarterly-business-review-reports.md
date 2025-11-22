# Viewing Quarterly Business Review Reports
Source: https://help.zscaler.com/zdx/viewing-quarterly-business-review-reports
PDF: https://help.zscaler.com/pdf/com/en/1458626.pdf

Quarterly Business Review (QBR) reports are available for download to ZDX users of all subscription levels. The reports can help provide insight into emerging traffic trends and the types of threats that Zscaler is blocking to protect your network. You can access the reports from the **Analytics **icon in the left-side navigation of the ZDX Admin Portal. To learn more, see [Downloading Quarterly Business Review Reports](/zdx/downloading-quarterly-business-review-reports).
You must have a minimum of 100 active devices for 30 days to generate and view QBR reports.
Viewing the QBR Reports
Each report provides the following information:
- [Quarterly Snapshot](#qbr-snapshot)
- [Where Are Your End Users](#qbr-endusers)
- [Incidents Overview](#qbr-incidents)
- [Network Incidents Overview](#qbr-nw-incidents)
- [Top ISPs by Users](#qbr-isp)
- [Application Incident Overview](#qbr-app-incidents)
- [End-to-End ZDX Score](#qbr-ee-score)
- [Average DNS Resolution Time](#qbr-avg-dns)
- [Average Latency from Source Network](#qbr-avg-latency)
- [Alerts Overview](#qbr-alerts)
- [Wi-Fi Analysis](#qbr-wifi)
- [Device Analysis](#qbr-device-analysis)
- [License Comparison](#qbr-license)
[]Shows a quarterly snapshot of your Application ZDX Score, Network Average Latency, and Users Monitored. To determine the score for an application, Zscaler identifies all the users that accessed the application for the calendar quarter, and then finds the lowest value each user experienced for the application. The average value is used to determine the application's ZDX Score for the quarterly snapshot.
[]Shows a geospatial distribution of each user's footprint around the world by visualizing where your users are located.
[]Shows a monthly overview of your incidents compared to the previous 6 months. An incident is an event that disrupts operational processes and isn't part of normal operations. For example, an incident occurs when there is an impact involving more than a normal or acceptable percentage of users in a department or region for one or more services. An incident might also involve the failure of a feature or service that should have been delivered.
[]Shows a monthly overview of your network incidents by network type and Internet Service Provider (ISP), compared to the previous 6 months.
[]Shows a monthly performance overview of your top ISPs by your users. Performance is calculated by the average time taken by the Egress router at the user’s location to reach the ISP.
[]Shows a monthly overview of your application incidents by application type, compared to the previous 6 months.
[]Shows a monthly overview of your application-specific ZDX Scores compared to the previous 6 months. To determine the score for an application, Zscaler identifies all the users that accessed the application for the calendar quarter, and then finds the lowest value each user experienced for the application. The lowest values for each user are added together and divided by the number of users. This is the application's ZDX Score for the end-to-end application experience.
[]Shows a monthly overview and your average DNS resolution time by location, compared to the previous 6 months. Any metric under 100ms is considered acceptable.
[]Shows a monthly overview of the average latency from your source network to Zscaler, by geolocation and user distribution, compared to the previous 6 months.
[]Shows a monthly overview and trend of alerts triggered, along with the average remediation time for an alert. If you have a high level of incidents, enable alerting in ZDX to help with monitoring and triage.
[]Shows device counts for the quarter that reflect Wi-Fi connectivity versus wired connectivity.
[]Shows monthly device counts per operating systems, event names, and models across the organization.
[]Shows a matrix that delineates ZDX feature support for Standard, M365, Advanced, and Advanced Plus subscriptions.