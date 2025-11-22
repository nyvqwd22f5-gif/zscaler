# ZIA Policy Leading Practices Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/zia-policy-leading-practices-guide
PDF: https://help.zscaler.com/pdf/com/en/1456801.pdf

Zscaler Internet Access (ZIA) is a security and traffic forwarding service running inline to your organization’s traffic. ZIA controls your traffic using simple-to-configure granular policies.
This document explores the policy configuration areas available to administrators. Understanding how to configure ZIA policies is crucial to securing your environment, maintaining user experience, and supporting productivity.
URL Filtering and Cloud App Control limit exposure to certain types of web content by allowing or restricting user access. A well-configured policy restricts or permits web content access without disrupting the end users or their experience.
To learn more, see [Understanding Policy Enforcement](/zia/about-policy-enforcement).
Overview
The following sections provide an overview of the important concepts in configuring Zscaler security policies.
Zscaler Service Modules
ZIA uses full-featured inline proxies called [ZIA Public Service Edges](/zia/about-zscaler-enforcement-nodes) to inspect and enforce policies on traffic entering or leaving your organization. ZIA Public Service Edges feature Single-Scan Multi-Action (SSMA) technology that handles the traffic inspection and policy execution in the ZIA Public Service Edge's web and firewall modules.
SSMA allows inspection engines to scan all content in a single pass. Packets are placed in shared memory in highly optimized custom servers. All CPUs on a ZIA Public Service Edge access those packets at the same time. With dedicated CPUs for each function, all engines can inspect the packets simultaneously instead of using a chained model of physical or virtual appliances (where each security service processes packets in turn, adding incremental latency). SSMA technology applies the Zscaler service policies based on a variety of security engines with minimal latency.
After the SSMA inspection process is complete, the ZIA Public Service Edge executes policies using a specific precedence order. Each ZIA Public Service Edge has two main modules for applying policies: a web module and a firewall module.
At a high level, this is how traffic flows through the modules:
- Outbound web traffic. The ZIA Public Service Edge sends outbound internet web traffic from your organization to the firewall module for policy evaluation. If the traffic violates a firewall policy, it blocks the transaction. If the traffic does not violate any firewall policies, it sends the traffic to the web module for policy evaluation. In the web module, if the traffic violates a web policy, it blocks the transaction. If the traffic does not violate any web policies, the transaction is allowed to the internet.
- Outbound non-web traffic. The ZIA Public Service Edge sends outbound non-web traffic bound for ports other than 80/443 (or other HTTP/HTTPS ports) directly to the firewall module for policy evaluation. If the traffic violates a firewall policy, it blocks the transaction. If the traffic does not violate any firewall policies, it allows the traffic to the internet.
- Inbound web traffic. The ZIA Public Service Edge sends inbound web traffic (HTTP/HTTPS traffic for ports 80/443) from the internet in response to HTTP GET/POST requests to its web module for policy evaluation. If the traffic violates a web policy, it blocks the transaction. If the traffic does not violate any web policies, it allows the traffic into your organization.
When the web traffic violates a firewall policy, both the Firewall Insights logs and the Web Insights logs indicate that the traffic is blocked. However, if the traffic passes through the firewall policy but is blocked due to a web policy violation later, the Firewall Insights logs still indicate that the traffic is allowed, whereas the Web Insights logs indicate it as blocked.
Order of Operations
Web traffic is first evaluated in the firewall module and, if not blocked, is sent to the web module. If your organization's web policy allows a transaction but a firewall policy blocks it, the Zscaler service applies the firewall policy (i.e., the traffic is blocked). For example, if a web [Cloud App Control](/zia/about-cloud-app-control) policy allows the application Box.net, but the firewall policy blocks it, the Zscaler service blocks the transaction.
If the firewall module does not block the user's HTTP or HTTPS transaction, the ZIA Public Service Edge sends the traffic to the web module for policy enforcement.
When the ZIA Public Service Edge receives web traffic, the web module inspects the traffic and applies your organization's web policies. The web module applies policies in a specific order based on the web traffic types, whether the traffic is encrypted or not, and whether SSL inspection is enabled or disabled. If the service finds a policy violation, it immediately blocks the transaction and does not apply other web policies.
Web module policies are enforced in the following order of operations:
- Firewall
- SSL Inspection
- Advanced Threat Protection (ATP)
- Malware/Antivirus (AV)
- Cloud App Control
- URL Control
- File Type Control
- Data Loss Prevention (DLP)
- Cloud Sandbox
[See image.](#zscaler-service-edge)
Policy Enforcement Examples
Understanding how the Zscaler service applies policies in different scenarios helps you determine why certain policies are or are not triggered on users' traffic. It also ensures that your organization's traffic is secured as expected.
The following examples illustrate how policies are applied to traffic.
Example 1
Organization X has the following policies:
- The firewall policy allows the cloud application Box.net.
- The web policy blocks the same application.
When a user from the organization opens a browser and requests the application Box.net, the user is blocked. Even though the firewall module allows the traffic, the web module inspects and enforces the web policy (to block Box.net).
Example 2
Organization Y has the following policies:
- The File Type Control policy blocks users from sending PDFs from the corporate network.
- The DLP policy blocks documents containing US Social Security numbers (SSNs), and specifies that the Zscaler service sends notifications to auditors when it detects any attempt to send SSNs.
When a user from the organization attempts to send a PDF that contains SSNs, the service blocks the transaction because of the File Type Control policy preventing PDFs. The DLP policy is not triggered, and the service doesn’t notify the auditor that a user has attempted to send SSNs from the organization.
Deployment Guide
Build a policy strategy that meets your needs as easily as possible. Most organizations use URL Filtering and Cloud App Control features simultaneously.
Gather a List of the Known Knowns
Before building a policy:
- Review any existing filter policies on legacy systems.
- Take stock of what is known about the environment.
- Look at the available predefined [URL Categories](/zia/about-url-categories) and [Cloud App Categories](/zia/about-cloud-app-categories).
Use this review to create a list of destinations (or types of destinations) that absolutely must be allowed, blocked, or restricted.
Commonly blocked destination types include:
- Legal Liability (adult material, gambling, illegal or questionable content, etc.).
- Privacy Risk (security, other encrypted content, spyware/adware).
- Potential Data Loss destinations (file host, webmail, peer-to-peer, etc.), except those specifically approved by the organization.
- Social Media or Streaming Media services.
Commonly allowed destinations include:
- Applications approved and used by the organization.
- Software and operating system update services.
- Vendors and partners specific to the organization.
Determine the Best Tool to Use
Understanding what traffic should be controlled greatly assists in selecting what policy type to use. Work through the list of known knowns and classify the proper policy type to meet your needs most effectively. Finding the best tool for the task makes policy building and management significantly easier.
Zscaler recommends employing policies as follows:
- Cloud App Control. Use Cloud App Control when you must explicitly allow, block, or restrict user access to a known list of applications or control aspects of user access (e.g., permitting view access but not upload access, receiving mail but not sending mail, etc.)
- URL Filtering. URL Filter is the default access control space. Use URL Filtering to create policies that prevent users from reaching URL categories, or allow access to certain destinations (prebuilt or custom-defined categories). URL Filtering allows the use of granular criteria to fine-tune access details.
- File Type Control. File Type Control is best for creating policies that limit user file type access on permitted destinations and web browsing. File Type Control restricts what files can be shared in one direction or another. File Type Control lets users enjoy web content while maintaining organizational security controls.
- Firewall. A firewall policy is best for controlling outbound connectivity for all non-web traffic; e.g., DNS, SSH, RDP, various United Communications as a Service (UCaaS) services, etc. With the Advanced Firewall subscription, you can use Firewall to control traffic by specific network service (port plus protocol) or by DPI application identification (network application). The Advanced Firewall subscription can also identify traffic that initially begins as web but is some other traffic type and apply the relevant firewall rules.
Furthermore, you can define rules about traffic on web destinations (such as blocking an IP address or allowing traffic to an FQDN or wildcard FQDN destination).
Examples
To block users from reaching adult content, use a URL Filtering policy to block the necessary URL categories.
To allow view access to GitHub while blocking uploads, use a Cloud App policy under the System Development category.
To permit users to browse entertainment sites while blocking the upload or download of PDFs and Microsoft documents, use a File Type Control policy for the Entertainment URL Category and select the file types to restrict.
Determine the Granularity
After identifying which policy type to use, decide if you need special criteria to narrow the traffic matching the rule. If the rule does not apply to all users connecting from anywhere, how should the policy properly identify the traffic? Each of the policy types has unique criteria.
Zscaler recommends the following guidance on selecting criteria:
- Specific Destinations (app or category). Use the appropriate policy type to narrow your selected destinations.
- Specific Users. Use Groups or Department for criteria, as this places control within the user directory space. Avoid using specific users unless testing or access is limited to a small (less than 4) set of users.
- Source Locations. While building policies for individual locations is acceptable, it is easier to manage [Location Groups](/zia/about-location-groups). You can add new locations to a Location Group and the locations are instantly included in all applicable policies.
- Time. Set access based on the data center’s time. For example, use the time to permit specific files during lunch or ensure certain functions are unavailable after hours or on weekends.
- Specific Device Groups. Using Zscaler Client Connector on user devices, you can configure policies to target device operating systems specifically. Alternatively, you can set a policy to filter traffic sourced by means other than Zscaler Client Connector.
- Device Trust Levels. Zscaler Client Connector continuously evaluates the posture of a device and returns the status of the device. Device Trust levels in ZIA are High, Medium, and Low and are associated with specific device posture profiles that you can configure.
- Mobile Admin. You can create explicit rules to allow and block based on these trust levels.
Configure Advanced Policy Settings
There are several Advanced Policy Settings in the ZIA Admin Portal. Go to Policy > URL & Cloud App Control > Advanced Policy Settings. The settings affect all traffic.
The following explains the settings:
- Children's Internet Protection Act (CIPA) Compliance. Set to Disable (unless in K-12 education). This feature allows K-12 education-based customers to configure a CIPA-compliant environment.
- Suspicious New Domains Lookup. Set to Enable. This feature provides advanced protection to users against newly registered and observed domains identified within hours of going live, along with newly revived domains that are inactive. New or idle domains are often considered unsafe and potentially malicious. Blocking them (within the URL policy) improves the overall security posture.
- AI/ML-based Content Categorization. Set to Enable. This feature enables AI/ML for the service to categorize traffic of uncategorized websites based on the content. This helps to identify whether the traffic fits within commonly blocked URL super categories and applies the appropriate policy.
- Embedded Sites Categorization. Set to Enable. This feature applies a URL filtering policy for sites embedded within others. It is commonly employed to stop users who attempt to bypass filtering by using translation services.
- SafeSearch. Set to Enable. This feature applies safe search enforcement on many top search sites. This feature requires you to enable SSL inspection of the traffic.
- Identity-based Block Override. Set to Optional. This feature prompts users to authenticate to access otherwise blocked destinations (as configured in a URL policy). It is not commonly enabled.
- Microsoft-Recommended Click-to-Run Microsoft 365 Configuration. Set to Enable. This feature automatically enables an SSL Inspection exemption and a Cloud App and Firewall policy for Microsoft 365 traffic. To customize the policy exemption, review SSL inspection, Cloud App Control, and Firewall policies to build a higher-order policy, or leave this option disabled and manage Microsoft 365 traffic differently. To learn more, see [About Microsoft One-Click Options](/zia/about-microsoft-one-click-options).
- UCaaS services. Enable per service if used in the environment. This feature manages SSL inspection and access control policy for the respective service to operate.
Configure Advanced Settings
Go to Administration > Advanced Settings to reveal additional global configuration options. The following section reviews a selection of options:
- Cascading to URL Filtering. Set to Disable. This feature lets traffic allowed by Cloud App Control to flow to URL Filtering for policy evaluation before any action is taken. This setting isn’t commonly used and often causes more issues than it resolves. This is a global option, so consider your policy structure before enabling the feature. If the feature is necessary, use Firewall Control to meet your needs first.
- Policy for Unauthenticated Traffic. Set to Enable. For policies that specify users and departments in the criteria, you can specify which rules the service applies to unauthenticated traffic. Enabling this feature logs a specific username based on why the traffic was not authenticated when the location enforced authentication. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic).
- Block Domain Fronting. Set to Enable. Domain fronting allows a client to conceal the true intended destination of an HTTPS request from censors and network security filters by *fronting* the request with a TLS connection to a different domain than the one set in the request’s host header, if both are hosted on the same Content Delivery Network (CDN) service. Using domain fronting, an attacker hides an HTTPS request to a bad site inside a TLS connection to a good site. Using this feature and performing SSL inspection allows Zscaler to evaluate traffic for domain fronting and block any detections. To learn more, see [Analysis of Domain Fronting Technique: Abuse and Hiding via CDNs](https://www.zscaler.com/blogs/security-research/analysis-domain-fronting-technique-abuse-and-hiding-cdns).
- Auto Proxy Forwarding for Non-Defined Ports. Set to Enable All. Advanced Firewall’s Deep Packet Inspection (DPI) capability identifies traffic (including web and other traffic) that bypasses the Secure Web Gateway (SWG) proxy and other specialized engines. With the Auto Proxy Forwarding for Non-Defined Ports toggles enabled, any non-standard traffic (by destination port) not currently redirected to the SWG or other specialized engines is subsequently redirected on the next session that targets that IP, port, and protocol destination. For example, if HTTPS is discovered on destination IP:2.2.2.2 and port:32556, subsequent sessions are directed to the SWG proxy for full policy inspection. You must create a Cloud Firewall rule that permits the traffic initially and an Allow rule with HTTPS defined as the network application to discover non-standard HTTPS.
[See image.](#zia-advanced-settings)
Build a Policy
To stage policy, begin with security concerns and have future expansion and management in mind. The following sections review the baseline recommendations for URL Filtering, Cloud App Control, File Type Control, Firewall, and DNS Control.
URL Filtering Policy Baseline
URL Filtering policies are usually the most straightforward of any policies configured. The categories regarding whether to allow or block are generally obvious, and the policy logic makes sense. The best approach for URL Filtering is to set a policy for Global > Specific > Global. In other words:
- Start with global rules. Create a rule that allows normally blocked destinations and blocks normally allowed destinations.
- Configure rules (allow or block) specific to source users, groups, locations, and destinations that apply to specific users and user groups.
- Create rules that apply to everyone and block unwanted traffic before the default (unwritten) allow-all rule.
The following table lays out a good starting policy strategy checklist.
| Rule # | Purpose | Criteria (minimum listed) | Action |
| ------ | ------- | ------------------------- | ------ |
| 1 | Global Specific Permit.Do not migrate your existing Allow list in full. Test Zscaler’s engines before determining what to migrate. | Category: Custom Exceptions (maintained to allow specific FQDN destinations, otherwise blocked by policy). | Allow |
| 2 | Global Specific Block.Do not migrate your existing Block list in full. Test Zscaler’s engines before determining what to migrate. | Category: Custom Blocks (maintained for destinations that would otherwise be allowed by policy). | Block |
| 3 | Global Security-based Block. | Category: Newly Registered and Observed Domains, Peer-to-Peer Site, Anonymizer, Computer Hacking, Copyright Infringement, Custom Encrypted Content, Newly Revived Domains, Other Security, Spyware/Adware. | Block |
| 4+ | Policies specific to User Groups.While not necessarily security related, it is good to stage policies in a disabled state to build a starting structure. | Category: Optional.User Group: As necessary. | Allow or Block |
| 5+ | Policy specific to Location Groups.Building a policy using user attributes is preferred. Policy follows the user anywhere. Policy by location could be necessary and should have a structure. | Category: Optional.Location: As necessary.Location Groups: As necessary. | Allow or Block |
| 6 | Global Category Blocks.Select the specific URL Categories that should not be accessible to any groups not permitted earlier. | Category: As desired. | Block |
| Default | Default Allow-all.This rule is unwritten and is the default action for URL Filtering Policy. Anything not matching a prior policy is allowed and is evaluated by the next policy module. | Unwritten. No criteria. Not configurable. | Allow |
The following is an example of a policy rule set.
[See image.](#zia-rule-order-example)
Every customer requires a set of policies that make sense for their specific environment and security concerns. The policy design example here creates the following conditions:
- Specific allows (overrides): Create rules that override Zscaler's blocked categories.
- Specific blocks: Create categories that MUST NOT be allowed under any circumstance.
- Specific security blocks: Create block rules that prevent user access due to security team requirements.
- Granular control: Create allow and block rules for granular company-specific access control requirements.
- Global blocks: Create block rules for categories not covered prior (or all categories if customer wishes to overwrite the implicit allow).
For help creating a set of policies that address your needs, contact your [Zscaler Account team](/contact-support).
Cloud App Control Policy Baseline
The recommended approach for Cloud App Control is to be strategic and selective wherever possible. Configure rules matching the applications and criteria for explicitly known needs and leave the unknown to URL Filtering policies. If it must be allowed, blocked, isolated, or controlled in some form, build a Cloud App Control rule. Otherwise, control access elsewhere.
Rules are applied top-down, so entries move from granular to less specific. If one team needs access to a specific tool and other teams should be blocked, build an access rule specific to the approved use group and another rule to block other groups.
If uncertain, rely on the URL Filtering policy.
General Guidance
Use the [Risk Profile](/zia/about-cloud-application-risk-profile) feature to control access to applications without needing to research and specify them individually. Creating a risk profile for applications with a Risk Index of 4 or 5 in an Unsanctioned status allows you to apply the profile to various Cloud Application categories and block or restrict access to risky applications.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights).
The following is an example Risk Profile:
- Select **Any **for **Cloud Applications**.
- Select a setting for **Cloud Application Risk Profile**.
- Select **Users **or **Locations **criteria.
[See image.](#zia-edit-cloud-application)
- Select **Block **or **Isolate **for **Action**.
Example Policy:
[See image.](#zia-policy-leading-practices)
Recommendations by Cloud App Category
The following are recommendations for the different Cloud App categories.
- Collaboration and Online Meetings: Common inclusions are Microsoft, Google, Zoom, and Webex services.
- DNS Over HTTPS Services: Common DNS over HTTPS, whether used by default in certain browsers or configured by end users. If you use Zscaler’s DNS Control features within the environment, Zscaler recommends blocking these services (either here or with more security granularity within DNS Control) to ensure DNS requests are captured and processed correctly.
- File Sharing: Contains many common and obscure file-sharing cloud applications. A common recommendation is to allow access to the organization’s selected/approved file-sharing service within Cloud App Control and then block the other services through a URL Filtering policy with the File Host category.
- Rules created within File Sharing give additional control to allow or block uploading traffic if viewing is allowed. This assists in permitting users access to view (download) files from third-party sites while preventing the upload of files to the same. SSL inspection is necessary for the additional feature to work.
- IT Services: Common space for development, design, SaaS hosts, identity providers (IdPs), security information and event management systems (SIEMs), OS updates, and other services, along with login services for Google, Microsoft, and Webex. You can configure this category to use [Tenant Profiles](/zia/adding-tenant-profiles) for related services.
- Productivity and CRM Tools: Contains the productivity tools used within the organization. Common examples are Microsoft, Google, Salesforce, and ServiceNow. You can configure this category to use [Tenant Profiles](/zia/adding-tenant-profiles) for related services.
- Social Networking: Contains popular social networking and media applications (Facebook, Discord, Reddit, TikTok, etc.). This category can granularly control access to the services and the user's ability to post to the service. SSL inspection is necessary to control posting.
- Streaming Media: Contains the common streaming platforms. Controlling access to these applications reduces bandwidth consumption and productivity loss. A common policy permits YouTube (+ option for [Tenant Profiles](/zia/adding-tenant-profiles)) and other approved media services for training purposes before further restricting the Music & Audio Streaming and Video Streaming categories by URL Filtering policy.
- System Development: Contains common development repositories, tools, and training sites related to development. You can configure rules to control the upload permissions to restrict users further if they can browse the content versus share and store content. You can find services not listed here under the IT Services category.
- Webmail: Zscaler’s recommendation is to explicitly allow webmail services selected by the organization and fully restrict sending mail or sending mail with attachments to any non-approved webmail services for users and devices within the corporate environment. SSL inspection is highly recommended for any permitted webmail services and is necessary to restrict sending.
File Type Control Policy Baseline
It is necessary to properly implement File Type Control to maintain organizational security by preventing uploading and downloading unwanted files while still allowing users access to internet services.
Zscaler recommends setting policies that control sending and receiving files to URL categories that don’t contain the expected file types.
Examples
- Prohibit Microsoft 365 documents from uploading or downloading to and from Entertainment, Gambling, and Productivity Loss sites.
- Permit executable downloads (i.e., .exe, .cab, etc.) from trusted vendors whose applications automatically update end user machines.
- Caution or Block downloads of executable files from all sites except those approved.
- Block the upload of files (i.e., .zip, .cad, .dwg, .stl, undetectable, etc.) from design teams to unsanctioned destinations.
Do not block files commonly used for websites unless you want to restrict access tightly and don’t mind severely impacting the user experience.
The following table outlines an example of a set of File Type Control policies.
| Rule # | Purpose | User/Groups/Departments | File Type | URL Category | Upload/Download | Action |
| ------ | ------- | ----------------------- | --------- | ------------ | --------------- | ------ |
| 1+ | Business exceptions | Specific Groups | Only file types required by the exception (e.g., PDF, archives, or Microsoft 365 documents from business partners).Applications that auto-update (OS, browsers, etc.). | Custom category for specific trusted sites. | Download and/or Upload | Allow |
| 2+ | Permit EXE download for IT Admins | IT Admins and Helpdesk | Archives (.zip, .7z, .bzip, .cab, .gzip, .rar, .tgz, etc.).Executables (.sh, .msi, .exe, .dll, .ps1, etc.).Other documents (.crt, .pcap, etc.). | Specifically accepted categories (business, education, info tech). | Download | Allow |
| 3+ | Permit uploads for developers | Developers | Source code, web content, video, other documents, executables, etc. | Custom category for specific trusted development sites. | Upload/Download | Allow |
| 4+ | Permit download of Microsoft 365 docs for business | Everyone | Microsoft 365, select archives, specific other documents (.cad, .csv, .txt), etc., as necessary. | Specific business-appropriate categories. | Download | Allow |
| 5+ | Block upload and download of unnecessary files | Everyone | Everything except .gzip, audio, image, select video and web content. | All categories. | Upload/Download | Block or Caution |
Cloud Firewall Control Policy Baseline
Zscaler’s Firewall service consists of three main capabilities: the core Firewall, DNS Control, and Cloud IPS Control.
The core Firewall is available as a Standard Firewall and Advanced Firewall. The Standard Firewall is available in all tiers of service that includes the SWG proxy and provides Layer 3, Layer 4, and FQDN rules. For example, you can define a rule to block a source or destination IP address plus FQDN (using an AND condition) plus network service (port and protocol, also using an AND in this case). Zscaler’s Standard Firewall provides aggregate logging for all flows and detailed logging where a block action is selected.
Zscaler’s Advanced Firewall adds per-user conditions (per-user, group, department, etc.), application identification through Deep Packet Inspection (DPI), an ability to detect and redirect non-standard web traffic to the SWG and other modules, DNS controls, and IPS controls for non-web traffic. The Advanced Firewall also adds detailed logging for each session and flow, regardless of whether they are allowed by policy or blocked.
The following Zscaler recommendations often assume that Advanced Firewall is used, and many suggestions blend one or more of these functions.
Enable Cloud Firewall (and IPS) per Location
Firewall rules apply only to locations where Firewall is enabled. It always applies to remote users. Ensure that Cloud Firewall and IPS are enabled at each location where Firewall, DNS, and IPS controls are needed (Admin > Location Management).
[See image.](#zia-gateway-options)
Determining the Firewall Strategy: Default Firewall Filtering Rule
The first Firewall rule to consider is the last. The setting here determines the strategic approach for defining all firewall rules.
Today, all Zscaler tenants ship with the default Firewall Filtering Rule set for the Block. This means all traffic by default is blocked unless it is allowed in a higher-ranked rule. This strategy is called *default block* (i.e., the traffic is placed on the *allowlist*) and requires explicitly defining any traffic and applications that can access the internet in one or more rules. You must tactfully add new applications or newly discovered applications.
[See image.](#zia-default-rule)
This default block is very secure and adopts Zero Trust tenants using a least-privilege approach. This approach, however, can mean disruption to business functions as applications unknown to network ops, security ops, or purchased or implemented outside the normal purview of these teams become non-functional.
A staged rollout is a common way to mitigate disruption, where traffic is initially examined, and all flows are attributed to an application that meets the business goals. This way, you can identify applications in advance and incrementally add Allow rules until few or no sessions are unattributable to the desired set of applications.
Historically, ZIA Firewall shipped with a default Allow rule setting, and many customers have maintained this setting.
The default Allow strategy is that all undesirable or malicious applications using the network must be explicitly defined in firewall rules. This is called a *block list* strategy and requires NetOps/SecOps validation to get a secure footing. The default Allow rule is often regarded as a low disruption approach—at least until a business suffers a breach due to the overly permissive policy.
Essential Firewall Best Practices
The following best practices assume a default block strategy is in place:
- Highest priority to main system-defined rules: Ensure top rules are the rules set to allow. This includes allowing Zscaler proxy traffic, Microsoft 365, and any other Click-to-Run rules to permit UCaaS communication. Putting any other rule higher than the Zscaler proxy traffic rule causes the proxy not to function. Any rule above the Click-to-Run rule is possible but not advised.
[See image.](#zia-highest-priority-policy)
- High priority to Recommended Firewall rule: The Recommended Firewall rule is also a system-defined rule that allows certain known traffic to pass the Layer 3 and Layer 4 firewall and be examined by higher-level proxy functions. These higher-level proxy functions include SWG for web (and other) traffic and DNS Control for standard DNS. This rule uses network services (port plus protocol) and specifically targets standard web (TCP:80 as HTTP and TCP:443 as HTTPS) and DNS (TCP:53 or UDP:53).
Because there is a deeper inspection of the web and DNS, enabling this rule doesn’t mean that this traffic passes uninspected and insecurely, but that you must specify policy for this traffic in those higher-level proxy engines. Zscaler doesn’t recommend putting any other traffic-type conditions in this rule. Reserve this rule for just the specialized ZIA functions. You don’t need to specify DNS over HTTPS (DoH) because it falls under the Web, but the DNS Control engine inspects it after it is determined to be a DoH flow.
- Blocking QUIC as a network service: QUIC is an alternative method to transmit web content that doesn't use TCP and forms the transport basis of the HTTP/3 protocol (which is not yet managed by SWG). Zscaler recommends blocking QUIC and forcing communications into HTTP/2 or HTTPS, which SWG fully manages. Most QUIC is UDP:443, also the current definition of the network service QUIC. Since QUIC appears on UDP:80, you might consider modifying the default definition of the network service QUIC (Admin > Network Services). The selection of the ICMP block drops the UDP packet and sends the client a Type 3 error message (`Destination Unreachable`) and Code 13 (`Communication Administratively Prohibited`) via ICMP. This allows the client a potentially faster switchover to another web transport method, resulting in a better user experience with little lag as the client learns quickly that QUIC is not working. This results in a better user experience regardless if you use a *default block* rule strategy.
[See image.](#zia-edit-firewall-filtering)
- Considered use of Network Applications in rules: Since DPI was incorporated into firewalls in the mid-2000s with next-generation firewalls, independent identification of applications is done regardless of the port used by the application. The strength of DPI is the certainty of the detection. If DPI identifies the traffic as application x, then it is certainly application x. The challenge with any DPI firewall is that application detection does not usually happen on the first packet. This means that several packets might be allowed before the application identification concludes and, therefore, an action (Allow, Block). This leakage means using network applications as the best practice should be applied to as few flows as possible. This limits the number of rule conditions that must stay open since DPI identifies the flow. The best way to do this is to blend network applications with at least one other condition in a rule, such as source or destination IP address, user, or network service. Alternatively, you can lower the priority of a rule (place it further down the rule list) with network applications so first-packet rules using conditions like network services, IP addresses, and FQDNs can trigger on their relevant flows immediately before DPI inspects the remainder flows. If you don’t follow this practice, you could get a lot of flow log entries for flows that were only short bursts and ended independent of firewall policy (before the network application was identified) as `Allowed due to insufficient app data`.
Deploying Without Disruption (Standard Firewall):
- Ensure your default action is set to **Allow **for all traffic if not blocked in a prior rule.
- Review your existing legacy firewall for any explicit **Block **policies.
- Configure **Allow **and **Block **policies in ZIA to match as necessary:
- Only build Network Services policy.
- Enable Firewall at the sublocation level.
- Forward non-web traffic from test locations and users to Zscaler:
- Convert select tunnels from 80/443 to all ports and protocols.
- Implement Z-Tunnel 2.0 for targeting remote users with Zscaler Client Connector.
- Improve your policy:
- Use Firewall NSS feed to your SIEM to identify blocked traffic during troubleshooting.
- Continue building **Allow **policies to match needs, allowing traffic from specific sublocations to the necessary destinations or services.
- **Block **what you know or, as necessary, to work with your policy.
- Set Default policy to **Block**.
Deploying Without Disruption (Advanced Firewall):
- Ensure your default action is set to **Allow **or all traffic if not blocked by a prior rule.
- Review your existing legacy firewall for any explicit **Block **policies.
- Configure known-necessary **Block **policies in ZIA.
- Enable Firewall at the sublocation level for all locations.
- Forward your additional non-web traffic to Zscaler:
- Convert tunnels and policy-based routing (PBR) from 80/443 to all ports and protocols.
- Implement Z-Tunnel 2.0 for remote users with Zscaler Client Connector.
- Review logs regularly to:
- Determine which traffic is triggering the Default policy.
- Identify if this traffic should be allowed or blocked.
- Build policy to match, ensuring it is higher in the list than the default policy.
- Repeat until Default policy matches are minimal enough to set the action to Block safely.
Policy Configuration Examples
The following sections provide configuration examples.
Restricting SSH to Trusted Destinations
In this use case, outbound connections via SSH are only available to specific trusted destinations and blocked otherwise. The purpose of the rule is that permitting SSH to any destination exposes a potential data exfiltration pathway.
Building the rules:
- Configure a Trusted SSH. To learn more, see [IP or FQDN Destination Groups](/zia/configuring-destination-ip-groups).
[See image.](#zia-add-destination)
- Build a rule to permit select services: **SSH**.
[See image.](#zia-permit-ssh)
- Select **Destination Groups**: **Trusted SSH.**
[See image.](#zia-trusted-ssh)
- Set Action: **Allow**.
- Click **Save**.
- Build a rule to **Block**.
- Select Services: **SSH.**
- Set **Action**: **Block/Reset**.
- Click **Save**.
[See image.](#zia-block-rule)
Restricting RDP to Specific Users
In this use case, outbound connections via RDP is only permitted by specific users and blocked for all others.
The purpose of this rule is that users initiating RDP to external machines can bypass filtering and data exfiltration.
Building the Rules:
- Build [Custom Network Service](/zia/adding-network-service).
- **TCP Destination Port**: **3389**.
[See image.](#zia-network-service)
- Build a rule to **Permit**.
- Select the desired user groups.
- Select the **Custom Service**.
- Select the **Application**: **Remote Desktop**.
[See image.](#zia-remote-desktop)
- Set **Action**: **Allow**.
- Click **Save**.
- Build a rule to Block.
- Select **Network Applications**: **RDP**.
[See image.](#zia-applications)
- Set **Action**: **Block/Rese**t.
- Click **Save**.
Selecting Applications requires an Advanced Firewall subscription. Standard licensed users can select Network Services.
[See image.](#zia-network-services-rule)
DNS Control Policy Baseline
DNS Control examines DNS requests and responses and secures these against undesirable, risky, or malicious domains and IP address categories. DNS Control offers many other rule conditions that can be combined with or used independently from categorizations like DNS protocol type, DNS record type, resolved country IP, etc.
Additionally, DNS Control is critical to preventing undesirable communications from leaving your environment. Visibility into the request, and control of the response, means you can steer users and machines away from many of the dangerous services before issuing the connection request.
Forwarding DNS Traffic to Zscaler
You must direct DNS traffic to ZIA for DNS Control to work. You can direct traffic to ZIA in different ways, but the main options are:
- Including DNS into the existing GRE or IPSec forwarding tunnels. This is usually done for HQ and branch locations.
- Enabling Z-Tunnel 2.0 on deployed Zscaler Client Connector clients and including DNS traffic (excluding any domains or IPs that should not be sent to Zscaler, particularly private solutions).
- Forwarding recursive DNS requests directly from a DNS server. This requires creating a location with the IP address of the DNS server sending traffic to ZIA. This method loses all end user context but is often done as an initial step for DNS security.
Recommendations
- **Protect users** from reaching malicious domains by blocking destination IP categories for the riskiest destinations as the first line of defense. Examples: Anonymizer, Botnet Callback, Malicious Content, Phishing.
[See image.](#zia-DNS-applications)
- **Block or Redirect DNS Over HTTPS **requests by Protocol, sending to a trusted public server to gain visibility into requests. This requires SSL Inspection to perform.
[See image.](#zia-DNS-applications-action)
- **Block DNS Tunneling** traffic to unwanted (Commonly Blocked DNS Tunnels) applications. Additionally, review the Unknown DNS Tunnels section for additional pieces to block.
[See image.](#zia-blocked-DNS-tunnels)
- **Permit DNS **requests to trusted servers (defined within an IP Destination Group). Then block or redirect any other DNS requests as the final policy.
[See image.](#zia-DNS-resolved)
- Create policy rules as their properties are shown in the rule order list.
[See image.](#zia-rule-order-example-2)
Deployment Checklist
The following checklists provide a guide to setting ZIA policies.
URL Filtering Recommendations by URL Super Category
Zscaler recommends downloading the [ZIA Filtering Recommendations by URL Super Categories Leading Practices Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/ZIA-Filtering-URL-Super-Category-Leading-Practices-Checklist.pdf) to help plan and implement ZIA policies: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/ZIA-Filtering-URL-Super-Category-Leading-Practices-Checklist.pdf).
To learn more, see [About URL Categories](/zia/about-url-categories).
URL Filtering Advanced Policy Settings
Zscaler recommends downloading the [ZIA URL Filtering Advanced Policy Settings Leading Practices Checklist](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/ZIA-URL-Filtering-Advanced-Policy-Settings-Leading-Practices-Checklist.pdf) to help plan and implement ZIA policies: [Download PDF](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/ZIA-URL-Filtering-Advanced-Policy-Settings-Leading-Practices-Checklist.pdf).
To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings).
Considerations
The following considerations are important when creating ZIA policies.
Policy for Non-Web Traffic Without Firewall Enabled
If the ZIA Public Service Edge receives outbound, non-web traffic going to ports other than 80/443, and the organization has a firewall policy enabled on the user's location. The ZIA Public Service Edge inspects the traffic and applies the policy using only the firewall module if the organization has not enabled firewall policy for the location. The ZIA Public Service Edge neither scans nor applies any policy to the traffic.
Policy for Unauthenticated Traffic
Properly configured ZIA policies should authenticate traffic associated with a user, but it might not be possible in every environment. Deploying and using Zscaler Client Connector even while on Trusted Networks greatly increases the authentication rate and user attribution to traffic.
Alternatively, Zscaler encourages you to enable the policy for Unauthenticated Traffic feature by going to Administration > Advanced Settings. This feature provides additional departments specific to various unauthenticated traffic reasons for selection when building policy. By enabling the feature, policies are enforced for traffic that isn’t authenticated even though authentication is enabled for the location. To learn more, see [Configuring Policies for Unauthenticated Traffic](/zia/configuring-policies-for-unauthenticated-traffic).
[]![ZIA Services Edge](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Zscaler-Service-Edge.png)
[]![Advanced Settings](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Auto-Proxy-Forwarding-Advanced-Settings.png)
[]![Rule Order Example](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Rule-Order-example.png)
[]![Productivity and CRM Tools](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Policy-Productivity-and-CRM-Tools.png)
[]![Default Rule](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Default-Policy.png)
[]![Highest Priority Policy](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Highest-Priority-Policy.png)
[]![Edit Firewall Filtering](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Edit-Firewall-Filtering-Rule.png)
[]![Network Services Rules](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Network-Services-Rules.png)
[]![Rule Order Example](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Rule-Order-example-2.png)
[]![Edit Cloud Application Risk Profile](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Edit-Cloud-Application-Risk-Profile.png)
[]![Add Destination Group](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Add-Destination-Group.png)
[]![SSH](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/SSH.png)
[]![Trusted SSH](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Trusted-SSH.png)
[]![Rule 7 and 8](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Rule-7-and-8.png)
[]![Add Network Service](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Add-Network-Service.png)
[]![Remote Desktop](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Remote-Desktop.png)
[]![Applications](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Applications.png)
[]![DNS Application](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/DNS-Application.png)
[]![DNS Application Action](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/DNS-Application-Action.png)
[]![DNS Application Commonly Blocked DNS Tunnels](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/DNS-Application-Commonly-Blocked-DNS-Tunnels.png)
[]![DNS Resloved](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Destination-Resolved.png)
[]![Gateway Options](/downloads/zscaler-deployments-operations/zia-deployments-operations/zia-policy-leading-practices/Gateway-Options.png)