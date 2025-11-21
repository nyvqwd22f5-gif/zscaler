# GRE Configuration Guide for Cisco 881 ISR
Source: https://help.zscaler.com/unified/gre-configuration-guide-cisco-881-isr
PDF: https://help.zscaler.com/pdf/com/en/1495346.pdf

The illustration provided in this article uses sample values for the IP addresses. Replace these values with the actual IP addresses that are used in your deployment.
This example illustrates how to configure a GRE tunnel between a Cisco 881 ISR and Internet & SaaS Public Service Edges. As shown in the figure, two GRE tunnels are configured between the gateway WAN port, fa4, which has a static public IP address, <Tunnel Source IP> (e.g., 192.0.2.2), and two Internet & SaaS Public Service Edges in two different data centers with the IP, <Primary DC VIP> (e.g., 216.66.5.49) and <Secondary DC VIP> (e.g., 199.168.149.179).
**![Diagram of GRE tunnel between a Cisco 881 ISR and ZIA Public Service Edges](/downloads/zia/traffic-forwarding/gre/gre-configuration-example-cisco-881-isr/GRE_tunnel_Cisco.png)
**
The following text in red represents the IP address values that you need to know or provide, based on your network setup for the GRE tunnels:
- <Tunnel Source IP>: The IP address of the tunnel source which is from your organization (e.g., 192.0.2.2).
- <Internal IP Range>: The internal range of IP addresses assigned by Zscaler for your organization (e.g., 172.18.58.120-172.18.58.127).
- <Primary DC VIP>: The IP address of the primary tunnel destination, which is the GRE virtual IP address of Zscaler's primary data center (e.g., 216.66.5.49).
- <Primary Internal Router IP>: The internal virtual IP of the router (i.e., tunnel source) for the GRE tunnel associated with the primary data center (e.g., 172.18.58.121).
- <Primary Internal Internet & SaaS Public Service Edge IP>: The internal virtual IP of the tunnel destination on the primary data center (e.g., 172.18.58.122).
- <Secondary DC VIP>: The IP address of the secondary tunnel destination, which is the GRE virtual IP address of Zscaler's secondary data center (e.g., 199.168.149.179).
- <Secondary Internal Router IP>: The internal virtual IP of the router (i.e., tunnel source) for the GRE tunnel associated with the secondary data center (e.g., 172.18.58.125).
- <Secondary Internal Internet & SaaS Public Service Edge IP>: The internal virtual IP of the tunnel destination on the secondary data center (e.g., 172.18.58.126).
The router receives ingress traffic on ports fa0, fa1, fa2, and fa3. They forward internet traffic to the WAN gateway port, fa4, which uses the GRE tunnel interfaces tunnel 2700 and tunnel 2800 to send the internet traffic through the GRE tunnel to the Zscaler service. The router performs NAT on the other traffic that it sends directly to the internet. For more information on configuring a GRE tunnel, see [Configuring GRE Tunnels](/unified/configuring-gre-tunnels).
Configuring GRE Tunnel for Cisco 881 ISR
This guide covers only the configuration details of GRE tunnels between the Cisco 881 ISR and the Internet & SaaS Public Service Edges. For any other specific information about the Cisco 881 ISR, refer to the [Cisco documentation.](https://www.cisco.com/c/en/us/support/routers/881-secure-fast-ethernet-multi-mode-4g-lte-isr-router/model.html?dtid=osscdc000283)
Perform the following tasks to configure the GRE tunnels from a Cisco 881 ISR router running iOS version 15.1 to Internet & SaaS Public Service Edges in different data centers. Refer to the Cisco documentation for information about the commands provided in this procedure.
Ensure to alter the sample configuration values provided in this article to suit your deployment needs.
- [1. Configure GRE tunnels from the public IP address of the Cisco ISR.](#config-gre-tunnel)
- [2. Configure failover mechanisms to determine the operational state of the forwarding path to Zscaler.](#config-failover)
- [3. Configure traffic forwarding along with failover.](#traffic-forwarding)
[]The following example shows how to configure GRE tunnels from a public IP address:
- [See Important Notes](#points)
ip route <Primary DC VIP> 255.255.255.255 <Default GW>
ip route <Secondary DC VIP> 255.255.255.255 <Default GW>
!
interface Tunnel2700
description "Zscaler Primary Tunnel"
ip address <Primary Internal Router IP> 255.255.255.252
ip tcp adjust-mss 1436
keepalive 10 3
tunnel source <Tunnel Source IP>
tunnel destination <Primary DC VIP>
!
interface Tunnel2800
description "Zscaler Backup Tunnel"
ip address <Secondary Internal Router IP> 255.255.255.252
ip tcp adjust-mss 1436
keepalive 10 3
tunnel source <Tunnel Source IP>
tunnel destination <Secondary DC VIP>
!
- []Public IP addresses can be on an Ethernet interface or a loopback interface based on a pre-existing configuration.
- Set the TCP maximum segment size (MSS) to an appropriate value based on the MTU of the path between the client and the Zscaler data center. In this example, the MSS value is set to 1436.
- NAT is not configured on the interface in this example, so the Zscaler service can log internal IP addresses and you can configure sub-locations.
- This example includes static routes to the Zscaler GRE endpoints. This is an optional configuration based on your deployment.
- The tunnel names used in this example are arbitrary, and you can use different tunnel names in your configuration.
[]You must configure both GRE keepalives and IP SLA to enable GRE tunnel failover.
- [Configure GRE keepalives](#gre-keepalive)
- [Configure IP SLA](#ip-sla)
[]Configure GRE keepalives on the tunnel interfaces to monitor the reachability of the Zscaler cloud.
GRE keepalives are configured at the tunnel interface layer. You can modify the timer values to suit your failover requirements. If the GRE tunnel traverses NAT, keepalives fail. If the tunnel source interface has a private IP address, then the GRE keepalives don't work.
interface Tunnel2700
keepalive 10 3
!
interface Tunnel2800
keepalive 10 3
!
[]Configure IP SLA (synthetic testing) to monitor the performance of the path to Zscaler. IP SLA tests are used to track latency and availability. An HTTP-based SLA test is shown in the following example:
- [See Important Notes](#sla-points)
track 1 ip sla 1
delay down 120 up 180
ip sla 1
http raw http://<Primary Internal Internet & SaaS Public Service Edge IP>​​​​​
timeout 5000
threshold 500
http-raw-request
GET http://gateway.<Zscaler Cloud Name>.net/vpntest HTTP/1.0\r\n
User-Agent: Cisco IP SLA\r\n
end\r\n
\r\n
exit
ip sla schedule 1 life forever start-time now
track 2 ip sla 2
delay down 120 up 180
ip sla 2
http raw http://<Secondary Internal Internet & SaaS Public Service Edge IP>
timeout 5000
threshold 500
http-raw-request
GET http://gateway.<Zscaler Cloud Name>.net/vpntest HTTP/1.0\r\n
User-Agent: Cisco IP SLA\r\n
end\r\n
\r\n
exit
ip sla schedule 2 life forever start-time now
- []This example includes only a single test. You can configure multiple tests for your deployment if required.
- Configure latency thresholds based on the response time observed between a client location and the Zscaler data center.
- The delay down command prevents frequent failovers due to short-lived flaps in the connection. This command ensures that the failover happens only when multiple connection drops are observed consecutively. The HTTP SLA probes are generated once in 60 seconds. In the following example, the delay time to mark an IP SLA test as down is configured as 120 seconds. The delay time to mark an object as up is configured as 180 seconds. The router generates HTTP SLA probe once every 60 seconds. This means that the router waits for two consecutive failures before marking the connection as down, and it waits for three consecutive successes before marking the connection as up.
[]After configuring the tunnels, you need to route the internet-bound traffic through the tunnels so that Zscaler can provide security controls and policies. You can route the traffic using the following methods:
- [Using default routes](#default-route)
- [Using policy-based routing (PBR)](#pbr)
In Cisco iOS routers, policy-based routing (PBR) is implemented using route maps. Some Cisco routers forward PBR traffic in the software path instead of employing hardware forwarding, which leads to CPU spikes and performance issues. If you experience performance issues after implementing PBR, Zscaler recommends that you use IP route-based forwarding instead of PBR.
[]For a simple branch office architecture, you can use a simple default route to forward traffic. In this example, the default route is changed from directing traffic to the ISP gateway to forwarding internet-bound traffic to Zscaler.
- [See Important Notes](#default-route-points)
ip route 0.0.0.0 0.0.0.0 Tunnel2700 track 1
ip route 0.0.0.0 0.0.0.0 Tunnel2800 200
ip route <Primary DC VIP> 255.255.255.255 <Default Gateway>
ip route <Secondary DC VIP> 255.255.255.255 <Default Gateway>
- []Include more specific routes to direct Zscaler tunnel endpoints as they are required to properly route GRE packets.
- The default route is usually directed towards Zscaler without the use of VRFs or PBR.
- If VRFs are in use (Cisco sometimes refers to an architecture called Front Door VRF), you have to modify the default route to place it in the appropriate VRF.
[]If you want to forward internet traffic only from specific user subnets, ports, or protocols from your network to Zscaler, you can use PBR to selectively forward traffic to Zscaler. In this example, we use PBR to forward internet-bound traffic to Zscaler:
- [See Important Notes](#pbr-points)
ip access-list extended zscaler
deny   ip 10.96.0.0 0.0.0.255 10.0.0.0 0.255.255.255
deny   ip 10.96.0.0 0.0.0.255 172.16.0.0 0.15.255.255
deny   ip 10.96.0.0 0.0.0.255 192.168.0.0 0.0.0.255
permit ip 10.96.0.0 0.0.0.255 any
!
route-map zscaler-pbr permit 10
match ip address zscaler
set ip next-hop verify-availability <Primary Internal Internet & SaaS Public Service Edge IP> track 1
set ip next-hop verify-availability <Secondary Internal Internet & SaaS Public Service Edge IP> 2 track 2
!
- []The ACL in the example matches all IP traffic except RFC1918 destinations.
- In this example, the IP SLA tests are referenced in the PBR `next-hop` commands. This provides IP SLA-based failover, and forwards traffic only to the respective tunnel if the tracked objects referencing the IP SLA tests are successful.
Verifying GRE Tunnel Configuration on Cisco 881 ISR
In the Admin Portal, you can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured GRE tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).
On the Cisco router, you can perform the following verification steps to monitor and troubleshoot the GRE tunnels. These steps are applicable to both IOS 12.2.X and 15.X.
- [Verify GRE interface status and connectivity](#verify-gre-interface-status)
- [Verify IP SLA functionality](#verify-ipsla)
- [Verify routing status](#verify-routing-status)
- [Verify failover configuration](#verify-failover)
[]To verify GRE interface status and connectivity for the Primary Internal Internet & SaaS Public Service Edge IP, use the `ping` command to validate if the tunnel is up and the routing is correct. In this sample output, 172.18.58.122 is the Primary Internal Internet & SaaS Public Service Edge IP address.
ping 172.18.58.122
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.18.58.122, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/2/4 ms
To verify GRE interface status and connectivity for the Secondary Internal Internet & SaaS Public Service Edge IP, use the `ping` command to validate if the tunnel is up and the routing is correct. In this sample output,172.18.58.126 is the Secondary Internal Internet & SaaS Public Service Edge IP address.
ping 172.18.58.126
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 172.18.58.126, timeout is 2 seconds:
!!!!! Success rate is 100 percent (5/5), round-trip min/avg/max = 1/2/4 ms
Use the `show interfaces` command to verify the connectivity and status of the configured GRE interface. The output of the command indicates if the GRE tunnel is configured correctly and if it passes traffic. The tunnel status `line protocol is up` indicates that the tunnel is active. The following sample output indicates an active tunnel status, where 172.18.58.121 is the Primary Internal Router IP, 192.0.2.2 is the Tunnel Source IP, and 216.66.5.49 is the Primary DC VIP:
Tunnel2700 is up,  line protocol is up
Hardware is Tunnel
Description: "Zscaler Primary Tunnel"
Internet address is 172.18.58.121/30
MTU 17916 bytes, BW 100 Kbit/sec, DLY 50000 usec,
reliability 255/255, txload 1/255, rxload 1/255
Encapsulation TUNNEL, loopback not set
Keepalive set (10 sec), retries 3
Tunnel linestate evaluation up
Tunnel source 192.0.2.2, destination 216.66.5.49
Tunnel protocol/transport GRE/IP
Key disabled, sequencing disabled
Checksumming of packets disabled
Tunnel TTL 255, Fast tunneling enabled
Tunnel transport MTU 1476 bytes
Tunnel transmit bandwidth 8000 (kbps)
Tunnel receive bandwidth 8000 (kbps)
Last input 00:00:32, output 00:00:01, output hang never
Last clearing of "show interface" counters 1w5d
Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
Queueing strategy: fifo
Output queue: 0/0 (size/max)
5 minute input rate 0 bits/sec, 0 packets/sec
5 minute output rate 0 bits/sec, 0 packets/sec
213293 packets input, 258967182 bytes, 0 no buffer
Received 0 broadcasts (0 IP multicasts)
0 runts, 0 giants, 0 throttles
0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
250377 packets output, 17670798 bytes, 0 underruns
0 output errors, 0 collisions, 0 interface resets
0 unknown protocol drops
0 output buffer failures, 0 output buffers swapped out
The status line protocol is down indicates that the tunnel is inactive. The following sample output indicates the status of the tunnel after a keepalive failure, where 172.18.58.121 is the Primary Internal Router IP, 192.0.2.2 is the Tunnel Source IP, and 216.66.5.49 is the Primary DC VIP:
Tunnel2700 is up, line protocol is down
Hardware is Tunnel
Description: "Zscalertwo Primary Tunnel"
Internet address is 172.18.58.121/30
MTU 17916 bytes, BW 100 Kbit/sec, DLY 50000 usec,
reliability 255/255, txload 1/255, rxload 1/255
Encapsulation TUNNEL, loopback not set
Keepalive set (10 sec), retries 3
Tunnel linestate evaluation down - keepalive down
Tunnel source 192.0.2.2, destination 216.66.5.49
Tunnel protocol/transport GRE/IP
Key disabled, sequencing disabled
Checksumming of packets disabled
Tunnel TTL 255, Fast tunneling enabled
Tunnel transport MTU 1476 bytes
Tunnel transmit bandwidth 8000 (kbps)
Tunnel receive bandwidth 8000 (kbps)
Last input 00:06:32, output 00:00:01, output hang never
Last clearing of "show interface" counters 1w5d
Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
Queueing strategy: fifo
Output queue: 0/0 (size/max)
5 minute input rate 0 bits/sec, 0 packets/sec
5 minute output rate 0 bits/sec, 0 packets/sec
213293 packets input, 258967182 bytes, 0 no buffer
Received 0 broadcasts (0 IP multicasts)
0 runts, 0 giants, 0 throttles
0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
250414 packets output, 17672574 bytes, 0 underruns
0 output errors, 0 collisions, 0 interface resets
0 unknown protocol drops
0 output buffer failures, 0 output buffers swapped out
[]To verify and troubleshoot the IP SLA functionality:
Use the `show ip sla summary` command to check the latest operation summary. The output displays the Stats (i.e., the RTT in milliseconds), Return Code, and Last Run information.
IPSLAs Latest Operation Summary
Codes: * active, ^ inactive, ~ pending
ID           Type        Destination       Stats       Return      Last
(ms)        Code        Run
-----------------------------------------------------------------------
*1           http        172.17.27.2       RTT=619     OK          3 seconds ago
*2           http        172.17.27.6       RTT=1377    OK          3 seconds ago
Use the `show track` command and verify if the `State is Up` and if the latest operation return code is `OK.` The output shows the number of changes, the time stamp of the last change, and the latest RTT in milliseconds.
Track 1
IP SLA 1 state
State is Up
8 changes, last change 00:04:12
Delay down 130 secs
Latest operation return code: OK
Latest RTT (millisecs) 619
Tracked by:
Static IP Routing 0
Track 2
IP SLA 2 state
State is Up
10 changes, last change 3d00h
Delay down 130 secs
Latest operation return code: OK
Latest RTT (millisecs) 1377
Tracked by:
Static IP Routing 0
Use the `show ip sla configuration 1 `command to see configuration information.
IP SLAs Infrastructure Engine-III
Entry number: 1
Type of operation to perform: http
Target address/Source address: 172.17.27.2/0.0.0.0
Target port/Source port: 80/0
Type Of Service parameters: 0x0
Vrf Name:
HTTP Operation: raw
HTTP Server Version: 1.0
URL: http://172.17.27.2
Proxy:
Raw String(s):
GET http://gateway.zscalertwo.net/vpntest HTTP/1.0\r\n
User-Agent: Cisco IP SLA\r\n
end\r\n
\r\n
Cache Control: enable
Owner:
Tag:
Operation timeout (milliseconds): 5000
Schedule:
Operation frequency (seconds): 60  (not considered if randomly scheduled)
Next Scheduled Start Time: Start Time already passed
Group Scheduled : FALSE
Randomly Scheduled : FALSE
Life (seconds): Forever
Entry Ageout (seconds): never
Recurring (Starting Everyday): FALSE
Status of entry (SNMP RowStatus): Active
Threshold (milliseconds): 500
Distribution Statistics:
Number of statistic hours kept: 2
Number of statistic distribution buckets kept: 1
Statistic distribution interval (milliseconds): 20
History Statistics:
Number of history Lives kept: 0
Number of history Buckets kept: 15
History Filter Type: None
Use the `show ip sla statistics `command to see operation statistics information.
IPSLAs Latest Operation Statistics
IPSLA operation id: 1
Latest RTT: NoConnection/Busy/Timeout
Latest operation start time: *02:29:07.511 UTC Sat May 19 2012
Latest operation return code: Timeout
Number of successes: 0
Number of failures: 2
Operation time to live: Forever
IPSLA operation id: 2
Latest RTT: 1 milliseconds
Latest operation start time: *02:29:10.719 UTC Sat May 19 2012
Latest operation return code: OK
Number of successes: 2
Number of failures: 0
Operation time to live: Forever
[]For IP route configuration, use the `show ip route` command to verify the status of routing on the router.
Routing entry for 185.46.212.90/32
Known via "static", distance 1, metric 0 (connected)
Routing Descriptor Blocks:
* directly connected, via Tunnel2700
Route metric is 0, traffic share count is 1 Additional Information:
For route-map configuration, use the `show route-map` command to ensure that the router applies the route map to the appropriate traffic.
route-map zscaler-pbr, permit, sequence 10
Match clauses:
ip address (access-lists): 101
Set clauses:
interface Tunnel2700 Tunnel2800
Policy routing matches: 76258 packets, 17131024 bytes
[]Perform the following tests to verify your GRE tunnel failover functionality:
Go to [ip.zscaler.com](http://ip.zscaler.com)** **to verify the data center that receives the traffic.
- **Test 1**: Bring the primary tunnel interface down manually and verify if the traffic fails over to the secondary interface. Bring the primary tunnel interface up and verify if the traffic fails over to the primary interface.
- **Test 2**: Configure an incorrect value for your router's Zscaler GRE tunnel IP <Primary DC VIP> and verify if the traffic fails over to the secondary interface. Reconfigure your router with the correct value of the primary Zscaler GRE tunnel IP address and verify if the traffic fails over to the primary interface.
- **Test 3**: Block the GRE port on the upstream Firewall/Router ACL and verify if the traffic fails over to the secondary interface. Correct the ACL configuration and verify if the traffic fails over to the primary interface.
- **Test 4**: Decrease the threshold values on the primary tunnel IP SLA to trigger a timeout and verify if the traffic fails over to the secondary interface. Revert the threshold values to the original values and verify if the traffic fails over to the primary interface.