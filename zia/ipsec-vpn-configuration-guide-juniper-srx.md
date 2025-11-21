# IPSec VPN Configuration Guide for Juniper SRX
Source: https://help.zscaler.com/zia/ipsec-vpn-configuration-guide-juniper-srx
PDF: https://help.zscaler.com/pdf/com/en/1399071.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article illustrates how to configure two IPSec VPN tunnels from a Juniper SRX 300 firewall to two ZIA Public Service Edges. As shown in the following diagram, the corporate office sends its internal traffic on the web interfaces `ge-0/0/1.0` through `ge-0/0/7.0` in the trust zone. The device forwards outbound traffic through `ge-0/0/0.0`. It sends internet-bound traffic through the tunnel interface `st0`, which has two sub-interfaces `unit 0` and `unit 1.`
![A network diagram showing the primary and backup IPSec tunnels from a Juniper SRX to two Zscaler ZIA Public Service Edges.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-juniper-srx/zia-traffic-forwarding-ipsec-vpn-juniper-srx.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2 for all the configured tunnels.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Dead Peer Detection (DPD) and VPN monitoring must be enabled so the firewall can detect if one VPN goes offline and moves the internet-bound traffic to the other VPN. In this configuration example, a route-based VPN is configured, where two tunnels are created and then inserted as the default routes in the routing table.
Prerequisites
Ensure you have the [Virtual IP (VIP) addresses of the ZIA Public Service Edges](/zia/locating-hostnames-and-ip-addresses-zia-public-service-edges).
Configuring the IPSec VPN Tunnel in the ZIA Admin Portal
In this configuration example, the peers are using an FQDN and a pre-shared key (PSK) for authentication.
To configure the IPSec VPN tunnels in the ZIA Admin Portal:
- [Add the VPN Credential](/zia/how-do-i-add-individual-vpn-credentials)
You need the FQDN and PSK when linking the VPN credentials to a location and creating the IKE gateways.
- [Link the VPN Credentials to a Location](/zia/how-do-i-add-location)
Configuring the IPSec VPN Tunnel on Juniper SRX
This article covers only the configuration details of IPSec VPN tunnels between the Juniper SRX 300 firewall and the ZIA Public Service Edges. For any other specific information about Juniper SRX 300, refer to the [Juniper SRX documentation](https://www.juniper.net/documentation/product/us/en/srx300/).
This section provides sample commands for configuring an IPSec VPN tunnel interface on a Juniper SRX 300 router running version 19.2R2.7. To learn more about the commands, refer to the [Juniper SRX documentation](https://www.juniper.net/documentation/us/en/software/junos/vpn-ipsec/topics/topic-map/security-ipsec-vpn-configuration-overview.html#d127e127). You must have a Juniper SRX 300 router running version 19.2R2.7 or later to configure IKEv2.
You must provide the following information to configure the tunnels:
- <Primary VIP Address> and <Backup VIP Address>: The VIP addresses of the ZIA Public Service Edges.
- <FQDN>: The FQDN of the VPN credentials you created in the ZIA Admin Portal.
- <Pre-Shared Key>: The pre-shared key (PSK) of the VPN credentials you created in the ZIA Admin Portal.
To configure the IPSec VPN Tunnel on Juniper SRX:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiation.
- [1. Configure the tunnel interfaces.](#ikev2-tunnel-interfaces)
- [2. Configure the security zones.](#ikev2-security-zones)
- [3. Configure the security policy.](#ikev2-security-policy)
- [4. Configure static routing.](#ikev2-static-routing)
- [5. Configure the IKE proposal.](#ikev2-ike-proposal)
- [6. Configure the IKE policy.](#ikev2-ike-policy)
- [7. Configure the IKE gateways](#ikev2-ike-gateways).
- [8. Configure IPSec VPN monitoring.](#ikev2-vpn-monitoring)
- [9. Configure the IPSec proposal.](#ikev2-ipsec-proposal)
- [10. Configure the IPSec policy.](#ikev2-ipsec-policy)
- [11. Configure the IPSec VPNs.](#ikev2-ipsec-vpns)
- [12. Configure source Network Address Translation (NAT)](#ikev2-source-nat).
**Configuring ECMP Flow-Based Forwarding on Juniper SRX (Optional)**
You can optionally configure ECMP flow-based forwarding on your Juniper SRX router to enable load balancing for your tunnels if multiple virtual IP addresses are configured in your Zscaler data center for the VPN tunnels.
- [See sample configuration commands](#sample-commands)
You must configure an IPSec tunnel with Zscaler before configuring ECMP Flow-Based Forwarding on the Juniper SRX 300.
[]The following are the sample commands for configuring ECMP flow-based forwarding with four IPSec tunnels to Zscaler on the Juniper SRX 300 router running version 19.2R2.7. To learn more about the commands, refer to the [Juniper SRX documentation](https://www.juniper.net/documentation/en_US/junos/topics/example/routing-policy-security-ecmp-flow-based-forwarding-configuring.html).
set interfaces st0 unit 0 family inet
set interfaces st0 unit 1 family inet
set interfaces st0 unit 2 family inet
set interfaces st0 unit 3 family inet
set routing-options static route 0.0.0.0/0 next-hop st0.0
set routing-options static route 0.0.0.0/0 next-hop st0.1
set routing-options static route 0.0.0.0/0 next-hop st0.2
set routing-options static route 0.0.0.0/0 next-hop st0.3
set routing-options forwarding-table export trust-to-untrust
set policy-options policy-statement trust-to-untrust to interface st0.0
set policy-options policy-statement trust-to-untrust to interface st0.1
set policy-options policy-statement trust-to-untrust to interface st0.2
set policy-options policy-statement trust-to-untrust to interface st0.3
set policy-options policy-statement trust-to-untrust then load-balance per-packet
set security ike proposal zvpn authentication-method pre-shared-keys
set security ike proposal zvpn dh-group group2
set security ike proposal zvpn authentication-algorithm sha1
set security ike proposal zvpn lifetime-seconds 86400
set security ike policy ikepolicy1 mode aggressive
set security ike policy ikepolicy1 proposals zvpn
set security ike policy ikepolicy1 pre-shared-key ascii-text "$9$gqoaUkqf36AGD39"
set security ike gateway vpn1 ike-policy ikepolicy1
set security ike gateway vpn1 address <Primary VIP1 Address>
set security ike gateway vpn1 dead-peer-detection always-send
set security ike gateway vpn1 dead-peer-detection interval 10
set security ike gateway vpn1 dead-peer-detection threshold 5
set security ike gateway vpn1 nat-keepalive 20
set security ike gateway vpn1 external-interface ge-0/0/0
set security ike gateway vpn2 ike-policy ikepolicy1
set security ike gateway vpn2 address <Primary VIP2 Address>
set security ike gateway vpn2 dead-peer-detection always-send
set security ike gateway vpn2 dead-peer-detection interval 10
set security ike gateway vpn2 dead-peer-detection threshold 5
set security ike gateway vpn2 nat-keepalive 20
set security ike gateway vpn2 external-interface ge-0/0/0
set security ike gateway vpn3 ike-policy ikepolicy1
set security ike gateway vpn3 address <Primary VIP3 Address>
set security ike gateway vpn3 dead-peer-detection always-send
set security ike gateway vpn3 dead-peer-detection interval 10
set security ike gateway vpn3 dead-peer-detection threshold 5
set security ike gateway vpn3 nat-keepalive 20
set security ike gateway vpn3 external-interface ge-0/0/0
set security ike gateway vpn4 ike-policy ikepolicy1
set security ike gateway vpn4 address <Primary VIP4 Address>
set security ike gateway vpn4 dead-peer-detection always-send
set security ike gateway vpn4 dead-peer-detection interval 10
set security ike gateway vpn4 dead-peer-detection threshold 5
set security ike gateway vpn4 nat-keepalive 20
set security ike gateway vpn4 external-interface ge-0/0/0
set security ipsec vpn-monitor-options interval 30
set security ipsec vpn-monitor-options threshold 5
set security ipsec proposal test protocol esp
set security ipsec proposal test authentication-algorithm hmac-sha1-96
set security ipsec proposal test lifetime-seconds 3600
set security ipsec policy vpnp1 proposal-set standard
set security ipsec vpn ikevpn bind-interface st0.0
set security ipsec vpn ikevpn df-bit set
set security ipsec vpn ikevpn vpn-monitor optimized
set security ipsec vpn ikevpn vpn-monitor source-interface ge-0/0/0
set security ipsec vpn ikevpn vpn-monitor destination-ip gateway.<Zscaler cloud>.net
set security ipsec vpn ikevpn ike gateway vpn1
set security ipsec vpn ikevpn ike idle-time 4000
set security ipsec vpn ikevpn ike ipsec-policy vpnp1
set security ipsec vpn ikevpn establish-tunnels immediately
set security ipsec vpn ikevpnsec bind-interface st0.1
set security ipsec vpn ikevpnsec df-bit set
set security ipsec vpn ikevpnsec vpn-monitor optimized
set security ipsec vpn ikevpnsec vpn-monitor source-interface ge-0/0/0
set security ipsec vpn ikevpnsec vpn-monitor destination-ip <Primary VIP1 Address>
set security ipsec vpn ikevpnsec ike gateway vpn2
set security ipsec vpn ikevpnsec ike idle-time 4000
set security ipsec vpn ikevpnsec ike ipsec-policy vpnp1
set security ipsec vpn ikevpnsec establish-tunnels immediately
set security ipsec vpn ikevpn3 bind-interface st0.2
set security ipsec vpn ikevpn3 df-bit set
set security ipsec vpn ikevpn3 vpn-monitor optimized
set security ipsec vpn ikevpn3 vpn-monitor source-interface ge-0/0/0
set security ipsec vpn ikevpn3 vpn-monitor destination-ip <Primary VIP1 Address>
set security ipsec vpn ikevpn3 ike gateway vpn3
set security ipsec vpn ikevpn3 ike idle-time 4000
set security ipsec vpn ikevpn3 ike ipsec-policy vpnp1
set security ipsec vpn ikevpn3 establish-tunnels immediately
set security ipsec vpn ikevpn4 bind-interface st0.3
set security ipsec vpn ikevpn4 df-bit set
set security ipsec vpn ikevpn4 vpn-monitor optimized
set security ipsec vpn ikevpn4 vpn-monitor source-interface ge-0/0/0
set security ipsec vpn ikevpn4 vpn-monitor destination-ip gateway.<Zscaler cloud>.net
set security ipsec vpn ikevpn4 ike gateway vpn4
set security ipsec vpn ikevpn4 ike idle-time 4000
set security ipsec vpn ikevpn4 ike ipsec-policy vpnp1
set security ipsec vpn ikevpn4 establish-tunnels immediately
set security flow tcp-mss ipsec-vpn mss 1300
set security nat source rule-set nat-out from zone trust
set security nat source rule-set nat-out to zone untrust
set security nat source rule-set nat-out rule interface-nat match source-address 192.168.0.0/16
set security nat source rule-set nat-out rule interface-nat match destination-address 0.0.0.0/0
set security nat source rule-set nat-out rule interface-nat then source-nat interface
set security policies from-zone trust to-zone untrust policy trust-to-untrust match source-address any
set security policies from-zone trust to-zone untrust policy trust-to-untrust match destination-address any
set security policies from-zone trust to-zone untrust policy trust-to-untrust match application any
set security policies from-zone trust to-zone untrust policy trust-to-untrust then permit
set security policies from-zone trust to-zone untrust policy any-permit match source-address any
set security policies from-zone trust to-zone untrust policy any-permit match destination-address any
set security policies from-zone trust to-zone untrust policy any-permit match application any
set security policies from-zone trust to-zone untrust policy any-permit then permit
set security policies from-zone trust to-zone vpn policy vpn-tr-vpn match source-address local-net
set security policies from-zone trust to-zone vpn policy vpn-tr-vpn match destination-address remote-net
set security policies from-zone trust to-zone vpn policy vpn-tr-vpn match application any
set security policies from-zone trust to-zone vpn policy vpn-tr-vpn then permit
set security policies from-zone vpn to-zone trust policy vpn-vpn-tr match source-address remote-net
set security policies from-zone vpn to-zone trust policy vpn-vpn-tr match destination-address local-net
set security policies from-zone vpn to-zone trust policy vpn-vpn-tr match application any
set security policies from-zone vpn to-zone trust policy vpn-vpn-tr then permit
set security zones security-zone trust address-book address local-net 192.168.0.0/16
set security zones security-zone trust host-inbound-traffic system-services all
set security zones security-zone trust host-inbound-traffic protocols all
set security zones security-zone trust interfaces vlan.0
set security zones security-zone untrust screen untrust-screen
set security zones security-zone untrust host-inbound-traffic system-services ike
set security zones security-zone untrust interfaces ge-0/0/0.0 host-inbound-traffic system-services dhcp
set security zones security-zone untrust interfaces ge-0/0/0.0 host-inbound-traffic system-services tftp
set security zones security-zone untrust interfaces ge-0/0/0.0 host-inbound-traffic system-services all
set security zones security-zone vpn address-book address remote-net 0.0.0.0/0
set security zones security-zone vpn interfaces st0.0
set security zones security-zone vpn interfaces st0.1
set security zones security-zone vpn interfaces st0.2
set security zones security-zone vpn interfaces st0.3
Troubleshooting
In the ZIA Admin Portal, you can go to Analytics > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/zia/about-insights) and [About Insights Logs](/zia/about-insights-logs).
In Junos OS, you can use the following CLI commands to monitor and troubleshoot the IPSec VPN tunnels.
- [Viewing the Routing Table](#routingtable)
- [Viewing the Phase 1 SA](#ViewPhase1SA)
- [Viewing the Phase 2 SA](#ViewPhase2SA)
- [Clearing the Phase 2 SA](#ClearPhase2SA)
[]Use the `show route `command to view the routing table. Ensure that `st0.0` and `st0.1` routes are in the routing table.
inet.0: 6 destinations, 7 routes (6 active, 0 holddown, 0 hidden)
+ = Active Route, - = Last Active, * = Both
0.0.0.0/0          *[Static/5] 00:28:59
via st0.0
> via st0.1
[Access-internal/12] 00:28:33
> to 10.10.120.1 via ge-0/0/0.0
10.10.104.0/24     *[Static/5] 00:28:33
> to 10.10.120.1 via ge-0/0/0.0
10.10.120.0/24     *[Direct/0] 00:28:33
> via ge-0/0/0.0
10.10.120.43/32    *[Local/0] 00:28:33
Local via ge-0/0/0.0
192.168.1.0/24     *[Direct/0] 00:28:45
> via vlan.0
192.168.1.1/32     *[Local/0] 00:28:59
Local via vlan.0
[]Use the `show security ike security-associations` command to view Phase 1 SA. In this sample output, 10.10.104.71 is the primary tunnel VIP address and 10.10.104.235 is the backup tunnel VIP address.
Index   State  Initiator cookie  Responder cookie  Mode           Remote Address
524617  UP     2d3dacab94ab709a  087e536c5da7e88c  IKEv2          10.66.45.209
524611  UP     ba44682e8c7f43d2  6c74ba78d214709a  IKEv2          10.66.91.26
[]Use the `show security ipsec security-associations` command to view Phase 2 SA. In this sample output, 10.10.104.71 is the primary tunnel VIP address and 10.10.104.235 is the backup tunnel VIP address.
Total active tunnels: 2     Total Ipsec sas: 2
ID              Algorithm       SPI    Life:sec/kb Mon lsys Port  Gateway
<67108867 ESP:aes-gcm-256/sha1 8d0f431d 13988/ unlim - root 500 10.66.45.209
>67108867 ESP:aes-gcm-256/sha1 2311ec4f 13988/ unlim - root 500 10.66.45.209
<131074 ESP:aes-gcm-256/sha1 fab7ab1f 86286/ unlim - root 500 10.66.91.26
>131074 ESP:aes-gcm-256/sha1 1012ab99 86286/ unlim - root 500 10.66.91.26
[]Use the `clear security ipsec security-associations` commands to clear Phase 2 SA. Similarly, you can use the `clear security isakmp` command to clear Phase 1 SA.
Total active tunnels: 1     Total Ipsec sas: 1
ID              Algorithm       SPI    Life:sec/kb Mon lsys Port         Gateway
<67108867 ESP:aes-gcm-256/sha1 8d0f431d 13988/ unlim - root 500 <Primary Tunnel VIP Address>
>67108867 ESP:aes-gcm-256/sha1 2311ec4f 13988/ unlim - root 500 <Primary Tunnel VIP Address>
root> clear security ipsec security-associations index 6710886
[]Configure the following interfaces on the router. Ensure the following:
- `ge-0/0/0.0` is the WAN external interface. It uses the IP address from a DHCP server.
- `ge-0/0/1.0` through `ge-0/0/7.0` are in the VLAN interface.
- `st0` and `st1` are the tunnel interfaces. The sub-interfaces `unit 0` and `unit 1` are configured in `st0`. Two default routes are configured using st0.0 and st0.1.
Enter the following commands:
set interfaces ge-0/0/0.0 unit 0 family inet dhcp
set interfaces ge-0/0/1.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/2.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/3.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/4.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/5.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/6.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces ge-0/0/7.0 unit 0 family ethernet-switching vlan members vlan-trust
set interfaces st0 unit 0 family inet
set interfaces st0 unit 1 family inet
set interfaces st1 unit 0 family inet
set interfaces vlan unit 0 family inet address 192.168.1.1/24
The CLI output should be similar to the following:
interfaces {
ge-0/0/0.0 {
unit 0 {
family inet {
dhcp;
}
}
}
ge-0/0/1.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/2.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/3.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/4.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/5.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/6.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
ge-0/0/7.0 {
unit 0 {
family ethernet-switching {
vlan {
members vlan-trust;
}
}
}
}
st0 {
unit 0 {
family inet;
}
unit 1 {
family inet;
}
}
st1 {
unit 0 {
family inet;
}
}
vlan {
unit 0 {
family inet {
address 192.168.1.1/24;
}
}
}
}
[]Configure the security zones and associate the interfaces with the zones. Ensure the following:
- `ge-0/0/0.0` is in the untrust zone.
- All Interfaces in the VLAN interface (e.g., `ge-0/0/1.0` through `ge-0/0/7.0`) are in the trust zone.
- `st0.0` is in the `vpn` zone.
Enter the following commands:
set security zones security-zone untrust interfaces ge-0/0/0.0
set security zones security-zone untrust host-inbound-traffic system-services ike
set security zones security-zone trust interfaces vlan0.0
set security zones security-zone trust host-inbound-traffic system-services all
set security zones security-zone vpn interfaces st0.0
set security zones security-zone vpn host-inbound-traffic system-services all
The CLI output should be similar to the following:
zones {
security-zone untrust {
host-inbound-traffic {
system-services {
ike;
}
}
interfaces {
ge-0/0/0.0;
}
}
security-zone trust {
host-inbound-traffic {
system-services {
all;
}
}
interfaces {
vlan0.0;
}
}
security-zone vpn {
host-inbound-traffic {
system-services {
all;
}
}
interfaces {
st0.0;
}
}
[]Configure a security policy to allow traffic from the `trust` zone to the `vpn` zone.
In the following CLI example, the `source-address`, `destination-address`, and `application` are set to `any`. Adding address book entries can make the policy strict.
Enter the following commands:
set security policies from-zone trust to-zone vpn policy <Security Policy Name> match source-address any
set security policies from-zone trust to-zone vpn policy <Security Policy Name> match destination-address any
set security policies from-zone trust to-zone vpn policy <Security Policy Name> match application any
set security policies from-zone trust to-zone vpn policy <Security Policy Name> then permit
The CLI output should be similar to the following:
from-zone trust to-zone vpn {
policy <Security Policy Name> {
match {
source-address any;
destination-address any;
application any;
}
then {
permit;
}
}
}
[]Configure static routing. Specify the traffic you want to route through the IPSec VPN tunnels to Zscaler.
Enter the following command:
set routing-options static route 0.0.0.0/0 next-hop st0.0 st0.1
The CLI output should be similar to the following:
routing-options {
static {
route 0.0.0.0/0 next-hop [ st0.0 st0.1 ];
}
}
[]Configure the IKE proposal for IKE Phase 1. The IKE proposal is a list of security parameters used to protect the IKE connection.
Enter the following commands:
set security ike proposal <IKE Proposal Name> authentication-method pre-shared-keys
set security ike proposal <IKE Proposal Name> dh-group group2
set security ike proposal <IKE Proposal Name> authentication-algorithm sha-256
set security ike proposal <IKE Proposal Name> encryption-algorithm aes-256-gcm
set security ike proposal <IKE Proposal Name> lifetime-seconds 3600
The CLI output should be similar to the following:
ike {
proposal <IKE Proposal Name> {
authentication-method pre-shared-keys;
dh-group group2;
authentication-algorithm sha-256;
encryption-algorithm aes-256-gcm;
lifetime-seconds 3600;
}
[]Configure the IKE policy to associate with the IKE proposal. The IKE policy defines the PSK of the peer and the IKE proposal used during the IKE negotiation. You need the <IKE Proposal Name> created in [5. Configure the IKE Proposal](/zia/ipsec-vpn-configuration-guide-juniper-srx-220#ikev2-ike-proposal).
Enter the following commands:
set security ike policy <IKE Policy Name> proposals <IKE Proposal Name>
set security ike policy <IKE Policy Name> pre-shared-key ascii-text <Pre-Shared Key>
The CLI output should be similar to the following:
policy <IKE Policy Name> {
mode aggressive;
proposals <IKE Proposal Name>;
pre-shared-key ascii-text "$9$iHfz9Cu1Eyp0"; ## SECRET-DATA
}
[]Configure two IKE gateways. You need the <IKE Policy Name> created in [6. Configure the IKE Policy](/zia/ipsec-vpn-configuration-guide-juniper-srx-220#ikev2-ike-policy).
Enter the following commands:
set security ike gateway <Primary IKE Gateway Name> ike-policy <IKE Policy Name>
set security ike gateway <Primary IKE Gateway Name> address <Primary VIP Address>
set security ike gateway <Primary IKE Gateway Name> dead-peer-detection always-send
set security ike gateway <Primary IKE Gateway Name> dead-peer-detection interval 20
set security ike gateway <Primary IKE Gateway Name> dead-peer-detection threshold 5
set security ike gateway <Primary IKE Gateway Name> nat-keepalive 10
set security ike gateway <Primary IKE Gateway Name> local-identity user-at-hostname "<FQDN>"
set security ike gateway <Primary IKE Gateway Name> external-interface ge-0/0/0.0
set security ike gateway <Primary IKE Gateway Name> version v2-only
set security ike gateway <Backup IKE Gateway Name> ike-policy <IKE Policy Name>
set security ike gateway <Backup IKE Gateway Name> address <Backup VIP Address>
set security ike gateway <Backup IKE Gateway Name> dead-peer-detection always-send
set security ike gateway <Backup IKE Gateway Name> dead-peer-detection interval 20
set security ike gateway <Backup IKE Gateway Name> dead-peer-detection threshold 5
set security ike gateway <Backup IKE Gateway Name> nat-keepalive 10
set security ike gateway <Backup IKE Gateway Name> local-identity user-at-hostname "<FQDN>"
set security ike gateway <Backup IKE Gateway Name> external-interface ge-0/0/0.0
set security ike gateway <Backup IKE Gateway Name> version v2-only
The CLI output should be similar to the following:
gateway <Primary IKE Gateway Name> {
ike-policy <IKE Policy Name>;
address <Primary VIP Address>;
dead-peer-detection {
always-send;
interval 20;
threshold 5;
}
nat-keepalive 10;
local-identity user-at-hostname "<FQDN>";
external-interface ge-0/0/0.0;
version v2-only;
}
gateway <Backup IKE Gateway Name> {
ike-policy <IKE Policy Name>;
address <Backup VIP Address>;
dead-peer-detection {
always-send;
interval 20;
threshold 5;
}
nat-keepalive 10;
local-identity user-at-hostname "<FQDN>";
external-interface ge-0/0/0.0;
version v2-only;
}
}
[]Configure VPN monitoring for IKE Phase 2 SAs.
Enter the following commands:
set security ipsec vpn-monitor-options interval 30
set security ipsec vpn-monitor-options threshold 4
The CLI output should be similar to the following:
ipsec {
vpn-monitor-options {
interval 30;
threshold 4;
}
[]Configure the IPSec proposal. The IPSec proposal is a list of protocols and algorithms used to negotiate with the IPSec peer.
For Phase 2, Zscaler recommends using AES-GCM-based ciphers if you have purchased a separate subscription. If you do not have a separate subscription, Zscaler recommends using NULL encryption.
Enter the following commands:
set security ipsec proposal <IPSec Proposal Name> protocol esp
set security ipsec proposal <IPSec Proposal Name> authentication-algorithm hmac-sha-256-128
set security ipsec proposal <IPSec Proposal Name> lifetime-seconds 3600
The CLI output should be similar to the following:
proposal <IPSec Proposal Name> {
protocol esp;
authentication-algorithm hmac-sha-256-128;
lifetime-seconds 3600;
}
[]Configure the IPSec policy to associate with the IPSec proposal. The IPSec policy defines the proposal used during the IPSec negotiation. You need the <IPSec Proposal Name> created in [9. Configure the IPSec Proposal](#ikev2-ipsec-proposal).
Enter the following command:
set security ipsec policy <IPSec Policy Name> proposals <IPSec Proposal Name>
The CLI output should be similar to the following:
policy <IPSec Policy Name> {
proposal-set <IPSec Proposal Name>;
}
[]Configure two IPSec VPNs that are associated with your tunnel interfaces and IKE gateways. You need the <Primary IKE Gateway Name>, <Backup IKE Gateway Name>, and <IPSec Policy Name> configured in [7. Configure the IKE Gateways](/zia/ipsec-vpn-configuration-guide-juniper-srx-220#ikev2-ike-gateways) and [10. Configure the IPSec Policy](/zia/ipsec-vpn-configuration-guide-juniper-srx-220#ikev2-ipsec-policy).
In the following CLI example, the IPSec VPNs are binding to tunnel interfaces `st0.0` and `st0.1`. If you want local subnets to use the VPN, you can define a proxy ID with the `proxy-identity` statement. In this example, the local subnet is `10.10.10.0/24`.
Enter the following commands:
set security ipsec vpn <Primary IPSec VPN Name> bind-interface st0.0
set security ipsec vpn <Primary IPSec VPN Name> df-bit copy
set security ipsec vpn <Primary IPSec VPN Name> ike gateway <Primary IKE Gateway Name>
set security ipsec vpn <Primary IPSec VPN Name> ike proxy-identity local 10.10.10.0/24 remote 0.0.0.0/0
set security ipsec vpn <Primary IPSec VPN Name> ike ipsec-policy <IPSec Policy Name>
set security ipsec vpn <Primary IPSec VPN Name> establish-tunnels immediately
set security ipsec vpn <Backup IPSec VPN Name> bind-interface st0.1
set security ipsec vpn <Backup IPSec VPN Name> df-bit copy
set security ipsec vpn <Backup IPSec VPN Name> ike gateway <Backup IKE Gateway Name>
set security ipsec vpn <Backup IPSec VPN Name> ike proxy-identity local 10.10.10.0/24 remote 0.0.0.0/0
set security ipsec vpn <Backup IPSec VPN Name> ike ipsec-policy <IPSec Policy Name>
set security ipsec vpn <Backup IPSec VPN Name> establish-tunnels immediately
The CLI output should be similar to the following:
vpn <Primary IPSec VPN Name> {
bind-interface st0.0;
df-bit copy;
}
ike {
gateway <Primary IKE Gateway Name>;
proxy-identity {
local 10.10.10.0/24;
remote 0.0.0.0/0;
}
ipsec-policy <IPSec Policy Name>;
}
establish-tunnels immediately;
}
vpn <Backup IPSec VPN Name> {
bind-interface st0.1;
df-bit copy;
}
ike {
gateway <Backup IKE Gateway Name>;
proxy-identity {
local 10.10.10.0/24;
remote 0.0.0.0/0;
}
ipsec-policy <IPSec Policy Name>;
}
establish-tunnels immediately;
}
}
[]Configure the source NAT parameters so that the firewall performs NAT on the traffic and doesn't send it through the tunnel interface. Source NAT isn't required for the traffic from the trust zone to the VPN zone because, as configured in the routing table, all internet traffic is sent through the IPSec VPN tunnels.
In the following source NAT rule, the source IP address `192.168.1.0/24` is the LAN IP subnet.
Enter the following commands:
set security nat source rule-set <NAT Rule Set Name> from zone trust
set security nat source rule-set <NAT Rule Set Name> to zone untrust
set security nat source rule-set <NAT Rule Set Name> rule <NAT Rule Name> match source-address 192.168.1.0/24
set security nat source rule-set <NAT Rule Set Name> rule <NAT Rule Name> match destination-address 0.0.0.0/0
set security nat source rule-set <NAT Rule Set Name> rule <NAT Rule Name> then source-nat interface
The CLI output should be similar to the following:
nat {
source {
rule-set <NAT Rule Set Name> {
from zone trust;
to zone untrust;
rule <NAT Rule Name> {
match {
source-address 192.168.0.0/16;
destination-address 0.0.0.0/0;
}
then {
source-nat {
interface;
}
}
}
}
}
}