# IPSec VPN Configuration Guide for Cisco ASA 55xx
Source: https://help.zscaler.com/zia/ipsec-vpn-configuration-guide-cisco-asa-55xx
PDF: https://help.zscaler.com/pdf/com/en/1399046.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article illustrates how to configure two IPSec VPN tunnels between a Cisco Adaptive Security Appliance (ASA) 55xx firewall and two ZIA Public Service Edges in the Zscaler cloud: a primary tunnel from the ASA appliance to a ZIA Public Service Edges in one data center and a secondary tunnel from the ASA appliance to a ZIA Public Service Edges in another data center.
![A network diagram showing the primary and secondary IPSec tunnels from a Cisco ASA to two Zscaler ZIA Public Service Edges.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-cisco-asa-55xx/IPSec_Cisco_ASA.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2 for all the configured tunnels.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Organizations typically forward all traffic destined for any port to the Zscaler service. Alternatively, you can limit the traffic that you forward to the service to HTTP and HTTPS traffic (traffic destined for port 80 and port 443). Regardless, tunneling provides visibility into the internal IP addresses, which can be used for the Zscaler security policies and logging.
Prerequisites
Before you configure the Zscaler service and the firewall, open a support ticket to provision the public source IP address. The public source IP address is only required if you want to set up an IPSec tunnel in phase one main mode.
Additionally, ensure that you have the [IP addresses of the ZIA Public Service Edges](/zia/locating-the-hostnames-and-ip-addresses-your-zens).
Configuring the IPSec VPN Tunnel in the ZIA Admin Portal
In this configuration example, the peers are using FQDN and a pre-shared key (PSK) for authentication.
To configure the IPSec VPN tunnels in the ZIA Admin Portal:
-
[Add the VPN Credential](/zia/adding-individual-vpn-credentials)
You need the FQDN and PSK when linking the VPN credentials to a location and creating the IKE gateways.
- [Link the VPN Credentials to a Location](/zia/how-do-i-add-location#vpn-credentials)
Configuring the IPSec VPN Tunnel on Cisco ASA 55xx
This article only covers the configuration details of IPSec VPN tunnels between the Cisco ASA 55xx firewall and the ZIA Public Service Edges. For any other specific information about Cisco ASA 55xx, refer to the [Cisco documentation](https://www.cisco.com/c/en/us/support/security/asa-5505-adaptive-security-appliance/model.html).
Choose your Cisco ASA 55xx version and configure it accordingly:
- [9.6](#IKEv2-9_6)
- [9.0](#IKEv2-9_0)
[]This section provides sample CLI commands for configuring two IPSec VPN tunnels on a Cisco ASA 55xx firewall running version 9.6. Refer to the Cisco documentation for information about the commands.
The following is the configuration for the two tunnels. Both tunnels must be configured at your gateway. Only a single tunnel is operational at any time. The second tunnel acts as a backup tunnel. The following text in red represents the values that your organization needs to provide, based on your network setup.
- <External Interface> - The external interface of the firewall
- <ZIA Public Service Edges VPN Map> - The external crypto map
- <Primary ZIA Public Service Edges IP Address> and <Backup ZIA Public Service Edges IP Address> - The IP addresses of the ZIA Public Service Edges
- <Flow Traffic Subnet> and <Flow Traffic Subnet Mask> - The superset of all the IP addresses that should flow through the tunnel
- <PSK> - The pre-shared key of the VPN credentials you created in the ZIA Admin Portal
- <Internal Server IP> - The public IP address of any internal web server hosted behind the organization’s firewall that needs to be accessed from outside
To configure the IPSec VPN tunnel on Cisco ASA 55xx firewall running version 9.6:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiations.
- [1. Configure IKE](#configure-ike-ikev2-9_6)
- [2. Create the Access Control List (ACL)](#acl-ikev2-9_6)
- [3. Configure IPSec](#ipsec-ikev2-9_6)
- [4. Configure the Port Filter](#port-filter-ikev2-9_6)
- [5. Configure Network Address Translation (NAT)](#nat-ikev2-9_6)
[]Establish a policy for the supported ISAKMP encryption, authentication Diffie-Hellman, lifetime, and key parameters. There is a global list of ISAKMP policies, each identified by sequence number**.**
This policy is defined as #1, which can conflict with an existing policy. If so, Zscaler recommends changing your existing policy number because the #1 policy must be the Zscaler policy. Otherwise, the tunnel negotiations fail.
crypto ikev2 policy 1
encryption aes-256
integrity sha
group 5 2
prf sha
lifetime seconds 86400
crypto ikev2 enable outside
The following group policy links the VPN tunnel protocol with the preceding crypto policy.
group-policy Zscaler-GRP internal
group-policy Zscaler-GRP attributes
vpn-tunnel-protocol ikev2
The tunnel group sets the pre-shared key that is used to authenticate the tunnel endpoints.
tunnel-group <Primary ZIA Public Service Edges IP Address> type ipsec-l2l
tunnel-group <Primary ZIA Public Service Edges IP Address> general-attributes
default-group-policy Zscaler-GRP
tunnel-group <Primary ZIA Public Service Edges IP Address> ipsec-attributes
peer-id-validate nocheck
ikev2 remote-authentication pre-shared-key <PSK>
ikev2 local-authentication pre-shared-key <PSK>
tunnel-group <Backup ZIA Public Service Edges IP Address> type ipsec-l2l
tunnel-group <Backup ZIA Public Service Edges IP Address> general-attributes
default-group-policy Zscaler-GRP
tunnel-group <Backup ZIA Public Service Edges IP Address> ipsec-attributes
peer-id-validate nocheck
ikev2 remote-authentication pre-shared-key <PSK>
ikev2 local-authentication pre-shared-key <PSK>
[]Access lists are configured to permit the creation of tunnels and to send relevant traffic over them.
Zscaler supports up to 8 Phase 2 SAs, as shown in the preceding example for version 9.6. One SA is used for the connection between the Cisco ASA’s public IP address and the ZIA Public Service Edges. You can then configure seven subnets to flow through the tunnel, forming the remaining seven SAs. If you want the traffic of more than seven subnets to flow through the tunnel, this example illustrates how to combine multiple subnets into one supernet, so there is only one allow statement for the access list attached to the cryptomap. In this example, the ASA sends all traffic down a single Phase 2 tunnel.
You should also create another object with a range of public IP addresses that should not flow through the tunnel. The example specifies an internally hosted Web server.
object network flow_traffic
subnet <Flow Traffic Subnet> <Flow Traffic Subnet Mask>*
*object network deny_traffic
host <Internal Server IP>
The following access list named Zscaler_MAP specifies all traffic that needs to be routed to the ZIA Public Service Edges. Traffic is transmitted through the tunnel to the ZIA Public Service Edges. Association with Child SA is done through the "crypto map" command. Deny traffic should deny all public IP ranges used for ‘NAT’ting.
access-list Zscaler_MAP extended deny ip object deny_traffic any
access-list Zscaler_MAP extended permit ip object flow_traffic any
[]The IPSec transform set defines the encryption, authentication, and IPSec mode parameters.
For Phase 2, Zscaler recommends using AES-GCM-based ciphers if you have purchased a separate subscription. If you do not have a separate subscription, Zscaler recommends using NULL encryption.
crypto ipsec ikev2 ipsec-proposal <Proposal Name>
protocol esp encryption aes-gcm-256
protocol esp integrity sha-256
The crypto map references the IPSec transform-set and further defines the Diffie-Hellman group and SA lifetime. You don't need to change the default SA lifetime value, which is 8 hours (28800 seconds), because it is the same as the Zscaler recommended value for Phase 2.
The mapping is created as #65000, which can conflict with an existing crypto map using the same number. If so, Zscaler recommends changing the mapping number to avoid conflicts. This crypto map ideally should be defined as the last map. If your corporation has RASVPN or SSLVPN crypto maps, then the Zscaler crypto map configuration should be just before them.
crypto map <ZIA Public Service Edges VPN Map> 65000 match address Zscaler_MAP
crypto map <ZIA Public Service Edges VPN Map> 65000 set peer <Primary ZIA Public Service Edges IP Address> <Backup ZIA Public Service Edges IP Address>
crypto map <ZIA Public Service Edges VPN Map> 65000 set ikev2 ipsec-proposal <Proposal Name>
crypto map <ZIA Public Service Edges VPN Map> interface <External Interface>
[]The Port Filter restricts traffic to specific ports that are permitted through the tunnels.
You can forward traffic destined for all ports. With this configuration, there is no need to create the following port or corresponding NAT rules. However, if you want to restrict traffic to ports 80 and 443, then create the following objects and link them to their corresponding NAT rules.
object service http
service tcp destination eq www
object service https
service tcp destination eq https
exit
[]Perform NAT on any traffic that bypasses the Zscaler service. Traffic that flows through the tunnel must maintain its source IP address. If you are forwarding only port 80 and 443 traffic to Zscaler, then establish the following NAT rules.
nat (inside,outside) source static flow_traffic flow_traffic service http http
nat (inside,outside) source static flow_traffic flow_traffic service https https
nat (inside,outside) after-auto source dynamic any interface
[]This section provides sample CLI commands for configuring two IPSec VPN tunnels on a Cisco ASA 55xx firewall running version 9.0. Refer to the Cisco documentation for information about the commands.
The following is the configuration for the two tunnels. Both tunnels must be configured at your gateway. Only a single tunnel is operational at any time. The second tunnel acts as a backup tunnel. The following text in red represents the values that your organization needs to provide, based on your network setup.
- <External Interface> - The external interface of the firewall
- <ZIA Public Service Edges VPN Map> - The external crypto map
- <Primary ZIA Public Service Edges IP Address> and <Backup ZIA Public Service Edges IP Address> - The IP addresses of the ZIA Public Service Edges
- <Flow Traffic Subnet> and <Flow Traffic Subnet Mask> - The superset of all the IP addresses that should flow through the tunnel
- <PSK> - The pre-shared key of the VPN credentials you created in the ZIA Admin Portal
- <Internal Server IP> - The public IP address of any internal web server hosted behind the organization’s firewall that needs to be accessed from outside
To configure the IPSec VPN tunnel on Cisco ASA 55xx firewall running version 9.0:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel configuration.
- [1. Configure IKE](#configure-ike-ikev2)
- [2. Create the Access Control List (ACL)](#acl-ikev2)
- [3. Configure IPSec](#ipsec-ikev2)
- [4. Configure the Port Filter](#port-filter-ikev2)
- [5. Configure Network Address Translation (NAT)](#nat-ikev2)
[]Establish a policy for the supported ISAKMP encryption, authentication Diffie-Hellman, lifetime, and key parameters. There is a global list of ISAKMP policies, each identified by sequence number**.**
This policy is defined as #1, which can conflict with an existing policy. If so, Zscaler recommends changing your existing policy number because the #1 policy must be the Zscaler policy. Otherwise, the tunnel negotiations fail.
crypto ikev2 policy 1
encryption aes-256
integrity sha
group 5 2
prf sha
lifetime seconds 86400
crypto ikev2 enable outside
The following group policy links the VPN tunnel protocol with the preceding crypto policy.
group-policy Zscaler-GRP internal
group-policy Zscaler-GRP attributes
vpn-tunnel-protocol ikev2
The tunnel group sets the pre-shared key that is used to authenticate the tunnel endpoints.
tunnel-group <Primary ZIA Public Service Edges IP Address> type ipsec-l2l
tunnel-group <Primary ZIA Public Service Edges IP Address> general-attributes
default-group-policy Zscaler-GRP
tunnel-group <Primary ZIA Public Service Edges IP Address> ipsec-attributes
peer-id-validate nocheck
ikev2 remote-authentication pre-shared-key <PSK>
ikev2 local-authentication pre-shared-key <PSK>
tunnel-group <Backup ZIA Public Service Edges IP Address> type ipsec-l2l
tunnel-group <Backup ZIA Public Service Edges IP Address> general-attributes
default-group-policy Zscaler-GRP
tunnel-group <Backup ZIA Public Service Edges IP Address> ipsec-attributes
peer-id-validate nocheck
ikev2 remote-authentication pre-shared-key <PSK>
ikev2 local-authentication pre-shared-key <PSK>
[]Access lists are configured to permit the creation of tunnels and to send relevant traffic over them.
Zscaler supports up to 8 Phase 2 SAs, as shown in the preceding example for version 9.0. One SA is used for the connection between the Cisco ASA’s public IP address and the ZIA Public Service Edges. You can then configure seven subnets to flow through the tunnel, forming the remaining seven SAs. If you want the traffic of more than seven subnets to flow through the tunnel, this example illustrates how to combine multiple subnets into one supernet, so there is only one allow statement for the access list attached to the cryptomap. In this example, the ASA sends all traffic down a single Phase 2 tunnel.
You should also create another object with a range of public IP addresses that should not flow through the tunnel. The example specifies an internally hosted Web server.
object network flow_traffic
subnet <Flow Traffic Subnet> <Flow Traffic Subnet Mask>*
*object network deny_traffic
host <Internal Server IP>
The following access list named Zscaler_MAP specifies all traffic that needs to be routed to the ZIA Public Service Edges. Traffic is transmitted through the tunnel to the ZIA Public Service Edges. Association with Child SA is done through the "crypto map" command. Deny traffic should deny all public IP ranges used for ‘NAT’ting.
access-list Zscaler_MAP extended deny ip object deny_traffic any
access-list Zscaler_MAP extended permit ip object flow_traffic any
[]The IPSec transform set defines the encryption, authentication, and IPSec mode parameters.
For Phase 2, Zscaler recommends using AES-GCM-based ciphers if you have purchased a separate subscription. If you do not have a separate subscription, Zscaler recommends using NULL encryption.
crypto ipsec ikev2 transform-set <Transform Set Name> esp-aes-gcm-256 esp-sha-hmac
The crypto map references the IPSec transform-set and further defines the Diffie-Hellman group and SA lifetime. You don't need to change the default SA lifetime value, which is 8 hours (28800 seconds), because it is the same as the Zscaler recommended value for Phase 2.
The mapping is created as #65000, which can conflict with an existing crypto map using the same number. If so, Zscaler recommends changing the mapping number to avoid conflicts. This crypto map ideally should be defined as the last map. If your corporation has RASVPN or SSLVPN crypto maps, then the Zscaler crypto map configuration should be just before them.
crypto map <ZIA Public Service Edges VPN Map> 65000 match address Zscaler_MAP
crypto map <ZIA Public Service Edges VPN Map> 65000 set peer <Primary ZIA Public Service Edges IP Address> <Backup ZIA Public Service Edges IP Address>
crypto map <ZIA Public Service Edges VPN Map> 65000 set ikev2 ipsec-proposal <Transform Set Name>
crypto map <ZIA Public Service Edges VPN Map> interface <External Interface>
[]The Port Filter restricts traffic to specific ports that are permitted through the tunnels.
You can forward traffic destined for all ports. With this configuration, there is no need to create the following port or corresponding NAT rules. However, if you want to restrict traffic to ports 80 and 443, then create the following objects and link them to their corresponding NAT rules.
object service http
service tcp destination eq www
object service https
service tcp destination eq https
exit
[]Perform NAT on any traffic that bypasses the Zscaler service. Traffic that flows through the tunnel must maintain its source IP address. If you are forwarding only port 80 and 443 traffic to Zscaler, then establish the following NAT rules.
nat (inside,outside) source static flow_traffic flow_traffic service http http
nat (inside,outside) source static flow_traffic flow_traffic service https https
nat (inside,outside) after-auto source dynamic any interface
Troubleshooting
In the ZIA Admin Portal, you can go to **Analytics** > **Tunnel Insights** to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/zia/about-insights) and [About Insights Logs](/zia/about-insights-logs).
On the Cisco router, you can use the following troubleshooting commands while setting up the tunnels. They apply to all tested ASA versions: 9.6 and 9.0. Note the values in green while troubleshooting.
- [Troubleshooting IKE](#troebleshooting-ike)
- [Troubleshooting the IPSec VPN Tunnels](#troubleshooting-ipsec-vpn-tunnel)
- [Verifying Packets Are Flowing Through the Tunnel](#verifying-packets)
[]Use the `show crypto isakmp sa` command to troubleshoot IKE. The following response shows an organization’s gateway with IKE configured correctly. The status should be UP-ACTIVE, which indicates that the tunnel is active.
IKEv2 SAs:
Session-id:59, Status:UP-ACTIVE, IKE count:1, CHILD count:1
Tunnel-id                 Local                Remote     Status         Role
2776614957       10.66.60.40/500       10.66.91.74/500      READY    INITIATOR
Encr: AES-GCM, keysize: 128, Hash: SHA96, DH Grp:14, Auth sign: PSK, Auth verify: PSK
Life/Active Time: 86400/403 sec
Child sa: local selector  192.168.202.0/0 - 192.168.202.255/65535
remote selector 0.0.0.0/443 - 255.255.255.255/443
ESP spi in/out: 0xf58c28b7/0x7eb079e7
[]Use the `show crypto ipsec stats` command to troubleshoot the IPSec VPN tunnels. The following response shows the number of active tunnels and a list of IPsec statistics.
IPsec Global Statistics
-----------------------
Active tunnels: 1
Previous tunnels: 59
Inbound
Bytes: 50159106
Decompressed bytes: 50159106
Packets: 37595
Dropped packets: 0
Replay failures: 0
Authentications: 37595
Authentication failures: 0
Decryptions: 0
Decryption failures: 0
TFC Packets: 0
Decapsulated fragments needing reassembly: 0
Valid ICMP Errors rcvd: 0
Invalid ICMP Errors rcvd: 0
Outbound
Bytes: 1110722
Uncompressed bytes: 1112122
Packets: 18861
Dropped packets: 1
Authentications: 18860
Authentication failures: 0
Encryptions: 0
Encryption failures: 0
TFC Packets: 0
Fragmentation successes: 0
Pre-fragmentation successses: 0
Post-fragmentation successes: 0
Fragmentation failures: 1
Pre-fragmentation failures: 1
Post-fragmentation failures: 0
Fragments created: 0
PMTUs sent: 1
PMTUs rcvd: 0
Protocol failures: 0
Missing SA failures: 0
System capacity failures: 0
Use the `show crypto ipsec sa` command to view the IPSec SAs. The following response shows a gateway with IKE configured correctly. Ensure that some packets are encapsulated and decapsulated. This indicates that traffic is flowing through the tunnel.
interface: outside
Crypto map tag: outside_map, seq num: 1, local addr: 10.66.60.40
access-list outside_cryptomap extended permit tcp 192.168.202.0 255.255.255.0 any eq https
local ident (addr/mask/prot/port): (192.168.202.0/255.255.255.0/6/0 - 65535)
remote ident (addr/mask/prot/port): (0.0.0.0/0.0.0.0/6/443)
current_peer: 10.66.91.74
#pkts encaps: 122, #pkts encrypt: 0, #pkts digest: 122
#pkts decaps: 198, #pkts decrypt: 0, #pkts verify: 198
#pkts compressed: 0, #pkts decompressed: 0
#pkts not compressed: 122, #pkts comp failed: 0, #pkts decomp failed: 0
#pre-frag successes: 0, #pre-frag failures: 0, #fragments created: 0
#PMTUs sent: 0, #PMTUs rcvd: 0, #decapsulated frgs needing reassembly: 0
#TFC rcvd: 0, #TFC sent: 0
#Valid ICMP Errors rcvd: 0, #Invalid ICMP Errors rcvd: 0
#send errors: 0, #recv errors: 0
local crypto endpt.: 10.66.60.40/500, remote crypto endpt.: 10.66.91.74/500
path mtu 1400, ipsec overhead 46(28), media mtu 1500
PMTU time remaining (sec): 0, DF policy: copy-df
ICMP error validation: disabled, TFC packets: disabled
current outbound spi: 7EB079E7
current inbound spi : F58C28B7
inbound esp sas:
spi: 0xF58C28B7 (4119603383)
transform: esp-null esp-md5-hmac no compression
in use settings ={L2L, Tunnel, PFS Group 2, IKEv2, }
slot: 0, conn_id: 372736, crypto-map: outside_map
sa timing: remaining key lifetime (kB/sec): (4008717/28569)
IV size: 0 bytes
replay detection support: Y
Anti replay bitmap:
0xFFFFFFFF 0xFFFFFFFF
outbound esp sas:
spi: 0x7EB079E7 (2125494759)
transform: esp-null esp-md5-hmac no compression
in use settings ={L2L, Tunnel, PFS Group 2, IKEv2, }
slot: 0, conn_id: 372736, crypto-map: outside_map
sa timing: remaining key lifetime (kB/sec): (3962871/28569)
IV size: 0 bytes
replay detection support: Y
Anti replay bitmap:
0x00000000 0x00000001
[]Use the `packet-tracer input inside tcp source_ip source_port dest_ip dest_port `command to simulate a packet from the inside interface with a specific source IP address and port and a specific destination IP address and port. The following response indicates whether the packet is flowing through the tunnel.
Phase: 1
Type: ACCESS-LIST
Subtype:
Result: ALLOW
Config:
Implicit Rule
Additional Information:
MAC Access list
Phase: 2
Type: ROUTE-LOOKUP
Subtype: input
Result: ALLOW
Config:
Additional Information:
in   0.0.0.0   0.0.0.0   outside
Phase: 3
Type: IP-OPTIONS
Subtype:
Result: ALLOW
Config:
Additional Information:
Phase: 4
Type: NAT
Subtype: host-limits
Result: ALLOW
Config:
nat (inside) 1 access-list inside_nat_outbound
match tcp inside any inside any range 1 79
dynamic translation to pool 1 (No matching global)
translate_hits = 0, untranslate_hits = 0
Additional Information:
Phase: 5
Type: HOST-LIMIT
Subtype:
Result: ALLOW
Config:
Additional Information:
Phase: 6
Type: VPN
Subtype: encrypt
Result: ALLOW
Config:
Additional Information:
Phase: 7
Type: VPN
Subtype: ipsec-tunnel-flow
Result: ALLOW
Config:
Additional Information:
Phase: 8
Type: IP-OPTIONS
Subtype:
Result: ALLOW
Config:
Additional Information:
Phase: 9
Type: FLOW-CREATION
Subtype:
Result: ALLOW
Config:
Additional Information:
New flow created with id 41542, packet dispatched to next module
Result:
input-interface: inside
input-status: up
input-line-status: up
output-interface: outside
output-status: up
output-line-status: up
Action: allow