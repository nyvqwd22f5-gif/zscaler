# IPSec VPN Configuration Guide for Palo Alto Networks Firewall
Source: https://help.zscaler.com/unified/ipsec-vpn-configuration-guide-palo-alto-networks-firewall
PDF: https://help.zscaler.com/pdf/com/en/1495411.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article illustrates how to configure two IPSec VPN tunnels from a Palo Alto Networks firewall to two Internet & SaaS Public Service Edges: a primary tunnel from the PAN appliance to an Internet & SaaS Public Service Edge in one data center and a secondary tunnel from the PAN appliance to an Internet & SaaS Public Service Edge in another data center.
In this article, the IP address of the primary Internet & SaaS Public Service Edge is 165.225.80.35 and the IP address of the secondary Internet & SaaS Public Service Edge is 185.46.212.35. You can learn how to locate the Internet & SaaS Public Service Edge IP addresses for your organization in the Prerequisites section.
![A network diagram showing the primary and secondary IPSec tunnels from a Palo Alto Networks firewall to two ZIA Public Service Edges.](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-palo-alto-networks-firewall/IPSec_Palo_Alto.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Organizations typically forward all traffic destined for any port to the Zscaler service. Alternatively, you can limit the traffic that you forward to the service to HTTP and HTTPS traffic (traffic destined for port 80 and port 443). Regardless, tunneling provides visibility into the internal IP addresses, which can be used for the Zscaler security policies and logging.
Prerequisites
Ensure you have the following information for setting up the tunnels:
- [IP addresses of the Internet & SaaS Public Service Edges](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges)
- [Virtual IP addresses of the Internet & SaaS Public Service Edges](/unified/locating-virtual-ip-addresses-internet-saas-public-service-edges)
- [Maximum Transmission Unit (MTU) for the tunnels](/unified/determining-optimal-mtu-gre-or-ipsec-tunnels)
Ensure that the locations of the [Internet & SaaS Public Service Edge Virtual IP addresses](/unified/locating-virtual-ip-addresses-internet-saas-public-service-edges) correspond to the locations of the [Internet & SaaS Public Service Edge IP addresses](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges).
If you are unable to ping both Internet & SaaS Public Service Edge IP addresses, please contact Zscaler Support.
Configuring the IPSec VPN Tunnels in the Admin Portal
To configure the IPSec VPN tunnels in the Admin Portal:
- [Adding the VPN Credential](/unified/adding-vpn-credentials)
Note the IP address or FQDN and the pre-shared key (PSK) of the added VPN credentials. You need this information to link the VPN credentials to a location and create the IKE gateways.
- [Linking the VPN Credentials to a Location](/unified/configuring-locations)
Configuring the IPSec VPN Tunnels on PAN-OS
This guide covers only the configuration details of IPSec VPN tunnels between the Palo Alto Networks firewall and the Internet & SaaS Public Service Edges. For any other specific information about Palo Alto Networks, refer to the [Palo Alto Networks documentation](https://docs.paloaltonetworks.com/).
This section describes how to configure two IPSec VPN tunnels on a PAN-OS firewall running version 8.x or later.
The following image shows the lab setup.
****![Screenshot of the Ethernet tab in the Palo Alto web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/ethernet_tab_in_the_palo_alto_networks_web_interface_0.png)
****
The **ethernet1/2*** *interface represents the internal corporate network. All traffic from the corporate network egresses through this interface. The **ethernet1/4*** *interface is the external interface. Traffic destined for any external network goes out through this interface. Ensure that the internal network is in the **trust** security zone and the external network is in the **untrust **security zone. Also, ensure that these two interfaces are in the same default virtual router service.
To configure the IPSec VPN tunnels on PAN-OS:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiation.
- [1. Configuring the Tunnel Interfaces](#configuretunnelinterface-8x)
- [2. Creating the IKE Crypto Profile](#createikecryptoprofile-8x)
- [3. Creating the IKE Gateway](#createikegateway-8x)
- [4. Creating the IPSec Crypto Profile](#createipseccryptoprofile-8x)
- [5. Creating the Tunnel Monitor Profile](#createtunnelmonitor-8x)
- [6. Creating the IPSec VPN Tunnels](#createipsectunnel-8x)
- [7. Defining the Policy-Based Forwarding Rule](#createforwardingrule-8x)
You need to create some additional security policies on the firewall to allow the internet traffic to flow through the IPSec tunnel to Internet & SaaS.
Troubleshooting
In the Admin Portal, you can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](/unified/about-insights-logs).
On the PAN appliance, the following are some sample commands that you can use to monitor and troubleshoot the VPNs. Make an SSH connection to the PAN-OS and log in to the CLI to execute the commands.
- [View a List of "show vpn" Commands](#showvpncommands)
- [View the VPN Tunnels and Their States and Peer Addresses](#vpntunnelstatespeeraddress)
- [View the VPN Gateway Configuration Information](#vpngatewayconfiginfo)
- [View the Phase 1 SA Tunnel](#viewphase1)
- [View the Phase 2 SA Tunnel](#viewphase2)
- [View the VPN Tunnels](#viewvpntunnel)
- [Clear Phase 1 SA Tunnel](#clearphase1)
- [Clear Phase 2 SA Tunnel](#clearphase2)
- [View the Routing Table](#viewroutingtable)
[]Configure two tunnel interfaces on the external interface (ethernet1/4). Ensure both tunnels are configured in the **untrust **security** **zone. In this example, the primary tunnel interface is named **tunnel.1 **with a source IP address **10.96.19.91**. The secondary tunnel interface is named **tunnel.2** with a source IP address **10.96.19.92**.
To configure the primary tunnel interface:
- In the Palo Alto Networks web interface, go to **Network **>** Interfaces**.
- Click the** Tunnel **tab.
- Click **Add**.
[See image.](#tunnelinterfaceadd-8x)
- In the **Tunnel Interface** window:
- **Interface Name**: Enter a name for the tunnel interface, such as `tunnel.1`.
- **Comment**: (Optional) Enter additional notes or information.
- **Netflow Profile**: Choose the appropriate Netflow profile. In this example, it's **None**.
- In the **Config **tab:
- **Assign Interface To**:
- **Virtual Router**: Choose **default**.
- **Security Zone**: Choose **untrust**.
[See image.](#tunnelinterface-8x)
- In the **IPv4 tab**, click **Add**.
- **IP**: Palo Alto Networks uses ICMP probes for tunnel and policy-based forward monitoring. Enter the source IP address from which the ICMP monitoring probes is initiated. The source IP address can be any IP address that does not coincide with an existing subnet. In this example, the IP is `10.96.19.91`.
[See image.](#tunnelinterfaceipv4)
- In the **Advanced** tab:
- **Management Profile**: Choose the appropriate management profile.
- **MTU**: Enter the optimal MTU for your tunnel. In this example, it's `1400`.
[See image.](#tunnelinterfaceadvanced)
- Click **OK**.
- Click **Config** and then **Save changes**.
[See image.](#clicksavetunnelinterface-8x)
- Click **Commit** and then **OK**.
[See image.](#clickcommittunnelinterface-8x)
- Repeat this procedure to configure the secondary tunnel interface (**tunnel.2**) using the source IP address **10.96.19.92**.
[]Create an IKE crypto profile that specifies the security settings for the IKE phase 1 negotiations.
To create an IKE crypto profile:
- In the Palo Alto Networks web interface, go to **Network**.
- Expand **Network Profiles**.
[See image.](#expandnetworkprofiles-8x)
- Select **IKE Crypto**.
[See image.](#ikecrypto-8x)
- Click **Add**.
[See image.](#addikecrypto-8x)
- In the **IKE Crypto Profile **window:
- **Name**: Enter a name for the IKE crypto profile, such as `zscaler`.
- **DH Group**: Click **Add**, and choose **group2**.
- **Encryption**: Click **Add**, and choose **aes128-cbc**.
- **Authentication**: Click **Add**, and choose **sha1**.
- **Key Lifetime**: Set it to `24`** Hours**.
- **IKEv2 Authentication Multiple**: Enter `0`.
[See image.](#ikecryptoprofile-8x)
- Click **OK**.
[]Create two IKE gateways, one for each Zscaler IPSec VPN node. In this example, the primary gateway created is named **ZscalerPrimaryTunnel **with the Internet & SaaS Public Service Edge IP address **165.225.80.35**. The secondary gateway is named **ZscalerBackupTunnel **with the Internet & SaaS Public Service Edge IP address **185.46.212.35**.
To create the primary IKE gateway:
- In the Palo Alto Networks web interface, go to **Network**.
- Expand **Network Profiles**.
[See image.](#ikev2networkprofiles)
- Click **IKE Gateways**.
[See image.](#ikev2ikegateways)
- Click **Add**.
[See image.](#ikev2addgateways)
- In the **IKE Gateway **window:
- **Name**: Enter a name for the IKE gateway, such as `ZScalerPrimaryTunnel`.
- **Version**:** **Select **IKEv2 mode only**.
- **Address Type**: Select **IPv4**.
- **Interface**: Choose the external interface **ethernet 1/4**.
- **Local IP Address**: Choose **None**.
- **Peer IP Type**: Choose **Static**.
- **Peer IP Address**: Enter the Internet & SaaS Public Service Edge IP address for the primary gateway. In this example, it's `165.225.80.35`.
- **Authentication**: Select **Pre-Shared Key**.
- **Pre-shared Key**: Enter the pre-shared key of the [VPN credentials](/unified/adding-vpn-credentials) you created in the Admin Portal.
- **Confirm Pre-shared Key**: Reenter the pre-shared key.
- **Local Identification**: Enter the FQDN or IP address of the [VPN credentials](/unified/adding-vpn-credentials) you created in the Admin Portal. In this example, it's the IP address** **`99.41.72.25`.
- **Peer Identification**: Choose **None**.
[See image.](#ikev2gatewayconfig)
- In the** Advanced Options** tab:
- **Enable Passive Mode**: Deselect.
- **Enable NAT Traversal**: Select.
- **IKE Crypto Profile**: Choose the IKE crypto profile you created in [2. Creating the IKE Crypto Profile](#createikecryptoprofile-8x). In this example, it's **zscaler**.
- **Liveness Check**: Select.
- **Interval**: Enter `5`.
[See image.](#ikev2advancedoptions)
- Click **OK**.
- Repeat the procedure to create the secondary IKE gateway (**ZscalerBackupTunnel**) using the Internet & SaaS Public Service Edge IP address **185.46.212.35**.
[]Create an IPSec crypto profile that specifies the security parameters for the IKE phase 2 negotiations.
To create an IPSec crypto profile:
- In the Palo Alto Networks web interface, go to **Network**.
- Expand **Network Profiles**.
[See image.](#ipsecexpandnetworkprofiles-8x)
- Click **IPSec Crypto**.
[See image.](#selectipseccrypto-8x)
- Click **Add**.
[See image.](#ipseccryptoadd-8x)
- In the **IPSec Crypto Profile **window:
- **Name**: Enter a name for the IPSec crypto profile, such as `zscaler-ipsec`.
- **IPSec Protocol**: Ensure **ESP **is chosen.
- **Encryption**: Click **Add**, and choose **null** for NULL encryption. If you want to use AES and have purchased the subscription, you can select **aes128**.
Zscaler recommends using NULL encryption for Phase 2 because it reduces the load on the local router/firewall for traffic destined for the internet. If you want to use AES, you can purchase a separate subscription.
- **Authentication**: Click **Add**, and choose **md5**.
- **DH Group**: Ensure **group2** is chosen.
- **Lifetime**: Set it to `8`** Hours**.
- Keep the **Enable** option unchecked because Zscaler does not support lifesize.
[See image.](#ipseccryptoprofile-8x)
- Click **OK**.
[]A tunnel monitor profile specifies how the firewall monitors IPSec tunnels and the actions it takes if the tunnel is unavailable.
To create a tunnel monitor profile:
- In the Palo Alto Networks web interface, go to **Network**.
- Expand **Network Profiles**.
[See image.](#monitorexpandnetworkprofiles-8x)
- Click **Monitor**.
[See image.](#selectmonitor-8x)
- Click **Add**.
[See image.](#monitoradd-8x)
- In the **Monitor Profile **window:
- **Name**: Enter a name for the monitor profile, such as `zscalersla`.
- **Action**: Choose **Fail Over**.
- **Interval (sec)**: Enter `20`.
- **Threshold**: Enter `5`.
[See image.](#monitorprofile-8x)
- Click **OK**.
[]Create two IPSec VPN tunnels to two different Internet & SaaS Public Service Edges. In this example, the primary IPSec tunnel is configured from the primary IKE gateway (**ZscalerPrimaryTunnel**), which has the Internet & SaaS Public Service Edge IP address **165.225.80.35 **and the Virtual IP address **165.225.80.34**. The secondary IPSec tunnel is configured from the secondary IKE gateway (**ZscalerBackupTunnel**), which has the Internet & SaaS Public Service Edge IP address **185.46.212.35** and the Virtual IP address **185.46.212.34**.
To create the primary IPSec VPN tunnel:
- In the Palo Alto Networks web interface, go to **Network **>** IPSec Tunnels**.
- Click **Add**.
[See image.](#ipsectunnelsadd-8x)
- In the **General** tab:
- **Name**: Enter a name for the tunnel, such as `ZscalerPrimaryTunnel`.
- **Tunnel Interface**: Choose the primary tunnel interface you created in [1. Configuring the Tunnel Interfaces](#configuretunnelinterface-8x). In this example, it's **tunnel.1**.
- **Type**: Ensure **Auto Key **is chosen.
- **Address Type**: Choose **IPv4**.
- **IKE Gateway**: Choose the primary IKE gateway you created in [3. Creating the IKE Gateway](#ikev1andikev2config). In this example, it's **ZScalerPrimaryTunnel**.
- **IPSec Crypto Profile**: Choose the IPSec crypto profile you created in [4. Creating the IPSec Crypto Profile](#createipseccryptoprofile-8x). In this example, it's **zscaler-ipsec**.
- **Show Advanced Options**: Select.
- **Enable Replay Protection**: Select.
- **Copy TOS Header**: Deselect.
- **Tunnel Monitor**: Select.
- **Destination IP**: Enter the Virtual IP address of your primary tunnel. In this example, it's `165.225.80.34`.
- **Profile**: Choose the tunnel monitor profile you created in [5. Creating the Tunnel Monitor Profile](#createtunnelmonitor-8x). In this example, it's **zscalersla**.
[See image.](#ipsectunnel-8x)
- In the **Proxy IDs** tab, click **Add.**
- **Proxy ID**: Enter a name for the proxy.
- **Local**: Enter the local IP address `0.0.0.0/0`.
- **Remote**: Enter the remote IP address `0.0.0.0/0`.
- **Protocol**: Ensure **Any** is chosen.
[See image.](#proxyID-8x)
- Click **OK**.
- Click **OK **again.
- Click **Config **and then **Save Changes**.
[See image.](#ipsectunnelsave-8x)
- Click **Commit** and then **OK**.
[See image.](#ipsectunnelcommit-8x)
- Repeat the procedure to create a secondary IPSec VPN tunnel (**ZscalerSecondaryTunnel)** using the secondary tunnel interface (**tunnel.2**), IKE gateway (**ZscalerBackupTunnel**), and Internet & SaaS Public Service Edge Virtual IP address (**185.46.212.34**).
[]Defining two policy-based forwarding rules to route the traffic from the Palo Alto Networks appliance into the tunnel.
To define the primary policy-based forwarding rule:
- In the Palo Alto Networks web interface, go to **Policies **> **Policy Based Forwarding**.
- Click **Add**.
[See image.](#policybasedfradd-8x)
- In the **General** tab:
- **Name**: Enter a name for the policy, such as `PTpolicy`.
- **Description**: (Optional) Enter a description.
- **Tags**: (Optional) Choose a tag.
[See image.](#policybasedfrgeneral-8x)
- In the **Source** tab, under **Zone**, click **Add**, and choose **trust**.
[See image.](#policybasedfrsource-8x)
- In the **Destination/Application/Service** tab:
- **Destination Address**: Ensure **Any** is selected.
- **Applications**: Ensure **Any** is selected.
- **Service**:** **Ensure **Any** is chosen.** **Note that if you only want to send traffic to port 80/443, click **Add**, and choose **service-http **and **service-https**.
[See image.](#policubasedfrdestination-8x)
- In the **Forwarding** tab:
- **Action**: Choose **Forward**.
- **Egress Interface**: Choose the primary tunnel interface you created in task [1. Configuring the Tunnel Interfaces](#configuretunnelinterface-8x). In this example, it's **tunnel.1**.
- **Next Hop**: Leave this field blank.
- **Monitor: **Select.
- **Profile**: Choose **zscalersla**.
- **Disable this rule if nexthop/monitor ip is unreachable**: Select.
- **IP address**: Enter the Virtual IP address of your primary tunnel. In this example, it's `165.225.80.34`.
- **Schedule**: Choose **None**.
[See image.](#policybasedfrforwarding-8x)
- Click **OK**.
- Repeat the procedure to define the policy-based forwarding rule for the secondary tunnel (**BTpolicy**) using the secondary tunnel interface (**tunnel.2**) and Internet & SaaS Public Service Edge Virtual IP address (**185.46.212.34**).
[]****![Screenshot of the Add button in the Tunnel tab.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/1.add_button_in_the_tunnel_tab_8.0.png)
****
[]****![Screenshot of a configured tunnel interface in the PAN web interface](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/1.tunnel_interface_configuration_in_the_pan_web_interface_8.0.png)
****
[![Screenshot of a configured IPv4 tab tunnel interface in the PAN web interface](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/1.tunnel_interfaces_ipv4_config_8.0.png)
]
[]
![Screenshot of a configured Advanced tab tunnel interface in the PAN web interface](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/1.tunnel_interfaces_advanced_config_8.0.png)
[]
[]****![Screenshot of the Save button in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/save_button_in_tunnel_config_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Commit button in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/commit_button_in_tunnel_config__the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Network Profiles menu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/3.network_profiles_menu._8.0.png)
****
[]
[]****![Screenshot of the IKE Crypto submenu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/ike_crypto_selection_submenu_8.0.png)
****
[]****![Screenshot of the Add button in the IKE Crypto panel.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/2.add_button_in_the_ike_crypto_panel_8.0.png)
****
[]
[]****![Screenshot of a configured IKE crypto profile in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/2.configured_ike_crypto_profile_in_the_pan_web_interface_8.0.png)
****
[![Screenshot of the Network Profiles menu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/3.ikev2_network_profiles_menu._8.0.png)
]
[]
[![Screenshot of the IKEv2 Gateways submenu. ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/ikev2_gateways_selection_submenu_8.0.png)
]
[]
[![Screenshot of the Add button in the IKEv2 Gateways panel. ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/3.add_button_in_the_ikev2_gateways_panel_8.0%20-%20Copy.png)
]
[]
[![Screenshot of a configured IKv2E gateway in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/3.ikev2_gateway_configuration_in_the_pan_web_interface_8.0.png)
]
[]
[![Screenshot of a configured IKEv2 gateway Advanced Options in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/3.ikev2_gateways_advanced_options_config_8.0.png)
]
[]
[]****![Screenshot of the Network Profiles menu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/4.network_profiles_menu_8.0.png)
****
[]****![Screenshot of the IPSec Crypto submenu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/ipsec_crypto_selection_submenu_8.0.png)
****
[]****![Screenshot of the Add button in the IPSec Crypto panel.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/4.add_button_in_the_ipsec_crypto_panel_8.0.png)
****
[]****![Screenshot of a configured IPSec crypto profile in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/4.configured_ipsec_crypto_profile_in_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Network Profiles menu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/5.network_profiles_menu_8.0.png)
****
[]****![Screenshot of the Monitor submenu.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/monitor_selection_submenu_8.0.png)
****
[]****![Screenshot of the Add button in the Monitor panel.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/5.add_button_in_the_monitor_panel_8.0.png)
****
[]****![Screenshot of a configured monitor profile in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/5.monitor_profile_configuration_in_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Add button in the IPSec Tunnels panel.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/6.add_button_in_the_ipsec_tunnels_panel_8.0.png)
****
[]****![Screenshot of a configured IPSec Tunnel in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/6.ipsec_tunnel_configuration_in_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of a configured Proxy ID in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/proxy_id_configuration_in_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Save button in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/6.save_button_in_the_pan_web_interface._8.0.png)
****
[]****![Screenshot of the Commit button in the PAN web interface.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/6.commit_button_in_the_pan_web_interface_8.0.png)
****
[]****![Screenshot of the Add button in the Policy Based Forwarding panel.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/7.add_button_in_the_policy_based_forwarding_panel_8.0.png)
****
[]****![Screenshot of the configured General tab in the Policy Based Forwarding Rule window.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/7.configured_general_tab_in_the_policy_based_forwarding_rule_window_8.0.png)
****
[]****![Screenshot of the configured Source tab in the Policy Based Forwarding Rule window.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/7.configured_source_tab_in_the_policy_based_forwarding_rule_window_8.0.png)
****
[]****![Screenshot of the configured Destination/Application/Service tab in the Policy Based Forwarding Rule window.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/7.-stt1ex_n8elagz6tors4zvex_lt8ivnxv_jqdden8e5wxth5ih3wlnhywi10yfxyr_d79tleqrsmid-tw7gb-chxlzdkm0hy_sdxs8um2k8t7kgnz36c3he2j2zyv9ikaouv5yc_8.0.png)
****
[]****![Screenshot of the configured Forwarding tab in the Policy Based Forwarding Rule window.](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/ipsec-configuration-guide/ipsec-vpn-configuration-example-palo-alto-networks-appliance/7.configured_forwarding_tab_in_the_policy_based_forwarding_rule_window_8.0.png)
****
[]Use the `show vpn` command to view the IPSec-VPN tunnel information, IKE gateway configuration, and IPSec tunnel configuration.
> flow Show dataplane IPSec-VPN tunnel information
> gateway show list of IKE gateway configuration
> ike-sa show IKE SA
> ipsec-sa show IPSec SA
> tunnel show list of auto-key IPSec tunnel configuration
[]Use the `show vpn flow` command to view the total number of configured VPN tunnels, their states, and peer addresses
total tunnels configured: 2
filter - type IPSec, state any
total IPSec tunnel configured: 2
total IPSec tunnel shown: 2
id    name                          state   monitor local-ip                      peer-ip                       tunnel-i/f
--    ----                          -----   ------- --------                      -------                       ----------
24    localzs3:primarytunnel         active  up      10.96.19.238                  10.66.88.108                  tunnel.2
[]Use the `show vpn gateway` command to view the VPN gateway configuration, number of gateways configured, their peer address, etc.
GwID     Name                 Peer-Address/ID                Local Address/ID               Protocol    Proposals
----     ----                 ---------------                ----------------               --------    ---------
17       localzs3             10.66.88.108                   10.96.19.238(email:pa220@ec2.c IKEv2       [PSK][DH2][AES128][SHA1]360-sec
Show IKE gateway config: Total 1 gateways found.
[]Use the `show vpn ike-sa` command to view the configured phase 1 SA tunnels.
IKEv2 SAs
Gateway ID      Peer-Address           Gateway Name           Role SN       Algorithm             Established     Expiration      Xt Child  ST
----------      ------------           ------------           ---- --       ---------             -----------     ----------      -- -----  --
17              10.66.88.108           localzs3               Init 1        PSK/ DH2/A128/SHA1    Jun.29 12:49:41 Jun.29 12:55:41 0  1      Established
IKEv2 IPSec Child SAs
Gateway Name           TnID     Tunnel                    ID       Parent   Role SPI(in)  SPI(out) MsgID    ST
------------           ----     ------                    --       ------   ---- -------  -------- -----    --
localzs3               24       localzs3:primarytunnel     1        1        Init CBF7DC1D 5D1568FD 00000001 Mature
Show IKEv2 SA: Total 1 gateways found. 1 ike sa found.
[]Use the `show vpn ipsec-sa` command to view the phase 2 SA tunnels.
GwID/client IP  TnID   Peer-Address           Tunnel(Gateway)                                Algorithm          SPI(in)  SPI(out) life(Sec/KB)
--------------  ----   ------------           ---------------                                ---------          -------  -------- ------------
17              24     10.66.88.108           localzs3:primarytunnel(localzs3)                ESP/A256/MD5       CBF7DC1D 5D1568FD 3527/102400
Show IPSec SA: Total 2 tunnels found. 1 ipsec sa found.
[]TnID    Name(Gateway)                        Local Proxy IP     Ptl:Port      Remote Proxy IP    Ptl:Port                                   Proposals
-----------------------------------------------------------------------------------------------------------------------------------------------------
3          Zscaler-Tunnel(VPN-71)            0.0.0.0/0          0:0           0.0.0.0/0          0:0         ESP tunl [DH2][NULL][MD5]      7200-sec
4          Zscaler-backup-tunnel(VPN-81)     0.0.0.0/0          0:0           0.0.0.0/0          0:0         ESP tunl [DH2][NULL][MD5]      7200-sec
Show IPSec tunnel config: Total 2 tunnels found
[]Use the `run clear vpn ike-sa` command to clear the phase 1 SA Tunnels.
Clear IKE SA: 0 IKEv1 SA, 1 IKEv2 SA.
[]Use the `run clear vpn ipsec-sa` command to clear the phase 2 SA Tunnels.
Clear IPSec SA: 0 IKEv1 SA, 2 IKEv2 SA.
[]Use the `show routing fib` command to view the total virtual routers.
total virtual-router shown :              1
--------------------------------------------------------------------------------
virtual-router name: default
interfaces:
ethernet1/1 ethernet1/2 tunnel.1 tunnel.2
tunnel.3 tunnel.4 tunnel.5 tunnel.6
tunnel.7 tunnel.8 tunnel.9 tunnel.10
tunnel.11 tunnel.12
route table:
flags: u - up, h - host, g - gateway, e - ecmp, * - preferred path
maximum of fib entries for device:                 2500
maximum of IPv4 fib entries for device:            2500
maximum of IPv6 fib entries for device:            2500
number of fib entries for device:                  25
maximum of fib entries for this fib:               2500
number of fib entries for this fib:                25
number of fib entries shown:                       25
id      destination           nexthop            flags  interface          mtu
--------------------------------------------------------------------------------
27      0.0.0.0/0             0.0.0.0            u      tunnel.11          1300
2821    10.10.104.0/24        10.96.19.254       ug     ethernet1/1        1500
2824    10.65.25.3/32         10.96.19.254       ug     ethernet1/1        1500
2826    10.66.88.107/32       10.96.19.254       ug     ethernet1/1        1500
2827    10.66.88.108/32       10.96.19.254       ug     ethernet1/1        1500
2822    10.66.88.131/32       10.96.19.254       ug     ethernet1/1        1500
2823    10.66.88.135/32       10.96.19.254       ug     ethernet1/1        1500
2820    10.96.19.0/24         0.0.0.0            u      ethernet1/1        1500
5       10.96.19.81/32        0.0.0.0            uh     tunnel.1           1300
4232    10.96.19.82/32        0.0.0.0            uh     tunnel.2           1300
7       10.96.19.83/32        0.0.0.0            uh     tunnel.3           1500
12      10.96.19.88/32        0.0.0.0            uh     tunnel.8           1400
13      10.96.19.89/32        0.0.0.0            uh     tunnel.9           1400
14      10.96.19.90/32        0.0.0.0            uh     tunnel.10          1400
15      10.96.19.91/32        0.0.0.0            uh     tunnel.11          1300
16      10.96.19.92/32        0.0.0.0            uh     tunnel.12          1300
2819    10.96.19.238/32       0.0.0.0            uh     ethernet1/1        1500
24      10.96.19.242/32       0.0.0.0            u      tunnel.7           1400
2825    165.225.241.79/32     10.96.19.254       ug     ethernet1/1        1500
49      172.19.1.0/24         0.0.0.0            u      ethernet1/2        1500
48      172.19.1.1/32         0.0.0.0            uh     ethernet1/2        1500