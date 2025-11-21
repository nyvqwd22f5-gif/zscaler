# Configuring the Default Sandbox Rule
Source: https://help.zscaler.com/zia/configuring-default-sandbox-rule
PDF: https://help.zscaler.com/pdf/com/en/1399816.pdf

The default rule for the [Sandbox policy](/zia/about-sandbox) blocks all Windows executables and Windows library files from suspicious URLs that contain certain malicious file types. Additionally, if a user downloads a Windows executable or Windows library file from a suspicious URL, and it contains an unknown file, the default action is to allow users to download the file then send the file to the Sandbox engine for analysis.
To configure the default Sandbox rule:
- [Step 1: Enable Inbound and Outbound Traffic Inspection](#enable-inbound-outbound-traffic-inspection)
- [Step 2: Edit the Default Sandbox Rule](#edit-default-sandbox-rule)
The Zscaler service [logs](/zia/viewing-sandbox-reports-data) all Sandbox transactions on the [Web Insights Logs](/zia/about-insights-logs) page. If a malicious file is allowed because it doesn't match criteria of the default Sandbox rule, the Zscaler service displays **Not Subscribed** in the **Threat Name** column.
[See image.](#seeimage1)
[]You must enable inbound and outbound traffic inspection in your Malware Protection policy to have files sent for sandboxing.
To enable inbound and outbound traffic inspection:
- Go to **Policy **>** Malware Protection**.
- Enable **Inspect Inbound Traffic** and **Inspect Outbound Traffic**.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
The Sandbox only analyzes files that are downloaded (inbound).
[]![Screenshot of the enabled Inpsect Inbound Traffic and Inspect Outbound Traffic switches.](/downloads/zia/policies/sandbox/configuring-sandbox-policy/ZIA-Malware-Protection-Inspect-Inbound-Outbound-Traffic.png)
[]You can change the settings of the default Sandbox rule, but you can't delete it. Zscaler recommends that you don't change the default settings.
To edit the default Sandbox rule:
- Go to** Policy **> **Sandbox**.
- Click the **Edit** icon next to the default rule.
The **Edit Sandbox Rule** window appears.
- In the **Edit Sandbox Rule** window:
- **Rule Status**: The default Sandbox rule is enabled and enforced. You can modify this field, but Zscaler doesn't recommend doing so.
- **Rule Label**: The default rule is associated with the selected label. You can modify this field.
- **File Types**: The default rule analyzes Windows executables and Windows library files. It also analyzes these files if they’re contained in ZIP archive files (.zip). With the Standard Sandbox subscription, the service only analyzes files that are equal to 2 MB or less. You can't modify this field.
- **URL Categories**: The default rule analyzes the file types above if they are downloaded from URLs in **Suspicious Destinations**. Suspicious destinations include the following URL categories:
- Nudity
- Pornography
- Anonymizer
- FileHost
- Shareware Download
- Web Host
- Miscellaneous or Unknown
- Other Miscellaneous
You can't modify this field.
- **Sandbox Categories**: The default rule applies to the following malicious file types
- **Sandbox Adware**: Files that automatically render advertisements/install adware. Often, these advertisements are unwanted and can lead to spyware or other grayware-oriented privacy violations.
- **Sandbox Malware/Botnet**: Files that behave like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware. This is a catchall category for any malicious file that doesn't fall under the other Sandbox categories. Most Sandbox-classified files aren't clearly known to be a specific threat or malware family-oriented because there aren't specific signatures or indicators to categorize the file. Instead the Zscaler service categorizes the file based on an aggregation of the file’s OS and application behaviors and network activity.
- **Sandbox P2P/Anonymizer**: Files that contain anonymizers and P2P clients. The Zscaler service detects if the file is exhibiting behavior consistent with P2P/anonymizer programs, such as Tor Browser or other VPN services, that essentially make a user’s internet activity untraceable.
-
**ZPA Application Segment**: Inspection of ZPA application segments for security and data protection services enables leveraging single posture for securing internet/SaaS and private applications.
Select up to 255 ZPA Application Segments. Selecting no value ignores the criterion in the policy evaluation. The list displays only those ZPA application segments that have the [Source IP Anchor](/zia/understanding-source-ip-anchoring) option enabled.
If you select the** Inspect App Segments** option from the list, then the configured rule applies to all the ZPA application segments paired to your ZIA tenant. This option is only available if the **SIPA App Segments** subscription is enabled for your organization.
[See image.](#zpa-application-segment-image)
You can make changes if necessary, but Zscaler recommends that you don't modify this field.
- **Protocols**: The default rule applies to file downloads from the following protocols.
- **FTP over HTTP**: File downloads from FTP over HTTP websites.
- **HTTP**: File downloads from HTTP websites.
- **HTTPS**: File downloads from HTTP websites encrypted by TLS/SSL.
- **Native FTP**: File downloads from native FTP servers.
You can't modify this field.
- **First-Time Action**: If a user downloads a Windows executable or Windows library file from a suspicious URL, and it contains an unknown file, the default action is to allow users to download the file then send the file to the Sandbox engine for analysis. You can't modify this field.
- **AI Instant Verdict**: This field is applicable only if the **First-Time Action** is **Quarantine** or **Allow and Scan**. You can’t modify this field for the default sandbox rule.
- **Action for Subsequent Downloads**:** **The default action is to **Block** Sandbox classified files (files the Sandbox previously analyzed) that match the criteria above. If a user attempts to download a malicious Sandbox classified file, the service displays a [block notification](/zia/sandbox-end-user-notifications-euns#sandbox-block-notification) and prevents the download.
If you choose **Allow**, the service allows users to download the files even if they're malicious, but logs the transactions. You can modify this field, but Zscaler doesn't recommend doing so.
Click **Save**.
[See image.](#seeimage2c)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
If a file doesn't match the criteria of the default Sandbox rule, then the file download is allowed even if it's malicious.
[]****![Screenshot of a Sandbox malware with the Not Subscribed tag in the Threa Name column](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Web-Insights-Logs-Not-Subscribed.png)
****
[]![Screenshot of the Edit Sandbox Rule window for the default Sandbox rule.](/downloads/zia/policies/sandbox/configuring-default-sandbox-rule/ZIA-Sandbox-Edit-Default-Rule.png)
![Screenshot of the Inspect App Segments option for the ZPA Application Segment field](/downloads/zia/policies/sandbox/configuring-default-sandbox-rule/zia-configuring-default-sandbox-zpa-app-segments-inspect-app-segments-option.png)
[]