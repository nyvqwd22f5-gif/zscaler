# Understanding the Alert Email
Source: https://help.zscaler.com/zdx/understanding-alerts-email
PDF: https://help.zscaler.com/pdf/com/en/1364566.pdf

Alert notifications are sent via email if this option is chosen when configuring the alert rule. To learn more, see [Configuring a Rule](/zdx/configuring-rule).
The alert email shows the following:
- **Alert Criteria Triggers**: These are the criteria selected when the alert rule was configured. If one or more alert criteria are met, then it is highlighted.
- **Alert Start Time**: This indicates the alert start time and if the alert has ended, then the alert end time is indicated. If the alert end time has not ended, then it indicates Ongoing.
- **Alert Rule**: The name of the alert rule. Click the name of the alert rule to view further details in the ZDX Admin Portal.
- **Alert Severity**: The level of severity for this alert rule.
- **Impacted**: The impacted Geolocations, Departments, OS Versions, and Devices. If the alert has ended, then devices are no longer listed.
[See image.](#email)
Click **View Alert** to view further details in the ZDX Admin Portal.
Incident Alert Email
If you configure alerts for incidents, the alert email shows the following:
- **Alert Criteria Triggers**: These are the criteria selected when the alert rule was configured. If one or more alert criteria are met, then it is highlighted.
- **Incident Type**: The type of incident (e.g., Application, Last Mile ISP).
-
**Epicenter**: The impacted epicenter displays where the center of the incident is.
For example, if the incident type is Application, then the epicenter shows the area of impacted users. To learn more, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
- **Alert Timeline**: This indicates the alert start time and if the alert has ended, then the incident end time is indicated. If the incident has not ended, then it indicates **Ongoing** in the **Incident Status** and no end time is shown.
- **Alert Rule**: The name of the alert rule. Click the name of the alert rule to view further details in the ZDX Admin Portal.
- **Impacted**: The impacted Geolocations, Devices, and Users. If the alert has ended, then devices are no longer listed.
[See image.](#inc)
Call Quality Alert Email
If you configure alerts for call quality, the alert email shows the following:
- **Alert Criteria Triggers**: These are the criteria selected when the alert rule was configured. If one or more alert criteria are met, then it is highlighted.
- **Alert Timeline**: This indicates the alert start time and if the alert has ended, then the incident end time is indicated. If the incident has not ended, then it indicates **Ongoing** in the **Incident Status** and no end time is shown.
- **Alert Rule**: The name of the alert rule. Click the name of the alert rule to view further details in the ZDX Admin Portal.
- **Alert Severity**: The level of severity of this alert rule.
- **Impacted**: The impacted Geolocations, Departments, Meetings, and Users.
[See image.](#cq)
[]
[![Sample Alert Email ](/downloads/zdx/alerts/understanding-alerts-email/zdx-alert-email-template.png)
]
[]
![Incident alert email sent after alert conditions are met](/downloads/zdx/alerts/understanding-alerts-email/ZDX-Alert-Email-Incident.png)
[]
![Call quality alert email is sent after alert conditions are met](/downloads/zdx/alerts/understanding-alerts-email/ZDX-Alert-Email-CallQuality.png)