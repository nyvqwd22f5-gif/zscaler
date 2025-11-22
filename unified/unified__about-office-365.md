# About Office 365
Source: https://help.zscaler.com/unified/about-office-365
PDF: https://help.zscaler.com/pdf/com/en/1494811.pdf

Zscaler enables direct-to-cloud access for internet-based cloud applications, like Microsoft Office 365. This is achieved by enabling organizations to send traffic directly to application servers over the internet, instead of backhauling traffic over costly MPLS circuits. Zscaler simplifies your Office 365 deployment by taking advantage of our global direct-to-cloud network, which will improve user experience and application performance for your organization. To learn more, see [Source IP Anchoring Configuration Guide for Office 365 Conditional Access](/unified/source-ip-anchoring-configuration-guide-office-365-conditional-access).
[]The Zscaler service complies with Microsoft’s Office 365 connectivity principles:
- Differentiate Traffic: Identify and differentiate Office 365 traffic using Microsoft-published endpoints data
- Egress Connections: Egress Office 365 data connections as close to the user as practical with matching DNS resolution
- Optimize Route Length: Avoid network hairpins and optimize connectivity directly into the nearest entry point into Microsoft’s network
- Assess Network Security: Assess inspecting traffic with proxies, traffic inspection devices
In general, for cloud-based applications going direct-to-cloud, having local internet breakouts for your branch office locations is key. Because Office 365 is a trusted enterprise cloud application, Zscaler can securely connect users to our cloud service. Zscaler's direct peering relationship with Microsoft allows us to extend our secure connectivity to Office 365, using their principals and recommendations.
Understanding Office 365 Applications
Deploying Office 365 (O365) using the traditional appliance model has certain challenges, but the Zscaler service has solutions to help alleviate these issues:
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
-
-
-
| Apps | Appliance Model Challenges | Zscaler Service Solutions |
| ---- | -------------------------- | ------------------------- |
| Exchange Online | Latency due to distance/operationsOutlook requires around 5 to 20 TCP connections per userDesigned for transient rather than persistent connections | Directing Peering with Microsoft O365 backbone networkUnlimited persistent connections without worrying about scale |
| Skype for BusinessMicrosoft Teams | Traditional proxies do not handle UDP trafficAdditional persistent connections by clientMedia traffic can add high load | Identify and automate IP/FQDN ports and protocols related to Skype and Microsoft TeamsBandwidth management controls |
| SharePoint OnlineOneDrive for Business | Additional persistent connections by clientLarge amount of data movementSame IP used for all connections | TCP optimizations to support higher window sizes for faster file uploads and downloads |
Managing Office 365 Authentication and Directory Services
User authentication is required to implement group and user policies and to leverage the Office 365 application usage and reporting capabilities of the Zscaler service. Zscaler supports authentication using:
- Microsoft Active Directory Domain Services (AD)
- Microsoft Azure Active Directory (Azure AD) for SAML-based Single Sign-On (SSO)
- Microsoft Active Directory Federation Services (ADFS) for SAML-based SSO
Zscaler supports authentication with an organization’s AD infrastructure using various methods including AD synchronization, SAML-based SSO using ADFS, and Kerberos.
With Office 365, mail servers and other collaboration services are located in data centers managed by Microsoft. Deploying ADFS along with Directory Synchronization (DirSync) is necessary to enable login to Office 365. This allows Office 365 to read and understand user/groups/departments and other directory objects from your organization’s on-premises AD. Office 365 uses Azure AD in the cloud, which is capable of syncing with an on-premises AD. Therefore, your organization does not need to replace its on-premises AD to use Office 365. To learn more, refer to the [Microsoft Technical documentation](https://docs.microsoft.com/en-us/office365/enterprise/deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure).
Managing Office 365 Content Inspection and Security
Office 365 applications rely on tunnel protocols like MAPI/RPC over HTTPS (Outlook) and on non-web protocols like RTMP, SIP (Lync) and Autodiscover (for all Office apps) for data transfers. To be in compliance with Microsoft's [connectivity principals and recommendations](#MS_conn_principals), you can enable the [Microsoft-Recommended One Click Office 365 Configuration](/unified/about-microsoft-one-click-options) for all Office 365 application URLs.
If your organization has a requirement to inspect Office 365 web apps, such as SharePoint, Yammer, and Office online, which run within a web browser, then content inspection and [SSL Inspection](/unified/about-ssl-inspection) can be enabled using the [Office 365 One Click Configuration](/unified/about-microsoft-one-click-options) option; where you can choose individual cloud applications. However, Zscaler strongly recommends using the [Microsoft-Recommended One Click Office 365 Configuration](/unified/about-microsoft-one-click-options) for better performance.
In addition, you can also use Zscaler's [Advanced Threat Protection](/unified/configuring-advanced-threat-protection-policy) (ATP), [File Type Control](/unified/about-file-type-control), [Data Loss Prevention (DLP)](/unified/about-data-loss-prevention), and [Sandbox](/unified/about-sandbox) to report any suspicious files and detect potential malware on your traffic.
Managing Bandwidth Control
Deploying a local internet breakout for Office 365 takes the load off backhauled MPLS networks. It also makes sense to use the same internet breakout for general internet bound traffic. However, you must ensure that the general browsing traffic doesn’t saturate the internet link and cause congestion for Office 365 traffic. Zscaler provides granular bandwidth controls to define guaranteed bandwidth for applications and constrain recreational traffic (e.g., streaming media traffic, social media traffic) when internet links are saturated. To define a bandwidth management policy for Office 365, Zscaler recommends that you add Office 365 to a bandwidth class and then define the appropriate bandwidth rule for that class. To learn more, see [Adding Rules to the Bandwidth Control Policy](/unified/adding-rules-bandwidth-control-policy) and [About Bandwidth Classes](/unified/about-bandwidth-classes). If you plan to deploy the OneDrive sync app and want to estimate the bandwidth users will need for syncing, refer to the [Microsoft Technical documentation](https://docs.microsoft.com/en-us/onedrive/network-utilization-planning#create-a-windows-qos-policy-for-the-onedrive-sync-client).