# Creating a Zero Trust Branch High Availability Cluster
Source: https://help.zscaler.com/zero-trust-branch/creating-zero-trust-branch-high-availability-cluster
PDF: https://help.zscaler.com/pdf/com/en/1533622.pdf

A Zscaler Zero Trust Branch high availability (HA) cluster consists of two identical Zero Trust Branch appliances (or *nodes*). One node is the primary node and has the active role. The other node is the secondary node and has the standby role. If the primary node fails, the secondary node takes over as the primary, active node. The nodes coordinate stateful failover and traffic handling using protocols such as traffic session state synchronization and Virtual Router Redundancy Protocol (VRRP).
- Traffic session state synchronization enables seamless, stateful failover between the nodes. This ensures uninterrupted service for session-based applications such as SSH, SCP, FTP, and HTTP during node failovers. The session state information on the primary node is continuously synchronized to the secondary node to ensure that it has up-to-date session data to seamlessly continue traffic processing if the primary node fails.
- VRRP determines the active and standby roles of the nodes, monitors the health and availability of the nodes, and initiates a failover when necessary. When VRRP detects a node failure and triggers a failover, the new active node uses the synchronized session data to maintain ongoing traffic sessions without disruption.
Prerequisites
Make sure the following prerequisites are met:
- Dedicate an unused VLAN for HA only.
- Configure two ports on the switch for that VLAN.
-
Connect a cable from the GE4 port of each appliance to one of the two ports on the switch.
The two appliances are connected to each other via a switch, not via a crossover cable that connects them directly.
Topology Diagram
The following sections provide a diagram depicting the topology of an HA cluster deployment and a description of its components and flow.
- [Topology diagram](#diagram)
- [Topology details](#details)
Creating a Cluster
To create and activate a cluster:
- [Step 1: Add a Template](#template)
- [Step 2: Add a Site](#site)
- [Step 3: Activate the Gateways](#gateways)
- [Step 4: (Optional) Configure VRRP](#VRRP)
[]![Topology diagram with two Zero Trust Branch appliances in the cluster, connected to each other via a LAN and the GE ports on a switch, and connected to the endpoint devices via a separate LAN](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/creating-zero-trust-branch-high-availability-cluster-draft-doc-59917/ha_topology.png)
[]
- The LAN segment hosts the endpoints that the HA cluster manages and secures.
- The Zero Trust Branch HA cluster consists of two identical Zero Trust Branch appliances configured for HA.
-
The appliances use a dedicated HA interface, and are connected to a switch via the GE4 port. TCP, UDP, and ICMP connections are synchronized between the nodes using this link. To learn more, see [Zero Trust Branch Physical Port Mapping](/zero-trust-branch/zero-trust-branch-physical-port-mapping).
This is the only supported way to connect the appliances. If you connect the appliances to each other directly, the failover does not function properly.
- The WAN uplink allows secure communication with Zero Trust Branch management and other external networks.
[]You must use an HA template to launch a Zero Trust Branch cluster. You can use a default HA template or create a custom template. To create a custom template:
- In the Zero Trust Branch Admin Portal, go to **Resources **> **Templates**.
-
Complete the [Add a New Template](/zero-trust-branch/managing-templates#add) procedure, ensuring that you select **standard_mode_ha** for the **Deployment Type.**
[See image.](#addTemplate)
[]When you add a site in a Zero Trust Branch HA deployment, you configure a gateway for each appliance.
- Go to **Deployments **> **Sites**.
- Complete the [Add a Site](/tech-pubs-drafts/adding-site-draft-doc-60374) procedure, ensuring that you select the default HA template or a custom HA template, and configure both gateways.
-
On the **Sites **page, review the site details. Both gateways are in a **Disconnected **state because they have not been activated.
[See image.](#no_activatedGateways)
[]
The example used in this procedure shows how to activate one gateway and is not intended to represent the cluster setup described in this article. Repeat this procedure for the secondary node. The gateway that is activated first becomes the primary node and the other gateway becomes the secondary node.
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
On the **Sites **page, you can observe the activation process, which goes through several states, such as **Initializing **and **Post-update**. When both gateways are activated, the primary gateway state is **Active **and the secondary gateway state is **Standby**.
[See image.](#activatedGateways)
[]You can configure a password and additional settings to prevent other devices using VRRP from communicating with the nodes in the HA cluster. To learn more, see [Configuring a High Availability Site with Virtual Router Redundancy Protocol](/zero-trust-branch/configuring-ha-site-vrrp).
[]![Add Template panel showing configuration of a new custom template for an HA cluster](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/creating-zero-trust-branch-high-availability-cluster-draft-doc-59917/template.png)
[]![Sites page details for an HA cluster where both gateways are in the Disconnected state because they are not activated](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/creating-zero-trust-branch-high-availability-cluster-draft-doc-59917/gatewaysNotActivated.png)
[]![Sites page details for an HA cluster where both gateways are activated. One gateway is in the Active state and the other gateway is in the Standby state.](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/creating-zero-trust-branch-high-availability-cluster-draft-doc-59917/activeGateways.png)