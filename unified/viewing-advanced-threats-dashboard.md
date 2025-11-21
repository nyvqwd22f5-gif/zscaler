# Viewing the Advanced Threats Dashboard
Source: https://help.zscaler.com/unified/viewing-advanced-threats-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1498791.pdf

The Advanced Threats dashboard provides an overview of cybersecurity threats in your organization.
Filtering
- **Time Range**: Use the Time Range filter in the upper right to choose a specific time range between **1 Day** and **90 Days** in which to view data. The selected period applies to all data within the dashboard. The default time range is **14 Days**.
- **Threat Category**: Select the categories of threat you want to include or exclude:
- [Threat Categories](#threat-categories)
Dashboard Widgets
- [Incoming Real Time Threats](#incoming-threats)
- [Advanced Threat Incidents](#advanced-threat-incidents)
[]This line graph shows the number of incidents recorded for the selected time period. Hover over a date in the graph to see the total number of incidents for that date and the breakdown among the threat categories.
[See image.](#incoming-threats-image)
[]This table provides a detailed list of threat incidents for the specified time range and type.
- **Name**: The name of the threat incident.
- **Category**: The threat category (e.g. **Spyware**, **Phishing**, etc.)
- **Impacted Systems**: The number of systems affected by the incident.
- **Status**: The action taken on the threat, e.g. **Allowed **or **Blocked**.
- **Last Known Date**: The date and time of the last known attempt by the threat.
- **First Known Date**: The date and time of the first known attempt by the threat.
[See image.](#advanced-threats-incidents-image)
Click any row in the table to see additional detail on that advanced threat incident on two tabs:
- The **Details **tab has information about the threat:
- **Policy Action**: The policy action enforced on transactions related to the incident.
- **Event Type**: The type of threat event.
- **Last Known Attempt**: The date and time of the last known attempt by the threat.
- **First Known Attempt**: The date and time of the first known attempt by the threat.
- **Duration**: The duration between the first and last known attempt by the threat.
- **Total Transactions**: The total number of transactions related to the threat.
- **Total Bytes**: The total bytes of data for all the transactions related to the threat.
- **File Name**: The name of the file related to the incident.
- **Sandbox Category**: The name of the sandbox category, if the file is sent for sandbox analysis.
- **File Type**: The type of file involved in the incident.
- **File Size**: The file size involved in the incident.
- **MD5**: The MD5 hash for the file that triggered the rule.
- **SHA-2 (256-bit)**: The hash of identical files.
- **Destination IP**: The destination IP.
- **Hostname**: The hostname involved in the incident.
- **Application Category**: The application category related to the incident, if applicable.
- **Application**: The name of the application involved in the incident, if applicable.
- **URL Category**: The [URL category](/unified/about-url-categories) of the incident.
[See image.](#advanced-threats-incidents-details-image)
- The **Impacted Systems **tab has information about the systems and users affected by the threat:
- **User Name**: The name of the user.
- **Client IP**: The IP address from which the transaction originated. This is the IP address of the client device.
- **Client External IP**: The internet gateway location IP address of the client.
- **Last Known Attempt**: The date and time of the last known attempt by the threat for the user.
- **First Known Attempt**: The date and time of the first known attempt by the threat for the user.
[See image.](#advanced-threats-incidents-impact-image)
- []Malware
- Spyware
- Virus
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sandbox Offensive Security Tools
- Sandbox Ransomware
- Suspected Spyware or Adware
- Adware/Spyware Sites
- Advanced Security
- Botnet Callback
- Browser Exploit
- Crypto Mining
- Domain Generated Algorithm Domains
- Malicious Content
- Suspicious Content
- Peer-to-Peer
- Phishing
- Suspicious Destinations
- Unauthorized Communication
- Webspam
- Cross-site Scripting
- Unknown (this represents all the incidents that the Zscaler service was unable to classify under a threat category or were not classifiable under any of the preceding categories)
[]![Incoming Real Times Threats line graph on the Advanced Threats dashboard](/downloads/unified/analytics/unified-dashboards/cybersecurity/viewing-advanced-threats-dashboard/advanced-threats-incoming.png)
[]![Advanced Threat Incidents table on the Advanced Threats dashboard](/downloads/unified/analytics/unified-dashboards/cybersecurity/viewing-advanced-threats-dashboard/advanced-threats-incidents.png)
[]![Details on an advanced threat incident on the Advanced Threats dashboard](/downloads/unified/analytics/unified-dashboards/cybersecurity/viewing-advanced-threats-dashboard/advanced-threats-incidents-detail.png)
[]![Impacted Systems for an advanced threat incident on the Advanced Threats dashboard](/downloads/unified/analytics/unified-dashboards/cybersecurity/viewing-advanced-threats-dashboard/advanced-threats-incidents-impacted-systems.png)