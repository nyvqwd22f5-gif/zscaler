# IPSec VPN Configuration Guide for SonicWall TZ 350
Source: https://help.zscaler.com/unified/ipsec-vpn-configuration-guide-sonicwall-tz-350
PDF: https://help.zscaler.com/pdf/com/en/1495421.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article illustrates how to configure two IPsec VPN tunnels from a SonicWall TZ 350 firewall to two Internet & SaaS Public Service Edges. As shown in the following figure, the corporate office sends its internal traffic to LAN port X0 in the internal network. It sends the outbound traffic to the WAN interface X1.
![A network diagram showing the primary and secondary IPSec tunnels from a SonicWALL TZ 350 firewall to two Zscaler ZIA Public Service Edges.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/IPSec_SonicWall_350.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Dead Peer Detection (DPD) must be enabled so the firewall can detect if a VPN is offline. If this occurs, it routes the internet-bound traffic through the backup VPN.
SonicWall TZ 350 firewall doesn't support VPN monitoring. It relies on DPD to failover.
Prerequisites
Ensure you have the [IP addresses of the Internet & SaaS Public Service Edges](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges).
Configuring the IPSec VPN Tunnel in the Admin Portal
In this configuration example, the peers use an FQDN and a pre-shared key (PSK) for authentication.
To configure the IPSec VPN tunnels in the Admin Portal:
- [Add the VPN Credential](/unified/adding-vpn-credentials)
You need the FQDN and PSK when linking the VPN credentials to a location and creating the IKE gateways.
- [Link the VPN Credentials to a Location](/unified/configuring-locations)
Configuring the IPSec VPN Tunnel in SonicOS
This article covers only the configuration details of IPSec VPN tunnels between the SonicWall TZ 350 firewall and the Internet & SaaS Public Service Edges. For any other specific information about SonicWall TZ 350, refer to the SonicWall documentation.
This section describes how to log in to the user interface of the SonicWall TZ 350 firewall running SonicOS version 6.5.4.4-44n and configure two IPsec VPN tunnel interfaces. See the SonicWall documentation for additional information about the user interface.
Log in to the SonicWall TZ 350 and complete the following tasks to configure IPSec VPN tunnels:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiation.
- [1. Define the VPN Policy and Specify the IKE Settings](#configure-ike-settings)
- [2. Enable DPD, Packet Fragmenting, and NAT Traversal](#enable-dpd-nat)
After you complete the configuration, you can monitor the status of the tunnel and view packet-level statistics by navigating to **Manage **> **VPN** > **Settings**.
[See image.](#monitor-status)
Troubleshooting
In the Admin Portal, you can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).
To troubleshoot your configuration on the SonicWall GUI:
- Verify that the default route is configured properly so traffic can reach the Internet & SaaS Public Service Edges.
- If the tunnel goes down, click **Renegotiate**.
[See image.](#troubleshoot)
- []Navigate to **Manage **> **VPN** > **Base** **Settings**.
- Under **VPN Global Settings**:
- Select **Enable VPN**.
- **View IP Version**: Choose **IPv4**
[See image.](#vpn-base-settings)
- Click **Add** to create a new VPN policy.
- In the **General** tab:
-
Under **Security Policy**:
- **Policy Type**: Choose **Site to Site.**
Zscaler recommends that you select the **Policy Type** as **Site to Site** to forward all traffic to Zscaler. However, you can also select any other policy type based on your policy requirements.
- **Authentication Method**: Choose **IKE using Preshared Secret.**
- **Name**: Enter `ZscalerTunnel`.
- **IPsec Primary Gateway Name or Address**: Enter `199.168.148.132` (See the *Prerequisites* to learn how to locate Internet & SaaS Public Service Edge IP addresses for your organization.)
- **IPsec Secondary Gateway Name or Address**: Enter `104.129.194.39` (See the *Prerequisites* to learn how to locate Internet & SaaS Public Service Edge IP addresses for your organization.)
- Under **IKE Authentication**:
- **Shared Secret**: Enter the shared secret.
- **Confirm Shared Secret**: Reenter the shared secret.
- **Local IKE ID**: Choose **E-mail Address** and enter `sonic@example.com`.
- **Peer IKE ID**: Choose **IPv4 Address**.
[See image.](#general-tab-config)
- In the **Network** tab, select the local networks and remote networks for which the traffic is tunneled through the IPsec tunnel:
- **Local Networks**: Select **Choose local network from list** and choose **LAN Subnets**.
Zscaler recommends that you select **LAN Subnets** in the **Local Networks** field to forward network traffic through Zscaler. However, you can select any subnet based on your traffic forwarding requirements.
- **Remote Networks**: Select **Use this VPN Tunnel as default route for all internet traffic**.
[See image.](#network-tab-config)
- In the **Proposals** tab, specify the parameters for the IKE (Phase 1) proposal and IPsec (Phase 2) proposal.
- Under **IKE (Phase 1) Proposal**:
- **Exchange**: Choose **IKEv2 Mode**.
- **DH Group**: Choose **Group 2**.
- **Encryption**: Choose **AES-128**.
- **Authentication**: Choose **SHA1**.
- **Life Time (seconds)**: Enter `86400`.
- Under **IPsec (Phase 2) Proposal**:
- **Protocol**: Choose **ESP**.
- **Encryption**: Choose **None**.
Zscaler recommends using NULL encryption for Phase 2 because it reduces the load on the local router/firewall for traffic destined for the internet. If you want to use AES, you can purchase a separate subscription and use the command `esp-aes`.
- **Authentication**: Choose **MD5**.
- **Life Time (seconds)**: Enter `28800`.
[See image.](#ikev2-config)
- In the **Advanced** tab:
- Select **Enable Keep Alive**.
- **VPN Policy bound to**: Choose **Zone WAN**.
- Select **Preempt Secondary Gateway**.
- **Primary Gateway Detection Interval (seconds)**: Enter `28800`.
[See image.](#advanced-tab-config)
- Click **OK**.
- []Navigate to **Manage **> **VPN** > **Advanced Settings**.
- Under **Advanced VPN Settings**:
- Select **Enable IKE Dead Peer Detection**.
- **Dead Peer Detection Interval (seconds)**: Enter `60`.
- **Failure Trigger Level (missed heartbeats)**: Enter `3`.
- Select **Enable Dead Peer Detection for Idle VPN sessions**.
- **Dead Peer Detection Interval for Idle VPN sessions (seconds)**: Enter `60`.
- Select **Enable Fragmented Packet Handling** and **Ignore DF (Don’t Fragment) Bit**.
- Select **Enable NAT Traversal**.
- Select **Clean up Active tunnels when Peer Gateway DNS name resolves to a different IP Address**.
- Under **IKEv2 Settings**:
- Select **Send** **IKEv2 Invalid SPI Notify**.
[See image.](#advanced-vpn-settings)
![Screenshot of VPN Base Settings in SonicWall TZ 350](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_manage_vpn_settings_page.png)
[]
![Screenshot of Configuring the General tab in SonicWall 350 UI](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_general_tab.png)
[]
![Screenshot of Configuring the Network tab in SonicWall 350 UI](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_network_tab.png)
[]
![Screenshot of Configuring the Proposal tab for IKEv2 settings in SonicWall 350 UI](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_proposals_tab_ikev2_proposal_page.png)
[]
![Screenshot of Configuring the Advanced tab in SonicWall 350 UI](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_advanced_tab.png)
[]
![Screenshot of Configuring the Advanced VPN settings page in SonicWall 350 UI](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_advanced_settings_page.png)
[]
[]![Screenshot of the VPN Base settings in the SonicWall TZ 350 UI.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_completed_config_monitor_status.png)
[]![Screenshot of the Renegotiate button in the VPN Base settings page.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-sonicwall-tz-350/sonicwall_TZ_350_troubleshooting.png)