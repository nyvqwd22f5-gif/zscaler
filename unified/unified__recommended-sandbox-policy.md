# Recommended Sandbox Policy
Source: https://help.zscaler.com/unified/recommended-sandbox-policy
PDF: https://help.zscaler.com/pdf/com/en/1494381.pdf

The default Sandbox rule blocks malicious Windows executables and Windows library files that users attempt to download from the following suspicious URL Categories:
- Nudity
- Pornography
- Anonymizer
- FileHost
- Shareware Download
- Web Host
- Miscellaneous or Unknown
- Other Miscellaneous
The default Sandbox rule analyzes and blocks Windows executable and Windows library files that are 2 MB or less.
If you have Advanced Sandbox, you can add rules to the policy. Due to the wide range of risk tolerance and performance expectations, configuring the Sandbox policy might vary significantly from the recommended policy below. Zscaler recommends you configure the policy according to your organization’s tolerance:
- **Low Tolerance for Malicious Files**: If your organization has low tolerance for downloading malware, you can choose **Quarantine** for **First-Time Action** on a majority of URL Categories. Organizations that might choose this option include:
- Financial institutions or organizations with high–value transactions.
- Organizations, departments, and legal institutions with access to sensitive data.
- **Low Tolerance for Quarantining Files**: If your organization has low tolerance for download delays and end–user interruptions from quarantining files, you can choose **Allow and Scan** for **First-Time Action** on all or a majority of URL Categories. Organizations that might choose this option include:
- Organizations with engineering or research labs that regularly download Windows executables or other files “suspicious” in nature, despite not having malicious intent.
- Organizations that regularly download or exchange diverse files with other organizations.
- **Low Tolerance for Suspicious Files**: If your organization has low tolerance for miscellaneous files employees might want to download or install, you can choose **Allow and Scan** for **First-Time Action** on a variety of file types including Archives, Executables, and PDF files. Organizations that might choose this option include:
- Organizations with employees that need to use third–party software to complete their tasks, which might include files that can be suspicious if downloaded from the wrong places.
- Organizations that regularly download or work with PDF or ZIP files which could come from unverified sources.
Zscaler recommends you [configure](/unified/configuring-sandbox-policy) the following [Sandbox](/unified/about-sandbox) policy.
Example Sandbox Rules
The following are some sample Sandbox policy rules that Zscaler recommends. These rules apply to all users, groups, departments, locations and location groups.
**Rule 1**: **Quarantine Executables**
The following table provides the rule criteria:
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
-
-
-
-
| File Types | URL Categories | Sandbox Categories | First-time Action | AI Instant Verdict | Subsequent Action |
| ---------- | -------------- | ------------------ | ----------------- | ------------------ | ----------------- |
| Windows Executables (exe64)Windows Library (dll64, dll,ocx,sys, scr) | NudityPornographyAnonymizerShareware DownloadMiscellaneous or UnknownOther Miscellaneous | Sandbox AdwareSandbox Malware/BotnetSandbox Offsec ToolsSandbox P2P/AnonymizerSandbox RansomwareSandbox Suspicious | Quarantine | Enabled | Block |
**Rule 2**: **Quarantine Unknown Office Files**
The following table provides the rule criteria:
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
-
-
| File Types | URL Categories | Sandbox Categories | First-time Action | AI Instant Verdict | Subsequent Action |
| ---------- | -------------- | ------------------ | ----------------- | ------------------ | ----------------- |
| Microsoft Excel (xls, xlsx, xlsn, etc.)Microsoft PowerPoint (ppt, pptx, ppm, potx, etc.)Microsoft RTF (rtf)Microsoft Word (doc, docx, docm, dotx, etc.) | Miscellaneous or UnknownOther Miscellaneous | Sandbox AdwareSandbox Malware/BotnetSandbox Offsec ToolsSandbox P2P/AnonymizerSandbox RansomwareSandbox Suspicious | Quarantine | Enabled | Block |
**Rule 3**: **Quarantine Unknown PDF Files**
The following table provides the rule criteria:
-
-
-
-
-
-
-
-
| File Types | URL Categories | Sandbox Categories | First-time Action | AI Instant Verdict | Subsequent Action |
| ---------- | -------------- | ------------------ | ----------------- | ------------------ | ----------------- |
| PDF Documents (pdf) | Miscellaneous or UnknownOther Miscellaneous | Sandbox AdwareSandbox Malware/BotnetSandbox Offsec ToolsSandbox P2P/AnonymizerSandbox RansomwareSandbox Suspicious | Quarantine | N/A | Block |
**Sandbox Default Rule**
The following table provides the rule criteria:
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
| File Types | URL Categories | Sandbox Categories | First-time Action | AI Instant Verdict | Subsequent Action |
| ---------- | -------------- | ------------------ | ----------------- | ------------------ | ----------------- |
| Windows Executables (exe, exec63, scr).Windows Library (dll64, ocx, sys).ZIP (zip) | Suspicious Destinations | Sandbox AdwareSandbox Malware/BotnetSandbox Offsec ToolsSandbox P2P/AnonymizerSandbox RansomwareSandbox Suspicious | Allow and scan first time | N/A | Block subsequent downloads |