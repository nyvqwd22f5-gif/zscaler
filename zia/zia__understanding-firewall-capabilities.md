# Understanding Firewall Capabilities
Source: https://help.zscaler.com/zia/understanding-firewall-capabilities
PDF: https://help.zscaler.com/pdf/com/en/1402371.pdf

The Zscaler cloud provides integrated cloud-based next-generation firewall capabilities that allow granular control over your organization's outbound TCP, UDP, and ICMP traffic.
Zscaler works with multiple firewall partners, and [provides a separate deployment guide for each partner](/zscaler-technology-partners/zscaler-and-firewall-technology-partner-deployment-guides).
You can configure the following firewall policies:
- [Firewall Filtering Policy](/zia/about-firewall-control): Add rules to allow or block specified types of traffic from your network to the internet. You can also specify how the sessions are logged.
- [NAT Control Policy](/zia/about-nat-control): Add rules to perform destination NAT. You can redirect traffic to specific IP addresses or ports.
- [DNS Control Policy](/zia/about-dns-control): Add rules to allow or block DNS requests, redirect requests to a different DNS server, or redirect DNS responses by substituting the IP address in a DNS response with a preconfigured IP address.
- [IPS Control Policy](/zia/about-ips-control): Add rules to control and protect your traffic from intrusion over all ports and protocols using signature-based detection.
[Configuring firewall policies](/zia/configuring-firewall-policies) requires configuring the four policies in the preceding list as applicable and [enabling the firewall](/zia/enabling-firewall-locations) for your locations. You might also need to enable [IPv6 configuration](/zia/understanding-ipv6-support), create [source](/zia/how-do-i-configure-source-ip-groups) and [destination IP](/zia/how-do-i-configure-destination-ip-groups) groups, modify [network services](/zia/about-network-services), create [network application groups](/zia/about-network-application-groups), and configure [custom ports](/zia/configuring-custom-ports).
Configuring a firewall policy also requires the following:
- An organization must forward its IP traffic from a known location.
- If your organization wants to apply firewall policies at the user level, user authentication and surrogate IP must be enabled. Otherwise, the Zscaler Firewall service applies organization and location policies.
[]Standard and Advanced Firewall
The following table lists the features and functionalities offered by Standard and Advanced Firewall subscriptions:
- [](/zia/about-network-services)
-
- [](/zia/about-locations)
- [](/zia/about-users)[](/zia/about-groups)[](/zia/about-departments)
- [](/zia/about-network-applications)
-
-
[](/zia/about-nat-control)[](/zia/about-ftp-control)[](/zia/about-dns-control)[](/zia/detecting-and-controlling-dns-tunnels)[](/zia/about-ips-control)[](/zia/about-advanced-settings#auto-proxy-forwarding)
| Features and Functionalities | Standard Firewall | Advanced Firewall |
| ---------------------------- | ----------------- | ----------------- |
| **Firewall policies based on the following criteria**:**Network and Application Services**: Manage your traffic based on network services and application services that are designated to use specific IP addresses, ports, and protocols (5-tuple firewall).**FQDN Filtering**:** **Control your network traffic based on fully qualified domain names (FQDN) and wildcard FQDN*.**Location Awareness**: Enforce policies on internet traffic from known locations (locations configured in the ZIA Admin Portal), sublocations, and remote users.**User Awareness**: Define granular policies based on users, groups, and departments.**Application Awareness**: Identify and control traffic that belongs to network applications using deep packet inspection (DPI). | Supported with limitations:User Awareness and Application Awareness criteria are *not *supportedOnly 10 firewall filtering rules are allowed | Supported |
| **Destination NAT**: Create rules to redirect your traffic to specific IP addresses and ports within a network using destination NAT. | Supported | Supported |
| **FTP Traffic Control**: Use configuration settings to manage native FTP traffic and FTP over HTTP traffic. Configure policies to allow access to specific FTP sites. | Supported | Supported |
| **DNS Security and Control**: Define granular DNS filtering policies to control DNS attributes, requests, and responses. Optimize DNS resolution using Zscaler Trusted DNS Resolver hosted in Zscaler data centers. | Supported (only 64 rules are allowed) | Supported |
| **DNS Tunnel and DNS Application Control**: Secure your DNS traffic from DNS tunneling, malicious domains, malware, and phishing attacks. Control DNS applications including web pages, social networking sites, search engines, and network services at the DNS level. | N/A | Supported |
| **IPS Control**: Use signature-based IPS to monitor your traffic in real time and protect your network against identified threats over all ports and protocols. In addition to the signatures managed by Zscaler, create and deploy custom IPS signature rules to identify unique threats that are specific to your organization's requirements and threat landscape. | N/A | Supported |
| **Non-Standard Traffic Redirection**: Identify outbound HTTP, HTTPS, FTP, DNS, RTSP, and PPTP traffic that is destined for non-standard ports and redirect the traffic to the web proxy (secure web gateway) for full web visibility and security. | N/A | Supported |
| **Firewall & IPS Dashboards, Insights, and Logs**:** **Analyze your traffic information using customizable dashboards, interactive charts, and real-time logs. | Supported.Limitations in logging in Standard Firewall include full logging for each blocked flow but aggregated logging every 15 minutes for allowed flows. | Supported |
| **DNS Dashboards, Insights, and Logs**: Analyze your traffic information using customizable dashboards, interactive charts, and real-time logs. | Supported.Limitations in logging: DNS tunnel and DNS application information are not populated in DNS logs. | Supported |
| **Miscellaneous**: Forwarding Control policy (including Source IP Anchoring) | Supported with limitations: User, group, and department criteria are not supported in the Forwarding Control policy. | Supported |
*Wildcard FQDN support for non-web traffic requires a ZIA edition that includes parsing of DNS traffic via DNS Control/Security. This capability is available across all new ZIA editions (2023 editions) and earlier ZIA editions with Advanced Firewall. Wildcard FQDN match against web traffic (HTTP and TLS/SNI) can function without the need for parsing DNS packets.