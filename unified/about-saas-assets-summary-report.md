# About SaaS Assets Summary Report
Source: https://help.zscaler.com/unified/about-saas-assets-summary-report
PDF: https://help.zscaler.com/pdf/com/en/1497526.pdf

The SaaS Assets Summary Report allows you to view a summary of SaaS Security API-based discovery and remediation activities. This serves as the starting point when investigating what data is affected and identifying risky users.
The SaaS Assets Summary Report provides the following benefits and enables you to:
- Gain visibility into your SaaS assets for Data Loss Prevention (DLP) incidents, malware incidents, and risky users in your organization.
- Analyze the report for individual applications to configure stronger policies to mitigate threats.
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
About the SaaS Assets Summary Report Page
On the SaaS Assets Summary Report page (Analytics > Internet & SaaS > Analytics > SaaS Assets Summary Report), you can do the following:
- Print the report.
- Filter the report by application or its category:
- Collaboration Applications (Slack, Webex Teams, Microsoft Teams, and Zoom)
- CRM Applications (Salesforce and Dynamic 365)
- Email Applications (Exchange and Gmail)
- File Sharing Applications (Box, OneDrive, SharePoint, ShareFile, Dropbox, Confluence, Smartsheet, and Google Drive)
- Gen AI Applications (ChatGPT)
- ITSM Applications (ServiceNow and Jira Software)
- Source Code Repository Applications (GitHub, GitLab, and Bitbucket)
- Public Cloud Storage Applications (Amazon S3, Google Cloud Platform, and Microsoft Azure)
- View data from the past 24 hours, last 7 days, last 15 days, last 30 days, or customize up to the last 90 days. The default time is 24 hours.
- **Total Incidents**: The total number of incidents across all the scanned data. An incident is a triggered DLP or malware policy. This is caused when a file is scanned for the first time or when a change in the file violates the policy. See the incidents broken down by policy type (DLP and Malware) and the number of files scanned.
-
**Incidents Trend**: See the incident trend based on the time frame selected for the report, and filter by SaaS application. By default, **All Application Categories **are shown. You can drill down on a trend line point to view the number of incidents broken down by policy type (DLP and Malware), and then click on whichever number you want to see logs for; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
[See image.](#trend-point)
- **Applications Generating the Incidents**: See the number of incidents per application. Each incident is broken down by policy type (DLP and Malware). You can click on whichever number you want to see logs for; you are redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
- **DLP Incidents by Engine, Dictionary, or Severity**: Filter to see the distribution of DLP incidents by engine, dictionary, or severity. You will see a breakdown within the DLP incidents at the types of data affected. You can also filter by the type of application.
- **Malware Incidents Threat Category**: See the distribution of malware incidents by threat category. You can filter by the type of application.
- **Departments with Most Incidents**: See the departments that own data that generated the most incidents.
-
**Users with Most Incidents**: See the users who own data that generated the most incidents.
The **unknown_saas_user*** is a user who can access the SaaS application but isn't added to the Zscaler service. For example, an organization, SafeMarch, has added 5,000 of its 10,000 employees. A user, john@safemarch.com, is registered on the SaaS application, but isn't added to the [users page](/unified/about-users). As a result, is referred to as an unknown SaaS application user.
- **Risky Cloud SaaS Applications in Use Across Organization**: See the risky cloud SaaS applications that are being used across your organization. You see the application, its category, its threat index, its net usage (GB), and the recommended configuration.
[]![A trend line in the SaaS Assets Summary Report, with a drill down on a point](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-summary-report/ZIA-6.1-Incidents-Trend_1%20(1).png)
![The SaaS Assets Summary Report and its widgets in the Admin Portal.](/downloads/zia/dashboard-analytics/reports/saas-assets-summary-report/SaaS_Assets_Summary_Report.png)