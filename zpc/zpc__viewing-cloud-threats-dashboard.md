# Viewing the Cloud Threats Dashboard
Source: https://help.zscaler.com/zpc/viewing-cloud-threats-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1394176.pdf

The Cloud Threats Dashboard offers visibility of alerts based on the threat category defined by ZPC for your cloud deployment. The threat category includes the following:
- Security Event: Alerts triggered for security events that have already occurred in the cloud deployment such as crypto mining, suspicious activity, etc.
- Security Exposure: Alerts triggered for potential exposure to security events such as dormant accounts, authentication misconfiguration, etc.
To learn more about alerts, see [About Alerts](/zpc/about-alerts).
On the Cloud Threats Dashboard page (Dashboard > Cloud Threats), you can do the following:
- Filter identities by the following parameters:
- **Business Units**: Select one or multiple business units. Business units are logical groups of multiple cloud accounts.
- **Clouds**: Select one or multiple cloud service providers for which you want to view assets.
- **Accounts**: Select one or multiple cloud accounts for which you want to view cloud assets.
- **Regions**: Select one or multiple regions for which you want to view cloud assets.
- View the **Alerts Lifecycle** information:
- **Alerts by Risk Level**: View open low, medium, high, and critical alerts with an assigned theme of Security Events or Security Exposure (Threat Category) for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, last 90 days, or last 180 days).
The Cloud Identities trend is a cumulative chart: the sum of local, federated, and external identities is the total number of open alerts.
- **Alert Detection and Fix Rate**: View new and resolved or closed alerts with an assigned theme of Security Events or Security Exposure (Threat Category) for the selected duration (last 7 days, last 15 days, last 30 days, last 60 days, last 90 days, or last 180 days).
- View **Security Event & Attack Vector Alerts**:
- **Security Event Category**: View alert count for security events which might have already occurred in your cloud deployment such as account takeovers or cryptocurrency mining. Select a security event category to view related security event trend and the top policies.
- **Alerts Trend**: View all the alerts for the selected security event category for the last 7 days.
- **Top Policies**: View the top 5 policies related to the security event category with the highest number of alerts.
- View **Security Exposure Alerts**:
- **Security Exposure Alert Category**: View alert count for potential exposure to security events such as privilege escalation or external exposure.
- **Exposure Trend**: View all the alerts for the selected security exposure category for the last 7 days.
- **Top Policies**: View the top 5 policies related to the security exposure category with the highest number of alerts.
![View the Cloud Threats dashboard on ZPC](/downloads/zpc/dashboards/about-cloud-threats-dashboard/zpc-cloud-threats-db.png.png?1663751370)