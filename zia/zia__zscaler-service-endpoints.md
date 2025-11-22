# Zscaler Service Endpoints
Source: https://help.zscaler.com/zia/zscaler-service-endpoints
PDF: https://help.zscaler.com/pdf/com/en/1421001.pdf

This article provides an overview of the various API endpoints offered by Zscaler to enable customers and partners to deploy the required infrastructure and integrate the Zscaler service with their environment. These API endpoints help you automate firewall configuration changes and their propagation in your environments to establish connectivity with the Zscaler cloud infrastructure.
For a list of all available Zscaler API endpoints, visit [config.zscaler.com](http://config.zscaler.com).
- To view insights into cloud operation status, upcoming maintenance, and security updates, visit the [Zscaler Trust Portal](https://trust.zscaler.com).
- The Zscaler service also provides the RSS Feed URLs for [blogs](https://trust.zscaler.com/blog-feed) and [notifications related to URL categories](https://trust.zscaler.com/blog-feed/url-category-notification).
ZIA Public Service Edges
This section provides information specific to Zscaler’s data centers, such as the list of IP addresses along with the prefixes advertised by each data center, VPN hostname, GRE virtual IP address, SVPN virtual IP address, and more. This information is necessary for adding the Zscaler data center’s address prefix to the allowlist in your firewall or tunneling your organization’s traffic to the Zscaler service.
The following links provide information specific to Zscaler’s data centers for each cloud in JSON format: ZIA Public Service Edge
- [zscaler.net](https://config.zscaler.com/api/zscaler.net/cenr/json)
- [zscalerone.net](https://config.zscaler.com/api/zscalerone.net/cenr/json)
- [zscalertwo.net](https://config.zscaler.com/api/zscalertwo.net/cenr/json)
- [zscalerthree.net](https://config.zscaler.com/api/zscalerthree.net/cenr/json)
- [zscloud.net](https://config.zscaler.com/api/zscloud.net/cenr/json)
Zscaler Central Authority (CA)
This section provides the list of IP addresses along with the prefixes used by the [Zscaler Central Authority](/zia/about-zscaler-cloud-architecture). You need to add these IP address prefixes to the allowlist in your firewall if you are using any of the following services:
- Third-party authentication service with Active Directory (AD)/OpenLDAP or Kerberos client authentication service is hosted in your organization’s data center. The AD and Kerberos servers must pass authentication requests directly to the CA hosted in the Zscaler cloud.
- ZIA Private Service Edges are installed in your organization’s data center. The Private Service Edges must communicate with other nodes in the Zscaler cloud, including the CA for user authentication and policy updates.
The IP addresses for the CA are split between required and recommended lists and the following links provide this information on a per-cloud basis in JSON format:
- [](https://config.zscaler.com/api/zscaler.net/hubs/cidr/json/required)
- [](https://config.zscaler.com/api/zscalerone.net/hubs/cidr/json/required)
- [](https://config.zscaler.com/api/zscalertwo.net/hubs/cidr/json/required)
- [](https://config.zscaler.com/api/zscalerthree.net/hubs/cidr/json/required)
- [](https://config.zscaler.com/api/zscloud.net/hubs/cidr/json/required)
- [](https://config.zscaler.com/api/zscaler.net/hubs/cidr/json/recommended)
- [](https://config.zscaler.com/api/zscalerone.net/hubs/cidr/json/recommended)
- [](https://config.zscaler.com/api/zscalertwo.net/hubs/cidr/json/recommended)
- [](https://config.zscaler.com/api/zscalerthree.net/hubs/cidr/json/recommended)
- [](https://config.zscaler.com/api/zscloud.net/hubs/cidr/json/recommended)
| Required | Recommended |
| -------- | ----------- |
| zscaler.net
zscalerone.net
zscalertwo.net
zscalerthree.net
zscloud.net | zscaler.net
zscalerone.net
zscalertwo.net
zscalerthree.net
zscloud.net |
Zscaler Client Connector
This section provides a list of the ZIA Public Service Edge IP addresses to which the Zscaler Client Connector forwards traffic. If you need to forward traffic from a site that is behind a firewall to the ZIA Public Service Edge (destination server) using Zscaler Client Connector, you need to add the destination server's IP address to the allowlist in your firewall.
The following links provide the list of destination servers’ IP addresses (referred to as SVPN IP addresses) for each Zscaler cloud in JSON format:
- [zscaler.net](https://config.zscaler.com/api/zscaler.net/svpn/json)
- [zscalertwo.net](https://config.zscaler.com/api/zscalertwo.net/svpn/json)
- [zscalerthree.net](https://config.zscaler.com/api/zscalerthree.net/svpn/json)
- [zscloud.net](https://config.zscaler.com/api/zscloud.net/svpn/json)
For zscalerone.net, the endpoints are yet to be published.
Future Data Centers
This section provides the list of IP addresses along with the prefixes that are allocated for Zscaler’s future data centers. These data centers will become operative as Zscaler expands its operations to new geographical regions and adds new cloud infrastructure. If you are setting up new organization sites, you can add these address prefixes to the allowlist in your firewall ahead of time to simplify the firewall configuration later. You can also add these address prefixes to your access control lists and application allowlists, as applicable.
The following links provide a list of IP addresses for each cloud that are advertised by Zscaler’s future data centers in JSON format:
- [zscaler.net](https://config.zscaler.com/api/zscaler.net/future/json)
- [zscalerone.net](https://config.zscaler.com/api/zscalerone.net/future/json)
- [zscalertwo.net](https://config.zscaler.com/api/zscalertwo.net/future/json)
- [zscalerthree.net](https://config.zscaler.com/api/zscalerthree.net/future/json)
- [zscloud.net](https://config.zscaler.com/api/zscloud.net/future/json)