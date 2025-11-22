# Downloading the Zscaler ITDR Microsoft Entra ID Executive Summary Report
Source: https://help.zscaler.com/itdr/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report
PDF: https://help.zscaler.com/pdf/com/en/1531749.pdf

The Zscaler ITDR Entra ID Executive Summary Report identifies the misconfigurations or vulnerabilities in your Microsoft Entra ID tenant that might cause security risk. It provides the tenant risk severity and provides recommendations to secure your Entra ID.
To download the Zscaler ITDR Entra ID Executive Summary Report:
- Go to **ITDR **> **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID** **Posture **dashboard:
- Select an Entra ID tenant from the** Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#entraID-dashboardresult)
The scan result for the Entra ID tenant appears.
-
Click **Downloads** and select **Executive Summary**.
[See image.](#itdr-entra-id-download-execu-summary)
The report is downloaded to your system as a PDF. The report displays the following information:
-
**Introduction**: An overview of the reports included in Entra ID Executive Summary Report.
Only the enrolled reports are displayed in the **Report Scope and Monitoring Capabilities** section.
- **Executive Summary in Numbers**: The summary of each report.
-
**Total Active Issues**: The total number of active identity security risks identified in your Entra ID tenant. Issues are categorized by severity level (**Critical**, **High**, **Medium**, or **Low**).
Zscaler recommends giving immediate attention to critical- or high-level findings.
- **Tenant Security Rating**: The security rating of the tenant. Provides a **Critical **or **High **rating to the tenant even if a single critical or high issue is identified.
- **Privileged identities at risk**: The number of privileged users, service principals, or groups with security risks.
- **Total Changes Detected**: The total changes identified in the tenant in the last 30 days. It includes both positive and suspicious changes in the tenant.
- **Identities with Suspicious Changes**: The number of identities that performed suspicious changes in configuration that might cause a security risk.
- **Changes to User-Defined Tracked Identities**: The number of identities that performed changes. This includes only those users, groups, service principals, and applications that you selected to monitor for [custom change detection](/itdr/creating-entra-id-custom-change-detection-policy).
- **Issues Resolved**: The number of security issues resolved since the last scan.
- **Entra ID Security Posture**: The security risks in the Entra ID tenant with severity level and impacted identities.
- **Entra ID Change Detection**: The last 10 suspicious and positive changes made by identities in the Entra ID tenant.
- **User-Defined Identity Tracking**: The last 10 changes detected in tracked identities.
- **Monitoring Status**: The monitoring status of the Entra ID tenant.
[See image.](#itdr-entra-id-assessment-report-downloaded-pdf)
[]![Download Entra ID executive summary report](/downloads/itdr/dashboard/entra-id/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report/itdr-download-entraID-summary.png)
[]![Displaying Entra ID Security Posture Report](/downloads/tech-pubs-drafts/itdr-draft-articles/draft-downloading-entra-id-executive-summary-report-doc-58254/Entra%20ID%20report1.png)
[]![The Entra ID Posture dashboard with annotation around Result for and scanned on options.](/downloads/itdr/dashboard/entra-id/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report/itdr-entra-id-post-scan-domain-date-without-options.png)