# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/zero-trust-branch/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for Zero Trust Branch.

**Clouds:** goairgap.com
The following service updates were deployed to goairgap.com on

## November 07, 2025
### Feature Available
#### Zero Trust Branch 8.0.7
The following enhancements to Zero Trust Branch are supported as part of the 8.0.7 release:
Remote Support Access
You can grant Zscaler Support personnel temporary super admin-level access to the Zero Trust Branch Admin Portal to assist with troubleshooting and configuration reviews. This access is strictly time bound, manually configured and activated by the admin only when required, and automatically revoked after the session expires. All actions performed during the remote session are fully audited to maintain transparency and security.
You can grant or revoke remote support access from the Zero Trust Branch Admin Portal (user profile drop-down menu > Remote Support Access).
[See image.](#enabling-remote-support-access-for-ztb)
To learn more, see [Managing Remote Support Access](/zero-trust-branch/managing-remote-support-access).
[]![Enabling remote support access in the Zero Trust Branch Admin Portal ](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/ztb-remote-support-access-rn.png)

## October 28, 2025
### Feature Available
#### Zero Trust Branch 8.0.6
The following enhancements to Zero Trust Branch are supported as part of the 8.0.6 release:
Gateway Version Manager
When you click the Upgrade available icon for a site, the Gateway Version Manager panel opens and provides a rich set of options:
- You can perform upgrade operations on a per-gateway basis.
- As the operations progress, you can observe the gateway status change (e.g., Initializing, Restarting, Standalone, Active, Standby) and the download and activation percentages complete.
- You can download up to three versions, activate a version, and designate a version as default. The appliance uses the default version after a factory reset, so consider designating the latest version as default. You can delete versions you no longer need, as long as the versions are not Default or Active.
- The following enhancement is available for Preview:
- If you are upgrading from version 8.0.6 or later, you can disable Use Legacy Method to Change Version to upgrade the entire file system, which offers highly reliable upgrades. In a high availability (HA) deployment, this option also allows you to upgrade active and standby gateways separately, with no need for automatic switchover during the upgrade process. If you do not use this option, you can select a version and upgrade as before.
[See image.](#upgrades)
Gateway Monitoring
On the Interfaces tab for a site, you can click the score in the last column of a WAN interface row to easily assess gateway uptime and WAN performance metrics.
[See image.](#metrics)
On the Monitoring tab for a site, you can see real-time gateway resource usage (i.e., CPU, memory, disk). The gateway refreshes resource usage data every 5 minutes.
[See image.](#usage)
Single VLAN in LAN as Source for DNS Proxy
When a DNS server is accessible through a Routed Tunnel (RT), DNS requests take the source IP addresses of the VLANs that are shared over the RT. You can instead select Use for DNS Proxy on the VLANs tab for a site. This sets up a specific VLAN in the LAN for DNS proxy, so DNS requests take the source IP address of that VLAN interface on the appliance.
[See image.](#dns-proxy)
Sharing Static Routes over Routed Tunnels
VLANs or subnets that are indirectly connected to Zero Trust Branch spokes (sites) can be shared via border gateway protocol (BGP) over routed tunnels. When you enable Share Over RT on a new or existing static route, the target subnet is advertised over the routed tunnel to the hub and across the SD-WAN fabric.
[See image.](#routed-tunnel-static)
Separate WAN and Private DNS Servers for a Site
To make it easier to manage DNS redirection and policies, you can configure WAN DNS servers and private DNS servers separately in the DNS settings for a site. The WAN DNS servers are used for site activation and DNS queries that the appliance initiates. The private DNS servers resolve DNS queries for both private namespaces (internal domains) and public domains. The values you enter populate the respective system group (e.g., System-Private-DNS-Servers-Group).
You can apply DNS redirection to the DNS policy for WAN DNS servers in addition to other DNS servers. Based on default DNS policies, the App Connector uses the WAN DNS server to resolve all Zscaler domains (Default-ZScaler-Domains-DNS-Policy) and the private DNS server to resolve all non-Zscaler domains (Default-DNS-Policy).
[See image.](#wan-dns)
To learn more, see [What Are Site DNS Policies?](/zero-trust-branch/what-site-dns-policies) and [Configuring Site DNS Policies](/zero-trust-branch/configuring-site-dns-policies).
Support for DHCP Options
There are additional standard DHCP options in the menu on the DHCP Options tab for a site. All options in the DHCP options menu are supported, except for the Domain Name Server (DNS) option, because per-interface DNS settings take precedence over it. For any DHCP options not listed, you can use the custom DHCP option and create your own.
[See image.](#dhcp-options)
[]![Sites list showing the Upgrade available icon that opens the Gateway Version Manager window](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/downloadIcon.png)
![Gateway Version Manager panel with several upgrade options](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/gw-vers-mgr.png)
[]
![WAN interface row with a score in the last column](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/iface-row.png)
![Interface Statistics panel showing statistics such as score, loss, latency, and jitter at the top and graphs showing average score, average loss, and average latency over a 24-hour timeline](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/interface-statistics.png)
[]![Monitoring tab for a site with charts and graphs showing CPU, memory, and disk usage](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/monitoring.png)
[]![VLANs tab for a site with option to use a VLAN for DNS proxy](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/dns-proxy-option.png)
[]![Add/Edit Static Route panel with option to share the route over routed tunnels](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/static-route-share-rt.png)
![Image]()
[]
![DNS settings with WAN DNS Servers and Private DNS Servers configuration sections](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/dns-servers.png)
![DNS Policies tab with a policy for WAN DNS servers with the Redirect action](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/dns-policy.png)
[]![DHCP Options tab with menu listing standard options and a custom option to create your own option](/sites/default/files/downloads/zero-trust-branch/release-notes/release-upgrade-summary-2025/dhcp-options.png)

## September 11, 2025
### Feature Available
#### Zero Trust Branch 8.0.5
The following enhancement to Zero Trust Branch (formerly Zero Trust Device Segmentation) is supported as part of the 8.0.5 release:
Manual Synchronization of ZIA and ZPA to Zero Trust Branch
When the Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) integrations with Zero Trust Branch are not synchronized or properly configured, the Location drop-down menu on the Add Site page might not display. Error messages describe the problems and direct you to the Zscaler Services Integration tile on the Settings > Integrations page, where you can manually trigger a sync action to resolve the issues independently, without contacting Zscaler Support.
This feature is intended only for customers using SD-WAN functionality within Zero Trust Branch.
[See images.](#services-integration-tile)
To perform this action, you must have Super Admin role permissions in ZIdentity.
To learn more, see [Adding a Site](/zero-trust-branch/adding-site).
[]![Zscaler Services Integation tile on the Settings > Integrations page, with a Settings button where you can sync the ZIA and ZPA integrations to Zero Trust Branch](/sites/default/files/downloads/zero-trust-branch/release-notes/zscaler-service-integ-tile.png)
![Zscaler Services Integration settings page, where you sync the ZIA and ZPA integrations with Zero Trust Branch](/sites/default/files/downloads/zero-trust-branch/release-notes/zscaler-service-integr.png)

## August 18, 2025
### Feature Available
#### Zero Trust Branch 8.0.4
The following enhancements to Zero Trust Branch (formerly Zero Trust Device Segmentation) are supported as part of the 8.0.4 release:
Enhancements to Connectivity
Zero Trust Branch has the following enhancements to connectivity:
- Allows DHCP to be used on the primary WAN interface, which can then be used for device activation.
- Establishes the following predefined DNS policies:
- Match DNS queries for Zscaler domains, and redirect them to the WAN DNS servers. This ensures that GeoIP location is properly identified and that the closest Zscaler data center is utilized for outbound traffic.
- Match DNS queries from the embedded AppC process and forward them to customer-configured private DNS servers. This ensures that when enabled, the AppC process can resolve the customer's private DNS namespaces.
- Match any downloaded app segment FQDN or wildcard FQDN, and return a predefined, non-configurable, synthetic IP address.
-
Allows users to configure custom DNS policies with the following specifications:
- Defined DNS gateways that specify primary and secondary DNS resolvers that are used as forwarders in policy.
- Match any specified source IP address/CIDRs and FQDN, or wildcard FQDN, and redirect (forward) the query to a user-defined DNS gateway.
- Match any specified source IP address/CIDRs and FQDN and override the response to a user-defined IP address.
- Match any specified source IP address/CIDRs and FQDN, or wildcard FQDN, and reject the query.
[See image.](#add-dns-policy)
Enhancements to Routing and Firewall Policies
Zero Trust Branch has the following enhancements to the routing and firewall policies:
- Traffic originating from the gateway (e.g., DHCP or DNS) and destined for Zscaler Private Access (ZPA) app segments is routed to ZPA using a predefined routing policy.
- Traffic originating from the gateway (e.g., DHCP or DNS) and destined for Airgap Network is permitted using a predefined firewall policy.
-
Establishes the following predefined routing policies:
- Default-ZPA-PBR: Any traffic sourced from Airgap Network and destined to ZPA app segments is forwarded to ZPA.
- Default ZIA Rule: Any traffic sourced from Airgap Network and destined to non-RFC 1918 subnets is forwarded to Zscaler Internet Access (ZIA). Note that ZIA policies must be configured to allow this traffic.
- Default-App-Segment-PBR: Any traffic sourced from Local Interface IPs and destined to ZPA app segments is forwarded to ZPA.
- Default Zscaler Rule: Any traffic destined to Zscaler cloud endpoints is sent directly via WAN interfaces.
[See image.](#default-policies)
Default policies are automatically created for new sites only in release 8.0.4. Sites upgraded from release 8.0.3 need these policies to be manually created.
- Added border gateway protocol (BGP) support on WAN links for active and standby gateways. Standby gateways can now pre-learn WAN routes, enhancing routing convergence during failover.
- DHCP relay support over routed tunnel and ZPA app segments.
Enhancements to the Platform
Zero Trust Branch supports the ZT8010, offering high throughput with 8x 10G SFP+ ports, 10x GbE RJ45 ports, and a redundant power supply for improved reliability and performance.
To learn more, see [What are Site DNS Policies?](/zero-trust-branch/what-site-dns-policies) and [Configuring Site DNS Policies](/zero-trust-branch/configuring-site-dns-policies).
[]![Default Routing Policies](/sites/default/files/downloads/zero-trust-branch/release-notes/default-policies.png)
[]![Viewing the DNS Policies tab for a Site](/sites/default/files/downloads/zero-trust-branch/administration/deployment-configuration/configuring-site-dns-policies/add-dns-policy.gif)

## April 30, 2025
### Feature Available
#### Zero Trust Branch 8.0.1
The following enhancements to Zero Trust Branch (formerly Zero Trust Device Segmentation) are supported as part of the 8.0.1 release:
Enhancements to Provisioning
Zero Trust Branch has the following enhancements to provisioning:
- Support for creating Zscaler Internet Access (ZIA) locations using the Zero Trust Branch Admin Portal.
- Support for default and custom templates for ZT400 and ZT600.
Enhancements to Connectivity
Zero Trust Branch has the following enhancements to connectivity:
- Location-based (ZIA locations) automated connectivity to the nearest ZIA data center via IPSec.
- Connectivity with ZIA over IPSec, with a primary and secondary IPSec tunnel.
- Branch-to-hub connectivity over a routed tunnel to support applications requiring Source IP visibility. You can create routed tunnels from a branch to a standalone or primary and secondary hub site, and share subnets over the routed tunnel.
- Open Shortest Path First (OSPF) support on LAN and WAN interfaces.
- App Connector support to allow zero trust connectivity for private applications hosted in sites and data centers.
- Routing policy that forwards select traffic to specific destinations based on your needs. The supported forwarding methods are LAN and WAN interfaces with the optional next hop IP, ZIA-IPSec, ZIA-GRE, ZPA, and routed tunnel. For example, to forward specific traffic through ZIA, configure source, destination, and ports, and then select either the ZIA-IPSec or ZIA-GRE traffic-forwarding method.
- WAN link selection is supported on WAN interfaces only. You can choose among three traffic-forwarding methods:
- None: Traffic strictly follows the defined primary and secondary WAN interfaces. If the primary WAN interface goes down, the traffic is switched to the secondary WAN interface.
- Best Link: Link score is calculated based on packet loss, jitter, and latency for the WAN interfaces. The best-performing WAN interface is selected for traffic forwarding.
- Load Balanced: Traffic is load balanced on the primary and secondary WAN interfaces defined in the routing policy.
- Routing policy supports destination matching based on Zscaler Private Access (ZPA) app segments, including wildcard FQDN matching for FQDN App Segments. For example, `*.acme.loc` would catch all current and future ZPA app segments within the `acme.loc` namespace.
- Destination matching in the routing policy includes top SaaS applications.
Enhancements to the Platform
Zero Trust Branch has the following enhancements to platform support:
- Support for SNMPv3.
- Enhanced Active Directory (AD) integration supports multiple domain controllers and multiple AD query strings.
- Factory reset support for ZT400, ZT600, and ZT800.

## January 15, 2025
### Feature Available
#### Zero Trust Device Segmentation 7.8
The following enhancements to Zero Trust Device Segmentation are supported as part of the 7.8 release:
Provisioning Enhancements
Zero Trust Device Segmentation has the following enhancements to provisioning:
- Zero Touch Provisioning allows easier configuration and enables onboarding at remote or branch office locations with a single URL click.
- Device Segmentation includes default templates, allowing ease of deployment for multiple sites, and the ability to create custom templates.
- Templates are supported for ZT800 and virtual machine (VM) form factors for both standalone and high-availability deployments.
- Templates support multiple LAN/WAN interfaces and zones. To learn more, see [Managing Templates](/zero-trust-branch/managing-templates).
Platform and Connectivity Enhancements
Zero Trust Device Segmentation has the following enhancements to platform support and connectivity:
- Support for connectivity with Zscaler Internet Access (ZIA) over GRE. You can configure policy-based routing to define the traffic that needs to leverage ZIA.
- Supports connectivity using source-based criteria based on user, TCP/UDP port, IP, network, MAC, or other device attributes. To learn more, see [Managing Objects](/zero-trust-branch/managing-objects).
- Site-to-site VPN allows connectivity between isolated networks via wireguard connection.
- Support for a dedicated high-availability link to allow faster failover time.
