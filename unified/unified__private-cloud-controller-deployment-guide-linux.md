# Private Cloud Controller Deployment Guide for Linux
Source: https://help.zscaler.com/unified/private-cloud-controller-deployment-guide-linux
PDF: https://help.zscaler.com/pdf/com/en/1528741.pdf

This deployment guide provides information on prerequisites, how to deploy a Private Cloud Controller on Red Hat Enterprise Linux 9.x, and post-deployment verification checks.
- [Step 1: Make Sure All Private Cloud Controller Deployment Prerequisites Are Met](#step1Prereqs)
- [Step 2: Configure Networking for the Deployed Private Cloud Controller](#step2network)
- [Step 3: Deploy the Private Cloud Controller on Linux](#step3deploy)
- Step 4: Verify that the deployed Private Cloud Controller is running and healthy. Also, check that it meets your sizing requirements.
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Cloud Controller console admin credentials or performing system software updates).
[]
Before deploying a Private Cloud Controller on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Cloud Controller supports between 100 to 250 Mbps of throughput. Use the information on this page to determine the Private Cloud Controller sizing requirements for your deployment. Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput.
- [Private Cloud Controller Specifications and Sizing Requirements](#SpecsSizing)
- [Private Cloud Controller Platform Prerequisites](#PlatformPrereqs)
- [Private Cloud Controller Security Guidance and Firewall Requirements](#Firewall)
- [Private Cloud Controller Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the Private Cloud Controller on a supported platform.
[]The following specifications are recommended by Zscaler for up to 250 Mbps throughput based on the sizing. Refer to the table below for the sizing and relevant SIEM data throughput.
- Memory (RAM), vCPU (for virtual machines), SIEM throughput, or CPU (for physical machines) cores:
| Active Users | Memory | SIEM Throughput | vCPU or CPU Cores |
| ------------ | ------ | --------------- | ----------------- |
| Up to 2,000 | 16 GB | 100 Mbps | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 32 GB | 150 Mbps | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 64 GB | 250 Mbps | 16 vCPUs or 16 CPUs |
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Cloud Controller must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable Private Applications for both remote and office users, each Private Cloud Controller needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Cloud Controllers are reachable over the internet for remote users in a disaster recovery scenario, or when the Private Cloud Controller is the closest Service Edge.
In the scenario where a Private Cloud Controller is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Cloud Controller's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Cloud Controller. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Cloud Controller. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a publish IP of the respective Private Cloud Controller. In the case of disaster recovery, you must add this IP address as the A record for that Private Cloud Controller.
Your firewalls must be configured to let the Private Cloud Controller establish outbound connections to the IP addresses of the Public Service Edge for Private Applications, and establish inbound connections from App Connectors, Private Service Edges for Private Applications, and Zscaler Client Connectors.
The following conditions apply to each Private Cloud Controller that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Cloud Controller is enrolled, an outbound TLS tunnel over TCP port 443 is established to the Private Applications cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the Public Service Edge for Private Applications
- Policy configuration download
- Private Cloud Controller software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional Private Cloud Controllers at any time, using the same provisioning key to add them to the existing Private Cloud Controller group, while ensuring network and internet connectivity. Private Cloud Controllers are designed to scale elastically. You can deploy additional Private Cloud Controllers in the same Private Cloud Controller group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Cloud Controllers in pairs (N+1), where N is the number of Private Cloud Controllers as per the sizing requirements. To learn more, see [Deploying Private Cloud Controllers](/unified/deploying-private-cloud-controllers) and [Private Cloud Controller Deployment Guide for Linux](/unified/private-cloud-controller-deployment-guide-linux).
After deployment, ensure that the Private Cloud Controller meets your sizing requirements. If disk space fills up in the Private Cloud Controller, Zscaler recommends archiving files and creating more log space.
Understanding Private Cloud Controller Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Cloud Controller supports up to 250 Mbps throughput. Private Cloud Controllers communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
Private Cloud Controller sizing must be based on the number of users that need to be redirected and the expected SIEM throughput. The exact throughput can vary and depends on other network factors such as your internal network setup and latency. Make sure that you have enough Private Cloud Controllers to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Cloud Controllers with lower specifications rather than fewer Private Cloud Controllers with higher specifications. For example, if you have fewer Private Cloud Controllers with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Cloud Controller that fails.
[]Before you begin any procedures within the [Private Cloud Controller Deployment Guide for Linux](/unified/private-cloud-controller-deployment-guide-linux), make sure that you have met all of the following prerequisites:
- Intel x86_64/AMD64 based architecture
- systemd
- Root or sudo access to the system in order to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Cloud Controller provisioning key](/unified/about-private-cloud-controller-provisioning-keys) obtained from the Admin Portal
- A static MAC address
[]Private Cloud Controllers can be deployed in different ways, so the security features for each deployment type are slightly different.
Operating System Security
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Cloud Controller in such an environment as long as the Private Cloud Controller can reach all Zscaler data centers containing Public Service Edges for Private Applications. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Cloud Controllers do not function if the TLS certificates presented by the ZPA Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Cloud Controller. This is necessary to allow the Private Cloud Controller to resolve and reach ZPA Public Service Edges. Private Cloud Controller requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Cloud Controllers require that the Zscaler Client Connector is at least on version 4.6 or later for Windows.
[]
Before you deploy the Private Cloud Controller on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Cloud Controller](#DHCP_IP)
- [Configure Static IP Addressing for a Private Cloud Controller](#Static_IP)
- [Configure the Domain Name System (DNS) Resolver for a Private Cloud Controller](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a Private Cloud Controller](#NTP)
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
[]DNS resolution is critical for the successful operation of the Private Cloud Controller. Private Cloud Controllers must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Cloud Controller console using your admin credentials.
- View the current connection profile.
[admin@pcc ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@pcc ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@pcc ~]$ sudo nmcli connection down "Profile 1"[admin@pcc ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@pcc ~]$ sudo cat /etc/resolv.conf
[]To configure Private Cloud Controllers to use internal NTP servers:
- Log in to the Private Cloud Controller console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@pcc ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@pcc ~]$ systemctl restart chronyd
[]To deploy a Private Cloud Controller, you need to download the RPM package on the Private Cloud Controller you're deploying. However in some cases, the Private Cloud Controller might be unable to download the package, and you'll have to download it on a server instead. Choose one of the following deployment options depending on your situation.
- [Downloading the RPM Package on the Private Cloud Controller](#RPMserviceedge)
- [Downloading the RPM Package on a Server](#RPMserver)
[]If the Private Cloud Controller can download the RPM package:
- Log in to the Private Cloud Controller console with sudo access or directly as the root user.
- Create a file named /etc/yum.repos.d/zscaler.repo. Use an editor, such as vi.
[admin@zpa-pcc ~]$ sudo vi /etc/yum.repos.d/zscaler.repo
Enter the following content within the file:
[zscaler]
name=Zscaler Private Access Repository
baseurl=https://yum.private.zscaler.com/yum/el9
enabled=1
gpgcheck=1
gpgkey=https://yum.private.zscaler.com/yum/el9/gpg
- Install the package using the yum install command.
[admin@pcc ~]$ sudo yum install zpa-pcc
- The Private Cloud Controller console asks for confirmation twice. Enter `y` both times and ensure that the GPG fingerprint matches (a6fe 2422 fce7 e8ac 672e 9e51 644e a315 8765 e1dd)as highlighted in green within the example below:
[admin@pcc ~]$ sudo yum install zpa-pcc
Loaded plugins: fastestmirror, langpacks
Determining fastest mirrors
* base: mirror.keystealth.org
* epel: mirrors.kernel.org
* extras: mirror.lug.udel.edu
* updates: mirrors.cat.pdx.edu
Resolving Dependencies
--> Running transaction check
---> Package zpa-pcc.x86_64 0:25.42.4-1.el9 will be installed
--> Finished Dependency Resolution
Dependencies Resolved
================================================================================
Package              Arch         Version             Repository         Size
================================================================================
Installing:
zpa-pcc     x86_64       25.42.4-1.el9       zscaler            1.1 M
Transaction Summary
================================================================================
Install 1 Package
Total download size: 1.1 M
Installed size: 2.9 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7/zscaler/packages/zpa-pcc-25.42.4-1.el9.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 8765e1dd: NOKEY kb 00:00:01 ETA
Public key for zpa-pcc-25.42.4-1.el9.x86_64.rpm is not installed
zpa-pcc-25.42.4-1.el9.x86_64.rpm                                                                                               | 1.1 MB      00:00:03
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
Installing : zpa-pcc-25.42.4-1.el9.x86_64                          1/1
Verifying  : zpa-pcc-25.42.4-1.el9.x86_64                           1/1
Installed:
zpa-pcc.x86_64 0:25.42.4-1.el9
Complete!
- Populate and apply the Private Cloud Controller provisioning key.
-
[See instructions.](#pkey_original)
After the Private Cloud Controller provisioning key is applied, and you have made any necessary network configuration changes, be sure to verify that the deployed Private Cloud Controller is running and healthy.
- Zscaler highly recommends [updating the Private Cloud Controller system software](/unified/understanding-private-cloud-controller-software-upgrades) before proceeding.
[]If the Private Cloud Controller can't download the RPM package, you must download the package on a server:
- Download the following files on a server with access for Red Hat Enterprise Linux 9-based deployments:
- RPM package ([zpa-pcc.rpm](https://yum.private.zscaler.com/yum/el9/zpa-pcc-25.42.4-1.el9.x86_64.rpm))
- GPG public key ([https://yum.private.zscaler.com/yum/el9/gpg](https://yum.private.zscaler.com/yum/el9/gpg))
- Use the scp command to copy the RPM package to the Private Cloud Controller, for example:
$ scp zpa-pcc.rpm admin@<server>:/home/admin
$ scp gpg admin@<server>:/home/admin
- Run chmod 777 zpa-pcc.rpm.
[admin@pcc ~]$ chmod 777 zpa-pcc.rpm
- Install using the yum install command.
[admin@pcc ~]$ sudo yum install zpa-pcc.rpm​​​​​
- Run cd.
[admin@pcc ~]$ cd /opt/zscaler/var/pcc/
- Apply the Private Cloud Controller provisioning key.
-
[See instructions.](#pkey_duplicate)
- Run the following command:
[admin@pcc ~]$ iptables -I INPUT 1 -j ACCEPT
- Zscaler highly recommends [updating the Private Cloud Controller system software](/unified/understanding-private-cloud-controller-software-upgrades) before proceeding.
- []Stop running the Private Cloud Controller service.
[admin@pcc ~]$ sudo systemctl stop zpa-pcc
- Create a provisioning key file with 644 permissions, at `/opt/zscaler/var/service-edge/provision_key`. For example:
[admin@pcc ~]$ sudo touch /opt/zscaler/var/pcc/provision_key
[admin@pcc ~]$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@pcc ~]$ sudo vi /opt/zscaler/var/pcc/provision_key
- Enter the following command to verify the file's content:
[admin@pcc ~]$ sudo cat /opt/zscaler/var/pcc/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-pcc service.
[admin@pcc ~]$ sudo systemctl start zpa-pcc
- []Stop running the Private Cloud Controller service.
[admin@pcc ~]$ sudo systemctl stop zpa-pcc
- Create a provisioning key file with 644 permissions at `/opt/zscaler/var/service-edge/provision_key`. For example:
[admin@pcc ~]$ sudo touch /opt/zscaler/var/pcc/provision_key
[admin@pcc ~]$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@pcc ~]$ sudo vi /opt/zscaler/var/pcc/provision_key
- Enter the following command to verify the file's content:
[admin@pcc ~]$ sudo cat /opt/zscaler/var/pcc/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-pcc service.
[admin@pcc ~]$ sudo systemctl start zpa-pcc