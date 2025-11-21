# Configuring Zero Trust Branch Site-to-Site Connectivity Over Routed Tunnels
Source: https://help.zscaler.com/zero-trust-branch/configuring-zero-trust-branch-over-routed-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1532667.pdf

Routed tunnels provide a secure way to connect branch locations over IP networks. Some applications, like VoIP phones, TACACS+, and Active FTP running in branches require direct source IP address visibility. Zscaler Zero Trust Branch supports remote site connectivity over Zero Trust Branch Routed Tunnels (RTs) and preserves the IP addresses required for these applications to function. The applications are deployed in a hub-and-spoke architecture, where a physical or virtual Zero Trust Branch appliance in a data center (the hub) and Zero Trust Branch appliances in the branch offices (the spokes) connect via the RTs. RTs use state cryptography to secure connections and are easy to implement.
Contact your Zscaler Account team for hub positioning guidance.
Values from the example topology are used throughout this article for illustration purposes only.
Topology
The following sections provide a diagram depicting the topology of site-to-site connectivity over RTs and a description of its components and flow.
- [Topology diagram](#topology-diagram-site-to-site)
- [Topology details](#topology-details-site-to-site)
[]![Diagram showing two sites connected to two hubs via Routed Tunnel and BGP](/downloads/zero-trust-branch/administration/routed-tunnel/site-to-site-connectivity.png)
- []The Pod30 and Pod50 sites are the spokes.
- For redundancy, both spokes are connected to a pair of identical hubs (hubA and hubB). The hub appliances do not communicate with each other.
-
The following interfaces are available at each spoke and hub:
| Spoke Interfaces |
| ---------------- |
| **Interface** | **Connection** |
| s2s_overlay0 | Generic Routing Encapsulation (GRE) tunnel to hubA |
| s2s_overlay1 | GRE tunnel to hubB |
| wg_vpn_client0 | RT to hubA |
| wg_vpn_client1 | RT to hubB |
| ge2 | Physical interface |
| Hub Interfaces |
| -------------- |
| **Interface** | **Connection** |
| s2s_overlay0 | GRE tunnel to Pod30 spoke |
| s2s_overlay1 | GRE tunnel to Pod50 spoke |
| wg_client | RT to Pod50 spoke |
| ge2 | Physical interface |
Configuration
Perform the following steps to configure BGP and establish peering between the spokes and hubs:
- [Step 1: Add Routed Tunnel Hubs](#hubs-site-to-site)
- [Step 2: Activate the Gateways](#activate-site-to-site)
- [Step 3: View the Hubs](#view-hubs)
- [Step 4: Identify Spokes](#spokes-site-to-site)
- [Step 5: Configure the RTs for the Spokes](#routed-tunnel-site-to-site)
- [Step 6: Enable Sharing Over RTs](#share-over-rt-site-to-site)
- [Step 7: Add a Policy-Based Routing Rule for the Spokes](#routing-site-to-site)
[]
Hubs can be physical or virtual Zero Trust Branch appliances. They are typically deployed in your data center. Launch hubs using the same image as the Zero Trust Branch appliance.
Routed tunnel hubs cannot be deployed in a public cloud.
To add a new hub:
- In the Zero Trust Branch Admin Portal, go to **Deployments **> **Hubs**.
-
Click **Add On-Prem Hub**.
[See image.](#add-hub)
-
In the **Add On-Prem Hub** panel:
- **Location**: Select **Add New Location**.
- **Name**: Enter a name for the location.
- **Gateway Name**: Enter a name for the gateway.
-
**User Reachable IP**: Enter the IP address for the gateway. This is the address the spokes use to communicate with the hub. If the hub and spokes at the branch site are separated by an external network such as the internet, enter the post-NAT address of the hub seen on the internet.
Make sure the IP address is entered correctly. An incorrect configuration can cause unexpected results or an end-to-end connectivity failure.
[See image.](#add-hub-panel)
- Click **Add**.
- Copy and save the activation code that displays. You use this code when you activate the gateway.
[See image.](#add-hub-activation-code)
- [Add a site.](/zero-trust-branch/adding-site)
[]![Hubs page with an Add On-Prem Hub button](/downloads/zero-trust-branch/administration/routed-tunnel/hub-add-a-hub-button.png)
[]![Add On-Prem Hub panel with fields for location, name, gateway name, and user-reachable IP address](/downloads/zero-trust-branch/administration/routed-tunnel/add-hub-panel.png)
[]![Add On-Prem Hub panel displaying the activation code to paste when you activate the gateway ](/downloads/zero-trust-branch/administration/routed-tunnel/add-hub-activation.png)
[]
To review the ports that need to be open, see [Open Ports on the Upstream Device](/zero-trust-branch/deploying-zero-trust-branch-appliance#OpenPorts).
The activation process uses the activation code and URL that you saved when you created the site in the Zero Trust Branch Admin Portal. If you cannot find this information:
- Go to **Deployments **> **Sites**.
- Click the site in the **Name **column.
-
Click the **Send Activation Link** icon at the end of the row.
[See image.](#activation-link)
Zscaler supports one subinterface per WAN interface. However, Zero Trust Branch activation is supported over the WAN interface on the main interface (which is tagged), not on a subinterface (which is untagged).
There are two ways to activate a Zero Trust Branch appliance.
- [Activation Code Method](#console)
- [Activation URL Method](#mgmt-port)
[]This method uses the activation code that you saved when you created the site in the Zero Trust Branch Admin Portal. Before you activate the appliance, you must configure it with the same parameters you configured when you created the site in the Zero Trust Branch Admin Portal.
This procedure uses these example values:
- **WAN interface**: ge3 set for DHCP (This interface is hard-coded.)
- **DNS servers**: 1.1.1.1 and 8.8.8.8
- **Web proxy**: hub3.goairgap.com:1883
- [a. Configure the network.](#console-network)
- [b. Configure the web proxy.](#console-webproxy)
- [c. Activate the appliance.](#console-activate)
[]This method uses the URL that you saved when you created the site in the Zero Trust Branch Admin Portal. The URL contains the configuration data for the WAN interface and the activation code.
-
Connect a laptop directly to the [Management port (GE1)](/zero-trust-branch/zero-trust-branch-physical-port-mapping#ZT400) on the appliance. The laptop automatically gets an IP address directly from the appliance.
[See image.](#network-diagram)
-
Open a browser on the laptop and paste the URL that you copied when you created the site.
After the appliance processes the configuration, it displays an **Activation is completed** message on the web page.
[See image.](#browser-validation)
-
In the Zero Trust Branch Admin Portal, go to **Deployments **> **Sites **and click the site in the **Name **column. In the site details, verify that the appliance is activated.
The **State **field value for an activated appliance is:
- **Standalone **for a standalone appliance
- **Active **for the primary node of an HA cluster
- **Standby **for the secondary node of an HA cluster
[Show image.](#portal-validation)
[]
-
In the console, enter `2` (Configure Gateway) from the menu and press `Enter`.
[See image.](#config-gateway-console)
-
Enter `1` (Configure Network) from the next menu and press `Enter`.
[See image.](#config-network-console)
-
Respond to the prompts to complete the network configuration.
[See image.](#config-network-cli)
[]
- In the console, press `Enter` to return to the main menu.
-
Enter `3` (Configure Web Proxy) and press `Enter`.
[See image.](#config-webproxy)
-
Respond to the prompts to complete the web proxy configuration.
[See image.](#config-webproxy-cli)
[]
- In the console, press `Enter` to return to the main menu.
-
Enter `1` (Activate Gateway) and press `Enter`.
[See image.](#activate-menu-1)
-
Enter `1` (Activate Airgap Gateway) from the next menu and press `Enter`.
[See image.](#activate-menu-2)
-
Enter the activation code that you saved when you created the site and press `Enter`.
[See image.](#activate-cli)
-
Press `2` (Main Menu) and press `Enter`. The screen shows that the appliance is activated.
[See image.](#gateway-active)
[]![Option 2 - Configure Gateway in console menu ](/downloads/zero-trust-branch/device-activation/config_gateway.png)
[]![Option 1 - Configure Network option in console menu](/downloads/zero-trust-branch/device-activation/config_network.png)
[]![Network configuration wizard in console with prompts and responses](/downloads/zero-trust-branch/device-activation/config_network_cli.png)
[]![Option 3 - Configure Web Proxy in console menu](/downloads/zero-trust-branch/device-activation/config_webproxy.png)
[]![Web proxy configuration wizard in console with prompts and responses](/downloads/zero-trust-branch/administration/deployment-configuration/gateway-activation/web-proxy-config.png)
[]![Option 1 - Activate Gateway option in the console menu](/downloads/zero-trust-branch/device-activation/activate_gateway_1.png)
[]![Option 1 - Activate Airgap Gateway in the console menu](/downloads/zero-trust-branch/device-activation/activate_gateway_2.png)
[]![Console output with the gateway activation code](/downloads/zero-trust-branch/device-activation/activate_cli.png)
[]![Console displaying the activated gateway](/downloads/zero-trust-branch/device-activation/gateway_activated.png)
[]![Browser showing that the gateway activation completed](/downloads/zero-trust-branch/device-activation/activation_message.png)
[]![Site details showing a green check mark icon showing the gateway is active](/downloads/zero-trust-branch/device-activation/activated_UI.png)
[]![Send Activation Link button at the end of the row for a site on the Sites page](/downloads/zero-trust-branch/device-activation/send-activation-link.png)
[]![Diagram showing a laptop directly connected to the GE1 management port on the appliance and the appliance connected to the internet via the GE3 WAN port. The laptop receives the 192.168.0.0/24 address from the appliance.](/downloads/zero-trust-branch/administration/deployment-configuration/gateway-activation/ztb-activation-diagram.png)
[]To view the hubs and the activated gateways, go to **Deployments **> **Hubs.**
[See image.](#hubs-page)
[]To identify the spokes:
- Go to **Deployment **> **Sites**.
-
Note the pods in the **Site Name** column. In this example, Pod30 and Pod50 are the spokes that BGP advertises over the routed tunnel.
[See image.](#sites)
[]Configure the RT from each spoke, terminating at the primary and secondary hubs.
To configure the routed tunnels:
- Go to **Deployments **> **Sites** and select the first spoke.
- Click **Settings **> **Routed Tunnel (RT)**.
-
Select the primary and secondary hubs and the WAN interfaces used to reach them.
[See image](#pod-30-rt-config)
- Enable **Connect To Hub**.
- Click **Save Changes**.
-
Repeat these steps for the second spoke.
[See image.](#pod-50-rt-config)
[]Spokes enable sharing over routed tunnels at the virtual LAN (VLAN) level. These encrypted routed tunnels advertise the BGP routes.
To enable sharing over routed tunnels:
- Go to **Deployment **> **Sites** and select the first spoke.
- Do one of the following, depending on your Zero Trust Branch version:
-
Click **VLANs **and enable **Share Over RT**.
[See image.](#share-over-rt-pod30)
-
Click **VLANs** > **Gear **icon > **Share on Routed Tunnel**.
[See image.](#share-over-routed-tunnel)
- Repeat these steps for the second spoke.
[]Configure a policy-based routing (PBR) rule on each spoke to direct traffic over a site-to-site VPN. To learn more, see [Configuring Routing Policies](/zero-trust-branch/configuring-routing-policies).
To configure a policy-based rule:
- Go to **Deployments **> **Sites **and select the first spoke.
- Do one of the following:
- If you are adding a new route, click **Routing Policy** > **Configure **> **Add Route**.
- If you are editing an existing rule, click **Routing Policy**, click the **Gear **icon at the end of the row, and then click the **Edit** icon.
-
Complete the **Add Routing Rule** or **Edit Routing Rule** panel, being sure to select **VPN **as the **Nexthop Interface Type**.
[See image.](#pbr-pod30-to-pod50)
- Click **Save**.
-
Repeat these steps for the second spoke, if that spoke initiates traffic.
[See image.](#pbr-pod50-to-pod30)
-
View the configured rules from both spokes.
[See image.](#pbr-pod30-50-list)
Only spokes that initiate traffic require rules. For example, if the Pod30 spoke initiates traffic to the Pod50 spoke, but not vice versa, only Pod30 needs a rule. Response traffic is handled automatically.
[]![Hubs page showing the hub names, gateway names, state, user-reachable IP address, and Zero Trust Branch version](/downloads/zero-trust-branch/administration/routed-tunnel/hubs-page-hubs.png)
![Image]()
[]![Sites page showing the sites (known as spokes in this article), templates used to create the sites, ZIA location, gateway name, state, IP address, and Zero Trust Branch version](/downloads/zero-trust-branch/administration/routed-tunnel/sites-page.png)
[]![Routed Tunnel configuration to create a routed path between the Pod30 spoke and the two hubs](/downloads/zero-trust-branch/administration/routed-tunnel/pod-30-routed-tunnel.png)
[]![Routed Tunnel configuration to create a routed path between the Pod50 spoke and the two hubs](/downloads/zero-trust-branch/administration/routed-tunnel/pod-50-routed-tunnel.png)
[]![Pod30 VLANs tab, with the Share Over RT switch enabled](/downloads/zero-trust-branch/administration/routed-tunnel/share-over-rt-pod30.png)
[]![VLANs tab with the Share on Routed Tunnel menu item selected from the Gear icon](/downloads/zero-trust-branch/administration/routed-tunnel/share-rt.png)
[]![Routing rule configuration for traffic flowing from Pod30 to Pod50](/downloads/zero-trust-branch/administration/routed-tunnel/pbr-pod30_pod50-configure.png)
[]![Pod30 Routing Policy tab showing the rule number and name, Pod30 as source, Pod50 as destination, any protocols, and the gateway ](/downloads/zero-trust-branch/administration/routed-tunnel/pbr-pod30.png)
![Pod50 Routing Policy tab showing the rule number and name, Pod50 as source, Pod30 as destination, any protocols, and the gateway ](/downloads/zero-trust-branch/administration/routed-tunnel/pbr-pod50.png)
[]![Routing rule configuration for traffic flowing from Pod50 to Pod30](/downloads/zero-trust-branch/administration/routed-tunnel/pbr-pod50_pod30-configure.png)
Verification
The following sections describe how to verify site-to-site connectivity over routed tunnels.
You run the CLI commands in these sections from the Zero Trust Branch Admin Portal console. To open the console, click the **>_Console** tab on the site details page.
[See image.](#console-ui)
- [Verify the Hub](#verify-hub-site-to-site)
- [Verify the Spoke](#verify-spoke-site-to-site)
- [Verify Routed Tunnel Traffic Flow](#verify-flow-logs)
[]Run the commands in the following sections to verify the hub:
- [Hub status](#hub-status-hub)
- [PBR rule configuration](#pbr-config-hub)
- [Virtual Routing and Forwarding (VRF) status](#vrf-status-hub)
- [BGP peering with spokes over site-to-site GRE tunnels](#bgp-peering-hub)
- [Peer uptime](#peer-uptime-hub)
- [Routes advertised by spokes via s2s_overlay GRE tunnels](#advertised-routes-hub)
- [Bidirectional Forwarding Detection (BFD) and BGP peering with spokes](#bfd-bgp-peering-hub)
[]To verify the hub, run the `ipconfig` command from the Zero Trust Branch Admin Portal console.
Physical interface:
`ztb-user--pod-40-hubA--pod-40-hubA:~$ifconfig ge2
ge2: flags=4161<**UP**, BROADCAST, RUNNING, MULTICAST> mtu 1500
...`
GRE tunnel-facing spokes:
`ztb-user--pod-40-hubA--pod-40-hubA:~$ifconfig s2s_overlay0
s2s_overlay0: flags=193<UP**, **RUNNING, NOARP> mtu 1256
...
ztb-user--pod-40-hubA--pod-40-hubA:~$ifconfig s2s_overlay1
s2s_overlay1: flags=193<UP**, **RUNNING, NOARP> mtu 1256
...`
RT-facing spokes:
` ztb-user--pod-40-hubA--pod-40-hubA:!$ifconfig wg_client
wg_client: flags=209<UP, POINTOPOINT, RUNNING, NOARP> mtu 1420
...`
[]To confirm that the policy-based rule is configured correctly, run the `ip rule` command from the Zero Trust Branch Admin Portal console.
Table 500 manages site-to-site tunnels (s2s overlays).
`user-test--pod-40-hubA--pod-40-hubA:~$docker exec vyos_container su - vyos sh -c 'ip rule'
1000:     from all lookup [13mdev-table]
1999:     from all goto 2001
2000:     from all lookup [13mdev-table] unreachable
2001:     from all lookup local
30000:    from all lookup main suppress_prefixlength 0
30100:    from all lookup 500
32765:    from all lookup local
32766:    from all lookup main
32767:    from all lookup default`
[]To verify that the site-to-site BGP Virtual Routing and Forwarding (VRF) on both hubs is up, run the `show vrf` command for each hub from the Zero Trust Branch Admin Portal console.
`user-test--pod-40-hubA--pod-40-hubA:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show vrf'
Name     State MAC address         Flags                      Interfaces
—---     —---- —----------------   —------------------------  —-----------------------------------
vrf-s2s  up    5e:cx:2x:ex:8x:cx   noarp,master,up, lower_up  s2s_overlay0,s2s_overlay1,pim6reg500
user-test--pod-40-hubB--pod-40-hubB:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show vrf'
Name     State MAC address         Flags                      Interfaces
—---     —---- —----------------   —------------------------  —-----------------------------------
vrf-s2s  up    5x:cx:2x:ex:8x:cx   noarp,master,up, lower_up  s2s_overlay0,pim6reg500,s2s_overlay1
`
[]To verify that the hubs established BGP peering with spokes over site-to-site GRE tunnels, run the `ip neighbor | grep` command for each hub from the Zero Trust Branch Admin Portal console.
`user-test--pod-40-hubA--pod-40-hubA:~$ docker exec vyos_container su - vyos sh -c 'ip neighbor | grep s2s'
100.64.219.144 dev s2s_overlay0 1laddr 100.64.174.92 PERMANENT
100.64.233.132 dev s2s_overlay0 1laddr 100.64.141.18 PERMANENT``user-test--pod-40-hubB--pod-40-hubB:~$ docker exec vyos_container su - vyos sh -c 'ip neighbor | grep s2s'
100.65.216.183 dev s2S_overlay1 Iladdr 100.64.151.96 PERMANENT`
[]To verify that the hubs established BGP peering with the spokes and to view the peer uptime, run the `show ip bgp vrf vrf-s2s summary` command from the Zero Trust Branch Admin Portal console.
`user-test--pod-40-hubA--pod-40-hubA:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show ip bgp vrf vrf-s2s summary'
IPv4 Unicast Summary (VRF vrf-s2s) :
BGP router identifier 100.65.195.202, local AS number 229 vrf-id 26
BGP table version 2
RIB entries 3, using 576 bytes of memory
Peers 4, using 82 KiB of memory
Neighbor           V      AS     MsgRevd   MsgSent     TblVer    InQ    OutQ      Up/Down  State/PfxRcd   PfxSnt Desc
100.64.219.144     4     219        1724      1725          2      0       0     1d04h34m             1        2  N/A
100.64.233.132     4     221        1726      1725          2      0       0     1d04h34m             1        2  N/A`
[]To view the hub BGP routing table and the BGP routes advertised by the spokes reachable via s2s_overlay GRE tunnels, run the `ip route show table 500` command for each hub from the Zero Trust Branch Admin Portal console.
`user-test--pod-40-hubA--pod-40-hubA:~$sudo docker exec vyos_container su - vyos sh -c '/opt/vyata/bin/vyatta-op-cmd-wrapper show ip route table 500'
...
VRF default table 500:
B›* 10.90.30.0/24 [20/0] via 100.64.233.132, s2s_overlay0, weight 1, 1d04h36m
B>* 10.90.50.0/24 [20/0] via 100.64.219.144, s2s_overlay0, weight 1, 1d04h37m
C>* 100.64.192.0/18 is directly connected, s2s_overlay0, 1004h44m
C>﻿* 100.65.192.0/18 is directly connected, s2s_overlay1, 1d04h44m
...
user-test--pod-40-hubB--pod-40-hubB:~$sudo docker exec vyos_container su - vyos sh -c '/opt/vyata/bin/vyatta-op-cmd-wrapper show ip route table 500'
...
VRF default table 500:
B›* 10.90.30.0/24 [20/0] via 100.65.216.183, s2s_overlay1, weight 1, 1d04h36m
B›* 10.90.50.0/24 [20/0] via 100.65.214.20, s2s_overlay1, weight 1, 1d04h36m
C>* 100.64.192.0718 1s directly connected, s2s_overlay0, 1004h44m
C›* 100.65.192.0/18 is directly connected, s2s_overlay1, 1d04h44m`
[]To view the hub's BFD and BGP peering with the spokes, run the `show configuration` command from the Zero Trust Branch Admin Portal console.
BFD detects link failure.
`user-test--pod-40-hubA--pod-40-hubA:~$sudo docker exec vyos_container su - vyos sh -c '/opt/vyata/bin/vyatta-op-cmd-wrapper show configuration'
...
protocols {
bfd {
peer 100.64.219.144 {
interval {
multiplier 50
}
source {
interface s2s_overlay0
}
vrf vrf-s2s
}
peer 100.64.233.132 {
interval {
multiplier 50
}
source {
interface s2s_overlay0
}
vrf vrf-s2s
}
peer 100.64.219.144 {
interval {
multiplier 50
}
source {
interface s2s_overlay1
}
vrf vrf-s2s
}
peer 100.64.233.132 {
interval {
multiplier 50
}
source {
interface s2s_overlay1
}
vrf vrf-s2s
}
}
}
vrf {
name vrf-s2s {
protocols {
bgp {
...
neighbor 100.64.219.144 {        //BGP Neighbor (Spoke)
address-family {
ipv4-unicast {
nexthop-self {
{
{
{
bfd {
{
remote-as external
update-source s2s_overlap0
neighbor 100.64.233.132 }        //BGP Neighbor (Spoke)
address-family {
ipv4-unicast {
nexthop-self {
}
}
}`
[]Run the commands in the following sections to verify the spokes:
- [Spoke status](#spoke-status-spoke)
- [PBR rule configuration](#pbr-spoke)
- [Virtual Routing and Forwarding (VRF) status](#vrf-spoke)
- [BGP peering with spokes over site-to-site GRE tunnels](#bgp-spoke)
- [Peer uptime](#peer-uptime-spoke)
- [Routes advertised by spokes via s2s_overlay GRE tunnels](#advertised-routes-spoke)
- [Verify communication between the spokes](#spoke-comm-spoke)
[]To verify the spokes, run the `ifconfig` command from the Zero Trust Branch Admin Portal console.
Physical interface:
`user-test--Pod50--pod50-gw-st:~$ifconfig ge3.50
ge3.50: flags=4163<UP, BROADCAST, RUNNING, MULTICAST> mtu 1500
...`
GRE tunnel-facing hubs:
`user-test--Pod50--pod50-gw-st:~$ifconfig s2s_overlay0
s2s_overlay0: flags=193<UP,RUNNING, NOARP> mtu 1256
inet 100.64.219.144 netmask 255.255.192.0
...
user-test--Pod50--pod50-gw-st:~$ifconfig s2s_overlay1
s2s_overlayl: flags=193<UP, RUNNING, NOARP> mtu 1256
inet 100.65.214.20 netmask 255.255.192.0
...`
Routed tunnel-facing hubs:
`user-test--Pod50--pod50-gw-st:~$ifconfig wg_vpn_client0
wg_vpn_client0: flags=209<UP,POINTOP0INT, RUNNING, NOARP> mtu 1280
inet 100.64.174.92 netmask 255.255.255.255 destination 100.64.174.92
...
user-test--Pod50--pod50-gw-st:~$ifconfig wg_vpn_client1
wg_vpn_client1: flags=209<UP,POINTOPOINT, RUNNING, NOARP> mtu 1280
inet 100.64.154.189 netmask 255.255.255.255 destination 100.64.154.189
...`
Site-to-site VPN uses the `wg_vpn_client0` and `wg_vpn_client1` interfaces. The previous command output shows that site-to-site VPN is enabled.
[]To confirm that the policy-based rule is configured correctly, run the `ip rule` command for each spoke from the Zero Trust Branch Admin Portal console.
Table 500 manages site-to-site tunnels (s2s overlays).
`user-test--Pod30--pod30-gw-st:~$ ip rule
1000:   from all lookup [13mdev-table]
1999:   from all goto 2001
2000:   from all lookup [13mdev-table] unreachable
2001:   from all lookup local
2100:   from all fwmark 0x800 lookup 500
3000:   from all fwmark 0x1000 lookup 300
...``user-test--Pod50--pod50-gw-st:~$ ip rule
1000:   from all lookup [13mdev-table]
1999:   from all got 2001
2000:   from all lookup [13mdev-table]
2001:   from all lookup local
2100:   from all fwmark 0x800 lookup 500
3000:   from all fwmark 0x1000 lookup 300
...`
To see a list of installed rules in order and the corresponding flow-mark of each rule, run the `iptables -nVL -t mangle` command from the Zero Trust Branch Admin Portal console.
`user-test--Pod30--pod30-gw-st:~$ iptables -nVL -t mangle
Chain PREROUTING (policy ACCEPT 253K packets, 93M bytes)
pkts bytes target     prot opt in  out  source      destination
346K 120M PBR-RULES  all  --  *   *    0.0.0.0/0    0.0.0.0/0
527K  27M CONNMARK    all  --  *   *    0.0.0.0/0   0.0.0.0/0   ctdir ORIGINAL CONNMARK set 0x1000
...
Chain POSTROUTING (policy ACCEPT 222K packets, 134M bytes)
pkts bytes target     prot opt in  out  source      destination
Chain PBR-RULES (1 references)
pkts bytes target     prot opt in  out   source       destination
0     0   MARK        all  --  *   *    0.0.0.0/0    0.0.0.0/0   ctdir ORIGINAL match-set
37 src match-set 38 dst MARK set 0x800
0     0   RETURN      all  --  *   *    0.0.0.0/0    0.0.0.0/0   mark match 0x800
Chain PBR-RULES-X (0 references)
pkts bytes target     prot opt in  out  source      destination`
To see what is within the source, destination, and protocols in match sets 37 and 38, run the `ipset list 37` and `ipset list 38` commands for each spoke from the Zero Trust Branch Admin Portal console.
`user-test--Pod30--pod30-80-gw-st:~$ ipset list 37
Name: 37
Type: hash:net
Revision: 6
Header: family inet hashsize 1024 maxelem 65536
Size in memory: 504
References: 1
Number of entries: 1
Members:
10.90.30.0/24
user-test--Pod30--pod30-gw-st:~$ ipset list 38
Name: 38
Type: hash:net
Revision: 6
Header: family inet hashsize 1024 maxelem 65536
Size in memory: 504
References: 1
Number of entries: 1
Members:
10.90.50.0/24                `
[]To verify that the site-to-site BGP VRF that was configured on each spoke is up, run the `show vrf` command from the Zero Trust Branch Admin Portal console.
`user-test--Pod30--pod30-gw-st:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show vrf'
Name      State    MAC address         Flags                         Interfaces
-------   -------  ----------------    ---------------------------   ------------------------------------
vrf-s2s   up       5e:cx:xx:ex:xx:x8   noarp, master, up, lower_up   pim6reg500,s2s_overlay0,s2s_overlay1
user-test--Pod50--pod50-gw-st:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show vrf'
Name	 State	  MAC address	       Flags			              Interfaces
-------  -------  ---------------- 	   ---------------------------    ------------------------------------
vrf-s2s	 up 	  5e:cx:xx:ex:xx:x8   noarp, master, up, lower_up    pim6reg500,s2s_overlay0,s2s_overlay1
`
[]To verify that the spokes established BGP peering through the primary and secondary hubs over site-to-site GRE tunnels, run the `ip neighbor | grep s2s` command for each spoke from the Zero Trust Branch Admin Portal console.
`user-test--Pod30--pod30-gw-st:~$ ip neighbor | grep s2s
100.65.192.133 dev s2s_overlay1 1laddr 100.64.129.207 PERMANENT
100.64.195.202 dev s2s_overlay0 1laddr 100.64.128.68 PERMANENT
user-test--Pod50--pod50-gw-st:~$ ip neighbor | grep s2s
100.65.192.133 dev s2s_overlay1 1laddr 100.64.129.207 PERMANENT
100.64.195.202 dev s2s_overlay0 1laddr 100.64.128.68 PERMANENT`
[]To verify that the spoke established BGP peering with primary and secondary hubs and view the peer uptime, run the `show ip bgp vrf vrf-s2s summary` command for each spoke from the Zero Trust Branch Admin Portal console.
`user-test--Pod30--pod30-gw-st:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show ip bgp vrf vrf-s2s summary'
IPv4 Unicast Summary (VRF vrf-s2s):
BGP router identifier 100.65.216.183, Local AS number 221 vrf-id 21
BGP table version 4
RIB entries 3, using 576 bytes of memory
Peers 4, using 82 KiB of memory
Neighbor	    V  AS	MsgRcvd	  MsgSent  TblVer InQ  OutQ  Up/Down  State/PfxRcd	PfxSnt Desc
100.64.195.202	4 229	    135	      136	 4     0     0   02:08:40	         1       2 N/A
100.65.192.133	4 230	    138	      138	 4     0     0   02:09:04		     1       1 N/A
user-test--Pod50--pod50-gw-st:~$ sudo docker exec vyos_container su - vyos sh -c '/opt/vyatta/bin/vyatta-op-cmd-wrapper show ip bgp vrf vrf-s2s summary'
...
Neighbor	    V  AS	MsgRcvd	  MsgSent  TblVer InQ  OutQ  Up/Down  State/PfxRcd	PfxSnt Desc
100.64.195.202	4 229	    128	      129	  2    0     0   02:01:37	         1       2 N/A
100.65.192.133	4 230	    128	      130	  2    0     0   02:01:04		     1       1 N/A`
[]To view the spoke BGP routing table and the BGP route advertised by the remote spoke reachable via the s2s_overlay0 GRE tunnel, run the `ip route show table 500` command for each spoke from the Zero Trust Branch Admin Portal console. In the first example, the Pod30 spoke sees the route advertised by Pod50. In the second example, the Pod50 spoke sees the route advertised by Pod30.
`user-test--Pod30--pod30-gw-st:~$ ip route show table 500
10.90.50.0/24 nhid 67 via 100.64.195.202 dev S2S_overlay0 proto bgp metric 20
100.64.192.0/18 dev S2S_overlayo proto kernel scope link src 100.64.233.132
local 100.64.233.132 dev s2s_overlay0 proto kernel scope host src 100.64.233.132
broadcast 127.255.255.255 dev s2s_overlay0 proto kernel scope link src 100.64.233.132
...
user-test--Pod50--pod50-gw-st:~$ ip route show table 500
10.90.30.0/24 nhid 457 via 100.64.195.202 dev s2s_over layo proto bep metric 20
100.64.192.0/18 dev s2s_overlay0 proto kernel scope link src 100.64.219.144
local 100.64.219.144 dev s2s_overlay0 proto kernel scope host src 100.64.219.144
broadcast 100.64.255.255 dev s2s_overlay0 proto kernel scope link src 100.64.219.144
...`
[]To verify connectivity between Pod30 and Pod50, ping the Pod30 host or an endpoint in Pod30 from an endpoint in Pod50. In this example, the `ip address show` command output shows the Pod30 host IP address.
` admin30@pod-30-1nx-a:~$ ip address show
1: lo: <LOOPBACK, UP, LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
link/Loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
valid_lft forever preferred_lft forever
inet6 ::1/128 scope host
valid_lft forever preferred_lft forever
2: ﻿﻿﻿ens160: <BROADCAST, MULTICAST,UP, LOWER_UP> mu 1500 qdisc mq state UP group default qlen 1000
link/ether 00:0c:29:db:81:c7 brd ff:ff:ff:ff:ff:ff
altname enp3s0
inet 10.90.30.2/32 brd 10.90.30.2 scope global dynamic ens160
valid_lft 57353sec preferred_lft 57353sec
inet6 fe80::6310:cd9c:af3c:2c30/64 scope link noprefixroute
valid_lft forever_preferred_lft forever
admin50@pod-50-1nx-a:~$ ping 10.90.30.2
PING 10.90.30.2 (10.90.30.2) 56(84) bytes of data.
64 bytes from 10.90.30.2: icmp_seq=1 ttl=61 time=6.89 ms
64 bytes from 10.90.30.2: icmp_seq=2 ttl=61 time=1.38 ms
...`
[]To verify that traffic is sent over the routed tunnel:
- In the Zero Trust Branch Admin Portal, go to **Monitoring & Logs** > **Flow Logs**.
-
View the highlighted information in the following excerpts from the flow log.
[See image.](#flow-logs-1)
[]![Tab on the site details page that opens the Zero Trust Branch Admin Portal console ](/downloads/zero-trust-branch/administration/routed-tunnel/console-tab-ui.png)
[]
This excerpt shows the source IP and destination IP for traffic flowing from Pod30 to Pod50:
![Flog logs showing source and destination IPs](/downloads/zero-trust-branch/administration/routed-tunnel/flow-logs-1.png)
This excerpt shows the destination IP for traffic flowing from Pod30 to Pod50:
![Flow Logs showing destination IP](/downloads/zero-trust-branch/administration/routed-tunnel/flow-logs-2.png)
This excerpt shows the interface through which traffic is sent over the routed tunnel:
![Flow Logs showing traffic sent over the routed tunnel](/downloads/zero-trust-branch/administration/routed-tunnel/flow-logs-3.png)
This excerpt shows the source IP for traffic flowing from Pod30 to Pod50:
![Flow Logs showing source IP](/downloads/zero-trust-branch/administration/routed-tunnel/flow-logs-4.png)