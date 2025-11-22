# Configuring Zscaler Client Connector App Profiles
Source: https://help.zscaler.com/unified/configuring-zscaler-client-connector-app-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493886.pdf

You can add a Zscaler Client Connector [profile](/unified/about-zscaler-client-connector-app-profiles) policy rule for each of the following device platforms:
- [Windows](#windows)
- [macOS](#macOS)
- [Linux](#linux)
- [iOS](#iOS)
- [Android](#android)
[]To add a new Windows policy rule:
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **Windows** and click **Add Windows Policy**. The **Add Windows Policy **window appears.
-
In the **Add Windows Policy **window, you can configure the following settings:
To find an option, you can enter search words in the **Search** field and press `Enter`. A navigation path to the option appears in the search results.
- [General](#general)
- [Groups](#groups)
- [Traffic Steering](#traffic)
- [Data Protection](#data-protection)
- [App Fail Open](#zcc-fail-open)
- [Firewall](#firewall)
- [Zscaler Client Connector Fail Close Settings](#zcc-fail-close-settings)
- [Passwords](#otp)
- [Authentication](#authentication)
- [Notification and Logging](#notification)
- [Captive Portal](#captive-portal)
- [Client Connector UI Language Settings](#UI-language-settings)
- [SCCM Client](#SCCM)
- [Command Line Interface Access](#CLI)
- [Zscaler Client Connector Telemetry Options](#telemetry_options)
- [Advanced](#adv)
- [Policy](#policy)
[]
- [PAC and Proxy](#pac-proxy)
- [App and IP Bypass](#app-bypass)
- [Disaster Recovery](#DR)
- [DNS](#DNS)
- [Location Policies](#location-policies)
- [Advanced](#advanced)
[]
- [Global Bypasses](#global)
- [IP Bypasses](#IP)
[]
- [ZIA Disaster Recovery](#ZIA)
- [ZPA Disaster Recovery](#ZPA)
- [Business Continuity](#Business_Continuity)
[]
- [Authentication](#auth)
- [ZPA Reauthentication Configuration](#zpa-reauth)
[]
- **Name**: Enter a unique alphanumeric name for your policy rule.
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order reflects the order of precedence among configured profile policy rules and helps determine which rule the app downloads for a user upon enrollment. Precedence is based on ascending numerical order.
- **Status**: Select **Disabled** to inactivate the rule or select **Enabled **to activate the rule. If you don’t enable the rule, the policy rule is not enforced.
-
**Forwarding Profile**: Select a forwarding profile of your configured forwarding profiles from the drop-down menu. You can also search for items to select. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
If you're using Zscaler Tunnel (Z-Tunnel) 2.0, you must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- **ZIA Posture Profile**: Select a [posture profile](/unified/about-internet-saas-posture-profiles) from the drop-down menu to apply to the app profile. You can also search for items to select.
- **Install Zscaler SSL Certificate**: If you’re using Zscaler Client Connector for Private Applications only, skip this option. Enable this option to allow Zscaler Client Connector to automatically [install the Zscaler SSL certificate](/unified/configuring-ssl-inspection-zscaler-client-connector) on users’ devices. If you [uploaded your organization’s custom certificate in the Admin Portal](/unified/uploading-custom-ssl-certificate-zscaler-client-connector), the app installs your organization’s custom certificate instead.
- **Install WFP Driver**: Enable this option to install and use the WFP-based Zscaler driver for Flow Logging, Block Domain Profile Detection, Process-Based Application Bypass, ZDX Autosense Probes, and Location Policy Override. This driver inspects all traffic including bypass traffic.
-
**Location Policy Override**: Enable this option to use location-based policies (rulesets for traffic steering and endpoint firewall rules that apply based on a user’s network type, e.g, On-Trusted or Off-Trusted). To learn more, see [About Location-Based Policies](/unified/about-location-based-policies).
If enabled, the Location Policies tab is enabled in the Traffic Steering section and the following app profile options are unavailable:
- Process-Based Application Bypass
- Source Port-Based Bypasses
- IP Bypasses
- Domain Inclusion
- Domain Exclusion
- Prioritize DNS Exclusions over Z-Tunnel 2.0
If you enable this feature for an existing app profile, the existing settings for these options are removed, copied to the [Win V4.7 and Older Client Configuration] section, and apply only to users with this app profile who use Zscaler Client Connector version 4.7 and earlier. If you want users with version 4.8 and later to continue using these settings, you must [add a new ruleset](/unified/adding-ruleset) that includes these settings and add it to this app profile.
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows, and you must first enable Install WFP Driver. Contact Zscaler Support to enable this feature.
-
**Notification Template**: Select one of your configured notification templates from the drop-down menu. You can also search for items to select. To learn more, see [Configuring Notification Templates for Zscaler Client Connector](/unified/configuring-notification-templates-zscaler-client-connector).
This option is available only for Zscaler Client Connector version 4.8 and later for Windows. If you assign an app profile with a notification template to users with Zscaler Client Connector version 4.7 or earlier, the Legacy Notification Settings template is used regardless of what is selected.
[]
-
**User Groups**: When a user enrolls Zscaler Client Connector with the Zscaler service, Zscaler Client Connector checks the group to which the user belongs and downloads the app profile with the appropriate rule.
- Click **Selected** to select user groups from the drop-down menu. The groups you've configured in the Admin Portal are displayed in this menu. There is no limit to the number of groups you can select.
- Click **All **to select all groups.
When new user groups are added, they are automatically selected. You can clear the checkbox to exclude them from your policy.
-
**Users**: Select this option to apply this rule to a specific user. The users you've configured in the Admin Portal are displayed in this menu after a user enrolls Zscaler Client Connector with the Zscaler service. Zscaler Client Connector checks if the user belongs and downloads the app profile with the appropriate rule. You can select up to 50 users. By default, no users are selected.
Don't select a user or a user group if you want to create and save a rule before applying it to a user or a user group.
-
**Device Groups**: Select this option to apply this rule to specific groups or to all device groups. Click **Select All** to select all device groups or select individual groups from the drop-down menu. Device groups created in the Admin Portal are displayed in this menu. To learn more, see [Creating Device Groups](/unified/creating-device-groups).
Device groups are available only on Zscaler Client Connector version 4.3 and later for Windows devices.
- **Follow Global Settings for Partner Login**: Enable this option to apply the **Allow Users of This Tenant to Login to Other Tenants** setting from the [ZPA Partner Logins](/unified/enabling-private-applications-partner-logins) page to this profile. If enabled, you cannot configure partner login access on this profile.
-
**Allow Users of This Tenant to Login to Other Tenants**: Enable this option to let users access a partner’s tenant if they are assigned this profile. If you enable this option, you can enter **Partner Domains** that users can select when they add a partner tenant to Zscaler Client Connector. If you leave **Partner Domains** blank, users must enter the partner domain in the app and can connect to any partner tenant.
Partner login settings on the app profile are available only on Zscaler Client Connector version 4.6 and later for Windows.
[]
-
**PAC Configuration**:
- **PAC URL Location**: Select one of the following options:
- **PAC URL**: If you're using Zscaler Client Connector for Private Applications only, skip this option. Enter a valid PAC URL in the **Custom PAC URL** field if you want Zscaler Client Connector to forward internet traffic to the Zscaler service and want to specify exceptions for certain types of traffic. The maximum number of characters is 512. If [Enforce Secure PAC URLs](/unified/enforcing-secure-pac-urls) or [Use Endpoint Location for Zscaler DC Selection](/unified/configuring-zscaler-client-connector-app-profiles#advanced) is enabled, you must enter a URL with the https:// prefix (not http://).
- **Registry Key**:
- **Registry Path**: Enter the **Registry Path** for Zscaler Client Connector to locate the PAC URL from the device. The maximum number of characters is 61,440. If [Use Endpoint Location for Zscaler DC Selection](/unified/configuring-zscaler-client-connector-app-profiles#advanced) is enabled, you must enter a URL with the https:// prefix (not http://).
- **Registry Name**: Enter the **Registry Name** for Zscaler Client Connector to locate the PAC URL from the device. The maximum number of characters is 2,048.
- **Fallback to gateway domain**: When you select this checkbox, Zscaler Client Connector falls back to the gateway domain when PAC proxies cannot be reached for Z-Tunnel 1.0.
You must add a **Custom PAC URL** before you can use one of the following preferred ports.
- **Use Preferred Port from PAC for Z-Tunnel 1.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 1.0. This feature does not impact the default ports 80, 443, and 8080.
- **Use Preferred Port from PAC for Z-Tunnel 2.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 2.0. This feature does not impact the default ports 80, 443, and 8080.
If you want to allow a user to bypass the app when connecting to the VPN gateway, use the VPN Gateway Bypass option.
- **Proxy Configuration**: Select from the following options:
- **Override WPAD**: The option to override Web Proxy Auto-Discovery is applicable only if you've selected a forwarding profile that uses forwarding profile PAC files.
- **Disable Loopback Restriction**: When you enable this option, Zscaler Client Connector removes the communication restriction to the loopback interface for apps that use the Windows container. When selected, you can enable **Remove Existing Exempted Containers **to have Zscaler Client Connector remove existing exempted containers from the firewall configuration before disabling loopback restriction for all containers.
- **Restart WinHTTP Service**: This option is applicable only if you've selected a forwarding profile that uses forwarding profile PAC files. Zscaler recommends selecting this option to delete any cached WPAD settings.
- **V8 JavaScript based PAC Parser**: Enable Google’s open-source V8 engine to compile JavaScript for the PAC parser.
- **Set Proxies on VPN Adapters**: When enabled, Zscaler Client Connector sets configured proxy settings on VPN adapters in addition to physical adapters.
-
**Detect External Proxy Using Custom Method**: Enable this option to have Zscaler Client Connector identify the system proxy by downloading the PAC and parsing the proxy instead of using the default Microsoft API. This option can help prevent Privtae Applications connection errors that could happen if the Microsoft API doesn’t detect recent updates or returns stale proxy information.
Applies only to Zscaler Client Connector version 4.8 and later for Windows.
- **Cache System Proxy on Startup**: Enable this option to save and restore proxy settings. This setting captures any existing system proxy settings in memory when Zscaler Client Connector starts. If a user exits or logs out of the app, a user turns off Internet & SaaS from the app, or if Zscaler Client Connector is uninstalled, captured proxy settings are restored to the system.
-
**Re-cache System Proxy**: Enable this option to have Zscaler Client Connector monitor the system proxy and to re-cache the proxy settings if changes are detected (e.g., if the system proxy is updated by a Microsoft Group Policy Object (GPO) after a user has logged in to Zscaler Client Connector).
This option displays only if Cache System Proxy on Startup is enabled and does not apply if the forwarding profile has Enforce Proxy mode selected. Applies only to Zscaler Client Connector version 4.8 and later for Windows.
[]
[]
Configure traffic bypass for process-based applications, VPN gateways, and source ports:
-
**Process-Based Application Bypass**: Allows bypassing of process-based applications [created in Application Bypass](/unified/adding-process-based-applications-bypass-traffic) that can be used for both Z-Tunnel 1.0 and Z-Tunnel 2.0. Select an option from the drop-down menu.
To use this feature, you must enable **Install WFP Driver**.
- **Source Port-Based Bypasses**: Enter the source port and protocol from which Zscaler Client Connector bypasses existing inbound traffic. The port value can range from `1` to `65,535`. The protocol value can be TCP, UDP, or *. You can click the **Copy** icon to copy the items from the list.
-
**VPN Gateway Bypass**: You can allow traffic destined for the VPN to bypass Zscaler Client Connector. The app sets the routing table to exclude any traffic destined for the VPN gateway.
When a route-based driver is in use, the app creates IP-based exclude routes in the routing table. When a filter-based driver is in use, it creates bypass filters in the filter table.
When your users have a VPN client running on their devices in conjunction with Zscaler Client Connector, the VPN gateway bypass must be used in these scenarios:
- You selected Tunnel for the forwarding profile action of any trusted network type.
- Your VPN runs in split-tunnel mode so that it takes some, but not all, user traffic from the device.
To allow traffic to bypass Zscaler Client Connector using Tunnel mode, enter any of the following for all of your VPN gateways:
-
An FQDN (e.g., `www.safemarch.com`)
If you add a fully qualified domain name (FQDN), the FQDN resolves and all resulting IP addresses are added to the bypass list at the start of the tunnel. However, if the FQDN resolves to a different IP address later, that address might not be bypassed. Zscaler recommends adding an IP or subnet where possible. Adding too many FQDNs can slow tunnel startup because Zscaler Client Connector resolves all these domains before starting tunneling.
- A specific IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. To ensure against connectivity issues, you must include all the VPN hostnames, IP addresses, or subnets to which the VPN connects. You can click the **Copy** icon to copy the items from the list.
To allow traffic to bypass Zscaler Client Connector using Tunnel with Local Proxy mode, Zscaler recommends adding the IP address or addresses and hostname of the VPN gateway to the system PAC file in the forwarding profile to enable direct connections for VPN traffic. To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
While you can also use this field to bypass non-VPN destinations, you must limit the number of items in this list because Zscaler Client Connector attempts to resolve all entries after a network change.
- **Upload File**: Allows you to upload a VPN gateway bypass list. The format is a text file with values separated by new lines or commas. Subsequent uploads with similar data in the list will not duplicate existing entries, but will add only the new entries.
[]
If you use Z-Tunnel 2.0, you can configure traffic bypasses for IP-based applications and include or exclude traffic based on IPv4 and IPv6 subnets, IP addresses, ports, and protocols. You must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- **Predefined IP-Based Application Bypass**: To bypass Z-Tunnel 2.0, click **Select All** or select applications from the **IP-Based application bypass** drop-down menu. You can also search for items to select.
- **Custom IP-Based Application Bypass**: Select applications from the **IP-Based application bypass** drop-down menu to bypass Z-Tunnel 2.0. You can also search for items to select. To add applications to the IP-based application list, see [Adding IP-Based Applications to Bypass Traffic](/unified/adding-ip-based-applications-bypass-traffic).
-
**IPv4/IPv6 Inclusions and Exclusions**: To send or bypass a specific subset of your traffic to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0, [complete the following steps.](#IPv-win)
[]
When adding subnets, the protocol value is *, TCP, or UDP. You can also enter the subnet `0.0.0.0/0`, which stands for all possible subnets. The maximum number of characters in each field is 6,144. If you enter overlapping values in the inclusion and exclusion lists, the longest match takes precedence (e.g., if `192.0.2.0/24` is in **IPv4 Inclusion** and `192.0.2.0/24:*:tcp` is in **IPv4 Exclusion**, any TCP requests to the `192.0.2.0/24` subnet bypass Z-Tunnel 2.0. You can click the **Copy** icon to copy the items from the list.
-
**IPv4 Inclusion**: Enter the specific subnets of the traffic you want to include in Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp, 192.0.2.1:80`-`100:udp, `or` 192.0.2.1:80:*`)
The default configuration includes all possible subnets (`0.0.0.0/0`).
-
**IPv4 Exclusion**: Enter the specific subnets of the traffic you want to exclude from Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, or` `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp,` `192.0.2.1:80-100:udp, or 192.0.2.1:80:*`)
The default configuration includes the` 224.0.0.0/4` multicast range, the `169.254.0.0/16` link-local range, the `255.255.255.255` broadcast address, and the RFC 1918 default private networks (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`). To learn more, refer to [RFC 1918 Address Allocation for Private Internets](https://datatracker.ietf.org/doc/html/rfc1918).
- **IPv6 Inclusion**: Enter the specific subnets of the traffic you want to include in Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `[2001:0000::]`)
- A subnet (e.g., `[2001:0000::/32]`)
- An IP:Port range (e.g., `[2001:0000::]:80, [2001:0000::]:80-100, `or` [2001:0000::]:*`)
- An IP:Port:Protocol (e.g., `[2001:0000::]:80:tcp`)
-
**IPv6 Exclusion**: Enter the specific subnets of the traffic you want to exclude for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `[2001:0000::]`)
- A subnet (e.g., `[2001:0000::/32]`)
- An IP:Port range (e.g., `[2001:0000::]:80,` `[2001:0000::]:80-100,` or` [2001:0000::]:*`)
- An IP:Port:Protocol (e.g., `[2001:0000::]:80:tcp`)
The default configuration includes the `FF00::/8` multicast range, the `FE80::/10` link-local range, and the `FC00::/7` unique local range.
Zscaler recommends that you keep these networks in the list, unless explicitly needed, because deleting them causes private network traffic (e.g., DHCP) to be tunneled through the cloud.
[]
ZIA Disaster Recovery** **provides users access even when the Internet & SaaS service is down and is available only to enrolled users.
To configure ZIA Disaster Recovery:
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Direct Internet Access**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Policy Based Access (Web only)**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Custom Destinations** field.
- **Allow Zscaler Preselected Destinations (Recommended)**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**DR Custom PAC URL**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the Internet & SaaS service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
You must configure the **Disaster Recovery (DR) Custom** PAC URL pointing to the private PAC server for private business continuity cloud (`https://<private pac domain>.pac.zsbcs.net/<insert the rest of the PAC URL>`. For example, `http://platform-pm.pac.zsbcs.net/platform-pm.zscalerbeta.net/DRPAC`. To learn more about private business continuity, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
- When configuring the custom PAC file, ensure that you allow access to the Private Applications IP range `100.64.0.0/16` and Private Applications domains, `zpath.net` and `zpatwo.net`, to prevent blocking Private Applications traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
}
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
Use the following sample custom PAC file for private business continuity users:
The private business continuity feature is in limited availability. To learn more, contact your Zscaler Account team.
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "ebay.com")))
return "DIRECT";
if ((localHostOrDomainIs(host, "yahoo.com")) ||
(localHostOrDomainIs(host, "msn.com")))
return drop;
/* Default Block Statement to block anything not allowed above */
return "PROXY ${GATEWAY.platform-bcp.zscalerbeta.net}:80; PROXY ${SECONDARY.GATEWAY.platform-bcp.zscalerbeta.net}:80";
}
- Replace `Platform-bcp` with the organization name.
- Replace `zscalerbeta.net` with the name of the cloud on which your organization is provisioned.
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 and later for Windows.
- Return PROXY to the Zscaler-managed business continuity subcloud to maintain your policies in the business continuity environment.
-
**Policy Based Access (All Ports)**: You can either block or allow access to specific URLs using a custom PAC file. The DR Custom PAC URL field is selected by default, and you can insert a custom PAC file URL (with the http:// or https:// prefix) that users can access when the Internet & SaaS service is down in the Custom Destinations field. This option allows you to forward the selected internet traffic using Z-Tunnel 2.0.
When configuring the custom PAC file, ensure that you allow access to the Private Applications IP range 100.64.0.0/16 and Private Applications domains, `zpath.net` and `zpatwo.net`, to prevent blocking Private Applications traffic.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
}
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server (e.g., Internet & SaaS Private Service Edge) using Z-Tunnel 2.0.
Available only for Zscaler Client Connector version 4.8 and later for Windows.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
If you have Internet & SaaS only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload .pem files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
ZPA Disaster Recovery provides users access to applications when the Private Applications service is down and is available only to enrolled users.
To configure ZPA Disaster Recovery:
- Select **Enable ZPA DR**.
- **DNS Settings:**
- **Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Activation Domain Name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation**:** **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users and/or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
Business Continuity allows users to continue to access applications during Private Applications-related cloud outages or Internet Service Provider (ISP) outages. Select **Configure ZPA Business Continuity** to enable this feature. To learn more, see [Configuring Business Continuity for Zscaler Client Connector](/unified/configuring-business-continuity-zscaler-client-connector).
[]
-
If you use Z-Tunnel 2.0, you can control how DNS requests are handled by Zscaler Client Connector to send only specific DNS requests to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0. Complete the following steps in the **Domain Inclusion** and **Domain Exclusion** fields:
You can enter specific domains (e.g., `google.com`) or enter a wildcard (e.g., `*`* *or `*.[internaldomain].com`) to include or exclude all or specific DNS domains. For specific domains, up to two levels of subdomains are automatically included or excluded (e.g., if you enter `safemarch.com`, Zscaler Client Connector includes downloads.safemarch.com but not web.downloads.safemarch.com). Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. The maximum number of characters is 65,535 in each field. You can click the **Copy** icon to copy the items from the list.
- **Domain Inclusion**: Enter the DNS domains for which Zscaler Client Connector should send requests.
- **Domain Exclusion**: Enter the DNS domains for which Zscaler Client Connector should not send requests.
[How Zscaler Client Connector processes the domain inclusions and exclusions](#DNS_IP_in_Exclusion)
- **DNS Server Route Exclusion**: When enabled, Zscaler Client Connector excludes DNS servers from the routing table.
- **Parallel IPv4 and IPv6 DNS requests**:
- **None**: Select this option if you do not want Zscaler Client Connector to modify existing system settings for parallel IPv4 and IPv6 DNS requests. The default is **None**.
- **Disabled**: Select this option to allow parallel IPv4 and IPv6 DNS requests via the Windows Registry.
- **Enabled**: Select this option to turn off parallel IPv4 and IPv6 DNS requests via the Windows Registry. This helps prevent requests from being dropped or blocked.
- **Truncate ZPA Large UDP DNS Response**: Enable to truncate DNS responses that exceed 512 bytes to retry the DNS query over TCP.
- **Update DNS Search Order**: When enabled, Zscaler Client Connector prioritizes Zscaler’s DNS over Cisco’s DNS. The higher priority DNS gets the DNS traffic.
- **Bind Trusted Criteria DNS request to Default Adapter**: This option has Zscaler Client Connector connect the DNS request to the default adapter. By default, this option is enabled. Disabled means Zscaler Client Connector does not connect the Trusted Hostname IP resolution DNS request to the default adapter.
-
**Prioritize DNS Exclusions over Z-Tunnel 2.0**: This feature is enabled by default in new app profiles and is recommended because DNS requests for excluded domains aren't sent to Internet & SaaS, which can cause resolution issues. Applies only to Zscaler Client Connector version 4.6 and later for Windows.
[How Zscaler Client Connector processes the domain inclusions and exclusions](#DNS_IP_in_Inclusion)
[]Zscaler Client Connector first checks if the DNS server IP address on the client is in **IPv4 Exclusion** or **IPv6 Exclusion**. If the DNS server IP address on the client is in either exclusion, Zscaler Client Connector then processes domain inclusions followed by domain exclusions. An explicit domain match takes precedence over a wildcard-based match. If the domain doesn't match a domain listed in **Domain Inclusion** or **Domain Exclusion** or the fields are empty, the DNS request is sent to the DNS server defined on the device.
If the DNS Server IP matches a value in **IPv4 Exclusion** or **IPv6 Exclusion**, Zscaler Client Connector sends the DNS request based on the following:
| Domain matches Domain Inclusion | Domain matches Domain Exclusion | DNS Request Forwarded To |
| ------------------------------- | ------------------------------- | ------------------------ |
| No | Yes | DNS Server on the device |
| Yes | No | Internet & SaaS |
| Wildcard (*) | Yes | DNS Server on the device |
| Wildcard (*) | No | Internet & SaaS |
| No or **Domain Inclusion** is empty | Wildcard (*) | DNS Server on the device |
| Yes | Wildcard (*) | Internet & SaaS |
| No | No | DNS Server on the device |
| **Domain Inclusion** is empty | **Domain Exclusion** is empty | DNS Server on the device |
Zscaler Client Connector prioritizes domain inclusions over domain exclusions unless **Prioritize DNS Exclusions over Z-Tunnel 2.0** is enabled.
[]Zscaler Client Connector first checks if the DNS server IP address on the client is in **IPv4 Inclusion** or **IPv6 Inclusion**. If the DNS server IP address on the client is in either inclusion, Zscaler Client Connector then processes domain exclusions followed by domain inclusions. An explicit domain match takes precedence over a wildcard-based match. If the domain doesn't match a domain listed in **Domain Inclusion** or **Domain Exclusion** or the fields are empty, the DNS request is sent to Internet & SaaS.
If the DNS Server IP matches a value in **IPv4 Inclusion** or **IPv6 Inclusion**, Zscaler Client Connector sends the DNS request based on the following:
| Domain matches Domain Inclusion | Domain matches Domain Exclusion | DNS Request Forwarded To |
| ------------------------------- | ------------------------------- | ------------------------ |
| No | Yes | DNS Server on the device |
| Yes | No | Internet & SaaS |
| Wildcard (*) | Yes | DNS Server on the device |
| Wildcard (*) | No | Internet & SaaS |
| No | Wildcard (*) | DNS Server on the device |
| Yes | Wildcard (*) | Internet & SaaS |
| No | No | Internet & SaaS |
| **Domain Inclusion** is empty | **Domain Exclusion** is empty | DNS Server on the device |
| **Domain Inclusion** is empty | No | DNS Server on the device |
| No | **Domain Exclusion** is empty | DNS Server on the device |
[]This section displays only if [Location Policy Override](/unified/configuring-zscaler-client-connector-app-profiles#general) is enabled.
-
**Location Ruleset Assignment**: Select a location ruleset from the [Location-Based Policies](/unified/about-location-based-policies) page for each of the following network types:
- **On-Trusted Network**
- **Off-Trusted Network**
- **VPN-Trusted Network**
- **Split VPN-Trusted Network**
You must select a ruleset for On-Trusted Network and for Off-Trusted Network. For VPN-Trusted Network and Split VPN-Trusted Network, the default value is Same as "On-Trusted Network," but you can change or clear it.
-
**Win V4.7 and Older Client Configuration**: The traffic steering and firewall configuration for users with this app profile that use Zscaler Client Connector version 4.7 and earlier. The default values are the ones that were configured in the app profile before the Location Policies Override feature was enabled, but you can change the values.
If [Endpoint Firewall Management](/unified/configuring-zscaler-client-connector-app-profiles#firewall) is not enabled, the Block All Inbound Traffic option in this section is not available and Zscaler Client Connector uses the Block All Inbound Traffic option in the Firewall section.
[]
-
**Tunnel Internal Client Connector Traffic**: Enable this option for Zscaler Client Connector to tunnel internal traffic (e.g., app updates and policy updates) through Zscaler. This option is only applicable if you deploy in a no-default route environment and applies to Zscaler Client Connector version 2.12 and later for Windows. If disabled, Zscaler Client Connector sends internal traffic directly.
When this option is enabled, Zscaler Client Connector does not tunnel PAC requests and continues to send PAC requests directly.
- **Intercept ZIA traffic**: Enable this option to have Zscaler Client Connector intercept Internet & SaaS traffic from all network adapters. This setting only applies to Tunnel Mode with a Packet Filter Based driver. Disable this option to have Zscaler Client Connector intercept Internet & SaaS traffic only from the default adapters (adapters with 0.0.0.0/0 route).
- **Prioritize IPv4 over IPv6**: This setting configures the operating system to prefer IPv4 over IPv6 and impacts applications running on that device. When enabled, this feature has no impact on IPv6 configuration. Applies to Zscaler Client Connector version 3.4 and later for Windows.
- **Route Table for Tunnel Connections**: Enable to have Zscaler Client Connector follow the routing table to connections for Internet & SaaS (i.e, Z-Tunnel 1.0, Z-Tunnel 2.0), Private Applications, and bypassed connections. If the setting remains disabled, it instead binds to the system's default interface.
- **Reactivate ZIA After**: Enter the number of minutes that must pass before Zscaler Client Connector reactivates Internet & SaaS after the user turns it off. To enable the reactivation period, enter any value from `1` to `1,440` minutes. To disable, enter `0` (zero) so that Zscaler Client Connector doesn't reactivate Internet & SaaS after the user turns it off.
-
**Use Endpoint Location for Zscaler DC Selection**: Enable this option to have Zscaler Client Connector use location services on the user’s device to find the nearest data center instead of MaxMind’s GeoIP. This option can help remote users avoid connecting to sub-optimal DCs due to incorrect geo-lookup results from MaxMind. Users must enable location services on their devices to use this option, and you must ensure that the URL in the Custom PAC File or the Registry Path uses the HTTPS protocol (not HTTP).
Applies only to Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
[]
If fail-open settings are also configured in [Client Connector Support](/unified/configuring-fail-open-settings-zscaler-client-connector), these fail-open settings take precedence. This feature is available only in Zscaler Client Connector version 4.6 and later for Windows.
- **ZIA Cloud Not Reachable**: Select one of the following options to set what happens if the ZIA cloud is not available:
- **Follow Global Config**: Allow access based on the setting in **ZIA Cloud Not Reachable** in [Client Connector Support](/unified/configuring-fail-open-settings-zscaler-client-connector). This option is selected by default.
- **Direct Internet Access**: Users are allowed to bypass the app and access the internet directly.
- **Disable Internet Access**: Blocks HTTP/HTTPS traffic. All other traffic is allowed.
- **Fallback to ZIA DR**: If **Enable ZIA DR** is enabled, follow the traffic forwarding settings in ZIA Disaster Recovery.
- **Z-Tunnel Failover**: Select one of the following options to set what happens if Zscaler Client Connector cannot establish a tunnel (Z-Tunnel 1.0 only):
- **Follow Global Config**: Allow access based on the setting in **Z-Tunnel Failover** in [Client Connector Support](/unified/configuring-fail-open-settings-zscaler-client-connector). This option is selected by default.
- **Direct Internet Access**: Users are allowed to bypass the app and access the internet directly.
- **Disable Internet Access**: Blocks HTTP/HTTPS traffic. All other traffic is allowed.
- **Fallback to ZIA DR**: If **Enable ZIA DR** is enabled, follow the traffic forwarding settings in ZIA Disaster Recovery.
-
[]**Endpoint Firewall Management**: When enabled, the Zscaler firewall uses location-based policies instead of other firewall rules (e.g., Windows Defender) to determine which inbound and outbound traffic is allowed and blocked. The default setting is disabled. Enable this option only if you want to use the endpoint firewall rules in rulesets. You must enable Install WFP Driver and Location Policy Override to select this option. To learn more, see [About Location-Based Policies](/unified/about-location-based-policies).
If enabled, the following app profile options are unavailable:
- Install Windows Firewall Inbound Rule
- Block All Inbound Traffic
- Trigger Domain Profile Detection
[How Zscaler Client Connector creates endpoint firewall rules with Endpoint Firewall Management](#firewall-rules)
This feature is available only for Zscaler Client Connector version 4.8 and later for Windows. Contact Zscaler Support to enable this feature.
-
**Install Windows Firewall Inbound Rule**: When enabled, Zscaler Client Connector installs the Zscaler Client Connector App Inbound Rule to the Windows Defender firewall.
Contact Zscaler Support to enable this feature.
-
**Block All Inbound Traffic**: When enabled for one or more network types, Zscaler Client Connector installs Zscaler App Rule as a Windows Filtering Platform (WFP) filter. Inbound traffic is allowed to the tunnel for the selected network types. After selecting one or more network types, the **Port-based Exclusions for Inbound Traffic** field appears. Enter the port and protocol to exclude the port from being blocked. The port value can range from `1` to `65535`. The protocol value can be TCP, UDP, or *.
This feature applies only to Zscaler Client Connector version 4.5 and later for Windows. To use this feature, you must first enable Install WFP Driver and you must not enable Install Windows Firewall Inbound Rule.
-
**Trigger Domain Profile Detection**: Enable this option to have Zscaler Client Connector prevent Windows Defender Firewall Domain Profile detection events during Private Applications service connections and disconnections. You can use this setting to ensure that Windows Defender Firewall on remote endpoints (i.e., Off-Trusted Network) continues to use the Public Profile when connected via Private Applications and apply secure firewall rules (e.g., you can block inbound internet traffic). However, when the endpoint is on-premises (i.e., On-Trusted Network), Windows Defender Firewall can automatically switch to the Domain Profile. Applies to Zscaler Client Connector version 4.4 or later for Windows.
To use this feature, you must enable the **Install WFP Driver** feature.
- **Block Domain Profile Detection**: When you enable **Trigger Domain Profile Detection**, you can select the different network types for which Zscaler Client Connector blocks Windows Defender Firewall domain profile detection. Choose **Select All **or one or more of the following options from the drop-down menu:
- **On-Trusted Network**
- **VPN-Trusted Network**
- **Off-Trusted Network**
- **Split VPN-Trusted Network**
[]If [Endpoint Firewall Management](/unified/configuring-zscaler-client-connector-app-profiles#firewall) is enabled, host firewall rules are created based on the assigned ruleset in the user's app profile for the active network type. These Zscaler Client Connector firewall rules take precedence over the existing host firewall rules (e.g., Windows Defender firewall).
You cannot use the Endpoint Firewall Management feature with third-party host firewall management solutions.
Zscaler Client Connector creates four types of firewall rules. The four types of rules are listed from highest to lowest priority:
-
-
-
-
-
-
[](/unified/configuring-zscaler-client-connector-app-profiles#firewall)
-
-
[](/unified/configuring-zscaler-client-connector-app-profiles#firewall)
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
| Type of Rules | Description | When Created | When Removed |
| ------------- | ----------- | ------------ | ------------ |
| Required for Zscaler Client Connector to function | Allow Zscaler Client Connector to maintain a control channel with the Zscaler Zero Trust Exchange (ZTE) for:Policy managementInternet & SaaSPrivate ApplicationsDigital Experience MonitoringZscaler Client Connector updatesPrivate Applications VPNAllow Zscaler Client Connector to maintain a data channel for traffic forwarding with the Zscaler Zero Trust Exchange (ZTE). | When Endpoint Firewall Management is enabled | The user exits or logs out of Zscaler Client ConnectorThe user logs out of the Windows session. |
| Required for core networking | Allow DNS, DHCPv4, DHCPv6, NTP, Kerberos, Loopback communications and ICMPv6 traffic required for IPv6.All allowed traffic rules are based on host services and not on port and protocol rules. For example, DNS resolutions are allowed if the request is handled by the host DNS service but not from utilities like nslookup. | When Endpoint Firewall Management is enabled | The user exits or logs out of Zscaler Client ConnectorThe user logs out of the Windows session. |
| Policy ruleset rules | Endpoint firewall rules defined in the policy ruleset assigned to the user's app profile based on the current network type. | When firewall rules are defined for the active network type and Zscaler Client Connector is forwarding traffic | The user exits or logs out of Zscaler Client ConnectorThe user logs out of the Windows session.The user stops the Internet & SaaS or Private Applications service.The Zscaler Tunnel (Z-Tunnel) or driver crashes. |
| Default rules | A default rule to allow all outbound traffic and a default rule to block or allow inbound traffic as defined in the policy ruleset. | When default firewall rules are defined for the active network type and Zscaler Client Connector is forwarding traffic | The user exits or logs out of Zscaler Client ConnectorThe user logs out of the Windows session.The user stops the Internet & SaaS or Private Applications service.The Zscaler Tunnel (Z-Tunnel) or driver crashes. |
The firewall rules are not added to or visible in Windows Defender. You can view a list of firewall rules created when Endpoint Firewall Management is enabled:
- Search for the `[ZSAFW]` string in the ZSATunnel log.
- Use Windows PowerShell to dump all WFP filters using the `netsh wfp dump` command.
-
Enable WFP Events in the Windows Event Log using the following commands: `> auditpol /set /subcategory:"Filtering Platform Policy Change" /success:enable /failure:enable`
You can also use these commands to view which traffic is being blocked by the Zscaler Client Connector firewall rules by publishing connection drop events to the Windows Event Log.
[]Enter the settings to use when Zscaler Client Connector is in strict enforcement mode and is in a fail-close state. You can include a configuration file with these settings when installing Zscaler Client Connector in strict enforcement mode using an [MSI file](/unified/customizing-zscaler-client-connector-install-options-msi) or an [EXE file](/unified/customizing-zscaler-client-connector-install-options-exe). If Zscaler Client Connector cannot retrieve the config profile after an initial enrollment attempt, Zscaler Client Connector uses these settings until the config profile is retrieved from the Zscaler back-end servers.
This feature is available only with Zscaler Client Connector version 4.6 and later for Windows and requires the **Install WFP Driver** option to be enabled.
- **Process-Based Application Bypass**: Allows bypassing of process-based applications [created in Application Bypass](/unified/adding-process-based-applications-bypass-traffic). Select an option from the drop-down menu.
- **IP Address Bypasses**: Allows bypassing of IP addresses. Enter any of the following:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, or 192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp, 192.0.2.1:80-100:udp, or 192.0.2.1:80:*`)
- **Exit or Uninstall Password**: Provide the password users must enter to exit or uninstall Zscaler Client Connector when in a fail-close state.
- **Thumbprint**: The public key to use with the fail-close settings configuration file. Click **Copy** to copy the thumbprint for use during installation.
- **Lockdown on Tunnel Process Exit**: Enable this option to have Zscaler Client Connector fail close while a tunnel is starting or restarting (e.g., after a user logs in to the device or out of the app, clicks **Repair App** or clicks **Restart Service**).
- **Lockdown on Firewall Error**: Enable this option to have Zscaler Client Connector fail close while a firewall or antivirus program is blocking Zscaler Client Connector traffic (i.e., an End FW/AV Error). Applies only to Zscaler Client Connector version 4.7 and later for Windows.
- **Lockdown on Driver Error**: Enable this option to have Zscaler Client Connector fail close while a Windows Lightweight Filter (LWF) driver error is preventing Zscaler Client Connector from starting a tunnel. Applies only to Zscaler Client Connector version 4.7 and later for Windows.
- **Download Zscaler Client Connector Fail Close Configuration**: Download a configuration file with these settings to use when installing Zscaler Client Connector.
[]
- **Install Endpoint DLP**: Enable **Install Endpoint DLP** to install Endpoint Data Loss Prevention (DLP) on a device. To learn more, see [About Endpoint Data Loss Prevention](/unified/about-endpoint-data-loss-prevention) and [Zscaler Endpoint Data Loss Prevention (DLP) Integration with Zscaler Client Connector.](/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector)
[]Configure the following optional passwords:
- **Logout Password**: Provide the password users must enter to log out of Zscaler Client Connector.
- **Disable Password ZIA**: Provide the password users must enter to disable the Internet & SaaS service.
- **Disable Password ZPA**: Provide the password users must enter to disable the Private Applications service.
- **Exit Password**: For Zscaler Client Connector version 3.5 and later for Windows, provide the password users must enter to exit the app from the system tray without disabling Internet & SaaS. For Zscaler Client Connector version 3.5 or earlier for Windows, this setting has the same functionality as **Disable Password ZIA**.
- **Uninstall Password**: Provide the password users must enter to uninstall Zscaler Client Connector.
- **Password to Disable ZDX**: Provide the password users must enter to disable the Digital Experience Monitoring service.
- **Password to Disable Endpoint DLP**: Enter a password to disable the [Endpoint Data Loss Prevention (DLP)](/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector) feature.
Click the **View **icon next to each password setting to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
[]
-
**Machine Token**: Select the machine token to which the rule applies from the drop-down menu. Machine tokens are configured in the Admin Portal. In the Admin Portal, machine token is referred to as [Machine Provisioning Key](/unified/about-machine-provisioning-keys).
Changing the existing machine token, or applying a different app profile to users or groups, won’t override the configuration of existing machine tunnels. You must remove the machine token from the app profile and then remove the machine tunnel in [Enrolled Devices](/unified/about-enrolled-devices) in the Admin Portal or users must reinstall Zscaler Client Connector. If you’re migrating to a new tenant, you must [uninstall](/unified/uninstalling-zscaler-client-connector) and reinstall Zscaler Client Connector.
- **ZPA Machine Authentication**: When you enable this option, you require users to authenticate against your IdP before the machine tunnel starts if you use the machine tunnel feature in Private Applications.
- **Oauth 2.0 One Id Machine Tunnel Authentication**: If you are subscribed to ZIdentity, you can enable this option to require users to authenticate on an external device set up to use an OAuth 2.0-based authentication mechanism before the machine tunnel starts. When end users click Zscaler Diagnostics on the Windows lock screen, the authentication window that appears includes a verification link and passcode and also a QR code that users can scan.
- **Force ZPA authentication to expire**: To trigger Private Applications authentication to expire, choose **Select All **or one or more of the following actions from the drop-down menu:
- **On System Sleep/Hibernate**: Trigger expiration when the system is put into sleep or hibernation mode.
-
**On System Restart**: Trigger expiration when the system is restarted.
This option does not trigger expiration if users log in to Windows with fast startup enabled.
- **On Network IP Change**: Trigger expiration if the network IP changes.
- **Windows Logon Session Start**: Triggers expiration when a user logs in, even if fast startup is enabled. Applies to Zscaler Client Connector version 4.5 and later for Windows.
- **Windows Session Lock**: Triggers expiration after a Windows user has been locked for the number of minutes in the **Minimum Time in Locked State (In Minutes)**. You can enter a number of minutes from `1` to `60`. Applies to Zscaler Client Connector version 4.6 and later for Windows.
-
**Prevent Auto Reauth During Device Lock**: If [Automatically Attempt ZPA Reauthentication](/unified/configuring-automatic-private-applications-reauthentication) is enabled, this option prevents the automatic reauthentication on a locked device until the device is unlocked (e.g., you use MFA and don’t want users to experience unexpected authorization requests if the Private Applications authentication expires while they’re away from their device).
This setting does not affect automatic reauthentication while a device is in sleep mode (without being auto-locked), in hibernate mode, or after a system restart. Applies only to Zscaler Client Connector version 4.8 and later for Windows.
-
**Automatically use previously selected certificate for reauthentication**: Select this option to store the certificate that users selected from the pop-up window if multiple authentication certificates are available when [authenticating using WebView2](/unified/enabling-webview-2-0-authentication). When users reauthenticate, the stored certificate is used automatically and they don’t have to re-select a certificate. The pop-up window does not display unless **Always display certificate info before reauthentication** is also selected.
Applies only to Zscaler Client Connector version 4.7 for Windows and is available if the **Display certificate selection popup on desktop option** is enabled.
-
**Always display certificate info before reauthentication**: Select this option to display the cached certificate in a pop-up window to require users to confirm that they want to use the previously selected certificate when reauthenticating.
Applies only to Zscaler Client Connector version 4.7 for Windows and is available if the **Automatically use previously selected certificate for reauthentication** is enabled.
[]
This feature is available only with Zscaler Client Connector version 4.8 and later for Windows. You must also enable Integrated Windows Authentication (IWA). To learn more, see [Configuring Automatic Private Applications Reauthentication](/unified/configuring-automatic-private-applications-reauthentication).
- **Follow Global Settings ZPA Reauthentication**: Enable this option to apply the Automatically Attempt ZPA Reauthentication setting from the [App Supportibility](/unified/configuring-automatic-private-applications-reauthentication) tab to this app profile. If enabled, you cannot configure Private Applications reauthentication on this profile.
- **Automatically Attempt ZPA Reauthentication by Location**: Select one or more network types from which to allow users to continue to access Private Applications. When a user changes locations and a network switch occurs, Zscaler Client Connector updates access based on these settings. Choose **Select All** or one or more of the following options from the drop-down menu:
- **On-Trusted Network**
- **VPN-Trusted Network**
- **Off-Trusted Network**
- **Split VPN-Trusted Network**
- **Timeout for Automatic ZPA Reauthentication (in seconds)**: Select the time it takes for the browser to automatically reauthenticate. The default is 30 seconds. You can also select 60, 90, or 120 seconds. If a user changes locations and a network switch occurs, the timeout does not restart.
[]
- **Log Mode**: Zscaler Client Connector generates logs that users can send to a designated support admin in your organization, or to Zscaler Support (in encrypted form). To specify the scope of the logs, select one of the following log modes:
- **Default (Current: <log mode>)**: Displays the default global log mode [configured in Platform Settings](/unified/configuring-default-global-log-mode). You can override this setting, for the current profile only, by selecting a different option from the drop-down menu.
- **Error**: Zscaler Client Connector logs only when the app encounters an error and functionality is affected.
- **Warn**: Zscaler Client Connector logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Zscaler Client Connector logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Zscaler Client Connector logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Log File Size in MB**: If you are using Zscaler Client Connector for Private Applications only, skip this option. Enter a value between `50` and `1,000` to specify the maximum size of the log file. The default log file size is 100 MB per log type. When logs reach the maximum file size, the oldest logs are truncated from the file to keep the file size below the maximum.
- **Use Zscaler Notification Framework**: This option enables notifications from the [Zscaler Notification Framework](/unified/using-zscaler-notification-framework) instead of from the Windows-based notification system.
-
**Bring Notification to Focus**: Enable this option to automatically bring the focus to notifications displayed by the Zscaler Notification Framework. You can use this feature to support user accessibility by directing the screen reader (e.g., Windows Narrator) focus automatically. Available with Zscaler Client Connector version 4.7 and later for Windows.
The default value for this option is **Enabled**. If enabled, the Windows idle screen timer resets when a notification is displayed, which can delay the device locking.
- **Notify Users before ZPA Authentication Expires**: Enable this option to alert users that applications they recently accessed through Private Applications are going to expire. In the warning message that displays, users can click **Reauthenticate** to take them to an authentication screen before expiration. You can set the time to display the expiration notification before an application expires in the **Advanced Notification time (In Mins)** field. Enter a value between `5` and `1,440`. Users can also click **Authenticate Early in** the **Private Access** window, under the Connectivity** **section, in Zscaler Client Connector, to reauthenticate Private Applications before their authentication expires.
-
**Flow Logging**: When enabled, a WFP-based Zscaler driver is installed for flow logging to capture excluded traffic.
You must enable **Install WFP Driver** to use this feature.
Zscaler Client Connector logs and reports traffic flows to Internet & SaaS from the following areas you enable:
- **ZPA**: Traffic that goes through the Private Applications Tunnel.
- **Direct**: Traffic that goes to the internet/intranet directly (i.e., the traffic not handled by Zscaler or VPN).
- **Report Zscaler Client Connector Blocked Traffic**: Whether the Flow Logger should report the traffic blocked by Zscaler Client Connector. This type of flow is also known as Unclassified Flow.
-
**Enable Local Packet Capture**: Enable this option to let users with this app profile access local packet capture. This option overrides the global setting for [Enable Local Packet Capture in Zscaler Client Connector](/unified/enabling-packet-capture-zscaler-client-connector) on the User Privacy tab.
When the feature is first enabled, the default value is the existing value from the Enable Local Packet Capture in Zscaler Client Connector field on the User Privacy tab.
-
**Enable Automatic Packet Capture**: Select this option to automatically start packet capture in selected scenarios. When enabled, the following options appear:
-
**Critical Scenarios**: Starts packet capture if Zscaler Client Connector fails to connect to Z-Tunnel 1.0, Z-Tunnel 2.0, a detected captive portal, or Private Applications, or if Zscaler Client Connector encounters a FW/AV error.
Packet capture can also be enabled for a lost connection to Z-Tunnel 1.0. Contact Zscaler Support to enable this scenario.
-
**Other Scenarios**: Starts packet capture if a connection to Z-Tunnel 2.0 is lost.
Packet capture can also be enabled when switching from a primary to a secondary Service Edge (or vice versa) based on [Dynamic ZIA Service Edge Assignment](/unified/configuring-forwarding-profiles-zscaler-client-connector#tunnel) or [Dynamic ZPA Service Edge Assignment](/unified/configuring-forwarding-profiles-zscaler-client-connector#forwarding-profile-action-zpa). Contact Zscaler Support to enable this scenario.
- **Allocate Additional space for Automatic Packet Capture**: Select this option to increase the disk space limit for PCAP files from the default setting of 500 MB. Two files for each scenario are stored until the space limit is reached, and then the oldest PCAP file is deleted. When this option is selected, you can select 1 GB, 2 GB, or 4 GB in **Additional Space**.
Applies only to Zscaler Client Connector version 4.8 and later for Windows. This option displays only if you select **Enable Local Packet Capture**.
[]These settings apply only to Zscaler Client Connector version 4.5 and later for Windows. If you use Zscaler Client Connector version 4.4 or earlier for Windows, you can enable captive portal detection on the Client Connector Support page. To learn more, see [Configuring Fail-Open Settings for Zscaler Client Connector](/unified/configuring-fail-open-settings-zscaler-client-connector).
- **Captive Portal Detection**: Select to enable captive portal detection.
-
**Fail Open**: Select to enable a fail-open state if a captive portal is detected. If enabled, Zscaler Client Connector blocks all traffic until users register in the captive portal using the embedded browser.
To use this feature, you must first enable** Embedded Captive Portal** in the app profile.
-
**If Captive Portal Detected, Then Disable Web Security for**: Enter the number of minutes the app must keep its services disabled after detecting a captive portal when **Fail Open** is enabled. You can enter any value between `1` and `60`. After the specified period, the app enables its services automatically and traffic is forwarded to the Zscaler service.
When configuring fail-open settings, Zscaler recommends setting the captive portal detection to a value that gives users a reasonable amount of time measured from the network change detection to the time they complete entering information requested by the portal. You cannot enter `0` (zero) in this field with Zscaler Client Connector version 4.5 and later for Windows. To disable captive portal detection, you must use the **Captive Portal Detection** field.
-
**Embedded Captive Portal**: Select to enable an embedded browser to use when Zscaler Client Connector detects a captive portal. If enabled, the captive portal loads in the embedded browser (not the default browser) for user authentication. Users do not access the internet directly. All network traffic is blocked except for Zscaler Client Connector processes (DHCP, DNS, LDAP, and Kerberos). Zscaler Client Connector does not apply internet security to the captive portal, so you must use a separate antivirus solution if you want to secure captive portal traffic.
Zscaler recommends that you enable the Zscaler Notification Framework so that end users receive a pop-up notification that allows them to open the captive portal with one click. To learn more, see [Using the Zscaler Notification Framework](/unified/using-zscaler-notification-framework).
To use this feature, you must first enable **Install WFP Driver** in the app profile and enable **WebView2**. To learn more, see [Enabling WebView2 Authentication](/unified/enabling-webview-2-0-authentication).
-
**Packet Capture for Captive Portal**: This option automatically starts packet capture when Zscaler Client Connector detects a captive portal. Zscaler Client Connector captures packets until 5 minutes have passed, or the user successfully authenticates the captive portal and the internet becomes available, or the disk space limit is reached. The disk space limit is the default setting (1 GB) or the latest limit set during manual packet capture.
The app displays notifications to users, but users do not need to manually start or stop the packet capture. The packet capture files are stored with the Zscaler Client Connector logs.
To use this feature, you must also enable local packet capture. To learn more, see [Enabling Packet Capture for Zscaler Client Connector](/unified/enabling-packet-capture-zscaler-client-connector).
[]Select the default display language for the Zscaler Client Connector app and the text in the Notifications window:
- **Use System Language**: The app displays based on the system language. This value is the default setting.
- **English**: The app displays in English, regardless of the user’s system language settings.
Users can change the display language from the default on the **More** window in the app (e.g., if they need to change the language temporarily when working with internal support).
This feature is available only with Zscaler Client Connector version 4.8 and later for Windows.
[]Enable **Configuration** to specify if the Microsoft System Center Configuration Manager (SCCM) app uses location detection behavior. This option is only applicable for Zscaler Client Connector version 3.6 and later for Windows. You can select **Cloud Management Gateway** (CMG) to force the SCCM client to always use the internet or use **Location Discovery**, which is the default.
- **On-Trusted Network**
- **VPN-Trusted Network**
- **Off-Trusted Network**
- **Split VPN-Trusted Network**
[]Enable **Command Line Interface** to allow admins to [interact with Zscaler Client Connector via a CLI.](/unified/interacting-zscaler-client-connector-remotely) Applies to Zscaler Client Connector version 4.4 or later for Windows.
If enabled, you can select the following options in **Disable Services**:
- **Disable ZPA Password**: Select this option to require a password when disabling the Private Applications service via CLI.
- **Disable ZIA Password**: Select this option to require a password when disabling the Internet & SaaS service via CLI. Applies to Zscaler Client Connector version 4.8 or later for Windows.
- **Disable ZDX Password**: Select this option to require a password when disabling the Digital Experience Monitoring service via CLI. Applies to Zscaler Client Connector version 4.8 or later for Windows.
For each selected option, you can click **Generate <Service> Disable Password** to generate a password to disable the service in the CLI and click **Cop**y to copy the generated password. Passwords expire after two hours.
[]This feature is available only for Zscaler Client Connector version 4.6 and later for Windows. Contact Zscaler Support to enable this feature.
- **Zscaler Client Connector Telemetry**: Enable to collect metrics including device events, statistics, profile, statistics for Zscaler Client Connector processes, and the top 5 processes. These metrics do not include personally identifiable information (PII). The default value is enabled.
[]
-
**Enable Anti-tampering**: Enable to allow anti-tampering. [Anti-tampering protection](/unified/anti-tampering-zscaler-client-connector) prevents end users from stopping and modifying Zscaler endpoint products.
You can set a timer to re-enable Zscaler Client Connector if a user disables it using the one-time password (OTP). In the **Reactivate Anti-Tampering After (In Mins)** field, enter a value between `0` and `1,440` minutes.
- **Override Anti Tampering Install Parameter**: Enable to use the **Enable Anti-tampering** setting from the app profile regardless of how the `--enableAntiTampering` or `ENABLEANTITAMPERING` install option was set during installation. Applies to Zscaler Client Connector version 4.5 and later for Windows only.
- **Send Disable Service Reason**: This option allows users to send a description about why a Zscaler service (e.g., Internet & SaaS, Private Applications, Digital Experience Monitoring) was disabled on a device. By default, this option is disabled. This information is accessible when viewing [device details](/unified/viewing-device-fingerprint-enrolled-device).
-
**Enable Zscaler Client Connector Revert**: When enabled, users have the option to [revert to the previous Zscaler Client Connector version](/unified/reverting-zscaler-client-connector-previous-version). Applies to Zscaler Client Connector version 3.9 and later for Windows. In the **Revert Password** field, provide the password that users must enter to revert to the previous Zscaler Client Connector version.
Click the **View **icon to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
- **Highlight Active Control**: Enable this option to display an outline around an actively selected control. Applies to Zscaler Client Connector version 2.1.2 and later for Windows.
- **Clear Kerberos DC:** Enable to clear the list of Kerberos preferred domain controllers in the cache when Zscaler Client Connector connects to and disconnects from Private Applications. Applies to Zscaler Client Connector version 4.5 and later for Windows only.
- **Force Location refresh on SCCM Client**: Enable this option to have Zscaler Client Connector trigger a location sync with the management point when the device connects to or disconnects from Private Applications instead of waiting for the SCCM client to do the automatic sync. Applies to Zscaler Client Connector version 4.5 and later for Windows only.
[]
**Policy Description**: Enter any notes regarding the policy.
[]To add a new macOS policy rule:
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **macOS** and click **Add macOS Policy**. The **Add macOS Policy **window appears.
-
In the **Add macOS Policy **window, you can configure the following settings:
To find an option, you can enter search words in the **Search** field and press `Enter`. A navigation path to the option appears in the search results.
- [General](#mac-general)
- [Groups](#mac-groups)
- [Traffic Steering](#mac-traffic)
- [Firewall](#mac-firewall)
- [Data Protection](#mac-data-protection)
- [Passwords](#mac-otp)
- [Authentication](#mac-auth)
- [Notification and Logging](#mac-notification)
- [Command Line Interface Access](#mac-CLI)
- [Zscaler Client Connector Telemetry Options](#mac_telemetry)
- [Advanced](#mac-adv)
- [Policy](#mac-policy)
[]
- [Pac and Proxy](#mac-pac-proxy)
- [App and IP Bypass](#mac-app-bypass)
- [Disaster Recovery](#mac-DR)
- [DNS](#mac-DNS)
- [Advanced](#mac-advanced)
[]
- [Global Bypasses](#mac-global)
- [IP Bypasses](#mac-IP)
[]
- [ZIA Disaster Recovery](#mac-ZIA)
- [ZPA Disaster Recovery](#mac-ZPA)
[]
- **Name**: Enter a unique alphanumeric name for your policy rule.
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order reflects the order of precedence among configured profile policy rules and helps determine which rule the app downloads for a user upon enrollment. Precedence is based on ascending numerical order.
- **Status**: Select **Disabled** to inactivate the rule or select **Enabled **to activate the rule. If you don’t enable the rule, the policy rule is not enforced.
-
**Forwarding Profile**: Select a forwarding profile of your configured forwarding profiles from the drop-down menu. You can also search for items to select. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
If you're using Zscaler Tunnel (Z-Tunnel) 2.0, you must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- **ZIA Posture Profile**: Select a [posture profile](/unified/about-internet-saas-posture-profiles) from the drop-down menu to apply to the app profile. You can also search for items to select.
- **Install Zscaler SSL Certificate**: If you’re using Zscaler Client Connector for Private Applications only, skip this option. Enable this option to allow Zscaler Client Connector to automatically [install the Zscaler SSL certificate](/unified/configuring-ssl-inspection-zscaler-client-connector) on users’ devices. If you [uploaded your organization’s custom certificate in the Admin Portal](/unified/uploading-custom-ssl-certificate-zscaler-client-connector), the app installs your organization’s custom certificate instead.
-
**Reconnect Tunnel on System Wakeup**: Allows Zscaler Client Connector to immediately restart Zscaler Tunnel (Z-Tunnel) 2.0 after a device wakes up from sleep. You can enable [reconnectT2OnWake](/unified/deploying-zscaler-client-connector-microsoft-intune-macos#reconnect-tunnel-2) functionality either via a Mobile Device Management (MDM) platform or through the App Profile.
Applies to Zscaler Client Connector versions 4.3.1.180 and 4.5.0.297 and later for macOS.
[]
-
**User Groups**: When a user enrolls Zscaler Client Connector with the Zscaler service, Zscaler Client Connector checks the group to which the user belongs and downloads the app profile with the appropriate rule.
- Click **Selected** to select user groups from the drop-down menu. The groups you've configured in the Admin Portal are displayed in this menu. There is no limit to the number of groups you can select.
- Click **All **to select all groups.
When new user groups are added, they are automatically selected. You can clear the checkbox to exclude them from your policy.
-
**Users**: Select this option to apply this rule to a specific user. The users you've configured in the Admin Portal are displayed in this menu after a user enrolls Zscaler Client Connector with the Zscaler service. Zscaler Client Connector checks if the user belongs and downloads the app profile with the appropriate rule. You can select up to 50 users. By default, no users are selected.
Don't select a user or a user group if you want to create and save a rule before applying it to a user or a user group.
- **Device Groups**: Select this option to apply this rule to specific groups or to all device groups. Click **Select All** to select all device groups or select individual groups from the drop-down menu. Device groups created in the Admin Portal are displayed in this menu. To learn more, see [Creating Device Groups](/unified/creating-device-groups).
[]
-
**PAC Configuration**:
- If you're using Zscaler Client Connector for Private Applications only, skip this option. Enter a valid PAC URL in the **Custom PAC URL** field if you want Zscaler Client Connector to forward all internet traffic to the Zscaler service and want to specify exceptions for certain types of traffic. The maximum number of characters is 512. If [Enforce Secure PAC URLs](/unified/enforcing-secure-pac-urls) is enabled, you must enter a URL with the https:// prefix (not http://).
- **Fallback to gateway domain**: When you select this checkbox, Zscaler Client Connector falls back to the gateway domain when PAC proxies cannot be reached for Z-Tunnel 1.0.
You must add a **Custom PAC URL** before you can use one of the following preferred ports.
- **Use Preferred Port from PAC for Z-Tunnel 1.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 1.0. This feature does not impact the default ports 80, 443, and 8080.
- **Use Preferred Port from PAC for Z-Tunnel 2.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 2.0. This feature does not impact the default ports 80, 443, and 8080.
If you want to allow a user to bypass the app when connecting to the VPN gateway, you can do so using the VPN Gateway Bypass option.
- **Proxy Configuration**: Select from the following options:
-
**V8 JavaScript based PAC Parser**: Enable Google’s open-source V8 engine to compile JavaScript for the PAC parser.
For Zscaler Client Connector version 4.3 and later for macOS, the legacy PAC parser option is not available. All users must use the **V8 JavaScript based PAC Parser** option.
- **Set Proxies on VPN Adapters**: When enabled, Zscaler Client Connector sets configured proxy settings on VPN adapters in addition to physical adapters.
- **Cache System Proxy**: Enable this option to save and restore proxy settings. This setting stores any existing system proxy settings when Zscaler Client Connector initiates. If a user exits or logs out of the app or if a user turns off Internet & SaaS from the app, proxy settings are restored to the system.
[]
[]
Configure traffic bypass for process-based applications and VPN gateways.
- **Process-Based Application Bypass**: When enabled, this option uses the Transparent Proxy System Extension to bypass applications defined via Application Bundle Identifier using the configuration profile in the mobile device management (MDM). To learn more, see [Deploying Zscaler Client Connector with JAMF Pro for macOS](/unified/deploying-zscaler-client-connector-jamf-pro-macos) and [Deploying Zscaler Client Connector with Microsoft Intune for macOS](/unified/deploying-zscaler-client-connector-microsoft-intune-macos).
-
**VPN Gateway Bypass**: You can allow traffic destined for the VPN to bypass Zscaler Client Connector. The app sets the routing table to exclude any traffic destined for the VPN gateway.
When a route-based driver is in use, the app creates IP-based exclude routes in the routing table.
When your users have a VPN client running on their devices in conjunction with Zscaler Client Connector, the VPN gateway bypass must be used in these scenarios:
- You selected Tunnel for the forwarding profile action of any trusted network type.
- Your VPN runs in split-tunnel mode so that it takes some, but not all, user traffic from the device.
- To allow traffic to bypass Zscaler Client Connector using **Tunnel **mode, enter any of the following for all of your VPN gateways:
-
An FQDN (e.g., `www.safemarch.com`)
If you add a fully qualified domain name (FQDN), the FQDN resolves and all resulting IP addresses are added to the bypass list at the start of the tunnel. However, if the FQDN resolves to a different IP address later, that address might not be bypassed. Zscaler recommends adding an IP or subnet where possible. Adding too many FQDNs can slow tunnel startup because Zscaler Client Connector resolves all these domains before starting tunneling.
- A specific IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. To ensure against connectivity issues, you must include all the VPN hostnames, IP addresses, or subnets to which the VPN connects. You can click the **Copy** icon to copy the items from the list.
-
To allow traffic to bypass Zscaler Client Connector using Tunnel with Local Proxy mode, Zscaler recommends adding the IP address or addresses and hostname of the VPN gateway to the system PAC file in the forwarding profile to enable direct connections for VPN traffic. To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
While you can also use this field to bypass non-VPN destinations, you must limit the number of items in this list because Zscaler Client Connector attempts to resolve all entries after a network change.
[]
For Z-Tunnel 2.0 only, you can configure traffic bypass for IP-based applications and add subnets for IPv4 and IPv6 inclusions and exclusions. You must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
To reset to the default configuration, click **Restore Default**. For both Destination Exclusions and Destination Inclusions, the default configuration includes all possible subnets (0.0.0.0/0) and excludes the RFC 1918 default private networks.
- **Predefined IP-Based Application Bypass**: To bypass Z-Tunnel 2.0, click **Select All** or select applications from the **IP-Based application bypass** drop-down menu. You can also search for items to select.
- **Custom IP-Based Application Bypass**: Select applications from the **IP-Based application bypass** drop-down menu to bypass Z-Tunnel 2.0. You can also search for items to select. To add applications to the IP-based application list, see [Adding IP-Based Applications to Bypass Traffic](/unified/adding-ip-based-applications-bypass-traffic).
-
**IPv4/IPv6 Inclusions and Exclusions**: To add specific subnets to send a specific subset of your traffic to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0, [complete the following steps.](#IPv-macOS)
[]
When adding subnets, the protocol value is *, TCP, or UDP. You can also enter the subnet `0.0.0.0/0`, which stands for all possible subnets. The maximum number of characters is 6,144. You can click the **Copy** icon to copy the items from the list.
- **IPv4 Inclusion**: Enter the specific subnets of the traffic you want to include for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp, 192.0.2.1:80`-`100:udp, `or` 192.0.2.1:80:*`)
- **IPv4 Exclusion**: Enter the specific subnets of the traffic you want to exclude for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp,` `192.0.2.1:80-100:udp, `or` 192.0.2.1:80:*`)
- **IPv6 Inclusion**: Enter the specific subnets of the traffic you want to include for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `[2001:0000::]`)
- A subnet (e.g., `[2001:0000::/32]`)
- An IP:Port range (e.g., `[2001:0000::]:80, [2001:0000::]:80-100, `or` [2001:0000::]:*`)
- An IP:Port:Protocol (e.g., `[2001:0000::]:80:tcp`)
- **IPv6 Exclusion**: Enter the specific subnets of the traffic you want to exclude for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `[2001:0000::]`)
- A subnet (e.g., `[2001:0000::/32]`)
- An IP:Port range (e.g., `[2001:0000::]:80,` `[2001:0000::]:80-100,` or` [2001:0000::]:*`)
- An IP:Port:Protocol (e.g., `[2001:0000::]:80:tcp`)
By default, the Zscaler service includes the RFC 1918 networks (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) in the exclusions list. To learn more, refer to [RFC 1918 Address Allocation for Private Internets](https://datatracker.ietf.org/doc/html/rfc1918). Zscaler also includes the multicast range 224.0.0.0/4. Zscaler recommends that you keep these networks in the list, unless explicitly needed, because deleting them causes private network traffic (e.g., DHCP) to be tunneled through the cloud.
[]
ZIA Disaster Recovery** **provides users access even when the Internet & SaaS service is down and is available only to enrolled users.
To configure ZIA Disaster Recovery:
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Send Traffic Direct**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Allow preselected destinations**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Use Custom Destinations URL** field.
- **Allow Zscaler Preselected Destinations (Recommended)**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**Allow Custom Destinations**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the Internet & SaaS service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
- When configuring the custom PAC file, ensure that you allow access to the Private Applications IP range `100.64.0.0/16` and Private Applications domains, `zpath.net` and `zpatwo.net`, to prevent blocking Private Applications traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Allow Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement apart from DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
If you have Internet & SaaS only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
ZPA Disaster Recovery provides users access to applications when the Private Applications service is down and is available only to enrolled users.
To configure ZPA Disaster Recovery:
- Select **Enable ZPA DR**.
- **DNS Settings:**
- **Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Activation Domain Name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users and/or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
-
You can add specific DNS domains to send all DNS requests to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0. Complete the following steps in the **Domain Inclusion** and **Domain Exclusion** fields:
You can enter specific domains (e.g., google.com) or enter * to include or exclude all DNS domains. Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. You can click the **Copy** icon to copy the items from the list.
- **Domain Inclusion**: Enter the DNS domains that Zscaler Client Connector should tunnel through Internet & SaaS. You can include a maximum of 65,535 characters.
- **Domain Exclusion**: Enter the DNS domains that Zscaler Client Connector should not tunnel through Internet & SaaS. You can exclude a maximum of 65,535 characters.
If you are using the same DNS domain in inclusions and exclusions, the longest domain name suffix is used.
Domain inclusions and exclusions take effect only if the DNS server IP address on the client belongs to RFC 1918 private subnet ranges that are by default excluded from Z-Tunnel 2.0.
- **DNS Server Route Exclusion**: When enabled, Zscaler Client Connector excludes DNS servers from the routing table.
- **DNS Priority Ordering for Trusted DNS Criteria: **Enable to have Zscaler Client Connector use the DNS servers corresponding to the DNS service name configured in DNS Priority Ordering for trusted network evaluation.
- **DNS Priority Ordering**: Add each DNS in the order you want Zscaler Client Connector to use them when **DNS Priority Ordering for Trusted DNS Criteria** is enabled. You can click the **Copy** icon to copy the items from the list.
- **Update DNS Search Order**: When enabled, Zscaler Client Connector prioritizes Zscaler’s DNS over Cisco’s DNS. The higher priority DNS gets the DNS traffic.
- **Bind Trusted Criteria DNS request to Default Adapter**: This option has Zscaler Client Connector connect the DNS request to the default adapter. By default, this option is enabled. Disabled means Zscaler Client Connector does not connect the Trusted Hostname IP resolution DNS request to the default adapter.
[]
- **Add Ifscope Route**: Enable this option to add the ifscope route corresponding to the default interface on the system.
- **Clear ARP Cache**: Enable this option to configure Zscaler Client Connector to clear the ARP cache when the service starts.
- **Tunnel Internal Client Connector Traffic**: Enable this option for Zscaler Client Connector to tunnel internal traffic (e.g., app updates and policy updates) through Zscaler. This option is only applicable if you deploy in a no-default route environment. If disabled, Zscaler Client Connector sends internal traffic directly.
When this option is enabled, Zscaler Client Connector does not tunnel PAC requests and continues to send PAC requests directly.
- **Route Table for Tunnel Connections**: Enable to have Zscaler Client Connector follow the routing table to connections for Internet & SaaS (i.e, Z-Tunnel 1.0, Z-Tunnel 2.0), Private Applications, and bypassed connections. If the setting remains disabled, it instead binds to the system's default interface.
- **Reactivate ZIA After**: Enter the number of minutes that must pass before Zscaler Client Connector reactivates Internet & SaaS after the user turns it off. To enable the reactivation period, enter any value from 1 to 1,440 minutes. To disable, enter 0 (zero). Zscaler Client Connector doesn't reactivate Internet & SaaS after the user turns it off.
- **Enable Transparent Proxy-based Traffic Interception**: When enabled, this setting uses a network extension to intercept network traffic.
[]
- **Install Endpoint DLP**: Enable **Install Endpoint DLP** to install Endpoint Data Loss Prevention (DLP) on a device. To learn more, see [About Endpoint Data Loss Prevention](/unified/about-endpoint-data-loss-prevention) and [Zscaler Endpoint Data Loss Prevention (DLP) Integration with Zscaler Client Connector.](/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector)
[]**Zscaler Firewall**: When enabled, the Zscaler firewall determines which network traffic is allowed and blocked. The default setting is disabled. To learn more, see [Blocking LAN Access](/unified/blocking-lan-access).
[]Configure the following optional passwords:
- **Logout Password**: Provide the password users must enter to log out of Zscaler Client Connector.
- **Disable Password ZIA**: Provide the password users must enter to disable the Internet & SaaS service.
- **Disable Password ZPA**: Provide the password users must enter to disable the Private Applications service.
- **Disable Password ZDX**: Provide the password users must enter to disable the Digital Experience Monitoring service.
- **Exit Password**: Provide the password users must enter to exit the app from the system tray without disabling Internet & SaaS.
- **Uninstall Password**: Provide the password users must enter to uninstall Zscaler Client Connector.
- **Password to Disable Endpoint DLP**: Enter a password to disable the [Endpoint Data Loss Prevention (DLP)](/unified/zscaler-endpoint-data-loss-prevention-dlp-integration-zscaler-client-connector) feature.
Click the **View **icon next to each password setting to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
[]
-
**Machine Token**: Select the machine token to which the rule applies from the drop-down menu. Machine tokens are configured in the Admin Portal.
In the Admin Portal, machine token is referred to as [Machine Provisioning Key](/unified/about-machine-provisioning-keys).
- **Force ZPA authentication to expire**: To trigger Private Applications authentication to expire, choose **Select All **or one or more of the following actions from the drop-down menu:
- **On System Sleep/Hibernate**
- **On System Restart**
- **On Network IP Change**
[]
- **Log Mode**: Zscaler Client Connector generates logs that users can send to a designated support admin in your organization, or to Zscaler Support (in encrypted form). To specify the scope of the logs, select one of the following log modes:
- **Default (Current: <log mode>)**: Displays the default global log mode [configured in Platform Settings](/unified/configuring-default-global-log-mode). You can override this setting, for the current profile only, by selecting a different option from the drop-down menu.
- **Error**: Zscaler Client Connector logs only when the app encounters an error and functionality is affected.
- **Warn**: Zscaler Client Connector logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Zscaler Client Connector logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Zscaler Client Connector logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Log File Size in MB**: If you are using Zscaler Client Connector for Private Applications only, skip this option. Enter a value between `50` and `1,000` to specify the maximum size of the log file. The default log file size is 100 MB per log type. When logs reach the maximum file size, the oldest logs are truncated from the file to keep the file size below the maximum.
- **Use Zscaler Notification Framework**: This option enables notifications from the [Zscaler Notification Framework](/unified/using-zscaler-notification-framework) instead of from the macOS-based notification system.
[]Enable **Command Line Interface** to allow admins to[ interact with Zscaler Client Connector via a CLI](/unified/interacting-zscaler-client-connector-remotely). Applies to Zscaler Client Connector version 4.3 and later for macOS. For **Disable Services,** click **Disable ZPA Password** to require a password when disabling the Private Applications service via CLI. Click **Generate Password** to generate a password to disable the Private Applications service in the CLI. Click **Copy **to copy the generated password. Passwords expire after two hours.
[]This feature is available only for Zscaler Client Connector version 4.5.1 and later for macOS. Contact Zscaler Support to enable this feature.
- **Zscaler Client Connector Telemetry**: Enable to collect metrics including device events, statistics, profile, statistics for Zscaler Client Connector processes, and the top 5 processes. These metrics do not include personally identifiable information (PII). The default value is enabled.
[]
- **Send Disable Service Reason**: This option allows users to send a description about why a Zscaler service (e.g., Internet & SaaS, Private Applications, Digital Experience Monitoring) was disabled on a device. By default, this option is disabled. This information is accessible when viewing [device details](/unified/viewing-device-fingerprint-enrolled-device).
- **Enable Zscaler Client Connector Revert**: When enabled, users have the option to [revert to the previous Zscaler Client Connector version](/unified/reverting-zscaler-client-connector-previous-version). Applies to Zscaler Client Connector version 3.9 and later for Windows. In the **Revert Password** field, provide the password users must enter to revert to the previous Zscaler Client Connector version.
[]
**Policy Description**: Enter any notes regarding the policy.
[]
To add a new Linux policy rule:
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **Linux** and click **Add Linux Policy**. The **Add Linux Policy **window appears.
-
In the **Add Linux Policy **window, you can configure the following settings:
To find an option, you can enter search words in the **Search** field and press `Enter`. A navigation path to the option appears in the search results.
- [General](#gen)
- [Groups](#grps)
- [Traffic Steering](#steering)
- [Passwords](#passwords)
- [Notification and Logging](#lin-notification-logging)
- [Advanced](#lin-adv)
- [Policy](#lin-policy)
[]
- [PAC and Proxy](#pacproxy)
- [App and IP Bypass](#appbypass)
- [Disaster Recovery](#lin-DR)
- [DNS](#lin-DNS)
- [Advanced](#lin-advanced)
[]
- [Global Bypasses](#lin-global)
- [IP Bypasses](#lin-IP)
[]
- [ZIA Disaster Recovery](#ZIA-DR)
- [ZPA Disaster Recovery](#ZPA-DR)
[]
- **Name**: Enter a unique alphanumeric name for your policy rule.
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order reflects the order of precedence among configured profile policy rules and helps determine which rule the app downloads for a user upon enrollment. Precedence is based on ascending numerical order.
- **Status**: Select **Disabled** to inactivate the rule or select **Enabled **to activate the rule. If you don’t enable the rule, the policy rule is not enforced.
-
**Forwarding Profile**: Select a forwarding profile of your configured forwarding profiles from the drop-down menu. You can also search for items to select. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
If you're using Zscaler Tunnel (Z-Tunnel) 2.0, you must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- **Install Zscaler SSL Certificate**: If you’re using Zscaler Client Connector for Internet & SaaS only, skip this option. Enable this option to allow Zscaler Client Connector to automatically [install the Zscaler SSL certificate](/unified/configuring-ssl-inspection-zscaler-client-connector) on users’ devices. If you [uploaded your organization’s custom certificate in the Admin Portal](/unified/uploading-custom-ssl-certificate-zscaler-client-connector), the app installs your organization’s custom certificate instead.
[]
-
**User Groups**: When a user enrolls Zscaler Client Connector with the Zscaler service, Zscaler Client Connector checks the group to which the user belongs and downloads the app profile with the appropriate rule.
- Click **Selected** to select user groups from the drop-down menu.
- Click **All **to select all groups.
When new user groups are added, they are automatically selected. You can clear the checkbox to exclude them from your policy.
- **Users**: Select this option to apply this rule to a specific user. The users you've configured in the Admin Portal are displayed in this menu after a user enrolls the app with the service. Zscaler Client Connector checks if the user belongs and downloads the app profile with the appropriate rule. You can select up to 50 users. By default, no users are selected.
Don't select a user if you want to create and save a rule before applying it to a user.
[]
**PAC Configuration**: If you're using Zscaler Client Connector for Private Applications only, skip this option. Enter a valid PAC URL in the **Custom PAC URL** field if you want Zscaler Client Connector to forward all internet traffic to the Zscaler service and want to specify exceptions for certain types of traffic. The maximum number of characters is 512. If [Enforce Secure PAC URLs](/unified/enforcing-secure-pac-urls) is enabled, you must enter a URL with the https:// prefix (not http://).
If you want to allow a user to bypass the app when connecting to the VPN gateway, use the VPN Gateway Bypass option.
[]
[]
Configure traffic bypass for VPN gateways and source ports:
-
**VPN Gateway Bypass**: You can allow traffic destined for the VPN to bypass Zscaler Client Connector. The app sets the routing table to exclude any traffic destined for the VPN gateway.
When a route-based driver is in use, the app creates IP-based exclude routes in the routing table.
When your users have a VPN client running on their devices in conjunction with Zscaler Client Connector, the VPN gateway bypass must be used in these scenarios:
- You selected Tunnel for the forwarding profile action of any trusted network type.
- Your VPN runs in split-tunnel mode so that it takes some, but not all, user traffic from the device.
To allow traffic to bypass Zscaler Client Connector using **Tunnel **mode, enter any of the following for all of your VPN gateways:
-
An FQDN (e.g., `www.safemarch.com`)
If you add a fully qualified domain name (FQDN), the FQDN resolves and all resulting IP addresses are added to the bypass list at the start of the tunnel. However, if the FQDN resolves to a different IP address later, that address might not be bypassed. Zscaler recommends adding an IP or subnet where possible. Adding too many FQDNs can slow tunnel startup because Zscaler Client Connector resolves all these domains before starting tunneling.
- A specific IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. To ensure against connectivity issues, you must include all the VPN hostnames, IP addresses, or subnets to which the VPN connects. You can click the **Copy** icon to copy the items from the list.
To allow traffic to bypass Zscaler Client Connector using Tunnel with Local Proxy mode, Zscaler recommends adding the IP address or addresses and hostname of the VPN gateway to the system PAC file in the forwarding profile to enable direct connections for VPN traffic. To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
While you can also use this field to bypass non-VPN destinations, you must limit the number of items in this list because Zscaler Client Connector attempts to resolve all entries after a network change.
- **Source Port-Based Bypasses**: Enter the source port and protocol from which Zscaler Client Connector bypasses existing inbound traffic. The port value can range from 1 to 65,535. The protocol value is TCP, UDP, or *. You can click the **Copy** icon to copy the items from the list.
[]
For Z-Tunnel 2.0 only, you can configure traffic bypass for IP-based applications and add subnets for IPv4 inclusions and exclusions. You must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
To reset to the default configuration, click **Restore Default**. For both Destination Exclusions and Destination Inclusions, the default configuration includes all possible subnets (0.0.0.0/0) and excludes the RFC 1918 default private networks.
- **Predefined IP-Based Application Bypass**: To bypass Z-Tunnel 2.0, click **Select All** or select applications from the **IP-Based application bypass** drop-down menu. You can also search for items to select.
-
**IPv4 Inclusions and Exclusions**:** **To send a specific subset of your traffic to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0, [complete the following steps.](#IPv-lin)
[]
When adding subnets, the protocol value is *, TCP, or UDP. You can also enter the subnet `0.0.0.0/0`, which stands for all possible subnets. The maximum number of characters is 6,144. You can click the **Copy** icon to copy the items from the list.
- **IPv4 Inclusion**: Enter the specific subnets of the traffic you want to include for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp, 192.0.2.1:80`-`100:udp, `or` 192.0.2.1:80:*`)
- **IPv4 Exclusion**: Enter the specific subnets of the traffic you want to exclude for Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp,` `192.0.2.1:80-100:udp, `or` 192.0.2.1:80:*`)
By default, the Zscaler service includes the RFC 1918 networks (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) in the exclusions list. To learn more, refer to [RFC 1918 Address Allocation for Private Internets](https://datatracker.ietf.org/doc/html/rfc1918). Zscaler also includes the multicast range 224.0.0.0/4. Zscaler recommends that you keep these networks in the list, unless explicitly needed, because deleting them causes private network traffic (e.g., DHCP) to be tunneled through the cloud.
[]
[]
ZIA Disaster Recovery** **provides users access even when the Internet & SaaS service is down and is available only to enrolled users. To configure ZIA Disaster Recovery:
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Send Traffic Direct**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Allow preselected destinations**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Use Custom Destinations URL** field.
- **Allow Zscaler Preselected Destinations (Recommended)**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**Allow Custom Destinations**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the Internet & SaaS service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
- When configuring the custom PAC file, ensure that you allow access to the Private Applications IP range `100.64.0.0/16` and Private Applications domains, `zpath.net` and `zpatwo.net`, to prevent blocking Private Applications traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Allow Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement apart from DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
If you have Internet & SaaS only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
ZPA Disaster Recovery provides users access to applications when the Private Applications service is down and is available only to enrolled users. To configure ZPA Disaster Recovery:
- Select **Enable ZPA DR**.
- **DNS Settings:**
- **Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **ZPA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users and/or groups for the app profile are part of a group to test Disaster Recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
-
To add specific subnets to send a specific subset of your traffic to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0, complete the following steps in the **Domain Inclusion** and **Domain Exclusion** fields:
You can enter specific domains (e.g., `google.com`) or enter * to include or exclude all DNS domains. Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. You can click the **Copy** icon to copy the items from the list.
- **Domain Inclusion**: Enter the DNS domains that Zscaler Client Connector should tunnel through Internet & SaaS. You can include a maximum of 65,535 characters.
- **Domain Exclusion**: Enter the DNS domains that Zscaler Client Connector should not tunnel through Internet & SaaS. You can exclude a maximum of 65,535 characters.
If you are using the same DNS domain in inclusions and exclusions, the longest domain name suffix is used.
Domain inclusions and exclusions take effect only if the DNS server IP address on the client belongs to RFC 1918 private subnet ranges that are by default excluded from Z-Tunnel 2.0.
- **Bind Trusted Criteria DNS request to Default Adapter**: This option has Zscaler Client Connector connect the DNS request to the default adapter. By default, this option is enabled. Disabled means Zscaler Client Connector does not connect the Trusted Hostname IP resolution DNS request to the default adapter.
[]
- **Tunnel Internal Client Connector Traffic**: Enable this option for Zscaler Client Connector to tunnel internal traffic (e.g., app updates and policy updates) through Zscaler. This option is only applicable if you deploy in a no-default route environment. If disabled, Zscaler Client Connector sends internal traffic directly.
- **Reactivate ZIA After**: Enter the number of minutes that must pass before Zscaler Client Connector reactivates Internet & SaaS after the user turns it off. To enable the reactivation period, enter any value from `1` to `1440` minutes. To disable, enter 0 (zero). Zscaler Client Connector doesn't reactivate Internet & SaaS after the user turns it off.
[]Configure the following optional passwords:
- **Logout Password**: Provide the password users must enter to log out of or uninstall Zscaler Client Connector.
- **Disable Password ZIA**: Provide a password users must enter to disable the Internet & SaaS service.
- **Disable Password ZPA**: Provide a password users must enter to disable the Private Applications service.
- **Exit Password**: Provide a password users must enter to exit the app from the system tray without disabling Internet & SaaS.
Click the **View **icon next to each password setting to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
[]
- **Log Mode**: Zscaler Client Connector generates logs that users can send to a designated support admin in your organization, or to Zscaler Support (in encrypted form). To specify the scope of the logs, select one of the following log modes:
- **Default (Current: <log mode>)**: Displays the default global log mode [configured in Platform Settings](/unified/configuring-default-global-log-mode). You can override this setting, for the current profile only, by selecting a different option from the drop-down menu.
- **Error**: Zscaler Client Connector logs only when the app encounters an error and functionality is affected.
- **Warn**: Zscaler Client Connector logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Zscaler Client Connector logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Zscaler Client Connector logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Log File Size in MB**: If you are using Zscaler Client Connector for Private Applications only, skip this option. Enter a value between `50` and `1,000` to specify the maximum size of the log file. The default log file size is 100 MB per log type. When logs reach the maximum file size, the oldest logs are truncated from the file to keep the file size below the maximum.
[]
**Send Disable Service Reason**: This option allows users to send a description about why a Zscaler service (e.g., Internet & SaaS, Private Applications, Digital Experience Monitoring) was disabled on a device. By default, this option is disabled. This information is accessible when viewing [device details](/unified/viewing-device-fingerprint-enrolled-device).
[]
**Policy Description**: (Optional) Enter any notes regarding the policy.
[]To add a new iOS policy rule:
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **iOS** and click **Add iOS Policy**. The **Add iOS Policy** window appears.
-
In the **Add iOS Policy **window, you can configure the following settings:
To find an option, you can enter search words in the **Search** field and press `Enter`. A navigation path to the option appears in the search results.
- [General](#iOS-general)
- [Groups](#iOS-groups)
- [Traffic Steering](#iOS-traffic)
- [Passwords](#iOS-otp)
- [Notification and Logging](#iOS-notification)
- [Advanced](#iOS-adv)
- [Policy](#iOS-policy)
[]
- [PAC and Proxy](#iOS-pac-proxy)
- [App and IP Bypass](#iOS-app-bypass)
- [Disaster Recovery](#iOS-disaster-recovery)
- [DNS](#iOS-DNS)
- [Advanced](#iOS-advanced)
[]
[]
- **Name**: Enter a unique alphanumeric name for your policy rule.
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order reflects the order of precedence among configured profile policy rules and helps determine which rule the app downloads for a user upon enrollment. Precedence is based on ascending numerical order.
- **Status**: Select **Disabled** to inactivate the rule or select **Enabled **to activate the rule. If you don’t enable the rule, the policy rule is not enforced.
-
**Forwarding Profile**: Select a forwarding profile from your configured forwarding profiles from the drop-down menu. You can also search for items to select. The supported forwarding profile modes for iOS are Tunnel and None. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
Zscaler does not support Z-Tunnel 2.0 on iOS at this time.
- **ZIA Posture Profile**: Select a [posture profile](/unified/about-internet-saas-posture-profiles) from the drop-down menu to apply to the app profile. You can also search for items to select.
[]
-
**User Groups**: When a user enrolls Zscaler Client Connector with the Zscaler service, Zscaler Client Connector checks the group to which the user belongs and downloads the app profile with the appropriate rule.
- Click **Selected** to select user groups from the drop-down menu. The groups you've configured in the Admin Portal are displayed in this menu. There is no limit to the number of groups you can select.
- Click **All **to select all groups.
When new user groups are added, they are automatically selected. You can clear the checkbox to exclude them from your policy.
-
**Users**: Select this option to apply this rule to a specific user. The users you've configured in the Admin Portal are displayed in this menu after a user enrolls Zscaler Client Connector with the Zscaler service. Zscaler Client Connector checks if the user belongs and downloads the app profile with the appropriate rule. You can select up to 50 users. By default, no users are selected.
Don't select a user or a user group if you want to create and save a rule before applying it to a user or a user group.
[]
- **PAC Configuration**: If you're using Zscaler Client Connector for Private Applications only, skip this option. Enter a valid PAC URL in the **Custom PAC URL** field if you want [Zscaler Client Connector to forward all internet traffic](/client-connector/what-is-zscaler-client-connector) to the Zscaler service and want to specify exceptions for certain types of traffic. The maximum number of characters is 512. If [Enforce Secure PAC URLs](/unified/enforcing-secure-pac-urls) is enabled, you must enter a URL with the https:// prefix (not http://).
- **Use Preferred Port from PAC for Z-Tunnel 1.0**: If is enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 1.0. This feature does not impact the default ports 80, 443, and 8080. You must add a **Custom PAC URL** before you can use the preferred port.
- **Use Preferred Port from PAC for Z-Tunnel 2.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 2.0. This feature does not impact the default ports 80 and 443.
If you want to allow a user to bypass the app when connecting to the VPN gateway, use the VPN Gateway Bypass option.
[]
**Global Bypasses**: Use** VPN Gateway Bypass** to allow traffic destined for the VPN to bypass Zscaler Client Connector. The app sets the routing table to exclude any traffic destined for the VPN gateway.
When a route-based driver is in use, the app creates IP-based exclude routes in the routing table.
When your users have a VPN client running on their devices in conjunction with Zscaler Client Connector, the VPN gateway bypass must be used in these scenarios:
- You've selected [Tunnel for the forwarding profile action](/unified/configuring-forwarding-profiles-zscaler-client-connector) of any trusted network type.
- Your VPN runs in split-tunnel mode so that it takes some, but not all, user traffic from the device.
To allow traffic to bypass Zscaler Client Connector using Tunnel mode, enter any of the following for all of your VPN gateways:
-
An FQDN (e.g., `www.safemarch.com`)
If you add a fully qualified domain name (FQDN), the FQDN resolves and all resulting IP addresses are added to the bypass list at the start of the tunnel. However, if the FQDN resolves to a different IP address later, that address might not be bypassed. Zscaler recommends adding an IP or subnet where possible. Adding too many FQDNs can slow tunnel startup because Zscaler Client Connector resolves all these domains before starting tunneling.
- A specific IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `ENTER` when finished. To ensure against connectivity issues, you must include all the VPN hostnames, IP addresses, or subnets to which the VPN connects. You can click the **Copy** icon to copy the items from the list.
To allow traffic to bypass Zscaler Client Connector using Tunnel with Local Proxy mode, Zscaler recommends adding the IP address or addresses and hostname of the VPN gateway to the system PAC file in the forwarding profile to enable direct connections for VPN traffic. To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
While you can also use this field to bypass non-VPN destinations, you must limit the number of items in this list because Zscaler Client Connector attempts to resolve all entries after a network change.
[]
- [ZIA Disaster Recovery](#iOS-ZIA)
- [ZPA Disaster Recovery](#iOS-ZPA)
[]
ZIA Disaster Recovery** **provides users access even when the Internet & SaaS service is down and is available only to enrolled users.
To configure ZIA Disaster Recovery:
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Send Traffic Direct**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Allow preselected destinations**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Use Custom Destinations URL** field.
- **Allow Zscaler Preselected Destinations (Recommended)**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**Allow Custom Destinations**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the ZIA service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
- When configuring the custom PAC file, ensure that you allow access to the ZPA IP range `100.64.0.0/16` and ZPA domains, `zpath.net` and `zpatwo.net`, to prevent blocking ZPA traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Allow Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
}
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement other than DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
If you have ZIA only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload .pem files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
ZPA Disaster Recovery provides users access to applications when the Private Applications service is down and is available only to enrolled users.
To configure ZPA Disaster Recovery:
- Select **Enable ZPA DR**.
- **DNS Settings:**
- **Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Activation Domain Name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users and/or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
-
You can add specific DNS domains to send all DNS requests to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0. Complete the following steps in the **Domain Inclusion** and **Domain Exclusion** fields:
You can enter specific domains (e.g., `google.com`) or enter * to include or exclude all DNS domains. Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. You can click the **Copy** icon to copy the items from the list.
- **Domain Inclusion**: Enter the DNS domains that Zscaler Client Connector should tunnel through Internet & SaaS. You can include a maximum of 65,535 characters.
- **Domain Exclusion**: Enter the DNS domains that Zscaler Client Connector should not tunnel through Internet & SaaS. You can exclude a maximum of 65,535 characters.
If you are using the same DNS domain in inclusions and exclusions, the longest domain name suffix is used.
Domain inclusions and exclusions take effect only if the DNS server IP address on the client belongs to RFC 1918 private subnet ranges that are by default excluded from Z-Tunnel 2.0.
[]
- **IPV6 Modes**: Zscaler Client Connector handles IPv6 traffic based on the configuration mode set here.
- **IPv6Cleanout**: If selected, Zscaler Client Connector does not apply any IPv6 settings.
- **IPv6BlockInDualStack**: If selected, Zscaler Client Connector blocks IPv6 traffic only in a dual stack network.
- **IPv6Block**: If selected, Zscaler Client Connector blocks IPv6 traffic irrespective of the network type.
- **IPv6NAT64Only**: If selected, Zscaler Client Connector handles IPv6 traffic through NAT64 translation.
- **IPv6Native**: If selected, Zscaler Client Connector handles IPv6 traffic natively.
- **Tunnel Internal Client Connector Traffic**: Enable this option for Zscaler Client Connector to tunnel internal traffic (e.g., app updates and policy updates) through Zscaler. This option is only applicable if you deploy in a no-default route environment. If disabled, Zscaler Client Connector sends internal traffic directly.
When this option is enabled, Zscaler Client Connector does not tunnel PAC requests and continues to send PAC requests directly.
- **Drop QUIC Traffic**: This option is for websites that use QUIC (UDP 443), which is not supported by Z-Tunnel 1.0. When enabled, Z-Tunnel 1.0 drops QUIC packets so the application can fall back to TCP 443.
- **Route Table for Tunnel Connections**: Enable to have Zscaler Client Connector follow the routing table to connections for Internet & SaaS (i.e, Z-Tunnel 1.0), Private Applications, and bypassed connections. If the setting remains disabled, it instead binds to the system's default interface.
- **Reactivate ZIA After**: Enter the number of minutes that must pass before Zscaler Client Connector reactivates Internet & SaaS after the user turns it off. To enable the reactivation period, enter any value from `1` to `1440` minutes. To disable, enter `0` (zero). Zscaler Client Connector doesn't reactivate Internet & SaaS after the user turns it off.
- **Use Tunnel SDK Version 4.3**: When enabled, Zscaler Client Connector switches Tunnel SDK Version from 3.8 to 4.3.
[]Configure the following optional passwords:
- **Logout Password**: Provide the password users must enter to log out of Zscaler Client Connector.
- **Disable Password ZIA**: Provide the password users must enter to disable the Internet & SaaS service.
- **Disable Password ZPA**: Provide the password users must enter to disable the Private Applications service.
- **Profile Passcode**: Provide the password users must enter to connect to the VPN.
Click the **View **icon next to each password setting to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
[]
- **Log Mode**: Zscaler Client Connector generates logs that users can send to a designated support admin in your organization, or to Zscaler Support (in encrypted form). To specify the scope of the logs, select one of the following log modes:
- **Default (Current: <log mode>)**: Displays the default global log mode [configured in Platform Settings](/unified/configuring-default-global-log-mode). You can override this setting, for the current profile only, by selecting a different option from the drop-down menu.
- **Error**: Zscaler Client Connector logs only when the app encounters an error and functionality is affected.
- **Warn**: Zscaler Client Connector logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Zscaler Client Connector logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Zscaler Client Connector logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Log File Size in MB**: If you are using Zscaler Client Connector for Private Applications only, skip this option. Enter a value between 50 and 1000 to specify the maximum size of the log file. The default log file size is 100 MB per log type. When logs reach the maximum file size, the oldest logs are truncated from the file to keep the file size below the maximum.
- **Show per-app VPN Tunnel Notification**: When enabled, Zscaler Client Connector notifies the end user that per-app VPN tunnel establishment is in progress.
[]
**Send Disable Service Reason**: This option allows users to send a description about why a Zscaler service (e.g., Internet & SaaS, Private Applications, Digital Experience Monitoring) was disabled on a device. By default, this option is disabled. This information is accessible when viewing [device details](/unified/viewing-device-fingerprint-enrolled-device).
[]
**Policy Description**: Enter any notes regarding the policy.
[]To add a new Android policy rule:
- Go to **Infrastructure > Connectors > Client**.
- Under Platform Settings, select **Android** and click **Add Android Policy**. The **Add Android Policy** window appears.
-
In the **Add Android Policy **window, you can configure the following settings:
To find an option, you can enter search words in the **Search** field and press `Enter`. A navigation path to the option appears in the search results.
- [General](#android-general)
- [Groups](#android-groups)
- [Traffic Steering](#android-traffic)
- [Passwords](#android-otp)
- [Notification and Logging](#android-notification)
- [Configure Cellular Quota Enforcement Settings](#android-cellular)
- [Advanced](#android-adv)
- [Policy](#android-policy)
[]
- [PAC and Proxy](#android-pac-proxy)
- [App and IP Bypass](#android-app-bypass)
- [Disaster Recovery](#android-DR)
- [DNS](#Android-DNS)
- [Advanced](#android-advanced)
[]
- [Global Bypasses](#andr-global)
- [IP Bypasses](#andr-IP)
[]
- **Bypass Traffic for Specific Application**: Enter the identifier of any Android application to configure a bypass for it. You can find the identifier after the `id` parameter in the URL of the app’s Google Play details page. For example, Zscaler Client Connector’s identifier is `zscaler.com.zscaler`. You can click the **Copy** icon to copy the items from the list.
- **Bypass Traffic for MMS Applications**: Enable this option for Zscaler Client Connector to automatically bypass standard messaging applications on Android. The bypassed messaging apps include WhatsApp and the Android Messages app.
-
**VPN Gateway Bypass**: You can allow traffic destined for the VPN to bypass Zscaler Client Connector. The app sets the routing table to exclude any traffic destined for the VPN gateway.
When a route-based driver is in use, the app creates IP-based exclude routes in the routing table.
When your users have a VPN client running on their devices in conjunction with Zscaler Client Connector, the VPN gateway bypass must be used in these scenarios:
- You selected **Tunnel** for the forwarding profile action of any trusted network type.
- Your VPN runs in Split-Tunnel mode so that it takes some, but not all, user traffic from the device.
To allow traffic to bypass Zscaler Client Connector using Tunnel mode, enter any of the following for all of your VPN gateways:
-
An FQDN (e.g., `www.safemarch.com`)
If you add a fully qualified domain name (FQDN), the FQDN resolves and all resulting IP addresses are added to the bypass list at the start of the tunnel. However, if the FQDN resolves to a different IP address later, that address might not be bypassed. Zscaler recommends adding an IP address or subnet where possible. Adding too many FQDNs can slow tunnel startup because Zscaler Client Connector resolves all these domains before starting tunneling.
- A specific IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter `when finished. To ensure against connectivity issues, you must include all the VPN hostnames, IP addresses, or subnets to which the VPN connects. You can click the **Copy** icon to copy the items from the list.
To allow traffic to bypass Zscaler Client Connector using Tunnel with Local Proxy mode, Zscaler recommends adding the IP address or addresses and hostname of the VPN gateway to the system PAC file in the forwarding profile to enable direct connections for VPN traffic. To learn more, see [Best Practices for Using PAC Files with Zscaler Client Connector](/unified/best-practices-using-pac-files-zscaler-client-connector).
While you can also use this field to bypass non-VPN destinations, you must limit the number of items in this list because Zscaler Client Connector attempts to resolve all entries after a network change.
- **Upload File**: Allows you to upload a VPN gateway bypass list. The format is a text file with values separated by new lines or commas. Subsequent uploads with similar data in the list will not duplicate existing entries, but will add only the new entries.
[]
If you use Z-Tunnel 2.0, you can configure traffic bypasses for IP-based applications and include or exclude traffic based on IPv4 subnets, IP addresses, ports, and protocols. You must choose a forwarding profile with Z-Tunnel 2.0 selected. To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- **Predefined IP-Based Application Bypass**: Click **Select All** or select applications from the **IP-Based application bypass** drop-down menu. You can also search for items to select.
- **Custom IP-Based Application Bypass**: Select applications from the **IP-Based application bypass** drop-down menu. You can also search for items to select. To add applications to the IP-based application list, see [Adding IP-Based Applications to Bypass Traffic](/unified/adding-ip-based-applications-bypass-traffic).
-
**IPv4 Inclusions and Exclusions**: To send or bypass a specific subset of your traffic to or from the Internet & SaaS Service Edge through Z-Tunnel 2.0, [complete the following steps.](#IPv-android)
[]
When adding subnets, the protocol value is *, TCP, or UDP. You can also enter the subnet `0.0.0.0/0`, which stands for all possible subnets. The maximum number of characters in each field is 6,144. If you enter overlapping values in the inclusion and exclusion lists, the longest match takes precedence (e.g., if `192.0.2.0/24` is in **IPv4 Inclusion** and `192.0.2.0/24:*:tcp` is in **IPv4 Exclusion**, any TCP requests to the `192.0.2.0/24` subnet bypass Z-Tunnel 2.0. You can click the **Copy** icon to copy the items from the list.
-
**IPv4 Inclusion**: Enter the specific subnets of the traffic you want to include in Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp, 192.0.2.1:80`-`100:udp, `or` 192.0.2.1:80:*`)
The default configuration includes all possible subnets (`0.0.0.0/0`).
-
**IPv4 Exclusion**: Enter the specific subnets of the traffic you want to exclude from Z-Tunnel 2.0 in the following formats:
- An IP address (e.g., `192.0.2.1`)
- A subnet (e.g., `192.0.2.0/24`)
- An IP:Port range (e.g., `192.0.2.1:80, 192.0.2.1:80-100, `or `192.0.2.1:*`)
- An IP:Port:Protocol (e.g., `192.0.2.1:80:tcp,` `192.0.2.1:80-100:udp, `or` 192.0.2.1:80:*`)
The default configuration includes the` 224.0.0.0/4` multicast range, the `169.254.0.0/16` link-local range, the `255.255.255.255` broadcast address, and the RFC 1918 default private networks (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`). To learn more, refer to [RFC 1918 Address Allocation for Private Internets](https://datatracker.ietf.org/doc/html/rfc1918).
Zscaler recommends that you keep these networks in the list, unless explicitly needed, because deleting them causes private network traffic (e.g., DHCP) to be tunneled through the cloud. To reset to the default configuration, click **Restore Default**.
[]
- [ZIA Disaster Recovery](#android-ZIA)
- [ZPA Disaster Recovery](#android-ZPA)
[]
- **Name**: Enter a unique alphanumeric name for your policy rule.
- **Rule Order**: Select the appropriate rule order value from the drop-down menu. The rule order reflects the order of precedence among configured profile policy rules and helps determine which rule the app downloads for a user upon enrollment. Precedence is based on ascending numerical order.
- **Status**: Select **Disabled** to inactivate the rule or select **Enabled **to activate the rule. If you don’t enable the rule, the policy rule is not enforced.
-
**Forwarding Profile**: Select a forwarding profile from your configured forwarding profiles from the drop-down menu. You can also search for items to select. The supported forwarding profile modes for Android are Tunnel and None. To learn more, see [Configuring Forwarding Profiles for Zscaler Client Connector](/unified/configuring-forwarding-profiles-zscaler-client-connector).
Zscaler does not support Z-Tunnel 2.0 on Android at this time.
- **ZIA Posture Profile**: Select a posture profile from the drop-down menu to apply to the app profile. You can also search for items to select.
- **Install Zscaler SSL Certificate**: If you’re using Zscaler Client Connector for Private Applications only, skip this option. Enable this option to allow Zscaler Client Connector to automatically [install the Zscaler SSL certificate](/unified/configuring-ssl-inspection-zscaler-client-connector) on users’ devices. If you [uploaded your organization’s custom certificate in the Admin Portal](/unified/uploading-custom-ssl-certificate-zscaler-client-connector), the app installs your organization’s custom certificate instead.
[]
-
**User Groups**: When a user enrolls Zscaler Client Connector with the Zscaler service, Zscaler Client Connector checks the group to which the user belongs and downloads the app profile with the appropriate rule.
- Click **Selected** to select user groups from the drop-down menu. The groups you've configured in the Admin Portal are displayed in this menu. There is no limit to the number of groups you can select.
- Click **All **to select all groups.
When new user groups are added, they are automatically selected. You can clear the checkbox to exclude them from your policy.
-
**Users**: Select this option to apply this rule to a specific user. The users you've configured in the Admin Portal are displayed in this menu after a user enrolls Zscaler Client Connector with the Zscaler service. Zscaler Client Connector checks if the user belongs and downloads the app profile with the appropriate rule. You can select up to 50 users. By default, no users are selected.
Don't select a user if you want to create and save a rule before applying it to a user.
-
**Device Groups**: Select this option to apply this rule to specific groups or to all device groups. Click **Select All** to select all device groups or select individual groups from the drop-down menu. Device groups created in the Admin Portal are displayed in this menu. To learn more, see [Creating Device Groups](/unified/creating-device-groups).
Device groups are available only on Zscaler Client Connector version 3.7 and later for Android devices.
[]
- **PAC Configuration**: If you're using Zscaler Client Connector for Private Applications only, skip this option.
- **Custom PAC URL**: Enter a valid PAC URL in the **Custom PAC URL** field if you want Zscaler Client Connector to forward all internet traffic to the Zscaler service and want to specify exceptions for certain types of traffic. The maximum number of characters is 512. If [Enforce Secure PAC URLs](/unified/enforcing-secure-pac-urls) is enabled, you must enter a URL with the https:// prefix (not http://).
- **Fallback to gateway domain**: If you select this checkbox, Zscaler Client Connector falls back to the gateway domain when PAC proxies cannot be reached for Z-Tunnel 1.0.
- If you added a **Custom PAC URL**, select a preferred port:
- **Use Preferred Port from PAC for Z-Tunnel 1.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 1.0. This feature does not impact the default ports 80 and 443.
- **Use Preferred Port from PAC for Z-Tunnel 2.0**: If enabled, Zscaler Client Connector uses the custom port from the PAC file for Z-Tunnel 2.0. This feature does not impact the default ports 80 and 443.
If you want to allow a user to bypass the app when connecting to the VPN gateway, use the VPN Gateway Bypass option.
[]
ZIA Disaster Recovery** **provides users access even when the Internet & SaaS service is down and is available only to enrolled users. To configure ZIA Disaster Recovery:
- Select **Enable ZIA DR**.
- Select from the following traffic forwarding actions in the drop-down menu:
- **Send Traffic Direct**: Traffic bypasses Zscaler Client Connector, giving the user access to all applications through direct internet access.
- **Disable Internet Access**: All traffic is dropped at the endpoint and users do not have access to the internet.
- **Allow preselected destinations**: You can either block or allow access to specific URLs using a custom PAC file. Insert the custom PAC file URL in the **Use Custom Destinations URL** field.
- **Allow Zscaler Preselected Destinations (Recommended)**: When enabled, users can access only the URLs that are present in the [Zscaler-provided global database allowlist](https://dll7xpq8c5ev0.cloudfront.net/drdb.txt). The rest of the URLs are blocked.
-
**Allow Custom Destinations**: Select this option to insert a custom PAC file URL in the **Custom Destinations** field. You can configure a custom PAC URL (with the http:// or https:// prefix) that users can access when the Internet & SaaS service is down. When configured in conjunction with the global database URL, both URL lists are allowed. The custom destinations URL takes precedence when there are any conflicts. You can also forward the traffic to a proxy server.
- When configuring the custom PAC file, ensure that you allow access to the Private Applications IP range `100.64.0.0/16` and Private Applications domains, `zpath.net` and `zpatwo.net`, to prevent blocking Private Applications traffic.
- If you have enabled both the **Allow Zscaler Preselected Destinations** and **Allow Custom Destinations** fields, ensure that you remove the `return drop;` syntax from the custom PAC file statement because it blocks the URLs listed in the Zscaler-provided global database allowlist.
Use the following sample custom PAC file:
function FindProxyForURL(url, host) {
var drop = "BLOCK";
/* Return DIRECT to Allow access */
if ((localHostOrDomainIs(host, "google.com")) ||
(localHostOrDomainIs(host, "salesforce.com")) ||
(localHostOrDomainIs(host, "microsoft.com")) ||
(localHostOrDomainIs(host, "zscaler.com")) )
return "DIRECT";
/* Default Block Statement to block anything not allowed above */
return drop;
- Return DIRECT to allow destination access.
- Return BLOCK (or any other return statement apart from DIRECT) to block destination access.
- Return PROXY to forward the selected internet traffic to a proxy server with or without a port. Applies to Zscaler Client Connector version 4.5 for Windows and macOS only.
- **DNS Settings**:
-
**Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
If you have Internet & SaaS only, you cannot download the DNS Record Generator.
- **ZIA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
If you have Internet & SaaS only, you cannot download the DNS Record Generator.
[]
ZPA Disaster Recovery provides users access to applications when the Private Applications service is down. ZPA Disaster Recovery mode is available only to enrolled users. To configure ZPA Disaster Recovery:
- Select **Enable ZPA DR**.
- **DNS Settings:**
- **Precreate a DNS TXT record with the Zscaler DNS generator tool**: To create an Active Domain Name and Domain Public Key, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **ZPA Domain name**: Enter a valid domain name.
- **TXT Record Signing Public Key**: Click **Upload** to add a valid public key. You can only upload `.pem` files.
- **Activation: **Activate or test disaster recovery by updating the DNS TXT record value. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
- **Test Mode: **Enable **Activate Test Mode** if the selected users and/or groups for the app profile are part of a group to test disaster recovery. Zscaler recommends that disaster recovery be tested periodically with just a few users.
[]
If you use Z-Tunnel 2.0, you can control how DNS requests are handled by Zscaler Client Connector to send only specific DNS requests to the Internet & SaaS Public Service Edge through Z-Tunnel 2.0. Complete the following steps in the **Domain Inclusion** and **Domain Exclusion** fields:
You can enter specific domains (e.g., `google.com`) or enter a wildcard (e.g., `*`* *or `*.[internaldomain].com`) to include or exclude all or specific DNS domains. For specific domains, up to two levels of subdomains are automatically included or excluded (e.g., if you enter `safemarch.com`, Zscaler Client Connector includes downloads.safemarch.com but not web.downloads.safemarch.com). Press `Enter` after each entry. You can add multiple items at the same time by separating each item with a comma and then pressing `Enter` when finished. The maximum number of characters is 65,535 in each field. You can click the **Copy** icon to copy the items from the list.
- **Domain Inclusion**: Enter the DNS domains for which Zscaler Client Connector should send requests.
- **Domain Exclusion**: Enter the DNS domains for which Zscaler Client Connector should not send requests.
[How Zscaler Client Connector processes the domain inclusions and exclusions](#DNS_IP_in_Exclusion_andr)
[]Zscaler Client Connector first checks if the DNS server IP address on the client is in **IPv4 Exclusion**. If the DNS server IP address on the client is in the exclusion, Zscaler Client Connector then processes domain inclusions followed by domain exclusions. An explicit domain match takes precedence over a wildcard-based match. If the domain doesn't match a domain listed in **Domain Inclusion** or **Domain Exclusion** or the fields are empty, the DNS request is sent to the DNS server defined on the device.
If the DNS Server IP matches a value in **IPv4 Exclusion**, Zscaler Client Connector sends the DNS request based on the following:
| Domain matches Domain Inclusion | Domain matches Domain Exclusion | DNS Request Forwarded To |
| ------------------------------- | ------------------------------- | ------------------------ |
| No | Yes | DNS Server on the device |
| Yes | No | Internet & SaaS |
| Wildcard (*) | Yes | DNS Server on the device |
| Wildcard (*) | No | Internet & SaaS |
| No or **Domain Inclusion** is empty | Wildcard (*) | DNS Server on the device |
| Yes | Wildcard (*) | Internet & SaaS |
| No | No | DNS Server on the device |
| **Domain Inclusion** is empty | **Domain Exclusion** is empty | DNS Server on the device |
[]
- **Drop QUIC Traffic**: This option is for websites that use QUIC (UDP 443), which is not supported by Z-Tunnel 1.0. When enabled, Z-Tunnel 1.0 drops QUIC packets so the application can fall back to TCP 443.
- **Reactivate ZIA After**: Enter the number of minutes that must pass before Zscaler Client Connector reactivates Internet & SaaS after the user turns it off. To enable the reactivation period, enter any value from `1` to `1,440` minutes. To disable, enter `0` (zero). Zscaler Client Connector doesn't reactivate Internet & SaaS after the user turns it off.
[]Configure the following optional passwords:
- **Logout Password**: Provide the password users must enter to log out of Zscaler Client Connector.
- **Disable Password ZIA**: Provide the password users must enter to disable the Internet & SaaS service.
- **Disable Password ZPA: **Provide the password users must enter to disable the Private Applications service.
- **Disable Password ZDX**: Provide the password users must enter to disable the Digital Experience Monitoring service.
- **Uninstall Password**: Provide the password users must enter to uninstall Zscaler Client Connector.
Click the **View **icon next to each password setting to show (![show-password-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/show-password-app-profile.png)
) or hide (![hide-psswrd-app-profile.png](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-zscaler-client-connector-app-profiles-windows/hide-psswrd-app-profile.png)
) the password.
[]
- **Log Mode**: Zscaler Client Connector generates logs that users can send to a designated support admin in your organization, or to Zscaler Support (in encrypted form). To specify the scope of the logs, select one of the following log modes:
- **Default (Current: <log mode>)**: Displays the default global log mode [configured in Platform Settings](/unified/configuring-default-global-log-mode). You can override this setting, for the current profile only, by selecting a different option from the drop-down menu.
- **Error**: Zscaler Client Connector logs only when the app encounters an error and functionality is affected.
- **Warn**: Zscaler Client Connector logs when the app is functioning but is encountering potential issues, or when conditions for the Error log mode are met.
- **Info**: Zscaler Client Connector logs general app activity, or when conditions for the Warn log mode are met.
- **Debug**: Zscaler Client Connector logs all app activity that could assist Zscaler Support in debugging issues, or when conditions for the Info log mode are met.
- **Log File Size in MB**: If you are using Zscaler Client Connector for Private Applications only, skip this option. Enter a value between 50 and 500 to specify the maximum size of the log file. The default log file size is 100 MB per log type. When logs reach the maximum file size, the oldest logs are truncated from the file to keep the file size below the maximum.
- **Verbose Logging**: When you select this option, users can enable extra debugging logs in Zscaler Client Connector.
- **ZPA ReAuth Notification**: Enable this option to alert users that applications they recently accessed through Private Applications are going to expire. In the warning message that displays, users can click **Reauthenticate** to take them to an authentication screen before expiration. You can set how far in advance of an application's expiration to display the expiration notification in the **Advanced Notification time (In Mins)** field. Enter a value between `5` and `1440`. Users can also click **Authenticate Early **in the **Private Access** window, under the Connectivity** **section, in Zscaler Client Connector, to reauthenticate Private Applications before their authentication expires.
[]
For Android devices, you can define a monthly quota to ensure that cellular bandwidth is used for business applications only. This quota setting affects cellular data only. It doesn't affect Wi-Fi. You must allowlist your business applications to exempt them from the quota.
Zscaler ended support of bandwidth quota control for Zscaler Client Connector version 1.5.3 and later for Android.
Before the quota is exceeded, users can use cellular data for both personal and business apps. When the quota is met, users can only access cellular data for corporate apps (i.e., apps placed on the allowlist). Personal apps are not allowed to access the cellular data network, but they can still be used on Wi-Fi.
- **Enable Quota on Cellular Network**: Enable to define a monthly quota to ensure that cellular bandwidth is used for business applications only. To learn more, see [Configuring a Cellular Quota with Zscaler Client Connector for Android](/unified/configuring-cellular-quota-zscaler-client-connector-android).
- **Enforce Quota Only For Roaming Users**: Enable to enforce the quota only when users are roaming.
- **Monthly Billing Day**: Select a day of the month from the drop-down menu. The day you select is when the cellular quota is reset every month (e.g., if you select 1, the cellular quota is reset on January 1st, February 1st, March 1st, etc.).
- **Quota (MB)**: Specify the quota in MB. Enter a value from 1 to 10,000.
- **Wi-Fi SSID**: (Optional) Enter the SSID of your internal local-area network (WLAN) if you want to test and simulate data usage for that specific SSID.
- **Block Notification Message**: (Optional) Enter or paste text of the notification that appears when the quota is exceeded. You can enter HTML tags and images, as long as the image files are accessible from the internet.
- **Android Applications on Allowlist**: (Optional) To allowlist Android applications:
- Add the apps’ identifiers, separated by commas, to exclude apps from the quota calculation. To find the app identifier, go to Google Play and navigate to the app’s details page. The identifier is listed after the `id` parameter in the details page’s URL. For example, the URL for Zscaler Client Connector’s Google Play detail page is `https://play.google.com/store/apps/details?id=zscaler.com.zscaler`. The identifier for Zscaler Client Connector is `zscaler.com.zscaler`.
- Click **Find Applications**.
- In the **Edit Applications List** window:
- View the applications under **Apps on Allowlist** list.
- Click the **Delete** icon for an application to remove it from **Apps on Allowlist**.
- Select applications from the **Preloaded Apps** list to add them back to **Apps on Allowlist**.
- Click **Save**.
The saved applications appear in the **Android Applications** on **Allowlist** section.
[]
**Send Disable Service Reason**: This option allows users to describe why a Zscaler service (e.g., Internet & SaaS, Private Applications, Digital Experience Monitoring) was disabled on a device. By default, this option is disabled. This information is accessible when viewing [device details](/unified/viewing-device-fingerprint-enrolled-device).
[]
**Policy Description**: Enter any notes regarding the policy.