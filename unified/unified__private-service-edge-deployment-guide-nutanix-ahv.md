# Private Service Edge Deployment Guide for Nutanix AHV
Source: https://help.zscaler.com/unified/private-service-edge-deployment-guide-nutanix-ahv
PDF: https://help.zscaler.com/pdf/com/en/1530883.pdf

This deployment guide provides information on prerequisites, how to deploy a Private Service Edge on Nutanix AHV, and post-deployment verification checks. For general information regarding Private Service Edge deployment for Private Applications, see [About Deploying Private Service Edges for Private Applications](/unified/about-deploying-private-service-edges-private-applications).
- [Step 1: Make Sure You Have Met All Private Service Edge Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the Private Service Edge on Nutanix](#deploy)
- [Step 3: Configure the Networking for the Deployed Private Service Edge](#networking)
- Step 4: Verify that the deployed Private Service Edge is [running and healthy](/unified/managing-deployed-private-service-edges-private-applications#Status). Also, check that it [meets your sizing requirements](/unified/managing-deployed-private-service-edges-private-applications#VerifySizing).
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications).
[]
Before deploying a Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 Private Service Edges.
- [Private Service Edge Specifications and Sizing Requirements](#SpecsSizing)
- [Private Service Edge Platform Prerequisites](#PlatformPrereqs)
- [Private Service Edge Security Guidance and Firewall Requirements](#Firewall)
- [Private Service Edge Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each Private Service Edge.
- Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| Active Users | Memory | vCPU or CPU Cores |
| ------------ | ------ | ----------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 32 GB (34 GB with ZDX) | 16 vCPUs or 16 CPUs |
To learn more, see the [Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Service Edge must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable for both remote and office users, each Private Service Edge needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Service Edges are reachable over the internet for remote users in a disaster recovery scenario, or when the Private Service Edge is the closest Service Edge.
In the scenario where a Private Service Edge is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Service Edge's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Service Edge. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Service Edge. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a [publish IP](/unified/about-private-service-edges-private-applications) of the respective Private Service Edge. In the case of disaster recovery, you must add this IP address as the A record for that Private Service Edge.
Your firewalls must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors.
The following conditions apply to each Private Service Edge that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Service Edge is enrolled, an outbound TLS tunnel over TCP port 443 is established to the cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the Public Service Edge
- Policy configuration download
- Private Service Edge software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional Private Service Edges at any time, using the same provisioning key to add them to the existing Private Service Edge group, while ensuring network and internet connectivity. Private Service Edges are designed to scale elastically. You can deploy additional Private Service Edges in the same Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Service Edges in pairs (N+1), where N is the number of Private Service Edges as per the sizing requirements. To learn more, see [About Deploying Private Service Edges](/unified/about-deploying-private-service-edges-private-applications) and [Supported Platforms for Private Service Edges](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the Private Service Edge meets your sizing requirements. To learn more, see [Verify Private Service Edge Sizing Specifications](/unified/managing-deployed-private-service-edges-private-applications). If disk space fills up in the Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance#diskspace_archive).
Understanding Private Service Edge Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Service Edge supports up to 500 Mbps throughput. Private Service Edges communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
For example, if you have a 1 Gbps aggregate (i.e., total inbound and outbound) connection in your data center, you can use the 500 Mbps throughput guideline to make sure you have enough Private Service Edges to support the connection and have room for failover (N+1). In this case, you would need to deploy 2 to 3 Private Service Edges to support the 1 Gbps connection.
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, AppProtection, or ZDX enabled. Make sure that you have enough Private Service Edges to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Service Edges with lower specifications rather than fewer Private Service Edges with higher specifications. For example, if you have fewer Private Service Edges with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Service Edge that fails.
[]Before you begin any procedures within the [Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform, make sure that you have met all of the following prerequisites:
- Intel x86_64/AMD64 based architecture
- systemd
- Root or sudo access to the system in order to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Service Edge provisioning key](/unified/about-private-service-edge-provisioning-keys-private-applications)
- A static MAC address
[]Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the Private Service Edge and its VMs to ensure that memory growths do not have an impact on the Private Service Edge performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [Private Service Edge Deployment Guides](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on CentOS 7.x). You can patch these systems when necessary by using the standard yum OS update mechanism. To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting Private Service Edges using firewall policies. Additionally, if you've installed the Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Service Edge in such an environment as long as the Private Service Edge is able to reach all Zscaler data centers containing Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90 day notice for activating additional IP CIDR ranges, in order to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Service Edge will not function if the TLS certificates presented by the Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Service Edge. This is necessary for allowing the Private Service Edge to resolve and reach Public Service Edges. Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). It may be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Service Edges require that the [Zscaler Client Connector](/z-app) be at least on version 2.1.2.
[]This procedure describes how to deploy a virtual appliance on Nutanix AHV.
Before you deploy a virtual appliance on Nutanix AHV, you must obtain the latest Zscaler Private Service Edge OVA. Use the following link to download the latest VMware image from Zscaler: [https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova](https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova).
After you obtain the latest Zscaler Private Service Edge OVA, upload the OVA to one of the following platforms:
- Prism Central. To learn more, refer to the [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide-Prism-vpc_2022_1:mul-ova-manage-pc-c.html).
- Prism Element. To learn more, refer to the [Nutanix documentation](https://portal.nutanix.com/page/documents/kbs/details?targetId=kA03200000099TXCAY).
The procedures in this article cover the deployment of a virtual appliance on Nutanix AHV by uploading the OVA to Prism Element.
To deploy a virtual appliance on Nutanix AHV:
- []Extract the VMDK file from the OVA. Right-click the OVA file, and click **7-Zip **> **Extract files** to extract the files.
- []Select the destination of the files and click **OK**.
- Upload the VMDK file to Prism Element.
- Log in to Prism Element.
- Click the **Settings **icon** **and then click **Image Configuration**.
[See image.](#imageConfiguration)
- Click **Upload Image**. The **Create Image **window appears.
[See image.](#createImageWindow)
- In the **Create Image **window:
- **Name**: Enter the name of the VM.
- **Image Type**: Select **DISK **from the drop-down menu.
- For **Image Source**, select **Upload a file**.
- Click **Choose File** and select the VMDK file [previously extracted](#extract-vmdk).
- Click **Open**.
[See image.](#imageType)
- Click **Save**.
- Return to the **Image Configuration** page (**Settings** > **Image Configuration**) and verify that the image is listed as **ACTIVE** in the table.
[See image.](#activeImage)
- Create the VM.
- Go to **VM **from the main menu.
- On the **Table **tab, click **Create VM**.
[See image.](#createVM)
The **Create VM window** appears.
- Under **General Information**:
- **Name**: Enter the name of the VM.
- **Timezone**: Select the timezone of the VM.
[See image.](#createVMGeneralInformation)
- Under **Compute Details**:
- **vCPU(s)**: Enter the CPU of the VM (e.g., 1 core of 2 cores).
- **Number Of Cores Per vCPU**: Enter the number of cores for the virtual CPU. The minimum required value is 4.
- **Memory**: Enter the memory of the VM (e.g., 8 GB or 4 GB).
[See image.](#createVMComputeDetails)
- Under **Disks**, click the **Delete **icon to remove the CD-ROM disk type.
[See image.](#createVMdeleteCDROM)
- Click **Yes** when prompted to delete the disk.
- Click **Add New Disk**.
[See image.](#createVMaddNewDisk)
- In the **Add Disk** window:
- **Type**: Select **Disk**.
- **Operation**: Select **Clone from Image Service**.
- **Bus Type**: Select **IDE**.
- **Image**: Select the image [previously uploaded](#select-nutanix-image).
The **Size** field is auto-populated based on the selected image.
[See image.](#CreateVMaddDiskWindow)
-
Click **Add**.
After adding the disk, you can click the** Edit **icon to edit the disk.
- Under **Network Adapters (NIC)**, click **Add New NIC**.
[See image.](#addNewNIC)
- In the **Create NIC **window, select **NR_PRT_DHCP** from the **Subnet Name** drop-down menu, then click **Add**.
[See image.](#createNICwindow)
- Click **Save**.
- On the **Table** tab (**VM **from the main menu), search for the VM by name.
[See image.](#searchForVM)
- Select the VM to view its details.
- Click **Power on**.
[See image.](#powerOnVm)
- Click **Launch Console **to configure the provisioning key.
[See image.](#launchConsole)
- Apply the Private Service Edge provisioning key.
- [See instructions.](#pkey)
[]![Selecting Settings in the Nutanix Portal.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-img-configuration.png)
[]![age window in the Nutanix Portal after clicking Upload Image.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm.png)
[]![Selecting DISK in the Image Type drop-down menu.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-disk.png)
![Verifying the image is active in the Nutanix portal.](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-nutanix-ahv/zpa-connector-nutanix-deployment-image-active2.png)
[]
![Clicking Create VM in the Table tab of the Nutanix portal.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm-window.png)
[]
[]![Entering General Configuration in the Create VM window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm-window-general2.png)
[]![Entering Computer Details in the Create VM window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm-window-compute.png)
[]![Deleting the CD ROM Disk Type in the Create VM window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm-window-disks.png)
[]![Adding a new disk in the Create VM window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-vm-window-add-new-disk.png)
[]![Entering parameters in the Add Disk window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-deployment-add-disk-window2.png)
[]![Adding a new NIC.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-add-new-nic2.png)
[]![Adding a new NIC in the Create NIC window.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-create-nic-window2.png)
![Searching for the VM in the Nutanix portal.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-search.png)
[]
[]![Powering on the VM in the Nutanix portal.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-vm-power-on.png)
[]![Launching the Private Service Edge console in the Nutanix portal.](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-nutanix-ahv/zpa-pse-nutanix-deployment-launch-console.png)
- []On Zscaler-provided virtual appliances, SSH is not enabled by default. It is required for a short time to configure the provisioning key for the Private Service Edge. Complete the following steps to temporarily enable SSH:
- Log in to the Private Service Edge console using your [admin credentials](/unified/managing-deployed-private-service-edges-private-applications#Default).
After the initial boot of an Private Service Edge instance, it might take up to 15 minutes for the admin credentials to apply. So, if you receive an invalid credentials error after the initial boot, wait a few minutes and try again.
- Start the SSH daemon using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl start sshd
This command temporarily enables SSH, but it does not persist if a reboot occurs. If you need SSH to remain enabled after a reboot, use the `sudo systemctl enable sshd` command.
- Verify the Private Service Edge's IP address using the following command:
[admin@zpa-service-edge ~]$ ifconfig
The configuration output should look similar to the following:
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500
inet 192.0.2.1 netmask 255.255.255.128 broadcast 192.168.144.127
inet6 fe80::20c:29ff:fef5:5d43 prefixlen 64 scopeid 0x20<link>
ether 00:0c:29:f5:5d:43 txqueuelen 1000 (Ethernet)
RX packets 8504 bytes 8732964 (8.3 MiB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 4900 bytes 427768 (417.7 KiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
- SSH into the virtual machine (VM) using a standard SSH client. Using the previous example, the Private Service Edge IP address is 192.0.2.1:
[admin@zpa-service-edge ~]$ ssh admin@192.0.2.1
- Populate the provisioning key file.
- Stop running the zpa-service-edge service. If the provisioning key was not detected when the Private Service Edge was first started, the Private Service Edge is in a sleep cycle and will look for the key again every 24 hours.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions at `/opt/zscaler/var/service-edge/provision_key`. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Private Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-service-edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
- []After the Private Service Edge is enrolled, disable SSH using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl stop sshd
However, if you used the `sudo systemctl enable sshd` command for the [previous step](#disable-ssh), then enter the `sudo systemctl disable sshd` command.
- Run the following commands:
[admin@zpa-service-edge ~]$ systemctl daemon-reload
[admin@zpa-service-edge ~]$ systemctl start zpa-service-edge
- Zscaler highly recommends [updating the Private Service Edge system software](/unified/understanding-private-service-edge-software-upgrades-private-applications) before proceeding.
[]
Before you deploy the Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a Private Service Edge](#Interfaces)
- [Configure Static Routing for a Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](#NTP)
- [Configure a Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/ifcfg-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
In the following example, the edited file is using a Private Service Edge IP address of 192.168.2.100, highlighted in green:
DEVICE="eth0"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- Edit the /etc/sysconfig/network file and configure the default gateway. For example:
NETWORKING=yes
GATEWAY=192.168.2.254
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]If necessary, additional interfaces can be configured by creating additional files in /etc/sysconfig/network-scripts.
- Log in to the Private Service Edge console using your admin credentials.
- Copy the /etc/sysconfig/network-scripts/ifcfg-eth0 file to /etc/sysconfig/network-scripts/ifcfg-eth1. For example:
[admin@zpa-service-edge ~]$ sudo cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth1
- Edit the new /etc/sysconfig/network-scripts/ifcfg-eth1 file with the network configuration information required for the interface. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth1
The content within the new file should be similar to the following:
DEVICE="eth1"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To add static routes to the interface control files for a Private Service Edge:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/route-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/sysconfig/network-scripts/route-eth0
Add additional static routes using the following format: <CIDR> via <GATEWAY> dev <INTERFACE>. For example:
192.168.0.0/16 via 192.0.2.1 dev eth0
172.16.0.0/12 via 192.0.2.1 dev eth0
10.0.0.0/8 via 192.0.2.2 dev eth0
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]DNS resolution is critical for the successful operation of the Private Service Edge. Private Service Edges must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/resolv.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/resolv.conf
Replace the example nameserver IP addresses and search domains with your company-specific configuration. For example:
nameserver 8.34.34.34
nameserver 8.35.35.35
search myexampledomain.com
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To configure Private Service Edges to use internal NTP servers:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the Private Service Edge to work through that proxy. The following procedure allows the Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the Private Service Edge to work through an explicit proxy:
- Log in to the Private Service Edge console using your admin credentials.
- Create a file named, /opt/zscaler/var/service-edge/proxy. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: <Proxy Hostname or IP Address>:<Proxy Port> (e.g., 192.0.2.0:0).
- To apply the changes, restart the Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The Private Service Edge will attempt to create a TLS session through the proxy specified in step 2.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.