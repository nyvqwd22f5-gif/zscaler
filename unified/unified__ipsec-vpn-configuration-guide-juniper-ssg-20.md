# IPSec VPN Configuration Guide for Juniper SSG 20
Source: https://help.zscaler.com/unified/ipsec-vpn-configuration-guide-juniper-ssg-20
PDF: https://help.zscaler.com/pdf/com/en/1495396.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article shows how to configure two IPSec VPN tunnels from a Juniper SSG 20 firewall running ScreenOS 6.2.0r1.0 to two Internet & SaaS Public Service Edges in the Zscaler cloud. To learn more about the WebUI, see the Juniper documentation.
As shown in the following figure, the internal traffic of the corporate office is in the Trust zone. The WAN port Ethernet 0/0 is in the Untrust zone. It sends internet-bound traffic through the VPN tunnel to the Zscaler cloud and performs NAT on the traffic it sends to the internet.
![A network diagram showing the primary and secondary IPSec tunnels from a Juniper SSG to two Zscaler ZIA Public Service Edges.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-juniper-ssg-20/IPSec_Juniper_SSG.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Dead Peer Detection (DPD) must be enabled so the firewall can detect if a VPN is offline. If this occurs, it routes the internet-bound traffic through the backup VPN. In this configuration example, a route-based VPN is configured, where two tunnels are created and then inserted as the default routes in the routing table.
Prerequisites
Ensure you have the following information for setting up the IPSec VPN tunnels:
- [Virtual IP (VIP) addresses of the Internet & SaaS Public Service Edges](/unified/locating-virtual-ip-addresses-internet-saas-public-service-edges)
- [Global IP addresses of the Internet & SaaS Public Service Edges](/unified/about-global-public-service-edges)
- [Maximum Transmission Unit (MTU)](/unified/determining-optimal-mtu-gre-or-ipsec-tunnels)
Configuring the IPSec VPN Tunnel in the Admin Portal
In this configuration example, the peers are using an FQDN and a pre-shared key (PSK) for authentication.
To configure the IPSec VPN tunnels in the Admin Portal:
- [Adding the VPN Credentials](/unified/adding-vpn-credentials)
You need the FQDN and PSK when linking the VPN credentials to a location and creating the IKE gateways.
- [Linking the VPN Credentials to a Location](/unified/configuring-locations)
Configuring the IPSec VPN Tunnel in the Juniper SSG 20 WebUI
This article only covers the configuration details of IPSec VPN tunnels between the Juniper SSG 20 firewall and the Internet & SaaS Public Service Edges. For any other specific information about Juniper SSG 20, refer to the [Juniper documentation](https://www.juniper.net/documentation/en_US/release-independent/screenos/information-products/pathway-pages/hardware/ssg-series/ssg5-ssg20.html).
The following image shows the interface setup in the Juniper WebUI (**Network** > **Interfaces** > **List**):
![Screenshot of the interface list on the Juniper WebUI ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-interface-list.png)
Ensure that the internet port (ethernet 0/0) is in the Untrust zone and the bgroup0 LAN and wireless ports are in the Trust zone.
To configure the IPSec VPN tunnels on Juniper SSG 20:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiation.
- [1. Configure the Tunnel Interfaces](#ikev2-tunnel-interfaces)
- [2. Create a Phase 1 Proposal](#ikev2-p1-proposal)
- [3. Create a Phase 2 Proposal](#ikev2-p2-proposal)
- [4. Configure the IKE Gateways](#ikev2-ike-gateways)
- [5. Configure the AutoKey IKE VPN Tunnels](#ikev2-autokey-ike)
- [6. Configure Policy-Based Routing](#ikev2-policy-based-routing)
After completing the configuration, you can go to **VPNs** > **Monitor Status** to see the status of the IPSec VPN tunnels.
[See image.](#seeimage0)
Testing the Configuration
You can test the configuration by browsing from the Trust zone (through the wireless or bgroup0 LAN ports) to any website. You must log in to the Zscaler cloud before you can access the site.
Troubleshooting
In the Admin Portal, you can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).
On the SSG 20 device, you can use the following CLI commands to monitor and troubleshoot the IPSec VPN tunnels.
- [Viewing the SA](#TroubleshootingViewingSA)
- [Clearing the SA](#TroubleshootingClearingSA)
[]![Screenshot of the Monitor Status page in the Juniper SSG5 WebUI.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-monitor-status-page.png)
[]Configure two IPSec tunnel interfaces using the internet port (ethernet 0/0). Ensure both tunnel interfaces are in the Untrust zone.
To configure the primary tunnel interface:
- Log in to the Juniper SSG 20 WebUI.
[See image.](#seeimageA1)
- Go to **Network** > **Interfaces** > **List**.
[See image.](#seeimageA2)
- In the upper-right corner, choose **Tunnel IF**.
[See image.](#seeimageA3)
- Click **New**.
[See image.](#seeimageA4)
- On the **Configuration** page:
[See image.](#seeimageA5)
- **Tunnel Interface Name**: Enter a number for the tunnel interface name. The name is prepended with **tunnel**. In this example, it's `tunnel.1`.
- **Zone (VR)**: Choose **Untrust (trust-vr)**.
- Select** Unnumbered**.
- **Interface**: Choose **ethernet0/0 (trust-vr)**.
- **Maximum Transfer Unit(MTU)**: Enter the optimal MTU for your tunnel. In this example, it's `1400` Bytes.
- Deselect **DNS Proxy**.
- **Traffic Bandwidth**:
- **Egress Maximum Bandwidth**: Enter the maximum bandwidth (Kbps) for outbound traffic. In this example, it's `50` kbps.
- **Egress Guaranteed Bandwidth**: Enter the guaranteed bandwidth (Kbps) for outbound traffic. In this example, it's `40` kbps.
- **Ingress Maximum Bandwidth**: Enter the maximum bandwidth (Kbps) for inbound traffic. In this example, it's `40` kbps.
- Deselect **NHRP Enable**.
- Click **OK**.
After configuring the primary tunnel, repeat this procedure to configure the backup tunnel interface (tunnel.2).
[]![Screenshot of the Juniper SSG 20 WebUI login page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-ssg-20-webui-login.png)
[]![Screenshot of the List menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-list-menu.png)
[]![Screenshot of the Tunnel IF option on the Interfaces (List) page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-tunnel-if-option.png)
[]![Screenshot of the New button on the Interfaces (List) page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-new-button-interface.png)
[]![Screenshot of the tunnel interface configuration on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-new-tunnel-interface-page.png)
[]Create a Phase 1 proposal with the following IKE parameters.
To create a Phase 1 proposal:
- Go to **VPNs** > **AutoKey Advanced** > **P1 Proposal**.
[See image.](#seeimageC1)
- Click **New**.
[See image.](#seeimageC2)
- On the P1 proposal **Edit** page:
[See image.](#seeimageC3)
- **Name**: Enter a name for the P1 proposal. In this example, it's `ZscalerP1`.
- **Authentication Method**: Choose **Preshare**.
- **DH Group**: Choose **Group 14**.
- **Encryption Algorithm**: Choose **AES-CBC(128 Bits)**.
- **Hash Algorithm**: Choose **SHA-1**.
- **Lifetime**: Enter a lifetime. In this example, it's `24` hours.
- Click **OK**.
[]![Screenshot of the P1 Proposal menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p1-proposal-menu.png)
[]![Screenshot of the New button on the P1 Proposal page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p1-proposal-new-button.png)
[]![Screenshot of the P1 proposal configuration on the Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p1-proposal-edit-page.png)
[]Create a Phase 2 proposal with the following IKE parameters.
To create a Phase 2 proposal:
- Go to **VPNs** > **AutoKey Advanced** > **P2 Proposal**.
[See image.](#seeimageD1)
- Click **New**.
[See image.](#seeimageD2)
- On the P2 proposal **Edit** page:
[See image.](#seeimageD3)
- **Name**: Enter a name for the P2 proposal. In this example, it's `ZscalerP2`.
- **Perfect Forward Secrecy**: Choose **NO-PFS**.
- **Encapsulation**: Select **Encryption (ESP)**.
- **Encryption Algorithm**: Choose **NULL**.
Zscaler recommends using NULL encryption for Phase 2 because it reduces the load on the local router/firewall for traffic destined for the internet. If you want to use AES, you can purchase a separate subscription.
- **Authentication Algorithm**: Choose **SHA-1**.
- **Lifetime**:
- **In Time**: Enter a lifetime. In this example, it's `8` hours.
- **In Kbytes**: Enter `0 `bytes.
- Click **OK**.
[]![Screenshot of the P2 Proposal menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p2-proposal-menu.png)
[]![Screenshot of the New button on the P2 Proposal page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p2-proposal-new-button.png)
[]![Screenshot of the P2 proposal configuration on the Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-p2-proposal-edit-page.png)
[]Configure two IKE gateways, one for each Internet & SaaS Public Service Edge. In this example, the primary gateway created is named Primary-Gateway with the Internet & SaaS Public Service Edge VIP addresses 165.225.80.34. The backup gateway is named Backup-Gateway with the Internet & SaaS Public Service Edge VIP address 185.46.212.34.
To configure the primary IKE gateway:
- Go to **VPNs** > **AutoKey Advanced** > **Gateway**.
[See image.](#seeimageE1)
- Click **New**.
[See image.](#seeimageE2)
- On the gateway **Edit** page:
[See image.](#seeimageE3)
- **Gateway Name**: Enter a name for the IKE gateway. In this example, it's `Primary-Gateway`.
- **Version**: Select **IKEv2**.
- Select **Remote Gateway **and then select **Static IP Address** under it.
- **IP Address/Hostname**: Enter the Internet & SaaS Public Service Edge VIP address for the primary gateway. In this example, it's `165.225.80.34`.
- **Peer ID**: Leave blank.
- **User**: Choose **None**.
- **Group**: Choose **None**.
- Click **Advanced**.
[See image.](#seeimageE4)
- On the advanced gateway **Edit** page:
[See image.](#seeimageE5)
- Select **IKEv2 Auth Method**.
- **Self**: Choose **preshare**.
- **Peer**: Choose **preshare**.
- **Preshared Key**: Enter the pre-shared key for the [VPN credentials](/unified/adding-vpn-credentials) you added in the Admin Portal.
- **Use As Seed**: Leave unselected.
- **Local ID**: Enter the FQDN for the [VPN credentials](/unified/adding-vpn-credentials) you added in the Admin Portal. In this example, it's the FQDN `example@safemarch.com`.
- **Outgoing Interface**: Choose **ethernet0/0**.
- **Security Level**:
- **User Defined**: Choose **Custom**.
- **Phase 1 Proposal**: Choose the P1 proposal you created in [2. Create a Phase 1 Proposal](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-p1-proposal). In this example, it's **ZscalerP1**.
- **Mode (Initiator)**: You can't modify this field.
- **Enable NAT-Traversal**: Select.
- **UDP Checksum**: Leave unselected.
- **Keepalive Frequency**: Enter `5` seconds.
- Select** DPD **under **Peer Status Detection.**
- **Interval**: Enter `5` seconds.
- **Retry**: Enter` 5` seconds.
- Select **Always Send**.
- **Preferred Certificate(optional)**:
- **Local Cert**: Choose **None**.
- **Peer CA**: Choose **None**.
- **Peer Type**: Choose the peer type. In this example, it's **X509-SIG**.
- **Use Distinguished Name for Peer ID**: Leave unselected.
- Click **Return**.
- Click **OK**.
[See image.](#seeimageE7)
- Repeat the procedure to create the backup IKE gateway (Backup-Gateway) using the Internet & SaaS Public Service Edge VIP address 185.46.212.34.
[]![Screenshot of the Gateway menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-menu.png)
[]![Screenshot of the New button on the Gateway page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-new-button.png)
[]![Screenshot of the IKE gateway configuration on the Edit page ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-edit-page.png)
[]![Screenshot of the Advanced button on the gateway Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-advanced-button.png)
[]![Screenshot of the advanced IKE gateway configuration on the Edit page ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-advanced-edit-page.png)
[]![Screenshot of the OK button on the gateway Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-gateway-ok-button.png)
[]Configure two AutoKey IKE VPN tunnels to two different Internet & SaaS Public Service Edges. In this example, the primary VPN tunnel is configured from the primary IKE gateway (Primary-Gateway). It uses the global Internet & SaaS Public Service Edge IP address 185.46.212.88 for VPN monitoring. The backup VPN tunnel is configured from the backup IKE gateway (Backup-Gateway). It uses the global Internet & SaaS Public Service Edge IP address 185.46.212.89 for VPN monitoring.
To configure the primary VPN tunnel:
- Go to **VPNs** > **AutoKey IKE**.
[See image.](#seeimageF1)
- Click **New**.
[See image.](#seeimageF2)
- On the AutoKey IKE **Edit** page:
[See image.](#seeimageF3)
- **VPN Name**: Enter a name for the VPN tunnel. In this example, it's `Primary-Tunnel`.
- Select **Remote Gateway**.
- Select **Predefined **and then choose the primary IKE gateway you configured in [4. Configure the IKE Gateways](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-ike-gateways). In this example, it's **Primary-Gateway**.
- Click **Advanced**.
[See image.](#seeimageF4)
- On the advanced AutoKey IKE **Edit** page:
[See image.](#seeimage5e)
- **Security Level**:
- **User Defined**: Choose **Custom**.
- **Phase 2 Proposal**: Choose the P2 proposal you created in [3. Create a Phase 2 Proposal](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-p2-proposal). In this example, it's **ZscalerP2**.
- Select **Replay Protection**.
- **Transport mode**: Leave unselected.
- **Bind to**: Choose **Tunnel Interface**, and choose the primary tunnel interface you configured in [1. Configure the Tunnel Interfaces](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-tunnel-interfaces). In this example, it's **tunnel.1**.
- **Proxy-ID**: Leave unselected.
- **DSCP Marking**: Select **Disable**.
- **VPN Group**: Choose **None**.
- Select **VPN Monitor**.
- **Source Interface**: Choose **ethernet0/0**.
- **Destination IP**: Enter the global Internet & SaaS Public Service Edge IP address for your primary tunnel. In this example, it's `185.46.212.88`.
- Select **Optimized**.
- Select **Rekey**.
- Click **Return**.
- Click **OK**.
[See image.](#seeimageF7)
- Repeat the procedure to create a backup VPN tunnel (Backup-Tunnel) using the backup tunnel interface (tunnel.2), IKE gateway (Backup-Gateway), and global Internet & SaaS Public Service Edge IP address (185.46.212.89).
[]![Screenshot of the AutoKey IKE menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-menu.png)
[]![Screenshot of the New button on the AutoKey IKE page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-new-button.png)
[]![Screenshot of the VPN configuration on the AutoKey Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-edit-page.png)
[]![Screenshot of the Advanced button on the AutoKey Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-advanced-button.png)
[]![Screenshot of the VPN configuration on the advanced AutoKey Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-advanced-edit-page.png)
[]![Screenshot of the OK button on the AutoKey Edit page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-autokey-ike-ok-button.png)
[]Configure policy-based routing (PBR) so your organization can send its outbound traffic from the Trust to the Untrust security zone and through the tunnel interfaces.
To configure PBR:
- [a. Configure an Extended Access Control List](#ikev2-extended-access-control-list)
- [b. Create a Match Group](#ikev2-match-group)
- [c. Create an Action Group](#ikev2-action-group)
- [d. Create a Policy](#ikev2-policy)
- [e. Bind the Policy to the Trust Interfaces](#ikev2-policy-binding)
- [f. Create Policies for the Security Zones](#ikev2-security-zone-policies)
[]Configure an extended Access Control List (ACL). The extended ACL defines the destination IP address, ports, and protocols.
To configure the extended ACL:
- Go to **Network** > **Routing** > **PBR** > **Extended ACL**.
[See image.](#seeimageG1a)
- In the upper-right corner, choose **trust-vr**.
[See image.](#seeimageG1b)
- Click **New**.
[See image.](#seeimageG1c)
- On the extended ACL **Configuration** page, do the following to add an entry for TCP traffic on port 80:
[See image.](#seeimageG1d)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Extended ACL ID**: Enter `1`.
- **Sequence No.**: Enter `10`.
- **Source IP Address / Netmask**: Leave blank.
- **Source Port**: Leave blank.
- **Destination IP Address / Netmask**: Leave blank.
- **Destination Port**: Enter `80~80`.
- **Protocol**: Choose **TCP**.
- **IP-TOS (1~255)**: Leave blank.
- Click** OK**.
- Click **Add Seq No**.
[See image.](#seeimageG1f)
- On the extended ACL **Configuration** page, do the following to add an entry for TCP traffic on port 443:
[See image.](#seeimageG1g)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Extended ACL ID**: It's automatically set to **1**. You can't modify this field.
- **Sequence No.**: Enter `20`.
- **Source IP Address / Netmask**: Leave blank.
- **Source Port**: Leave blank.
- **Destination IP Address / Netmask**: Leave blank.
- **Destination Port**: Enter `443~443`.
- **Protocol**: Choose **TCP**.
- **IP-TOS (1~255)**: Leave blank.
- Click **OK**.
- Click **Add Seq. No**.
[See image.](#seeimageG1i)
- On the extended ACL **Configuration** page, do the following to add an entry for ICMP traffic:
[See image.](#seeimageG1j)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Extended ACL ID**: It's automatically set to **1**. You can't modify this field.
- **Sequence No.**: Enter `30`.
- **Source IP Address / Netmask**: Leave blank.
- **Source Port**: Leave blank.
- **Destination IP Address / Netmask**: Leave blank.
- **Destination Port**: Leave blank.
- **Protocol**: Choose **ICMP**.
- **IP-TOS (1~255)**: Leave blank.
- Click **OK**.
- Click **Add Seq. No**.
[See image.](#seeimageG1l)
- On the extended ACL **Configuration** page, do the following to add an entry for UDP traffic on port 53:
[See image.](#seeimageG1m)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Extended ACL ID**: It's automatically set to **1**. You can't modify this field.
- **Sequence No.**: Enter `40`.
- **Source IP Address / Netmask**: Leave blank.
- **Source Port**: Leave blank.
- **Destination IP Address / Netmask**: Leave blank.
- **Destination Port**: Enter `53~53`.
- **Protocol**: Choose **UDP**.
- **IP-TOS (1~255)**: Leave blank.
- Click **OK**.
Your extended ACL configuration should look similar to the following:
![Screenshot of the extended ACL configuration](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-list-page.png)
[]![Screenshot of the Extended ACL menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-menu.png)
[]![Screenshot of the trust-vr option on the Extended ACL List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-trust-vr-option.png)
[]![Screenshot of the New button on the Extended ACL List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-new-button.png)
[]![Screenshot of the extended ACL configuration for TCP port 80 on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-configuration-window-tcp-port-80.png)
[]![Screenshot of the Add Seq No button on the Extended ACL List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-list-add-seq-no-button.png)
[]![Screenshot of the extended ACL configuration for TCP port 443 on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-configuration-window-tcp-port-443.png)
[]![Screenshot of the Add Seq No button on the Extended ACL List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-list-add-seq-no-button.png)
[]![Screenshot of the extended ACL configuration for ICMP traffic on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-configuration-window-icmp-port.png)
[]![Screenshot of the Add Seq No button on the Extended ACL List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-list-add-seq-no-button.png)
[]![Screenshot of the extended ACL configuration for UDP port 53 on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-extended-acl-configuration-window-udp-port-53.png)
[]Create a match group for the extended ACL.
- Go to **Network** > **Routing** > **PBR** > **Match Group**.
[See image.](#seeimageG2a)
- In the upper-right corner, choose **trust-vr**.
[See image.](#seeimageG2b)
- Click **New**.
[See image.](#seeimageG2c)
- On the match group **Configuration** page:
[See image.](#seeimageG2d)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Match Group Name**: Enter a name for the match group. In this example, it's `Match-Group`.
- **Sequence No.**: Enter `10`.
- **Extended ACL**: Choose the extended ACL you configured in [a. Configure an Extended Access Control List](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-extended-access-control-list). In this example, it's **1**.
- Click **OK**.
Your match group configuration should look similar to the following:
![Screenshot of the match group configuration](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-match-group-list-page.png)
[]![Screenshot of the Match Group menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-match-group-menu.png)
[]![Screenshot of the trust-vr option on the Match Group List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-match-group-trust-vr-option.png)
[]![Screenshot of the New button on the Match Group List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-match-group-new-button.png)
[]![Screenshot of the match group configuration on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-match-group-configuration-window.png)
[]Create an action group and route it to the tunnel interfaces.
- Go to **Network** > **Routing** > **PBR** > **Action Group**.
[See image.](#seeimageG3a)
- In the upper-right corner, choose **trust-vr**.
[See image.](#seeimageG3b)
- Click **New**.
[See image.](#seeimageG3c)
- On the action group **Configuration** page, do the following to add an entry for the primary tunnel interface:
[See image.](#seeimageG3d)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Action Group Name**: Enter a name for the action group. In this example, it's `Action-Group`.
- **Sequence No.**: Enter `10`.
- **Route To**:
- **Next Hop**: Leave unselected.
- Select **Interface **and then choose the primary tunnel interface you configured in [1. Configure the Tunnel Interfaces](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-tunnel-interfaces). In this example, it's **tunnel.1**.
- Click **OK**.
- Click **Add Seq No**.
[See image.](#seeimageG3f)
- On the action group **Configuration** page, do the following to add an entry for the backup tunnel interface:
[See image.](#seeimageG3g)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Action Group Name**: Enter the same action group name used in step d. In this example, it's `Action-Group`.
- **Sequence No.**: Enter "20".
- **Route To**:
- **Next Hop**: Leave unselected.
- Select **Interface** and then choose the backup tunnel interface you configured in [1. Configure the Tunnel Interfaces](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-tunnel-interfaces). In this example, it's **tunnel.2**.
- Click **OK**.
Your action group configuration should look similar to the following:
![Screenshot of the action group configuration](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-list-page.png)
[]![Screenshot of the Action Group menu In the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-menu.png)
[]![Screenshot of the trust-vr option on the Action Group List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-trust-vr-option.png)
[]![Screenshot of the New button on the Action Group List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-new-button.png)
[]![Screenshot of the action group configuration for the primary tunnel interface on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-tunnel1-configuration-page.png)
[]![Screenshot of the Add Seq No button on the Action Group List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-add-seq-no-button.png)
[]![Screenshot of the action group configuration for the backup tunnel interface on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-action-group-tunnel2-configuration-page.png)
[]Create a policy for the match and action group.
- Go to **Network** > **Routing** > **PBR** > **Policy**.
[See image.](#seeimageG4a)
- In the upper-right corner, choose **trust-vr**.
[See image.](#seeimageG4b)
- Click **New**.
[See image.](#seeimageG4c)
- On the policy **Configuration** page:
[See image.](#seeimageG4d)
- **Virtual Router**: It's automatically named **trust-vr**. You can't modify this field.
- **Policy Name**: Enter a name for the policy. In this example, it's `Zscaler-Policy`.
- **Sequence No.**: Enter `10`.
- **Match Group**: Choose the match group you created in [b. Create a Match Group](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-match-group). In this example, it's **Match-Group**.
- **Action Group**: Choose the action group you created in [c. Create an Action Group](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-action-group). In this example, it's **Action-Group**.
- Click **OK**.
[]![Screenshot of the Policy menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-menu.png)
[]![Screenshot of the trust-vr option on the Policy List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-trust-vr-option.png)
[]![Screenshot of the New button on the Policy List page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-new-button.png)
[]![Screenshot of the policy configuration on the Configuration page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-configuration-page.png)
[]Bind the policy to the Trust interfaces.
- Go to **Network** > **Routing** > **PBR** > **Policy Binding**.
[See image.](#seeimageG5a)
- Under the **Policy Name** column to the right of the **bgroup0** interface, click **N/A**.
[See image.](#seeimageG5b)
- In the **Policy Binding** window:
[See image.](#seeimageG5c)
- **Interface**: It's automatically named **bgroup0**. You can't modify this field.
- Select **Enable**.
- **Policy**: Choose the policy you created in [d. Create a Policy](/unified/ipsec-vpn-configuration-guide-juniper-ssg-20#ikev2-policy). In this example, it's **Zscaler-Policy**.
- Click **OK**.
- Repeat the procedure to bind the policy to the **wireless0/0** interface.
[]![Screenshot of the Policy Binding menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-binding-menu.png)
[]![Screenshot of the N/A button on the Policy Binding page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-binding-na-button.png)
[]![Screenshot of the policy binding configuration in the Policy Binding window](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policy-binding-window.png)
[]Create two policies, one policy that allows traffic from the Trust to the Untrust zone and another policy that allows traffic from the Untrust to the Trust zone.
- Go to **Policy** > **Policies**.
[See image.](#seeimageG6a)
- On the **Policies **page:
[See image.](#seeimageG6b)
- **From**: Choose **Trust**.
- **To**: Choose **Untrust**.
- Click **New**.
[See image.](#seeimageG6c)
- On the **Policies (From Trust to Untrust) **page:
[See image.](#seeimageG6d)
- **Name (optional)**: Leave blank.
- **Source Address**: Select **Address Book Entry** and then choose **Any** from the drop-down menu.
- **Destination Address**: Select **Address Book Entry** and then choose **Any** from the drop-down menu.
- **Service**: Choose **Any**.
- **Application**: Choose **None**.
- **WEB Filtering**: Leave unselected.
- **Action**: Choose **Permit**.
- **Tunnel**:
- **VPN**: Choose **None**.
- **Modify matching bidirectional VPN policy**: Leave unselected.
- **L2TP**: Choose **None**.
- **Logging**: Leave unselected.
- **Position at Top**: Leave unselected.
- **Session-limit**: Leave unselected.
- **Counter**: Enter `0`.
- **Alarm without drop**: Leave unselected.
- Click **OK**.
- Repeat the procedure to configure a second policy that allows traffic from **Untrust** to **Trust**.
Your policy configuration should look similar to the following:
![Screenshot of the configured security zone policies](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-configured-policies-page.png)
[]![Screenshot of the Policies menu in the Juniper WebUI](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policies-menu.png)
[]![Screenshot of the configured Policies page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policies-page.png)
[]![Screenshot of the New button on the Policies page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policies-new-button.png)
[]![Screenshot of the configured security zone policies on the Policies (From Trust to Untrust) page](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-juniper-ssg-20/zia-juniper-webui-policies-from-trust-to-untrust-page.png)
[]Use the `get sa` command to view SAs and to check the status of the tunnel. In the following response, the "sta"
ssg5-serial-wlan-> get sa
total configured sa: 2
HEX ID    Gateway       Port Algorithm    SPI      Life:sec kb Sta PID vsys
00000014< 10.10.104.71  500  esp:null/md5 00000000 expir unlim I/I -1 0
00000014> 10.10.104.71  500  esp:null/md5 00000000 expir unlim I/I -1 0
00000015< 10.10.104.235 500  esp:null/md5 33511797 2149  unlim A/U -1 0
00000015> 10.10.104.235 500  esp:null/md5 008a8a67 2149  unlim A/U -1 0
Use the get sa active command to check the active SAs:
Total active sa: 1
total configured sa: 2
HEX ID       Gateway       Port Algorithm    SPI      Life:sec kb Sta PID vsys
00000015< 10.10.104.235 500  esp:null/md5 33511797 2048 unlim  A/U -1 0
00000015> 10.10.104.235 500  esp:null/md5 008a8a67 2048 unlim  A/U -1 0
Use the get sa stat command to check the active SAs
total configured sa: 2
HEX ID Gateway Fragment Auth-Fail Other Totalbytes
00000014< 10.10.104.71 0 0 0 0
00000014> 10.10.104.71 0 0 0 0
00000015< 10.10.104.235 0 0 0 345976469
00000015> 10.10.104.235 0 0 0 32472216
Use the get sa id 20 command to check the active SAs
index 0, name VPN-71, peer gateway ip 10.10.104.71. vsys<Root>
auto key. tunnel if binding node, tunnel mode, policy id in:<-1> out:<-1> vpngrp:<-1>. sa_list_nxt:<0xffffffff>.
tunnel id 20, peer id 0, NSRP Local. site-to-site. Local interface is ethernet0/0 <10.10.120.41>.
esp, group 2, null encryption, md5 authentication
autokey, IN inactive, OUT inactive
monitor<1>, latency: -1, availability: 0
DF bit: clear
app_sa_flags: 0x5000a4
proxy id: local 0.0.0.0/0.0.0.0, remote 0.0.0.0/0.0.0.0, proto 0, port 0
ike activity timestamp: 1782025
nat-traversal map not available
incoming: SPI 00000000, flag 00004000, tunnel info 40000014, pipeline
life 0 sec, expired, 0 kb, 0 bytes remain
anti-replay on, last 0x0, window 0x0, idle timeout value <0>, idled 1744 seconds
next pak sequence number: 0x0
outgoing: SPI 00000000, flag 00000000, tunnel info 40000014, pipeline
life 0 sec, expired, 0 kb, 0 bytes remain
anti-replay on, last 0x0, window 0x0, idle timeout value <0>, idled 1744 seconds
next pak sequence number: 0x0
ssg5-serial-wlan-> get sa id 21
index 1, name vpn-81, peer gateway ip 10.10.104.235. vsys<Root>
auto key. tunnel if binding node, tunnel mode, policy id in:<-1> out:<-1> vpngrp:<-1>. sa_list_nxt:<0xffffffff>.
tunnel id 21, peer id 1, NSRP Local. site-to-site. Local interface is ethernet0/0 <10.10.120.41>.
esp, group 2, null encryption, md5 authentication
autokey, IN active, OUT active
monitor<1>, latency: 1, availability: 100
DF bit: clear
app_sa_flags: 0x4000a7
proxy id: local 0.0.0.0/0.0.0.0, remote 0.0.0.0/0.0.0.0, proto 0, port 0
ike activity timestamp: 1732254
nat-traversal map not available
incoming: SPI 33511799, flag 00004000, tunnel info 40000015, pipeline
life 3600 sec, 3537 remain, 0 kb, 0 bytes remain
anti-replay on, last 0x1724, window 0xffffffff, idle timeout value <0>, idled 0 seconds
next pak sequence number: 0x0
outgoing: SPI 01c2e484, flag 00000000, tunnel info 40000015, pipeline
life 3600 sec, 3537 remain, 0 kb, 0 bytes remain
anti-replay on, last 0x0, window 0x0, idle timeout value <0>, idled 0 seconds
next pak sequence number: 0xc52
ssg5-serial-wlan->
[]Enter the following command to clear the SA:
ssg5-serial-wlan-> clear sa 21