# Determining Optimal MTU for GRE or IPSec Tunnels
Source: https://help.zscaler.com/unified/determining-optimal-mtu-gre-or-ipsec-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1495281.pdf

A suboptimal maximum transmission unit (MTU) for your organization's GRE or IPSec tunnel results in severe performance degradation. This article teaches you how to determine the optimal MTU for your organization's tunnels.
Overview
When a user from your organization requests a website, the user's traffic first travels from your organization's edge network appliance (for example, a router or firewall) to an Internet & SaaS Public Service Edge via a primary or secondary GRE or IPSec tunnel. From there, the Internet & SaaS Public Service Edge sends the traffic out to the requested destination web server if it complies with your organization's security and compliance policies.
**![Diagram showing the travel of user traffic through the Zscaler ZIA Public Service Edge and GRE Tunnel to the user’s appliance.](/downloads/zia/traffic-forwarding/determining-the-optimal-mtu-for-gre-or-ipsec-tunnels/user_traffic_diagram_0.png)
**
When you configure a GRE or IPSec tunnel to the Internet & SaaS Public Service Edge, you must set an MTU for the tunnel. The MTU determines the maximum packet size that can be sent over that tunnel, and setting an optimal MTU here is crucial. A suboptimal MTU for the tunnel results in significantly poor performance for your users.
An optimal tunnel MTU is equal to or lower than the following key values:
- The Network Appliance MTU: The maximum total data per packet allowed by the edge network appliance from which the tunnel is built
- The Path MTU: The maximum total data per packet allowed by appliances that stand in the path between your network appliance and the Internet & SaaS Public Service Edge
If your tunnel MTU is larger than either value, the network or path appliance divides each packet into fragments. The appliance then places each fragment into its own packet, with its own header (The appliance thus must ensure that the maximum size of each fragment is its own MTU minus the header size.). The appliance also records in the header the following information so that the receiving appliance can properly identify the fragments and reassemble them into the original packet that was sent:
- **Total Length:** The size of the fragment
- **Identification:** The value that identifies the original packet the fragment belongs to.
- **More Fragments (MF):** A flag set to a 1 for all fragments except the last one, which is set to 0. A flag set to a 1 indicates to the receiving appliance that more fragments of this packet are coming, while a flag set to a 0 indicates that the appliance has received the last fragment of the packet.
- **Fragment Offset:** A value that helps the receiving appliance reassemble the packet fragments into the right sequence
When this fragmentation process occurs for each packet sent through your tunnel, your users experience significant performance issues.
To help avoid this scenario and ensure efficient packet transport, Zscaler recommends you complete the following tasks to determine and set the optimal MTU for your tunnels.
Configuration Instructions
- [1. Determine the Network Appliance MTU: the maximum total data per packet allowed by your network appliance](#determinemtu)
- [2. Determine the Maximum Segment Size (MSS): the maximum payload data per packet allowed by appliances that stand in the path between your network appliance and the Internet & SaaS Public Service Edge](#determinemss)
- [3. Calculate the path MTU value: the maximum total data per packet allowed by appliances that stand in the path between your network appliance and the Internet & SaaS Public Service Edge](#calculatemtu)
- [4. Compare your Network Appliance MTU and path MTU and set the lesser value as the MTU for your tunnel](#compare)
After you complete these tasks, the packets transported through your tunnel do not exceed the network appliance MTU or the path MTU. This helps ensure the most efficient transport for your packets and vastly improves performance.
[]Refer to your network appliance documentation to learn how to determine the appliance MTU. For example, if you have a Cisco appliance, you can find instructions [here](http://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst4500/12-2/25sg/configuration/guide/conf/sw_int.html#wp1049274).
You must determine the network appliance MTU before proceeding to the next step.
[]Before you begin, make sure you have the following information ready:
- Your network appliance MTU (referenced above)
- The IP addresses of the primary and secondary Internet & SaaS Public Service Edges to which your organization forwards traffic. [Click to learn how to locate this information for your organization.](#locate)
You can determine the MSS for your appliance using the following procedures based on the OS of the appliance:
- [For macOS](#mac-instructions)
- [For Windows](#windows-instructions)
- [For Linux](#linux-instructions)
[]The `-g` component of the ping command applies only to appliances running macOS.
- Execute the following ping command to the Internet & SaaS Public Service Edge or VPN host name using the appliance from which you're building the GRE or IPSec tunnels:
ping -g [network appliance MTU value minus 50] -G 1600 -h 10 -D [destination]
- This command allows you to discover a range for the MSS ⁠— that is, a range for the maximum payload data per packet allowed by appliances that stand in the path between your network appliance and the Internet & SaaS Public Service Edge. It directs your appliance to send to the destination ping sweeps ⁠— a sequence of packets that incrementally increase in size (by 10 bytes, in this case) ⁠— until the packets reach a specified size, or until the packets reach a point at which adding another 10 bytes makes the packets exceed the MSS.
- Following is a more detailed explanation of the command components and the values to use.
- `-g`: Packet size to start with when sending the ping sweep.
The value to plug in for g must equal the network appliance MTU minus 50. For example, if your network appliance MTU is 1450, the value is 1400.
- `-G`: Packet segment size to end with when sending the ping sweep.
For this command, use the value 1600.
- `-h`: Increment (in number of bytes) by which to increase the size of packets when sending the ping sweep.
For this command, use the value 10.
- `-D`: Prevents the tunnel from fragmenting packets. This is critical to ultimately discovering the MSS. Even if the appliance doesn't reach the G value (the size with which to end the ping sweep), because of this component, the appliance stops sending packets once it finds it has to fragment packets to keep them from exceeding the MSS. Without this limitation, the appliance simply continues to send packets by fragmenting them. For example, if the MSS is 1470, and your packet size was 1478, it fragments that packet into two packets so that the first is 1400 bytes, and the second packet 8 bytes.
- `[destination]`: This is the packet destination**.** These are the IP addresses of the primary and secondary Internet & SaaS Public Service Edges to which your organization forwards traffic.
- For example, if your organization's network appliance MTU is 1450, and your destination IP address is 10.10.10.13, your ping command is:
ping -g [1400] -G 1600 -h 10 -D 10.10.10.13
- When the appliance ends the ping sweeps, identify the packet size at which your pings stopped. You now know that the MSS is somewhere between this value and this value plus 10.
- Execute the same ping command, but change the values entered for -g and -h.
- For `-g`, enter the packet size at which your appliance stopped sending packets, as identified in step 2.
- For `-h`, use 1 so that the appliance increases the packet size by increments of 1.
ping -g [packet size at which appliance stopped sending packets, identified in step 2] -G 1600 -h 1 -D [destination]
- For example, if the value you identified in step 2 was 1450, your ping command is:
ping -g [1450] -G 1600 -h 1 -D 10.10.10.13
- Again, identify the packet size at which your pings stopped. That value is your MSS.
- [See an example.](#mac-command)
[]For appliances running Windows, execute the following bash loop command to perform a ping sweep:
for /l %i in(<Sweep Min Size, Sweep Count Increase By, Sweep Max Size>)do @ping -n 1 -w 100 <Ping Destination IP> -l %i -f.
- [See an example.](#windows-command)
The command:
for /l %i in (1400,1,1404) do @ping -n 1 -w 100 8.8.8.8 -l %i -f
The expected output of the command:
[]C:\Windows\system32>for /l %i in (1400,1,1404) do @ping -n 1 -w 8.8.8.8 -l %i -f
Pinging 8.8.8.8. with 1400 bytes of data:
Reply from 8.8.8.8: bytes=1400 time=6ms TTL=64
Ping statistics for 8.8.8.8:
Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 6ms, Maximum = 6ms, Average = 6ms
Pinging 8.8.8.8 with 1401 bytes of data:
Reply from 8.8.8.8: bytes=1401 time<1ms TTL=64
Ping statistics for 8.8.8.8:
Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms
Pinging 8.8.8.8 with 1402 bytes of data:
Reply from 8.8.8.8: bytes=1402 time<1ms TTL=64
Ping statistics for 8.8.8.8:
Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms
Pinging 8.8.8.8 with 1403 bytes of data:
Reply from 8.8.8.8: bytes=1403 time<1ms TTL=64
Ping statistics for 8.8.8.8:
Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms
[]For appliances running Linux, enter the following bash loop command to perform a ping sweep:
for size in {<Sweep Min Size>..<Sweep Max Size>..<Sweep Count Increase By>}; do ping -s $size -c 1 -M do <Ping Destination IP>; done
- [See an example.](#linux-command)
The command:
for size in {900..904..1}; do ping -s $size -c 1 -M do 8.8.8.8; done
The expected output of the command:
[]root@user1-ubuntu:~# for size in {900..904..1}; do ping -s $size -c 1 -M do 8.8.8.8; done
PING 8.8.8.8 (8.8.8.8) 900(928) bytes of data.
76 bytes from 8.8.8.8: icmp_seq=1 ttl=114 (truncated)
— 8.8.8.8 ping statistics —
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 22.078/22.078/22.078/0.000 ms
PING 8.8.8.8 (8.8.8.8) 901(929) bytes of data.
76 bytes from 8.8.8.8: icmp_seq=1 ttl=114 (truncated)
— 8.8.8.8 ping statistics —
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 17.283/17.283/17.283/0.000 ms
PING 8.8.8.8 (8.8.8.8) 902(930) bytes of data.
76 bytes from 8.8.8.8: icmp_seq=1 ttl=114 (truncated)
— 8.8.8.8 ping statistics —
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 22.515/22.515/22.515/0.000 ms
PING 8.8.8.8 (8.8.8.8) 903(931) bytes of data.
76 bytes from 8.8.8.8: icmp_seq=1 ttl=114 (truncated)
— 8.8.8.8 ping statistics —
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 16.494/16.494/16.494/0.000 ms
PING 8.8.8.8 (8.8.8.8) 904(932) bytes of data.
76 bytes from 8.8.8.8: icmp_seq=1 ttl=114 (truncated)
— 8.8.8.8 ping statistics —
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 8.494/8.494/8.494/0.000 ms
- []GRE Tunnels: If you're building GRE tunnels, Zscaler Support can provide you with the IP addresses of the primary and secondary Internet & SaaS Public Service Edges to which your organization must forward traffic. See [Configuring GRE Tunnels](/unified/configuring-gre-tunnels) for more information.
- IPSec Tunnels: If you're building IPSec tunnels, see [Locating the Hostnames and IP Addresses for Internet & SaaS Public Service Edges.](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges)
[]In this example:
- The network appliance MTU is 1330.
- The destination Internet & SaaS Public Service Edge IP address is 192.152.0.19.
In this case, execute the following ping command:
ping -g 1330 -G 1600 -h 10 -D 192.152.0.19
The appliance sent to the IP address 192.152.0.19 pings starts at a packet segment size of 1330 bytes, increasing the size by increments of 10.
The appliance stopped sending packets once they reached 1468 bytes (even before they reached the G value of 1600 bytes). Since the command specified that packets cannot be fragmented, the appliance stopped sending packets when adding another 10 bytes to 1468 makes the packet size exceed the MSS ⁠— in other words, the point at which the appliance begins fragmenting packets in order to transport them.
From this, you can deduce that the MSS is somewhere between 1468 and 1478.
PING 192.152.0.19 (10.152.0.19): (1330 ... 1600) data bytes
1338 bytes from 192.152.0.19: icmp_seq=0 ttl=121 time=418.883 ms
1348 bytes from 192.152.0.19: icmp_seq=1 ttl=121 time=441.258 ms
1358 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1368 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1378 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1388 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1398 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1408 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1418 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1428 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1438 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1448 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1458 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1468 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
ping: sendto: Message too long
ping: sendto: Message too long
ping: sendto: Message too long
With the information from the first ping command, execute the following second ping command:
ping -g 1468 -G 1478 -h 1 -D 192.152.0.19
From this result, you can conclude that your MSS is 1472 bytes.
PING 192.152.0.19 (10.152.0.19): (1330 ... 1600) data bytes
1468 bytes from 192.152.0.19: icmp_seq=0 ttl=121 time=418.883 ms
1469 bytes from 192.152.0.19: icmp_seq=1 ttl=121 time=441.258 ms
1470 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1471 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
1472 bytes from 192.152.0.19: icmp_seq=2 ttl=121 time=289.218 ms
ping: sendto: Message too long
ping: sendto: Message too long
ping: sendto: Message too long
[]With your MSS, you can now calculate the path MTU ⁠— the maximum packet size allowed by appliances that stand in the path between your network appliance and the Internet & SaaS Public Service Edge. The path MTU is the MSS value plus the values for the IP header (20 bytes) and the ICMP header (8 bytes). Use the following calculation.
Path MTU = MSS + 20 Bytes (IP Header) + 8 bytes (ICMP Header)
For example, if your MSS is 1472, your path MTU is 1500 (that is, 1472 + 20 + 8).
[]Compare your network appliance MTU and your path MTU. Subtract the tunnel header length from the lower of these two MTU values to set your tunnel MTU.
For example, if your network appliance MTU is 1500, and your path MTU is 1300, the value you set as the tunnel MTU is:
Tunnel MTU = Path MTU - Tunnel Header Length in bytes
For GRE tunnel, the header length = 24 bytes.
For IPsec tunnel, the header length is variable and can be up to 64 bytes.
This ensures that packets traveling through your GRE or IPSec tunnel do not exceed the packet size limitations of your network appliance or other appliances in the path between your network appliance and the Internet & SaaS Public Service Edge.
If you experience issues performing the tasks above, Zscaler recommends that you use a tunnel MTU of 1400.