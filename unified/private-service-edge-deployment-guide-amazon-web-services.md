# Private Service Edge Deployment Guide for Amazon Web Services
Source: https://help.zscaler.com/zpa/private-service-edge-deployment-guide-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1484556.pdf

This deployment guide provides information on prerequisites, how to deploy a ZPA Private Service Edge on Amazon Web Services (AWS) and post-deployment verification checks.
- [Step 1: Make Sure That You Have Met All of the ZPA Private Service Edge Deployment Prerequisites](#step1Prereqs)
- [Step 2: Configure the Networking for the Deployed ZPA Private Service Edge](#step2network)
- [Step 3: Disable the Password Expiration for the STIG-Hardened Private Service Edge Image](#step3disablepassword)
- [Step 4: Deploy the ZPA Private Service Edge on Amazon Web Services (AWS)](#deploy)
- Step 5: Verify that the deployed ZPA Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges#Status). Also, check that it meets your [sizing requirements](/zpa/service-edge-deployment-guide-amazon-web-services#step1Prereqs).
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
[]For AWS, you must deploy ZPA Private Service Edges in your Virtual Private Clouds (VPCs). For each VPC, there should be a pair of ZPA Private Service Edges deployed for resilience and scalability. The ZPA Private Service Edges should be deployed across Availability Zones to ensure continuity of service in the event of an incident. Zscaler automatically load balances across the ZPA Private Service Edges. Additional capacity can be handled by adding additional ZPA Private Service Edges into each Availability Zone.
If Instance Metadata Service Version 2 (IMDSv2) is enabled, ZPA Private Service Edges will fetch the AWS VM ID.
ZPA Private Service Edges should be in appropriate security groups to accept incoming connections from Zscaler Client Connector and App Connectors. The ZPA Private Service Edges' security group should permit inbound and outbound access on port 443. The security group should allow inbound SSH to the AWS EC2 instance.
- [Deploying a ZPA Private Service Edge using the Instance Wizard](#wizard)
- [Deploying a ZPA Private Service Edge using a Launch Template with Auto Scaling (Advanced Deployment)](#launchtemplate)
[]This procedure describes how you can deploy ZPA in AWS using the instance wizard. If you require a more scalable solution, Zscaler recommends deploying the ZPA Private Service Edge using a Launch Template with Auto Scaling.
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances. It is also assumed that you already have a security group created and have edit access to it.
To deploy a ZPA Private Service Edge on AWS using the instance wizard:
- Log in to the AWS Management Console.
- Click **EC2**.
- On the **EC2 Dashboard** page, under the **Create Instance** section, click **Launch Instance**. Within the EC2 Management Console, the instance wizard appears.
- In **Step 1: Choose AMI**, under **Community AMIs**, search for `ZPA Private Service Edge`.
The ZPA Private Service Edge AMI is currently available under **Community AMIs** for regions **US West (Oregon) - us-west-2** and **US East (N. Virginia) us-east-1**. If you require an AMI in another region, you can request this through Zscaler Support.
Alternatively, you can deploy ZPA Private Service Edge on a [CentOS 7.x instance](/zpa/service-edge-deployment-guide-centos-oracle-and-redhat#step3deploy), using one of the deployment options in step 3. Make sure the CentOS 7.x meets the requirements in the [prerequisites](/zpa/zpa-service-edge-deployment-prerequisites). To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
- When the **Zscaler Private Access Service Edge** AMI appears, click **Select**.
- In **Step 2: Choose an Instance Type**, select an instance type that supports the ZPA Private Service Edge's [sizing requirements](/zpa/service-edge-deployment-guide-amazon-web-services#step1Prereqs).
- Click **Next: Configure Instance Details**.
- In **Step 3: Configure Instance**:
- Choose suitable values for your VPC.
- For **Auto-assign Public IP**, choose **Enable**.
- Click **Review and Launch**.
- In **Step 7: Review Instance Launch**, verify the instance configuration.
A ZPA Private Service Edge needs inbound and outbound access on TCP port 443, so ensure that the security group is configured accordingly.
- Click **Launch** to power on the instance.
- Verify that the instance launched successfully and that the **Instance State** is running.
- Click **Connect**.
In the **Connect To Your Instance** window that appears, take note of the private key name (i.e., a .pem file) and the public hostname or IP address for your instance. You will need this information for the next step.
If the proper columns are shown, you can also see this information within the table on the **Instances** page.
- Update the security group associated with the ZPA Private Service Edge to temporarily allow inbound access on port 22, then complete the following steps to connect to the instance. SSH access is required to configure the provisioning key for the ZPA Private Service Edge.
- [See instructions.](#securitygrp)
- Apply the ZPA Private Service Edge provisioning key.
- [See instructions.](#provisionkey1)
After the ZPA Private Service Edge provisioning key is applied, be sure to verify that the deployed ZPA Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges#Status).
- Zscaler highly recommends updating the host OS software before proceeding.
- []Log in to the ZPA Private Service Edge console using your admin credentials.
After the initial boot of a ZPA Private Service Edge instance, it might take up to 15 minutes for the admin credentials to apply. If you receive an invalid credentials error after initial boot, wait a few minutes and try again.
-
Using a standard SSH client, enter the following command to connect to the AWS instance: `ssh -i admin@`.
In the following example, the private key for the AWS instance is `AWS.pem` and the ZPA Private Service Edge IP address is 172.16.255.255: `ssh -i AWS.pem admin@172.16.255.25`.
- When asked if you want to continue connecting, enter `yes`.
- []Stop running the zpa-service-edge service. If the provisioning key is not detected when the ZPA Private Service Edge first starts, the ZPA Private Service Edge is in a sleep cycle and looks for the key again every 24 hours.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at `/opt/zscaler/var/service-edge/provision_key`. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save it. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-service-edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
In AWS, make sure you disable inbound access on port 22 for the security group associated with the ZPA Private Service Edge.
[]This procedure describes how you can deploy ZPA in AWS through Launch Templates and Auto Scaling configurations to create a scalable and supportable infrastructure.
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances.
To deploy a ZPA Private Service Edge on AWS using a Launch Template with Auto Scaling:
- Log in to the AWS Management Console.
- Click **EC2**.
- In the left-side navigation, under **Network & Security**, click **Security Groups**.
- Click **Create Security Group**.
The **Create Security Group** window appears.
- In the **Create Security Group** window:
- Enter a **Security group **name.
- Enter a **Description**.
- Select the proper **VPC** from the drop-down menu.
- On the **Outbound** tab, allow access to 0.0.0.0/0 on all ports.
If necessary, outbound access can be restricted to ZPA hosts and ports. For details regarding required IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
- On the **Inbound** tab, allow access to the public IP address on port 443.
-
Click **Create**.
The new group appears on the **Security Groups** page.
- In the left-side navigation, under **Instances**, click **Launch Templates**.
- Click **Create launch template**.
Within the EC2 Management Console, the **Create launch template** page appears.
- Create a launch template on the **Create launch template** page.
- [See Instructions.](#createtemplate)
- On the confirmation page that appears, click **Create Auto Scaling Group**.
Within the EC2 Management Console, the **Create Auto Scaling Group** wizard appears.
- In **Step 1: Configure Auto Scaling group details**, the **Launch Template** you created previously is automatically selected:
- **Group name**: Enter a name for the Auto Scaling group.
- **Group size**: Enter `2`.
- **Subnet**: Select a subnet from the drop-down menu. This is where your ZPA Private Service Edges are deployed. As stated previously, for each VPC there should be a pair of ZPA Private Service Edges deployed for resilience and scalability, so make sure that you select 2 subnets from the drop-down menu.
- Click **Next: Configure scaling policies**.
- In **Step 2: Configure scaling policies**:
- Select **Use scaling policies to adjust the capacity of this group**.
- Enter the minimum and maximum size for the scale between instances.
- **Name**: Enter a name for the group.
- **Metric type**: Select **Average CPU Utilization** from the drop-down menu.
- **Target value**: Enter `50`.
Your scaling policy should start with the initial deployment of 2 ZPA Private Service Edges; each ZPA Private Service Edge is capable of passing 400 to 500 Mbps traffic. An additional ZPA Private Service Edge can be added when this limit is reached, which occurs when the ZPA Private Service Edge runs at about 50% CPU utilization. To learn more about ZPA Private Service Edge throughput, see [ZPA Private Service Edge Specifications and Sizing Requirements](#step1Prereqs).
- Click **Next: Configure Notifications**.
- In **Step 3: Configure Notifications**, set up your notifications as needed and click **Next: Configure Tags**. To learn more, refer to the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ASGettingNotifications.html#as-configure-asg-for-sns).
- In **Step 4: Configure Tags**, set up your tags as needed and click **Review**. To learn more, refer to the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-tagging.html).
- In **Step 5: Review**, verify your configuration settings and click **Create Auto Scaling group**.
After the ZPA Private Service Edges are initialized, they'll be provisioned into the ZPA Private Service Edge group you specified in theZPA Admin Portal. The provisioning is based on the provisioning key included in the [script you entered](#user-data-script) in the **User data** field for the Launch Template and Auto Scaling Group configuration.
- Zscaler highly recommends [updating the ZPA Private Service Edge system software](/zpa/about-service-edge-software-updates) before proceeding.
- []Make sure that **Create a new template** is selected.
- Enter a **Launch template name**.
- Enter a **Template version description**.
- Under the **Launch template contents** section, click **Search for AMI**.
- In the **Search for AMI** window that appears:
- From the **AMI catalog** menu, select **Community AMIs**.
- From the **AMI menu**, filter for `zpa-service-edge-2023.03` and select it from the list.
- For **Instance type**, select a type that supports the ZPA Private Service Edge's [sizing requirements](#step1Prereqs).
- Select the proper SSH **Key pair name** to deploy.
- For **Network type**, make sure **VPC** is selected.
- From the **Security Groups** drop-down menu, select the group you created in step 5.
- (Optional) You can customize your **Network interfaces**, if necessary. However, the default settings are adequate for deployment.
- (Optional) You can add **Tags** to the launch template, if necessary. To learn more, refer to the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html).
- Expand the **Advanced details** section.
- []Within the **User data** field, enter the following script:
#!/bin/bash
#Stop the Service Edge service which was auto-started at boot time
systemctl stop zpa-service-edge
#Create a file from the Service Edge provisioning key created in the ZPA Admin Portal
#Make sure that the provisioning key is between double quotes
echo "<Service Edge Provisioning Key>" > /opt/zscaler/var/service-edge/provision_key
#Run a yum update to apply the latest patches
yum update -y
#Start the Service Edge service to enroll it in the ZPA cloud
systemctl start zpa-service-edge
#Wait for the Service Edge to download latest build
sleep 60
#Stop and then start the Service Edge for the latest build
systemctl stop zpa-service-edge
systemctl start zpa-service-edge
In the `echo` statement above, make sure that you have included the ZPA Private Service Edge provisioning key you copied from the ZPA Admin Portal, for example:
The domain (e.g., api.private.com) in the echo statement will depend on which ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
echo
"1|api.private.zscaler.com|IhQ9C+gJG+x1AFcO3XGlrMW1SDkIuuyRsNwfB4B+cDc2RNNPePNGuI26N/zZJ08ZjaGW5EKiIQ28rfE9TobevoQAt192+CcUgiKUCtGO7w5+2MeOmhiOTjB+Ox/PlWEoJSqqZFKR5EdNDZr+zd2/gYXTNAn8oG+BDT7NMV7YocvcnvBZG6DfOImAwtSlOSY45tJprEtoCSpT+SCsijyPCuv61QdqObIJcnA5Cs8jo6LjSqqlVYkBYgTEJgZdNKHlMkV5lxk/Ayh43A4hGLCnY+InMTj0sF7US8/NZlR/2mdAbAbmf+1ujDr/k1YgC9QQX3alr7qpHIFO/HxvyutzIu9+QXqkdCA6tL8o+RQiFrDJ7YTiQ/HxlVPlN0tKyw2K" > /opt/zscaler/var/service-edge/provision_key For all other fields within this section, the default settings are adequate for deployment.
- Click **Create launch template**.