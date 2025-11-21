# ZIA Security Policies Troubleshooting Runbook
Source: https://help.zscaler.com/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook
PDF: https://help.zscaler.com/pdf/com/en/1532307.pdf

The ZIA Security Policy Troubleshooting Runbook provides comprehensive guidance for troubleshooting requests related to scenarios involving URL, domain, IP address, file analysis, and related vulnerabilities. It highlights various checks on third-party websites and Zscaler's tools that help you achieve clarity on the security verdicts. By following these structured steps, users can efficiently address issues related to Zscaler's security policies and ensure proper handling of security threats.
Requesting Zscaler to Review URL, Domain, IP Address, File, MD5, IOCs, CVE, or Vulnerabilities
If you request that Zscaler review vulnerabilities, and the request includes reviewing URLs, domains, files, CVEs, or vulnerabilities against Zscaler’s protection, the following sections describe the appropriate reactions.
Related to CVE or Vulnerabilities
If you have a query with Zscaler’s protection against a specific CVE or vulnerability, complete the following steps.
[Troubleshooting](#cve-vulnerabilities-troubleshooting)
[]
Go through [Zscaler ’s Threatlabz’s Product Security Advisories](https://www.zscaler.com/security-advisories) and search for a matching CVE number or keyword.
[Further Steps](#cve-vulnerabilities-further)
[]
If you still need assistance, prepare an issue summary with any supporting information (e.g., a vulnerability scanning report from a third-party vendor) and open a support case with [Zscaler Support](/contact-support)
Related to Review on URL, Domain, IP Address, File, MD5, or IOCs
If you disagree with the Zscaler detection result for a specific URL or file, export the Web Insights logs with all fields selected for the respective destinations and complete the following steps.
[Troubleshooting](#review-url-troubleshooting)
[]
-
Go to your [Zulu account](https://zulu.zscaler.com/) and enter the URL to find the verdict from Zscaler. Click **Reanalyze **if an existing verdict is found.
[See image.](#zulu-url-risk-analyzer)
- Go to [Zscaler Threat Library portal](https://threatlibrary.zscaler.com/) and search using the threat name.
[See image.](#zscaler-threat-library)
- Perform a check from the [Public VirusTotal (URL)](https://www.virustotal.com/gui/home/url) or [VirusTotal (File) portal](https://www.virustotal.com/gui/home/upload). Click **Reanalyze **if an existing verdict is found. Take note of the verdict and record the VirusTotal’s URL post analysis completion.
[See image.](#virus-total)
- Go to [Zscaler Sandbox Scanning Portal](https://filecheck.zscaler.com/) and submit the files for analysis.
[See image.](#zscaler-sandbox-scanning-portal)
The maximum size for one file is 20 MB.
[Further Steps](#review-url-further)
[]
If you still need assistance, prepare an issue summary with all supporting information (e.g., a screenshot or URL post analysis from the previous troubleshooting steps) and open a support case [Zscaler Support](/contact-support).
Determining Issue Threat Classification
Zscaler’s security controls include Malware Protection, Advanced Threat Protection (ATP), and Sandbox.
[See image.](#threat-malware-detection-protocol)
Using the information in Web Insights logs helps to scope the security controls involved and provide troubleshooting guidance to isolate the cause of potential policy misbehavior.
For policy block action, see [ZIA Policy Reasons](/zia/policy-reasons).
The following are Web Insights logs examples with additional useful fields.
Malware Protection
| Policy Action | Threat Name | Threat Category | Threat Super Category | Blocked Policy Type |
| ------------- | ----------- | --------------- | --------------------- | ------------------- |
| Malware block: malicious file | W32/Blat.A.gen!Eldorado | Unwanted Application | Virus | Malware Protection |
| Malware block: malicious file | Win32.RMMTool.TeamViewer.CS | Remote Access Tools | Virus | Malware Protection |
| Malware block: malicious file | JS/Agent.CRJ | Other Virus | Virus | Malware Protection |
| Not allowed to upload or download encrypted or password-protected archive files | None | None | None | Malware Protection |
| Not allowed to upload or download unscannable file formats | None | None | None | Malware Protection |
Advanced Threat Protection
| Policy Action | Threat Name | Threat Category | Blocked Policy Type | URL Category |
| ------------- | ----------- | --------------- | ------------------- | ------------ |
| PageRisk block inbound response: page is unsafe | None | None | Advanced Threat Protection | Suspicious Content |
| IPS block outbound request: botnet command and control traffic | Win64.Backdoor.Sliver | None | Advanced Threat Protection | Botnet Callback |
| DGA Domain Block | None | None | Advanced Threat Protection | Domain Generation Algorithm (DGA) Domains |
| Reputation block outbound request: malicious URL | HTML.Injection.SEO-SPAM | None | Advanced Threat Protection | Malicious Content |
| IPS block outbound request: browser cookie theft | HTML.Exploit.CookieStealing | None | Advanced Threat Protection | Cross-site Scripting |
| IPS block outbound request: cross-site scripting (XSS) attack | JS.Exploit.XSS | None | Advanced Threat Protection | Cross-site Scripting |
| Country block outbound request: not allowed to access sites in this country | None | None | Advanced Threat Protection | Suspicious Destination |
Malware Protection and Advanced Threat Protection
For Malware Protection and ATP policy types, complete the applicable troubleshooting steps according to the following symptoms.
[Policy Not Working as Expected: Access is Blocked Unexpectedly (Unaware of Any Block Policy Configured)](#access-is-blocked)
[]
Use these steps if you think that the policy is correctly configured, but the web logs show a contradicting policy action (e.g., an Allow to Differentiate policy is configured, but access is blocked or cautioned as confirmed by the web logs).
Review the Policy Action value in the Web Insights logs for the transaction before continuing.
Troubleshooting
If the Blocked Policy Type is Malware Protection or Advanced Threat Protection, and the Policy Action matches one of the block values, then complete the following checks:
- Ensure **SSL Inspection** is enabled.
- Ensure [Malware Protection Policy](/zia/configuring-malware-protection-policy) **Traffic Inspection** and **Protocol Inspection **are enabled.
- Check the [Malware Protection Policy](/zia/configuring-malware-protection-policy) and [Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) configurations. If the configuration is set as **Block**, then the enforcement is working as expected.
- For [Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) configuration, check for any matching entry in **Blocked Malicious URLs**.
- Check any URL classification changes for the reported URL and compare the changes to a previous period when the access was working.
- Verify the **Unscannable Files** and **Password-Protected Files** configuration for [Malware Protection Security Exceptions](/zia/configuring-security-exceptions-malware-protection-policy).
- For **Unscannable Files** in **Malware Protection Policy**:
- The setting *Unscannable *applies to uploading or downloading files that the Zscaler service is unable to scan.
- The following rules apply when using the **Unscannable Files** setting:
- The Zscaler service supports files (archive files larger than 400 MB, or extracted files larger than 200 MB) for Malware Protection scans. The Zscaler service does not scan files that exceed that limit.
- If a file is within the size limit, it is allowed or blocked based on the Malware Protection policy settings. If the file can't be scanned, it is blocked, and any subsequent upload or download attempts are blocked. The service then displays an end user notification to prevent users from uploading or downloading it.
- If a file exceeds the size limit and the Zscaler service can identify the file type, then the file is allowed or blocked based on **File Type Control **policy.
- If a file exceeds the size limit and the Zscaler service cannot identify the file type, then users can download but cannot upload the file.
- Check if there are any files within an archive (e.g., an .xslx file) that might match the detection criteria. Rename the .xlsx file to a .zip extension, then extract the file using any archive extractor tool.
- For **Password-Protected Files** in Malware Protection Policy:
- **Password-Protected Files** applies to uploading or downloading password-protected archive files.
- Check if there are one or more files within an archive that match the detection criteria.
- Verify the affected URL or file against the following resources:
- [Zulu](https://zulu.zscaler.com/): Enter the URL and click **Analyze**.
- [Zscaler's Threat Library](https://threatlibrary.zscaler.com/): Enter the **Threat Name** (based on Web Insights log) and click **Search**.
- [VirusTotal (URL)](https://www.virustotal.com/gui/home/url): Enter the **URL**, **Domain**, **IP Address**, or **File **hash.
- [VirusTotal (File)](https://www.virustotal.com/gui/home/upload): Upload the file.
Further Steps
If you still need assistance, prepare an issue summary with any supporting information (e.g., a vulnerability scanning report from a third-party vendor) and open a support case with [Zscaler Support](/contact-support). Provide the following data:
- Relevant configuration screenshots:
- Malware Policy & Exception configuration
- Advanced Threat Protection Policy & Exception configuration
- Web Insights logs with all fields selected
- Temporarily enable **Remote Assistance**.
[Policy Not Working as Expected: Access is Allowed Unexpectedly (Block Policy Configured, but Access is Allowed)](#access-is-allowed)
[]
The policy might be correctly configured, but the web logs show a contradicting policy action. For example, a Block policy is configured, but access is allowed as confirmed by the web logs. Check the Policy Action value in the Web Insights logs for the transaction before continuing to the next section.
Troubleshooting
If the **Policy Action** is **Allowed**, complete the following checks:
- Verify **SSL Inspection** is enabled.
- Verify that the [Malware Protection Policy](/zia/configuring-malware-protection-policy) **Traffic Inspection **and **Protocol Inspection** options are enabled.
- Check [Malware Protection Policy](/zia/configuring-malware-protection-policy) and [Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) configurations. If the configuration is set to **Allow**, then review to see if you should change the configuration to **Block**.
- For [Malware Protection Policy](/zia/configuring-malware-protection-policy) configuration, check for any matching entry in **Security Exceptions** by going to **Security Exceptions** > **Do Not Scan Content from these URLs**.
- For [Advanced Threat Protection Policy](/zia/configuring-advanced-threat-protection-policy) configuration, check for any matching entry in **Security Exceptions** by going to **Security Exceptions** > **Do Not Scan Content from these URLs**.
- Verify the affected URL or file against the following resources:
- [Zulu](https://zulu.zscaler.com/): Enter the URL and click **Analyze**.
- [Zscaler's Threat Library](https://threatlibrary.zscaler.com/): Enter the **Threat Name** (based on Web Insights log) and click **Search**.
- [VirusTotal (URL)](https://www.virustotal.com/gui/home/url): Enter the **URL**, **Domain**, **IP Address**, or **File **hash.
- [VirusTotal (File)](https://www.virustotal.com/gui/home/upload): Upload the file.
Further Steps
If you still need assistance, create an issue summary with the data and open a support case with [Zscaler Support](/contact-support). Provide the following data:
- Relevant configuration screenshots:
- **Malware Policy & Exception** configuration.
- **Advanced Threat Protection Policy & Exception** configuration.
- Web Insights logs with all fields selected.
- Temporarily enable **Remote Assistance**.
Sandbox
Before troubleshooting a reported issue, confirm that the Sandbox is responsible for the block or unexpected behavior. Various ZIA policies, such as Malware Protection, File Type Control, or other upstream security solutions, can also impact file downloads.
SSL Inspection is a prerequisite for Sandbox policies to apply. If traffic isn't getting SSL inspected, Sandbox policies do not apply.
[Review the End User Notification (EUN)](#review-eun)
[]
EUN for Quarantine:
[See image.](#eun-quarantine)
EUN for Sandbox Block:
[See image.](#eun-sandbox)
To learn more about the action and EUN, see [About Sandbox End User Notifications](/zia/about-sandbox-end-user-notifications).
Review the Web Insights Logs
Sandbox
-
-
-
-
-
-
-
-
-
-
| Policy Action | Threat Category | Threat Super Category | Blocked Policy Type |
| ------------- | --------------- | --------------------- | ------------------- |
| Allowed | Benign | Sandbox | None |
| Allowed | Sent for Analysis | Sandbox | None |
| QuarantinedML QuarantinedIsolate and Scan | Sent for Analysis | Sandbox | Sandbox |
| Sandbox Block Inbound ResponseML Block | Sandbox MalwareSandbox AdwareSandbox AnonimyzerSandbox Offensive Security ToolsSandbox Ransomware | Sandbox | Sandbox |
If **Threat Super Category **value matches **Sandbox**, use the following troubleshooting steps according to the symptoms.
[Zscaler Sandbox Policy Behavior Issues](#sandbox-policy-behavior)
[]
There are cases where files are incorrectly blocked, are not analyzed by Zscaler Sandbox, or continue to stay in the quarantine queue. These issues might be due to various reasons, such as policy misconfigurations, forwarding errors, or backend processing delays. Follow the Sandbox issue symptoms in the next section for troubleshooting steps.
File is Being Blocked by Zscaler Sandbox
- Review Policy Settings:
- Check the Sandbox policy configurations to verify if any existing rule matches the transaction.
- Using the Web Insights Logs, examine the **Blocked Policy Type** field to identify the specific **Blocked Policy Name** responsible for blocking the file.
| Blocked Policy Name | Blocked Policy Type |
| ------------------- | ------------------- |
| Quarantine Malicious | Sandbox |
| Catch_All | Sandbox |
- Check the file’s MD5 Hash:
- Filter Web Insights logs for the affected traffic, and click the MD5 hash link to open the Sandbox report.
[See image.](#web-insight-logs)
- If the report classifies the file as malicious (**Class Type**), then the block is expected according to the security verdict.
[See image.](#cloud-sandbox)
File is Not Sent to Zscaler Sandbox for Analysis
If the issue is the file was not sent to the Zscaler Sandbox for analysis, complete the following troubleshooting steps.
Troubleshooting
Verify that a Sandbox report is available for the file’s MD5 hash. In Web Insights logs, find the transaction for the affected file and check in the MD5 field.
- If a Sandbox report is available, this means the file was already analyzed by Zscaler Sandbox. The report includes the date and time of analysis, helping determine when the file was scanned.
- If a Sandbox report is not available, this means the file was possibly excluded from Sandbox analysis due to licensing, policy settings, or file characteristics.
[See image.](#insight-logs)
The next section describes possible reasons why a file might not be sent to the Zscaler Sandbox for analysis.
Sandbox Licensing Restrictions
Sandbox behavior depends on your Sandbox subscription (Basic vs. Advanced). For example, the Basic Sandbox subscription supports only specific file types (e.g., .exe, .dll) and file sizes (less than 2 MB).
[](/zia/about-sandbox#SandboxFileTypes)
-
-
-
-
-
-
-
-
| In-line Sandbox | Basic | Advanced |
| --------------- | ----- | -------- |
| File Types | Windows Executable (exe, exe64, scr),Windows Library (dll64, dll, ocx, sys), ZIP (zip) | .exe, .dll, .scr, .ocx, .sys, .class, .jar, .pdf, .swf, Microsoft Office documents, .apk, .zip, .rar, .7z, .bz, .bz2, .tar, .tgz, .gtar, .rtf, .ps1, .hta, .vba, script files in zipsFor a complete list of file types supported with Advance Sandbox, see the Advanced Sandbox File Types section in About Sandbox. |
| File Size | 2 MB or less | Up to 20 MB , 2 MB SWF and 50 MB APKArchive and exe are supported for 50 MB |
| AI-Driven Quarantine | ❌ | ✅ |
| File Quarantine | Not available | Yes - Hold file until confirmed Sandbox clean |
| Policy Control | Single default rule | Granular quarantine-based policies |
| Reporting | ❌ | ✅ |
| URL Categories | ❌ | ✅ |
| API | ❌ | ✅ |
| Patient 0 | ❌ | ✅ |
| In-Line Blocking | URLs in Suspicious Destinations:NudityPornographyAnonymizerFileHostShareware DownloadWeb HostMiscellaneous or UnknownOther Miscellaneous | All URL Categories |
If your current subscription is Basic Sandbox, then only files that match the Basic Sandbox criteria are analyzed. To enable broader file type support and enhanced threat detection, you must upgrade to Advanced Sandbox.
No Active Content
For Microsoft Office documents (e.g., .docx, .xlsx, .pptx, etc.) and PDFs, Zscaler Sandbox performs an initial static analysis on the ZIA Public Service Edge before determining whether it is required to send the file for deeper analysis.
- If the file is new to Zscaler cloud, then ZIA Public Service Edge checks for active content (e.g., macros, embedded scripts, suspicious objects).
- If no active content is found, the file is classified as benign and isn't sent to the Zscaler Sandbox.
- The Web Insights Logs indicate `Allowed - No Active Content` as the **Policy Action**.
[See image.](#allowed-no-active-content)
Files Aren't Delivered or Quarantine Not Releasing the Files
If a file remains in quarantine indefinitely and the user is not able to get the file, it could be due to one-time download links or dynamically generated files. Complete the following troubleshooting steps.
Troubleshooting
For expired or one-time download links, some files are hosted on one-time download links (meaning that after the initial request, the file is no longer available for retrieval using the same URL).
- Review the Web Insights logs.
- Confirm that the first URL download transaction is showing `Sent for Analysis` in the **Threat Category** field.
- Check to see if subsequent transactions for the same URL download show **Allowed**, even though the user can't download the file.
- See if the **Response Code** field in the Web Insights logs show `404 - File not found` or `403 - Forbidden` from the destination server, indicating the file is no longer accessible.
Dynamic file generation (changing hashes):
Certain websites generate a new file with each request, causing the MD5 hash to change continuously. Since each file’s MD5 is different, the file is quarantined repeatedly. Review the Web Insights logs:
Check if there are multiple** Sent for Analysis **in the **Threat Category **field for the same URL but with different MD5 hashes. This behavior indicates that each request results in a new unique file which ultimately prevents a successful file download.
[See image.](#sent-for-analysis)
Solution:
- Create a Sandbox rule for the affected domain to **Allow and Scan** files instead of holding them in quarantine. This ensures that the file is delivered immediately, while still allowing Sandbox to analyze it in the background.
[See image.](#allow-scan)
- If the file is later classified as malicious, the customer receives a Patient 0 alert.
- Ensure that exceptions are created only for necessary domains, not for broad categories of files.
[Zscaler Sandbox Logging and Alerting Issues](#sandbox-logging-alerting)
[]
There are issues such as missing Patient 0 alerts, unexpected MD5 hash, or broken Sandbox report links in the Web Insights on ZIA Admin Portal. These issues can impact visibility and response times to address a security event. Follow the applicable troubleshooting steps according to the following symptoms.
Not Receiving Patient 0 Alerts
An Advanced Sandbox subscription is required to configure and receive patient 0 alerts.
If you've configured the [first-time action](/zia/how-do-i-add-rules-sandbox-policy#first-time-action) of a [Sandbox rule](/zia/how-do-i-add-rules-sandbox-policy) to allow and scan unknown files, the Zscaler service completes the following tasks:
- Allows users to download files that match the rule criteria.
- Sends the files to the Sandbox for behavioral analysis.
A patient 0 event occurs when a user downloads an unknown file that is scanned and found to be malicious. On the [Alerts page](/zia/about-alerts), you can add the patient 0 alert and receive emails about these events within approximately two hours.
In order to receive patient 0 alerts, you must define an alert in the ZIA Admin Portal:
- Go to **Administration **> **Account Management **> **Alerts **> **Add Alert Definition** > **Alert Name** > **Patient 0**.
- Send the alert notification to a security email distribution group on the ZIA Admin Portal by going to **Publish Alerts** > **Add Alert Subscription **and enabling **Critical Patient 0 alerts**.
- View Patient 0 alerts on the [Security dashboard](/zia/about-dashboards#security). The Sandbox Patient 0 Events widget displays the patient 0 events that occurred in your organization. The following information is displayed:
- **Alert Time**: Displays the time the patient 0 alert is sent.
- **MD5**: The MD5 hash of the malicious file. Click to view the following reports:
- [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report).
- [CrowdStrike Endpoint Hits report](/zia/viewing-crowdstrike-endpoint-hits-report) (requires a [CrowdStrike integration](/zia/configuring-crowdstrike-integration)).
- **Threat**: The threat name of the malicious file. You can enter this name in the [Zscaler Threat Library](https://threatlibrary.zscaler.com/) to learn more about it.
- **Allowed Transactions**: The total number of allowed transactions that occurred with the malicious file. Click to view the transaction logs on the [Web Insights Logs](/zia/about-insights-logs) page.
- Hover over an event to see the following information:
- **File Information**: Displays the following information about the malicious file.
- **File Type**: The type of file (e.g., .exe, .dll, .pdf, etc.).
- **File Size**: The total bytes of the file.
- **MD5**: The MD5 hash of the file.
- **Users Affected**: Lists the users affected by the malicious file and their location.
MD5 Sent for Analysis After Benign Result
If the symptom is that the Quarantine page is displayed even though the same file was previously analyzed and classified as benign, this could happen when the file analysis result is not present in the ZIA Public Service Edge at the time of download.
[See image.](#md5-sent-analysis)
- Check if the MD5 consistently remains the same in **Web Insights** logs across different file download attempts. If the MD5 is different for the same file, then a reanalysis of the file is expected.
- The file analysis might not be present in the specific ZIA Public Service Edge after a file was first analyzed.
Solution
- This behavior is by design. This ensures each ZIA Public Service Edge updates independently based on geographic location.
- After the initial download in each location, the file is fast-pathed for subsequent users.
- If a file has already been analyzed as benign, users can briefly see the Quarantine page when downloading from a new location.
- In this case, the user might have to wait and retry the file download again.
MD5 in Web Insights is Not Showing as Hyperlink
Advanced Sandbox subscription is required to access Sandbox reports.
If you already have the Advanced Sandbox subscription, but the MD5 hash in Web Insights logs is not clickable (preventing you from accessing the Sandbox Report), note the following information.
Troubleshooting
The Web Insights logs Threat Super Category value is not **Sandbox. **Review the Web Insights logs. If they show **Threat Super Category** is not **Sandbox**, the MD5 is not clickable (this is the expected behavior).
[See image.](#super-threat-category-not-sandbox)
- The MD5 hash is only a clickable hyperlink when the **Threat Super Category** value is **Sandbox**.
- If the **Threat Super Category** is a different value than **Sandbox**, then the MD5 is displayed as plain text instead of a hyperlink.
Further Steps
If you still need assistance, prepare an issue summary, including any supporting information (e.g., a vulnerability scanning report from a third-party vendor) and open a support case with [Zscaler Support](/contact-support).
Provide the following data:
- The relevant configuration screenshots:
- Sandbox policy configuration
- Advanced Threat Protection Exception configuration
- The Web Insights logs with all fields selected.
- Temporarily enable **Remote Assistance**.
[]![ZULU URL Risk Analyzer](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/zulu-url-risk-analyzer.png)
[]![Zscaler Threat Library](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/zscaler-threat-library.png)
[]![Virus Total](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/virus-total.png)
[]![Zscaler Sandbox Scanning Portal](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/zscaler-sandbox-scanning-portal.png)
[]![Threat Malware Detection Protocol](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/threat-malware-detection-protocol.png)
[]![EUN Quarantine](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/eun-quarantine.png)
[]![EUN Sandbox](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/eun-sandbox.png)
[]![Web Insights Logs](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/web-insights-logs.png)
[]![Cloud Sandbox](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/cloud-sandbox.png)
[]![Insights Logs](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/insight-logs.png)
[]![Allowed No Active Content](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/allowed-no-active-content.png)
[]![Sent for Analysis](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/sent-for-analysis.png)
[]![Allow Scan](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/allow-scan.png)
[]![MD5 Sent for Analysis](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/md5-sent-analysis.png)
[]![Threat Super Category not Sandbox](/downloads/troubleshooting-runbooks/zia-security-policies-troubleshooting-runbook/super-threat-category-not-sandbox.png)