# Configuring Internet & SaaS Virtual Service Edge for Microsoft Hyper-V
Source: https://help.zscaler.com/unified/configuring-internet-saas-virtual-service-edge-microsoft-hyper-v
PDF: https://help.zscaler.com/pdf/com/en/1495671.pdf

Zscaler supports standalone Virtual Service Edge for production deployments on Microsoft Hyper-V.
Requirements
Ensure that you meet all of the following requirements:
- A Virtual Service Edge cluster must contain at least two Virtual Service Edge instances in order to provide n+1 redundancy for production. It can contain a maximum of 16 Virtual Service Edge instances. You need a subscription license count for each Virtual Service Edge in a cluster.
- Virtual Service Edges only require outbound connections to the Zscaler cloud. Configure your firewall to allow the necessary outbound connections. To view the firewall requirements, log in to the Admin Portal, go to the Help menu, and select Cloud Configuration Requirements.
- Verify that your license is appropriate to your needs. In the Admin Portal, go to the Subscriptions page and look for the Virtual Service Edges, noting the server count.
- Virtual Machine specs for a Virtual Service Edge cluster:
- **Hypervisor**: Windows Server 2019 with Hyper-V feature enabled
- The Promiscuous Mode option must be enabled using the Microsoft NDIS capture on the Virtual Switch. Zscaler load balancers and Virtual Service Edges use the Common Address Redundancy Protocol (CARP) to process traffic across multiple Virtual Service Edge instances. In order to support this, enabling promiscuous mode on your Windows Server is required.
Run the following PowerShell commands to enable the Promiscuous Mode:
PS C:\Users\Administrator> $extention=VMSystemswitchextensionportfeature -FeatureID 776e0ba7-94a1-41c8-8f28-951f524251b5
PS C:\Users\Administrator> $extension.SettingData.MonitorMode=2
PS C:\Users\Administrator> Add-VMSwitchExtensionPortFeature -ExternalPort -SwitchName <vSwitch-name> -VMSwitchExtensionFeature $extension
You must run these commands as an administrator.
- Verify that the Microsoft NDIS Capture has been enabled for the Virtual Switch on the Virtual Switch Manager of the Hyper-V Windows Manager.
[See image.](#extension-virtual-switch)
- **CPUs**: 4 CPU cores
- **Minimum Required RAM**: 32 GB
- **Recommended RAM**: 48 GB for production
- **Disk**: 500 GB (thin provisioned). Zscaler recommends using SSDs.
- **Network Interfaces**: 3 interfaces (1 for Management, 1 for the Virtual Service Edge, and 1 for the Load Balancer). These interfaces should be on the same VLAN. This VLAN should be accessible by user traffic and have outbound access to the internet.
- []The required IP addresses are listed in [the following table.](#table)
Configuring a Virtual Service Edge Cluster
If you are configuring a Virtual Service Edge cluster, you must create at least two Virtual Service Edge instances and download their respective SSL certificates. Each Virtual Service Edge VM requires a unique SSL certificate, which can be downloaded from the Admin Portal.
To configure a Virtual Service Edge cluster:
- [1. Add the Virtual Service Edge Instances](/unified/adding-virtual-service-edge-instances)
- [2. Download the Hyper-V VM File](#download-hyper-v)
- [3. Download the Virtual Service Edge Certificates](/unified/downloading-virtual-service-edge-certificates)
- [4. Add the Virtual Service Edge Cluster](/unified/adding-virtual-service-edge-clusters)
- [5. Bind the Virtual Service Edge Cluster to a Location](#Bind)
- [6. Create a Firewall Filtering Rule to Bypass Virtual Service Edge IP Addresses](#Firewall)
- [7. Configure the Virtual Service Edge VM](#Sphere)
Testing the Configuration
To test the configuration:
- On the Hyper-V client, click the **Console **tab or use SSH to connect to the management IP address.
- Run the following command:
sudo vzen status
The output should show that the Virtual Service Edge service and load balancer are running.
[See image.](#output-sudo-vzen-status)
- Run the following command:
sudo vzen troubleshoot connection | grep 9422
The output should show an established connection.
After you configure a Virtual Service Edge cluster, you can then forward your internet traffic to it using one of the mechanisms described in [Forwarding Traffic to Internet & SaaS Virtual Service Edges](/unified/forwarding-traffic-virtual-service-edges). To learn more about monitoring the Virtual Service Edge cluster, including how to monitor Virtual Service Edge health, see [Monitoring Internet & SaaS Virtual Service Edge Clusters](/unified/monitoring-virtual-service-edge-clusters).
[]
-
-
-
-
| IP Address | Purpose | Requirements |
| ---------- | ------- | ------------ |
| Management IP Address | This is used to make an SSH connection to the Virtual Service Edge VM for management. It is also used to download Virtual Service Edge builds from the Zscaler cloud. | Accessible via SSH by the Virtual Service Edge administrator during install, and requires outbound access to the internet. This is configured in the Virtual Service Edge CLI. |
| Proxy IP Address | This is used for the following:Outbound data connection (proxied traffic)Outbound control connection to the Zscaler cloudHealth monitoring by the load balancerIn a Virtual Service Edge standalone, it is used to listen for user traffic | It must be in the same subnet as the load balancer and cluster IP addresses. This is used when creating a Virtual Service Edge instance in the Admin Portal. |
| Load Balancer IP Address | This is used to make an outbound control connection to the Zscaler cloud, as well as receiving initial requests from users. | It must be in the same subnet as the proxy and cluster IP addresses. It is not required for a Virtual Servide Edge standalone. |
| Cluster IP Address | In a Virtual Service Edge cluster, it provides fault tolerance and is used to listen for user traffic. This interface does not explicitly get an IP address | It must be in the same VLAN as the proxy and load balancer IP addresses. It is not required for a Virtual Service Edge standalone. |
[]To download the Hyper-V VM file for each Virtual Service Edge in a cluster:
- Go to **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Virtual Service Edges**.
- Click **Download Hyper-V VM File**.
If the Hyper-V VM file fails to download, contact Zscaler Support for the image.
[See image.](#image-hyper-v)
[]![Screenshot of Virtual Service Edges Page with Hyper-V VM download file](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-microsoft-hyper-v/ZIA-Virtual-Service-Edges-Page-with-Hyper-V.png)
[]Add a location and bind the Virtual Service Edge cluster (or standalone Virtual Service Edge) to it so your organization can enable features such as authentication, firewall, SSL inspection, and location-level policies. The service associates the traffic that it receives on the Virtual Service Edge with its location and applies the features and policies configured for the location.
To bind a Virtual Service Edge or a Virtual Service Edge cluster to a location:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
-
On the **Locations** page, click **Add Location** or click the **Edit** icon for an existing location.
The **Add Location** or **Edit Location** window appears.
-
In the **Add Location** or **Edit Location** window, do one of the following:
- **Virtual Service Edges**: Select the standalone Virtual Service Edge you want to bind to the location.
-
**Virtual Service Edge Clusters**: Select the Virtual Service Edge cluster you want to bind to the location.
[See image.](#bind-vzen-cluster-location)
To learn more about the other fields, see [Configuring Locations](/unified/configuring-locations).
- Click **Save**.
[]****![Screenshot of Add Location window highlighting the Virtual Service Edges and Virtual Service Edge Clusters options.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-clusters/ZIA-add-location-virtual-service-edges-clusters.png)
****
[]Zscaler performs ICMP and HTTP monitoring from the Load Balancer (LB) to the Virtual Service Edge in order to monitor the health of the Virtual Service Edge and ensure that traffic is distributed appropriately. For health probes to work, you must create a Firewall Filtering rule to allow all Virtual Service Edge proxy, load balancer, and cluster IP addresses.
To create a Firewall Filtering rule:
- Go to **Policies **>** Access Control **>** Firewall **>** Firewall Filtering Policy**.
-
Click **Add Firewall Filtering Rule**.
The **Add Firewall Filtering Rule **window appears.
- In **Add Firewall Filtering Rule **window, click the **Source IP** tab.
- In **IP Addresses**, add the following IP addresses for your Virtual Service Edges:
- Proxy IP address
- Load balancer IP address
-
Cluster IP address
These are the IP addresses you created in [Step 4](/unified/adding-virtual-service-edge-clusters). To learn more about the other fields, see [Configuring Firewall Filtering Policy](/unified/configuring-firewall-filtering-policy).
- Under **Network Traffic**, select **Allow**.
- Click **Save** and activate the change.
[]If you are deploying a Virtual Service Edge cluster, you must configure each Virtual Service Edge instance as a VM on the Hyper-V manager.
Zscaler recommends using different servers for each instance to achieve fault tolerance.
To configure the Virtual Service Edge on the Hyper-V manager:
- Launch the Hyper-V Manager Windows application.
-
On the **Action** menu or pane, click **New **and select** Virtual Machine**.
The **New Virtual Machine Wizard** appears.
- On the **Before You Begin **screen, review the content and click **Next**.
- On the **Specify Name and Location **screen:
- In the **Name **field, enter a name for the VM.
-
(Optional) Select **Store the virtual machine in a different location** and, in the **Location** field, specify the path to a location where you want to store the VM.
By default, the location for the VM is set to **C:\ProgramData\Microsoft\Windows\Hyper-V\ **and this field is grayed out.
- Click **Next**.
- On the **Specify Generation **screen, select **Generation 1 **and click **Next**.
- On the **Assign Memory **screen, set the **Startup memory** to 32768 MB and click **Next**.
- On the **Configure Networking **screen, select the Virtual Switch that you want to connect to the physical NIC and click **Next**.
- On the **Connect Virtual Hard Disk **screen:
- Select **Use an existing virtual hard disk**.
- In the **Location **field, specify the path to the location where the downloaded Hyper-V VM file is placed on the disk.
- Click **Finish**.
- Click **Settings** of the newly created VM.
- Add two more NICs and select the virtual switch that they must connect to.
-
On the third NIC, in the **Advanced Features**, select **Enable MAC address spoofing**.
The third NIC in the Virtual Service Edge has CARP enabled by the Load Balancer. So, enabling the MAC address spoofing facilitates sending of frames by the Virtual/Cluster IP.
[See image.](#hyper-v-vm-settings)
- Click **OK**.
- Select the Virtual Service Edge VM and click either the **Power On** button or **Power On the virtual machine**.
-
On the **Console** tab, log in to the FreeBSD command prompt with the following credentials:
- Username: zsroot
- Password: zsroot
The following guidelines apply:
- Zscaler strongly recommends that you change this default password by running the passwd command.
- Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
- Run the following command to configure the network:
sudo vzen configure-network
- Specify the following information:
- Address of the DNS server that is used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic (e.g., 10.84.0.100).
- Management interface IP with CIDR netmask. You use the management IP address for SSH or FTP (e.g., 10.84.0.110/24).
- Default gateway IP address (e.g., 10.84.0.200).
- Hostname of the Virtual Service Edge
- Install the SSL certificates of the Virtual Service Edge instances in the cluster. These are the certificates that you downloaded from the Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service. When you configure a Virtual Service Edge cluster, ensure that you upload the correct certificate for each Virtual Service Edge instance.
- Navigate to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- On the Hyper-V client, click the **Console **tab, and log in with the following credentials:
Username: zsroot
Password: zsroot
- Go to the **Console **tab or use SSH to connect to the management IP address.
- Run the following command:
sudo vzen install-cert <cert-bundle.zip>
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
- (Optional) if you want to use an SNMP management system to monitor the Virtual Service Edge cluster, [enable SNMP for Virtual Service Edge](/unified/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
- Run the following command:
sudo vzen snmp-admin-configure
- Enter a user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries from this user name only.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
- Run the following command:
sudo vzen snmp-trap-configure
- When asked which traps you want to configure, enter v3 traps.
- Enter the IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- Enter a user name for the SNMP management system.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
-
Download the Virtual Service Edge build and start the Virtual Service Edge:
- On the Hyper-V client, click the **Console **tab or use SSH to connect to the management IP address.
- Run the following command to download the Virtual Service Edge build:
sudo vzen download-build
The initial build is around 1 GB, so depending on your internet connection, it may take a while. The system automatically installs the downloaded build. After the installation is complete, the Virtual Service Edge starts automatically.
[][![Screenshot of SSH port showing that the VZEN service and load balancer are running](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/ssh_and_vzen_status_screenshot.png)
]
[]![Screenshot of Hyper-V Windows Manager with Microsoft NDIS Capture enabled for the Virtual Switch](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-virtual-service-edge-hyper-v/Virtual-Switch-Manager-HyperV.png)
[]![Screenshot of Hyper-V VM settings with Enable MAC address spoofing selected](/downloads/zscaler-tech-pubs-style-guide/draft-articles/configuring-virtual-service-edge-hyper-v/Hyper-V-Manager-VM-Settings.png)