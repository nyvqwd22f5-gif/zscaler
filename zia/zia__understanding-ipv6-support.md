# Understanding IPv6 Support
Source: https://help.zscaler.com/zia/understanding-ipv6-support
PDF: https://help.zscaler.com/pdf/com/en/1404786.pdf

As Internet Protocol version 6 (IPv6) gradually replaces its predecessor Internet Protocol version 4 (IPv4), enterprises and service providers are migrating their internal networks to IPv6 to overcome IPv4 exhaustion and other shortcomings of IPv4, such as performance, scalability, security, and more. Mobile internet access has accelerated the depletion of IPv4 address space, leading service providers to deploy IPv6-only addresses to mobile devices. To address the network infrastructure’s shift towards IPv6, the Zscaler service brings in IPv6 support using tunneling and network address translation (NAT) technologies.
IPv6 support is extended by Zscaler based on the [traffic forwarding method](/zia/choosing-traffic-forwarding-methods) and also whether the client device is inside a [location](/zia/about-locations).
- **For clients inside a location:** Forward IPv6 traffic inside an IPv4 tunnel to ZIA Service Edges using a [GRE tunnel](/zia/about-generic-routing-encapsulation-gre) or [IPSec tunnel](/zia/about-ipsec-vpns). Both web and non-web traffic can be forwarded using these tunneling methods.
- **For clients outside a location:** Forward web requests using [PAC files](/zia/about-pac-file) or [Zscaler Client Connector](/client-connector/what-is-zscaler-client-connector) using Z-Tunnel 1.0 to Service Edges via a self-hosted or ISP-provided NAT64 gateway. To forward both web and non-web traffic from IPv6 clients, use Zscaler Client Connector over Z-Tunnel 2.0 and a self-hosted or ISP-provided NAT64 gateway.
Zscaler highly recommends using Zscaler Client Connector as your preferred forwarding method for IPv6 traffic whenever feasible.
-
When forwarding your organization's IPv6 traffic to Zscaler's data centers, you must ensure that the traffic is forwarded only to IPv6-enabled data centers. To check if a Zscaler data center is IPv6-enabled, go to the [Zscaler config page](https://config.zscaler.com/) and verify that the data center has an IPv6 virtual IP associated with it.
Furthermore, when using Zscaler Client Connector, you must forward your users' IPv6 traffic only to data centers in the IPv6-enabled subcloud managed by Zscaler. To learn how to do this, see [Configuring IPv6 Settings](/zia/configuring-ipv6-settings#client-connector).
For information specific to Zscaler's data centers, see [Cloud Enforcement Node Ranges](https://config.zscaler.com/zscaler.net/cenr).
- Zscaler's My IP Address service ([ip.zscaler.com](http://ip.zscaler.com)) might not recognize IPv6 traffic passing through the Zscaler cloud. Exercise caution when using the My IP Address service for troubleshooting or [verifying connectivity to the Zscaler cloud](/zia/verifying-users-traffic-being-forwarded-zscaler-service) when IPv6 is enabled on the client.
Explaining IPv6 Traffic Configuration
The following sections explain how IPv6 traffic is forwarded and processed by the Zscaler service, the configuration workflow, and logging:
- [Forwarding IPv6 Traffic from Clients Inside a Location](#location-traffic)
- [Forwarding IPv6 Traffic from Clients Outside a Location](#remote-traffic)
- [Processing of IPv6 Traffic](#traffic-processing)
- [IPv6 Configuration Workflow](#configuration-workflow)
- [Logging for IPv6 Traffic](#logs)
[]You can forward your organization's IPv6 traffic from a location to the Zscaler service and enforce security policies on IPv6 traffic. Although Zscaler's cloud infrastructure can handle IPv6 traffic, the outer packets arriving in a tunnel at the Service Edges must be IPv4 packets. Therefore, to apply policies on your organization’s IPv6 traffic, the Zscaler service requires you to forward the IPv6 traffic inside IPv4 tunnels to the Service Edges. You can establish an IPv4 tunnel between your organization’s network from a specific location and the Service Edges using one of the following traffic forwarding methods:
- [Generic Routing Encapsulation (GRE) Tunnel](/zia/about-generic-routing-encapsulation-gre)
- [IPSec Tunnel](/zia/about-ipsec-vpns)
In addition to enforcing security policies on IPv6 traffic, the Zscaler service also provides customized DNS64/NAT64 mechanisms to establish connections between IPv6 clients and IPv4 destinations (IPv4-only or dual-stack destinations).
With this IPv6 support for clients inside a location, the Zscaler service supports the following use cases:
- [IPv6 Client Accessing an IPv4-only/Dual-Stack Destination](#location-ipv6-ipv4)
- [IPv6 Client Accessing an IPv6-only Destination](#location-ipv6-ipv6)
- [IPv4 Client Accessing an IPv6-only Destination](#location-ipv4-ipv6)
[]The IPv6 traffic from a client inside a location with IPv4 internet access is forwarded to the Service Edge inside an IPv4 tunnel. The Zscaler service establishes an IPv4 connection with an IPv4-only/dual-stack destination using the DNS64/NAT64 mechanism.
![An illustration of IPv6 clients connecting with IPv4 destinations through GRE/IPSec tunnel](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv4-GRE-IPSec.png)
[]The IPv6 traffic from a client inside a location with IPv4 internet access is forwarded to Service Edge inside an IPv4 tunnel. The Zscaler service establishes an IPv6 connection with the destination.
![An illustration of IPv6 clients connecting with IPv6 destinations through GRE/IPSec tunnel](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv6-GRE-IPSec.png)
[]The Zscaler service establishes an IPv6 connection with the destination.
[]Clients from unknown locations (remote users) can use Zscaler Client Connector or PAC files to forward their traffic to Service Edges. When using PAC files or Zscaler Client Connector with Z-Tunnel 1.0, only web traffic is forwarded to Service Edges via [explicit proxy mode](/zia/what-proxy-mode). However, if you are using Zscaler Client Connector with Z-Tunnel 2.0, both web and non-web traffic can be forwarded.
For IPv6 clients that are connected to an IPv6 internet, a NAT64/DNS64 service is needed, as Service Edges can only be reached via an IPv4 internet. You can use a self-hosted or ISP-provided NAT64 gateway to perform the address translation from IPv6 to IPv4.
The NAT64/DNS64 service is not needed for dual-stack clients if they are connected to the internet with support for both IPv6 and IPv4 concurrently.
With this IPv6 support for clients outside a location, the Zscaler service supports the following use cases:
- [IPv6 Client Accessing an IPv4-only/Dual-stack Destination](#remote-ip6-ipv4)
- [IPv6 Client Accessing an IPv6-only Destination](#remote-ipv6-ipv6)
[]The IPv6 traffic from a client outside a location is forwarded to the Service Edge using Zscaler Client Connector or PAC file. The Zscaler service uses the DNS64/NAT64 mechanism (for Z-Tunnel 2.0) or regular DNS resolution (for Z-Tunnel 1.0 or PAC file) to establish an IPv4 connection. For non-web traffic forwarded using Z-Tunnel 2.0, an IPv4 connection is established if the destination IPv6 contains a NAT64 prefix recognized by Zscaler. Otherwise, an IPv6 connection is established.
The following illustration shows how IPv6 traffic is forwarded to IPv4 destinations using PAC files or Z-Tunnel 1.0:
![An illustration of IPv6 clients connecting with IPv4 destinations using PAC files and ZTunnel 1.0](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv4-PAC-ZTunnel1_0.png)
The following illustration shows how IPv6 traffic is forwarded to IPv4 destinations using Z-Tunnel 2.0:
![An illustration of IPv6 clients connecting with IPv4 destinations using ZTunnel 2.0](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv4-ZTunnel2_0.png)
[]The IPv6 traffic from a client outside a location is forwarded to the Service Edge using Zscaler Client Connector or PAC file. The Zscaler service establishes an IPv6 connection with the destination using the DNS64/NAT64 mechanism for web traffic. For non-web traffic forwarded using Z-Tunnel 2.0, an IPv6 connection is established.
The following illustration shows how IPv6 traffic is forwarded to IPv6-only destinations using a PAC file or Z-Tunnel 1.0:
![An illustration of IPv6 clients connecting with IPv6 destinations using PAC files and ZTunnel 1.0](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv6-PAC-ZTunnel1_0.png)
The following illustration shows how IPv6 traffic is forwarded to IPv6-only destinations using Z-Tunnel 2.0:
![An illustration of IPv6 clients connecting with IPv6 destinations using ZTunnel 2.0](/downloads/zia/traffic-forwarding/ipv6/understanding-ipv6-support/IPv6-IPv6-ZTunnel2_0.png)
[]The Zscaler service prefers an IPv4 connection whenever possible, and an IPv6 connection is established for IPv6-only destinations. The preference for IPv4 connections (via NAT64) has the following advantages:
- Better utilization of existing IPv4 infrastructure
- Applying rich-security policies on IPv6 traffic
- Accessing IPv4 services from the IPv6 network
The following sections explain how the traffic forwarded from IPv6 clients using different proxy modes is handled by the Zscaler service.
- [Processing of Explicit Proxy-Traffic from IPv6 Clients](#explicit-proxy)
- [Processing of Transparent Proxy-Traffic from IPv6 Clients](#transparent-proxy)
[]When web traffic from IPv6 clients arrives at a Service Edge in [explicit proxy mode](/zia/what-proxy-mode) via Zscaler Client Connector over Z-Tunnel 1.0 or using PAC files, the Zscaler service establishes an IPv4 or IPv6 connection to the destination based on how the server can be reached, as described in the following bullet points:
- If the destination is reachable only via IPv4, then the Zscaler service establishes an IPv4 connection.
- If the destination is reachable via IPv4 or IPv6, then the Zscaler service establishes an IPv4 connection.
- If the destination is reachable only via IPv6, then the Zscaler service establishes an IPv6 connection.
[]When traffic from IPv6 clients arrives at a Service Edge in [transparent proxy mode](/zia/what-proxy-mode) using an IPv4 tunnel (GRE or IPSec) or via Zscaler Client Connector (Z-Tunnel 2.0 only), the Zscaler service establishes an IPv4 or IPv6 connection to the destination based on how the server can be reached, as described in the following bullet points:
- If the destination IPv6 address has a prefix match with [NAT64 prefixes](/zia/about-nat64-prefixes) supported for the organization, then the IPv4 address is extracted from the destination IPv6 address and an IPv4 connection is established.
- If the destination IPv6 address is a regular IPv6 address, an IPv6 connection is established.
For establishing an IPv4 connection with the destination, the Zscaler service employs the NAT64/DNS64 mechanism to translate IPv6 packets of the inbound traffic to IPv4 packets. This translation depends on the following parameters:
- Type of traffic (DNS queries or non-DNS traffic)
- The prefix used in the inbound IPv6 packets
- DNS64/NAT64 prefix configurations in the ZIA Admin Portal
For DNS queries, the Zscaler service tries to resolve the domain name for an A record. If an A record is available, an AAAA record is synthesized using DNS64 and an IPv4 connection is established using NAT64. If an A record is not available, an AAAA record is used to establish an IPv6 connection.
The Zscaler service uses the well-known prefix and its default NAT64 and DNS64 prefixes for the DNS64/NAT64 mechanism and organizations do *not* require any additional configuration. However, organizations can configure their network-specific NAT64/DNS64 prefixes in the ZIA Admin Portal. To learn more, see [About NAT64 Prefixes](/zia/about-nat64-prefixes) and [About the DNS64 Prefix](/zia/about-dns64-prefix).
[]To enable IPv6 support for your organization and obtain access to IPv6 configurations and settings, contact Zscaler Support.
To allow the Zscaler service to handle your organization’s IPv6 traffic, you need to enable IPv6 support for your organization under Administration > IPv6 Configuration. Enabling IPv6 support for your organization allows you to route your users’ IPv6 traffic to the Zscaler cloud using one of the supported forwarding methods. However, to allow and process IPv6 traffic that is tunneled using GRE or IPSec within an outer IPv4 tunnel, you need to additionally enable IPv6 support for the locations from where the traffic originates. If IPv6 support is not enabled for a location, the IPv6 traffic arriving at the location is dropped. To learn more, see [Configuring Locations](/zia/configuring-locations).
If you are using Zscaler Client Connector set up with Z-tunnel 2.0 to forward your IPv6 traffic, you need to configure the application appropriately. To learn more, see the [Zscaler Client Connector documentation](/client-connector).
After enabling IPv6 support, you can optionally configure your network-specific NAT64 and DNS64 prefixes under Administration > IPv6 Configuration. To learn more, see [Configuring IPv6 Settings](/zia/configuring-ipv6-settings).
When IPv6 support is enabled and the necessary configurations are complete, the IPv6 traffic from your organization can be routed to the Service Edge inside an IPv4 tunnel, and the Zscaler service tries to translate the IPv6 packets to IPv4 packets using a built-in NAT64/DNS64 mechanism to establish client-server communication over IPv4 instead of IPv6. If an IPv4 connection is established, the Zscaler service applies policies that are configured based on IPv4 addresses in the ZIA Admin Portal on the translated IPv4 traffic. However, if the destination is an IPv6-only server, the Zscaler service establishes an IPv6 connection.
The Zscaler service allows you to configure and enforce limited policies on IPv6 server-bound connections. You can configure these policies in the following ways:
- [Using Locations or Location Groups](#location-based-policy)
- [Using URL Categories](#url-category-based-policy)
- [Using IP Address Groups](#ip-address-based-policy)
[]You can configure policies based on [Locations](/zia/about-locations) or [Location Groups](/zia/about-location-groups) criteria to be enforced on all IPv6 traffic that originates from those locations. When a sublocation is added to a location with the IPv6 option enabled, the Zscaler service automatically creates a new Other6 sublocation that identifies all the IPv6 addresses in that location. Using Other6 as the location criteria, you can define policies for all of the IPv6 traffic that originates from that location. To learn more, see [Understanding Sublocations](/zia/understanding-sublocations).
The Locations and Location Groups criteria are supported in various web and firewall policies.
[]You can configure policies based on URL Categories to be enforced on traffic bound to specific IPv6 sites or destinations. The Zscaler service allows you to add individual domains or IP addresses to URL categories, which can then be used in policies to control the traffic bound to those IPv6 destinations. To learn more, see [Configuring Custom URL Categories](/zia/adding-custom-url-categories).
The URL Categories criterion is supported in various web and firewall policies.
[]You can configure policies based on Source or Destination IP Address Groups to be enforced on traffic originating from or destined to any IPv6 device. The Zscaler service provides predefined source and destination IPv6 address groups, All IPv6, which encompasses all IPv6 source or destination addresses. Using All IPv6 as the source or destination group criteria, you can define policies for all traffic originating from or destined to an IPv6 device. To learn more, see About [Source](/zia/about-source-ip-groups) or [Destination IP Address Groups](/zia/about-destination-groups).
The Source and Destination IPv6 Address Groups criteria are supported in various web and firewall policies.
[]The Zscaler service records and displays logs for your IPv6 traffic on the respective Insights Logs page:
- Web Insights Logs: [Filters](/zia/web-insights-logs-filters) and [Columns](/zia/web-insights-logs-columns)
- Firewall Insights Logs: [Filters](/zia/firewall-insights-logs-filters) and [Columns](/zia/firewall-insights-logs-columns)
- DNS Insights Logs: [Filters](/zia/dns-insights-logs-filters) and [Columns](/zia/dns-insights-logs-columns)
In addition, the [Nanolog Streaming Service](/zia/about-nanolog-streaming-service) allows you to stream your logs in real time from the [Zscaler Nanolog](/zia/about-zscaler-cloud-architecture) to your security information and event management (SIEM) system. To learn more, see [Adding NSS Feeds](/zia/adding-nss-feeds).