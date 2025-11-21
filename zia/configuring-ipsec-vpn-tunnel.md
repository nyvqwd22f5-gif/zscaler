# Configuring an IPSec VPN Tunnel
Source: https://help.zscaler.com/zia/configuring-ipsec-vpn-tunnel
PDF: https://help.zscaler.com/pdf/com/en/1399026.pdf

You can configure an IPSec VPN tunnel between the gateway of your corporate network and a ZIA Public Service Edge. Zscaler recommends configuring two separate VPNs to two different ZIA Public Service Edges for high availability. If the primary IPSec VPN tunnel or if an intermediate connection goes down, all traffic is then rerouted through the backup IPSec VPN tunnel to the backup ZIA Public Service Edge.
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2 for all the configured tunnels.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Prerequisites
Ensure that you have the following information for each tunnel:
- IP address or hostname of your local gateway
- Shared secret
- [IP addresses or hostnames of the ZIA Public Service Edges](/zia/locating-the-hostnames-and-ip-addresses-your-zens)
Configuring an IPSec VPN Tunnel
To configure an IPSec VPN to a ZIA Public Service Edge:
- [Review the supported IPSec VPN parameters](/zia/about-ipsec-vpns#supported-ipsec-vpn-parameters)
- [Add VPN credentials in the Admin Portal](/zia/adding-vpn-credentials)
- [Link the VPN credentials to a location](/zia/configuring-locations)
- Configure your edge router or firewall to forward traffic to the Zscaler service. See the following configuration guides:
If you want to forward IPv6 traffic to ZIA, you must configure IPv6 traffic selectors for both IKEv1 and IKEv2 on your device. You must also ensure that [IPv6 support](/zia/configuring-ipv6-settings) is enabled for your organization and locations in the ZIA Admin Portal to forward IPv6 traffic.
- [IPSec VPN Configuration Guide for Cisco ASA 55xx](/zia/ipsec-vpn-configuration-guide-cisco-asa-5505)
- [IPSec VPN Configuration Guide for Cisco 881 ISR](/zia/ipsec-vpn-configuration-guide-cisco-881-isr)
- [IPSec VPN Configuration Guide for Juniper SRX 220](/zia/ipsec-vpn-configuration-guide-juniper-srx-220)
- [IPSec VPN Configuration Guide for Juniper SSG 20](/zia/ipsec-vpn-configuration-guide-juniper-ssg-20)
- [IPSec VPN Configuration Guide for FortiGate 60D Firewall](/zia/ipsec-vpn-configuration-guide-fortigate-60d-firewall)
- [IPSec VPN Configuration Guide for Palo Alto Networks Firewall](/zia/ipsec-vpn-configuration-guide-palo-alto-networks-firewall)
- [IPSec VPN Configuration Guide for SonicWall TZ 100](/zia/ipsec-vpn-configuration-guide-sonicwall-tz-100)
- [IPSec VPN Configuration Guide for SonicWall TZ ](/zia/ipsec-vpn-configuration-guide-sonicwall-tz-100)[350](/zia/ipsec-vpn-configuration-guide-sonicwall-tz-350)
To learn more, see the [Interoperability List](/zia/about-ipsec-vpns#zscaler-interoperability-list).
Integrating Zscaler with Check Point
To forward traffic from Check Point (GAIA version R80.30 or later), follow the steps recorded in the [Check Point documentation](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk174848&partition=Advanced&product=IPSec).
Check Point doesn't support Layer 7 health checks on third-party vendors.
Troubleshooting
You can go to **Analytics** > **Tunnel Insights** to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/zia/about-insights) and [About Insights Logs](/zia/about-insights-logs).