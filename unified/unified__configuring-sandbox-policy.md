# Configuring the Sandbox Policy
Source: https://help.zscaler.com/unified/configuring-sandbox-policy
PDF: https://help.zscaler.com/pdf/com/en/1494351.pdf

If you have Advanced Sandbox, you can add rules to the [Sandbox policy](/unified/about-sandbox). You can configure different rules in your Sandbox policy to apply to different sets of users or locations. Due to the wide range of risk tolerance and performance expectations, configuring the Sandbox policy might vary significantly. To learn more, see the [recommended Sandbox policy](/unified/recommended-sandbox-policy).
To configure the Sandbox policy:
- [Step 1: Enable Inbound and Outbound Traffic Inspection](#enable-inbound-outbound-traffic-inspection)
- [Step 2: Add a Sandbox Rule](#add-sandbox-rule)
The Zscaler service logs transactions in real time, and you can view the [Sandbox reports and data](/unified/viewing-sandbox-reports-and-data) under Dashboards and Analytics.
[Watch a video about Malware Protection, including how to enable inbound and outbound traffic inspection](https://fast.wistia.net/embed/iframe/hpfifrfl74)
[]You must enable inbound and outbound traffic inspection in your Malware Protection policy to have files sent for sandboxing.
To enable inbound and outbound traffic inspection:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Malware Protection**.
- Enable **Inspect Inbound Traffic** and **Inspect Outbound Traffic**.
[See image.](#seeimage1)
- Click **Save** and activate the change.
The sandbox only analyzes files that are downloaded (inbound).
[]![Screenshot of the enabled Inpsect Inbound Traffic and Inspect Outbound Traffic switches.](/downloads/zia/policies/sandbox/configuring-sandbox-policy/ZIA-Malware-Protection-Inspect-Inbound-Outbound-Traffic.png)
[Watch a video about how to add a Sandbox rule](https://fast.wistia.net/embed/iframe/k0w76q7sgb?quality=1080p)
[]To add a Sandbox rule:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Sandbox**.
-
Click **Add Sandbox Rule**.
The **Add Sandbox Rule** window appears.
-
In the **Add Sandbox Rule** window:
- **Rule Order**:** **Policy rules are evaluated in ascending numerical order (Rule 1 before Rule 2, and so on), and the rule order reflects this rule's place in the order. You can change the value, but if you've enabled [Admin Rank](/unified/about-admin-rank), your assigned admin rank determines the rule order values you can select.
- **Admin Rank**: This option appears if you enabled the [admin rank](/unified/about-admin-rank) on the [Advanced Settings](/unified/configuring-advanced-settings) page. Enter a value from 0-7 (0 is the highest rank). Your assigned [admin rank](/unified/about-admin-rank) determines the values you can select. You cannot select a rank that is higher than your own. The rule's admin rank determines the value you can select in rule order, so that a rule with a higher admin rank always precedes a rule with a lower admin rank.
- **Rule Name**: Enter a unique name for the Sandbox rule, or use the default name.
- **Rule Status**: Choose to **Enable** or **Disable** the rule. An enabled rule is actively enforced. A disabled rule is not actively enforced and doesn't lose its place in the rule order scheme. The Zscaler service simply skips it and moves to the next rule.
- **Rule Label**: Select a rule label to associate it with the rule. To learn more, see [About Rule Labels](/unified/about-rule-labels).
- **File Types**: Select the file types** **to which the rule applies. The file types you can select for your Sandbox policy include the following:
- **Archive**
- 7-Zip (7z)
- Bzip2 (bz, bz2)
- Optical Disc Image (iso)
- Tape Archive (tar)
- Roshal Archive (rar)
- Zip Archive File (zip)
- ZIP with Suspicious Script File (js, vbs, svg, ps1, hta, cmd, lnk)
- **Executable**
- Microsoft Software Installer (msi)
- Visual Basic Script (vbs)
- Windows Executable (exe)
- Windows Library (dll64, dll, ocx, sys)
- Windows PowerShell Script (ps1)
- Windows Batch File (cmd, bat)
- **Image**
- Joint Photographic Experts Group (jpeg)
- Portable Network Graphic (png)
- **Microsoft Office**
- Microsoft Excel (xls, xlsx, xlsm, xla, xlam, xlsb, slk, xltm)
- Microsoft PowerPoint (ppt, pptx, pptm, potx, ppsx, ppam, potm, ppsm)
- Microsoft RTF (rft)
- Microsoft Word (doc, docx, docm, dotx, dotm)
- **Mobile**
- Android Application Package (apk)
- **Other Documents**
- Portable Document Format (pdf)
- **Other Microsoft**
- Windows Script (wrc, wsf, wsh)
- **Python**
- Python Source Code (`.py`)
- Pickle (`.p`, `.pkl`, `.pickle`)
- Python Dynamic Module (`.pyd`)
- Python Script (`.pyw`)
- **Web Content**
- Adobe Flash (swf)
- HTML Application (hta)
- Java Applet (jar, class, applet)
-
**URL Categories**: Select **Any **to select all [URL categories](/unified/about-url-categories), or select specific URL categories. You can search for URL categories or click the **Add** icon to add a new category.
You can also select [custom TLD categories](/unified/about-tld-categories) from this field.
- **Users**:** **Select **Any** to apply the rule to all [users](/unified/about-users), or select up to 32 users under General Users. If you've enabled [Policy for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic), you can select Special Users to apply this rule to all unauthenticated users, or select specific types of unauthenticated users. You can search for users or click the **Add** icon to add a new user.
- **Groups**:** **Select **Any** to apply the rule to all [groups](/unified/about-groups), or select up to 32 groups. You can search for groups or click the **Add** icon to add a new group.
-
**Departments**:** **Select** Any** to apply the rule to all [departments](/unified/about-departments), or select up to 32 departments. If you've enabled [Policy for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic), you can select Special Departments to apply this rule to all unauthenticated transactions. You can search for departments or click the **Add** icon to add a new department.
Any rule that applies to [unauthenticated traffic](/unified/configuring-policies-unauthenticated-traffic) must apply to all groups and departments. So, if you have chosen to apply this rule to unauthenticated traffic for either **Users** or **Departments**, select **Any **from the drop-down menus for **Groups** and **Departments**.
-
**Locations**:** **Select **Any** to apply the rule to all [locations](/unified/about-locations), or select up to 32 locations. You can also search for a location or click the **Add** icon to add a new location.
Contact Zscaler Support to increase the limit of **Users**, **Groups**, **Departments**, or **Locations**.
- **Location Groups**: Select **Any** to apply the rule to all [location groups](/unified/about-location-groups), or select up to 32 location groups. You can also search for a location group.
- **Sandbox Categories**: Select the types of malicious files.
- **Sandbox Adware**: Files that automatically render advertisements/install adware. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Sandbox Malware/Botnet**: Files that behave like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware. This is a catchall category for any malicious file that doesn't fall under the other sandbox categories. Most sandbox-classified files aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead, the Zscaler service categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **Sandbox P2P/Anonymizer**: Files that contain anonymizers and P2P clients. The Zscaler service detects if the file is exhibiting behavior consistent with P2P/anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
- **Sandbox Offsec Tools**: Offensive security tools are often the same tools threat actors might leverage, but for different purposes. While threat actors can use these tools for malicious reasons, they can also be used by cyber security professionals.
- **Sandbox Ransomware**: A type of malware that prevents or limits users from accessing their system, either by locking the system or by locking the user's files, until a ransom is paid.
- **Sandbox Suspicious**: Files that exhibit some malicious behaviors but are not fully classified as malware.
- **ZPA Application Segment**: Inspection of application segments of Private Applications for security and data protection services enables leveraging single posture for securing Internet & SaaS and Private Applications.
Select up to 255 application segments of Private Applications. Selecting no value ignores the criterion in the policy evaluation. The list displays only those application segments of Private Applications that have the [Source IP Anchoring](/unified/understanding-source-ip-anchoring) option enabled.
- []**Protocols**: Select the protocols to which the rule applies.
- **FTP over HTTP**: File downloads from FTP over HTTP websites.
- **HTTP**: File downloads from HTTP websites.
- **HTTPS**: File downloads from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: File downloads from native FTP servers.
-
[]**First-Time Action**: Choose the action that Zscaler takes when a user downloads an unknown file.
- **Allow and do not scan**:** **Allow users to download the unknown file. The service doesn't send the file to the sandbox for behavioral analysis.
- **Allow and scan**:** **Allow users to download the unknown file. The service sends the unknown file to the sandbox for behavioral analysis. If the file is found to be malicious, this becomes a patient 0 event. You can [configure the Patient 0 alert](/unified/configuring-patient-0-alert) to receive emails about these events.
- **Quarantine**:** **Quarantines the file while its being analyzed. The service displays a [quarantine notification](/unified/about-sandbox-end-user-notifications#sandbox-quarantine-notification). If the file is safe, the user can download the file after the analysis. If unsafe, the service blocks the download.
-
**Quarantine and Isolate**: Sandbox and browser isolation integration allows users to access unknown Microsoft Office and PDF documents as view-only in an isolated browser in real-time without waiting for the final sandbox verdict. The end user can download the file if the verdict is benign in the original file. If the sandbox verdict is suspicious or malicious, you can choose to receive a flattened PDF after content disarmament to remove the suspicious or malicious content.
The Internet & SaaS Isolation Advanced Plus license is needed to support the **Quarantine and Isolate** action for the Advanced Cloud sandbox policy for the following supported file types: Microsoft Excel, PowerPoint, Word, Rich Text Format, and PDF. To learn more, see [Sandbox Integration with Isolation](/unified/sandbox-integration-isolation).
- **Minimum Threat Score**: If you choose **Sandbox Suspicious** for the **Sandbox Categories** and **Quarantine** for **First-Time Action**, you can enter a custom minimum threat score value between 40 and 70 to allow downloading of files below the entered value. The default value is 0, but manually entering a value can be useful if you work with files that might otherwise be flagged as a threat.
The Zscaler service does an initial sandbox static analysis for unknown PDF or Microsoft Office files to check if they contain active content. If they do, they are sent to the sandbox for behavioral analysis. If they don't, they are classified as benign and allowed to download.
-
**AI Instant Verdict**: If you choose **Quarantine** or **Allow and Scan** for **First-Time Action**, you can enable **AI Instant Verdict** to have the Zscaler service use AI analysis to instantly assign threat scores to unknown files. If AI analysis assigns a threat score higher than 90, the Zscaler service identifies the file as high-confidence malicious and blocks download.
[See image.](#ai-instant-quarantine)
If AI analysis assigns a threat score between 70-90 and the sandbox policy **First-Time Action** is **Allow and scan**, the file is sent to quarantine for further analysis. After analysis, the service allows or blocks the file download based on your configured **Action for Subsequent Downloads**.
[See image.](#ai-instant-allow-and-scan)
-
**Action for Subsequent Downloads**: Choose to **Allow** or **Block** downloads of sandbox-classified files (files the Sandbox previously analyzed) that match the criteria above. If you choose **Block** and a user attempts to download a malicious Sandbox classified file, the service displays a [block notification](/unified/about-sandbox-end-user-notifications#sandbox-block-notification) and prevents the download.
If you choose **Allow** and a user attempts to download a malicious sandbox-classified file, the service allows the download. Zscaler doesn't recommend this setting, unless it's for testing or exceptions.
- **Description**: Optionally, enter additional notes or information. The description cannot exceed 10,240 characters.
[See image.](#add-sandbox-rule-window)
- Click **Save** and activate the change.
[]![Screenshot of the AI Instant Verdict Option with Quarantine.](/downloads/zia/policies/sandbox/configuring-sandbox-policy/ZIA-Sandbox-AI-Instant-Verdict-Quarantine.png)
[]![Screenshot of the AI Instant Verdict Option with Allow and Scan.](/downloads/zia/policies/sandbox/configuring-sandbox-policy/ZIA-Sandbox-AI-Instant-Verdict-Allow-and-scan.png)
[]![Screenshot of the Add Sandbox Rule window.](/downloads/zia/policies/sandbox/configuring-sandbox-policy/ZIA-Sandbox-Add-Rule.png)