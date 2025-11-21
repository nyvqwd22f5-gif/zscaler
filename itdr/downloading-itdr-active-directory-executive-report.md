# Downloading the Active Directory Executive Summary Report
Source: https://help.zscaler.com/itdr/downloading-itdr-active-directory-executive-report
PDF: https://help.zscaler.com/pdf/com/en/1531645.pdf

The Zscaler ITDR Active Directory (AD) Executive Summary Report reveals misconfigurations or vulnerabilities in your AD. It provides the AD domain risk severity to assess the security posture of the AD. It lists top risks and provides remediation guidance to secure your AD.
To download the AD Executive Summary Report:
- Go to **ITDR** > **Dashboard** > **Active Directory Posture**.
- On the **Active Directory Posture **dashboard:
- Select an AD domain from the **Result for** drop-down menu.
-
Select a timestamp from the **Scanned on** drop-down menu.
The scan result for the AD domain appears.
-
Click **Downloads** and select **Executive Summary**.
[See image.](#itdr-ad-download-assessment-report-option)
-
The report is downloaded to your system as a PDF. The report displays the following information:
-
**Introduction**: An overview of the reports included in AD Executive Summary Report.
Only the enrolled reports are displayed in the **Report Scope and Monitoring Capabilities** section.
- **Executive Summary in Numbers**: The summary of each report.
-
**Total Active Issues**: The total number of active identity security risks identified in your AD domain. Issues are categorized by severity level (**Critical**, **High**, **Medium**, or **Low**).
Zscaler recommends giving immediate attention to critical- or high-level findings.
- **Domain Security Rating**: The security rating of the domain. Provides a **Critical **or **High **rating to the domain even if a single critical or high issue is identified.
- **Privilege identities at risk**: The number of privileged users, service principals, or groups with security risks.
- **Total Changes Detected**: The total changes identified in the domain in the last 30 days. It includes both positive and suspicious changes in the domain.
- **Identities with Suspicious Changes**: The number of identities that performed suspicious changes in configuration that might cause a security risk.
- **Changes to User-Defined Tracked Identities**: The number of identities that performed changes. This includes only those users, groups, service principals, and applications that you selected to monitor for [custom change detection](/itdr/creating-active-directory-custom-change-detection-policy).
- **Issues Resolved**: The number of security issues resolved since the last scan.
- **Active Directory Posture**: The security risks in the AD domain with severity level and impacted identities.
- **Active Directory Change Detection**: The last 10 suspicious and positive changes made by identities in the AD domain
- **User-Defined Identity Tracking**: The last 10 changes detected in tracked identities.
- **Monitoring Status**: The monitoring status of the AD domain.
[See image.](#deception-itdr-ad-assessment-report)
[]![Download AD executive summary report](/downloads/itdr/dashboard/active-directory/downloading-itdr-active-directory-executive-report/itdr-download-executive-summary.png)
[]![Displaying Active Directory Posture report](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-reports/downloading-itdr-active-directory-executive-report/AD-security-posture-report.png)