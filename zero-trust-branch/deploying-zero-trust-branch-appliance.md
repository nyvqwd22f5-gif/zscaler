# Deploying a Zero Trust Branch Appliance
Source: https://help.zscaler.com/zero-trust-branch/deploying-zero-trust-branch-appliance
PDF: https://help.zscaler.com/pdf/com/en/1532526.pdf

You can deploy Zero Trust Branch and pass traffic through it with minimal configuration because:
- The Zero Trust Branch appliance automatically establishes an IPSec tunnel to Zscaler Internet Access (ZIA) via the GE3 WAN port.
- The default Zscaler routing policy allows traffic to be sent to ZIA.
- The default (system) firewall policy allows traffic over LANs and WANs.
Prerequisites
Make sure the following prerequisites are met:
- [Verify That Your Tenant Is Provisioned](#VerifyTenant)
- [Review the Device Port Mapping](#PortMapping)
- [Determine the Template to Use](#DetermineTemplate)
- [Determine the Interfaces to Use](#DetermineInterfaces)
- [Open Ports on the Upstream Device](#OpenPorts)
- [Verify Internet Connectivity for the Primary WAN Interface](#VerifyConnectivity)
- [Gather Details for the Configuration](#GatherDetails)
Deploying Zero Trust Branch
To deploy Zero Trust Branch, complete the following steps:
- [Step 1: Mount and Cable the Appliance](#MountCable)
- [Step 2: Change the Default Password](#Password)
- [Step 3: Clone and Modify a Template](#Template)
- [Step 4: Add a Site](#Site)
- [Step 5: Activate the Appliance](#Activate)
- [Step 6: Configure the LAN Interface](#LAN)
- [Step 7: Configure the VLAN](#VLAN)
- [Step 8. Verify the Deployment](#Verification)
[]Verify that Zscaler provisioned your tenant. If not, contact your Zscaler account team. After the tenant is provisioned, Zscaler sends the super admin an email invitation that must be accepted. The super admin can then log in to the Zero Trust Branch Admin Portal.
[]Review the port mapping on your appliance model. To learn more, see [Zero Trust Branch Physical Appliance Port Mapping](/zero-trust-branch/zero-trust-branch-physical-port-mapping).
[]Each site uses a single template, which defines the Zero Trust Branch model to be deployed at the site and configuration settings such as the DNS server address, DHCP service type, deployment type, platform, and NAT enablement. Choose from one of the following options:
- Clone the default template or an existing template, save it with a new name, and customize it (recommended). To find a template to clone, search for templates matching your Zero Trust Branch model number.
- Use the default template for your site.
- Create your own template from scratch.To learn more, see [Managing Templates](/zero-trust-branch/managing-templates).
[]The following table shows the interfaces that each Zero Trust Branch model uses in a high availability (HA) deployment. The interfaces with an asterisk (*) are fixed and cannot be changed, even on cloned templates.
The GE4 interface is fixed in an HA deployment, but in a standalone deployment it can be used for LAN. All other interfaces with an asterisk are fixed in a standalone deployment as well.
| Purpose | ZT400 | ZT600 | ZT800 | ZT8010 |
| ------- | ----- | ----- | ----- | ------ |
| Management | GE1* | GE1* | GE3* | GE1* |
| LAN | GE2 | GE2, GE3 | GE1, GE5, GE6 | GE3, GE5, GE6, XE11, XE12, XE13, XE14 |
| WAN | GE3* | GE2, GE5* | GE2*, GE7, GE8 | GE2*, XE7, XE8, XE9, XE10 |
| HA | GE4* | GE4* | GE4* | GE4* |
[]A Zero Trust Branch appliance uses proxy hub3.goairgap.com:1883 for activation and the management plane. When you activate a new site, all required ports and protocols override the proxy, so you only need to open the ports and protocols in bold on the upstream firewall or other L3 device.
| Application or Service | Inbound/Outbound | Port | URL or IP Address |
| ---------------------- | ---------------- | ---- | ----------------- |
| Zero Trust Branch Admin Portal | Outbound | TCP 443 | <tenant name>.goairgap.com |
| Zero Trust Branch API | Outbound | TCP 443 | <tenant name>.api.goairgap.com |
| Internal device management for the customer network | Inbound/Outbound | ICMP/SSH | Management IP address |
| Amazon Web Services (AWS) Global Accelerator for Zero Trust Branch Admin Portal performance | Outbound | TCP 80 | *.awsglobalaccelerator.com |
| Docker repository to pull container images | Outbound | TCP 443 | docker.repos.goairgap.com |
| WAN monitoring | Outbound | TCP 443 | gateway.<cloud>.netDefault: gateway.zscaler.net`curl `command: https://gateway.zscalerthree.net/get_loc |
| Routed tunnel: Bidirectional forwarding detection (BFD), spoke-to-hub data traffic, border gateway protocol (BGP) | Inbound | UDP 443 | Spoke-reachable IP address |
| Zscaler Internet Access (ZIA) | Outbound | GRE Protocol 47UDP 500UDP 4500 | https://config.zscaler.com/zscaler.net/cenrhttps://config.zscaler.com/zscalertwo.net/cenrpac.zscaler.net;gateway.zscaler.net |
| Zscaler Private Access (ZPA) | Outbound | TLS TCP 443 | https://config.zscaler.com/private.zscaler.com/zpaprod.zpath.net:private.zscaler.com |
| Zero Trust Branch gateway activation | Outbound | TCP 443 | gwactivation.goairgap.com |
| Management plane | Outbound | TCP 1883 | hub3.goairgap.com |
| **Remote management** | **Outbound** | **UDP 51820** | **wg.goairgap.com** |
| **Public DNS server IP addresses** | **Outbound** | **UDP 53** | **1.1.1.1, 8.8.8.8** |
| **NTP** | **Outbound** | **UDP 123** | **0.pool.ntg.org, 1.pool.ntg.org, 2.pool.ntg.org, 3.pool.ntg.org** |
[]Test that the primary WAN interface can reach the internet.
[]Collect the following information:
- For each interface that is statically configured, collect the IP address, mask, gateway, and primary and secondary DNS servers.
- If the Zero Trust Branch appliance is to operate as a DHCP server, collect the scope that will be used, the DNS server IP addresses, the LAN interface IP address (or IP addresses if there is more than one LAN interface), and the corresponding VLAN (or VLANs if there is more than one VLAN on the LAN side).
- If the Zero Trust Branch appliance is to operate as a DHCP relay, collect the IP address of the DHCP server.
[]
To mount and cable the appliance:
- Review the package contents and mount the Zero Trust Branch appliance using the instruction manual for your model. To learn more, see [Zero Trust Branch Appliances Wall and Rack Mount Instruction Manual](/zero-trust-branch/zero-trust-branch-appliances-wall-and-rack-mount-instruction-manual).
- Cable the appliance based on the [interfaces that you decided to use](#DetermineInterfaces).
[]To connect to the console port and change the default admin password:
- Download an SSH, telnet, and terminal emulator client such as PuTTY, Minicom, screen2, SecureCRT, Terminus, or ZOC Terminal.
- Connect one end of the serial console cable to your laptop, and make sure the other end is connected to the console port on the appliance.
- Establish a serial connection using the following parameters:
- **Baud Rate**: 115,200
- **Data Bits**: 8
- **Stop Bits**: 1
- **Parity**: None
- **Flow Control**: XON/XOFF
- Log in to the console using the default credentials:
- **Login ID**: `admin`
- **Password**: `a!rg@p`
- Enter `3` (Change Administrator Password) in the console menu and press `Enter`.
- Enter the current password and press `Enter`.
- Enter the new password and press `Enter`.
- Enter the new password again and press `Enter`.
- Press `Enter` to continue and to log out of the console.
- Use the new password to log in to the console.
[]Zscaler recommends that you clone a template and then modify it to meet your requirements. Alternatively, you can create a new template. To learn more, see [Managing Templates](/zero-trust-branch/managing-templates).
[]To learn more, see [Adding a Site](/zero-trust-branch/adding-site).
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
[]A Zero Trust Branch appliance can be deployed to protect multiple VLANs. To process multiple VLANs, the switchport connecting to the LAN-side interface of the Zero Trust Branch appliance must be configured as a trunk port, and it must allow the VLANs that need to be protected by Zero Trust Branch.
The following is an example configuration of a switchport connecting to the LAN side of the Zero Trust Branch appliance via the GE2 interface. The F0/5 interface is configured with trunk and allows VLANs 50, 60, 70, and 80. The laptop connects to the switch via the F0/4 interface, which is configured to allow access to VLAN 50.
`interface FastEthernet0/5
description connected to ZT400 Ge2
switchport trunk encapsulation dot1q
switchport trunk allowed clan 50,60,70,80
interface FastEthernet0/4
description connected to test laptop
switchport access vlan 50
switchport mode access
end`
[]
Zero Trust Branch deployment is not complete until the VLAN to be protected is enabled in the Zero Trust Branch Admin Portal. Ensure that a LAN port is connected to the switch and that it is in the same VLAN as the devices (i.e., broadcast packets from the devices must reach the LAN port). The following example describes how to configure Zero Trust Branch to receive traffic from VLANs 50, 60, 70, and 80 and protect devices connected to those VLANs.
[See image.](#diagram)
This procedure shows how to add a new VLAN. If you are using an existing production VLAN, make sure that the default gateway IP address is the same as the existing Switch Virtual Interface (SVI) address for that VLAN.
- In the Zero Trust Branch Admin Portal, go to **Deployments > Sites**.
-
Select the site that you activated, and click **Add Airgap VLAN**.
[See image.](#add-vlan)
-
In the **Add Airgap VLAN** panel, complete the information for this VLAN.
If you are configuring an untagged port, enter `1` in the **VLAN Tag** field.
[See image.](#add-vlan-panel)
- Click **Add**.
-
On the **VLANs **tab, in the **Disable/Enable** column, enable the VLAN.
[See image.](#enable-vlan)
-
Connect the laptop to the access port on the switch. In this example, you configured F0/4 as an access port on VLAN 50.
The laptop automatically gets an IP address within the DHCP range that you configured when you added the VLAN. All the Zero Trust Branch appliances connected to the switch have the same subnet mask, which provides device segmentation.
[]![Diagram showing a Zero Trust Branch appliance connected to the Zero Trust Exchange via the GE3 WAN port and to a switch via the GE2 LAN port. The F0/5 LAN interface is a trunk port allowing access to VLANs 50, 60, 70, and 80. The F0/4 interface is the access port on VLAN 50, which provides access to the laptop  ](/downloads/zero-trust-branch/deploying-zero-trust-branch/deploying-zero-trust-branch-appliance-draft-doc-59803/vlan-diagram.png)
[]![VLAN page for a site with the button to add a new VLAN](/downloads/zero-trust-branch/vlan/add-vlan.png)
[]![Panel used to add a new VLAN, including configuration of the gateway interface, interface IP, DHCP service, DHCP address range, and DNS servers](/downloads/zero-trust-branch/vlan/configure-a-vlan.png)
[]![VLAN page with a Disable/Enable switch to enable the new VLAN](/downloads/zero-trust-branch/vlan/enable-vlan.png)
[]To verify the Zero Trust Branch deployment:
- Open a browser and go to a few websites.
- Go to `ip.zscaler.com`.
- Observe that traffic from the laptop goes to the internet via ZIA:
- In the Zero Trust Branch Admin Portal, go to **Deployments **> **Sites **and select the site.
- Select **Settings** > **ZIA** > **IPSec Tunnels**.
- Verify the value in the **Status **column is **ESTABLISHED**.