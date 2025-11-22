# About FTP Control
Source: https://help.zscaler.com/unified/about-ftp-control
PDF: https://help.zscaler.com/pdf/com/en/1494111.pdf

By default, the Zscaler service doesn't allow users from a location to upload or download files from FTP sites that use FTP over HTTP. Only native FTP traffic is allowed. With FTP Control, Zscaler provides access control for native FTP and FTP over HTTP traffic. This can be particularly useful if you are using a Zscaler Client Connector (formerly known as Zscaler App or Z App) or PAC based deployment, as they only support FTP over HTTP traffic. FTP Control also extracts files and runs a security scan.
FTP Control provides the following benefits and enables you to:
- Manage your organization's FTP traffic by monitoring users' access to FTP servers using FTP (only passive FTP), FTPS, and FTP over HTTPS protocol.
- Inspect your users' FTP traffic, including passive FTP, FTPS, and FTP over HTTPS traffic, and protect the traffic against malicious software using the Malware Protection policy.
- Control FTP traffic using protocol-based conditions in Data Loss Prevention (DLP), Sandbox, File Type Control, URL Filtering, and Bandwidth Control policies.
There are multiple levels of FTP Control:
- You can configure the FTP Control policy to allow access to specific FTP sites.
- If you have [Malware Protection](/unified/configuring-malware-protection-policy), you can scan FTP over HTTP traffic and native FTP traffic in real time. To learn more, see [Configuring the FTP Control Policy](/unified/configuring-ftp-control-policy).
- If you have [Data Loss Prevention (DLP)](/unified/configuring-dlp-policy-rules-content-inspection#protocols), [Sandbox](/unified/configuring-sandbox-policy), [File Type Control](/unified/configuring-file-type-control-policy), [URL Filtering](/unified/configuring-url-filtering-policy#protocols), and [Bandwidth Control](/unified/adding-rules-bandwidth-control-policy#protocols), you can configure those policies based on protocols (e.g., FTP over HTTP and native FTP).
- Complete FTP logging in [Firewall Insights](/unified/about-insights).
The FTP Control policy applies to traffic from the known locations of an organization. However, if a remote user uses a dedicated port, then the service supports FTP over HTTP for them. When they use a dedicated port, if their browser connects to FTP sites and downloads files, the service will be able to scan the content for viruses and spyware.
[URL Filtering](/unified/about-url-filtering) policy rules take precedence over the FTP Control policy. For example, if you have a URL Filtering Policy rule that blocks access to Adult Material, the Zscaler service will block users who try to transfer files from ftp://ftp.site.com. Also, user-, department-, or group-level URL filtering rules blocking access to specific sites will not be enforced for FTP sites because FTP does not support cookies. Only rules applied to all users will be enforced. For example, if you have a catch-all URL Filtering rule that blocks access to Adult Material, anybody trying to FTP to ftp://ftp.site.com will get blocked. To learn how the FTP policy fits into the overall order of policy enforcement, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
The service supports passive FTP only. If the destination server does not support passive FTP, the service generates an alert message to this effect in the end user's browser. The service also supports FTPS (FTP over TLS) in passive mode. You can either set up implicit or explicit FTPS. To use explicit FTPS, set a proxy in the FTP client.
About the FTP Control Page
On the FTP Control page (Policies > Access Control > Firewall > FTP Control), you can do the following:
- [Configure the FTP Control Policy](/unified/configuring-ftp-control-policy).
- [View the Recommended Policy](/unified/recommended-ftp-control-policy).
![Numbered screenshot of FTP Control page](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policies/ftp-control/about-ftp-control/zia-about-ftp.png)