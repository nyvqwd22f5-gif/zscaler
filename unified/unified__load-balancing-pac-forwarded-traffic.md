# Load Balancing for PAC Forwarded Traffic
Source: https://help.zscaler.com/unified/load-balancing-pac-forwarded-traffic
PDF: https://help.zscaler.com/pdf/com/en/1495476.pdf

Zscaler supports up to 8 Virtual IP (VIP) addresses in a cluster and up to 64 clusters in a data center to ensure load balancing for the incoming traffic. Load balancing is typically based on the source IP address and the destination IP address. Many deployments have traffic-forwarding either through Zscaler Client Connector or directly via a browser. If your organization uses NAT, the traffic originating from multiple users has the same public IP address.
Many organizations use only Zscaler Client Connector as the traffic forwarding method. In such cases, a large volume of users from one physical location are behind an edge gateway with a single egress IP address. This means that all the users have the same source IP address. So, the typical load balancing calculation leads all the users from the organization to connect to the same Internet & SaaS Public Service Edge in the data center. This results in the overloading of a single Service Edge instance in the data center, thereby causing performance issues.
To evenly distribute PAC forwarded traffic over multiple Service Edge instances in a data center, the PAC server returns multiple VIPs within the same data center as the destination IP address. When the clients with the same source IP address are assigned with different VIPs as the destination IP addresses, they are load-balanced to different Service Edge instances. This ensures even distribution of traffic from the same source IP address over multiple Service Edge instances.
The PAC server uses the [`${GATEWAY_FX}`](/unified/writing-pac-file#dynamic-gateway-tokens) and [`${GATEWAY_Fn}`](/unified/writing-pac-file#gateway-index-tokens) variables, (where n can take up to 8 values from 0 to 7) in the Zscaler-hosted PAC file to assign the VIPs for the incoming traffic:
Load balancing for PAC forwarded traffic can be classified as:
- [Load Balancing for Zscaler Client Connector Traffic](#zapp)
- [Load Balancing for Non-Zscaler Client Connector Traffic](#non-zapp)
[]For Zscaler Client Connector users, the PAC server allocates VIPs for devices through the [`${GATEWAY_FX}`](/unified/writing-pac-file#dynamic-gateway-tokens) variable in the Zscaler-hosted PAC file. When the Zscaler Client Connector connects to the PAC server to download a PAC file, it sends a unique device identifier with the request. The PAC server allocates one of the VIPs to the device based on the device identifier received from the HTTP request using the [`${GATEWAY_FX}`](/unified/writing-pac-file#dynamic-gateway-tokens) variable. When the same device connects again to download the PAC file, the PAC server allocates the same VIP that was allocated to the device earlier based on its unique identifier.
[]Each data center can have up to 8 unique VIPs assigned to it. For non-Zscaler Client Connector users, admins can leverage the [`${GATEWAY_Fn}`](/unified/writing-pac-file#gateway-index-tokens) variable in the Zscaler-hosted PAC file to evenly distribute the clients across multiple VIPs.
[`${GATEWAY_Fn}`](/unified/writing-pac-file#gateway-index-tokens) represents 8 different variables starting from `${GATEWAY_F0}` to `${GATEWAY_F7}` that are used to pick an available VIP from the data center. The PAC server returns the VIP value based on the variable used in the PAC file. If the number of VIPs assigned to a data center is less than 8, then the PAC server allocates the available VIPs to all 8 variables in a round-robin fashion.
The following image illustrates how the VIPs are mapped to the variables based on the number of available VIPs in a data center:
[See image.](#vip-table)
Zscaler recommends the following PAC file format for non-Zscaler Client Connector users to leverage the multiple VIP features using a single PAC file.
- [See recommended PAC file format for non-Zscaler Client Connector users](#recommended-pac)
[]![VIP Mapping](/downloads/zscaler-tech-pubs-style-guide/draft-articles/load-balancing-guide-pac-forwarded-traffic/vip-mapping.png)
[]`splitPublicTraffic()` splits the client private IP address into its corresponding octets and performs last `octet%8` to get the index between 0 to 7. This function file uses multiple PAC functions to evenly distribute client traffic over the 8 PAC variables. Initially, the PAC file uses the `myIpAddress()` function to determine the client source IP address. Then, it extracts the last octet of the client IP. This number is divided by 8 and the remainder is used to assign one of the 8 gateway variables.
function splitPublicTraffic() {
var myip = myIpAddress();        /* get the client’s Private IP address */
var ipbytes = myip.split(".");    /* split the IP into its octets and store in an array */
var lastoctet = parseInt(ipbytes[3], 10);
switch (lastoctet % 8) {        /* last octet % 8 returns the index to use */
case 0:
return "PROXY ${GATEWAY_F0}:80; PROXY ${SECONDARY_GATEWAY_F0}:80; DIRECT";
case 1:
return "PROXY ${GATEWAY_F1}:80; PROXY ${SECONDARY_GATEWAY_F1}:80; DIRECT";
case 2:
return "PROXY ${GATEWAY_F2}:80; PROXY ${SECONDARY_GATEWAY_F2}:80; DIRECT";
case 3:
return "PROXY ${GATEWAY_F3}:80; PROXY ${SECONDARY_GATEWAY_F3}:80; DIRECT";
case 4:
return "PROXY ${GATEWAY_F4}:80; PROXY ${SECONDARY_GATEWAY_F4}:80; DIRECT";
case 5:
return "PROXY ${GATEWAY_F5}:80; PROXY ${SECONDARY_GATEWAY_F5}:80; DIRECT";
case 6:
return "PROXY ${GATEWAY_F6}:80; PROXY ${SECONDARY_GATEWAY_F6}:80; DIRECT";
case 7:
return "PROXY ${GATEWAY_F7}:80; PROXY ${SECONDARY_GATEWAY_F7}:80; DIRECT";
}
}
function FindProxyForURL(url, host) {
var privateIP = /^(0|10|127|192\.168|172\.1[6789]|172\.2[0-9]|172\.3[01]|169\.254|192\.88\.99)\.[0-9.]+$/;
var resolved_ip = dnsResolve(host);
/* Don't send non-FQDN or private IP auths to us */
if (isPlainHostName(host) || isInNet(resolved_ip, "192.0.2.0","255.255.255.0") || privateIP.test(resolved_ip))
return "DIRECT";
/* FTP goes directly */
if (url.substring(0,4) == "ftp:")
return "DIRECT";
/* test with ZPA*/
if (isInNet(resolved_ip, "100.64.0.0","255.255.0.0"))
return "DIRECT";
/* Updates are directly accessible */
if (((localHostOrDomainIs(host, "trust.zscaler.com")) ||
(localHostOrDomainIs(host, "trust.zscaler.net")) ||
(localHostOrDomainIs(host, "trust.zscalerone.net")) ||
(localHostOrDomainIs(host, "trust.zscalertwo.net")) ||
(localHostOrDomainIs(host, "trust.zscalerthree.net")) ||
(localHostOrDomainIs(host, "trust.zscalergov.net")) ||
(localHostOrDomainIs(host, "trust.zsdemo.net")) ||
(localHostOrDomainIs(host, "trust.zscloud.net")) ) &&
(url.substring(0,5) == "http:" || url.substring(0,6) == "https:"))
return "DIRECT";
/* use zscaler proxy */
return splitPublicTraffic();
}