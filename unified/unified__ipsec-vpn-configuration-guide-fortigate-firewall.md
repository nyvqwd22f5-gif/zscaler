# IPSec VPN Configuration Guide for FortiGate Firewall
Source: https://help.zscaler.com/unified/ipsec-vpn-configuration-guide-fortigate-firewall
PDF: https://help.zscaler.com/pdf/com/en/1495401.pdf

This article uses only sample IP addresses in the configuration steps and screenshots. For tunnel interface configuration, you must use only RFC 1918 IP addresses and not APIPA addresses.
This article illustrates how to configure two IPSec VPN tunnels from a FortiGate firewall to two Internet & SaaS Public Service Edges: a primary tunnel from the FortiGate firewall to an Internet & SaaS Public Service Edge in one data center and a backup tunnel from the same firewall to an Internet & SaaS Public Service Edge in another data center. In this example, the peers are using a pre-shared key for authentication. DPD is enabled so the firewall can detect if one VPN goes offline and move the internet-bound traffic to the backup VPN.
This article uses private IP addresses because it was tested in a lab environment.
![A network diagram of the primary and secondary IPSec tunnels from a FortiGate 60D firewall to two Zscaler ZIA Public Service Edges](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/IPSec_FortiGate.png)
Zscaler IPSec tunnels support a limit of 400 Mbps for each public source IP address. If your organization wants to forward more than 400 Mbps of traffic, Zscaler recommends using one of the following configurations:
- Configure multiple IPSec tunnels with different public source IP addresses.
- Configure multiple IPSec VPN tunnels with the same public source IP address using NAT-T and source port randomization with IKEv2.
For example, if your organization forwards 800 Mbps of traffic, you can configure two primary VPN tunnels and two backup VPN tunnels.
Prerequisites
Before you start configuring the Zscaler service and the firewall, ensure that you send Zscaler the following information:
- The IP address of the tunnel interface on the firewall
- [IP addresses of the Internet & SaaS Public Service Edges](/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges)
Configuring the IPSec VPN Tunnel in the Admin Portal
In this configuration example, the peers are using an FQDN and a pre-shared key (PSK) for authentication.
To configure the IPSec VPN tunnels in the Admin Portal:
- [Add the VPN Credential](/unified/adding-vpn-credentials)
You need the FQDN and PSK to link the VPN credentials to a location and create the IKE gateways.
- [Link the VPN Credentials to a Location](/unified/configuring-locations)
Configuring the IPSec VPN Tunnel in FortiOS
This article only covers the configuration details of IPSec VPN tunnels between the FortiOS and the Internet & SaaS Public Service Edges. For any other specific information about FortiOS, refer to the [Fortinet documentation](https://docs.fortinet.com/product/fortigate/5.2).
This section describes how to configure two IPSec VPN tunnel interfaces on a FortiGate 300E firewall running version v6.0.2. Refer to the Fortinet documentation for additional information about the user interface.
The following figure shows the lab setup:
![Screenshot of the internal and external tunnel interfaces in the FortiGate 60D web UI](/downloads/zia/the_internal_and_external_tunnel_interfaces_in_the_fortigate_60d_web_ui.png)
The corporate office sends its traffic through the internal interface in the internal network. It sends traffic destined for any external network through the external interface, wan1.
To configure the IPSec VPN tunnels on a FortiGate firewall:
Zscaler does not support Extended Sequence Number (ESN) based proposals during IPSec tunnel negotiation.
- [1. Configure the VPN Parameters](#ikev2-config-vpn-parameter)
- [2. Define the IPv4 Policies](#define-ipv4-policies-6x)
- [3. Establish the Static Routes](#establish-static-routes-6x)
- [4. Define the Policy Routes](#define-policy-routes-6x)
Troubleshooting
In the Admin Portal, you can go to Logs > Insights > Tunnel Insights to see data as well as monitor the health and status of your configured IPSec VPN tunnels. To learn more, see [About Insights](/unified/about-insights) and [About Insights Logs](unified/about-insights-logs).
In FortiOS, go to **VPN **>** Monitor **>** IPsec Monitor** to verify the status and that traffic is flowing through the primary tunnel.
[See image.](#seeimage0)
The network processor (NP) of some Fortinet devices doesn’t support offloading VPN phase one traffic, resulting in an unacceptable drop in VPN tunnel performance. To learn more, see [How to disable offloading IPVPN ESP packets to NP per Phase 1](http://kb.fortinet.com/kb/documentLink.do?externalID=FD36044).
For more troubleshooting information on FortiOS, see the [Fortinet FortiOS Handbook](https://docs.fortinet.com/document/fortigate/5.2.15/fortios-handbook).
[]![Screenshot of the IPsec Monitor content pane](/downloads/zia/ipsec_monitor_content_pane.png)
[]Define the VPN parameters for the primary and backup VPN tunnels.
- Go to **VPN **>** IPsec Tunnels**.
-
Click **Create New**.
[See image.](#vpn-create-new)
-
In the **VPN Setup** tab:
- **Name**: Enter a name for the VPN tunnel. In this example, it's `Zscaler`**.**
- **Template Type**: Select **Custom**.
[See image.](#vpn-setup-ikev2)
- In the **New VPN Tunnel** tab:
-
Under the **Network** section:
- **IP Version**: Choose **IPv4**.
- **Remote Gateway**: Select **Static IP Address**.
- **IP Address**: Enter your IP address.
- **Interface**: Select an interface based on your requirements.
- **NAT Traversal**: Choose **Enable**.
- **Keepalive Frequency**: Enter `10`.
- **Dead peer Detection**: Select **On Demand**.
[See image.](#New-VPN-Tunnel-tab-image)
-
Under the **Authentication** section:
- **Method**: Select **Pre-shared Key**.
- **Pre-shared Key**: Enter the Pre-shared Key value.
- **IKE Version**: Select** 2**.
- **Accept Types**: Select **Any Peer ID**.
[See image.](#vpn-setup-authentication-ikev2)
-
Under **Phase 1 proposal** and **Phase 2 selectors** sections, configure the parameters for the primary tunnel as shown in the following image:
[See image.](#vpn-setup-ikev2-phase1and2)
Zscaler recommends using NULL encryption for Phase 2 because it reduces the local router/firewall load for traffic destined for the internet. If you want to use AES, you can purchase a separate subscription.
- Repeat this procedure for the backup tunnel.
After configuring both tunnels, you can go to **VPN **>** IPsec **>** Tunnels** to view them.
[See image.](#vpn-setup-ikev2-tunnels)
[]Define the IPv4 policies to allow access to the newly configured tunnels.
- Go to **Policy & Objects **>** Policy **>** IPv4**.
-
Click **Create New**.
[See image.](#ipv4-policy-create-new)
-
Create a new policy rule to allow the Zscaler primary tunnel access to the Fortigate external interface (wan1). In this example, we are forwarding all traffic to the service.
[See image.](#ipv4-new-policy-rule)
If you want to forward only HTTP and HTTPS traffic to the Zscaler service, select them in the **Service** field.
-
Create a new policy rule to allow internal network access to the Zscaler primary tunnel.
[See image.](#ipv4-new-policy-internal-network)
- Repeat this procedure to configure similar policy rules for the backup tunnel.
Once all four policies are defined, you can go to **Policy & Objects **>** Policy **>** IPv4** to view them.
[See image.](#ipv4-four-configured-policies)
[]Establish static routes for the primary and backup tunnels and configure them with the same priority and distance as the default route.
- Go to **Network **>** Static Routes**.
-
Click **Create New**.
[See image.](#static-routes-create-new)
-
Define the primary tunnel route as shown in the following image. Ensure that this tunnel gets an equal distance and a larger priority value than the default route. A tunnel with a larger priority value has a lower priority. The PBR overrides that priority setting. Since there are two tunnels, the primary tunnel priority value must have a lower priority than the secondary tunnel.
[See image.](#static-primary-tunnel-route)
-
Define the secondary tunnel route as shown in the following figure:
[See image.](#static-secondary-tunnel-route)
After establishing the static routes, you can go to** Monitor **>** Routing Monitor** and verify the routing table.
[See image.](#static-route-status)
[]Define a policy route for each tunnel. In this example, we are forwarding all traffic to Zscaler.
- Go to **Network **>** Policy Routes**.
- Define the primary tunnel as shown in the following image:
[See image.](#policy-route-status)
If you want to forward only HTTP and HTTPS traffic to the Zscaler service:
- Select port 80 as the destination port and define rules for the primary and secondary tunnels.
- Define similar rules that specify port 443 as the destination port.
[]![Screenshot of the Create New button in the Tunnels content pane](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/Fortigate_300E_create_ipsec-tunnel.png)
[]![Screenshot of the configured VPN Setup window in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigare_300E_vpn_setup_ikev2.png)
[![Screenshot of the IPSec tunnel configuration in the FortiGate 300E VPN setup Network section](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ikev2_vpn_setup_network_section.png)
]
[]
[![Screenshot of the IPSec tunnel configuration in the FortiGate 300E Authentication section](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ikev2_vpn_setup_authentication_section.png)
]
[]
[![Screenshot of the IPSec tunnel configuration in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ikev2_vpn_setup_phase1-proposal.png)
]
[]
![Screenshot of the configured primary and secondary IPSec tunnels in the Tunnels content pane](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigare_300E_ikev2_vpn_setup_tunnels_content.png)
[]
[![Screenshot of the Create New button in the IPv4 content pane](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ipv4_policy_create_new.png)
]
[]
[![Screenshot of the first configured IPv4 policy in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ipv4_policy_new_policy_rule.png)
]
[]
[![Screenshot of the second configured IPv4 policy in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ipv4_policy_new_policy_internal_network.png)
]
[]
[![Screenshot of four configured IPv4 policies in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_ipv4_four_configured_policies.png)
]
[]
[![Screenshot of the Create New button in the Static Routes pane](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_static_routes_create_new.png)
]
[]
[![Screenshot of the configured static route for the primary IPSec tunnel](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_static_primary_tunnel_route.png)
]
[]
[![Screenshot of the configured static route for the secondary IPSec tunnel](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_static_secondary_tunnel_route.png)
]
[]
[![Screenshot of the Routing Monitor content pane](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_routing_monitor_status.png)
]
[]
[![Screenshot of the configured policy route in the FortiGate 300E](/downloads/zia/traffic-forwarding/ipsec/ipsec-vpn-configuration-guide-fortigate-60d-firewall/fortigate_300E_policy_route_status.png)
]
[]