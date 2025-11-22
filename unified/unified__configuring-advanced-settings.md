# Configuring Advanced Settings
Source: https://help.zscaler.com/unified/configuring-advanced-settings
PDF: https://help.zscaler.com/pdf/com/en/1493631.pdf

On the Advanced Settings page in the Admin Portal, you can configure settings for a variety of Zscaler service features.
To adjust the advanced settings:
- Go to **Policies **>** Common Configuration** >** Advanced **>** Advanced Settings**.
- Configure the following options:
- [Admin Ranking](#admin-ranking)
- [Advanced Web App Control Options](#web-app-control)
- [Admin Portal Session Timeout](#session-timeout)
- [Authentication Exemptions](#auth-exemption)
- [Kerberos Authentication Exemptions](#kerberos)
- [Basic Authentication Exemptions](#basic-auth)
- [Digest Authentication Exemptions](#digest-auth)
- [Remove Range Headers](#remove-range-headers)
- [Internal IP Logging](#internal-IP-logging)
- [Windows App Traffic Authentication](#windows-app-traffic-auth)
- [Policy for Unauthenticated Traffic](#unauthenticated-traffic)
- [HTTP Tunnel Control](#http-tunnel-control)
- [Domain Fronting](#domain-fronting)
- [Office 365 One Click Configuration](#o365)
- [Traffic Forwarded to ZPA from ZIA](#xff-header-zpa-traffic)
- [DNS Optimization](#dns-optimization)
- [Firewall for Z-Tunnel 1.0 and PAC Road Warriors](#firewall-remote-users)
- [Enable EDNS Client Subnet (ECS) Option](#ecs-prefix)
- [Risk Score Settings](#risk-score)
- [HTTP/2 for Non-Browser Traffic](#http2-non-browser-traffic)
-
Complete the following configurations, if you have [enabled the firewall service](/unified/configuring-firewall-policies).
By default, the Zscaler service "listens to":
- Port 80 for HTTP traffic
- Port 443 for HTTPS traffic
- Port 53 for DNS traffic
- Port 21 for FTP traffic
- Port 554 for RTSP traffic
- Port 1723 for PPTP traffic
If your organization uses other or additional ports for the above types of traffic, you can enable the service to use custom ports for them. To do this, create a custom [network service](/unified/about-network-services) with the appropriate ports and select it from the following options:
- [Services Forwarded to HTTP Web Proxy](#HTTP-Web-Proxy)
- [Services Applicable to DNS Transaction Policies](#DNS)
- [Services Forwarded to FTP Proxy](#FTP-proxy)
- [Services Forwarded to RTSP](#RTSP)
- [Services Forwarded to PPTP](#PPTP)
To learn more, see [Configuring Custom Ports](/unified/configuring-custom-ports).
- Configure the following options:
- [Auto Proxy Forwarding for Non-Defined Ports](#auto-proxy-forwarding)
- Click **Save** and activate the change.
[]**Enable Admin Ranking**:** **Turn on this feature if you want to [rank administrators](/unified/about-admin-rank) and use the ranks when you manage policies.
[]**Allow Cascading to URL Filtering**: Enable this if you want the service to apply the [URL Filtering policy](/unified/about-url-filtering) even if it has already applied a [Cloud App Control policy](/unified/about-cloud-app-control) that explicitly allows a transaction. By default, if a user requests a cloud app that you explicitly allow with a Cloud App Control policy rule, the service only applies the Cloud App Control policy and does not apply the URL Filtering policy. For example, if you have a Cloud App Control rule that allows viewing Facebook, but a URL Filtering policy that blocks www.facebook.com, a user is still allowed to view Facebook because, by default, the service doesn't apply the URL Filtering policy if a Cloud App Control rule allows the transaction. However, in the same example, if you allow cascading to URL filtering, the service blocks the user from Facebook because of your URL Filtering policy.
If a user requests a cloud app for which you haven't configured a Cloud App Control policy rule, the service still evaluates and applies the URL filtering policy. To learn more, see [Understanding Policy Enforcement](/unified/understanding-policy-enforcement).
If you enable this option, the system globally allows cascading to URL filtering for all the Cloud App Control policies, irrespective of the cascading settings at the policy level.
[]**Session Timeout Duration**: Specify how long admins can be inactive on the Admin Portal before they must log in again. By default, inactive sessions restart after 30 minutes. You can configure a different time interval, from 5 minutes to 600 minutes (10 hours). All active sessions automatically restart after a continuous log in period of 720 minutes (12 hours) that is not configurable.
[]The service can exempt specific [URL categories](/unified/about-url-categories), URLs, [cloud app categories](/unified/understanding-cloud-app-categories), or specific cloud apps from [cookie authentication](/unified/about-zscaler-cookies):
- **Exempted URL Categories**: Select the URL categories you want to exempt from cookie authentication. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- **Exempted URLs**: Enter URLs you want to exempt from cookie authentication, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. By default, you can add up to 25K custom URLs (across all categories). To learn more, see [Ranges & Limitations](/unified/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25K items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25K Items** or **Remove Page**, a confirmation window appears.
- **Exempted Applications**: Select cloud app categories or cloud apps you want to exempt from cookie authentication.
[]The service can exempt specific [URL categories](/unified/about-url-categories), URLs, [cloud app categories](/unified/understanding-cloud-app-categories), or specific cloud apps from [Kerberos authentication](/unified/about-kerberos-authentication):
- **Exempted URL Categories**: Select the URL categories you want to exempt from Kerberos authentication. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- **Exempted URLs**: Enter the URLs you want to exempt from Kerberos authentication, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. By default, you can add up to 25K custom URLs (across all categories). To learn more, see [Ranges & Limitations](/unified/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25K items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25k Items** or **Remove Page**, a confirmation window appears.
- **Exempted Applications**: Select cloud app categories or cloud apps you want to exempt from Kerberos authentication.
[]The service can exempt specific [URL categories](/unified/about-url-categories), [cloud app categories](/unified/understanding-cloud-app-categories), or specific cloud apps from Basic authentication:
-
**Exempted URL Categories**: Select the URL categories you want to exempt from Basic authentication. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
If you want to exempt specific URLs, you can add them to a custom category and exempt the category. To learn more, see [Configuring Custom URL Categories](/unified/configuring-custom-url-categories).
- **Exempted Applications**: Select the cloud app categories or cloud apps you want to exempt from Basic authentication.
This feature is not enabled by default. To have this feature enabled for your organization, contact your Zscaler Account team.
[]The service can exempt specific [URL categories](/unified/about-url-categories), URLs, [cloud app categories](/unified/understanding-cloud-app-categories), or specific cloud apps from digest authentication:
- **Exempted URL Categories**: Select the URL categories you want to exempt from digest authentication. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- **Exempted URLs**: Enter URLs you want to exempt from digest authentication, and click **Add Items**. You can enter multiple entries. Press `Enter` after each entry. By default, you can add up to 25K custom URLs (across all categories). To learn more, see [Ranges & Limitations](/unified/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines). For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove the first 25K items from the list (**Remove 25K Items**) or only items from a specific page (**Remove Page**). If you select **Remove 25k Items** or **Remove Page**, a confirmation window appears.
- **Exempted Applications**: Select the cloud app categories or cloud apps you want to exempt from digest authentication.
[]**URL Categories**: Select the URL categories for which you want to remove range headers.
[]**Log Internal IPs from XFF Headers**:** **When the Zscaler service logs a transaction, it includes the source IP address, which is always the public IP address of the firewall or edge router that sent the traffic to the service. But if you use [proxy chaining](/unified/configuring-proxy-chaining) to forward traffic to the Zscaler service, a proxy server can insert an X-Forwarded-For (XFF) header in outbound HTTP requests. The XFF header identifies the IP address of the original client that sent the HTTP request through the proxy server.
If you enable **Internal IP Logging**, the service logs the source IP address that is in the XFF header. Then, when the service forwards the traffic to its destination, it removes the original XFF header and replaces it with an XFF header that contains the IP address of the client gateway (the organization’s public IP address). Replacement of the original XFF header ensures that an organization's internal IP addresses are not exposed to the external world.
Zscaler Client Connector also sends IP addresses as part of the XFF headers.
[]**Enforce Surrogate IP Authentication**:** **Some Windows 8 Metro apps use Internet Explorer as their user agent but do not support cookies or redirects, so the service does not allow traffic to these sites. Enable this option to allow the service to use the user-to-device mappings to apply the appropriate user policies to the traffic of the top Windows 8 Metro apps. The [Surrogate IP](/unified/about-surrogate-ip) feature must be enabled.
[]**Enable Policy For Unauthenticated Traffic**: For policies where you can specify users and departments in the criteria, the Zscaler service allows you to specify whether you want a rule to apply if the user traffic is unauthenticated. You must turn on this feature here if you want this option to appear when configuring your policy rules. Any rule that applies to unauthenticated traffic must apply to all locations; you cannot apply a rule to unauthenticated traffic and select particular locations. To learn more, see [Configuring Policies for Unauthenticated Traffic](/unified/configuring-policies-unauthenticated-traffic).
[]A client can send an HTTP CONNECT method request in order to establish a tunnel connection to a remote server through the Zscaler service. When the connection is established, the service then tunnels the traffic to the destination server on behalf of the client. The HTTP CONNECT method is typically used to initiate an SSL connection, but it can be used for tunneling purposes.
- **Inspect Tunneled HTTP Traffic**: Enable to allow the Zscaler service to enforce configured policies on tunneled HTTP traffic that is sent via a CONNECT method request. For example, if this option is enabled and the service receives a CONNECT request to www.cnn.com:80, the service applies the configured web policies to HTTP traffic that it forwards to www.cnn.com. By default, this option is enabled. If this option is disabled, then the service doesn't apply the policies to HTTP traffic that it forwards to www.cnn.com.
- **Block Tunneling to Non-HTTP/HTTPS Ports**: Enable to allow the service to restrict HTTP CONNECT method requests to the standard HTTP/HTTPS ports 80 and 443. By default, this option is enabled. You can disable this option to allow all HTTP CONNECT requests to non-standard HTTP/HTTPS ports, in addition to ports 80 and 443. For example, if this option is disabled, a CONNECT request for SSH to port 22 is allowed.
- **Block Non-RFC Compliant HTTP Traffic on HTTP/HTTPS Ports**: Enable to allow the service to block traffic that isn't compliant with Request for Comments (RFC) HTTP protocol standards. For example, binary traffic or other non-RFC compliant traffic, such as HTTP/0.9, is blocked through standard HTTP/HTTPS ports 80 and 443. You can disable this option to allow any non-RFC compliant traffic over HTTP/HTTPS ports. By default, this option is disabled.
- **Block Non-HTTP Traffic on HTTP/HTTPS Ports**: Enable to allow the service to restrict traffic on HTTP/HTTPS ports to HTTP traffic only. When enabled, FTP, SMTP, or other non-HTTP-compliant traffic is blocked through standard HTTP/HTTPS ports 80 and 443. By default, this option is disabled.
[]
- **Block Domain Fronting**: Enable to allow the service to block the HTTP/S transactions that have an FQDN mismatch between:
- The request URL and the request's host header. The service doesn't consider it a mismatch if either of the fields, host header, or FQDN URL is empty.
- The SNI (Server Name Indication) and the inner request's host header. The service doesn't consider it a mismatch if either of the fields, host header, or SNI is empty.
-
**Block CONNECT Host and SNI Mismatch**: Enable to block forward proxy connections where the CONNECT host doesn't match the SSL/TLS client hello SNI. When there is a mismatch, SNI is logged into the URL weblog field and the CONNECT host is logged into the existing weblog field "Domain fronted host header."
- **Exempted URL Categories**: Select the URL categories you want to exempt from domain fronting. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- **Exempted Cloud Applications**: Select the cloud app categories or cloud apps you want to exempt from domain fronting.
You can enable the Block CONNECT Host and SNI Mismatch option, but if you have a use case where an upstream proxy puts the IP into the CONNECT host name received by Zscaler, there will be a mismatch (so traffic is blocked). In this case, you can enable the [Prefer SNI over CONNECT Host for DNS](#prefer-sni) option.
[]To learn more about this option, see [About Microsoft One Click Options](/unified/about-microsoft-one-click-options).
[]
**Insert XFF Header for ZPA Traffic**: Inserts the XFF header for traffic that is forwarded from Internet & SaaS to Private Applications through a Private Applications gateway ([Source IP Anchored](/unified/understanding-source-ip-anchoring) and [Internet & SaaS-inspected Private Applications traffic](/unified/configuring-forwarding-policy)). This field is enabled by default. If you don't want to insert the XFF header for outbound requests, disable this field. To learn more about XFF headers, see [Internal IP Logging](#internal-IP-logging).
This field is only available if you have a subscription to either Source IP Anchoring or Private Applications App Inspection.
[See image.](#xff-header-zpa-traffic-image)
[]**Settings for DNS Optimization**: You can configure DNS optimization settings to allow Zscaler to perform a DNS lookup and override the externally resolved IP addresses in the outbound HTTP/S connections to establish a connection to the destination server that is geographically closer to the Internet & SaaS Service Edge (Public, Private, or Virtual). DNS optimization ensures reduced latency and increased performance efficiency. Additionally, it prevents DNS spoofing and hence acts as an extra layer of security to customers who are concerned that their client machine DNS might be compromised.
DNS optimization does not affect the DNS resolution process that is configured for your organization. It does not operate on the DNS packets but rather on the HTTP header of unencrypted HTTP traffic or the SNI field in the TLS hello if the traffic is encrypted (HTTPS). After DNS resolution is performed and when the client makes its initial HTTP or HTTPS request to the IP address returned in the DNS response, the Zscaler proxy intercepts the request and performs a DNS lookup. If this lookup fetches an IP address that is different from the externally resolved IP address, the proxy overrides the externally resolved IP address.
- DNS optimization applies only to Z-Tunnel 2.0 and [transparent](/unified/understanding-proxy-mode#transparent-mode) mode traffic (e.g., traffic via GRE or IPSec tunnels without a PAC file).
- Using auth bypass or SSL bypass does not affect DNS optimization as the domain name would still be visible in the SNI.
To enable and configure DNS optimization, select the **Optimize DNS Resolution** checkbox and configure the DNS optimization settings individually for URL categories, cloud applications, and FQDNs using the following options:
- **Optimize These URL Categories**: Select the [URL categories](/unified/about-url-categories) to which DNS optimization must apply.
- **Optimize These Cloud Applications**: (Requires the Advanced Firewall license) Select the [cloud applications](/unified/understanding-cloud-app-categories) that the DNS optimization must apply.
-
**Optimize These FQDN**: Enter the IP addresses or FQDNs that the DNS optimization must apply.
To add multiple entries, press `Enter` after each entry and then click **Add Items**. You can add up to 25K custom URLs (across all categories). To learn more, see [Ranges & Limitations](/unified/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines).
For item lists, you can view up to 500 items on a page and filter the list by searching for a word, phrase, or number within an item. To remove items from the list, you can use one of the following options:
- Remove a single item by clicking the **Remove** icon displayed beside the item.
- Remove items from a specific page by clicking **Remove Page** under the **Remove** drop-down menu and confirming your choice.
- Remove all 25K items from the list by clicking **Remove 25K Items** under the **Remove** drop-down menu and confirming your choice.
- **Do Not Optimize These URL Categories**: If you want to exclude specific URL categories from DNS optimization by overriding the include list, specify the categories in this field.
- **Do Not Optimize These Cloud Applications**: If you want to exclude specific cloud applications from DNS optimization by overriding the include list, specify the applications in this field.
-
**Do Not Optimize These FQDN**: If you want to exclude specific IP addresses or FQDNs from DNS optimization by overriding the include list, specify the IP addresses or FQDNs and add the following internal domains to this field:
- `prod.zpath.net`
- `gateway.``<cloud>``.net`
- `ecservice.``<cloud>``.net`
- `ecgw.``<cloud>``.net`
To add multiple entries, press `Enter` after each entry and then click **Add Items**. You can add up to custom 25K URLs (across all categories). To learn more, see [Ranges & Limitations](/unified/ranges-limitations). For guidance on entering URLs, see the [URL format guidelines](/unified/url-format-guidelines).
For item lists, you can view up to 500 items on a page and filter the list by searching for a word, phrase, or number within an item. To remove items from the list, you can use one of the following options:
- Remove a single item by clicking the **Remove** icon displayed beside the item.
- Remove items from a specific page by clicking **Remove Page** under the **Remove** drop-down menu and by confirming your choice.
- Remove all 25K items from the list by clicking **Remove 25K Items** under the **Remove** drop-down menu and by confirming your choice.
-
[]**Prefer SNI over CONNECT Host for DNS Resolution**: Enable to use the SSL/TLS client hello SNI for DNS resolution instead of the CONNECT host for forward proxy connections. This works only if the CONNECT host is not part of an SSL policy. This handles exceptions such as a malformed but valid SNI server name that isn't parsable to the actual resolvable domain.
- **Exempted URL Categories**: Select the URL categories you want to exempt from domain fronting. By default, you can add up to 64 custom categories. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
- **Exempted Cloud Applications**: Select the cloud app categories or cloud apps you want to exempt from DNS optimization.
[See image.](#seeimage1)
If you have [IPv6 support enabled](/unified/configuring-ipv6-settings) for your organization, you can additionally configure DNS optimization settings for IPv6 connections to dual-stack or IPv6-only destinations. The Zscaler service performs a DNS lookup and might override the externally resolved IPv6 addresses in the outbound HTTP/S connections to establish an IPv6 or IPv4 connection to the destination server that is geographically closer to the Internet & SaaS Service Edge.
When IPv6 support is enabled for your organization, DNS optimization for IPv6 connections is automatically enabled for all URL categories and cloud applications.
To configure DNS optimization settings for IPv6 connections, select the **Optimize DNS Resolution (IPv6)** checkbox and configure the DNS optimization settings individually for URL categories and cloud applications using the following options:
- **Optimize All (IPv6)**: Enable this option to apply DNS optimization to all [URL categories](/unified/about-url-categories) and [cloud applications](/unified/understanding-cloud-app-categories). However, if you want to enable DNS optimization for specific URL categories or cloud applications, use the following options.
- **Optimize These URL Categories (IPv6)**: If you want to enable DNS optimization for specific URL categories, select the categories using this field.
- **Optimize These Cloud Applications (IPv6)**: (Requires the Advanced Firewall license) If you want to enable DNS optimization for specific cloud applications, select the applications using this field.
- **Do Not Optimize These URL Categories (IPv6)**: If you want to exclude specific URL categories from DNS optimization by overriding the include list, specify the categories in this field.
-
**Do Not Optimize These Cloud Applications (IPv6)**: If you want to exclude specific cloud applications from DNS optimization by overriding the include list, specify the applications in this field.
[See image.](#dns-optimization-ipv6)
After completing your configurations, ensure that you click **Save **and activate your changes.
[]**Enable Firewall for Z-Tunnel 1.0 and PAC Road Warriors**: Enabling the option applies the following firewall rules to the remote user traffic forwarded via Z-Tunnel 1.0 or PAC:
- All the default firewall rules.
- All the user-defined rules configured without any location criteria.
- All the user-defined rules configured for the Road Warrior location because Road Warrior applies only to Z-Tunnel 2.0 when this option is disabled.
Hence, before enabling, ensure that the above firewall rules are relevant for the traffic forwarded via Z-Tunnel 1.0 and PAC.
[]**Enable HTTP/2 for Non-Browser Traffic**: Enable this option to make HTTP/2 the default web protocol for accessing various applications at your organizational level.
The **HTTP/2** feature is only available if it is enabled for your organization.
[]**Enable Real-Time Risk Score Updates**: Enable this option to allow Internet & SaaS Public Service Edges to track risky user activities that might increase user risk in real time. When enabled:
- Displays the risk score in the **User Risk Profile** column on the [User Management page](/unified/about-internet-saas-users).
- The policies that include user risk as a criterion can only receive real-time risk increase updates. This might result in limited user access.
- You can view the recent risk score increases in the [User Risk Report](/unified/about-user-risk-report).
[]From the **HTTP Services** and **HTTPS Services** lists, choose the custom service that specifies the ports your organization uses for HTTP or HTTPS.
[]From the **DNS Services** list, choose the custom service that specifies the ports your organization uses for DNS traffic.
If no values are selected for the **DNS Services** option, [DNS Control policies](/unified/about-dns-control) are not enforced on your organization's traffic. However, Zscaler might still resolve your DNS queries if the predefined NAT rule, [Zscaler Trusted DNS Resolver](/unified/about-nat-control), is enabled. You can manually disable this rule, if required.
[]From the **FTP Services** list, choose the custom service that specifies the ports your organization uses for FTP traffic.
[]From the **RTSP Services** list, choose the custom service that specifies the ports your organization uses for RTSP traffic.
[]From the **PPTP Services** list, choose the custom service that specifies the ports your organization uses for PPTP traffic.
[]Enable to redirect outbound HTTP, HTTPS, FTP, DNS, RTSP, and PPTP traffic to the web engine for inspection. Use this if the traffic is destined to a non-standard port and doesn't match any predefined network services. RTSP and PPTP are applicable only with [transparent mode](/unified/understanding-proxy-mode#transparent-mode) connectivity to the Internet & SaaS Public Service Edge (i.e., GRE or IPSec tunnels with no PAC file).
The firewall identifies destinations of web traffic when an Allow rule exists, identifying HTTP or HTTPS at a network application. The next time a session is directed to a non-standard web location, the CFW will ensure that the traffic is inspected by the SWG.
Auto Proxy Forwarding for Non-Defined Ports requires the Advanced Firewall license. To learn more, see [Zscaler Pricing and Plans](https://www.zscaler.com/pricing-and-plans).
[]You can configure the following settings to include the [EDNS Client Subnet (ECS) option](/unified/about-edns-client-subnet-ecs-injection) in DNS queries to obtain geolocated responses for clients from the external DNS service used by your organization:
Before enabling the ECS option, ensure that you have [configured the ECS prefix objects](/unified/adding-edns-client-subnet-ecs-prefixes), so they can be prepopulated for selection in the **ECS Prefix** field.
- **Enable ECS Option for Locations and Remote Users**: Enable this option to include the ECS option in all DNS queries, originating from all locations and remote users.
- **ECS Prefix**: This field appears when the ECS option is enabled using the preceding setting. Select the ECS prefix that must be used in DNS queries. To learn how to configure ECS prefixes, see [Adding EDNS Client Subnet (ECS) Prefixes](/unified/adding-edns-client-subnet-ecs-prefixes).
[]![A screenshot of the advanced DNS optimization settings](/downloads/tech-pubs-drafts/zia-draft-articles/configuring-advanced-settings-draft/DNS%20settings.png)
[]
![Insert XFF Header for ZPA Traffic field in the Advanced Settings page](/downloads/zia/policies/configuring-advanced-settings/zia-xff-header-zpa-traffic-advanced-settings.png)
[]![A screenshot of the DNS optimization settings for IPv6 connections to dual-stack or IPv6-only destinations](/downloads/zia/policies/configuring-advanced-settings/DNS%20optimization%20IPv6.png)