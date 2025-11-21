# Deploying on a VMware Virtual Machine
Source: https://help.zscaler.com/zero-trust-branch/deploying-vmware-virtual-machine
PDF: https://help.zscaler.com/pdf/com/en/1509401.pdf

Zero Trust Branch appliances can be deployed as a virtual machine (VM) over VMware ESXi.
Prerequisites
- [Hardware Requirements](#hardware)
- [Software Requirements](#software)
- [Internet Connectivity](#connect)
- [Typical Setup](#sample)
Configuration
Follow these steps to configure Zero Trust Branch on a VM:
- [Step 1: Configure VMware ESXi.](#config-esxi)
- [Step 2: Provision the Zero Trust Branch appliance and install.](#provision-gw)
- [Step 3: Configure the WAN port.](#config-wan)
- [Step 4: Activate branch appliance Zero Trust Branch appliances.](#activate-gw)
- [Step 5: Configure VLAN.](#config-vlan)
- []Create two port groups (e.g. LAN and WAN port group). The LAN port group must be configured as a trunk port group (e.g., VLAN ID = 4095) and the WAN port group as an access port group (specific VLAN ID).
- Ensure the security settings for the LAN port group allow promiscuous mode, forged transmits, and MAC address change.
- The WAN port group must be in the same VLAN as the upstream firewall/router.
[This recording](https://www.loom.com/share/22a0e548c5a74bdca136f0bae9ecf65c?sid=fed581fa-4df9-4394-960b-c18543bf824a) shows how to create two port groups: "Airgap WAN" with VLAN ID 150, and "Airgap LAN" with VLAN ID 4095. Note that if Zero Trust Branch protection is deployed across multiple VLANs, the VLAN ID for the LAN port group must be 4095.
[]Follow these steps to create a new VM in the ESXi server:
- Ensure that the VM specifications meet the requirements listed in [Hardware Requirements](#hardware).
- Select Linux and Ubuntu 64-bit as the OS type during the **Create new VM **workflow.
- Ensure that two NICs are attached to the VM. The first NIC must be in the LAN port group, and the second NIC must be in the WAN port group.
- During the installation, select **eth1 **as the preferred interface for connecting to the internet. This allows security updates to be downloaded during the installation.
[This recording](https://www.loom.com/share/85df287589934087a871f1b7682412a8?sid=22b35d8b-980a-4d14-9554-ed2b8cb68565) shows the provisioning process.
[]Zscaler recommends that you connect the WAN port group to the network and ensure internet connectivity is active. Do the following:
- Log in to the branch appliance via the VMware console using the default credentials.
- Branch appliances communicate with various AWS public cloud services such as RDS, ALB, and Elastic over the WAN uplink. These connections can be aggregated into a single outgoing connection via Zero Trust Branch-hosted forward proxy (e.g., `hub3.goairgap.com` on TCP port 1883). To configure this proxy setting, select option `2` in the **Configure Gateway** menu of the gateway command line interface.
- After configuring the IP address and proxy, and establishing internet connectivity for the branch appliance, a 6-digit code displays in the gateway command line interface.
[This recording](https://www.loom.com/share/d06055ffc6264ff496816156e563f978?sid=7f123f8a-9931-4926-bd88-fe567aad834c) shows the WAN configuration process.
[][Zero Trust Branch ]configuration, policy management, logging, and reporting are managed via the SaaS-based Zero Trust Branch Admin Portal.
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
- **NAT Enable**: (Optional) Select this checkbox if your [branch appliance uses NAT to route all the traffic leaving the branch appliance toward the non-Zero Trust Branch network.
- **Activation Code**: Enter the code you received when you [configured the WAN port](#config-wan). It can take 5 to 10 minutes to activate and provision the appropriate microservices.
- **WAN Virtual IP**: Enter the floating IP address to be used between two branch appliances.
- **WAN VRRP Group ID (1 - 255**): Enter a number between 1–255 to uniquely identify the WAN router.
- Click **Add**.
[See image.](#add-gateway-image)
- Similarly, create another VM and activate it as a standby:
- On the **Gateway** page, click the **Gear **icon for the gateway that you want to make a standby.
- Select **Add Standby Gateway** from the menu.
- Provide the standby gateway name and 6-digit code from the newly installed VM.
[][Zero Trust Branch ]deployment is not complete until the VLAN to be protected is enabled in the Zero Trust Branch Admin Portal. Ensure that a LAN port is connected to the switch and that it is in the same VLAN as the devices (broadcast packets from the devices must reach the LAN port).
- Go to **Networking > VLANs**.
-
Select the site where the Zero Trust Branch-protected VLAN is configured, and click **Add VLAN**.
[See image.](#vlans-image)
-
In the **Add VLAN** panel, complete the information for this VLAN. For an untagged port, enter `1` in the **VLAN Tag** field.
[See image.](#add-vlan-image)
-
If you are using an existing production VLAN, make sure that the default gateway IP address is the same as the existing Switch Virtual Interface (SVI) address for that VLAN.
[This recording](https://www.loom.com/share/6677958ff3b84ba0bc5e60d0c5cab544?sid=c9017339-b5d7-4ef0-9772-d819a50604b0) shows how to add a VLAN.
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
[]![Adding and updating network gateways on the Gateways page.](/downloads/device-segmentation/deploying-device-segmentation-devices/deployment-overview/gateways.png)
[]![Add Gateway panel.](/downloads/device-segmentation/deploying-device-segmentation-devices/deployment-overview/add-gateway.png)
[]![VLANs page.](/downloads/device-segmentation/deploying-device-segmentation-devices/deployment-overview/vlans.png)
[]![Add VLAN panel.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-virtual-machine/add-vlan.png)
[]
|  | **Option 1** | **Option 2** |
| --- | ------------ | ------------ |
| CPU | 4 vCPU | 8 vCPU |
| Memory | 16 GB | 32 GB |
| Storage | 256 GB | 256 GB |
| Ports | 4x vNICs | 4x vNICs |
| Throughput (64KB HTTP) | 10 Gbps | 20 Gbps |
| Sessions | 500K | 1 million |
| Number of Endpoints | 500 | 1,000 |
[]
VM deployment of Zscaler Zero Trust Branch appliances has two interfaces (LAN and WAN). Hypervisor ESXi must be configured as follows:
- LAN/Airgap Port Group: A new port-group is created for the Airgapping VLAN, and the Airgap LAN interface/NIC1 is part of this newly created port group. Configure the following security settings on the newly created port group:
- Enable **Promiscuous Mode**.
- Enable **MAC Address Change**.
- Enable **Forged Transmits**.
- If deployed for multiple VLANs, the VLAN ID for the port group is 4095 (Trunk VLAN).
- WAN Port Group: Zero Trust Branch connects back to the existing network and interfaces via NIC2/WAN interface. Either the existing port group or new port group that has untagged access on the ESXi servers is used to connect back to the existing network.
[]
Branch appliances need internet connectivity to be activated, retrieve the configuration, synchronize policies, and stream logs with the Zero Trust Branch Admin Portal. Ensure the appliances are allowed to send the outbound TCP and UDP packets over the following ports and protocols:
- `hub3.goairgap.com` (TCP:1883)
- `wg.goairgap.com` (UDP:51820)
[]
![Image showing typical VMware virtual machine deployment.](/downloads/device-segmentation/deploying-device-segmentation-devices/deploying-virtual-machine/sample%20vm%20setup.png)