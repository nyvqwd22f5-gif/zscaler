# Private Cloud Controller Deployment Guide for VMware Platforms
Source: https://help.zscaler.com/zpa/private-cloud-controller-deployment-guide-vmware-platforms
PDF: https://help.zscaler.com/pdf/com/en/1529183.pdf

This deployment guide provides information on prerequisites and how to deploy a [Private Cloud Controller](/zpa/deploying-private-cloud-controllers) on a VMware platform. For general information regarding Private Cloud Controller deployment, see [Deploying Private Cloud Controllers](/zpa/deploying-private-cloud-controllers).
- [Step 1: Make Sure You Have Met All Private Cloud Controller Deployment Prerequisites](#step1Prereqs)
- [Step 2: Deploy the Private Cloud Controller on a VMware Platform](#step2Deploy)
- [Step 3: Configure the Networking for the Deployed Private Cloud Controller](#network)
- Step 4: Verify that the deployed [Private Cloud Controller](/zpa/deploying-private-cloud-controllers) is [running and healthy](/zpa/managing-deployed-private-cloud-controllers#status). Also, check that it meets your sizing requirements.
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your [Private Cloud Controller](/zpa/deploying-private-cloud-controllers) console admin credentials or performing system software updates).
[]
- [Deploying on VMware vCenter](#vcenter)
- [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere)
[]
Before deploying a Private Cloud Controller on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Cloud Controller supports between 100 to 250 Mbps of SIEM throughput. Use the information on this page to determine the Private Cloud Controller sizing requirements for your deployment. Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput.
- [ZPA Private Cloud Controller Specifications and Sizing Requirements](#SpecsSizing)
- [ZPA Private Cloud Controller Platform Prerequisites](#PlatformPrereqs)
- [ZPA Private Cloud Controller Security Guidance and Firewall Requirements](#Firewall)
- [ZPA Private Cloud Controller Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the Private Cloud Controller on a supported platform.
[]The following specifications are recommended by Zscaler for up to 250 Mbps SIEM throughput based on the sizing. Refer to the following table for the sizing and relevant SIEM data throughput.
- Memory (RAM), vCPU (for virtual machines), SIEM throughput, or CPU (for physical machines) cores:
| Active Users | Memory | SIEM Throughput | vCPU or CPU Cores |
| ------------ | ------ | --------------- | ----------------- |
| Up to 2,000 | 16 GB | 100 Mbps | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 32 GB | 150 Mbps | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 64 GB | 250 Mbps | 16 vCPUs or 16 CPUs |
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Cloud Controller must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable ZPA for both remote and office users, each Private Cloud Controller needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Cloud Controllers are reachable over the internet for remote users in Business Continuity.
In the scenario where a Private Cloud Controller is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Cloud Controller's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Cloud Controller. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Cloud Controller. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a publish IP of the respective Private Cloud Controller. In the case of disaster recovery, you must add this IP address as the A record for that Private Cloud Controller.
Your firewalls must be configured to let the Private Cloud Controller establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors, ZPA Private Service Edges, and Zscaler Client Connectors.
The following conditions apply to each Private Cloud Controller that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Cloud Controller is enrolled, an outbound TLS tunnel over TCP port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the ZPA Public Service Edge
- Tenant-specific configuration and policy download
- ZPA Private Cloud Controller software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional ZPA Private Cloud Controllers at any time, using the same provisioning key to add them to the existing Private Cloud Controller group, while ensuring network and internet connectivity. Private Cloud Controllers are designed to scale elastically. You can deploy additional Private Cloud Controllers in the same Private Cloud Controller group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Cloud Controllers in pairs (N+1), where N is the number of Private Cloud Controllers as per the sizing requirements. To learn more, see [About Deploying Private Cloud Controllers](/zpa/about-deploying-private-cloud-controllers) and [Private Cloud Controller Deployment Guides for Supported Platforms](/zpa/business-continuity-management/private-cloud-controller-deployment-guides-supported-platforms).
After deployment, ensure that the Private Cloud Controller meets your sizing requirements. If disk space fills up in the Private Cloud Controller, Zscaler recommends archiving files and creating more log space.
Understanding Private Cloud Controller Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Cloud Controller supports up to 250 Mbps SIEM throughput. Private Cloud Controllers communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput and the number of users when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput. The exact throughput can vary and depends on other network factors such as your internal network setup and latency. Make sure that you have enough Private Cloud Controllers to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Cloud Controllers with lower specifications rather than fewer Private Cloud Controllers with higher specifications. For example, if you have fewer Private Cloud Controllers with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Cloud Controller that fails.
[]Before you begin any procedures within the [Private Cloud Controller Deployment Guide for Linux](/zpa/private-cloud-controller-deployment-guide-linux), make sure that you have all of the following prerequisites:
- Intel x86_64/AMD 64-based architecture
- systemd
- Root or sudo access to the system to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Cloud Controller provisioning key](/zpa/about-private-cloud-controller-provisioning-keys) obtained from the ZPA Admin Portal
- A static MAC address
[]Private Cloud Controllers can be deployed in different ways, so the security features for each deployment type are slightly different.
Operating System Security
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Cloud Controller in such an environment as long as the Private Cloud Controller can reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Cloud Controllers do not function if the TLS certificates presented by the ZPA Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Cloud Controller. This is necessary to allow the Private Cloud Controller to resolve and reach ZPA Public Service Edges. Private Cloud Controller requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa) It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Cloud Controllers require that the [Zscaler Client Connector](/z-app) is at least on version 4.6 or later for Windows.
[]
Before you deploy the Private Cloud Controller on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Cloud Controller](#DHCP_IP)
- [Configure Static IP Addressing for a Private Cloud Controller](#Static_IP)
- [Configure the Domain Name System (DNS) Resolver for a Private Cloud Controller](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a ZPA Private Cloud Controller](#NTP)
[]By default, virtual machine-based Private Cloud Controllers are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Cloud Controller.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Cloud Controller.
- Log in to the Private Cloud Controller console using your admin credentials.
- View the IP address.
` [admin@pcc ~]$ ip addr show`
- View the current connection profiles.
` [admin@pcc ~]$ nmcli connection show`
- Modify the connection profile to configure the interface's IP network for a dynamic Ethernet connection by using the following format: sudo nmcli connection modify <profile name> ipv4.method auto. For example:
` [admin@pcc ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For a static Ethernet connection, modify the connection profile to identify the IP addresses and gateway using the following format: sudo nmcli connection modify <profile name> ipv4.method manual ipv4.<IPv4 address> ipv4.gateway<IPv4 gateway>.
` [admin@pcc ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254`
- Apply the changes to bring the connection profile back up using the following format: sudo nmcli connection up <profile name>.
` [admin@pcc ~]$ sudo nmcli connection up "Profile 1"`
- Verify the IP address.
` [admin@pcc ~]$ ip addr show`
- Review the new connection profile.
`[admin@pcc ~]$ nmcli connection show`
[]DNS resolution is critical for the successful operation of the Private Cloud Controller. Private Cloud Controllers must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the ZPA Private Cloud Controller console using your admin credentials.
- View the current connection profile.
[admin@pcc ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@pcc ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@pcc ~]$ sudo nmcli connection down "Profile 1"[admin@pcc ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@pcc ~]$ sudo cat /etc/resolv.conf
[]To configure Private Cloud Controllers to use internal NTP servers:
- Log in to the ZPA Private Cloud Controller console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@pcc ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@pcc ~]$ systemctl restart chronyd
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a Private Cloud Controller on a VMware platform with vCenter.
The following additional prerequisites apply to VMware vCenter only:
- VMware vCenter version ESXi 7.0 Update 2 or later.
- Access to vCenter to deploy an OVA file as a virtual machine (VM).
- Access to vCenter to configure the virtual NIC of the VM onto the appropriate Virtual Network or VLAN.
- Access to vCenter to modify the vApp attributes of the VM.
- VMware vSphere Client Integration Plugin installed (which enables the functionality needed to upload new OVA/OVF images into vSphere).
To deploy a Private Cloud Controller on VMware vCenter:
- Obtain the latest VMware image from Zscaler. You can also use the following link to download the file for the vSphere Web Client:
[https://dist.private.zscaler.com/vms/VMware/2025.04/zpa-pcc-el9-2025.04.ova](https://dist.private.zscaler.com/vms/VMware/2025.04/zpa-pcc-el9-2025.04.ova).
- Connect to a vCenter Server with the vSphere Web Client and log in.
[See image.](#vcenter_login)
- Click **Home**, then click **VMs and Templates**.
[See image.](#vcenter_vmstemplates)
- From the **Actions** menu, select **Deploy OVF Template**.
[See image.](#vcenter_deployovf)
The **Deploy OVF Template** window appears.
- For **1 Source > 1a Select source**, complete one of the following procedures:
- Select **URL**, enter the following URL for the Private Cloud Controller image into the provided field, then click **Next**:
https://dist.private.zscaler.com/vms/VMware/2025.04/zpa-pcc-el9-2025.04.ova
The image is downloaded and then uploads to vCenter.
- If you’ve already downloaded the VMware image to your local system, select **Local file**, click **Browse** to locate the image file, and then click **Next**.
[See image.](#vcenter_selectsource)
- For **1 Source > 1b Review** **details**, verify that the OVF template details are correct, then click **Next**.
[See image.](#vcenter_reviewovf)
- For **2 Destination > 2a Select name and folder**, the name and folder specified in vCenter has no impact on the ZPA service. Select a name and folder that is suitable for your organization, then click **Next**.
[See image.](#vcenter_destinationfolder)
- For **2 Destination > 2b Select a resource**, select the destination resource (i.e., cluster, host, vApp, or resource pool), then click **Next**.
[See image.](#vcenter_destinationresource)
- For **2 Destination > 2c Select storage**, choose **Thin Provision** for the virtual disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#vcenter_destinationstorage)
- For **2 Destination > 2d Setup networks**, configure the **IP allocation** network settings as necessary.
The Private Cloud Controller is preconfigured to obtain an IP address on its primary interface via DHCP.
- If the DHCP service is available in your environment, select **DHCP**.
- If the DHCP service is not available in your environment, you must complete the following networking tasks:
- [Configure Static IP Addressing](/zpa/networking-deployed-private-cloud-controllers#Static_IP)
- [Configure the Domain Name System (DNS) Resolver](/zpa/networking-deployed-private-cloud-controllers#DNS)
[See image.](#vcenter_networksettings)
- For **3 Ready to complete**, ensure that the **Power on after deployment** checkbox is not selected, then click **Finish**.
[See image.](#vcenter_readytocomplete)
Within the **Recent Tasks** panel, you can monitor the deployment progress.
[See image.](#vcenter_recenttasks)
After the deployment has successfully completed, ensure that the VM has not been powered on before proceeding to the next step.
- Within the **Navigator** panel, select the deployed VM, and select **Edit Settings **from the **Actions** menu.
[See image.](#vcenter_navigator)
The **Edit Settings** window appears.
-
In the **Edit Settings** window, select the **vApp Options** tab.
[See image.](#vcenter_vappoptions)
-
Under **Authoring > OVF** settings:
- For **OVF environment transport**, select the **VMware Tools** checkbox.
- For **Installation boot**, select the **Enable **checkbox.
- Click **OK**.
[See image.](#vcenter_ovfsettings)
-
From the **Actions** menu, select **Power > Power On**.
[See image.](#vcenter_poweron)
- Verify the local time on the VMware machine is correct. If not, update the time using [Network Time Protocol](/zpa/networking-deployed-private-cloud-controllers#NTP).
- Make any necessary network configuration changes before applying the provisioning key.
- Apply the Private Cloud Controller provisioning key.
- [See instructions.](#prvskey1)
- Zscaler highly recommends [updating the Private Cloud Controller system software](https://zpa/understanding-private-cloud-controller-software-upgrades) before proceeding.
[]![Logging into the VMware Server using the vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-webclientlogin.png)
[]![Accessing VMs and Templates within the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vmsandtemplates.png)
[]![Accessing the Deploy OVF Template within the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-deployovftemplate.png)
[]![Select the source location of the VMware image file](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectsource.png)
[]![Review and verify the OVF template details](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-reviewdetails.png)
[]![Select the name and folder for the destination](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectnameandfolder.png)
[]![Select a resource for the destination ](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectaresouce.png)
[]![Select Thin Provision for the destination storage](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectstorage.png)
[]![Configure the network settings for the destination ](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-setupnetworks.png)
[]![Review the setting selections before completing](/downloads/zpa/business-continuity-management/private-cloud-controller-deployment-guides-supported-platforms/private-cloud-controller-deployment-guide-vmware-platforms/zpa-vmwarevcenter-readytocomplete.png)
[]![Monitor the deployment in Recent Tasks](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-recenttaskspanel.png)
[]![VMware vSphere Web Client with Actions menu](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-actionsmenueditsettings.png)
[]![VMware vSphere Web Client with Edit Settings window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vappoptionstab.png)
[]![VMware vSphere Web Client with Edit Settings window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vappoptions-ovfsettings.png)
![Select Power On in the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-actionsmenupoweron.png)
[]
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a ZPA Private Cloud Controller on a VMware platform with vSphere Hypervisor.
The following additional prerequisites apply to VMware vSphere Hypervisor (ESXi) only:
- RHEL 9 deployments are only supported on ESXi 7.0 Update 2 or later. To learn more about ESXi support, see [End-of-Support for VMware vSphere Hypervisor (ESXi) Version 5.5](/eos-eol/end-support-vmware-vsphere-hypervisor-esxi-version-5.5).
- VMware offers ESXi as part of a paid vSphere edition or free of charge with the vSphere Hypervisor edition. However, the free version of the platform does not include several deployment features. Specifically, the standalone vSphere Hypervisor edition is not able to parse the extended OVF attributes that allow you to provide the Private Cloud Controller provisioning key during deployment.
- VMware vSphere Client
- Hypervisor account
To deploy a Private Cloud Controller on vSphere Hypervisor (ESXi):
- Log in to the vSphere Hypervisor (ESXi) Server with the vSphere Client.
[See image.](#hypervisor_login)
- Go to **File > Deploy OVF Template...**.
[See image.](#hypervisor_ovftemplate)
- Complete one of the following procedures:
- Enter the following URL for the Private Cloud Controller image into the provided field, then click **Next**:** **[https://dist.private.zscaler.com/vms/VMware/2025.04/zpa-pcc-el9-2025.04.ova](https://dist.private.zscaler.com/vms/VMware/2025.04/zpa-pcc-el9-2025.04.ova)
If you use this option, the image is downloaded from the URL and uploaded to the vSphere Hypervisor (ESXi) server from the local system.
- If you’ve already downloaded the VMware image to your local system, click **Browse** to locate the file, then click **Next**.
- Verify that the **OVF Template Details** are correct, then click **Next**.
- The **Name and Location** specified in vSphere Hypervisor (ESXi) has no impact on the ZPA service. Select a name and folder that is suitable for your organization, then click **Next**.
- After you are asked to select a **Storage** configuration, make sure that you select **Thin Provision** for the disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#hypervisor_thinprovision)
- Ensure that the **Power on after deployment** checkbox is selected, then click **Finish**.
Within the **Recent Tasks** panel, you can monitor the deployment progress. After the deployment has successfully completed, ensure that the VM has powered on before proceeding to the next step.
- The Private Cloud Controller is preconfigured to obtain an IP address on its primary interface via DHCP.
- If the DHCP service is available in your environment, skip to the following step.
- If the DHCP service is not available in your environment, you must complete the following networking tasks before proceeding to step 9 below:
- [Configure Static IP Addressing](/zpa/networking-deployed-private-cloud-controllers#Static_IP)
- [Configure the Domain Name System (DNS) Resolver](/zpa/networking-deployed-private-cloud-controllers#DNS)
- Verify the local time on the VMware machine is correct. If not, update the time using [Network Time Protocol](/zpa/networking-deployed-private-cloud-controllers#NTP).
- Make any necessary network configuration changes before applying the provisioning key.
- Apply and populate the Private Cloud Controller provisioning key.
- [See instructions.](#prvskey2)
- Zscaler highly recommends [updating the Private Cloud Controller system software](/zpa/understanding-private-cloud-controller-software-upgrades) before proceeding.
[]![VMware vSphere Client login screen](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-login.png)
[]![VMware vSphere Client with File menu](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-filemenu-deployovftemp.png)
[]![VMware vSphere Client with Deploy OVF Template window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-storagediskformat.png)
- []Stop the running Private Cloud Controller service.
$ sudo systemctl stop zpa-pcc
- Create a provisioning key file with 644 permissions at `/opt/zscaler/var/pcc/provision_key`. For example:
[admin@pcc ~]$ sudo touch /opt/zscaler/var/pcc/provision_key[admin@pcc ~]$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and click **Save**. Use an editor, such as vi.
[admin@pcc ~]$ sudo vi /opt/zscaler/var/pcc/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<PCC Provisioning Key>" | sudo tee /opt/zscaler/var/pcc/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@pcc ~]$ sudo cat /opt/zscaler/var/pcc/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the Private Cloud Controller service.
[admin@pcc ~]$ sudo systemctl start zpa-pcc
- []Stop running the Private Cloud Controller service.
[admin@pcc ~]$ sudo systemctl stop zpa-pcc
- Create a provisioning key file with 644 permissions, at `/opt/zscaler/var/pcc/provision_key`. For example:
[admin@pcc ~]$ sudo touch /opt/zscaler/var/pcc/provision_key[admin@pcc ~]$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and click **Save**. Use an editor, such as vi.
[admin@pcc ~]$ sudo vi /opt/zscaler/var/pcc/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<PCC Provisioning Key>" | sudo tee /opt/zscaler/var/pcc/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@pcc ~]$ sudo cat /opt/zscaler/var/pcc/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the Private Cloud Controller service.
[admin@pcc ~]$ sudo systemctl start zpa-pcc