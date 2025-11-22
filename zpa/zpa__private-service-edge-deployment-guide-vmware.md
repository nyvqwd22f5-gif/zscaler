# Private Service Edge Deployment Guide for VMware Platforms
Source: https://help.zscaler.com/zpa/private-service-edge-deployment-guide-vmware
PDF: https://help.zscaler.com/pdf/com/en/1484541.pdf

This deployment guide provides information on prerequisites and how to deploy a ZPA Private Service Edge on a VMware platform. For general information regarding ZPA Private Service Edge deployment, see [About Deploying ZPA Private Service Edges](/zpa/about-deploying-service-edges).
- [Step 1: Make sure that you have met all of the ZPA Private Service Edge Deployment Prerequisites](#step1Prereqs)
- [Step 2: (Optional) Migrate ZPA Private Service Edges to RHEL 9](#rhel9migration)
- [Step 3: Deploy the ZPA Private Service Edge on a VMware platform](#step2Deploy)
- [Step 4: Disable the Password Expiration for the STIG-Hardened Private Service Edge Image](#step3disablepassword)
- [Step 5: Configure the networking for the deployed ZPA Private Service Edge](#network)
- Step 6: Verify that the deployed ZPA Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges#Status). Also, check that it meets your sizing requirements.
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your ZPA Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed ZPA Private Service Edge](/zpa/managing-deployed-zpa-private-service-edges).
[]
- [Deploying on VMware vCenter](#vcenter)
- [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere)
[]
Before deploying a ZPA Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each ZPA Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the ZPA Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 ZPA Private Service Edges.
500 Mbps of throughput is an aggregate of multiple streams of traffic.
- [ZPA Private Service Edge Specifications and Sizing Requirements](#SpecsSizing)
- [ZPA Private Service Edge Platform Prerequisites](#PlatformPrereqs)
- [ZPA Private Service Edge Security Guidance and Firewall Requirements](#Firewall)
- [ZPA Private Service Edge Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the ZPA Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each ZPA Private Service Edge.
- Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| Active Users | Memory | vCPU or CPU Cores |
| ------------ | ------ | ----------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 32 GB (34 GB with ZDX) | 16 vCPUs or 16 CPUs |
To learn more, see the [ZPA Private Service Edge Deployment Guide](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each ZPA Private Service Edge must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable ZPA for both remote and office users, each ZPA Private Service Edge needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
ZPA Private Service Edges are reachable over the internet for remote users in a disaster recovery scenario, or when the ZPA Private Service Edge is the closest Service Edge.
In the scenario where a ZPA Private Service Edge is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the ZPA Private Service Edge's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the ZPA Private Service Edge. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the ZPA Private Service Edge. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a [publish IP](/zpa/about-zpa-private-service-edges#AbourSvcEdgePage) of the respective ZPA Private Service Edge. In the case of disaster recovery, you must add this IP address as the A record for that ZPA Private Service Edge.
Your firewalls must be configured to let the ZPA Private Service Edge establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors.
The following conditions apply to each ZPA Private Service Edge that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a ZPA Private Service Edge is enrolled, an outbound TLS tunnel over TCP port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the ZPA Public Service Edge
- Policy configuration download
- ZPA Private Service Edge software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional ZPA Private Service Edges at any time, using the same provisioning key to add them to the existing ZPA Private Service Edge group, while ensuring network and internet connectivity. ZPA Private Service Edges are designed to scale elastically. You can deploy additional ZPA Private Service Edges in the same ZPA Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy ZPA Private Service Edges in pairs (N+1), where N is the number of ZPA Private Service Edges as per the sizing requirements. To learn more, see [About Deploying ZPA Private Service Edges](/zpa/about-deploying-service-edges) and [Supported Platforms for ZPA Private Service Edges](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the ZPA Private Service Edge meets your sizing requirements. To learn more, see [Verify ZPA Private Service Edge Sizing Specifications](/zpa/managing-deployed-zpa-private-service-edges#VerifySizing). If disk space fills up in the ZPA Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring ZPA Private Service Edge Performance](/zpa/monitoring-private-service-edge-performance#diskspace_archive).
Understanding ZPA Private Service Edge Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each ZPA Private Service Edge supports up to 500 Mbps throughput. ZPA Private Service Edges communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
500 Mbps of throughput is an aggregate of multiple streams of traffic.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
For example, if you have a 1 Gbps aggregate (i.e., total inbound and outbound) connection in your data center, you can use the 500 Mbps throughput guideline to make sure you have enough ZPA Private Service Edges to support the connection and have room for failover (N+1). In this case, you would need to deploy 2 to 3 ZPA Private Service Edges to support the 1 Gbps connection.
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, AppProtection, or ZDX enabled. Make sure that you have enough ZPA Private Service Edges to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more ZPA Private Service Edges with lower specifications rather than fewer ZPA Private Service Edges with higher specifications. For example, if you have fewer ZPA Private Service Edges with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller ZPA Private Service Edge that fails.
[]Before you begin any procedures within the [ZPA Private Service Edge Deployment Guide](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform, make sure that you have the following:
- Intel x86_64/AMD64-based architecture
- systemd
- Root or sudo access to the system to configure a new package repository and install packages
- DNS resolution and network access
- A [ZPA Private Service Edge provisioning key](/zpa/about-zpa-service-edge-provisioning-keys) obtained from the ZPA Admin Portal
- A static MAC address
[]ZPA Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The ZPA Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the ZPA Private Service Edge and its VMs to ensure that memory growth does not have an impact on the ZPA Private Service Edge performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [ZPA Private Service Edge Deployment Guides](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Security Technical Implementation Guide (STIG) images are provided for AWS, GCP, Microsoft Azure, Nutanix, and VMware by default. To learn more, see [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform). The remaining private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on RHEL 9.x). You can patch these systems when necessary by using the standard yum OS update mechanism. Zscaler recommends that you harden the operating system, including the `sshd-config` file, on the VM images in accordance with your organization's security standards after initial deployment. To learn more, see [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges#Updating).
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting ZPA Private Service Edges using firewall policies. Additionally, if you've installed the ZPA Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a ZPA Private Service Edge in such an environment as long as the ZPA Private Service Edge is able to reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing ZPA Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. ZPA Private Service Edge will not function if the TLS certificates presented by the ZPA Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the ZPA Private Service Edge. This is necessary for allowing the ZPA Private Service Edge to resolve and reach ZPA Public Service Edges. ZPA Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa) It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]ZPA Private Service Edges require that the [Zscaler Client Connector](/z-app) be at least on version 2.1.2.
[]
Before you deploy the ZPA Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a ZPA Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a ZPA Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a ZPA Private Service Edge](#Interfaces)
- [Configure Static Routing for a ZPA Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a ZPA Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a ZPA Private Service Edge](#NTP)
- [Configure a ZPA Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based ZPA Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a ZPA Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based ZPA Private Service Edge.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the connection profile using the following format: `<profile name>`` connection.id ``<new connection name>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN
- Review the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Edit the profile using a static IP address and a default gateway with the following format: `<connection ID>`` ipv4.method manual ipv4.addresses ``<IP addresses> ``ipv4.gateway ``<gateway IP> ``ipv4.dns ``<DNS IP> ``ipv4.dns-search ``<sub.subdomain.domain.com subdomain.domain.com domain.com>`. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
- To apply the changes, bring the connection connection ID back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up LAN
- Verify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Verify the default gateway.
[admin@zpa-service-edge ~]$ ip route show default
- Verify the DNS settings.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]If necessary, additional changes can be made to interfaces by configuring new ones using `nmcli connection add con-name` or by renaming existing ones using `nmcli connection modify`.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- View the current connection profiles.
[admin@zpa-service-edge ~]$ nmcli connection show
- Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto
For static, modify the connection profile and identify the IP addresses and gateway using the following format: `<profile name>`` ipv4.method manual ipv4.addresses ``<address>`` ipv4.gateway ``<address>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254
- To apply the changes, bring the connection profile back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Reverify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Reverify the new connection.
[admin@zpa-service-edge ~]$ nmcli connection show
[]To add static routes to the interface control files for a ZPA Private Service Edge:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the static route for an existing Ethernet connection using the following format: `<profile name>`` ipv4.routes ``<address and gateway>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes "192.168.2.241/24 10.10.10.1"
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1" [admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the new route is added.
[admin@zpa-service-edge ~]$ ip route
[]DNS resolution is critical for the successful operation of the ZPA Private Service Edge. ZPA Private Service Edges must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the DNS settings using the following format: `<profile name>`` ipv4.dns ``<nameserver IP>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]To configure ZPA Private Service Edges to use internal NTP servers:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the `/etc/chrony.conf` file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the ZPA Private Service Edge to work through that proxy. The following procedure allows the ZPA Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the ZPA Private Service Edge to work through an explicit proxy:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Create a file named `/opt/zscaler/var/service-edge/proxy`. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: `<Proxy Hostname or IP Address>``:``<Proxy Port>` (e.g., `192.0.2.0:0`)
- To apply the changes, restart the ZPA Private Service Edge using the following command:
`[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge`
The ZPA Private Service Edge will attempt to create a TLS session through the proxy specified previously.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation. To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
[]
This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new ZPA Private Service Edges can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the`/opt/zscaler/var` folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
- Requires ESXi version 7.0 Update 2 or newer, including ESXi 8.x. To learn more about ESXi support, see [End-of-Support for VMware vSphere Hypervisor (ESXi) Version 5.5](/eos-eol/end-support-vmware-vsphere-hypervisor-esxi-version-5.5).
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Use a current [provisioning key](/zpa/about-zpa-service-edge-provisioning-keys) or create a new [ZPA Private Service Edge group](/zpa/about-zpa-private-service-edge-groups) with a provisioning key for each location.
- Verify the [version profile](/zpa/configuring-version-profile) is **Default**, **Previous Default**, or **New Release** by doing one of the following:
- If **Persist Local Version Profile** is **Disabled**, check the **Version Profile** inherited from the tenant.
[See image.](#persistdisabled)
- If **Persist Local Version Profile** is **Enabled**, select an option for the **Version Profile**.
[See image.](#persistenabled)
- Follow the [step-by-step guide](/zpa/service-edge-deployment-guide-vmware) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
- Add trusted networks and enable **Publicly Accessible** (if applicable) on the new ZPA Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-01.png)
- (Optional) [Disable the ZPA Private Service Edge groups](/zpa/editing-service-edge-groups) 15 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
- During regional off hours, remove trusted networks and disable public access (if applicable) on CentOS 7 ZPA Private Service Edge groups.
![Edit private service edge group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-guide-migration-rhel9/edit-private-service-edge-group-02.png)
[]![Persist local version profile disabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-disabled-01.png)
[]![Persist local version profile enabled and version profile default](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-migration-rhel9/version-profile-config-enabled-01.png)
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a ZPA Private Service Edge on a VMware platform with vCenter. The following additional prerequisites apply to VMware vCenter only:
- VMware vCenter version ESXi 7.0 Update 2 or later
- Access to vCenter to deploy an OVA file as a virtual machine (VM)
- Access to vCenter to configure the virtual NIC of the VM onto the appropriate Virtual Network or VLAN
- Access to vCenter to modify the vApp attributes of the VM
- VMware vSphere Client Integration Plugin installed (which enables the functionality needed to upload new OVA/OVF images into vSphere)
To deploy a ZPA Private Service Edge on VMware vCenter:
- Obtain the latest VMware image from Zscaler. You can also use the following link to download the file for the vSphere Web Client:
[https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova](https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova).
- Connect to a vCenter Server with the vSphere Web Client and log in.
[See image.](#vcenter_login)
- Click on **Home**, then click **VMs and Templates**.
[See image.](#vcenter_vmstemplates)
- From the **Actions** menu, select **Deploy OVF Template**.
[See image.](#vcenter_deployovf)
The Deploy OVF Template window appears.
- For **1 Source > 1a Select source**, complete one of the following procedures:
- Select **URL**, enter the following URL for the ZPA Private Service Edge image into the provided field, then click **Next**:
`https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova`.
The image downloads from the link and uploads to vCenter.
- If you’ve already downloaded the VMware image to your local system, select **Local file** and **Browse** to the location of the image file, and then click **Next**.
[See image.](#vcenter_selectsource)
- For **1 Source > 1b Review** details, verify that the OVF template details are correct, then click **Next**.
[See image.](#vcenter_reviewovf)
- For **2 Destination > 2a Select name and folder**, the name and folder specified in vCenter has no impact on the ZPA service. So, select a name and folder that is suitable for your organization, then click **Next**.
[See image.](#vcenter_destinationfolder)
- For **2 Destination > 2b Select a resource**, select the destination resource (i.e., cluster, host, vApp, or resource pool), then click **Next**.
[See image.](#vcenter_destinationresource)
- For **2 Destination > 2c Select storage**, choose **Thin Provision** for the virtual disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#vcenter_destinationstorage)
- For **2 Destination > 2d Setup networks**, configure the **IP allocation** network settings as necessary.
The ZPA Private Service Edge is preconfigured to obtain an IP address on its primary interface via DHCP.
- If the DHCP service is available in your environment, select DHCP.
- If the DHCP service is not available in your environment, you must complete the following networking tasks:
- [Configure Static IP Addressing](/zpa/service-edge-deployment-guide-vmware#Static_IP)
- [Configure the Domain Name System (DNS) Resolver](/zpa/service-edge-deployment-guide-vmware#DNS)
[See image.](#vcenter_networksettings)
- For **3 Ready to Complete**, ensure that **Power on after deployment** is not selected, then click **Finish**.
[See image.](#vcenter_readytocomplete)
Within the Recent Tasks panel, you can monitor the deployment progress.
[See image.](#vcenter_recenttasks)
After the deployment has successfully completed, ensure that the VM has not been powered on before proceeding to the next step.
- Within the **Navigator** panel select the deployed VM, and from the **Actions** menu select **Edit Settings**.
[See image.](#vcenter_navigator)
The **Edit Settings** window appears.
- Select the **vApp Options** tab.
[See image.](#vcenter_vappoptions)
- Under **Authoring > OVF** settings:
- For **OVF environment transport**, select **VMware Tools**.
- For **Installation boot**, select **Enable**.
- Click **OK**.
[See image.](#vcenter_ovfsettings)
- From the **Actions** menu, select **Power > Power On**.
[See image.](#vcenter_poweron)
- Verify the local time on the VMware machine is correct. If it is not, update the time using [Network Time Protocol](/zpa/service-edge-deployment-guide-vmware#NTP).
- Make any necessary [network configuration](/zpa/service-edge-deployment-guide-vmware#network) changes before applying the provisioning key.
- Apply the ZPA Private Service Edge provisioning key.
- [See instructions.](#prvskey1)
- Zscaler highly recommends [updating the ZPA Private Service Edge system software](/zpa/about-service-edge-software-updates) before proceeding.
[]![Logging into the VMware Server using the vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-webclientlogin.png)
[]![Accessing VMs and Templates within the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vmsandtemplates.png)
[]![Accessing the Deploy OVF Template within the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-deployovftemplate.png)
[]![Select the source location of the VMware image file](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectsource.png)
[]![Review and verify the OVF template details](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-reviewdetails.png)
[]![Select the name and folder for the destination](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectnameandfolder.png)
[]![Select a resource for the destination ](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectaresouce.png)
[]![Select Thin Provision for the destination storage](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-selectstorage.png)
[]![Configure the network settings for the destination ](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-setupnetworks.png)
[]![Review the setting selections before completing](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-readytocomplete.png)
[]![Monitor the deployment in Recent Tasks](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-recenttaskspanel.png)
[]![VMware vSphere Web Client with Actions menu](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-actionsmenueditsettings.png)
[]![VMware vSphere Web Client with Edit Settings window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vappoptionstab.png)
[]![VMware vSphere Web Client with Edit Settings window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-vappoptions-ovfsettings.png)
![Select Power On in the VMware vSphere Web Client](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwarevcenter-actionsmenupoweron.png)
[]
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a ZPA Private Service Edge on a VMware platform with vSphere Hypervisor.
The following additional prerequisites apply to VMware vSphere Hypervisor (ESXi) only:
- RHEL 9 deployments are only supported on ESXi 7.0 Update 2 or later. To learn more about ESXi support, see [End-of-Support for VMware vSphere Hypervisor (ESXi) Version 5.5](/eos-eol/end-support-vmware-vsphere-hypervisor-esxi-version-5.5).
- VMware offers ESXi as part of a paid vSphere edition or free of charge with the vSphere Hypervisor edition. However, the free version of the platform does not include several deployment features. Specifically, the standalone vSphere Hypervisor edition is not able to parse the extended OVF attributes that allow you to provide the ZPA Private Service Edge provisioning key during deployment.
- VMware vSphere Client
- Hypervisor account
To deploy a ZPA Private Service Edge on vSphere Hypervisor (ESXi):
- Log in to the vSphere Hypervisor (ESXi) Server with the vSphere Client.
[See image.](#hypervisor_login)
- Go to **File > Deploy OVF Template...**.
[See image.](#hypervisor_ovftemplate)
- Complete one of the following procedures:
- Enter the following URL for the ZPA Private Service Edge image into the provided field: `https://dist.private.zscaler.com/vms/VMware/2025.03/zpa-service-edge-el9-2025.03.ova`, then click **Next.**
If you use this option, the image is downloaded from the URL and uploaded to the vSphere Hypervisor (ESXi) server from the local system.
- If you’ve already downloaded the VMware image to your local system, **Browse** to the location of the image file, then click **Next**.
- Verify that the **OVF Template Details** are correct, then click **Next**.
- The **Name and Location** specified in vSphere Hypervisor (ESXi) has no impact on the ZPA service. So, select a name and folder that is suitable for your organization, then click **Next**.
- After you are asked to select a **Storage** configuration, make sure that you select **Thin Provision** for the disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#hypervisor_thinprovision)
- Ensure that **Power on after deployment** is selected, then click **Finish**.
Within the **Recent Tasks** panel, you can monitor the deployment progress. After the deployment has successfully completed, ensure that the VM has powered on before proceeding to the next step.
- The ZPA Private Service Edge is preconfigured to obtain an IP address on its primary interface via DHCP.
- If the DHCP service is available in your environment, skip to step 9 below.
- If the DHCP service is not available in your environment, you must complete the following networking tasks before proceeding to step 9 below:
- [Configure Static IP Addressing](/zpa/service-edge-deployment-guide-vmware#Static_IP)
- [Configure the Domain Name System (DNS) Resolver](/zpa/service-edge-deployment-guide-vmware#DNS)
- Verify the local time on the VMware machine is correct. If it is not, update the time using [Network Time Protocol](/zpa/service-edge-deployment-guide-vmware#NTP).
- Make any necessary [network configuration](/zpa/service-edge-deployment-guide-vmware#network) changes before applying the provisioning key.
- Apply and populate the ZPA Private Service Edge provisioning key.
- [See instructions.](#prvskey2)
- Zscaler highly recommends [updating the ZPA Private Service Edge system software](/zpa/about-service-edge-software-updates) before proceeding.
[]![VMware vSphere Client login screen](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-login.png)
[]![VMware vSphere Client with File menu](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-filemenu-deployovftemp.png)
[]![VMware vSphere Client with Deploy OVF Template window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-storagediskformat.png)
- []Stop the running ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
- []Stop the running ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
[]
This information applies to Security Technical Implementation Guide (STIG) images that were released on November 24, 2024 and December 12, 2024. STIG images released after these dates are not affected.
If you're using an affected STIG image, passwords automatically expire every 60 days for Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure, or 95 days (60 days + a 35-day grace period) for VMware.
If the password expires without changing it or disabling expiration, admin access to a ZPA Private Service Edge is no longer available. When admin access expires, the only recovery method is to deploy a new ZPA Private Service Edge.
[]STIG-hardened prebuilt Private Service Edge images affected by password expiration were released on:
- AWS and GCP: November 24, 2024
- Azure and VMware: December 12, 2024
To verify if an image is STIG-hardened:
- Go to the Private Service Edges page in the ZPA Admin Portal.
- Expand the row for a Private Service Edge in the table.
- Under **Private Service Edge Host Platform**, if you see `ZSIVersion: 2024.11` or `ZSIVersion: 2024.12` for the ZSIVersion, the image is STIG-hardened.
[See image.](#StigImage)
Zscaler recommends using one of these methods for passwords:
- [Disable or Set a Password for AWS, GCP, and Azure.](#StigMarketplace)
- [Disable or Set a Password for VMware.](#StigOVAs)
- []Disable the password expiration:
-
Enter the following command (replacing `admin` with your admin username):
``[admin@zpa-service-edge ~]$ sudo chage -M -1 adm`in`
-
Verify that the password is set to never expire.
``[admin@zpa-service-edge ~]$ sudo chage -l adm`in
`Last password change                               : Feb 18, 20`25
`Password expires                                   : never`
`Password inactive                                  : never`
`Account expires                                    : never`
Minimum number of days between password change     : 1
Maximum number of days between password change     : -1
Number of days of warning before password expires  : 7`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 days.
-
[]Disable the password expiration by entering the following command (replacing `admin` with your admin username):
`$ sudo chage -M -1 admin`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 or 95 days.
[]
Example STIG-hardened image with `ZSIVersion: 2024.11.`
![Verify STIG-hardened image on a ZPA Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/app-connector-deployment-guide-amazon-web-services-draft-doc-56293/zpa-pse-stig-image-verification-nov2024.png)