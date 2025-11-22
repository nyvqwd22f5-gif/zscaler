# About Sandbox
Source: https://help.zscaler.com/unified/about-sandbox
PDF: https://help.zscaler.com/pdf/com/en/1494341.pdf

[]Sandbox provides an additional layer of security against zero-day threats and Advanced Persistent Threats (APTs) through Sandbox analysis, an integrated file behavioral analysis. To ensure your organization's web security, the Zscaler service runs and analyzes files in a virtual environment to detect malicious behavior. It propagates a hash of malicious files to all Internet & SaaS Public Service Edges throughout the cloud, effectively maintaining a real time denylist so it can prevent users anywhere in the world from downloading malicious files. Additionally, you can use artificial intelligence (AI) analysis in the rules that make up your [Sandbox policy](/unified/configuring-sandbox-policy) to instantly determine the likelihood of a file being benign or suspicious.
Sandbox provides the following benefits and allows you to:
- Analyze unknown files in a virtual environment to detect malicious behavior.
- Hash propagation of malicious files across all Internet & SaaS Public Service Edges to protect users anywhere in the world from downloading malicious files.
- Use AI tools to provide real-time analysis of unknown files.
About the Default Sandbox Rule
By default, the sandbox does the following:
- It analyzes Windows executable files and Windows library files (such as dynamic-link libraries) that are 2 MB or less and downloaded from URLs in suspicious URL categories. The suspicious URL categories include:
- Nudity
- Pornography
- Anonymizer
- FileHost
- Shareware Download
- Web Host
- Miscellaneous or Unknown
- Other Miscellaneous
The service also analyzes these files if they’re contained in ZIP archive files (.zip).
Zscaler Sandbox supports file sizes up to 50MB for Windows EXEs, Android APKs, and Archive file types.
- When users attempt to download files that meet the preceding criteria and the service has never seen the files before, the service allows the downloads and sends the files to the Sandbox engine for analysis.
- It blocks files that contain the following types of malicious files:
- **Adware**: Files that automatically render advertisements/install adware. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Malware & Botnets**: Files that behave like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware. This is a catchall category for any malicious file that doesn't fall under the other Sandbox categories. Most Sandbox-classified files aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead, it categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **P2P & Anonymizers**: Files that exhibit behaviors consistent with P2P/anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
- It blocks malicious file downloads from any of the following protocols:
- **FTP over HTTP**: File downloads from FTP over HTTP websites.
- **HTTP**: File downloads from HTTP websites.
- **HTTPS**: File downloads from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: File downloads from native FTP servers.
[See image.](#seeimage)
You can [modify the default rule](/unified/configuring-default-sandbox-rule), but it isn't recommended.
If you've configured the Sandbox policy to block known malicious files and a user attempts to download a malicious file, the service displays a notification explaining that the file was blocked because it is malicious. The service also logs transactions in real time, and you can view Sandbox reports and data under Dashboard and Analytics.
To learn how this policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
Advanced Sandbox Features
If your organization has Advanced Sandbox, you have the following benefits:
- You can [add rules](/unified/configuring-sandbox-policy) to the Sandbox policy. Rules are applied in the rule order list from first to last. The default rule is always the last rule checked.
- You can scan files sized higher than 2 MB.
- You can specify which file types the sandbox analyzes. Zscaler supports sandboxing for the following:
- [File Types](#SandboxFileTypes)
- You can enable artificial intelligence (AI) prescanning for unknown files in quarantine.
- By default, Advanced Sandbox allows for 100 API file submissions per day. This quota can be raised by contacting your Zscaler Account team or Zscaler Support.
- You can compare the report outputs of an unpatched vulnerable VM with a fully patched secure VM to identify mitigation effectiveness and potential risk. To learn more, see [Viewing Sandbox Reports and Data](/unified/viewing-sandbox-reports-and-data).
About the Sandbox Page
If you don't have Advanced Sandbox, some of the following options won't be available.
On the Sandbox page (Policies > Cybersecurity > Inline Security > Sandbox), you can do the following:
- [Add rules to the Sandbox policy](/unified/configuring-default-sandbox-rule).
- [View the recommended policy for Sandbox](/unified/recommended-sandbox-policy).
- Select one of the following **View by** option to see the Sandbox rules accordingly:
- **Rule Order**: Displays the rules based on the rule order. By default, the rules are listed in the ascending rule order.
[See image.](#rule-order-sandbox)
- **Rule Label**: Displays the rules based on the rule labels. The rules are grouped under the associated rule labels.
You can expand or collapse all the rule labels using the **Expand All** or **Collapse All** buttons.
[See image.](#rule-label-sandbox)
- Search for a configured Sandbox rule.
- View a list of all configured Sandbox rules. For each rule, you can see the following:
- **Rule Order**: The rule order number. Sandbox rules are evaluated in ascending numerical order. The default rule is evaluated last.
- **Admin Rank**: The assigned [admin rank](/unified/about-admin-rank) for the rule. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking).
- **Rule Name**: The name of the rule.
- **Criteria**: The criteria of the rule (e.g., Sandbox Categories, File Types, Protocols, etc.).
- **Action**: Displays the configured Sandbox actions of the rule.
- **Label and Description**: The label and description of the policy rule, if available.
- [Modify the table and its columns](/unified/using-tables).
- Edit a configured Sandbox rule.
- Duplicate a configured Sandbox rule.
****![Screenshot of Sandbox page and its features](/downloads/zia/policies/sandbox/about-sandbox/About%20Sandbox%20Details.png)
****
- []Archive
- 7-Zip
- Bzip2
- Tar
- RAR
- ZIP
- ZIP with Suspicious Script File
- Executable
- Visual Basic Script
- Windows Executable
- Windows Library
- Windows PowerShell Script
- Microsoft Office
- Microsoft Excel
- Microsoft PowerPoint
- Microsoft RTF
- Microsoft Word
- Mobile
- Android Application Package
- Other Documents
- Portable Document Format
- Web Content
- Adobe Flash
- HTML Application
- Java Applet
[]![Screenshot of the Edit Sandbox Rule window for the default Sandbox rule.](/downloads/zia/policies/sandbox/about-sandbox/Sandbox%20Add%20Rule.png)
[]![Screenshot of the Sandbox Rule window with Rule Order view selected.](/downloads/zia/policies/sandbox/about-sandbox/ZIA-Sandbox-Policy-Page-Viewby-Rule-Order.png)
[]![Screenshot of the Sandbox Rule window with Rule Label view selected.](/downloads/zia/policies/sandbox/about-sandbox/ZIA-Sandbox-Policy-Page-Viewby-Rule-Label.png)