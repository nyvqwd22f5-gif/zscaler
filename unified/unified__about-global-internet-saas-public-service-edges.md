# About Global Internet & SaaS Public Service Edges
Source: https://help.zscaler.com/unified/about-global-internet-saas-public-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1495576.pdf

Zscaler has configured several Global, or Ghost, Internet & SaaS Public Service Edges across its clouds. These Public Service Edge addresses do not listen for traffic but are dummy addresses that every Public Service Edge knows about. They can be useful when working in no default route environments. To learn more, see [Implementing Zscaler in No Default Route Environments](/unified/implementing-zscaler-no-default-route-environments).
You can use the following IPs as Global Public Service Edge IPs:
- 185.46.212.88
- 185.46.212.89
- 185.46.212.90
- 185.46.212.91
- 185.46.212.92
- 185.46.212.93
- 185.46.212.97
- 185.46.212.98
No Default Route Example
In order to send packets to a Global Public Service Edge (185.46.212.88), a user's traffic with PAC configured will first resolve their PAC server address to http://pac.<Zscaler Cloud>.net/<your organization's domain>/No-Default-Route. Because the user is coming from a Public Service Edge IP via a tunnel, the PAC server returns the Zscaler Global IP.
Replace <Zscaler Cloud> with your cloud name.
![Diagram showing flow for using ZENs in no default route environments ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/zens/global-zscaler-enforcement-nodes-zens/global-zen-diagram-1.png?1602249562)
Use PAC files to direct the corporate user traffic to the Global Public Service Edge IP address.
Ensure that you route the traffic destined to the Global Public Service Edge IP address through a GRE or an IPSec tunnel.
![Diagram of using Global ZENs with no default route environments with DNAT](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/zens/global-zscaler-enforcement-nodes-zens/global-zen-diagram-2.png)
If the user is outside the corporate network coming from a non-Zscaler Public Service Edge IP and non-customer public IP, then the PAC would use the "${GATEWAY}" variable instead.
![Diagram showing how to use Global ZENs in no default route environments as a remote user](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/zens/global-zscaler-enforcement-nodes-zens/global-zen-diagram-3.png?1602249731)
In the above solution, each of the customer location configurations will remain the same, providing a simple method of deploying configuration without differences between locations. This minimizes configuration and deployment complexity. In addition, both internal and external scenarios can be accommodated by a single PAC.
Customers can also detect whether the user is present on-premises (by resolving an internal domain) and then return the Global Public Service Edge IP. A sample PAC file is given below:
var egressip = "${SRCIP}";
/*Assuming HQ source IP is 1.1.1.1*/
if (shExpMatch(egressip,"1.1.1.1")) {
/* User is in the HQ*/
return "PROXY 185.46.212.88:80;  PROXY ${COUNTRY_GATEWAY_FX}:80; PROXY ${COUNTRY_SECONDARY_GATEWAY_FX}:80   ";
}
return "PROXY ${COUNTRY_GATEWAY_FX}:80; PROXY ${COUNTRY_SECONDARY_GATEWAY_FX}:80";