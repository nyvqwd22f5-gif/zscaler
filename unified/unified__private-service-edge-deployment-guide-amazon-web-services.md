# Private Service Edge Deployment Guide for Amazon Web Services
Source: https://help.zscaler.com/unified/private-service-edge-deployment-guide-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1498076.pdf

This deployment guide provides information on prerequisites, how to deploy a Private Service Edge on Amazon Web Services (AWS) and post-deployment verification checks.
- [Step 1: Make Sure That You Have Met All of the Private Service Edge Deployment Prerequisites](#step1Prereqs)
- [Step 2: Configure the Networking for the Deployed Private Service Edge](#step2network)
- [Step 3: Deploy the Private Service Edge on Amazon Web Services (AWS)](#deploy)
- Step 4: Verify that the deployed Private Service Edge is [running and healthy](/unified/managing-deployed-private-service-edges-private-applications#Status). Also, check that it is meeting your [sizing requirements](/unified/private-service-edge-deployment-guide-amazon-web-services#step1Prereqs).
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications).
[]
Before deploying a Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 Private Service Edges.
- [Private Service Edge Specifications and Sizing Requirements](#sizing_reqs)
- [Private Service Edge Platform Prerequisites](#prereq)
- [Private Service Edge Security Guidance and Firewall Requirements](#securityguidancefirewallreqs)
- [Private Service Edge Zscaler Client Connector Requirements](#clientconnectorres)
After you have met all of the prerequisites, you can deploy the Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each Private Service Edge.
-
Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| Active Users | Memory | vCPU or CPU Cores |
| ------------ | ------ | ----------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 16 GB (18 GB with ZDX) | 16 vCPUs or 16 CPUs |
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
You can deploy additional Private Service Edges at any time, using the same provisioning key to add them to the existing Private Service Edge group, while ensuring network and internet connectivity. Private Service Edges are designed to scale elastically. You can deploy additional Private Service Edges in the same Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Service Edges in pairs (N+1), where N is the number of Private Service Edges as per the sizing requirements. To learn more, see [About Deploying Private Service Edges ](/unified/about-deploying-private-service-edges-private-applications)and [Supported Platforms for Private Service Edges](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the Private Service Edge meets your sizing requirements. To learn more, see [Verify Private Service Edge Sizing Specifications](/unified/managing-deployed-private-service-edges-private-applications). If disk space fills up in the Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance).
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
- A Private Service Edge provisioning key obtained from the Admin Portal
- A static MAC address
[]Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the Private Service Edge and its VMs to ensure that memory growths do not have an impact on the Private Service Edge performance. For enhanced security, you must use the passwd command to change the credentials on the default admin account. To learn more, see the[ Private Service Edge Deployment Guides](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on CentOS 7.x). You can patch these systems when necessary by using the standard yum OS update mechanism. To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications). To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting Private Service Edges using firewall policies. Additionally, if you've installed the Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Service Edge in such an environment as long as the Private Service Edge is able to reach all Zscaler data centers containing Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa?_gl=1*swxzud*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDg4MTk3OC4zMDkuMS4xNzI0ODgzMzM3LjM0LjAuOTg5MTEyNzA5) (for the private.zscaler.com cloud) or config.zscaler.com/zpatwo.net/zpa (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90 day notice for activating additional IP CIDR ranges, in order to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Service Edge will not function if the TLS certificates presented by the Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Service Edge. This is necessary for allowing the Private Service Edge to resolve and reach Public Service Edges. Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa ](https://config.zscaler.com/private.zscaler.com/zpa?_gl=1*18i0rqk*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDg4MTk3OC4zMDkuMS4xNzI0ODgzNTA1LjIuMC45ODkxMTI3MDk.)(for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa?_gl=1*18i0rqk*_gcl_au*MTk3MzQ4MDc5Ny4xNzIyMjY0MzE3*_ga*MTczMTUxNjQzNS4xNzA2NjMzNTAw*_ga_10SPJ4YJL9*MTcyNDg4MTk3OC4zMDkuMS4xNzI0ODgzNTA1LjIuMC45ODkxMTI3MDk.) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa). It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Service Edges require that the [Zscaler Client Connector](/client-connector) be at least on version 2.1.2.
[]
Before you deploy the Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Service Edge](#configuredhcp)
- [Configure Static IP Addressing for a Private Service Edge](#staticip)
- [Configure Additional Interfaces for a Private Service Edge](#additionalinterface)
- [Configure Static Routing for a Private Service Edge](#staticrouting)
- [Configure the Domain Name System (DNS) Resolver for a Private Service Edge](#dnsresolver)
- [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](#ntpservers)
- [Configure a Private Service Edge to Use an Explicit Proxy Server](#explicitproxyserver)
- [Configure yum to Use an HTTP Proxy Server](#configureyumtouseanhttp)
[]By default, virtual machine-based Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
- If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
-
View the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Modify the connection profile using the following format: <profile name> connection.id <new connection name>. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
-
Review the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Edit the profile using a static IP and a default gateway with the following format: <connection ID> ipv4.method manual ipv4.addresses <IP addresses> ipv4.gateway <gateway IP> ipv4.dns <DNS IP> ipv4.dns-search <domain name>. For example:
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
`[admin@zpa-service-edge ~]$ sud cat /etc/resolv.conf`
[]If necessary, additional changes can be made to interfaces by configuring new ones using `nmcli connection add con-name` or by renaming existing ones using `nmcli connection modify`.
- Log in to the Private Service Edge console using your admin credentials.
-
View the IP address.
`[admin@zpa-service-edge ~]$ ip addr show`
-
View the current connection profiles.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For static, modify the connection profile and identify the IP addresses and gateway using the following format: `<profile name>`` ipv4.method manual ipv4.addresses ``<address>`` ipv4.gateway ``<address>``.` For example:
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
`[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"
[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"`
-
Verify the new route is added.
[admin@zpa-service-edge ~]$ ip route
[]DNS resolution is critical for the successful operation of the Private Service Edge. Private Service Edges must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Service Edge console using your admin credentials.
-
View the current connection profile.
`[admin@zpa-service-edge ~]$ nmcli connection show`
-
Modify the DNS settings using the following format: `<profile name>`` ipv4.dns ``<nameserver IP>`. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241`
-
To apply the changes, bring the connection profile down and then back up. For example:
`[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"
[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"`
-
Verify the nameservers record was added.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]To configure Private Service Edges to use internal NTP servers:
- Log in to the Private Service Edge console using your admin credentials.
-
Edit the `/etc/chrony.conf` file. Use an editor, such as vi.
`[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf`
Add your internal NTP servers to the list. For example:
`server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst`
-
To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the Private Service Edge to work through that proxy. The following procedure allows the Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the Private Service Edge to work through an explicit proxy:
- Log in to the Private Service Edge console using your admin credentials.
-
Create a file named, /opt/zscaler/var/service-edge/proxy. Use an editor, such as vi.
`[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy`
Enter the proxy information using the following format: `<Proxy Hostname or IP Address>``:``<Proxy Port>` (e.g., `192.0.2.0:0`).
-
To apply the changes, restart the Private Service Edge using the following command:
`[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edgeThe Private Service Edge will attempt to create a TLS session through the proxy specified in step 2.`
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation. To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](https://help.zscaler.com/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
[]For AWS, you must deploy Private Service Edges in your Virtual Private Clouds (VPCs). For each VPC there should be a pair of Private Service Edges deployed for resilience and scalability. The Private Service Edges should be deployed across Availability Zones to ensure continuity of service in the event of an incident. Zscaler automatically load balances across the Private Service Edges. Additional capacity can be handled by adding additional Private Service Edges into each Availability Zone.
Private Service Edges should be in appropriate Security Groups to accept incoming connections from Zscaler Client Connector and App Connectors. The Private Service Edges' Security Group should permit inbound and outbound access on port 443. The security group should allow inbound SSH to the AWS EC2 instance.
- [Deploying a Private Service Edge using the Instance Wizard](#wizard)
- [Deploying a Private Service Edge using a Launch Template with Auto Scaling (Advanced Deployment)](#launchtemplate)
[]This procedure describes how you can deploy in AWS using the Instance wizard. If you require a more scalable solution, Zscaler recommends deploying the Private Service Edge using a Launch Template with Auto Scaling.
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances. It is also assumed that you already have a Security Group created and have edit access to it.
To deploy a Private Service Edge on AWS using the Instance wizard:
- Log in to the AWS Management Console.
- Click **EC2**.
- On the **EC2 Dashboard** page, under the **Create Instance** section, click **Launch Instance**. Within the EC2 Management Console, the instance wizard appears.
- In **Step 1: Choose an Amazon Machine Image (AMI)**, under **Community AMIs**, search for `Private Service Edge`.
The Private Service Edge AMI is currently available under **Community AMIs** for regions **US West (Oregon) - us-west-2** and **US East (N. Virginia) us-east-1**. If you require an AMI in another region, you can request this through Zscaler Support.
Alternatively, you can deploy Private Service Edge on a [CentOS 7.x instance](/unified/private-service-edge-deployment-guide-linux), using one of the deployment options in step 3. Make sure the CentOS 7.x meets the requirements in the [prerequisites](/unified/private-service-edge-deployment-prerequisites).
- When the **Zscaler Private Access Service Edge** AMI appears, click **Select**.
- In **Step 2: Choose an Instance Type**, select an instance type that supports the Private Service Edge's [sizing requirements](/unified/private-service-edge-deployment-guide-amazon-web-services#step1Prereqs).
- Click **Next: Configure Instance Details**.
- In **Step 3: Configure Instance Details**:
- Choose suitable values for your VPC.
- For **Auto-assign Public IP**, choose **Enable**.
- Click **Review and Launch**.
- In **Step 7: Review Instance Launch**, verify the instance configuration.
A Private Service Edge needs inbound and outbound access on TCP port 443, so ensure that the Security Group is configured accordingly.
- Click **Launch** to power on the instance.
- Verify that the instance launched successfully and that the **Instance State** is running.
- Click **Connect**.
In the **Connect To Your Instance** window that appears, take note of the private key name (i.e., a .pem file) and the public hostname or IP address for your instance. You will need this information for step 14 below.
If the proper columns are shown, you can also see this information within the table on the **Instances** page.
- Update the Security Group associated to the Private Service Edge to temporarily allow inbound access on port 22, then complete the following steps to connect to the instance. SSH access is required in order to configure the provisioning key for the Private Service Edge.
- [See instructions.](#securitygrp)
- Apply the Private Service Edge provisioning key.
- [See instructions.](#provisionkey1)
After the Private Service Edge provisioning key is applied, be sure to verify that the deployed Private Service Edge is [running and healthy](/unified/managing-deployed-private-service-edges-private-applications#Status).
- Zscaler highly recommends updating the host OS software before proceeding.
- []Log in to the Private Service Edge console using your admin credentials.
After the initial boot of a Private Service Edge instance, it might take up to 15 minutes for the admin credentials to apply. So, if you receive an invalid credentials error after initial boot, wait a few minutes and try again.
- Using a standard SSH client, enter the following command to connect to the AWS instance: ssh -iadmin@ In the following example, the private key for the AWS instance is AWS.pem and the ZPA Private Service Edge IP address is 35.160.130.25: ssh -i AWS.pem admin@35.160.130.25
- When you are asked if you want to continue connecting, enter `yes`.
- []Stop the running the zpa-service-edge service. If the provisioning key is not detected when the Private Service Edge first started, then the Private Service Edge is in a sleep cycle and looks for the key again every 24 hours.
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/service-edge/provision_key. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa--service-edge service.
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
In AWS, be sure to disable inbound access on port 22 for the Security Group associated with the Private Service Edge.
[]This procedure describes how you can deploy Private Applications in AWS through Launch Templates and Auto Scaling configurations in order to create a scalable and supportable infrastructure.
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances.
To deploy a Private Service Edge on AWS using a Launch Template with Auto Scaling:
- Log in to the AWS Management Console.
- Click **EC2**.
- From the menu on the right, under **Network & Security**, click **Security Groups**.
- Click **Create Security Group**.
The **Create Security Group** window appears.
- In the **Create Security Group** window:
- Enter a **Security group **name.
- Enter a **Description**.
- Select the proper **VPC** from the drop-down menu.
- On the **Outbound** tab, allow access to 0.0.0.0/0 on all ports.
If necessary, outbound access can be restricted to hosts and ports. For details regarding required IPs, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
- On the **Inbound** tab, allow access to the public IP address on port 443.
- Click **Create**.
- The new group appears in the **Security Groups** page. From the menu on the right, under **Instances**, click **Launch Templates**.
- Click **Create launch template**.
Within the EC2 Management Console, the **Create launch template** page appears.
- Create a launch template in the **Create launch template** page
- [See Instructions.](#createtemplate)
- On the confirmation page that appears, click **Create Auto Scaling Group**.
Within the EC2 Management Console, the **Create Auto Scaling Group** wizard appears.
- In **Step 1: Configure Auto Scaling group details**, the **Launch Template** you created previously is automatically selected:
- Enter a **Group name**.
- Set the **Group size** to **Start with** `2` **instances**.
- Select a **Subnet** from the drop-down menu. This is where your Private Service Edges are deployed. As stated previously, for each VPC there should be a pair of Private Service Edges deployed for resilience and scalability. So make sure that you select 2 subnets from the drop-down menu.
- Click **Next: Configure scaling policies**.
- In **Step 2: Configure scaling policies**:
- Select **Use scaling policies to adjust the capacity of this group**.
- Enter the minimum and maximum size for the scale between instances.
- Enter a **Name** for the group.
- From the **Metric type** drop-down menu, select **Average CPU Utilization**.
- Enter a **Target value **of 50.
Your scaling policy should start with the initial deployment of 2 Private Service Edges; each Private Service Edge is capable of passing 400-500 Mbps traffic. An additional Private Service Edge can be added once this limit is reached, which occurs once the Private Service Edge runs at about 50% CPU utilization. To learn more about Private Service Edge throughput, see [Private Service Edge Specifications and Sizing Requirements](#step1Prereqs).
- Click **Next: Configure Notifications**.
- In **Step 3: Configure Notifications**, set up your notifications as needed and click **Next: Configure Tags**. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ASGettingNotifications.html#as-configure-asg-for-sns).
- In **Step 4: Configure Tags**, set up your tags as needed and click Review. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-tagging.html).
- In **Step 5: Review**, verify your configuration settings and click **Create Auto Scaling group**.
After the Private Service Edges are initialized, they'll be provisioned into the Private Service Edge group you specified in the Admin Portal. The provisioning is based on the provisioning key included in the script you entered in the **User data** field for the Launch Template (step 8m. above) and Auto Scaling Group configuration.
- Zscaler highly recommends [updating the Private Service Edge system software](/unified/understanding-private-service-edge-software-upgrades-private-applications) before proceeding.
- []Make sure that **Create a new template** is selected.
- Enter a **Launch template name**.
- Enter a **Template version description**.
- Under the **Launch template contents** section, click **Search for AMI**.
- In the **Search for AMI** window that appears:
- From the **AMI catalog** menu, select **Community AMIs**.
- From the **AMI menu**, filter for `zpa-service-edge-2023.03` and select it from the list.
- For **Instance type**, select a type that supports the Private Service Edge's [sizing requirements](#step1Prereqs).
- Select the proper SSH **Key pair name** to deploy.
- For **Network type**, make sure **VPC** is selected.
- From the **Security Groups** drop-down menu, select the group you created in step 5 above.
- (Optional) You can customize your **Network interfaces**, if necessary. However, the default settings are adequate for deployment.
- (Optional) You can add **Tags** to the launch template, if necessary. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html).
- Expand the **Advanced details** section.
- Within the **User data** field enter the following script:
#!/bin/bash
#Stop the Service Edge service which was auto-started at boot time
systemctl stop zpa-service-edge
#Create a file from the Service Edge provisioning key created in the Admin Portal
#Make sure that the provisioning key is between double quotes
echo "<Service Edge Provisioning Key>" > /opt/zscaler/var/service-edge/provision_key
#Run a yum update to apply the latest patches
yum update -y
#Start the Service Edge service to enrol[l it in the](#!/bin/bash) cloud
systemctl start zpa-service-edge
#Wait for the Service Edge to download latest build
sleep 60
#Stop and then start the Service Edge for the latest build
systemctl stop zpa-service-edge
systemctl start zpa-service-edge
In the `echo` statement above, make sure that you have included the Private Service Edge provisioning key you copied from the Admin Portal, for example:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
echo
"1|api.private.zscaler.com|IhQ9C+gJG+x1AFcO3XGlrMW1SDkIuuyRsNwfB4B+cDc2RNNPePNGuI26N/zZJ08ZjaGW5EKiIQ28rfE9TobevoQAt192+CcUgiKUCtGO7w5+2MeOmhiOTjB+Ox/PlWEoJSqqZFKR5EdNDZr+zd2/gYXTNAn8oG+BDT7NMV7YocvcnvBZG6DfOImAwtSlOSY45tJprEtoCSpT+SCsijyPCuv61QdqObIJcnA5Cs8jo6LjSqqlVYkBYgTEJgZdNKHlMkV5lxk/Ayh43A4hGLCnY+InMTj0sF7US8/NZlR/2mdAbAbmf+1ujDr/k1YgC9QQX3alr7qpHIFO/HxvyutzIu9+QXqkdCA6tL8o+RQiFrDJ7YTiQ/HxlVPlN0tKyw2K" > /opt/zscaler/var/service-edge/provision_key For all other fields within this section, the default settings are adequate for deployment.
- Click **Create launch template**.