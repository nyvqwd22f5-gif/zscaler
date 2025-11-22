# Downloading the Endpoint Credential Exposure Executive Summary Report
Source: https://help.zscaler.com/itdr/downloading-endpoint-credential-exposure-executive-report
PDF: https://help.zscaler.com/pdf/com/en/1531730.pdf

You can download the Endpoint Credential Exposure Executive Summary Report in PDF format. The report displays an abstract of credential exposure and vulnerabilities that exist on your endpoints. It highlights the misconfigurations that have the highest impact. You can leverage this report to identify credential exposure risks, prioritize what issue to focus on first, and mitigate issues before the credentials are compromised.
To download the report:
- Go to **ITDR** > **Dashboard** >** Endpoint Credential Exposure**.
-
Select a date from the **As of Date** calendar.
[See image.](#itdr-exec-report-select-date)
The endpoint credential exposure scan data for the selected date appears.
-
Click **Download Exec Report**.
[See image.](#itdr-download-exec-report)
The report is downloaded to your system in the PDF format. The report displays the following information:
- **Generated: **The report generation date.
- **Data As Of: **The date of data considered in report generation.
- **Endpoints Scanned: **The total number of endpoints scanned.
- **Summary: **Displays the following findings:
-
**Findings by Severity**: The count of credential exposure findings categorized by severity level (**Critical**, **High**, **Medium**, and **Low**).
Zscaler recommends giving immediate attention to critical- or high-level findings.
- **Total Credential Exposure Findings**: The total number of credential exposure issues identified as of the given date.
- **Credentials in Focus: **Displays the following findings:
- **Browser Infostealer Risk**: Displays credential risk that is stored in the browser. It analyzes the credentials stored in ChatGPT or OpenAI, Claude, Anthropic, Google Gemini, Okta SSO, Ping Identity, etc.
- **DevOps Credential Risk**: Displays development and operations credential risk that is saved on endpoints and can be used to break into cloud infrastructure. It includes credentials for AWS, Azure, GCP, JIRA or Confluence, Jenkins, GitLab, etc.
- **Notable Credential Risk: **Displays the critical credential risk exposed to attackers that might cause immediate security risk. It includes information such as Database Connection Strings, Cached Domain Credentials, etc.
- **Privilege Escalation Risk:** Displays the setting risk that could allow attackers to gain elevated system access. It includes Unquoted Service Paths, Unmanaged Local Admins, Modifiable Service Binaries, Modifiable PATH Variables, etc.
- **Other Credentials:** Displays the additional credential risk that attackers could steal or spread across the system. It includes Files Potentially Containing Passwords, SSH Private Keys, VNC Passwords, etc.
- **Top 5 Priority Findings:** Displays the top 5 credential exposure risks on the affected endpoints and their severity level. These issues have the highest impact, so you must focus on them first.
- **Immediate Actions Required:** Displays the recommendation on next steps to be taken immediately to reduce credential exposure risk.
[See image.](#itdr-exec-report-pdf-downloaded)
[]![Select a scan date](/downloads/itdr/dashboard/endpoint-credential-exposure/downloading-endpoint-credential-exposure-executive-report/itdr-ece-dashboard-select-scan-date-download-pdf.png)
[]![Download the exposed credential executive summary report](/downloads/itdr/dashboard/endpoint-credential-exposure/downloading-endpoint-credential-exposure-executive-report/itdr-ece-dashboard-download-pdf-3.png)
[]![View Credential Exposure Summary report details](/downloads/itdr/dashboard/endpoint-credential-exposure/downloading-endpoint-credential-exposure-executive-report/Endpoint%20Credential%20Report.png)