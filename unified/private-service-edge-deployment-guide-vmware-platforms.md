# Private Service Edge Deployment Guide for VMware Platforms
Source: https://help.zscaler.com/unified/private-service-edge-deployment-guide-vmware-platforms
PDF: https://help.zscaler.com/pdf/com/en/1496761.pdf

This deployment guide provides information on prerequisites and how to deploy a Private Service Edge on a VMware platform. For general information regarding Private Service Edge deployment, see [About Deploying Private Service Edges](/unified/about-deploying-private-service-edges-private-applications).
- [Step 1: Make sure that you have met all of the Private Service Edge Deployment Prerequisites](#step1Prereqs)
- [Step 2: (Optional) Migration Private Service Edges to RHEL 9](#step2rhel9migration)
- [Step 3: Deploy the Private Service Edge on a VMware platform](#step3Deploy)
- [Step 4: Configure the networking for the deployed Private Service Edge](#step4network)
- Step 5: Verify that the deployed Private Service Edge is [running and healthy](/unified/managing-deployed-private-service-edges-private-applications#Status). Also, check that it is meeting your sizing requirements.
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed Private Service Edge](/unified/managing-deployed-private-service-edges-private-applications).
[]
Before deploying a Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 Private Service Edges.
- [Private Service Edge Specifications and Sizing Requirements](#sizing-reqs)
- [Private Service Edge Platform Prerequisites](#platform-prereqs)
- [Private Service Edge Security Guidance and Firewall Requirements](#securityguidance-firewallreqs)
- [Private Service Edge Zscaler Client Connector Requirements](#cc-reqs)
After you have met all of the prerequisites, you can deploy the Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each Private Service Edge.
-
Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| **Active Users** | **Memory** | **vCPU or CPU Cores** |
| ---------------- | ---------- | --------------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 32 GB (34 GB with ZDX) | 16 vCPUs or 18 CPUs |
To learn more, see the [Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Service Edge must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable for both remote and office users, each Private Service Edge needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Service Edges are reachable over the internet for remote users in a disaster recovery scenario, or when the Private Service Edge is the closest Service Edge.
In the scenario where a Private Service Edge is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Service Edge's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Service Edge. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Service Edge. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a [publish IP](/unified/about-private-service-edges-private-applications#AbourSvcEdgePage) of the respective Private Service Edge. In the case of disaster recovery, you must add this IP address as the A record for that Private Service Edge.
Your firewalls must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors.
The following conditions apply to each Private Service Edge that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Service Edge is enrolled, an outbound TLS tunnel over TCP port 443 is established to the cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the Public Service Edge
- Policy configuration download
- Private Service Edge software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional Private Service Edges at any time, using the same provisioning key to add them to the existing Private Service Edge group, while ensuring network and internet connectivity. Private Service Edges are designed to scale elastically. You can deploy additional Private Service Edges in the same Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Service Edges in pairs (N+1), where N is the number of Private Service Edges as per the sizing requirements. To learn more, see [About Deploying Private Service Edges](/unified/about-deploying-private-service-edges-private-applications) and [Supported Platforms for Private Service Edges](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the Private Service Edge meets your sizing requirements. To learn more, see [Verify Private Service Edge Sizing Specifications](/unified/managing-deployed-private-service-edges-private-applications). If disk space fills up in the Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance).
Understanding Private Service Edge Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Service Edge supports up to 500 Mbps throughput. Private Service Edges communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
For example, if you have a 1 Gbps aggregate (i.e., total inbound and outbound) connection in your data center, you can use the 500 Mbps throughput guideline to make sure you have enough Private Service Edges to support the connection and have room for failover (N+1). In this case, you would need to deploy 2 to 3 Private Service Edges to support the 1 Gbps connection.
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, AppProtection, or ZDX enabled. Make sure that you have enough Private Service Edges to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Service Edges with lower specifications rather than fewer Private Service Edges with higher specifications. For example, if you have fewer Private Service Edges with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Service Edge that fails.
[]Before you begin any procedures within the[ Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform, make sure that you have met all of the following prerequisites:
- Intel x86_64/AMD64 based architecture
- systemd
- Root or sudo access to the system in order to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Service Edge provisioning key](/unified/about-private-service-edge-provisioning-keys-private-applications)
- A static MAC address
[]Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the Private Service Edge and its VMs to ensure that memory growths do not have an impact on the Private Service Edge performance. For enhanced security, you must use the passwd command to change the credentials on the default admin account. To learn more, see the [Private Service Edge Deployment Guides](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on CentOS 7.x). You can patch these systems when necessary by using the standard yum OS update mechanism. To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications). To learn more about support for CentOS 7.x, see End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x.
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting Private Service Edges using firewall policies. Additionally, if you've installed the Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Service Edge in such an environment as long as the Private Service Edge is able to reach all Zscaler data centers containing Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa?_gl=1*1842ool*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDk0NTE1MS4zMTAuMS4xNzI0OTUyMzU0LjU0LjAuMTczNzcyMjA5NQ..) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa?_gl=1*l34gc3*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDk0NTE1MS4zMTAuMS4xNzI0OTUyMzU0LjU0LjAuMTczNzcyMjA5NQ..) (for the zpatwo.net cloud).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90 day notice for activating additional IP CIDR ranges, in order to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Service Edge will not function if the TLS certificates presented by the Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Service Edge. This is necessary for allowing the Private Service Edge to resolve and reach Public Service Edges. Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa?_gl=1*1j5oz9t*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDk0NTE1MS4zMTAuMS4xNzI0OTUyMzU0LjU0LjAuMTczNzcyMjA5NQ..) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa?_gl=1*zfqh14*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDk0NTE1MS4zMTAuMS4xNzI0OTUyMzU0LjU0LjAuMTczNzcyMjA5NQ..) (for the zpatwo.net cloud). It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Service Edges require that the [Zscaler Client Connector](/unified/administration/client-connector) be at least on version 2.1.2.
[]This article provides migration instructions to replace CentOS 7 instances with Red Hat Enterprise Linux 9 (RHEL 9). The enrollment and provisioning of new Private Service Edges can be automated in a few steps using Terraform (IaC) or Container Orchestration to further simplify deployment.
Note the following requirements for successfully migrating from CentOS 7 to RHEL 9:
- Use a fresh install for all deployments.
- The EL9 repository must be used with RHEL 9 base OS. Older platform binaries (EL7/EL8) are not supported.
- Ensure that the/opt/zscaler/var folder is empty before install.
- Yum upgrades from EL7/EL8 to RHEL9 are not supported.
- Requires ESXi version 7.0 Update 2 or newer, including ESXi 8.x.
Use the following steps to migrate from CentOS 7 to RHEL 9:
- Use a current [provisioning key](/unified/about-private-service-edge-provisioning-keys-private-applications) or create a new[ Private Service Edge group](/unified/about-private-service-edge-groups-private-applications) with a provisioning key for each location.
- Verify the [version profile](/unified/configuring-version-profile) is **Default**, **Previous Default**, or **New Release** by doing one of the following:
-
If Persist Local Version Profile is Disabled, check the Version Profile inherited from the tenant.
[See image.](#version-prof-config-disabled)
-
If Persist Local Version Profile is Enabled, select an option for the Version Profile.
[See image.](#version-prof-config-enabled)
-
Follow the [step-by-step guide](/unified/private-service-edge-deployment-guide-vmware-platforms) to deploy new VMs using the RHEL 9 images and newly created provisioning keys. Ensure the yum repository is pointing to the new RHEL 9 link: `https://yum.private.zscaler.com/yum/el9`
Only RHEL 9 repositories and RPMs are supported on RHEL 9.
-
Add trusted networks and enable **Publicly Accessible** (if applicable) on the new Private Service Edge groups.
[See image.](#edit-psegroup-redhat)
- (Optional) [Disable the Private Service Edge groups](/unified/editing-private-service-edge-groups-private-applications) 15 minutes prior to the regional off-hours maintenance window to allow connections to gradually drain down.
-
During regional off hours, remove trusted networks and disable public access (if applicable) on CentOS 7 Private Service Edge groups.
[See image.](#edit-psegroup-centos)
[]
- [Deploying on VMware vCenter](#vcenter)
- [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere)
[]Before you deploy the Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Service Edge](#dhcpipaddressing)
- [Configure Static IP Addressing for a Private Service Edge](#configure-static-ip-addressing)
- [Configure Additional Interfaces for a Private Service Edge](#configure-additional-interfaces)
- [Configure Static Routing for a Private Service Edge](#configure-static-routing)
- [Configure the Domain Name System (DNS) Resolver for a Private Service Edge](#configure-dns-resolver)
- [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](#configure-ntp-servers)
- [Configure a Private Service Edge to Use an Explicit Proxy Server](#configure-to-use-explicit-proxy-server)
- [Configure yum to Use an HTTP Proxy Server](#configure-yum)
[]By default, virtual machine-based Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
- Log in to the Private Service Edge console using your admin credentials.
-
View the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Modify the connection profile using the following format: `<profile name>`` connection.id ``<new connection name>`. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
-
Review the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Edit the profile using a static IP and a default gateway with the following format: `<connection ID>`` ipv4.method manual ipv4.addresses ``<IP addresses>`` ipv4.gateway ``<gateway IP>`` ipv4.dns ``<DNS IP>`` ipv4.dns-search ``<domain name>`. For example:
`$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
-
To apply the changes, bring the connection connection ID back up. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection up LAN`
-
Verify the IP address.
`[admin@zpa-service-edge ~]$ ip addr show`
-
Verify the default gateway.
`[admin@zpa-service-edge ~]$ ip route show default`
-
Verify the DNS settings.
`[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf`
[]If necessary, additional changes can be made to interfaces by configuring new ones using `nmcli connection add con-name` or by renaming existing ones using `nmcli connection modify`.
- Log in to the Private Service Edge console using your admin credentials.
-
View the IP address.
`[admin@zpa-service-edge ~]$ ip addr show`
-
View the current connection profiles.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Configure the interface's IP network using either a dynamic or static ethernet configuration.
For dynamic, modify the connection profile. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For static, modify the connection profile and identify the IP addresses and gateway using the following format: <profile name> ipv4.method manual ipv4.addresses <address> ipv4.gateway <address>. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254`
-
To apply the changes, bring the connection profile back up. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"`
-
Reverify the IP address.
`[admin@zpa-service-edge ~]$ ip addr show`
-
Reverify the new connection.
`[admin@zpa-service-edge ~]$ nmcli connection show`
[]To add static routes to the interface control files for a Private Service Edge:
- Log in to the Private Service Edge console using your admin credentials.
-
Edit the static route for an existing ethernet connection using the following format: `<profile name>`` ipv4.routes ``<address and gateway>`. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes 192.168.2.241/24 10.10.10.1`
-
To apply the changes, bring the connection profile down and then back up. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"``[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"`
-
Verify the new route is added.
`[admin@zpa-service-edge ~]$ ip route`
[]DNS resolution is critical for the successful operation of the Private Service Edge. Private Service Edges must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Service Edge console using your admin credentials.
-
View the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show                                                `
-
Modify the DNS settings using the following format: `<profile name>`` ipv4.dns ``<nameserver IP>`. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241`
-
To apply the changes, bring the connection profile down and then back up. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"``[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"`
-
Verify the nameservers record was added.
`[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf`
[]To configure Private Service Edges to use internal NTP servers:
- Log in to the Private Service Edge console using your admin credentials.
-
Edit the /etc/chrony.conf file. Use an editor, such as vi.
`[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf`
-
Add your internal NTP servers to the list. For example:
`server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst`
-
To apply the changes, restart the chrony daemon using the following command:
`[admin@zpa-service-edge ~]$ systemctl restart chronyd`
[]If your traffic is going through a proxy, you must manually configure the Private Service Edge to work through that proxy. The following procedure allows the Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the Private Service Edge to work through an explicit proxy:
- Log in to the Private Service Edge console using your admin credentials.
-
Create a file named, `/opt/zscaler/var/service-edge/proxy`. Use an editor, such as vi.
`[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy`
Enter the proxy information using the following format: `<Proxy Hostname or IP Address>``:``<Proxy Port>`` (e.g., 192.0.2.0:0)`.
-
To apply the changes, restart the Private Service Edge using the following command:
`[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge`
The Private Service Edge will attempt to create a TLS session through the proxy specified in step 2.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS ](https://docs.centos.org/en-US/docs/)and [Red Hat](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a Private Service Edge on a VMware platform with vCenter. The following additional prerequisites apply to VMware vCenter only:
- VMware vSphere Hypervisor (ESXi) version 7.0 Update 2 or later
- Access to vCenter to deploy an OVA file as a virtual machine (VM)
- Access to vCenter to configure the virtual NIC of the VM onto the appropriate Virtual Network or VLAN
- Access to vCenter to modify the vApp attributes of the VM
- VMware vSphere Client Integration Plugin installed (which enables the functionality needed to upload new OVA/OVF images into vSphere)
To deploy a Private Service Edge on VMware vCenter:
- Obtain the latest VMware image from Zscaler. You can also use the following link to download the file for the vSphere Web Client: [https://dist.private.zscaler.com/vms/VMware/2024.06/zpa-service-edge-el9-2024.06.05.ova](https://dist.private.zscaler.com/vms/VMware/2024.06/zpa-service-edge-el9-2024.06.05.ova).
- Connect to a vCenter Server with the vSphere Web Client and log in.
[See image.](#vcenter_login)
- Click on **Home**, then click **VMs and Templates**.
[See image.](#vcenter_vmstemplates)
- From the **Actions** menu, select **Deploy OVF Template...**.
[See image.](#vcenter_deployovf)
The Deploy OVF Template window appears.
- For **1 Source > 1a Select source**, complete one of the following procedures:
- Select **URL**, enter the following URL for the Private Service Edge image into the provided field, then click **Next**:
`https://dist.private.zscaler.com/vms/VMware/2024.06/zpa-service-edge-el9-2024.06.05.ova`.
The image downloads from the link and uploads to vCenter.
- If you’ve already downloaded the VMware image to your local system, select **Local file** and **Browse...** to the location of the image file, then click **Next**.
[See image.](#vcenter_selectsource)
- For **1 Source > 1b Review** details, verify that the OVF template details are correct, then click **Next**.
[See image.](#vcenter_reviewovf)
- For **2 Destination > 2a Select name and folder**, the name and folder specified in vCenter has no impact on the service. So, select a name and folder that is suitable for your organization, then click **Next**.
[See image.](#vcenter_destinationfolder)
- For **2 Destination > 2b Select a resource**, select the destination resource (i.e., cluster, host, vApp, or resource pool), then click **Next**.
[See image.](#vcenter_destinationresource)
- For **2 Destination > 2c Select storage**, choose **Thin Provision** for the virtual disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#vcenter_destinationstorage)
- For **2 Destination > 2d Setup networks**, configure the **IP allocation** network settings as necessary.
The Private Service Edge is preconfigured to obtain an IP address on its primary interface via DHCP.
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
- Within the **Navigator** panel select the deployed VM, and from the **Actions** menu select **Edit Settings...**.
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
- Verify the local time on the VMware machine is correct. If it is not, update the time using [Network Time Protocol](/unified/private-service-edge-deployment-guide-vmware-platforms#NTP).
- Make any necessary [network configuration](/unified/private-service-edge-deployment-guide-vmware-platforms#network) changes before applying the provisioning key.
- Apply the Private Service Edge provisioning key.
- [See instructions.](#prvskey1)
- Zscaler highly recommends [updating the Private Service Edge system software](/unified/understanding-private-service-edge-software-upgrades-private-applications) before proceeding.
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
[]The following deployment procedure only provides additional information on prerequisites and how to deploy a Private Service Edge on a VMware platform with vSphere Hypervisor.
The following additional prerequisites apply to VMware vSphere Hypervisor (ESXi) only:
- RHEL 9 deployments are only supported on ESXi 7.0 Update 2 or later.
- VMware offers ESXi as part of a paid vSphere edition or free of charge with the vSphere Hypervisor edition. However, the free version of the platform does not include several deployment features. Specifically, the standalone vSphere Hypervisor edition is not able to parse the extended OVF attributes that allow you to provide the Private Service Edge provisioning key during deployment.
- VMware vSphere Client
- Hypervisor account
To deploy a Private Service Edge on vSphere Hypervisor (ESXi):
- Log in to the vSphere Hypervisor (ESXi) Server with the vSphere Client.
[See image.](#hypervisor_login)
- Go to **File > Deploy OVF Template...**.
[See image.](#hypervisor_ovftemplate)
- Complete one of the following procedures:
- Enter the following URL for the Private Service Edge image into the provided field: `https://dist.private.zscaler.com/vms/VMware/2024.06/zpa-service-edge-el9-2024.06.05.ova`, then click **Next**:
If you use this option, the image is downloaded from the URL and uploaded to the vSphere Hypervisor (ESXi) server from the local system.
- If you’ve already downloaded the VMware image to your local system, **Browse...** to the location of the image file, then click **Next**.
- Verify that the **OVF Template Details** are correct, then click **Next**.
- The **Name and Location** specified in vSphere Hypervisor (ESXi) has no impact on the service. So, select a name and folder that is suitable for your organization, then click **Next**.
- After you are asked to select a **Storage** configuration, make sure that you select **Thin Provision** for the disk format, then click **Next**. This selection generally results in smaller disk space utilization.
[See image.](#hypervisor_thinprovision)
- Ensure that **Power on after deployment** is selected, then click **Finish**.
Within the **Recent Tasks** panel, you can monitor the deployment progress. After the deployment has successfully completed, ensure that the VM has powered on before proceeding to the next step.
- The Private Service Edge is preconfigured to obtain an IP address on its primary interface via DHCP.
- If the DHCP service is available in your environment, skip to step 9 below.
- If the DHCP service is not available in your environment, you must complete the following networking tasks before proceeding to step 9 below:
- [Configure Static IP Addressing](/zpa/service-edge-deployment-guide-vmware#Static_IP)
- [Configure the Domain Name System (DNS) Resolver](/zpa/service-edge-deployment-guide-vmware#DNS)
- Verify the local time on the VMware machine is correct. If it is not, update the time using [Network Time Protocol](/unified/private-service-edge-deployment-guide-vmware-platforms#NTP).
- Make any necessary [network configuration](/unified/private-service-edge-deployment-guide-vmware-platforms#network) changes before applying the provisioning key.
- Apply and populate the Private Service Edge provisioning key.
- [See instructions.](#prvskey2)
- Zscaler highly recommends [updating the Private Service Edge system software](/unified/understanding-private-service-edge-software-upgrades-private-applications) before proceeding.
[]![VMware vSphere Client login screen](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-login.png)
[]![VMware vSphere Client with File menu](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-filemenu-deployovftemp.png)
[]![VMware vSphere Client with Deploy OVF Template window](/downloads/zpa/service-edge-deployment-guide-vmware/zpa-vmwareesxi-storagediskformat.png)
- []Stop the running Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key.
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
- []Stop the running Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key.
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
[]![version-profile-config-disabled.png](/sites/default/files/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-vmware-platforms/version-profile-config-disabled.png)
[]![version-profile-config-enabled.png](/sites/default/files/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-vmware-platforms/version-profile-config-enabled.png)
[]![edit-private-service-edge-group-red-hat.png](/sites/default/files/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-vmware-platforms/edit-private-service-edge-group-red-hat.png)
[]![edit-private-service-edge-group-centos.png](/sites/default/files/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-vmware-platforms/edit-private-service-edge-group-centos.png)