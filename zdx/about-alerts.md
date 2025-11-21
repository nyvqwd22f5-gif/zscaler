# About Alerts
Source: https://help.zscaler.com/zpc/about-alerts
PDF: https://help.zscaler.com/pdf/com/en/1392506.pdf

Zscaler Posture Control (ZPC) continuously scans your cloud resources and triggers alerts when it detects any security policy violations and sends alert notifications to recipients or to third-party systems for investigation.
ZPC provides security policies for both runtime and build-time environments. These policies describe the scenarios for which alerts must be triggered. ZPC triages the alerts by severity (Critical, High, Low, or Medium) to help you prioritize the alerts and take action in a timely manner. You can configure custom [alert rules](/zpc/adding-alert-rules) to trigger alerts for specific policy violations on your cloud resources.
The alert details are displayed on the Alerts page. You can also get an overview of the alert lifecycle and trends on the [ZPC dashboard](/zpc/viewing-cloud-threats-dashboard).
Alerts provide the following benefits and enable you to:
- View and manage alert notifications for any security policy violations detected in the cloud resources.
- Create and manage custom alert rules for specific policy violations based on your organization's requirements.
- Stay informed about critical security events.
- Send alert data to third-party tools for further evaluation.
**Alert Types**
The alerts are classified as:
- **Cloud Alerts**: Alerts triggered for security policy violations that occur within your cloud resources during runtime.
- **IaC Alerts**: Alerts triggered for misconfigurations detected in your IaC infrastructure during build time.
About the Alerts Page
On the Alerts page (select Alerts in the left-side navigation), you can see the following tabs:
- [Cloud Alerts](#viewing-cloudalerts-tab)
- [IaC Alerts](#viewing-iacalerts-tab)
- [Ignore Filters](#viewing-alert-ignore-filters-tab)
- [Notifications](#viewing-alert-notifications-tab)
![View the Alerts page](/downloads/zpc/alerts/about-alerts/zpc-alerts-page.png)
[]On the Cloud Alerts tab, you can do the following:
- View the list of cloud alerts generated for various cloud accounts. Click the **Alert ID** to [view additional details](/zpc/viewing-alert-details). For a detailed description of each alert attribute, see [Alert Attributes](/zpc/alert-attributes).
- [View alerts grouped by policy](/zpc/viewing-alerts-grouped-policy).
- [Apply filters](/zpc/using-filters) to view specific data in the table.
- [Resolve or ignore a single alert](/zpc/ignoring-or-resolving-alerts) or multiple alerts.
- Search for specific data in the searchable columns.
- Sort the column data.
- [Modify the table and its columns](/zpc/using-tables).
- [Ignore or resolve the open alerts](/zpc/resolving-alerts).
- [Select a saved filter](/zpc/using-filters).
- [Hide the filters](/zpc/using-filters).
- Export the alert data along with the following attributes per your requirements to an Excel file and [download the report](/zpc/downloading-reports):
- **Audit Procedure**: Steps to audit the policy violation.
- **Remediation**: Steps to remediate the policy violation.
- **Resource Metadata**: The metadata of the asset or identity.
- **All Contributing Factors**: The aggregated findings of an alert that describes the security violation in the policy.
When this option is not selected, only the first 15 aggregated findings are included in the Export report.
[See image.](#export-cloud-alert)
![View the Cloud Alerts tab](/downloads/zpc/alerts/about-alerts/zpc-cloudalerts-tab.png)
[]On the IaC Alerts tab, you can do the following:
- View the list of alerts triggered for misconfigurations detected in the IaC resources. Click the **Alert ID** to [view additional details](/zpc/viewing-alert-details). For a detailed description of each alert attribute, see [Alert Attributes](/zpc/alert-attributes).
- [View alerts by scan ID](/zpc/viewing-iac-alerts-grouped-scan).
- [View alerts grouped by policy](/zpc/viewing-alerts-grouped-policy).
- [Apply filters](/zpc/using-filters) to view specific data in the table.
- [Resolve or ignore an alert](/zpc/ignoring-or-resolving-alerts) or multiple alerts.
- Search for specific data in the searchable columns.
- Sort the column data.
- [Resolve or ignore the alert](/zpc/ignoring-or-resolving-alerts).
- [Modify the table and its columns](/zpc/using-tables).
- [Select a saved filter](/zpc/using-filters).
- [Hide the filters](/zpc/using-filters).
- Export the alert data as a report. To learn more, see [Downloading Reports](/zpc/downloading-reports).
![View the IaC Alerts tab](/downloads/zpc/alerts/iac-alerts/about-iac-alerts/zpc-iacalert-tab.png)
[]The Notifications tab displays a list of alert rules you've configured for specific policy violations. Depending on your organization's subscriptions, you can configure cloud alert rules or IaC alert rules.
On the Notifications tab, you can do the following:
- View the alert rule details. For each alert, you can see:
- **Alert Rule Name**: The name of the alert rule.
- **Alert Type**: The type of alert (Cloud or IaC).
- **Integration Type**: The third-party tool (ServiceNow, Jira, Amazon Security Lake, AWS S3, Azure Blob, or Slack) to which the alert notifications are sent.
- **State**: The enabled or disabled state of the alert rule.
When you initially add an alert rule but don't configure the notifications, the** State** is displayed as **Saved**.
- [Add an alert rule](/zpc/adding-alert-rules).
- Sort the column data.
- [Enable or disable the alert rule](/zpc/enabling-or-disabling-alert-rules).
- [Edit an alert rule](/zpc/editing-deleting-alert-rules).
- [Delete an alert rule](/zpc/editing-deleting-alert-rules).
- [Modify the table and its columns](/zpc/using-tables).
- Search for an alert rule.
![View the Notifications tab](/downloads/zpc/alerts/about-alerts/zpc-notifications-tab.png)
[]The **Ignore Filters** tab shows the list of filters you've added to ignore alerts for some security policies based on specific criteria for a set time period.
On the Ignore Filters tab, you can do the following:
- View the list of alert filters. For each filter, you can see:
- **Filter Name**: The name of the ignore filter. Click to view additional details of the filter, and edit, delete, or disable the filter. [See image.](#filter-drawer)
- **Alert Type**: The type of alert (cloud alert or IaC alert) that must be ignored.
- **Filter Scope**: The list of entities on which the filter is applied.
- **Created By**: The admin who created the filter.
- **Created**: The date and time when the filter was created.
- **Updated By**: The admin who updated the filter.
- **Updated Date**: The date and time when the filter was updated.
- **End Date**: The date when the filter is going to be disabled.
- [Add an alert ignore filter](/zpc/adding-alert-ignore-filters).
- Search for a specific filter.
- Sort the column data.
- [Enable or disable the alert ignore filter](/zpc/enabling-or-disabling-alert-ignore-filters).
- [Edit or delete the alert ignore filter](/zpc/editing-or-deleting-alert-ignore-filters).
- [Modify the table and its columns](/zpc/using-tables).
![View the Ignore Filter tab](/downloads/zpc/alerts/about-alerts/zpc-ignorefilter-tab.png)
[![View the filter drawer](/downloads/zpc/alerts/about-alerts/zpc-ignorefilterdrawer1.png)
]
[![Export the Cloud Alert Data](/downloads/zpc/alerts/about-alerts/zpc-export-cloud-alerts.png)
]