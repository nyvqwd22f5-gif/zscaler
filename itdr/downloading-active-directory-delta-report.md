# Downloading the Active Directory Delta Report
Source: https://help.zscaler.com/itdr/downloading-active-directory-delta-report
PDF: https://help.zscaler.com/pdf/com/en/1531841.pdf

Security teams often face challenges in monitoring and responding to changes in their identity security posture due to frequent updates in Active Directory (AD) domains and credential exposure data. A static snapshot of security posture lacks the ability to track changes over time. This limitation makes it difficult to identify improvements, regressions, and emerging risks.
Zscaler ITDR allows you to compare two historical AD scans and generate a delta report. This report provides detailed insights into changes in the AD security posture, and highlights newly identified risks, resolved issues, and updates to previously known risks. ITDR automates this comparison, enabling security teams to quickly identify new risks, address key changes, and prepare targeted responses efficiently.
To support further analysis and collaboration, ITDR allows you to download the AD delta report in PDF and Excel formats. With these reports, you can analyze data offline, share insights with stakeholders, and streamline remediation efforts to improve the security posture of your AD environment.
To download the AD delta report:
- Go to **ITDR** > **Dashboard** > **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard, click **Downloads** and select one of the following options from the drop-down menu:
[See image.](#itdr-ad-delta-report-pdf-exceldownlload-option-image)
- [Delta Report PDF](#itdr-ad-delta-report-pdf)
- [Delta Report Excel](#itdr-ad-delta-report-excel)
[]In the **Delta Report PDF **window, select the AD scans that you want to compare.
-
Select the first AD scan timestamp from the drop-down menu, and click **Next**.
[See image.](#itdr-ad-delta-report-pdf-first-scan-image)
-
Select the second AD scan timestamp (an older date) from the drop-down menu, and click **Submit**.
[See image.](#itdr-ad-delta-report-pdf-second-scan-image)
The delta report is downloaded to your system in the PDF. The report includes the following information in a structured and concise format with clear insights into the security posture changes between the two AD scans:
- **Baseline Scan (A)**: The timestamp of the previous scan that you selected in the second scan.
- **Current Scan (B)**: The timestamp of the current scan that you selected in the first scan.
- **Executive Summary**: The issue comparison summary includes:
- **Total Issues**: The total number of issues that is identified in the current scan (Scan B) and its comparison with the previous scan (Scan A).
- **Critical Issues**: The number of critical issues identified in the current scan (Scan B) and its comparison with the previous scan (Scan A).
- **Issues Resolved**: The number of issues resolved in the current scan (Scan B).
- **New Issues**: The number of new issues detected in the current scan (Scan B).
- **Overall Risk Level**: A unified risk severity comparison between Scan A and Scan B. Severity levels are categorized as **Critical**, **High**, **Medium**, or **Low**. The risk posture improves as the severity level decreases.
- **Issue Changes Overview**: The total number of new, resolved, and updated issues in a bar chart, providing a quick overview of changes.
- **Key Highlights**: The key highlights on the security posture of the AD domain, such as top new issues, major improvements, and remaining critical issues that require attention.
- **New Issues Detected**: The list of new detected issues along with their severity levels and affected objects number.
- **Resolved Issues**: The list of resolved issues along with their severity levels and affected objects number.
- **Updated Issues**: The list of existing issues that are updated along with their severity levels and change comparison between the previous scan (Scan A) and current scan (Scan B).
[See image.](#itdr-ad-delta-pdf-report-image)
-
[]In the **Delta Report Excel** window, select the AD scans that you want to compare.
-
Select the first AD scan timestamp from the drop-down menu, and click **Next**.
[See image.](#itdr-ad-delta-excel-first-scan-image)
-
Select the second AD scan timestamp (an older date) from the drop-down menu, and click **Submit**.
[See image.](#itdr-ad-delta-excel-second-scan-image)
The delta report is downloaded to your system in the Excel format. The first scan is referred to as Scan B and the second as Scan A. The Excel report displays the following AD object-level information in separate tabs for in-depth analysis:
- **Export Summary**: A list of all the tab names included in the delta Excel report.
- **Delta Summary**: The issue comparison summary including scan timestamps; the total number of new, resolved, and updated issues; unified risk severity; and the total number of affected AD objects.
- **New Issues**: The total number of new issues introduced in Scan B, including issue name, severity levels (**High**, **Medium**, or **Low**), and affected AD object details.
- **Resolved Issues**: The total number of issues resolved and no longer detected in Scan B, including issue name, severity levels, and affected AD object details.
- **Updated Issues**: The total number of existing issues with a change in the number of affected AD objects, including issue name and severity levels.
- **Detailed Changes**: The details of affected AD identities that were added or removed based on the changes recorded in the **Updated Issues** tab.
[See image.](#itdr-ad-delta-excel-report-details-image)
[]![Download AD delta report PDF and Excel options](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-download-summary-report-pdf-excel.png)
[]![Select the first AD scan](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-ad-delta-pdf-first-scan.png)
[]![Select the second AD scan](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-ad-delta-pdf-second-scan.png)
[]![Displaying AD Delta PDF Report](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-reports/downloading-active-directory-delta-report/AD-Delta-Report-1.png)
[]![Select the first AD scan ](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-ad-delta-xl-first-scan.png)
[]![Select the second AD scan](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-ad-delta-xl-second-scan.png)
[]![View AD delta Excel report](/downloads/itdr/dashboard/active-directory/downloading-active-directory-delta-report/itdr-ad-delta-pdf-report-excel-details-1.png)