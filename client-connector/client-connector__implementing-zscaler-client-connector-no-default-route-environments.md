# Implementing Zscaler Client Connector in No-Default Route Environments
Source: https://help.zscaler.com/client-connector/implementing-zscaler-client-connector-no-default-route-environments
PDF: https://help.zscaler.com/pdf/com/en/1506796.pdf

You can deploy Zscaler Client Connector in a no-default route environment to provide a greater level of protection for end users connecting to the internet with minimal changes to the environment. In a typical network, the default route determines how traffic is forwarded to a specific destination when a route for that destination isn't available. The default route usually points to the edge router, and eventually out to the internet.
Some companies have deployed an alternate architecture, known as a no-default route environment, in their network. In such an environment, a default route isn't propagated through the network and the only way to egress is via an edge proxy server. Proxy servers are configured with a default route and placed in an edge DMZ (a neutral zone between an organization's internal network and the internet), which allows internet egress.
In a no-default route environment, browser traffic is explicitly sent to a proxy using a PAC file that is either served through a local web server, through the proxy itself, or through the use of Web Proxy Automatic Discovery. DNS resolution of public DNS records is restricted for all devices except the proxy server. The following image shows traffic flow in an explicit proxy environment.
![Traffic flow in explicit proxy environment](/downloads/client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/explicit-proxy-network-flow.png)
In these explicit proxy environments, the web browser downloads the PAC file and sends the request to access the website explicitly to the on-premises proxy. The proxy server challenges the web browser for authentication. The browser resends the request to the proxy and includes the required credentials. The proxy validates the credentials with the IdP and queries the DNS server to resolve the hostname for the website. Upon successful DNS resolution, the proxy server sends a new request to the website on the internet via the edge firewall/router. The website responds back to the proxy with the requested content and the proxy server inspects the content and sends the website content to the web browser. Internal hosts are neither allowed to resolve external DNS records nor access the internet directly without sending the request via the proxy server.
![Explicit proxy environment](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/explicit-proxy-network-flow_1.png)
Zscaler Client Connector Traffic Flow in a Typical Environment
Prior to deploying Zscaler Client Connector in a no-default route environment, it is important to first understand how the client operates in a typical environment. The following image shows traffic flow for Zscaler Client Connector in a typical environment. It doesn't show all operations (e.g., SAML and PKI) as those operations have no bearing on this article.
![Traffic flow in a typical environment](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/zscaler-client-connector-traffic-flow-in-typical-environments.png)
In a typical environment, Zscaler Client Connector communicates with the following entities:
| **Operation** | **Entity** | **Communication Details** |
| ------------- | ---------- | ------------------------- |
| Captive Portal Detection | Zscaler Client Connector Portal | Probe to gateway.zscaler.netProbe to gateway.[cloudname].net |
| Login Start | Zscaler Client Connector Portal | API call to login.[cloudname].net |
| Name Resolution | Internal DNS Servers | DNS resolution requests |
| Policy Download | Zscaler Client Connector PortalZscaler PAC Server | API call to mobile.[cloudname].netDownload App Profile PAC from pac.[cloudname].net |
| Service Discovery & Enrollment | Zscaler Client Connector Portal | API call to gateway.[cloudname].netAPI call to mobile.[cloudname].net |
| Tenant Cloud Discovery | Zscaler Client Connector Portal | Probe to mobile.zscaler.net |
| ZIA Authentication | Customer IdPZIA SAML SP | SAML call to customer IdPSAML call to ZIA (SP) |
| ZIA Traffic Forwarding | ZIA Public/Private Service Edge | Forwarding using Tunnel with Local Proxy, Z-Tunnel 1.0 & 2.0 |
| ZPA Authentication | Customer IdPZPA SAML SP | SAML call to customer IdPSAML call to ZPA (SP) |
| ZPA Traffic Forwarding | ZPA Broker/Public/Private Service Edge | Forwarding using Microtunnel (M-Tunnel) |
Configuration Requirements for Implementing Zscaler Client Connector in a No-Default Route Environment
You can deploy Zscaler Client Connector in no-default route environments to support different kinds of traffic forwarding requirements. Zscaler Client Connector supports operation in a no-default environment on the following platforms:
- Windows
- macOS
- Linux
- iOS
- Android
- Android on ChromeOS
[]At a high level, you must configure the following requirements to enable Zscaler Client Connector to communicate with Zscaler cloud in a no-default route environment:
| **Requirement** | **Description** |
| --------------- | --------------- |
| System PAC | For initial Service Discovery, Enrollment, Authentication and Policy and PAC Download using an Explicit Proxy IP address |
| Internal DNS Server Records | Spoofed Zscaler records pointing to Zscaler global virtual IP (GVIP) or an internal NAT address so Zscaler Client Connector can resolve Zscaler cloud addresses |
| GRE/IPsec Tunnel | To provide connectivity to the Zscaler cloud during initial configuration of Zscaler Client Connector and traffic forwarding for ZIA and ZPA. Tunnel isn't used for traffic forwarding if a Private Service Edge is present |
| ZIA Private Service Edge (optional) | You can deploy a ZIA Private Service Edge to forward traffic directly to the internet from the customer location. If Z-Tunnel 2.0 forwarding is required from on-premises, then a ZIA Private Service Edge is highly recommended |
| App and Forwarding Profile Settings | You must configure App and Forwarding Profiles to support the environment with the use of **Tunnel Internal Client Connector Traffic** and other features |
| Third-Party Proxy (optional) | You must configure explicit proxies to bypass authentication to the IdP and Zscaler cloud, must not attempt to re-resolve DNS based on Server Name Indication (SNI) and disable SSL inspection |
[]Zscaler Client Connector supports forwarding of different types of traffic in no-default environments. The following table includes the requirements for each type of traffic forwarded by Zscaler Client Connector. The configuration details for each scenario are covered in this article.
| **Scenario** | **ZIA Traffic Type** | **Zscaler Client Connector Forwarding Method** | **System PAC File** | **DNS Records** | **GRE/IPSec Tunnel** | **Third-Party Proxy** | **Zscaler Private/****Virtual Service Edge** | **Zscaler Private Access (ZPA)** |
| ------------ | -------------------- | ---------------------------------------------- | ------------------- | --------------- | -------------------- | --------------------- | -------------------------------------------- | -------------------------------- |
| 1 | HTTP/HTTPS | Tunnel w/ Local Proxy | Required | Required | Required | Supported | Supported | Supported |
| 2 | TCP 80, 443 | Z-Tunnel 1.0 | Required | Required | Required | Supported | Supported | Supported |
| 3 | All ports/protocols | Z-Tunnel 2.0 | Required | Required | Required* | N/A | Required | Supported |
| 4 | All ports/protocols | Z-Tunnel 2.0 | Required | Required | Required** | Required | N/A | Supported |
* GRE/IPSec tunnels used for all traffic except for ZIA traffic forwarding
** GRE/IPSec tunnels used for Service Discovery, Enrollment, and initial authentication only
Common Configuration Steps for All No-Default Route Environments
The following image shows the Zscaler Client Connector traffic flow during Service Discovery, Enrollment, and Initialization in no-default route environments.
![Traffic flow during service discovery](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/client-connector-traffic-flow-no-default.png)
The following image shows Zscaler Client Connector using the Zscaler GVIP as an Explicit Proxy for Service Discovery, Enrollment, and Initialization in no-default route environments.
![Zscaler Client Connector using the Zscaler GVIP as an Explicit Proxy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/client-connector-zscaler-gvip.png)
The following image shows that Zscaler Client Connector can use an internal IP as an Explicit Proxy for Service Discovery, Enrollment, and Initialization in no-default route environments. An edge device performs Destination NAT to the Zscaler GVIP.
![Zscaler Client Connector can use an internal IP as an Explicit Proxy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/client-connector-internal-ip.png)
No External Route Networks: Certain networks don't allow injection of public IP prefixes in internal routing tables. In these networks, an internal IP address can be used instead of the Zscaler GVIP with an upstream router/firewall performing Destination NAT and translating the internal address to the Zscaler GVIP. In these environments, the spoofed Zscaler DNS records must reference the internal IP instead of the Zscaler GVIP.
You must configure the following high-level steps to support Zscaler Client Connector in all no-default environments, regardless of traffic type and forwarding method. These steps allow Zscaler Client Connector to perform service discovery and enrollment when using Zscaler GVIPs.
- [1. Create GRE/IPSec tunnel configurations in ZIA and set up the tunnels from a router or firewall to the closest Zscaler data centers.](#create-gre-ipsec)
- [2. Create a new location in ZIA.](#new-location)
- [3. Determine the Zscaler GVIP address to use as the Explicit Proxy IP address and set up routing.](#determine-gvip)
- [4. Create required spoofed Zscaler DNS records in the internal DNS server.](#create-spoofed)
- [5. Create a System PAC file in ZIA Admin Portal and assign the PAC URL to internal devices using GPO or WPAD.](#create-system-pac-file)
- [6. Exempt IdP URLs from authentication in ZIA.](#exempt-idp-urls)
[]Use the following steps to create GRE/IPSec tunnel configurations in ZIA and set up the tunnels from a router or firewall to the closest Zscaler data centers:
- [Configuring GRE Tunnels](/zia/configuring-gre-tunnels)
- [Configuring an IPSec VPN Tunnel](/zia/configuring-ipsec-vpn-tunnel)
[]Follow the steps in [Configuring Locations](/zia/configuring-locations) to configure a new location in ZIA. The **Enforce Authentication **option must be **Disabled **for the newly created location.
[See image.](#enforce-authentication)
[]![Enforce authentication](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Common-config-new-location_0.png)
[]Determine the Zscaler GVIP address Zscaler Client Connector connects to by selecting one from the bottom of the page at [https://config.zscaler.com/[cloudname].net/cenr](https://config.zscaler.com/%5Bcloudname%5D.net/cenr.). For example, if your tenant is hosted in the zscalertwo cloud, use the configuration information from [https://config.zscaler.com/zscalertwo.net/cenr.](https://config.zscaler.com/zscalertwo.net/cenr.) The Zscaler GVIP address is located at the bottom of the page. The following image shows a list of GVIPs that you can use for forwarding traffic across the GRE/IPSec tunnel. This article uses 185.46.212.88 for all configurations except when forwarding traffic to a ZIA Private Service Edge.
![GVIPs used for forwarding traffic](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/zscaler-GVIP.png)
Create a route to forward traffic to the Zscaler GVIP via the GRE/IPSec tunnels.
[]Using 185.46.212.88 as the Zscaler VIP, create the following DNS Type A records in the internal DNS server.
| **DNS Record** | **Record Type** | **IP Address** | **Example Records for ZS2** |
| -------------- | --------------- | -------------- | --------------------------- |
| gateway.[cloudname].net | A | 185.46.212.88 | gateway.zscalertwo.net |
| gateway.zscaler.net | A | 185.46.212.88 | gateway.zscaler.net |
| login.[cloudname].net | A | 185.46.212.88 | login.zscalertwo.net |
| mobile.[cloudname].net | A | 185.46.212.88 | mobile.zscalertwo.net |
| mobile.zscaler.net | A | 185.46.212.88 | mobile.zscaler.net |
| pac.[cloudname].net | A | 185.46.212.88 | pac.zscalertwo.net |
Certain networks don't allow injection of public IP prefixes in internal routing tables. In those scenarios, you can use an internal IP address for DNS records instead of the Zscaler GVIP with an upstream router/firewall performing Destination NAT and translating the internal address to the Zscaler GVIP.
The following table shows the DNS records when an internal IP address is used instead of a Zscaler GVIP address.
| **DNS Record** | **Record Type** | **IP Address (No External Route Environments)** | **Example Records for ZS2** |
| -------------- | --------------- | ----------------------------------------------- | --------------------------- |
| gateway.zscaler.net | A | 10.10.10.10 | gateway.zscaler.net |
| mobile.zscaler.net | A | 10.10.10.10 | mobile.zscaler.net |
| gateway.[cloudname].net | A | 10.10.10.10 | gateway.zscalertwo.net |
| mobile.[cloudname].net | A | 10.10.10.10 | mobile.zscalertwo.net |
| login.[cloudname].net | A | 10.10.10.10 | login.zscalertwo.net |
| pac.[cloudname].net | A | 10.10.10.10 | pac.zscalertwo.net |
[]A System PAC file is required for initial discovery, enrollment, authentication, app and forwarding profile policy and PAC file downloads. The System PAC enables Zscaler Client Connector to communicate with the Zscaler cloud in an explicit proxy mode. You can use a Zscaler GVIP address as the explicit proxy address or you can use a third-party proxy, as long as it meets the [configuration requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#config-requirements). After enrollment, the System PAC is no longer used by Zscaler Client Connector. Zscaler Client Connector restores the System PAC upon exit.
To create a hosted PAC file in ZIA, see [About Hosted PAC Files](/zia/about-hosted-pac-files).
The following hosted System PAC file references the Zscaler GVIP [previously mentioned](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#determine-gvip) and is specific to the Zscaler Two cloud.
[See PAC file.](#pac-file-1)
[]
`function FindProxyForURL(url, host) {
var egressip = "${SRCIP}";
var privateIP = /^(0|10|127|192\.168|172\.1[6789]|172\.2[0-9]|172\.3[01]|169\.254|192\.88\.99)\.[0-9.]+$/;
var resolved_ip = dnsResolve(host);
// Bypass RFC-1918 and internal domain
if ((shExpMatch(host, "*.internaldomain.com")) || (privateIP.test(resolved_ip)))
return "DIRECT";
// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
{
if ((dnsDomainIs(host, "1.2.3.4")) || (shExpMatch(host, "*.zscaler.net")) ||
(shExpMatch(host, "*.zscalertwo.net")) || //Service Discovery, Enrollment, Login
(shExpMatch(host, "mobilesupport.zscaler.com")) || //Support
(shExpMatch(host, "*.zdxcloud.net")) || //ZDX
(shExpMatch(host, "*.digicert.com")) || //Cert validation
// Required for ZPA
(shExpMatch(host, "*.prod.zpath.net")) || (shExpMatch(host, "*.private.zscaler.com")) ||
// Zscaler Updates
(localHostOrDomainIs(host, "d32a6ru7mhaq0c.cloudfront.net")) || (localHostOrDomainIs(host, "d3l44rcogcb7iv.cloudfront.net")) ||
(localHostOrDomainIs(host, "dwv281inkfqg3.cloudfront.net")) ||
// Required for Entra IdP
(shExpMatch(host, "*.msauth.net")) || (shExpMatch(host, "*.msauthimages.net")) ||
(shExpMatch(host, "*.msftauthimages.net")) || (localHostOrDomainIs(host, "login.microsoftonline.com")) ||
(localHostOrDomainIs(host, "autologon.microsoftazuread-sso.com")) || (localHostOrDomainIs(host, "login.windows.net")) ||
// Required for OKTA
(shExpMatch(host, "*.okta.com")) || (shExpMatch(host, "*.oktacdn.com")) || (shExpMatch(host, "*.oktapreview.com")))
{
return "PROXY 185.46.212.88:80";
}
}
return "DIRECT";
}`
You can use the System PAC file for devices that are on Trusted Networks (with a GRE/IPSec tunnel) or Off Trusted Networks (remote users). The PAC file logic detects the device location using the `${SRCIP}` macro. If the device is at a location with an existing GRE/IPSec tunnel, it uses the Zscaler GVIP as the Explicit Proxy IP address in order to connect to Zscaler and if the device is on an Off Trusted Network, it communicates directly with the closest Zscaler data center.
The following table shows the System PAC file code details:
[](https://config.zscaler.com/%5Bcloudname%5D.net/cenr)
[](#zscaler-ip-addresses)
[]![Zscaler aggregate IP address ranges](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Common-config-PAC-file-code-details-public-egress.png)
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `var egressip = "${SRCIP}";` | Determines the client's public IP address using the ${SRCIP} macro which is only available when the PAC file is hosted in the Zscaler cloud. |
| `if ((shExpMatch(host, "*.internaldomain.com")) || (privateIP.test(resolved_ip)))
return "DIRECT";` | Don't use proxy for internal domains and RFC-1918 addresses. Replace `internaldomain.com` with your internal domains. |
| `// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))` | List of Zscaler public IP addresses to detect whether Zscaler Client Connector is accessing the Zscaler cloud using a GRE/IPSec tunnel. These addresses are documented in the Zscaler Aggregate IP Address Ranges section: https://config.zscaler.com/[cloudname].net/cenrSee image. |
| `if ((dnsDomainIs(host, "1.2.3.4")) || (shExpMatch(host, "*.zscaler.net")) ||` | Special URL checked by Zscaler Client Connector to enroll using an explicit proxy, in this case the Zscaler GVIP (185.46.212.88). |
| `(shExpMatch(host, "*.zscalertwo.net")) || //Service Discovery, Enrollment, Login` | Replace the wildcard domain with the one that matches the customer cloud. |
| `(shExpMatch(host, "mobilesupport.zscaler.com")) || //Support
(shExpMatch(host, "*.zdxcloud.net")) || //ZDX
(shExpMatch(host, "*.digicert.com")) || //Cert validation` | Required for support access, Zscaler Digital Experience (ZDX) and certificate validation during discovery and enrollment. |
| `(shExpMatch(host, "*.prod.zpath.net")) || (shExpMatch(host, "*.private.zscaler.com")) ||` | Required for ZPA discovery and enrollment. |
| `(localHostOrDomainIs(host, "d32a6ru7mhaq0c.cloudfront.net")) || (localHostOrDomainIs(host, "d3l44rcogcb7iv.cloudfront.net")) ||
(localHostOrDomainIs(host, "dwv281inkfqg3.cloudfront.net")) ||` | Required for Zscaler Client Connector software and module updates during discovery and enrollment. |
| `(shExpMatch(host, "*.msauth.net")) || (shExpMatch(host, "*.msauthimages.net")) ||
(shExpMatch(host, "*.msftauthimages.net")) || (localHostOrDomainIs(host, "login.microsoftonline.com")) ||
(localHostOrDomainIs(host, "autologon.microsoftazuread-sso.com")) || (localHostOrDomainIs(host, "login.windows.net")) ||` | Required for authentication during enrollment. The example shows domains required by Entra. Use domains required for your IdP. |
| `{
return "PROXY 185.46.212.88:80";
}` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address for service discovery, enrollment, authentication, and policy and pac downloads.Instead of using the Zscaler GVIP, use the internal IP address, e.g., 10.10.10.10 for No External Route Networks. |
| `return "DIRECT";
}` | All other traffic is sent directly to the local network. |
[][Zscaler Client Connector] must be able to authenticate with the IdP in order for enrollment and policy downloads to succeed. To ensure that Zscaler Client Connector is able to authenticate, you must add the IdP URLs to the Authentication Exemptions list in ZIA.
- Follow the steps in [Exempting URLs and Cloud Apps from Authentication](/zia/exempting-urls-cloud-apps-authentication) to configure the authentication exemptions list.
The IdP URLs depend on the type of IdP in use. Consult your IdP documentation for details. The following example shows IdP URLs for Microsoft Entra ID and Okta.
- Add the IdP and other required URLs to the Exempted URLs list.
[See image.](#exempted-urls)
[]![Exempted URLs list](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/add-IdP-to-exempted-URLs.png)
The following are example URLs for Entra ID and Okta.
| **IdP/Service** | **URL** |
| --------------- | ------- |
| Entra ID | login.microsoftonline.com |
|  | autologon.microsoftazuread-sso.com |
|  | *.windowsazure.com |
|  | device.login.microsoftonline.com |
|  | login.microsoft.com |
|  | login.windows.net |
|  |  |
| Okta | *.okta.com |
|  | *.oktacdn.com |
|  | *.oktapreview.com |
| ZPA | *.zpath.net |
|  | *.private.zscaler.com |
Scenarios: Types of Traffic Forwarded by Zscaler Client Connector
- [Scenario 1 - Forwarding ZIA HTTP/HTTPS Traffic Using Tunnel with Local Proxy and ZPA Traffic](#scenario-1)
- [Scenario 2 - Forwarding ZIA TCP 80/443 Traffic Using Z-Tunnel 1.0 and ZPA Traffic](#scenario-2)
- [Scenario 3 - Forwarding ZIA Traffic on All Ports and Protocols Using Z-Tunnel 2.0 via On-Premises ZIA Private Service Edge and ZPA Traffic](#scenario-3)
- [Scenario 4 - Forwarding ZIA Traffic on All Ports and Protocols Using Z-Tunnel 2.0 via On-Premises Third-Party Proxy And ZPA Traffic](#scenario-4)
[]The following image shows Zscaler Client Connector forwarding ZIA and ZPA traffic via the Zscaler GVIP IP.
![Zscaler Client Connector forwarding ZIA and ZPA traffic via the Zscaler GVIP](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/scenario-1-client-connector-forwards-traffic_0.png)
In this scenario, after enrollment has completed, Zscaler Client Connector forwards ZIA HTTP/HTTPS using TWLP/Z-Tunnel 1.0 and ZPA traffic using M-Tunnels to the Zscaler GVIP. The Zscaler GVIP in turn forwards the traffic to ZIA and ZPA services in the Zscaler cloud. You can optionally use a third-party proxy in this scenario as long as it meets the [configuration requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#config-requirements) and forwards the traffic through the GRE/IPSec tunnel. The steps in this scenario do not cover configuration using a third-party proxy as third-party proxies aren't required.
You must configure the following high-level steps to forward HTTP/HTTPS traffic by Zscaler Client Connector using Tunnel with Local Proxy (TWLP) in No-Default Environments.
- [1. Complete Common Configuration Requirements for All No-Default Route Environments](#scenario-1-common-config-for-no-default)
- [2. Create a Hosted Forwarding Profile PAC File for Tunnel with Local Proxy (TWLP)](#scenario-1-create-forwarding-profile-pac-file)
- [3. Create a Forwarding Profile to Use Tunnel with Local Proxy for On Trusted Network and Use Z-Tunnel 2.0 for Off Trusted Network](#scenario-1-forwarding-profile-on-off-trusted)
- [4. Create a Hosted App Profile PAC File for Tunnel with Local Proxy (TWLP)](#scenario-1-create-hostel-tunnel-local-proxy-app-profile-pac-file)
- [5. Create an App Profile](#scenario-1-create-app-profile)
[]Before following the next steps, make sure the [configuration requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#config-requirements) for all no-default route environments are met.
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file.
[See PAC file.](#scenario-1-forwarding-pac-file)
[]
``function FindProxyForURL(url, host) {`
`   if ((dnsDomainIs(host, "1.2.3.4")) ||`
`       (shExpMatch(host, "*.prod.zpath.net")))`
`     return "PROXY 185.46.212.88:80";`
`   return "PROXY ${ZAPP_LOCAL_PROXY}";`
`}``
See the following table for forwarding PAC file details.
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `if ((dnsDomainIs(host, "1.2.3.4")) ||` | Special URL checked by Zscaler Client Connector to enroll using an Explicit proxy, in this case the Zscaler GVIP (185.46.212.88). |
| `(shExpMatch(host, "*.prod.zpath.net")))` | Required for ZPA discovery and enrollment. |
| `return "PROXY 185.46.212.88:80";` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address to complete discovery and enrollment.Instead of using the Zscaler GVIP, use the internal IP address, e.g., 10.10.10.10 for No External Route Networks. |
| `return "PROXY ${ZAPP_LOCAL_PROXY}";` | Send all other traffic to Zscaler Client Connector. |
[]To create a forwarding profile for on-trusted and off-trusted networks:
- In the Zscaler Client Connector Portal, go to **Administration** > **Forwarding Profile**.
- Click **Add Forwarding Profile**.
The **Add Forwarding Profile** window appears.
- Enter a name for the profile.
- For **Predefined Trusted Networks**, choose the **Selected** option. This allows Zscaler Client Connector to detect when it is in a no-default-route environment. To learn more about trusted networks, see [Configuring Trusted Networks for Zscaler Client Connector](/zscaler-client-connector/configuring-trusted-networks-zscaler-client-connector).
[See image.](#scenario-1-edit-forwarding-profile)
[]![forwarding profile section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario%201-%20Forwarding%20Profile_0.png)
- For **On Trusted Network**, select **Tunnel with Local Proxy**.
- For **Proxy Action Type**, select **Enforce**.
- Select the **PAC URL Location** and choose **PAC URL**.
- In the **Custom PAC URL** section, enter the PAC URL for the forwarding profile.
[See image.](#scenario-1-edit-forwarding-profile-cont)
[]![On trusted network](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-1-Fwd-Profile-TWLP-On-Trusted-Network_1.png)
- For **Off Trusted Network**, select the forwarding mechanisms as per your organization's requirements. Zscaler supports all forwarding mechanism for off-trusted network users. The following example uses Z-Tunnel 2.0.
- For **Off Trusted Network**, choose **Tunnel**.
- For **Tunnel version selection**, select **Z-Tunnel 2.0**.
[See image.](#scenario-1-forwarding-profile-off-trusted)
[]![Off trusted](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-1-Fwd-Profile-ZT2-Off-Trusted-Network-1_1_1.png)
- Enable **Redirect Web Traffic to Zscaler Client Connector Listening Proxy**.
A PAC URL is not required for an Off-Trusted Network.
[See image.](#scenario-1-forwarding-profile-off-trusted-1)
[]![forwarding profile section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd-Profile-Off-Trusted-Network-Cont_0.png)
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file:
[See PAC file.](#scenario-1-pac-file)
[]
``function FindProxyForURL(url, host) {`
`   var customPort = "${ZS_CUSTOM_PORT}"; // Assigned port for local region - ZS_CUSTOM_PORT`
`   var privateIP = /^(0|10|127|192\.168|172\.1[6789]|172\.2[0-9]|172\.3[01]|169\.254|192\.88\.99)\.[0-9.]+$/;`
`   var resolved_ip = dnsResolve(host);`
`   var trust = /^(trust|ips).(zscaler|zscalerone|zscalertwo|zscalerthree|zsdemo|zscalergov|zscloud|zsfalcon|zdxcloud|zdxpreview).(com|net)$/;`
`   var iam = /^.*.(zslogin|zsloginbeta|zslogindemo).net$/;`
`   var egressip = "${SRCIP}";`
`    // Don't send non-FQDN or private IP auths to us`
`   if (isInNet(resolved_ip, "192.0.2.0", "255.255.255.0") || privateIP.test(resolved_ip))`
`       return "DIRECT";`
`   // Zscaler public egress subnets`
`   if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||`
`       (isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||`
`       (isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||`
`       (isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||`
`       (isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||`
`       (isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||`
`       (isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||`
`       (isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||`
`       (isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||`
`       (isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||`
`       (isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||`
`       (isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||`
`       (isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||`
`       (isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))`
`       return "PROXY 185.46.212.88:80";`
`   if (trust.test(host) || iam.test(host) || /^trust.zscaler.us$/.test(host) || /^config.zscaler.com$/.test(host))`
`       return "DIRECT";`
`   // Bypasses for ZPA`
`   if ((isInNet(resolved_ip, "100.64.0.0", "255.255.0.0")) || (shExpMatch(host, "*.private.zscaler.com")) || (shExpMatch(host, "*.zpath.net")))`
`       return "DIRECT";`
`   return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";`
`}``
Use the following PAC file code details:
[](https://config.zscaler.com/%5Bcloudname%5D.net/cenr)
[](#scenario-1-zscaler-ip-addresses)
[]![Zscaler aggregate IP address ranges](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-1-Common-config-PAC-file-code-details-public-egress.png)
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `var egressip = "${SRCIP}";` | Determines the client's public IP address using the ${SRCIP} macro which is only available when the PAC file is hosted in the Zscaler cloud. |
| `if ((shExpMatch(host, "*.internaldomain.com")) || (privateIP.test(resolved_ip)))
return "DIRECT";` | Don't use proxy for internal domains and RFC-1918 addresses. Replace `internaldomain.com` with your internal domains. |
| `// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
return "PROXY 185.46.212.88:80";` | List of Zscaler public IP addresses to detect whether Zscaler Client Connector is accessing the Zscaler cloud using a GRE/IPSec tunnel. These addresses are documented in the Zscaler Aggregate IP Address Ranges section: https://config.zscaler.com/[cloudname].net/cenrSee image. |
| `{
return "PROXY 185.46.212.88:80";
}` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address for service discovery, enrollment, authentication, and policy and pac downloads.Instead of using the Zscaler GVIP, use the internal IP address, e.g., 10.10.10.10 for No External Route Networks. |
| `    if (trust.test(host) || iam.test(host) || /^trust.zscaler.us$/.test(host) || /^config.zscaler.com$/.test(host))
return "DIRECT";
// Bypasses for ZPA
if ((isInNet(resolved_ip, "100.64.0.0", "255.255.0.0")) || (shExpMatch(host, "*.private.zscaler.com")) || (shExpMatch(host, "*.zpath.net")))
return "DIRECT";` | When Zscaler Client Connector is Off Trusted Network use this criteria to bypass Zscaler. |
| `    return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";
}` | Use auto-assigned data centers to connect via Z-Tunnel 2.0 when Off Trusted Network. |
[]Create an App Profile** **and associate it to the [previously created Forwarding Profile](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#scenario-1-forwarding-profile-on-off-trusted):
- In the Zscaler Client Connector Portal, in the left-side navigation, click **App Profiles** and select the relevant OS. The following example uses Windows.
- Click **Add Windows Policy**. The **Add Windows Policy** window appears.
- For** Forwarding Profile**, choose the forwarding profile [previously created](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#scenario-1-forwarding-profile-on-off-trusted).
[See image.](#scenario-1-app-profile-general)
[]![Enter a Name and select a Forwarding Profile](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario%201%20-%20App%20Profile_0.png)
- In the **PAC and Proxy** section, enter the URL in the **Custom PAC URL** section.
- In **Proxy Configuration**, enable **Disable Loopback Restriction**.
- Enable the **Cache System Proxy**. When enabled, this option restores the System PAC after the user exits Zscaler Client Connector.
- **Override WPAD**:** **(Optional) Enable this option if WPAD is in use.
- **Restart WinHTTP Service**:** **(Optional) Enable this option if WPAD is in use.
[See image.](#scenario-1-app-profile-pac-proxy)
[]![PAC and Proxy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/scenario-1-app-profile-2_1.png)
- In the **Advanced** section, enable **Tunnel Internal Client Connector Traffic**.
[See image.](#scenario-1-app-profile-advanced)
[]![Advanced section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/scenario-1-app-profile-3_1.png)
[]In this scenario, Zscaler Client Connector forwards ZIA TCP 80/443 traffic using Z-Tunnel 1.0 and ZPA traffic using M-Tunnels to the Zscaler GVIP. The Zscaler GVIP, in turn, forwards the traffic to ZIA and ZPA services in the Zscaler cloud. In this scenario, you can optionally use a third-party proxy as long as it meets the [requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#scenario-table) and forwards the traffic through the GRE/IPSec tunnel. The following directions don't cover configuration using a third-party proxy because third-party proxies aren't required and can be deprecated in this scenario.
![Zscaler Client Connector forwards ZIA TCP 80/443 traffic using Z-Tunnel 1.0 and ZPA traffic using M-Tunnels](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Zscaler-Fwd-Traffic_0.png)
The following high-level steps must be configured to forward TCP 80/443 traffic by Zscaler Client Connector using Z-Tunnel 1.0 in no-default Environments.
- [1. Complete common configuration requirements for all no-default route environments](#scenario-2-common-config-requirements)
- [2. Create a hosted Z-Tunnel 1.0 Forwarding Profile PAC file](#scenario-2-forwarding-profile-pac-file)
- [3. Create a Forwarding Profile to use Z-Tunnel 1.0 when On Trusted Network and use Z-Tunnel 2.0 when Off Trusted Network](#scenario-2-forwarding-profile-off-on-trusted)
- [4. Create a hosted App Profile PAC file](#scenario-2-hosted-app-profile-pac-file)
- [5. Create an App Profile](#scenario-2-create-app-profile)
[]Ensure that all [configuration requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#config-requirements) have been met before continuing with the following steps.
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file.
[See PAC file.](#scenario-2-pac-file)
[]
``function FindProxyForURL(url, host) {`
`   if ((dnsDomainIs(host, "1.2.3.4")) ||`
`       (shExpMatch(host, "*.prod.zpath.net")))`
`     return "PROXY 185.46.212.88:80";`
`   return "PROXY ${ZAPP_LOCAL_PROXY}";`
`}``
Refer to the following table for forwarding PAC file details.
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `if ((dnsDomainIs(host, "1.2.3.4")) ||` | Special URL checked by Zscaler Client Connector to enroll using an Explicit proxy, in this case the Zscaler GVIP (185.46.212.88). |
| `(shExpMatch(host, "*.prod.zpath.net")))` | Required for ZPA discovery and enrollment. |
| `return "PROXY 185.46.212.88:80";` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address to complete discovery and enrollment.Instead of using the Zscaler GVIP, use the internal IP address, e.g., 10.10.10.10 for No External Route Networks. |
| `return "PROXY ${ZAPP_LOCAL_PROXY}";` | Send all other traffic to Zscaler Client Connector. |
[]Create a [Trusted Network Criteria ](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector)so Zscaler Client Connector can detect when it is on a Trusted Network (no-default route environment). Follow these steps to create forwarding profile:
- In the Zscaler Client Connector Portal, go to **Administration** > **Forwarding Profile**.
- Click **Add Forwarding Profile**.
The **Add Forwarding Profile** window appears.
- Enter a name for the profile.
- For **Predefined Trusted Networks**, choose the **Selected** option. This allows Zscaler Client Connector to detect when it is in a no-default-route environment. To learn more about trusted networks, see [Configuring Trusted Networks for Zscaler Client Connector](/zscaler-client-connector/configuring-trusted-networks-zscaler-client-connector).
[See image.](#scenario-2-edit-forwarding-profile)
[]![Edit forwarding profile](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Fwd-Profile-TWLP-Trusted-Network-Detection_1.png)
- For **On Trusted Network**, select **Tunnel**.
- For Tunnel version selection, select **Z-Tunnel 1.0**.
- For **Proxy Action Type**, select **Enforce**.
- Select the **PAC URL Location** and choose **PAC URL**.
- In the **Custom PAC URL** section, enter the PAC URL for the forwarding profile.
[See image.](#scenario-2-edit-forwarding-profile-cont)
[]![On trusted network](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Fwd-Profile-TWLP-Trusted-Network-Detection-On-Trusted_0_1.png)
- For **Off Trusted Network**, select the forwarding mechanisms as per your organization's requirements. Zscaler supports all forwarding mechanism for off-trusted network users. The following example uses Z-Tunnel 2.0.
- For **Tunnel version selection**, select **Z-Tunnel 2.0**.
[See image.](#scenario-2-edit-forwarding-profile-off-trusted-network)
[]![Off trusted network](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Fwd-Profile-TWLP-Trusted-Network-Detection-On-Trusted_0_0_1.png)
- Enable **Redirect Web Traffic to Zscaler Client Connector Listening Proxy**.
A PAC URL is not required for an Off Trusted Network.
[See image.](#scenario-2-edit-forwarding-profile-cont-2)
[]![Edit forwarding profile](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Fwd-Profile-Off-Trusted-Network-Cont.png)
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file:
[See PAC file.](#scenario-2-use-app-pac-file)
[]
`function FindProxyForURL(url, host) {
var customPort = "${ZS_CUSTOM_PORT}"; // Assigned port for local region - ZS_CUSTOM_PORT
var privateIP = /^(0|10|127|192\.168|172\.1[6789]|172\.2[0-9]|172\.3[01]|169\.254|192\.88\.99)\.[0-9.]+$/;
var resolved_ip = dnsResolve(host);
var trust = /^(trust|ips).(zscaler|zscalerone|zscalertwo|zscalerthree|zsdemo|zscalergov|zscloud|zsfalcon|zdxcloud|zdxpreview).(com|net)$/;
var iam = /^.*.(zslogin|zsloginbeta|zslogindemo).net$/;
var egressip = "${SRCIP}";
// Don't send non-FQDN or private IP auths to us
if (isInNet(resolved_ip, "192.0.2.0", "255.255.255.0") || privateIP.test(resolved_ip))
return "DIRECT";
// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
return "PROXY 185.46.212.88:80";
if (trust.test(host) || iam.test(host) || /^trust.zscaler.us$/.test(host) || /^config.zscaler.com$/.test(host))
return "DIRECT";
// Bypasses for ZPA
if ((isInNet(resolved_ip, "100.64.0.0", "255.255.0.0")) || (shExpMatch(host, "*.private.zscaler.com")) || (shExpMatch(host, "*.zpath.net")))
return "DIRECT";
return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";
}`
Refer to the following table for forwarding PAC file details.
[](#scenario-2-zscaler-ip-addresses)
[]![Zscaler aggregate IP address ranges](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-Common-config-PAC-file-code-details-public-egress%20-%20Copy.png)
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `var egressip = "${SRCIP}";` | Determines the client's public IP address using the ${SRCIP} macro which is only available when the PAC file is hosted in the Zscaler cloud. |
| `if ((shExpMatch(host, "*.internaldomain.com")) || (privateIP.test(resolved_ip)))
return "DIRECT";` | Don't use proxy for internal domains and RFC-1918 addresses. Replace `internaldomain.com` with your internal domains. |
| `// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
return "PROXY 185.46.212.88:80";` | List of Zscaler public IP addresses to detect whether Zscaler Client Connector is accessing the Zscaler cloud using a GRE/IPSec tunnel. These addresses are documented in the Zscaler Aggregate IP Address Ranges section: https://config.zscaler.com/[cloudname].net/cenrSee image. |
| `{
return "PROXY 185.46.212.88:80";
}` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address for service discovery, enrollment, authentication, and policy and pac downloads.Instead of using the Zscaler GVIP, use the internal IP address, e.g, . 10.10.10.10 for No External Route Networks. |
| `    if (trust.test(host) || iam.test(host) || /^trust.zscaler.us$/.test(host) || /^config.zscaler.com$/.test(host))
return "DIRECT";
// Bypasses for ZPA
if ((isInNet(resolved_ip, "100.64.0.0", "255.255.0.0")) || (shExpMatch(host, "*.private.zscaler.com")) || (shExpMatch(host, "*.zpath.net")))
return "DIRECT";` | When Zscaler Client Connector is Off Trusted Network, use this criteria to bypass Zscaler. |
| `    return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";
}` | Use auto-assigned data centers to connect via Z-Tunnel 2.0 when Off Trusted Network. |
[]Create an App Profile** **and associate it to the [previously created Forwarding Profile](/client-connector/implementing-zscaler-client-connector-no-default-route-environments):
- In the Zscaler Client Connector Portal, on the left-side navigation, click **App Profiles** and select the relevant OS. The following example uses Windows.
- Click **Add Windows Policy**. The **Add Windows Policy** window appears.
- For** Forwarding Profile**, choose the forwarding profile created [previously created](/client-connector/implementing-zscaler-client-connector-no-default-route-environments).
[See image.](#scenario-2-create-app-profile-1)
[]![Enter a Name and select a Forwarding Profile](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-App-Profile-General_2.png)
- In the **PAC and Proxy** section, enter the URL in the **Custom PAC URL** section.
- In **Proxy Configuration**, enable **Disable Loopback Restriction**.
- Enable the **Cache System Proxy **option. When enabled, this option restores the System PAC after the user exits Zscaler Client Connector.
- **Override WPAD**: (Optional) Enable this option if WPAD is in use.
- **Restart WinHTTP Service**:** **(Optional) Enable this option if WPAD is in use.
[See image.](#scenario-2-create-app-profile-2)
[]![PAC and Proxy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-App-Profile-PAC-and-Proxy_1.png)
- In the **Advanced** section, enable **Tunnel Internal Client Connector Traffic**.
[See image.](#scenario-2-create-app-profile-3)
[]![Advanced section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-2-App-Profile-Advanced_1.png)
[]In this scenario, Zscaler Client Connector forwards ZIA traffic across all ports and protocols using Z-Tunnel 2.0 via the ZIA Private Service Edge. ZPA M-Tunnels and authentication traffic are forwarded using the Zscaler GVIP. The Zscaler GVIP, in turn, forwards the traffic to ZPA services in the Zscaler cloud. In this scenario, the ZIA location associated with the ZIA Private Service Edge cluster has Force Authentication enabled to ensure that the Private Service Edge doesn't operate as an open proxy.
![Zscaler Client Connector forwards ZIA traffic across all ports and protocols using Z-Tunnel 2.0](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Forwarding-ZIA-Traffic_0.png)
You must configure the following high-level steps to forward traffic on all ports/protocols by Zscaler Client Connector using Z-Tunnel 2.0 in no-default Environments.
- [1. Complete Common Configuration Requirements for All no-default Route Environments](#scenario-3-complete-common-config-req)
- [2. Create a Hosted Forwarding Profile PAC File](#scenario-3-create-hosted-forwarding-profile)
- [3. Create a Forwarding Profile to Use Z-Tunnel 2.0 Forwarding for Both Trusted Network (no-default Route Network) and Off Trusted Network](#scenario-3-forwarding-profile-on-off-trusted)
- [4. Create a Hosted App Profile PAC File](#scenario-3-created-hosted-app-profile-pac-file)
- [5. Create an App Profile](#scenario-3-app-profile)
- [6. Deploy a ZIA Private Service Edge Cluster and Associate with a New ZIA Location with Force Authentication Enabled](#scenario-3-deploy-zia-private-service-edge)
[]Ensure that all [configuration requirements](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#config-requirements) have been met before continuing with the following steps.
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file:
[See PAC file.](#scenario-3-use-forwarding-profile-pac-file)
[]
``function FindProxyForURL(url, host) {`
`   var resolved_ip = dnsResolve(host);`
`   if ((dnsDomainIs(host, "1.2.3.4")) || (shExpMatch(host, "*.zscaler.net")) ||`
`       (shExpMatch(host, "*.zscalertwo.net")) || //Service Discovery, Enrollment, Login`
`       (shExpMatch(host, "mobilesupport.zscaler.com")) || //Support`
`       (shExpMatch(host, "*.zdxcloud.net")) || //ZDX`
`       (shExpMatch(host, "*.digicert.com")) || //Cert validation`
`        `
`       // Zscaler Updates`
`       (localHostOrDomainIs(host, "d32a6ru7mhaq0c.cloudfront.net")) || (localHostOrDomainIs(host, "d3l44rcogcb7iv.cloudfront.net")) ||`
`       (localHostOrDomainIs(host, "dwv281inkfqg3.cloudfront.net")) ||`
`        `
`       // Required for Entra IdP`
`       (shExpMatch(host, "*.msauth.net")) || (shExpMatch(host, "*.msauthimages.net")) ||`
`       (shExpMatch(host, "*.msftauthimages.net")) || (localHostOrDomainIs(host, "login.microsoftonline.com")) ||`
`       (localHostOrDomainIs(host, "autologon.microsoftazuread-sso.com")) || (localHostOrDomainIs(host, "login.windows.net")))`
`   {`
`       return "PROXY 185.46.212.88:80";`
`   }`
`   /* Forward to Client Connector */`
`   return "DIRECT";`
`}``
Refer to the following table for forwarding PAC file details.
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `if ((dnsDomainIs(host, "1.2.3.4")) || (shExpMatch(host, "*.zscaler.net")) ||` | Special URL checked by Zscaler Client Connector to enroll using an Explicit proxy, in this case the Zscaler GVIP (185.46.212.88). |
| `(shExpMatch(host, "*``.zscalertwo.net``")) || //Service Discovery, Enrollment, Login` | Replace the wildcard domain with the one that matches the cloud. |
| `(shExpMatch(host, "mobilesupport.zscaler.com")) || //Support``(shExpMatch(host, "*.zdxcloud.net")) || //ZDX``(shExpMatch(host, "*.digicert.com")) || //Cert validation` | Required for Support access, Zscaler Digital Experience (ZDX), and certificate validation during discovery and enrollment. |
| `(localHostOrDomainIs(host, "d32a6ru7mhaq0c.cloudfront.net")) || (localHostOrDomainIs(host, "d3l44rcogcb7iv.cloudfront.net")) ||``(localHostOrDomainIs(host, "dwv281inkfqg3.cloudfront.net")) ||` | Required for Zscaler Client Connector software and module updates during discovery and enrollment. |
| `(shExpMatch(host, "*``.msauth.net``")) || (shExpMatch(host, "*``.msauthimages.net``")) ||``(shExpMatch(host, "*``.msftauthimages.net``")) || (localHostOrDomainIs(host, "``login.microsoftonline.com``")) ||``(localHostOrDomainIs(host, "``autologon.microsoftazuread-sso.com``")) || (localHostOrDomainIs(host, "``login.windows.net``")) ||` | Required for authentication during enrollment. The example shows domains required by Entra. Use domains required for your IdP. |
| `return "PROXY 185.46.212.88:80";` | If Zscaler Client Connector is at a no-default route location, it uses the Zscaler GVIP 185.46.212.88 as the explicit proxy address to complete discovery and enrollment.Instead of using the Zscaler GVIP, use the internal IP address, e.g., 10.10.10.10 for No External Route Networks. |
| `return "DIRECT";``}` | All other traffic is sent to Zscaler Client Connector. |
[]Create a [Trusted Network Criteria](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector) so Zscaler Client Connector can detect when it is on a Trusted Network (no-default route environment). Follow these steps to create a forwarding profile:
- In the Zscaler Client Connector Portal, go to **Administration** > **Forwarding Profile**.
- Click **Add Forwarding Profile**.
The **Add Forwarding Profile** window appears.
- Enter a name for the profile.
- For **Predefined Trusted Networks**, choose the **Selected** option. This allows Zscaler Client Connector to detect when it is in a no-default route environment. To learn more about trusted networks, see [Configuring Trusted Networks for Zscaler Client Connector](/zscaler-client-connector/configuring-trusted-networks-zscaler-client-connector).
[See image.](#scenario-3-forwarding-profile-1)
[]![General settings](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd-Profile-TWLP-Trusted-Network-Detection_2.png)
- For **On Trusted Network**, select **Tunnel**.
- For Tunnel version selection, select **Z-Tunnel 2.0**.
[See image.](#scenario-3-forwarding-profile-2)
[]![On trusted network](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd-Profile-On-Trusted-Network_0.png)
- Disable **Redirect Web Traffic to Zscaler Client Connector Listening Proxy** and **Use Z-Tunnel 2.0 for Proxied Web Traffic**.
- For **Proxy Action Type**, select **Apply on Trusted Network Type Change**.
- Select the **PAC URL Location** and choose **PAC URL**.
- In the **Custom PAC URL** section, enter the PAC URL for the forwarding profile.
[See image.](#scenario-3-forwarding-profile-3)
[]![forwarding profile section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd%2520Profile-ZT2-On-Trusted-Network-Cont_0.png)
- For **Off Trusted Network**, select the forwarding mechanisms as per your organization's requirements. Zscaler supports all forwarding mechanism for off-trusted network users. The following example uses **Tunnel**.
- For **Tunnel version selection**, select **Z-Tunnel 2.0**.
[See image.](#scenario-3-forwarding-profile-4)
[]![Off-trusted network](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd-Profile-ZT2-Off-trusted-Network_0_0.png)
- Enable **Redirect Web Traffic to Zscaler Client Connector Listening Proxy**.
A PAC URL is not required for an Off Trusted Network.
[See image.](#scenario-3-forwarding-profile-5)
[]![forwarding profile section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Fwd-Profile-Off-Trusted-Network-Cont_0.png)
[]Follow the steps for [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia) to add a custom PAC file. Use the following PAC file:
`function FindProxyForURL(url, host) {
var customPort = "${ZS_CUSTOM_PORT}"; // Assigned port for local region - ZS_CUSTOM_PORT
var egressip = "${SRCIP}";
// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
return "PROXY 10.10.10.50";
return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";
}`
[](https://config.zscaler.com/%5Bcloudname%5D.net/cenr)
[](#scenario-3-zscaler-ip-addresses)
[]![Zscaler aggregate IP address ranges](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-Common-config-PAC-file-code-details-public-egress%20-%20Copy%20-%20Copy.png)
| **PAC File Code Details** | **Notes** |
| ------------------------- | --------- |
| `var egressip = "${SRCIP}";` | Determines the client's public IP address using the ${SRCIP} macro which is only available when the PAC file is hosted in the Zscaler cloud. |
| `// Zscaler public egress subnets
if ((isInNet(egressip, "58.220.95.0", "255.255.255.0")) || (isInNet(egressip, "64.215.22.0", "255.255.255.0")) ||
(isInNet(egressip, "87.58.64.0", "255.255.192.0")) || (isInNet(egressip, "94.188.131.0", "255.255.255.128")) ||
(isInNet(egressip, "94.188.139.64", "255.255.255.192")) || (isInNet(egressip, "94.188.248.64", "255.255.255.192")) ||
(isInNet(egressip, "98.98.26.0", "255.255.255.0")) || (isInNet(egressip, "98.98.27.0", "255.255.255.0")) ||
(isInNet(egressip, "98.98.28.0", "255.255.255.0")) || (isInNet(egressip, "101.2.192.0", "255.255.192.0")) ||
(isInNet(egressip, "104.129.192.0", "255.255.240.0")) || (isInNet(egressip, "112.137.170.0", "255.255.255.0")) ||
(isInNet(egressip, "124.248.141.0", "255.255.255.0")) || (isInNet(egressip, "128.177.125.0", "255.255.255.0")) ||
(isInNet(egressip, "136.226.0.0", "255.255.0.0")) || (isInNet(egressip, "137.83.128.0", "255.255.192.0")) ||
(isInNet(egressip, "140.210.152.0", "255.255.254.0")) || (isInNet(egressip, "147.161.128.0", "255.255.128.0")) ||
(isInNet(egressip, "154.113.23.0", "255.255.255.0")) || (isInNet(egressip, "165.225.0.0", "255.255.128.0")) ||
(isInNet(egressip, "165.225.192.0", "255.255.192.0")) || (isInNet(egressip, "167.103.0.0", "255.255.0.0")) ||
(isInNet(egressip, "170.85.0.0", "255.255.0.0")) || (isInNet(egressip, "185.46.212.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.96.0", "255.255.240.0")) || (isInNet(egressip, "194.9.112.0", "255.255.252.0")) ||
(isInNet(egressip, "194.9.116.0", "255.255.255.0")) || (isInNet(egressip, "196.23.154.64", "255.255.255.224")) ||
(isInNet(egressip, "196.23.154.96", "255.255.255.224")) || (isInNet(egressip, "197.98.201.0", "255.255.255.0")) ||
(isInNet(egressip, "197.156.241.224", "255.255.255.224")) || (isInNet(egressip, "198.14.64.0", "255.255.192.0")) ||
(isInNet(egressip, "199.168.148.0", "255.255.254.0")) || (isInNet(egressip, "209.55.128.0", "255.255.192.0")) ||
(isInNet(egressip, "209.55.192.0", "255.255.224.0")) || (isInNet(egressip, "211.144.19.0", "255.255.255.0")) ||
(isInNet(egressip, "220.243.154.0", "255.255.254.0")) || (isInNet(egressip, "221.122.91.0", "255.255.255.0")))
return "PROXY 10.10.10.50:80";` | List of Zscaler public IP addresses to detect whether Zscaler Client Connector is accessing the Zscaler cloud using a GRE/IPSec tunnel. These addresses are documented in the Zscaler Aggregate IP Address Ranges section: https://config.zscaler.com/[cloudname].net/cenrIf Zscaler Client Connector is at a no-default route location with a GRE/IPSec tunnel, then connect to the ZIA Private Service Edge VIP address at `10.10.10.50`.See image. |
| `return "PROXY ${GATEWAY_FX}:${ZS_CUSTOM_PORT}; PROXY ${SECONDARY_GATEWAY_FX}:${ZS_CUSTOM_PORT}; DIRECT";
}` | Use auto-assigned data centers to connect via Z-Tunnel 2.0 when Off Trusted Network. |
[]Create an App Profile** **and associate the [previously created Forwarding Profile](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#scenario-3-forwarding-profile-on-off-trusted) with it.
- In the Zscaler Client Connector Portal, on the left-side navigation, click **App Profiles** and select the relevant OS. The following example uses Windows.
- Click **Add Windows Policy**. The **Add Windows Policy** window appears.
- For** Forwarding Profile**, choose the [forwarding profile created previously](/client-connector/implementing-zscaler-client-connector-no-default-route-environments#scenario-3-forwarding-profile-on-off-trusted).
[See image.](#scenario-3-app-profile-1)
[]![General settings Windows Policy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile_0.png)
- In the **PAC and Proxy** section, enter the URL in the **Custom PAC URL** section.
- In **Proxy Configuration**, enable **Disable Loopback Restriction**.
- Enable the **Cache System Proxy **option. When enabled, this option restores the System PAC when the user exits Zscaler Client Connector.
- **Override WPAD**:** **(Optional) Enable this option if WPAD is in use.
- **Restart WinHTTP Service**:** **(Optional) Enable this option if WPAD is in use.
[See image.](#scenario-3-app-profile-2)
[]![PAC and Proxy](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-PAC-and-Policy_0.png)
- In the **Advanced** section, enable the **Tunnel Internal Client Connector Traffic**.
[See image.](#scenario-3-app-profile-3)
[]![Tunnel Internal Client Connector Traffic](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-PAC-Advanced.png)
- In the **App and IP Bypass** section, under **IPv4 Exclusion**, ensure that all internal IP subnets are added so the internal traffic is not tunneled to ZIA.
[See image.](#scenario-3-app-profile-4)
[]![IPv4 Exclusion section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-PAC-App-And-Bypass_1.png)
- Ensure that `0.0.0.0/0` is present in the IPv4 Inclusion section.
[See image.](#scenario-3-app-profile-5)
[]![IPv4 Inclusion section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-PAC-App-And-Bypass-2_2.png)
- Add a list of all internal domains in the Domain Exclusion field for which DNS requests are sent to internal DNS servers and not ZIA.
[See image.](#scenario-3-app-profile-6)
[]![Domain Exclusion in DNS](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-DNS-1_1.png)
- Ensure `*` is added to the Domain Inclusion field, so all external DNS requests are tunneled via ZIA.
[See image.](#scenario-3-app-profile-7)
[]![Domain inclusion in DNS section](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-3-App-Profile-DNS-2_2.png)
[]The detailed steps to deploy a ZIA Private Service Edge cluster are not covered in this article because they are well documented in the Zscaler Help Portal.
- [Deploying a Zscaler ZIA Private Service Edge](/zia/deploying-private-service-edge)
- [Deploying a Zscaler ZIA Virtual Service Edge](/zia/configuring-virtual-service-edge-clusters)
Create a new ZIA Location and associate the ZIA Private Service Edge cluster to that location and ensure that Force Authentication is enabled for that location to prevent traffic leakage with an open proxy.
[]In this scenario, Zscaler Client Connector forwards ZIA traffic across all ports and protocols using Z-Tunnel 2.0 via a third-party proxy. ZPA M-Tunnels and authentication traffic are forwarded using the Zscaler GVIP. The Zscaler GVIP, in turn, forwards the traffic to ZPA services in the Zscaler cloud.
![Zscaler forwards forwards ZIA traffic across all ports and protocols ](/downloads/zscaler-client-connector/interoperability/implementing-zscaler-client-connector-no-default-route-environments/Scenario-4-Forwarding-ZIA-traffic_1.png)
The configuration for this scenario is the same as [Scenario 3](/client-connector/implementing-zscaler-client-connector-no-default-route-environments) with the following exceptions regarding the third-party proxy:
- The Forwarding Profile for Z-Tunnel 2.0, when on-premises should only use TLS (instead of DTLS).
- The proxy must not attempt to authenticate requests destined for Zscaler IP addresses.
- The proxy must not attempt to authenticate requests destined for the IdP.
- The proxy must not attempt to re-resolve DNS based on SNI.
- The proxy must have TLS inspection disabled and tunnel all Zscaler and IdP bound requests.
- A separate ZIA Location (used for the ZIA Private Service Edge cluster in the previous step) isn't required.
- To account for situations where Zscaler Client Connector falls back to Z-Tunnel 1.0 at locations with a large number of users, consider using a Source-NAT IP address pool with multiple IP addresses and ensure that the load-balancing used with the pool uses sticky connections based on client IP addresses.