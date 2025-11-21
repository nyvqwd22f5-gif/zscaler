# Virtual Service Edge Configuration Guide for Dual Arm Mode
Source: https://help.zscaler.com/zia/virtual-service-edge-configuration-guide-dual-arm-mode
PDF: https://help.zscaler.com/pdf/com/en/1401151.pdf

Use a dual arm configuration for your ZIA Virtual Service Edges if you have an environment that requires your Virtual Service Edges to use two zones: a disconnected network or isolate the internet zone from the internal users and another that faces the internet.
The dual arm configurations of Virtual Service Edges for your organization might be required in the following scenarios:
- [Deploying Virtual Service Edge using the dual arm configuration in standalone mode with external or no load balancer](#standalone-mode-with-external-or-no-lb)
- [Deploying Virtual Service Edge using the dual arm configuration in cluster mode with user traffic on one arm](#cluster-mode-with-user-traffic-on-one-arm)
- [Deploying Virtual Service Edge using the dual arm configuration in cluster mode with user traffic on both arms](#cluster-mode-with-user-traffic-on-both-arm)
Configuring Cluster IP
This configuration applies only to the dual arm configuration in cluster mode with user traffic in both arms.
After configuring the dual arm for Virtual Service Edge, you must configure cluster IP based on the preceding scenarios.
To configure cluster IP for Virtual Service Edges with dual arm configuration:
- [1. Add cluster IP parameters to the LB interface.](#cluster-ip-lb)
- [2. Add cluster IP parameters to the proxy interface.](#cluster-ip-proxy-ip)
- [3. Enable promiscuous mode for the LB interface.](#promiscuous-mode-lb)
- [4. Reboot Virtual Service Edge and start the services.](#reboot-vse)
After the new interfaces are assigned, ensure they are mapped to the correct VLAN by checking the MAC addresses, as the order might be different on the VM. Also, ensure the proper format is followed while assigning the custom routes in the vzen_custom.conf file so that the next hops are reachable.
You can test whether the cluster IP addresses are available and active for the following interfaces:
-
For the LB interface, run the following command:
`/sc/smlb/bin/smmgr -ys smnet="ifconfig :type any"`
- [See a sample output of this command](#sample-output-LB)
-
For the proxy interface, run the following command:
`/sc/sme/bin/smmgr -ys smnet="ifconfig :type any"`
- [See a sample output of this command](#sample-output-proxy)
[][root@perf-vzen ]:-$/sc/smlb/bin/smmgr -ys smnet="ifconfig :type any"
//+SHARED MEMORY KEY 17 (/sc/smlb/)
SMNET Interface Table
-----------------------
zs0:    flags=8903<UP,BROADCAST,PROMISC,SIMPLEX,MULTICAST>
(zs0)=em2 metric 0 mtu 1500 type 6 [0x80be00020/0xb91013fe010]
capabilities=db<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,POLLING,VLAN_HWCSUM>
capenable=9b<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,VLAN_HWCSUM>
HWassist 0x6    ether: 00:50:56:9b:5f:50
inet 10.66.105.68 netmask 0xffffff00 broadcast 10.66.105.255
media: [no carrier] Ethernet autoselect
Rx: Packets 18082863 Bytes 2776690390 Multicast 654535
Tx: Packets 78884 Bytes 7362836 Multicast 11195
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 50000
zs1:    flags=8903<UP,BROADCAST,PROMISC,SIMPLEX,MULTICAST>
(zs1)=em4 metric 0 mtu 1500 type 6 [0x80be004d0/0xb91013fde90]
capabilities=db<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,POLLING,VLAN_HWCSUM>
capenable=9b<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,VLAN_HWCSUM>
HWassist 0x6    ether: 00:50:56:9b:15:43
inet 10.66.2.71 netmask 0xffffff00 broadcast 10.66.2.255
media: [no carrier] Ethernet autoselect
Rx: Packets 326381 Bytes 26002247 Multicast 261962
Tx: Packets 107367 Bytes 10527037 Multicast 9411
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 50000
CARP-71:        flags=9<UP,LOOPBACK>
(carp127)(MASTER vhid=71 advbase=1 advskew=132 sc2ifp(flags/drv_flags 0x9/0x40)
vmac=00:00:5e:00:01:47
initial sha1 0xd1ca7dc7:0x9f0f47e9:0x9c48b1d5:0x7de0dff6:0x185ac373 counter 0x1/0x640aee2e7163cff3
cldname zscalerone.net sc_key )
metric 0 mtu 1500 type 248=0xf8 [0x80be00980/0xb91087ffad0]
HWassist 0x0    inet 10.66.105.71 netmask 0xffffffff
Rx: Packets 0 Bytes 0 Multicast 0
Tx: Packets 11193 Bytes 626808 Multicast 0
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 0
CARP-75:        flags=9<UP,LOOPBACK>
(carp128)(MASTER vhid=75 advbase=1 advskew=206 sc2ifp(flags/drv_flags 0x9/0x40)
vmac=00:00:5e:00:01:4b
initial sha1 0xd5467984:0x99d1aa36:0xefa02b:0x9219ef2d:0xf65ff620 counter 0x1/0x66932b974af664ee
cldname zscalerone.net sc_key )
metric 0 mtu 1500 type 248=0xf8 [0x80be00e30/0xb91087ff790]
HWassist 0x0    inet 10.66.2.75 netmask 0xffffffff
Rx: Packets 0 Bytes 0 Multicast 0
Tx: Packets 9409 Bytes 526904 Multicast 0
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 0
Profiler stats: tot calls=1, tot/min/max/avg cpu time=6863/6863/6863/6863 microseconds
[][root@perf-vzen ]:-$/sc/sme/bin/smmgr -ys smnet="ifconfig :type any"                                                                                              //+SHARED MEMORY KEY 17 (/sc/sme/)
SMNET Interface Table
-----------------------
ztun0:  flags=8811<UP,POINTOPOINT,SIMPLEX,MULTICAST>
(ztun0)metric 0 mtu 1400 type 23=0x17 [0x80be00020/0xb9100db4050]
HWassist 0x0    inet 10.66.105.71 --> 10.66.105.71 netmask 0xffffffff
Rx: Packets 0 Bytes 0 Multicast 0
Tx: Packets 1 Bytes 28 Multicast 1
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 100
zs0:    flags=8803<UP,BROADCAST,SIMPLEX,MULTICAST>
(zs0)=em1 metric 0 mtu 1500 type 6 [0x80be004d0/0xb91013fddd0]
capabilities=db<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,POLLING,VLAN_HWCSUM>
capenable=9b<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,VLAN_HWCSUM>
HWassist 0x6    ether: 00:50:56:9b:b8:9d
inet 10.66.105.67 netmask 0xffffff00 broadcast 10.66.105.255
media: [no carrier] Ethernet autoselect
Rx: Packets 518519 Bytes 33963109 Multicast 456548
Tx: Packets 65429 Bytes 6533314 Multicast 1
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 50000
zs1:    flags=8803<UP,BROADCAST,SIMPLEX,MULTICAST>
(zs1)=em3 metric 0 mtu 1500 type 6 [0x80be00980/0xb91013fdc50]
capabilities=db<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,POLLING,VLAN_HWCSUM>
capenable=9b<RXCSUM,TXCSUM,VLAN_MTU,VLAN_HWTAGGING,VLAN_HWCSUM>
HWassist 0x6    ether: 00:50:56:9b:27:7a
inet 10.66.2.70 netmask 0xffffff00 broadcast 10.66.2.255
media: [no carrier] Ethernet autoselect
Rx: Packets 290861 Bytes 29662943 Multicast 194589
Tx: Packets 121089 Bytes 13655929 Multicast 1
Error: Rx 0 Tx 0 RxMC_drop 0 Dropped 0 Collision 0 Unsup_Proto 0
Send queue: 0 of 50000 (0 drops) drv side 0 of 50000
Profiler stats: tot calls=1, tot/min/max/avg cpu time=4051/4051/4051/4051 microseconds
[]
- Log in to the VM.
-
Enter the following command:
`vi /sc/smlb/conf/vzen_custom.conf`
-
Edit the vzen_custom.conf file to add the following lines:
`[SME]
smlb_vserver="<Increment the vserv id present in /sc/smlb/conf/vzen.conf>"
smlb_cluster="<New smlb_vserver id - configured in the preceding line>,<VIP for em4 SMLB> -h1 -T -ea -db -es -em -m5 -s<SMEID - vserv id present in /sc/sme/conf/vzen.conf>,<Dual SME IP em3>"
smlb_monitor="5 -mi -i2 -r 5 -t 2 -w1 -W100"
[-end-of-SME-]`
Replace all text in red with the appropriate values.
Ensure to add the SMEID and SME IP to the `smlb_cluster` line for each of your Virtual Service Edges.
For example, to add cluster IP parameters to the LB interface:
`[SME]
smlb_vserver="32999"
smlb_cluster="32999,10.66.2.75 -h1 -T -ea -db -es -em -m5 -m3 -s32665,10.66.2.72 -s32678,10.66.2.70 "
smlb_monitor="5 -mi -i2 -r 5 -t 2 -w1 -W100"
[-end-of-SME-]`
[]
- Log in to the VM.
-
Enter the following command:
`vi /sc/sme/conf/vzen_custom.conf`
-
Edit the vzen_custom.conf file to add the following lines:
`[SME]
smlb_server="<New smlb_vserver id - configured in the preceding step> <SMEID - vserv id present in /sc/sme/conf/vzen.conf>"
smlb_cluster="<New smlb_vserver id - configured in the preceding step>,<VIP for em4 SMLB> -h1 -T -ea -db -es -em -m5 -s<SMEID - vserv id present in /sc/sme/conf/vzen.conf>,<Dual SME IP em3>"
[-end-of-SME-]`
Replace all text in red with the appropriate values.
Ensure to add the SMEID and SME IP to the `smlb_cluster` line for each of your Virtual Service Edges.
For example, to add cluster IP parameters to the proxy interface:
`[SME]
smlb_server="32999 32678"
smlb_cluster="32999,10.66.2.75 -h1 -T -ea -db -es -em -m5 -m3 -s32665,10.66.2.72 -s32678,10.66.2.70"
[-end-of-SME-]`
[]
- Log in to the VM.
-
Enter the following command:
`sudo vi /etc/rc.conf`
-
Add the following lines:
`ifconfig_em4="down promisc"
ifconfig_em2="down promisc"
network_interfaces="lo0 em0 em1 em2 em3 em4 em5"`
[]
- Log in to the VM.
-
Enter the following command:
`reboot`
This deployment is used when you expect the following in a standalone mode:
- Internal user traffic to access internal or external servers.
- Remote user traffic from the internet-facing side to access internal or external servers.
[]![Screenshot of ZIA Virtual Service Edge Dual Arm Configuration in Standalone Mode](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/virtual-service-edge-configuration-guide-dual-arm-mode/ZIA-Virtual-Service-Edge-Dual-Arm-Standalone-Mode.png)
To deploy the Virtual Service Edge using the dual arm configuration in standalone mode with external or no load balancer:
-
[1. Add the Virtual Service Edge instances.](/zia/adding-virtual-service-edge-instances)
You must add the internal-facing proxy IP address (i.e., em1) to the **Proxy IP Address** field and select **Standalone** for the **Deployment Mode** field.
- [2. Download the Virtual Service Edge VM.](/zia/downloading-virtual-service-edge-vm)
- [3. Download the Virtual Service Edge certificates.](/zia/downloading-virtual-service-edge-certificates)
- [4. Bind the standalone Virtual Service Edge to a location.](#bind-vse-location)
- [5. Create a firewall filtering rule to bypass Virtual Service Edge IP addresses.](#Firewall)
- [6. Configure a new VM on the VMware ESXi using the downloaded Virtual Service Edge VM.](#log-in-vmware-esxi)
- [7. Start the VM and create an IP plan.](#ip-plan-vm)
- [8. Prepare the vSphere.](#vsphere-without-lb)
- [9. Configure the DNS server, management interface em0, and default route out.](#config-dns-server)
- [10. Configure an additional proxy interface.](#additional-proxy-interface)
- [11. (Optional) Configure an additional management interface.](#additional-mgmt-interface)
- [12. Restart the Virtual Service Edge.](#restart-vse)
Ensure that the autostart for Virtual Service Edge services is enabled.
You can test this deployment by connecting to the em2 IP address and port 80. Alternatively, configure a browser with em2 (i.e., <em2 IP address>:80) and then send traffic and apply policies. The em2 serves the traffic to the internet. You can verify if the traffic is following the correct path using the PCAP files.
If `smnet_route` is configured, then the server is accessed through the em1 interface.
If SSL decryption is enabled, the ZZscaler root certificate must be installed. You can also disable authentication for servers without federated user identities.
[]Add a location and bind the standalone Virtual Service Edge to it so your organization can enable features such as authentication, firewall, SSL inspection, and location-level policies. The service associates the traffic that it receives on the Virtual Service Edge with its location and applies the features and policies configured for the location.
To bind a Virtual Service Edge to a location:
- Go to **Administration **>** Locations**.
-
Click **Add Location** or click the **Edit** icon for an existing location.
The **Add Location** or **Edit Location** window appears.
-
In the **Add Location** or **Edit Location** window, select the standalone Virtual Service Edge you want to bind to the location.
[See image.](#bind-vzen-cluster-location)
To learn more about the other fields, see [Configuring Locations](/zia/configuring-locations).
- Click **Save**.
[]****![Screenshot of Add Location window highlighting the Virtual Service Edges and Virtual Service Edge Clusters options.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-clusters/ZIA-add-location-virtual-service-edges-clusters.png)
****
[]Zscaler performs ICMP and HTTP monitoring from the switch/vswitch to the Virtual Service Edge to monitor the health of the Virtual Service Edge. For health probes to work, you must create a Firewall Filtering rule to allow all Virtual Service Edge proxies.
To create a Firewall Filtering rule:
- Go to **Policy** > **Firewall Control**.
-
Click **Add Firewall Filtering Rule**.
The **Add Firewall Filtering Rule **window appears.
- In **Add Firewall Filtering Rule **window, click the **Source IP** tab.
-
In **IP Addresses**, add the Proxy IP address for your Virtual Service Edges.
To learn more about the other fields, see [Configuring Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).
- Under **Network Traffic**, select **Allow**.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]
- Log in to the vSphere client.
- Go to **File **>** Deploy OVF Template**.
- Use the Deploy OVF Template wizard to deploy the Virtual Service Edge VM.
- Accept all defaults to import the Virtual Service Edge VM.
- Select the Virtual Service Edge VM and click either the **Power On** button or **Power On the virtual machine**.
-
On the **Console** tab, log in to the FreeBSD command prompt with the following credentials:
- Username: zsroot
- Password: zsroot
After you log in with the default credentials, you are prompted to change the default password.
-
Change the default password:
- **New Password**: Enter a new password that meets your organization's password standards.
- **Retype New Password**: Re-enter the new password.
[See image.](#ssh-in-browser)
Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
-
(Optional) If you want Zscaler to enforce password complexity for the password you set, run the following command:
`vzen enforce-password-complexity`
The current password expires after running this command.
[See image.](#password-complexity)
A valid password contains a mix of upper- and lowercase letters, numbers, and other characters. You can use a 24-character password with characters from at least three of these categories, or a 16-character password containing characters from all the categories. Characters that form a common pattern are discarded by the check. If you use a passphrase, use at least 4 words to form a phrase that is 32 to 40 characters long and contains enough different characters.
-
Run the following command to configure the network:
`sudo vzen configure-network`
- Specify the following information:
- Address of the DNS server (e.g., 10.84.0.100) used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic.
- Management interface IP with CIDR netmask. You use the management IP address (e.g., 10.84.0.110/24) for SSH or FTP.
- Default gateway IP address (e.g., 10.84.0.200).
- Hostname of the Virtual Service Edge
- Install the SSL certificates of the Virtual Service Edge instances. These are the certificates that you downloaded from the ZIA Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service. When you configure a Virtual Service Edge, ensure that you upload the correct certificate for each Virtual Service Edge instance.
- Go to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- On the vSphere client, click the **Console **tab, and log in with the following credentials:
Username: zsroot
Password: zsroot
- Go to the **Console **tab or use SSH to connect to the management IP address.
-
Run the following command:
`sudo vzen install-cert <cert-bundle.zip>`
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
- If you installed the Cavium NITROX card in your server:
- On the vSphere client, click the **Configuration **tab.
- Click **Edit...**
In the **Mark devices for passthrough** window, select the Cavium NITROX card.
[See image.](#image3)
- Select the Virtual Service Edge to which the Cavium NITROX card needs to be added. Ensure that the Virtual Service Edge is powered off. Then, click **Edit virtual machine settings**. In the **Virtual Machine Properties** window, click **Add...**
[See image.](#image4)
- Select **PCI Device**, then click **Next**.
[See image.](#image5)
- Select the Cavium NITROX card from the drop-down menu, then click **Next**.
[See image.](#image6)
- Click **Finish** to add the Cavium NITROX card.
[See image.](#image7)
- Click **OK** to finish the setup.
[See image.](#image8)
-
Run the following command to configure the card:
`sudo vzen install-nitrox`
- (Optional) if you want to use an SNMP management system to monitor the Virtual Service Edge, [enable SNMP for Virtual Service Edge](/zia/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
-
Run the following command:
`sudo vzen snmp-admin-configure`
- Enter a user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries from this user name only.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
-
Run the following command:
`sudo vzen snmp-trap-configure`
- When asked which traps you want to configure, enter v3 traps.
- Enter the IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- Enter a user name for the SNMP management system.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
-
Download the Virtual Service Edge build and start the Virtual Service Edge.
- On the vSphere client, click the **Console **tab or use SSH to connect to the management IP address.
- Run the following command to download the Virtual Service Edge build:
sudo vzen download-build
The initial build is around 1 GB, so it might take a while depending on your internet connection. The downloaded build is automatically installed. The Virtual Service Edge automatically starts after the installation is complete.
[]Start the VM. After the VM is started, create 4 virtual interfaces.
By default, your Virtual Service Edge has the following interfaces:
-
**em0**: Internet-facing Management interface. This management communication is used for downloading software updates, SSH, SNMP, NTP, etc. This is configured on the CLI using the following command:
`sudo vzen configure-network`
- **em1**: Internal-facing Proxy interface. The interface that receives user traffic from the internal side. This is configured in the ZIA Admin Portal.
In the dual arm configuration, you must configure two extra interfaces for each of your Virtual Service Edges:
- **em2**: Internet-facing Proxy interface. The interface that receives user traffic from the internet-facing side. This is configured in the `/sc/sme/conf/vzen_custom.conf` file.
-
**em3**: (Optional) Internal-facing Management interface.
em3 is not required if em0 is configured to connect to Zscaler cloud nodes (i.e., CA, CDSS, etc.).
[]![Screenshot of Mark devices for passthrough window on vSphere highlighting Cavium NITROX card](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/vsphere_cavium_nitrox_screenshot.png)
.
[]![Screenshot of vZEN Virtual Machine Properties window highlighting Add button ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/vzen_vm_properties_window.png)
[]![Screenshot of Add Hardware window highlighting PCI Device option](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/pci_device_vsphere_screenshot.png)
[]![Screenshot of Add Hardware window highlighting Cavium NITROX card connection option from drop-down menu](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/cavium_nitrox_connection_option_screenshot.png)
[]![Screenshot of Add Hardware window showing finalized Hardware type and PCI/PCIe Device](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/cavium_nitrox_hardware_screenshot.png)
[]![Screenshot of Virtual Machines Property window highlighting the new added hardware](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/vm_properties_cavium_screenshot.png)
[]
- Shut down your Virtual Service Edge and power off the virtual machine (VM).
- Using vSphere, add two additional interfaces and map them to the appropriate network or VLAN (em2 and em3).
- Add the em0 and em2 interfaces to the internet-facing network.
- Add the em1 and em3 interfaces to the internal-facing network.
- Restart the Virtual Service Edge.
Depending on your deployment type (explicit or transparent), you might need to set VMware-specific parameters such as Promiscuous Mode.
[]To configure the DNS server, management interface em0, and default route out:
-
Log in to the VM from the VMware ESXi portal.
Use zsroot as the username and password. Ensure to change the password after logging in.
-
Run the following command:
`sudo vzen configure-network`
You can now log in to the internet-facing Management IP address (i.e., em0) using SSH.
[]You need to configure an additional management interface, em3. If configured, this interface provides inbound access from the management interface to the Zscaler Central Authority (CA) to receive updates for your Virtual Service Edge.
If em0 is configured to get updates from CA and CDSS, em3 is optional.
To configure an additional management interface:
- Run ifconfig to ensure that the em3 interface is active.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em3.
-
Add the following line to the end of the file:
`ifconfig_em3="<IP Address>"`
Replace <IP Address> with the IP address in your subnet which is internal-facing (user network).
-
(Optional) The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN, add the following to the end of the file:
`static_routes="em3_internal"
route_em3_internal="-net <Destination Subnet> <Gateway IP Address>"`
Replace <Destination Subnet> with the IP subnet of the user network/internal network and replace <Gateway IP Address> with your desired gateway IP address (ideally the inside router).
For example, to add a static route to a different subnet or VLAN:
`static_routes="em3_internal"
route_em3_internal="-net 10.0.0.0/8 10.88.44.1"`
- Restart the VM.
- Verify the configuration:
- Ping the newly added subnet gateway.
-
Print the route information by entering the following command:
`sudo netstat -rn`
[]You need to configure an additional proxy interface, em2. The proxy interface processes user traffic from the switch/vswitch on the internet-facing side.
To configure an additional proxy interface:
- Log in to the VM.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em2.
-
Enter the following command:
`cd /sc/sme/conf`
- Create a new file called vzen_custom.conf.
-
Add the following lines:
`[SME]
smnet_dev=em2=zs1:<em2 Internet facing proxy IP/Mask>
smnet_route="<subnet/subnetmask/internal facing gateway>"
smnet_dflt_gw=<Default Gateway>
system_ip=<em2 Internet facing proxy IP>
[-end-of-SME-]`
Replace all text in red with the appropriate values.
For example, to add an additional proxy interface:
`[root@perf-vzen ]:-$cat /sc/sme/conf/vzen_custom.conf
[SME]
smnet_dev=em2=zs1:10.66.2.70/24
smnet_route="10.65.1.220/32/10.66.105.254,10.72.5.2/32/10.66.105.254"
smnet_dflt_gw=10.66.2.254
system_ip=10.66.2.70
[-end-of-SME-]`
If you want to route the traffic through internal-facing interfaces (e.g., to access internally hosted servers), use `smnet_route` for em1, or else remove it.
[]To restart the Virtual Service Edge:
- Log in to the VM.
-
Enter the following command:
`sudo vzen restart`
[]This deployment is used when you expect the following in a cluster mode:
- Internal user traffic to access internal or external servers.
- Remote user traffic from the cluster IP on the internal-facing side to access internal servers.
To learn more, see [About Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters) and [Configuring Virtual Service Edge Clusters](/zia/configuring-virtual-service-edge-clusters).
![ZIA Network diagram illustrating traffic flow of a Virtual Service Edge in dual arm mode.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/virtual-service-edge-configuration-guide-dual-arm-mode/ZIA-Virtual-Service-Edge-Dual-Arm-Cluster-Mode-With-User-Traffic-on-One-Arm.png?1688566277)
Each of your Virtual Service Edges need two additional IPs for this dual arm configuration. The cluster IP is the proxy gateway that users point to. It’s also the VIP for the Virtual Service Edges. To learn more, see [Locating the Virtual IP Addresses for ZIA Public Service Edges](/zia/locating-virtual-ip-addresses-your-zia-public-service-edges).
By default, your Virtual Service Edge has the following interfaces:
-
**em0**: Internet-facing Management interface. This management communication is used for downloading software updates, SSH, SNMP, NTP, etc. This is configured on the CLI using the following command:
`sudo vzen configure-network`
- **em1**: Internal-facing Proxy interface. The interface that receives internal user/remote user traffic from the internal side. This is configured in the ZIA Admin Portal.
- **em2**: Internal-facing The LB service interface. The interface in the user network that receives user traffic from the internal-facing cluster IP. This is configured in the ZIA Admin Portal.
In the dual arm configuration, you must configure two extra interfaces for each of your Virtual Service Edges:
- **em3**: Internet-facing Proxy interface. The interface that forwards user traffic to the internet. This is configured in the `/sc/sme/conf/vzen_custom.conf` file.
-
**em4**: (Optional) Internal-facing Management IP address.
em4 is not required if em0 is configured to connect to Zscaler cloud nodes (i.e., CA, CDSS, etc.).
To deploy the Virtual Service Edge using the dual arm configuration in cluster mode with user traffic on one arm:
Repeat these steps for all of your additional Virtual Service Edges.
- [1. Prepare the vSphere.](#step1-cluster-traffic-1side)
- [2. Configure an additional proxy interface.](#step3-cluster-traffic-1side)
- [3. (Optional) Configure an additional management interface.](#step2-cluster-traffic-1side)
- [4. Restart the Virtual Service Edge.](#step4-cluster-traffic-1side)
[]
- Shut down your Virtual Service Edge and power off the virtual machine (VM).
- Using vSphere, add two additional interfaces and map them to the appropriate network or VLAN (em3 and em4).
- Add the em0 and em3 interfaces to the internet-facing network.
- Add the em1, em2, and em4 interfaces to the internal-facing network.
- Restart the Virtual Service Edge.
[]You need to configure an additional management interface, em4. If configured, this interface provides inbound access from the management interface to the Zscaler Central Authority (CA) to receive updates for your Virtual Service Edge.
If em0 is configured to get updates from CA and CDSS, em4 is optional.
To configure an additional management interface:
- Run ifconfig to ensure that the em4 interface is active.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em4.
-
Add the following line to the end of the file:
`ifconfig_em4="<IP Address>"`
Replace <IP Address> with the IP address in your subnet which is internal-facing (user network).
- (Optional) The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN, add the following to the end of the file:
- static_routes="em4_internal"
route_em4_internal="-net <Destination Subnet> <Gateway IP Address>"
Replace <Destination Subnet> with the IP subnet of the user network/internal network and replace <Gateway IP Address> with your desired gateway IP address (ideally the inside router).
- Restart the VM.
- Verify the configuration:
- Ping the newly added subnet gateway.
-
Print the route information by entering the following command:
`sudo netstat -rn`
[]You need to configure the additional proxy interface, em3. The proxy interface processes internet traffic.
To configure an additional proxy interface:
- Log in to the VM.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em3.
-
Enter the following command:
`cd /sc/sme/conf`
- Create a new file called vzen_custom.conf.
-
Add the following lines:
`[SME]
smnet_dev=em3=zs1:<em3 Internet facing proxy IP/Mask>
smnet_route="<subnet/subnetmask/internal facing gateway>"
smnet_dflt_gw=<Default Gateway>
system_ip=<em3 Internet facing proxy IP>
[-end-of-SME-]`
For example, to add an additional proxy interface:
`[root@perf-vzen ]:-$cat /sc/sme/conf/vzen_custom.conf
[SME]
smnet_dev=em3=zs1:10.66.2.70/24
smnet_route="10.65.1.220/32/10.66.105.254,10.72.5.2/32/10.66.105.254"
smnet_dflt_gw=10.66.2.254
system_ip=10.66.2.70
[-end-of-SME-]`
If the internal users are not on the same VLAN as the Virtual Service Edge internal network, ensure to add reverse routes (i.e., `smnet_route="``<subnet/subnetmask/internal facing gateway>``"`) on the Virtual Service Edge for such internal networks.
Replace all text in red with the appropriate values.
[]After you have configured the additional interfaces, restart your Virtual Service Edge.
To restart the Virtual Service Edge:
- Log in to the VM.
-
Enter the following command:
`vzen restart`
Ensure that the autostart for Virtual Service Edge services is enabled.
[]This deployment is used when you expect the following in a cluster mode:
- Internal user traffic to access internal or external servers.
- Remote user traffic from the cluster IP on the internet-facing side to access internal or external servers.
To learn more, see [About Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters) and [Configuring Virtual Service Edge Clusters](/zia/configuring-virtual-service-edge-clusters).
![ZIA Network diagram illustrating traffic flow of a Virtual Service Edge in dual arm mode.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/virtual-service-edge-configuration-guide-dual-arm-mode/ZIA-Virtual-Service-Edge-Dual-Arm-Cluster-Mode-With-User-Traffic-on-Both-Arm.png?1688716293)
Each of your Virtual Service Edges need three additional IPs for a dual arm configuration. The cluster IP is the proxy gateway that users point to. It’s also the VIP for the Virtual Service Edges. To learn more, see [Locating the Virtual IP Addresses for ZIA Public Service Edges](/zia/locating-virtual-ip-addresses-your-zia-public-service-edges).
By default, your Virtual Service Edge has the following interfaces:
-
**em0**: Internet-facing Management interface. This management communication is used for downloading software updates, SSH, SNMP, NTP, etc. This is configured on the CLI using the following command:
`sudo vzen configure-network`
- **em1**: Internal-facing Proxy interface. The interface that receives user traffic from the internal side. This is configured in the ZIA Admin Portal.
- **em2**: Internal-facing LB service interface. The interface in the user network that receives user traffic from the internal-facing cluster IP. This is configured in the ZIA Admin Portal.
In the dual arm configuration, you must configure three extra interfaces for each of your Virtual Service Edges:
- **em3**: Internet-facing Proxy interface. The interface that receives/forwards user traffic from/to the internet. This is configured in the `/sc/sme/conf/vzen_custom.conf` file.
- **em4**: Internet-facing LB service interface. The interface in the internet-facing network that receives user traffic from the internet-facing cluster IP. This LB communication is used for downloading policies and uploading logs from the Zscaler Central Authority (CA).
-
**em5**: (Optional) Internal-facing Management interface.
em5 is not required if em0 is configured to connect to Zscaler cloud nodes (i.e., CA, CDSS, etc.).
To deploy the Virtual Service Edge using the dual arm configuration in cluster mode with user traffic on both arms:
Repeat these steps for all of your additional Virtual Service Edges.
- [1. Prepare the vSphere.](#step1-cluster-traffic-2side)
- [2. Configure an additional proxy Interface.](#step3-cluster-traffic-2side)
- [3. (Optional) Configure an additional management interface.](#step2-cluster-traffic-2side)
- [4. Configure an additional LB interface.](#step4-cluster-traffic-2side)
- [5. Restart the Virtual Service Edge.](#step6-cluster-traffic-2side)
[]
- Shut down your Virtual Service Edge and power off the VM.
- Using vSphere, add 3 additional interfaces and map them to the appropriate network or VLAN (em3, em4, and em5).
- Add the em0, em3, and em4 interfaces to the internet-facing network.
- Add the em1, em2, and em5 interfaces to the internal-facing network.
- Restart the Virtual Service Edge.
[]You need to configure an additional management interface, em5. If configured, this interface provides inbound access from the management interface to the CA to receive updates for your Virtual Service Edge.
If em0 is configured to get updates from CA and CDSS, em5 is optional.
To configure an additional management interface:
- Run ifconfig to ensure that the em5 interface is active.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em5.
-
Add the following line to the end of the file:
`ifconfig_em5="<IP Address>"`
Replace <IP Address> with the IP address in your subnet which is internal-facing (user network).
- (Optional) The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN, add the following to the end of the file:
- static_routes="em5_internal"
route_em5_internal="-net <Destination Subnet> <Gateway IP Address>"
Replace <Destination Subnet> with the IP subnet of the user network/internal network and replace <Gateway IP Address> with your desired gateway IP address (ideally the inside router).
- Restart the VM.
- Verify the configuration:
- Ping the newly added subnet gateway.
-
Print the route information by entering the following command:
`sudo netstat -rn`
[]You need to configure an additional proxy interface, em3. The proxy interface processes internet traffic from the cluster IP. The cluster IP is where your users push their traffic to.
To configure an additional proxy interface:
- Log in to the VM.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em3.
-
Enter the following command:
`cd /sc/sme/conf`
- Create a new file called vzen_custom.conf.
-
Add the following lines:
`[SME]
smnet_dev=em3=zs1:<em3 Internet facing proxy IP/Mask>
smnet_route="<subnet/subnetmask/internal facing gateway>"
smnet_dflt_gw=<Default Gateway>
system_ip=<em3 Internet facing proxy IP>
[-end-of-SME-]`
For example, to add an additional proxy interface:
`[root@perf-vzen ]:-$cat /sc/sme/conf/vzen_custom.conf
[SME]
smnet_dev=em3=zs1:10.66.2.70/24
smnet_route="10.65.1.220/32/10.66.105.254,10.72.5.2/32/10.66.105.254"
smnet_dflt_gw=10.66.2.254
system_ip=10.66.2.70
[-end-of-SME-]`
If the internal users are not on the same VLAN as the Virtual Service Edge internal network, ensure to add reverse routes (i.e., `smnet_route="``<subnet/subnetmask/internal facing gateway>``"`) on the Virtual Service Edge for such internal networks.
Replace all text in red with the appropriate values.
[]You need to configure an additional LB interface, em4. The load balancer process works in tandem with the proxy interface.
To add an additional LB interface:
- Log in to the VM.
- Update the /etc/rc.conf system configuration file. To do this:
-
Enter the following command:
`sudo vi /etc/rc.conf`
- Modify the "network_interfaces=" line to include em4.
-
Enter the following command:
`cd /sc/smlb/conf`
- Create a file called vzen_custom.conf.
-
Add the following lines:
`[SME]
smnet_dev=em4=zs1:<em4 Internet facing LB IP/Mask>
smnet_route="<subnet/subnetmask/internal facing gateway>"
smnet_dflt_gw=<Default Gateway>
system_ip=<em4 Internet facing LB IP>
[-end-of-SME-]`
Replace all text in red with the appropriate values.
For example, to add an additional LB interface:
`[root@perf-vzen ]:-$cat /sc/smlb/conf/vzen_custom.conf
[SME]
smnet_dev=em4=zs1:10.66.2.71/24
smnet_route="10.65.1.220/32/10.66.105.254,10.70.6.2/32/10.66.105.254"
smnet_dflt_gw=10.66.2.254
system_ip=10.66.2.71
[-end-of-SME-]`
[]To restart the Virtual Service Edge:
- Log in to the VM.
-
Enter the following command:
`vzen restart`
[]![Serial Console window](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/SSH-in-browser-password-reset-password.png)
[]![Serial Console window](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/SSH-CLI-Password-Complexity.png)