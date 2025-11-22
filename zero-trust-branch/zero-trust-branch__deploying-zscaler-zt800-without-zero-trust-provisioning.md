# Deploying on a Zscaler ZT800 without Zero Touch Provisioning
Source: https://help.zscaler.com/zero-trust-branch/deploying-zscaler-zt800-without-zero-trust-provisioning
PDF: https://help.zscaler.com/pdf/com/en/1509601.pdf

Zero Trust Branch appliances can be deployed on a ZT800 device without using Zero Touch Provisioning for version 7.8 or earlier.
Prerequisites
- [Hardware Specifications](#hardware)
- [Network Information](#network)
- [Typical Setup](#typical-setup)
Configuration
The steps below describe how to configure Zero Trust Branch on a Zscaler ZT800 when using version 7.8 or earlier.
- [Step 1: Connect to a Zscaler ZT800.](#connect-zt800)
- [Step 2: Configure the WAN port.](#config-wan)
- [Step 3: Activate Zero Trust Branch appliances.](#activate-gw)
- [Step 4: Configure Zero Trust Branch appliance LAN.](#config-lan)
- [Step 5: Configure VLAN.](#config-vlan)
[]When deployed on a Zscaler ZT800, Zero Trust Branch uses six 1GbE RJ45 ports and two 1GbE SFP ports. Any two of these can be configured as LAN (device-side) and WAN (firewall-/router-side) ports.
Connect a laptop to the management port of the branch appliance over the RJ45 cable. Configure your laptop’s Ethernet interface with a static IP address in the subnet of 192.168.99.0/24 (e.g., 192.168.99.10).
- Log in to the branch appliance over SSH using the default management IP address and credentials. You can also connect to the branch appliance over the serial RJ45 console port.
- In the gateway command line interface, configure the LAN and WAN ports. Select `1` to configure the branch appliance and `1` to configure the network. Review [this recording](https://www.loom.com/share/9ea0049d436d4116997dc92e42eeab4d?sid=44a4b036-6e01-40ac-9857-e7176c74a96d) for more information.
- Select the LAN and WAN interface from the available options.
[]Zscaler recommends that you connect the WAN port group to the network and ensure internet connectivity is active.
-
Connect the switchport on the WAN side to the untagged or access port and refer to the following sample Cisco configuration. In this example, the switchport (Ge1/1/5) connecting to the WAN side of Zero Trust Branch is part of the VLAN445 and is configured as an access port.
`interface GigabitEthernet1/1/5
switchport access vlan 445
switchport mode access`
- The WAN port can be configured with the static address or the DHCP. Virtual IP address is a floating IP address shared across both branch appliances when configured in the HA pair. Review [this recording](https://www.loom.com/share/9ea0049d436d4116997dc92e42eeab4d?sid=4b4d899b-cd31-4454-9df4-ddbf4cab10fc) where enp8s0f0 and enp10s0f0 are 1GbE interfaces and configured as a LAN/WAN interface.
- Branch appliances communicate with various AWS public cloud services such as RDS, ALB, and Elastic over the WAN uplink. These connections can be aggregated into a single outgoing connection via Zero Trust Branch-hosted forward proxy (e.g., `hub3.goairgap.com`) on TCP port 1883. To configure this proxy setting, select option `2` in the **Configure Gateway** menu of the gateway command line interface.
- After configuring the IP address and proxy, and establishing internet connectivity for the branch appliance, a 6-digit code displays in the gateway command line interface.
[]Branch appliance configuration, policy management, logging, and reporting are managed via the SaaS-based Zero Trust Branch Admin Portal.
To activate the branch appliance:
- Go to **Networking > Gateways.**
-
Click **Add Gateway**.
[See image.](#gateways-image)
-
In the **Add Gateway** panel, complete the following information:
- **Location**: Select the location for this branch appliance, or select **Add New Location**.
- **Name**: (Optional) If adding a new location, enter a name for the location.
- **Gateway Name**: Enter a name for the branch appliance.
- **DHCP Service**: Select **DHCP Server** or **DHCP Relay**, based on whether the branch appliance is a DHCP server or relay to your existing DHCP server.
- **NAT Enable**: (Optional) Select this checkbox if your branch appliance uses NAT to route all the traffic leaving the branch appliance toward the non-Zero Trust Branch network.
- **Activation Code**: Enter the code you received when you [configured the WAN port](#config-wan). It can take 5 to 10 minutes to activate and provision the appropriate microservices.
- **WAN Virtual IP**: Enter the floating IP address to be used between two branch appliances.
- **WAN VRRP Group ID (1 - 255**): Enter a number between 1–255 to uniquely identify the WAN router.
- Click **Add**.
[This recording](https://www.loom.com/share/894d129cae994d939de9e64ed98ba4ff?sid=67950ff9-4826-4237-9620-7f07c5e7fdc0) shows the gateway activation process.
[See image.](#add-gateway-image)
- To deploy the branch appliance's high-availability pair, configure another appliance and activate it as a standby gateway using the following steps:
- On the **Gateway** page, click the **Gear **icon for the gateway that you want to make a standby.
- Select **Add Standby Gateway** from the menu.
- Provide the standby gateway name, 6-digit code from the newly installed VM, and WAN virtual IP address and group ID number as described in the previous step.
- Click **Add**.
[]A single cluster of branch appliances can be deployed to protect multiple VLANs. To process multiple VLANs, the switchport connecting to the LAN-side interface of the branch appliance must be configured as a trunk port, and it must allow the VLANs that need to be protected by Zero Trust Branch.
The following is a sample Cisco configuration of a switchport connecting to the LAN side of branch appliances. In this example, Ge1/1/4 is connected to the LAN side, is configured with trunk, and allows VLAN 226 and VLAN 227.
`interface GigabitEthernet1/1/4
switchport trunk allowed vlan 226,227
switchport mode trunk`
[]Zero Trust Branch deployment is not complete until the VLAN to be protected is enabled in the Zero Trust Branch Admin Portal. Ensure that a LAN port is connected to the switch and that it is in the same VLAN as the devices (broadcast packets from the devices must reach the LAN port). This section describes how to configure Zero Trust Branch to receive traffic from VLAN 226 and VLAN 227 and protect devices connected to those VLANs.
- Go to **Networking > VLANs**.
-
Select the site where the Zero Trust Branch-protected VLAN is configured, and click **Add VLAN**.
[See image.](#vlans-image)
-
In the **Add VLAN** panel, complete the information for this VLAN. For an untagged port, enter `1` in the **VLAN Tag** field.
[See image.](#add-vlan-image)
-
If you are using an existing production VLAN, make sure that the default gateway IP address is the same as the existing Switch Virtual Interface (SVI) address for that VLAN.
[This recording](https://www.loom.com/share/6677958ff3b84ba0bc5e60d0c5cab544?sid=67dc69db-238e-4884-88f3-08bc07d2ac22) shows how to add a VLAN.
-
Log in to your existing L2/L3 switch, router, or firewall, and shut down the SVI/VLAN interface. Add a return route for VLAN with Zero Trust Branch WAN Virtual IP address as a next hop. Here are sample Cisco commands (for VLAN 226 with subnet mask 10.16.226.0/24):
`#conf t
#int vlan 226
#shutdown
#exit
#ip route 10.16.226.0 255.255.255.0 < airgap-wan-vip >`
-
Turn on the VLAN in the Zero Trust Branch Admin Portal.
By default, the VLANs are created in the staged state. Each VLAN must be enabled to configure it into the branch appliances.
The DHCP Service option provides DHCP service ON/OFF and non-airgapped options:
- DHCP Service ON: The branch appliance assigns the IP address and `/32` net mask and ringfences the endpoints in the VLAN.
- DHCP Service OFF: The branch appliance acts as a DHCP relay and modifies the DHCP response to `/32` net mask and ringfences all the endpoints in the VLAN.
- Non-Airgapped: The branch appliance assigns the net mask as per the default configured network subnet mask or network mask received from the DHCP servers. It does not ringfence the endpoints. However, the admin can still create segmentation policies based on network and group-level policies.
[]![Adding and updating network gateways on the Gateways page.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-zscaler-zts2000/gateways.png)
[]![Add Gateway panel.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-zscaler-zts2000/add-gateway.png)
[]![VLANs page.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-zscaler-zts2000/vlans.png)
[]![Add VLAN panel.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-virtual-machine/add-vlan.png)
[]
-
-
-
-
-
| Parameter | Specification |
| --------- | ------------- |
| CPU | 8C Atom |
| Memory | 16 GB |
| Storage | 256 GB |
| Ports | 6x 1GbE2x 1GbE small form-factor pluggable (SFP)Supported SFPs:Finisar FCLF8522P2BTLFinisar FTLF8519P3BNLFinisar FTLF1318P3BTL |
| Form Factor | Desktop |
| Throughput (64KB HTTP) | 6 Gbps |
| Sessions | 500K |
| Number of Endpoints | 750 |
[]
-
-
| Details | Value | Description |
| ------- | ----- | ----------- |
| Site/Location Name | <name> | Site or branch name. |
| Branch Appliance Names | <name1>, <name2> | Appliance names. |
| Zero Trust Branch WAN/Uplink IPs | <IP1>, <IP2> | Zero Trust Branch upstream/WAN/NIC. Two IP addresses must be in the existing network. Three IP addresses are required for the high availability deployment. |
| Appliance Default Gateway | <IP> | Default gateways for the branch appliances. |
| DNS Servers | <IP1>, <IP2> | Enterprise private DNS server IP addresses that must be assigned to devices in the Zero Trust Branch network. |
| DHCP Servers | <IP1>, <IP2> | DHCP servers to which DHCP requests are relayed. Ensure that you have a pool assigned for Zero Trust Branch VLANs. |
| Internet Connectivity | `hub3.goairgap.com` (TCP:1883)`wg.goairgap.com` (UDP:51820) | Branch appliances require internet connectivity using these outbound TCP and UDP ports. |
[]
Port Configuration
[]![Port configuration for a ZT800](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-zscaler-zts2000/Hardware_Zscaler-ZTS2000_Rear_Callouts.png)
The ZT800 has the following ports:
- Serial RJ45 Console Port: You can use PuTTY or similar serial console application to access the Zero Trust Branch console. Use the following settings for proper serial connection:
- Baud Rate: 115,200
- Data Bits: 8
- Parity: None
- Stop Bits: 1
- Flow Control: Off
- enp2s0f0 - 1GbE SFP LAN/WAN Port
- enp2s0f1 - 1GbE SFP LAN/WAN Port
- enp2s0f2 - Reserved
- Management Port (enp2s0f3): Out-of-band management port with a fixed address of 192.168.99.99/24.
- enp8s0f0 - 1GbE Port
- enp8s0f1 - 1GbE Port
- enp10s0f0 - 1GbE Port
- enp10s0f1 - 1GbE Port
Ports 1, 2, and 6–9 can be used as either LAN or WAN ports.
- When used as LAN ports, device-side interfaces connected to the L2 switch via the trunk interface with Zero Trust Branch-protected VLANs allowed as member ports. The LAN port acts as the default gateway for both Zero Trust Branch-protected VLANs and devices.
- When used as WAN ports, the upstream interface connects to the L2 switch as an untagged port in the same VLAN as the upstream firewall or L2/L3 switch. All internet-bound or non-Zero Trust Branch destined traffic is routed to the network/VLAN after the policy check.