# About Alerts
Source: https://help.zscaler.com/zia/about-alerts
PDF: https://help.zscaler.com/pdf/com/en/1399136.pdf

[Watch a video about Alerts](https://fast.wistia.net/embed/iframe/9to9j2rhzn)
You can configure the Zscaler service to email specific individuals when certain events occur, so your organization can take action in a timely manner. To learn more, see [About Alert Subscriptions](/zia/about-alert-subscriptions). You can create up to 128 alerts. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zia/ranges-limitations#Other).
The Alerts page provides the following benefits and enables you to:
- Configure notification triggers for high priority issues.
- Monitor high priority issues and detections in one place.
You can create an alert for different types of events, such as when the service detects incoming or outgoing malware or when there is a policy violation. When you receive an alert, you can investigate it by going to Analytics and viewing logs of the event.
Events are grouped into classes. For a list of events that can trigger alerts, organized by class, see the table within each class type below.
Alert Classes
Depending on your organization's subscriptions, you can configure the service to send alerts for the following classes.
If configuring alerts in your SIEM via NSS, refer to the Security Alerts table below for Logged Fields and Values. Additionally, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs) and [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs) for a more comprehensive list.
- [Security Alerts](#SecurityAlertsTable)
- [Access Control Alerts](#AccessControlAlertsTable)
- [System Alerts](#SystemAlertsTable)
- [Data Loss Prevention Alerts](#DataLossPreventionAlertsTable)
- [Patient 0 Alerts](#Patient0AlertsTable)
About the Define Alerts Page
On the Define Alerts page (Administration > Alerts), you can do the following:
- [Add an alert](/zia/adding-alerts).
- View a list of all configured alerts. For alerts, you can see the following:
- **Alert Name**: Displays the trigger event that generated the alert.
- **Alert Class**: Displays the class of the event that triggered the alert.
- **Triggered By**: Displays the number of event occurrences for a given time period.
- **Applies To**: Displays whether the event is applied to the Organization, a Location, Department or User.
- **Severity**: Displays the severity level of the event (i.e., Critical, Major, Minor, Info, or Debug).
- **Status**: Displays whether the alert is enabled or disabled.
- [Edit an alert](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- Search for an alert.
- Click the** Global Configuration** tab to [resend alerts](/zia/resending-alerts).
- Click the **Publish Alerts** tab to specify [alert subscriptions](/zia/about-alert-subscriptions) for email recipients.
![The Alerts page](/downloads/tech-pubs-drafts/zia-draft-articles/about-alerts-doc-54336/about-alerts-callout.png)
[]
| Event | Logged Field | Value |
| ----- | ------------ | ----- |
| Advanced Security | URL Category | Advanced Security |
| Adware/Spyware | URL Category | Spyware Callback |
| Adware/Spyware Sites | URL Category | Adware/Spyware Sites |
| Botnet Callback | URL Category | Botnet Callback |
| Browser Exploit | URL Category | Browser Exploit |
| Cross-site Scripting | URL Category | Cross-site Scripting |
| Crypto Mining | URL Category | Crypto Mining & Blockchain |
| Incoming/Outgoing Malware | Threat Category/Malware Category | Malware, Exploit, MalwareTool, ArchiveBomb, MalwareSecurityRisk, Other Malware |
| Incoming/Outgoing Spyware | Threat Category/Malware Category | Spyware, Dialer, BackDoor, Adware Proxy, PWStealer, Downloader, Other Spyware |
| Incoming/Outgoing Unscannable Files | Policy Reason | Not allowed to upload/download unscannable file formats |
| Incoming/Outgoing Viruses | Threat Category/Malware Category | Virus, Unwanted Applications, BootVirus, Macro, Worm, Trojan, MisDisinfection, Other Viruses, Ransomware, Remote Access Tool, Unrecognized Virus |
| Malicious Content | URL Category | Malicious Content |
| Peer-to-peer | URL Category | Peer-to-peer |
| Phishing | URL Category | Phishing |
| Privacy Risk | URL Category | Privacy Risk |
| Sandbox Adware | Threat Category/Malware Category | Sandbox Adware |
| Sandbox Anonymizer | Threat Category/Malware Category | Sandbox Anonymizer |
| Sandbox Malware | Threat Category/Malware Category | Sandbox Malware |
| Sandbox Offensive Security Tools | Threat Category/Malware Category | Sandbox Offensive Security Tools |
| Sandbox Ransomware | Threat Category/Malware Category | Sandbox Ransomware |
| Suspicious Content | URL Category | Suspicious Content |
| Suspicious Destination | URL Category | Suspicious Destination |
| Unauthorized Communication | URL Category | Unauthorized Communication |
| Web Spam | URL Category | Web Spam |
[]
| Event |
| ----- |
| Chat File Transfer |
| Social Network Post |
| Streaming Upload |
| Streaming View/Listen |
| URL Filtering Blocked Sites |
| Webmail File Attachment |
[]
| Event |
| ----- |
| ADP Schedule Update Failure |
| Auth Bridge Down |
| LDAP Connection Down |
| LDAP Failure |
| LDAP Success |
| Traffic Decrease |
| Traffic Increase |
| Policy Violation |
[]
| Event |
| ----- |
| Custom Engine Violation |
| GLBA Violation |
| HIPAA Violation |
| IDM Schedule Update Failure |
| PCI Violation |
[]
| Event |
| ----- |
| Patient 0 (Requires Advanced Sandbox) |