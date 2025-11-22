# Configuring the FTP Control Policy
Source: https://help.zscaler.com/unified/configuring-ftp-control-policy
PDF: https://help.zscaler.com/pdf/com/en/1494116.pdf

You can configure the [FTP Control](/unified/about-ftp-control) policy to allow access to specific sites. With [Malware Protection](/unified/configuring-malware-protection-policy), you can also scan FTP over HTTP traffic and FTP traffic in real time.
To configure the FTP Control policy:
- [1. Allow or block FTP over HTTP traffic and native FTP traffic.](#allow-block)
- [2. Enable or disable scanning for FTP traffic.](#scanning)
[]From the [FTP Control](/unified/about-ftp-control) page, you can allow or block FTP over HTTP traffic. You can also allow or block native FTP traffic by URL categories or specified URLs.
To configure the FTP Control policy:
- Go to **Policies** > **Access Control** > **Firewall** > **FTP Control**.
- Complete the following:
- **Allow FTP over HTTP**:** **By default, the Zscaler service doesn't allow users from a location to upload or download files from FTP sites that use FTP over HTTP. Select this to enable browsers to connect to FTP over HTTP sites and download files. If a remote user uses a dedicated port, then the service supports FTP over HTTP for them.
- **Allow Native FTP**: Select to enable users to connect to native FTP sites and download files.
If you enable this option, you will see the following option:
- **Allow Any URL Category**: Select this to allow FTP traffic for all [URL categories](/unified/about-url-categories). The policy applies to traffic from the known locations of an organization.
If you enable this, you can configure the FTP Control policy to allow access to specific sites. You can select from the following:
- **Allowed URL Categories**: You can select [URL super-categories, categories, or both](/unified/about-url-categories). You can select any number of categories. You can also search for categories or add a custom category by clicking the **Add** icon.
-
**Allowed URLs**: Enter the URLs for which native FTP traffic will be allowed. You can add up to 25,000 URLs. For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25,000 items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window will appear.
This feature is successful when the FTP proxy can retrieve the URLs. If you are using transparent traffic forwarding, enter an IP address instead of a URL. Alternatively, Zscaler recommends implementing one of the following workarounds:
- FQDN-based Firewall rule set to Allow
- Forward proxy mode
- FTP traffic over HTTP CONNECT
- Click **Save** and activate the change.
[]From the [Malware Protection](/unified/configuring-malware-protection-policy) page, you can enable or disable scanning for FTP over HTTP traffic and native FTP traffic.
To inspect FTP over HTTP traffic and native FTP traffic:
- Go to **Policies **> **Cybersecurity** > **Inline Security** > **Malware Protection**.
- In the **Protocol Inspection **section, enable the following switches to scan FTP traffic:
- **Inspect FTP over HTTP**: Enable to scan FTP over HTTP traffic in real time. The Traffic Inspection setting determines whether inbound, outbound, or both types of traffic is scanned. It scans all files, including those with up to 5 layers of recursive compression.
- **Inspect FTP**: Enable to scan FTP traffic in real time. The Traffic Inspection setting determines whether inbound, outbound, or both types of traffic is scanned. It scans all files, including those with up to 5 layers of recursive compression.
You can also apply [Data Loss Prevention (DLP)](/unified/about-data-loss-prevention), [Sandbox](/unified/about-sandbox), and [File Type Control](/unified/about-file-type-control) policies to files extracted from the above protocols.