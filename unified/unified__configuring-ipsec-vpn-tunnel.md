# Configuring an IPSec VPN Tunnel
Source: https://help.zscaler.com/unified/configuring-ipsec-vpn-tunnel
PDF: https://help.zscaler.com/pdf/com/en/1492891.pdf

You can configure an IPSec VPN tunnel between the gateway of your corporate network and an Internet & SaaS Public Service Edge. Zscaler recommends configuring two separate VPNs to two different Internet & SaaS Public Service Edges for high availability. If the primary IPSec VPN tunnel or if an intermediate connection goes down, all traffic is then rerouted through the backup IPSec VPN tunnel to the backup Internet & SaaS Public Service Edge.
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Prerequisites
Ensure that you have the following information for each tunnel:
- IP address or hostname of your local gateway
- Shared secret
- [IP addresses or hostnames of the Internet & SaaS Public Service Edges](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges)
Configuring an IPSec VPN Tunnel
To configure an IPSec VPN to an Internet & SaaS Public Service Edge:
- [Review the supported IPSec VPN parameters](/unified/understanding-ipsec-vpns)
- [Add VPN credentials in the Admin Portal](/unified/adding-vpn-credentials)
- [Link the VPN credentials to a location](/unified/configuring-locations)
-
Configure your edge router or firewall to forward traffic to the Zscaler service. See the following configuration guides:
If you want to forward IPv6 traffic to Internet & SaaS, you must configure IPv6 traffic selectors for both IKEv1 and IKEv2 on your device. You must also ensure that [IPv6 support](/unified/configuring-ipv6-settings) is enabled for your organization and locations in the Admin Portal to forward IPv6 traffic.
- [IPSec VPN Configuration Guide for Cisco ASA 55xx](/unified/ipsec-vpn-configuration-guide-cisco-asa-55xx)
- [IPSec VPN Configuration Guide for Cisco 881 ISR](/unified/ipsec-vpn-configuration-guide-cisco-881-isr)
- [IPSec VPN Configuration Guide for Juniper SRX](/unified/ipsec-vpn-configuration-guide-juniper-srx)
- [IPSec VPN Configuration Guide for Juniper SSG 20](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20)
- [IPSec VPN Configuration Guide for FortiGate 60D Firewall](/unified/ipsec-vpn-configuration-guide-fortigate-firewall)
- [IPSec VPN Configuration Guide for Palo Alto Networks Firewall](/unified/ipsec-vpn-configuration-guide-palo-alto-networks-firewall)
- [IPSec VPN Configuration Guide for SonicWall TZ 350](/unified/ipsec-vpn-configuration-guide-sonicwall-tz-350)
To learn more, see the [Interoperability List](/unified/understanding-ipsec-vpns#zscaler-interoperability-list).
Integrating Zscaler with Check Point
To forward traffic from Check Point (GAIA version R80.30 or later), follow the steps recorded in the [Check Point documentation](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk174848&partition=Advanced&product=IPSec).
Check Point doesn't support Layer 7 health checks on third-party vendors.
Troubleshooting
You can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).