# Best Practices for Deploying GRE Tunnels
Source: https://help.zscaler.com/unified/best-practices-deploying-gre-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1495321.pdf

Zscaler recommends that organizations use a combination of GRE tunneling, [PAC files](/unified/understanding-pac-files), [Surrogate IP](/unified/about-surrogate-ip), and Zscaler Client Connector to forward traffic to the Zscaler service. This article provides best practices for deploying GRE tunnels.
Ensure to alter the sample configuration values provided in this article to suit your deployment needs.
Deploying GRE Tunnels
The following are the best practices for deploying GRE:
- Zscaler recommends that you configure two GRE tunnels from an internal router behind the firewall to the Internet & SaaS Public Service Edges. To learn more, see [GRE Deployment Scenarios](/unified/gre-deployment-scenarios).
- Zscaler requires building primary and backup GRE tunnels from every internet egress location and, if applicable, from each internet service provider.
- Zscaler recommends using one of the following methods to provision a GRE tunnel to your account:
- [Submit a Zscaler Support ticket or contact Zscaler Support](/unified/configuring-gre-tunnels#step2-substep) to receive the GRE tunneling configuration.
- [Self-provision a GRE tunnel using the Admin Portal](/unified/self-provisioning-gre-tunnels).
- Zscaler recommends that you calculate the maximum transmission unit (MTU) and maximum segment size (MSS) values on the GRE tunnel based on the MTU and MSS configuration of the WAN interface. An incorrectly configured MTU results in higher fragmentation, leading to performance degradation.
- [See an example calculation.](#example-calculation)
[]In this example, the tunnel MTU and MSS values are calculated for a WAN interface that is 1,500 bytes.
WAN Interface MTU = 1,500
WAN Interface MSS = MTU (1,500) – IP (20) – TCP (20) = 1,460 (40 bytes TCP+IP Header)
GRE = 4 bytes header
GRE MTU = MTU (1,500) – IP (20) – GRE (4) = 1,476
GRE MSS = GRE MTU (1,476) – IP (20) – TCP (20) = 1,436
To learn more, refer to the [Cisco documentation](https://www.cisco.com/c/en/us/support/docs/ip/generic-routing-encapsulation-gre/25885-pmtud-ipfrag.html).
[![Diagram showing Primary and Secondary GRE Tunnels to different ZIA Public Service Edges from a corporate office](/downloads/zia/traffic-forwarding/gre/best-practices-deploying-gre-tunnels/ZIA-Best-Practices-Deploying-GRE-Tunnels-Diagram-1.png)
](/downloads/zia/traffic-forwarding/gre/best-practices-deploying-gre-tunnels/ZIA-Best-Practices-Deploying-GRE-Tunnels-Diagram-1.png)
Supported Bandwidth for GRE Tunnels
Zscaler supports a maximum bandwidth of 1 Gbps for each GRE tunnel if its internal IP addresses aren't behind NAT. Zscaler uses the internal IP addresses to load balance the GRE traffic over multiple servers. If the internal subnet is behind NAT, Zscaler can only support up to 250 Mbps of traffic for each tunnel. If your organization wants to forward more than 1 Gbps of traffic, Zscaler recommends configuring more GRE tunnels with different public source IP addresses. For example, if your organization forwards 2 Gbps of traffic, you can configure two primary GRE tunnels and two backup GRE tunnels. If your organization forwards 3 Gbps of traffic, you can configure three primary GRE tunnels and three backup GRE tunnels. When configuring multiple GRE tunnels, you should maintain client persistence to avoid issues because a server with persistence checking refuses connection to different egress IP addresses. You can use a Load Balancer (LB), ECMP, or other means to maintain persistence.
Zscaler recommends 1 Gbps per GRE tunnel because:
- A significant part of the internet infrastructure uses network links that are 1 Gbps. Multilink technologies such as Link Aggregation Control Protocol (LACP) still rely on aggregating multiple 1 Gbps interfaces. More than 1 Gbps of traffic from a single source IP address can result in a bottleneck.
- Internet peering is not 100% reliable, and managing traffic flows over 1 Gbps is difficult during any crisis or unforeseen issues.
Monitoring GRE Tunnels
Zscaler requires you to monitor your GRE tunnels so that failover between the primary and backup tunnels is triggered if a tunnel goes down.
GRE tunneling interfaces do not have a built-in mechanism for detecting when a tunnel is down. Enable GRE keepalives to serve as a basic detection mechanism. GRE keepalives can be configured on the physical or on the logical interface. The GRE keepalives monitor the interface, but not the service beyond the interface.
Zscaler recommends the configuration `keepalive 10 3` in which GRE keepalives are sent every 10 seconds and 3 retries.
To perform service monitoring, deploy Layer 7 health checks if your vendor supports it. If your vendor does not support Layer 7 health checks, deploy Layer 4 health checks, such as ICMP and PAC-based failover.
A majority of Cisco devices support Layer 7 health checks using IPSLA. Some Juniper devices support health checks using RPM (real-time performance monitoring).
Do not perform these Layer 7 health checks on commonly visited websites, such as www.google.com. Doing so results in Google placing Zscaler's IP addresses on their denylist and enforcing Google CAPTCHA to all users coming from those Zscaler IP addresses.
Perform HTTP Raw Request to the following URL: http://gateway.<Zscaler Cloud>.net/vpntest.
- [See sample IPSLA configuration for a Cisco router.](#cisco-ipsla-sample)
- []This example includes only a single test. You can configure multiple tests for your deployment if required.
- Configure latency thresholds based on the response time observed between a client location and the Zscaler data center. In the following example, `500` is the threshold Round Trip Time.
- The delay down command prevents frequent failovers due to short-lived flaps in the connection. This command ensures that the failover happens only when multiple connection drops are observed consecutively. The HTTP SLA probes are generated once in `60` seconds. In the following example, the delay time to mark an IP SLA test as down is configured as `120` seconds. The delay time to mark an object as up is configured as `180 `seconds. The router generates an HTTP SLA probe once every `60` seconds. This means that the router waits for two consecutive failures before marking the connection as down, and it waits for three consecutive successes before marking the connection as up.
track 1 ip sla 1
delay down 120 up 180
ip sla 1
http raw http://<Primary Global Public Service Edge IP>​​​​​
timeout 5000
threshold 500
http-raw-request
GET http://gateway.<Zscaler Cloud>.net/vpntest HTTP/1.0\r\n
User-Agent: Cisco IP SLA\r\n
end\r\n
\r\n
exit
ip sla schedule 1 life forever start-time now
track 2 ip sla 2
delay down 120 up 180
ip sla 2
http raw http://<Secondary Global Public Service Edge IP>
timeout 5000
threshold 500
http-raw-request
GET http://gateway.<Zscaler Cloud>.net/vpntest HTTP/1.0\r\n
User-Agent: Cisco IP SLA\r\n
end\r\n
\r\n
exit
ip sla schedule 2 life forever start-time now
- Replace <Zscaler Cloud> with your cloud name.
- Replace <Primary Global Public Service Edge IP>​​​​​ and <Secondary Global Public Service Edge IP> with Global Public Service Edge IP addresses. To learn more, see [About Global Internet & SaaS Public Service Edges](/unified/about-global-internet-saas-public-service-edges).
Configuring GRE Tunnel Failover
Zscaler requires you to connect tunnel monitoring to tunnel failover. When service monitoring is down, the primary tunnel should failover to the backup tunnel, and when monitoring is available, switch back to the primary tunnel.
- [See sample tunnel failover configuration for a Cisco router.](#sample-cisco-tunnel-failover)
[]route-map ZS-NET-PORT permit 10
match ip address ZS-NET-PORT
set ip next-hop verify-availability 172.18.56.162 1 track 1
set ip next-hop verify-availability 172.18.56.166 2 track 2