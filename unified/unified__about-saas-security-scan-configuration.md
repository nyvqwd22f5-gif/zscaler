# About SaaS Security Scan Configuration
Source: https://help.zscaler.com/unified/about-saas-security-scan-configuration
PDF: https://help.zscaler.com/pdf/com/en/1493591.pdf

In order for the SaaS Security Data at Rest Scanning [Data Loss Prevention (DLP)](/unified/about-data-rest-scanning-dlp) and [Malware Detection](/unified/about-data-rest-scanning-malware-detection) policies to inspect content in sanctioned SaaS applications, you must create SaaS Security scan schedules.
Before scheduling a scan, you must configure the DLP and Malware Detection policy (i.e., configure policy rules for your [SaaS application tenant](/unified/about-saas-application-tenants)). When configuring a scan schedule for a tenant, you must select the Data at Rest Scanning policy. This allows the scan to use the policy rules associated with the tenant, and to inspect content based on the rule's specifications (e.g., criteria, action, etc.).
Scheduling a Data at Rest Scanning DLP or Malware scan for a SaaS application provides the following benefits and enables you to:
- Gain a precise understanding of the scan process with clear and actionable status updates. The Scan Initialized state immediately shows you that the scan is set up and is preparing to begin, instead of having no information during scheduling delays.
- Monitor accurate scan progress; admins need not guess whether the scan is active or delayed anymore. The Refresh button allows you to check current updates on demand, without contacting support for clarification.
To learn more, see [Understanding SaaS Security Scan Schedules](/unified/understanding-saas-security-scan-schedules).
About the SaaS Security Scan Configuration Page
On the Scan Configuration page (Policies > Common Configuration > Out-of-Band CASB > Scan Configuration), you can do the following:
- [Add a new scan schedule.](/unified/configuring-saas-security-scan-schedules)
- Search for a scan schedule.
- View a list of all configured scan schedules. For scan schedules, you can see the following:
- **SaaS Application Tenant**: The [SaaS application tenant](/unified/about-saas-application-tenants) chosen for the scan schedule.
- **Schedule Criteria**: The specified policy and the amount of historical data inspected by the scan.
- **Description**: The description of the scan schedule, if available.
- **Status**: Displays the status of each scan.
- **Scan Initialized**: When a scan is initialized, the necessary prerequisites for the scan are verified and evaluated to ensure readiness. Scan Initialized does not indicate the actual start of the scanning process. When the scan is initialized, the date and time of the initialization are also displayed.
- **Running**: A scan starts running when the initialization is completed successfully. When the scan is running, the date and time the scan started are also displayed.
- **Scan Stopped**: When a scan stops, the date and time the scan stopped, and the reason are also displayed.
-
Stop a scan at any time.
Stopping a scan flushes the processing queue. If you stop the scan, you must use one of the following options to start it again.
- If you configure the scan to inspect all historical data, the scan processes all data from the beginning. This might result in duplicate results for data that the scan has already inspected.
- First, analyze your [SaaS Security Insights logs](/unified/about-saas-security-insights-logs) to find when the scan stopped processing your historical data. Then, configure the scan to inspect data starting from that date, so it ignores already processed data.
- Refresh the status of a scan at any time.
- Start a scan at any time.
- Edit or delete a scan schedule.
- [Modify the table and its columns.](/unified/using-tables)
![Add a scan schedule for selected SaaS applications.](/downloads/zia/policies/saas-security/data-rest-scanning-policies/about-saas-security-scan-configuration/SaaS%20Security%20Scan%20Configuration_0.png)