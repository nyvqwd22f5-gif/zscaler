# Private Service Edge Deployment Guide for Linux
Source: https://help.zscaler.com/zpa/private-service-edge-deployment-guide-linux
PDF: https://help.zscaler.com/pdf/com/en/1484566.pdf

This deployment guide provides information on prerequisites, how to deploy a ZPA Private Service Edge on Red Hat Enterprise Linux 9.x (and 8.x), and post-deployment verification checks.
- [Step 1: Make Sure That You Have Met All of the ZPA Private Service Edge Deployment Prerequisites](#step1Prereqs)
- [Step 2: Configure the Networking for the Deployed ZPA Private Service Edge](#step2network)
- [Step 3: (Optional) Migrate ZPA Private Service Edges to Red Hat Enterprise Linux 9](#rhel9migration)
- [Step 4: Deploy the ZPA Private Service Edge on CentOS, Oracle, or Red Hat](#step3deploy)
- Step 5: Verify that the deployed ZPA Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges#Status). Also, check that it meets your sizing requirements.
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your ZPA Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges).
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
[]To deploy a ZPA Private Service Edge, you need to download the RPM package on the ZPA Private Service Edge you're deploying. However in some cases, the ZPA Private Service Edge might be unable to download the package, and you'll have to download it on a server instead. Choose one of the following deployment options depending on your situation.
- [Downloading the RPM Package on the ZPA Private Service Edge](#RPMserviceedge)
- [Downloading the RPM Package on a Server](#RPMserver)
[]If the ZPA Private Service Edge can download the RPM package:
- Log in to the ZPA Private Service Edge console with sudo access or directly as the root user.
- Create a file named `/etc/yum.repos.d/zscaler.repo`. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/yum.repos.d/zscaler.repo
Enter the following content within the file:
[zscaler]
name=Zscaler Private Access Repository
baseurl=https://yum.private.zscaler.com/yum/el9
enabled=1
gpgcheck=1
gpgkey=https://yum.private.zscaler.com/yum/el9/gpg
For Red Hat Enterprise Linux 8-based deployments, you must use `https://yum.private.zscaler.com/yum/el8` as the `baseurl`.
- Install the package using the `yum install` command.
[admin@zpa-service-edge ~]$ sudo yum install zpa-service-edge
- The ZPA Private Service Edge console asks for confirmation twice. Enter y both times and ensure that the GPG fingerprint matches, `a6fe 2422 fce7 e8ac 672e 9e51 644e a315 8765 e1dd`, as highlighted in green within the example below:
[admin@zpa-service-edge ~]$ sudo yum install zpa-service-edge
Loaded plugins: fastestmirror, langpacks
Determining fastest mirrors
* base: mirror.keystealth.org
* epel: mirrors.kernel.org
* extras: mirror.lug.udel.edu
* updates: mirrors.cat.pdx.edu
Resolving Dependencies
--> Running transaction check
---> Package zpa-service-edge.x86_64 0:25.49.5-1.el9 will be installed
--> Finished Dependency Resolution
Dependencies Resolved
================================================================================
Package              Arch         Version             Repository         Size
================================================================================
Installing:
zpa-service-edge     x86_64       25.49.5-1.el9       zscaler            1.1 M
Transaction Summary
================================================================================
Install 1 Package
Total download size: 1.1 M
Installed size: 2.9 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7/zscaler/packages/zpa-service-edge-25.49.5-1.el9.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 8765e1dd: NOKEY kb 00:00:01 ETA
Public key for zpa-service-edge-25.49.5-1.el9.x86_64.rpm is not installed
zpa-service-edge-25.49.5-1.el9.x86_64.rpm                                                                                               | 1.1 MB      00:00:03
Retrieving key from https://yum.private.zscaler.com/gpg
Importing GPG key 0x8765E1DD:
Userid    : "Zscaler, Inc. (External Package Repository Signing Key) <ext-pkg-repo@zscaler.com>"
Fingerprint: a6fe 2422 fce7 e8ac 672e 9e51 644e a315 8765 e1dd
From      : https://yum.private.zscaler.com/gpg
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Installing : zpa-service-edge-25.49.5-1.el9.x86_64                          1/1
Verifying  : zpa-service-edge-25.49.5-1.el9.x86_64                           1/1
Installed:
zpa-service-edge.x86_64 0:25.49.5-1.el9
Complete!
- Populate and apply the ZPA Private Service Edge provisioning key.
- [See instructions.](#pkey_original)
After the ZPA Private Service Edge provisioning key is applied, and you have made any necessary [network configuration changes](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat), be sure to verify that the deployed ZPA Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges#Status).
- Zscaler highly recommends [updating the ZPA Private Service Edge system software](/zpa/about-service-edge-software-updates) before proceeding.
Console outputs reference 25.49.5-1.el9 if you are using the ZPA Private Service Edge RPM for Red Hat Enterprise Linux 9-based deployments.
[]If the ZPA Private Service Edge can't download the RPM package, you must download the package on a server:
- Download the following files on a server with access:
- For Red Hat Enterprise Linux 8-based deployments:
- RPM package ([zpa-service-edge.rpm](https://yum.private.zscaler.com/yum/el8/zpa-service-edge-25.49.5-1.el8.x86_64.rpm))
- GPG public key ([https://yum.private.zscaler.com/yum/el8/gpg](https://yum.private.zscaler.com/yum/el8/gpg))
- For Red Hat Enterprise Linux 9-based deployments:
- RPM package ([zpa-service-edge.rpm](https://yum.private.zscaler.com/yum/el9/zpa-service-edge-25.49.5-1.el9.x86_64.rpm))
- GPG public key ([https://yum.private.zscaler.com/yum/el9/gpg](https://yum.private.zscaler.com/yum/el9/gpg))
- Use the scp command to copy the RPM package to the ZPA Private Service Edge, for example:
$ scp zpa-service-edge.rpm admin@<server>:/home/admin
$ scp gpg admin@
- Run `chmod 777 zpa-service-edge.rpm`.
[admin@zpa-service-edge ~]$ chmod 777 zpa-service-edge.rpm
- Install using the `yum install` command.
[admin@zpa-service-edge ~]$ sudo yum localinstall zpa-service-edge.rpm​​​​​
- Run `cd`.
[admin@zpa-service-edge ~]$ cd /opt/zscaler/var/service-edge/
- Apply the ZPA Private Service Edge provisioning key.
- [See instructions.](#pkey_duplicate)
- Run the following:
[admin@zpa-service-edge ~]$ iptables -I INPUT 1 -j ACCEPT
- Zscaler highly recommends [updating the ZPA Private Service Edge system software](/zpa/about-service-edge-software-updates) before proceeding.
- []Stop the running ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-service-edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
- []Stop running the ZPA Private Service Edge service.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-service-edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge