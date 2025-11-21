# Viewing the Entra ID Posture Scan Report
Source: https://help.zscaler.com/itdr/viewing-entra-id-posture-scan-report
PDF: https://help.zscaler.com/pdf/com/en/1531750.pdf

You can view the Entra ID posture scan report for a scanned Entra ID tenant. On the [Entra ID Posture](/itdr/about-entra-id-posture-dashboard) dashboard, you can select an Entra ID tenant and timestamp to view the posture report. The Entra ID vulnerability report shows issues for the identities, service principals, and configuration settings. The report enables you to analyze and remediate issues to maintain the security posture of your tenant.
The Entra ID vulnerability reports are permanently deleted when the retention policy period expires. To learn more, see [Configuring a Retention Policy](/itdr/about-advanced-settings#itdr-adv-settings-retention-page-section).
To view the Entra ID vulnerability report:
- **Go to ITDR** > **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID Posture **dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#entraID-result)
The scan result for the Entra ID tenant appears.
-
Click **View Report**.
[See image.](#itdr-entra-id-view-vulnerability-option)
The vulnerability report for the Entra ID tenant appears with the following information:
- **Issue**: The vulnerability issue details. You can use the search field to search for a specific issue.
- **Description**: The issue description. You can use the search field to search for a specific description.
- **Type of Risk**: The type of vulnerability risk (e.g., **Best Practice Violations**, **Privilege Escalation**, **Hybrid Risk**, **Privilege Leak**, etc.). You can use the search field to search for a specific risk type.
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Medium**, or **Low**). You can filter the column to view issues by severity.
- **Remediation**: The remediation assessment (e.g., **Difficult**, **Moderate**, or **Easy**). You can filter the column to view issues by remediation.
-
**Actions**: Click the **Create ServiceNow** ticket icon to create a ServiceNow ticket to track and assess the issue.
[See image.](#itdr-entra-id-view-vulnerability-issues)
Click **Download Excel Report** to download the report as an Excel file. You can also [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
[]![View Entra ID posture report option](/downloads/itdr/dashboard/entra-id/viewing-entra-id-vulnerability-report/itdr-entraID-posture-view-report.png)
[]![View Entra ID posture scan report details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-vulnerability-report/itdr-entraID-posture-report.png)
[]![The Entra ID Posture dashboard with annotation around Result for and scanned on options.](/downloads/itdr/dashboard/entra-id/viewing-entra-id-vulnerability-report/itdr-entra-id-post-scan-domain-date-without-options.png)