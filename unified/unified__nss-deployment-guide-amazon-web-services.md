# NSS Deployment Guide for Amazon Web Services
Source: https://help.zscaler.com/unified/nss-deployment-guide-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1496671.pdf

Zscaler's [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service) can be deployed via Amazon Web Services (AWS). This guide describes the tasks required for NSS deployment, enabling you to stream either web logs or Firewall logs to a security information and event management (SIEM) system.
As shown in the following diagram, the web and mobile traffic logs and the Firewall logs are stored in the Nanolog in the Zscaler cloud. An organization can deploy the NSS instance on an EC2 instance on AWS. When an organization deploys one NSS for web and mobile logs and another NSS for Firewall logs, each NSS opens a secure tunnel to the Nanolog in the Zscaler cloud. The Nanolog then streams copies of the logs to each NSS in a highly compressed format to reduce bandwidth footprint; the original logs are retained in the Nanolog.
![Diagram of copies of web and mobile logs and firewall logs being streamed to each NSS in a compressed format through AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/diagram_zia_nss_aws-deployment_v2.png)
Prerequisites
Ensure you have a [subscription](/unified/viewing-subscriptions) to either NSS for Web or NSS for Firewall and review the following specifications and requirements:
- [VM Specs](#vm-specs)
- [Network Specs](#network-specs)
- [Firewall Requirements](#firewall-requirements)
Deploying NSS
To deploy NSS:
- [Step 1: In the Admin Portal, Add an NSS Server and Download the SSL Certificate](#step-add-nss-server-download-ssl-certificate)
- [Step 2: In the Admin Portal, Compute the Recommended VM Instance Specifications](#step-get-recommended-vm-specs)
- [Step 3: In the AWS Management Console, Provision and Configure an EC2 Instance](#step-provision-configure-ec2-instance)
- [Step 4: Configure and Start the NSS on the VM Instance](#step-configure-start-nss)
- [Step 5: In the Admin Portal, Add NSS Feeds](#step-add-nss-feeds)
Post-Deployment Tasks
After you have verified your deployment, you can perform additional tasks:
- [Troubleshooting Deployed NSS Servers](#Troubleshooting)
- [Configuring Advanced NSS Settings](#Networking)
- [Deploying Multiple NSS Virtual Machines for Reliability](#deploying)
- []EC2 instance type: One of the following dual-core instances. NSS uses one core for the control plane and another core for the data plane:
- t2.large
- t2.xlarge
- t2.2xlarge
- m4.large
- m4.4xlarge
- r4.large
- r4.xlarge
- r4.4xlarge
- c4.8xlarge
- Instance memory:
- 8 GB for up to 15K users
- 16 GB for up to 40K users
- 32 GB for up to 100K users
- EBS storage volume type: Magnetic is sufficient, but General Purpose SSD is recommended.
- Data disk size: 500 GB
To learn more, see [Compute the Recommended VM Instance Specifications](/unified/nss-deployment-guide-amazon-web-services#step-get-recommended-vm-specs).
-
[]Two network interfaces:
- The first network interface is the management IP address. It is used for control connections to the Zscaler cloud and to make an SSH connection to the NSS VM for configuration and management. You can customize the deployment and define a separate IP address for the SSH connection to the NSS VM.
- The second network interface is the service IP address. It is used for data connections to the Zscaler cloud and to the SIEM.
Second management or service network interfaces are currently not supported in the NSS over AWS deployment.
- Two Elastic IPs to assign a public IP address with both network interfaces. The two elastic IPs are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
- Bandwidth for log download: 11 Mbps for 10K users is an example average value.
[]It is mandatory to deploy the NSS instance behind a VM network security group. The NSS instance requires only outbound connections to the Zscaler cloud. It doesn't require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, refer to the Zscaler Cloud Configuration Requirements for your Zscaler cloud: https://config.zscaler.com/<Zscaler Cloud Name>/nss.
You can find the name of your Zscaler cloud in the URL you use to log in to the Zscaler service. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/nss](https://config.zscaler.com/zscaler.net/nss).
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
Communication from the NSS to the Zscaler cloud must be excluded from SSL inspection to ensure that the NSS can authenticate to the Nanolog cluster using mutual TLS.
Zscaler does not recommend or support forwarding outbound traffic from the NSS to or through the Internet & SaaS Public Service Edge as this can result in networking, latency, and administration issues.
[]
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
From the **NSS Servers **tab, click **Add NSS Server**.
The **Add NSS Server** window appears.
-
In the **Add NSS Server **window:
- **Name**: Enter a name for the NSS.
-
**Type**: The **NSS for Web **type is selected by default. To configure NSS for Firewall logs, select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **Status**: The NSS is **Enabled** by default.
[See image.](#add_nss_server)
- Click **Save**.
-
Click **Download** in the **SSL Certificate** column of your newly added NSS server and save the certificate for later [configuring the NSS virtual appliance on AWS](/unified/nss-deployment-guide-amazon-web-services#step-configure-start-nss).
[See image.](#ssl_cert_download)
[]![The Add NSS Server window in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia-nss-server-web.png)
[]![The NSS Servers tab in the ZIA Admin Portal. The Download button under the SSL Certificate column is highlighted.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia-nss-server-web-ssl-certificate.png)
[]You must enter information about your traffic and users so that the Zscaler service can compute the appropriate resources for your NSS.
The NSS buffers the logs for at least one hour. If a SIEM goes offline for maintenance or if the connection between the NSS and the SIEM is disrupted, the NSS buffers the logs and sends them once the connection is re-established. The amount of memory required to buffer the logs is incorporated into the VM spec computation. The buffer size increases proportionally to the amount of RAM allocated to the NSS.
To compute the appropriate resources for your NSS:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
Click **Deploy NSS Virtual Appliance** to enter data that the Zscaler service needs to compute the appropriate resources for your NSS.
The **NSS Virtual Appliance Deployment** window appears.
-
In the **NSS Virtual Appliance Deployment **window, choose either of the following NSS types:
- [NSS for Web](#nss_web)
- [NSS for Firewall](#nss_fw)
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- For the platform, select **Amazon Web Services**.
- Click **Compute**.
The recommended EC2 instance type is listed. You use this information when later [setting up the EC2 instance](#launch-ec2-instance). You can click the **Configuration Info** links for more information on AWS and how to set up an EC2 instance.
[See image.](#ec2_instance_type_img)
See the following table for AWS EC2 instance specifications:
| Instance Type | Memory | Cores |
| ------------- | ------ | ----- |
| t2.large | 8 GB | 2 |
| t2.xlarge | 16 GB | 4 |
| t2.2xlarge | 32 GB | 8 |
| m4.large | 8 GB | 2 |
| m4.4xlarge | 64 GB | 16 |
| r4.large | 15.25 GB | 2 |
| r4.xlarge | 30.5 GB | 4 |
| r4.4xlarge | 122 GB | 16 |
| c4.8xlarge | 60 GB | 36 |
- Click **Close**.
[]![Recommended EC2 instance type and configuration info in the NSS Virtual Appliance Deployment window in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia-nss-compute-ec2-instance-type-web.png)
[]To determine the memory and bandwidth requirements:
- **Number of Users**:** **Enter the number of users. The service displays the recommended resources for NSS and the EC2 instance.
- **Peak Transactions per Hour**: The peak number of transactions in an hour. You can retrieve this data by going to **Internet & SaaS** > **Dashboard **> **Web Overview**. This is recommended to adjust the VM specification to your organization’s workload.
[See image.](#nss_web_img)
The recommended internet bandwidth is the peak bandwidth required to download the logs from the Nanolog in the Zscaler cloud. If NSS is not allocated the bandwidth it needs, the logs can accumulate in the Nanolog. This can result in frequent connection resets, and the logs are not streamed to NSS.
[]![The NSS Virtual Appliance Deployment window with NSS for Web selected. The platform is AWS.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia-nss-virtual-appliance-deployment-web.png)
[]To determine the memory and bandwidth requirements:
- **Number of Users**:** **Enter the number of users. The service displays the recommended resources for NSS and the EC2 instance.
- **Peak Sessions Per Hour**:** **The peak number of sessions and DNS requests in an hour. You can retrieve this data by going to **Internet & SaaS** > **Dashboard** > **Firewall Overview**. This is recommended to adjust the VM specification to your organization’s workload.
- **Peak DNS Requests Per Hour**: You can retrieve this data by going to **Internet & SaaS** > **Dashboard** > **DNS Overview**. This is recommended to adjust the VM specification to your organization’s workload.
[See image.](#nss_fw_img)
The recommended internet bandwidth is the peak bandwidth required to download the logs from the Nanolog in the Zscaler cloud. If NSS is not allocated the bandwidth it needs, the logs can accumulate in the Nanolog. This can result in frequent connection resets and the logs are not streamed to NSS.
[]![The NSS Virtual Appliance Deployment window with NSS for Firewall selected. The platform is AWS.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/zia-nss-virtual-appliance-deployment-fw.png)
[]Use the following procedure to launch a new EC2 instance with an NSS AMI, configure two network interfaces with Elastic IPs, and configure the required security group settings:
-
[]In AWS, in the top-right corner of the screen, select the region where you want to launch the instance.
[See image.](#img-aws-region)
- Create a security group:
- Go to **EC2**.
- In the left-side navigation, go to **Network & Security** > **Security Groups**.
-
[]Click **Create security group**.
The **Create security group** page appears.
-
In the **Basic details** section:
-
**Security group name**: Enter a name for the security group (e.g., `Zscaler NSS`).
You later assign this security group to the two network interfaces that you create when [launching an EC2 instance](#launch-ec2-instance).
- **Description**: Enter a description of the security group.
- **VPC**: The virtual private cloud (VPC) of the security group
[See image.](#img-aws-create-security-group)
-
In the **Inbound rules** section, click **Add rule** and configure the connection requirements.
[See image.](#img-aws-inbound-rules)
To connect to your EC2 instance via SSH, you are required to open port 22 for inbound connections. In production, you should authorize only a specific IP address or range of addresses to access your instance and not use 0.0.0.0. To learn more, refer to the [AWS documentation](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html).
-
In the **Outbound rules** section, click **Add rule **and configure the connection requirements.
[See image.](#img-aws-outbound-rules)
The inbound and outbound rules are required to enable the NSS AMI to communicate with the Zscaler cloud and Nanolog and enable remote control of the instance via SSH. To learn more about the outbound connection requirements, refer to https://config.zscaler.com/<Zscaler Cloud Name>/nss. The <Zscaler Cloud Name> can be found in the URL that you use to log in to the Admin Portal. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/nss.](https://config.zscaler.com/zscaler.net/nss.)
- Click **Create security group**.
- []Launch an EC2 instance:
- Go to **EC2** > **Instances**.
-
Click **Launch instances**.
The **Launch an instance **page appears.
- In the **Name and tags** section, enter a name for the instance.
- In the **Application and OS Images (Amazon Machine Image)** section:
-
Click **Browse more AMIs**.
[See image.](#img-aws-browse-more-amis)
The **Choose an Amazon Machine Image (AMI)** page appears.
- Enter `zsos42` in the search bar and press `Enter`.
- Select **AWS Marketplace AMIs**.
-
Click **Select** next to **Zscaler NSS (ZSOS42) AMI** in the results.
[See image.](#img-aws-zscaler-nss-ami)
-
Click **Subscribe now **when prompted.
You are redirected to the **Application and OS Images (Amazon Machine Image)** section, which shows that the AMI is verified.
[See image.](#img-aws-verified-provider)
-
In the **Instance type** section, select the recommended EC2 instance type [previously computed](/unified/nss-deployment-guide-amazon-web-services#step-get-recommended-vm-specs) in the Admin Portal.
[See image.](#img-aws-instance-type)
Zscaler’s EC2 instance type recommendation is based on the expected number of transactions, users, and the most economical option for the customer. If you are unable to select the recommended type, contact Zscaler Support.
- []In the **Key pair (login)** section, select or create a key pair. Creating a key pair generates a PEM file that you later use to [log in to the VM instance](/unified/nss-deployment-guide-amazon-web-services#remotelogin) via SSH. To create a key pair:
-
Click **Create new key pair**.
The **Create key pair** window appears.
-
In the **Create key pair** window:
- **Key pair name**: Enter a name for the key pair.
- **Key pair type**: Select **RSA**.
- **Private key file format**: Select **.pem**.
[See image.](#img-aws-key-pair)
-
Click **Create key pair**.
The PEM file is automatically downloaded.
- In the **Network Settings** section, click **Edit** and configure the following fields:
- **Subnet**: Select the subnet of the instance.
-
**Auto-assign public IP**: Ensure that this setting is disabled.
Auto-assign IP can only be assigned to instances with one network interface; NSS requires two network interfaces.
-
**Firewall (security groups)**: Click **Select existing security group** and select the security group that you [previously created](#create-security-group) (e.g., Zscaler NSS).
[See image.](#img-aws-network-settings)
- In the **Advanced network configuration** subsection:
-
**Network interface 1**: Leave all fields in their default settings, and then click **Add network interface**.
[See image.](#img-aws-network-interface-1)
-
**Network interface 2**: Ensure that the second network interface is in the same subnet as the first network interface. Otherwise, leave all fields in their default settings.
[See image.](#img-aws-network-interface-2)
By default, the EC2 instance has one network interface (eth0), but NSS requires an additional interface (eth1) in the same subnet. The management interface (eth0) is used for control connections to the Zscaler cloud and to make an SSH connection to the NSS for configuration and management. The service interface (eth1) is used for data connections to the Zscaler cloud (streaming nanologs) and to the SIEM (syslog feed).
-
In the **Configure storage** section, select the storage specifications [previously computed](/unified/nss-deployment-guide-amazon-web-services#step-get-recommended-vm-specs) in the Admin Portal. **General purpose SSD (gp3)** is recommended, but **Magnetic (standard)** is sufficient.
[See image.](#img-aws-configure-storage)
-
Review your EC2 instance configuration, and then click **Launch instance**.
After the instance launches, a success message appears with the instance ID link.
[See image.](#img-aws-instance-launch-success)
-
Click the instance ID link.
You are redirected to the **Instances** page.
-
On the **Instances** page, click the **Instance ID** of the instance.
[See image.](#img-aws-instance-id)
-
Scroll down and click the **Networking** tab.
[See image.](#img-aws-networking-tab)
-
[]In the **Network Interfaces** section, copy and save the interface IDs of the two network interfaces created for the instance. You use the IDs when [associating Elastic IPs](#allocate-associate-elastic-ips) to the network interfaces.
[See image.](#img-aws-interface-id-copied)
The first network interface is the management interface (eth0). The second network interface is the service interface (eth1).
- []Allocate and associate two Elastic IPs:
- Go to **Network & Security** > **Elastic IPs**.
-
Click **Allocate Elastic IP address**.
The **Allocate Elastic IP address** page appears.
-
Ensure the **Network border group** is in the same region you [previously selected](#select-region), and then click **Allocate**.
[See image.](#img-aws-allocate-elastic-ip)
You are redirected to the **Elastic IP addresses** page, and a success message appears.
-
Click the newly allocated Elastic IP address.
[See image.](#img-aws-allocate-elastic-ip-success)
[]This is the public IP address of the management interface. You later use this IP address to [log in to the VM instance](/unified/nss-deployment-guide-amazon-web-services#remotelogin).
-
Click **Associate Elastic IP address**.
[See image.](#img-aws-associate-elastic-ip)
The **Associate Elastic IP address** page appears.
- On the **Associate Elastic IP** **address** page:
- **Resource type**: Select **Network interface**.
- **Network interface**: Enter the interface ID of the first (i.e., management) network interface that you [previously copied and saved](#copy-interface-ids).
-
**Private IP address**: Select the private IP address of the network interface that automatically populates in the field.
[See image.](#img-aws-elastic-ip-config)
- Click **Associate**.
After the Elastic IP address is associated, a success message appears.
-
Go to your EC2 instance page (**EC2** > **Instances**) to verify that the Elastic IP address is allocated.
[See image.](#img-aws-verify-elastic-ip)
- Repeat the [entire procedure](#allocate-associate-elastic-ips) to allocate and associate a second Elastic IP address to the second (i.e., service) interface.
[]![Region drop-down menu in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-region.png)
[]![Create security group page with Basic details configured in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-create-security-group.png)
[]![Inbound rules configured for a security group in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-inbound-rules.png)
[]
![Outbound rules configured for a security group in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-outbound-rules.png)
[]![Browse more AMIs in AWS. An AMI is a template that contains the software configuration required to launch an EC2 instance. ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-browse-more-amis.png)
[]
![The Zscaler NSS (ZSOS42) AMI selected in AWS ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-zscaler-nss-ami.png)
[]
![The Zscaler NSS (ZSOS42) AMI is from a verified provider](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-verified-provider.png)
[]![m4.large is one of several recommended instance types for deploying NSS over AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-instance-type.png)
[]
![Key pairs generate a .pem file for download that is used for securely login purposes](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-key-pair.png)
[]
![The Network settings configuration in AWS for deploying NSS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-network-settings.png)
[]
![The Advanced network configuration of Network interface 1 of an EC2 instance in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-network-interface-1.png)
[]
![Network interface 2 of an EC2 instance in AWS. Deploying NSS requires two network interfaces in the same subnet](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-network-interface-2.png)
[]
![General purpose SSD is the recommended storage specification for NSS over AWS deployment](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-configure-storage.png)
[]
![The launch of an instance in AWS is successfully initiated](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-instance-launch-success.png)
[]
![The Instance ID of a launched EC2 instance in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-instance-id.png)
[]
![The Networking tab has details on an instance and its network interfaces ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-networking-tab.png)
[]
![Copy the interface ID of the network interfaces of an EC2 instance](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-interface-id-copied.png)
[]![Allocate an Elastic IP address to an EC2 instance in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-allocate-elastic-ip-address.png)
[]
![After allocating an Elastic IP address, it can be associated to a network interface](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-elastic-ip-address-allocate-success.png)
[]
![The Associate Elastic IP address button in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-associate-elastic-ip-address.png)
[]![The Associate Elastic IP address configuration for an allocated Elastic IP address in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-associate-elastic-ip-address-config.png)
[]
![The Instance summary shows an allocated and associated Elastic IP address](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-verify-elastic-ip-address.png)
[]The following NSS configuration procedure runs through an SSH terminal connection. You use the PEM file that you [previously downloaded](/unified/nss-deployment-guide-amazon-web-services#create-key-pair-pem-file) to log in to the VM instance.
Before you start:
- Ensure you have completed the [provisioning and configuration of an EC2 instance](/unified/nss-deployment-guide-amazon-web-services#step-provision-configure-ec2-instance).
- []Note the private IP address and subnet mask of the service network interface (eth1) that you created for the EC2 instance:
- In AWS, go to **EC2**.
- In the left-side navigation, go to **Instances**.
-
Select your newly launched EC2 instance, and then scroll down and click the **Networking** tab.
[See image.](#img-aws-ec2-instance-networking-tab)
-
In the **Network Interfaces** section, copy the **Private IPv4 address **of the** **second (i.e.,** **service - eth1) network interface and save for [configuring the NSS network settings](/unified/nss-deployment-guide-amazon-web-services#confignss).
[See image.](#img-aws-ec2-instance-network-interface-private-IP)
-
In the **Networking details** section, click the **Subnet ID** link.
[See image.](#img-aws-ec2-instance-network-interface-subnet-id)
The **Subnets **page appears.
-
On the **Subnets** page, select the subnet and note the subnet mask (e.g., /24) in the** IPv4 CIDR** column.
[See image.](#img-aws-ec2-instance-network-interface-subnet-mask)
Configuring the NSS Virtual Appliance on AWS
To configure the NSS virtual appliance on the VM:
- [a. Copy the SSL certificate.](#copysslcert)
- [b. Remote log in to the VM instance.](#remotelogin)
- [c. Install the SSL certificate.](#installsslcert)
- [d. Configure the NSS network settings.](#confignss)
- [e. Download the NSS binaries.](#download)
- [f. Start the NSS.](#start)
- [g. Verify the configuration.](#verifyconfig)
- []Using FTP, SCP, or SFTP, copy the SSL certificate file that you [previously downloaded](/unified/nss-deployment-guide-amazon-web-services#step-add-nss-server-download-ssl-certificate) from the Admin Portal to the VM.
- Find the public hostname or [IP address](#public-ip-address-management-interface) of your instance in the VM.
[]Use the following SSH command with your [previously downloaded](#create-key-pair-pem-file) PEM file and [public IP address](#public-ip-address-management-interface) of your instance to get shell access to the VM.
ssh -i <key-pair-name>.pem zsroot@<instance-public-IP-address>
The following is an example:
ssh -i nss-zscaler.pem zsroot@44.239.205.223
[]NSS uses an SSL certificate to authenticate itself to the Zscaler service. Make sure that the SSL certificate is installed on only one active NSS VM at a time. Having multiple NSS VMs that use only one certificate causes cloud connection flapping, which disrupts the streaming of logs to the NSS.
- Copy the `NssCertificate.zip` file to the `/home/zsroot` root directory.
- Run the following command:
sudo nss install-cert NssCertificate.zip
- Check the configuration by running the following command**:**
sudo nss dump-config
-
[]Enter the command `netstat -rn` and note the default gateway IP address. For example:
| Destination | Gateway |
| ----------- | ------- |
| Default | 172.31.16.1 |
| 127.0.0.1 | link#1 |
| 172.31.16.0/20 | link#3 |
| 172.31.30.202 | link#3 |
The first network interface (i.e., management - eth0) is configured by default when you start the VM.
- Configure the NSS network (i.e., the service interface - eth1 only) by running the command `sudo nss configure` and completing the following IP configurations:
- Enter a name server (e.g., 172.31.0.2). You can change (`C`), delete (`D`), or not change it (`N`). In this case, enter `N`.
- You can optionally add a name server. In this case, enter `N`.
- Enter the service interface IP address with the subnet mask (smnet_dev). This is the private IP address and subnet mask of the second network interface (i.e., service interface - eth1) that you [previously noted](#private-ip-service-interface) in AWS.
- Enter the service interface default gateway IP address (smnet_dflt_gw). This is the default gateway IP address (e.g., 172.31.16.1) that you noted previously after running the command `netstat -rn`.
[]![The Networking tab of an EC2 instance in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/service_interface_aws_instance_networking_tab.png)
[]![Private IPv4 address of service interface in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/aws-service-interface-private-ip.png)
[]![The subnet ID link for the service interface in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/service_interface_aws_instance_subnet_ID_0.png)
[]![The subnet mask of the service interface in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-amazon-web-services/service_interface_aws_instance_subnet_mask.png)
[]Before starting the NSS, run the following command** **to download and install the NSS binaries:
sudo nss update-now
After the first NSS software deployment, the software is automatically updated with new versions.
[]Unless you are planning to use this instance for passive backup, run the command `sudo nss start` and ensure that the command shows that the NSS virtual appliance started successfully. It can take a few minutes for the NSS to start streaming logs to the SIEM.
After starting the NSS for the first time, you can run the following command to check that the latest NSS software version is installed:
sudo nss checkversion
To enable the NSS to start automatically after a restart, run the following command:
sudo nss enable-autostart
You can also explore other options by running the following command:
sudo nss help
[]To verify the configuration, run the following command:
sudo nss troubleshoot netstat|grep tcp
When the output of the command is displayed, verify that the following TCP connections are established in the following order:
- `Connection to the Zscaler cloud on port 443`: This is the control connection that is used to authenticate NSS to the Zscaler Central Authority (CA) and to download the configuration. It's also the data connection to the Nanolog so it can stream the logs.
- `Connection to the SIEM`: This is the long-lived TCP connection to the SIEM on the specified log data port. If there are multiple feeds configured, multiple connections must be listed.
The absence of any one of the preceding connections, even after waiting a few minutes, usually indicates that there is a firewall configuration issue and the logs cannot be streamed. To troubleshoot issues, see [Troubleshooting Deployed NSS Servers](/unified/troubleshooting-deployed-nss-servers).
[]An NSS feed specifies the data from the logs that the NSS sends to the SIEM. You can filter the data so that you send only the data you need to the SIEM. You can add up to 16 NSS feeds for each NSS server. ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS server to ensure optimal performance.) Each feed can have different filters and fields, and a different output format (e.g., CSV). To learn more about how to configure each feed, see [Adding NSS Feeds](/unified/adding-nss-feeds).
[]An [NSS server](/unified/adding-nss-servers) represents the NSS virtual machine (VM) in the Admin Portal. When you create an NSS server in the portal, an SSL certificate is generated. You download the SSL certificate from the portal and upload it to the NSS VM that you configure and [deploy](/unified/deploying-nss-virtual-appliances). The newly configured NSS VM uses the SSL certificate to authenticate itself to the Zscaler service.
Each NSS server supports up to 16 [NSS feeds](/unified/adding-nss-feeds). ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS to ensure optimal performance.) Each NSS feed can have different filters and fields and a different output format (e.g., CSV).
For site reliability, you can deploy multiple NSS VMs, either in an active-active or active-passive configuration.
Active-Active Configuration
Zscaler recommends leveraging two NSS servers per NSS type (i.e., NSS for Web and NSS for Firewall) and deploying each pair in an active-active configuration. In this configuration, you create two NSS servers of the same NSS type in the Admin Portal with separate SSL certificates.
Running multiple active NSS VMs with the same SSL certificate causes cloud connection flapping, which disrupts the streaming of logs to the NSS.
Optionally, for optimal reliability, you can configure the NSS VMs to stream logs to two separate SIEMs. In this configuration, each NSS VM runs independently, streaming logs to its respective SIEM at the same time.
Zscaler does not recommend configuring two NSS VMs of the same NSS type to stream logs to a single SIEM. In this case, each NSS VM sends copies of the same logs to the SIEM, which might not be able to deduplicate them.
Active-Passive Configuration
Alternatively, you can deploy multiple NSS VMs in an active-passive configuration. In this configuration, you create one NSS server (for Web or Firewall) in the Admin Portal and use the generated SSL certificate to deploy one active NSS VM; the second VM serves as a cold standby. Both NSS VMs use the same SSL certificate in this configuration, but they should not connect to the Zscaler Nanolog at the same time as this results in connection flapping.
If the active NSS VM fails, you must perform failover activities, ideally within one hour of the failure to prevent data loss. In this time frame, you can leverage the following NSS reliability mechanisms:
- **NSS to SIEM**: The NSS buffers the logs in the VM memory to increase its resiliency to transient network issues between the SIEM and the NSS. If the connection drops, the NSS replays logs from the buffer, according to the Duplicate Logs setting.
- **Nanolog to SIEM**: If the connectivity between the Zscaler cloud and the NSS is interrupted, the NSS misses logs that arrived at the Nanolog cluster during the interruption, and they are not delivered to the SIEM. When the connection is restored, the NSS one-hour recovery allows the Nanolog to replay logs up to one hour back.
To learn more about NSS for Web, NSS for Firewall, and NSS Log Recovery subscriptions, contact Zscaler Support.
[]
This article describes additional features that facilitate deploying the NSS in cases where you have specific requirements or restrictions. It includes the following topics:
- [Configuring a Second Management Interface](#Management)
- [Configuring a Second Service Interface](#Service)
- [Configuring the Additional Interfaces from the Console](#Additional)
- [Configuring a Local NTP Server](#Local)
- [Configuring NSS in Explicit Proxy Mode](#proxy)
- [Updating an NSS VM Hostname](#update_hostname)
- [Allowing SSH Access to the NSS Only from a Specific Subnet or IP](#allowing)
- [Setting Up Key-Based Authentication to the NSS](#key_based_auth)
[]Sometimes, the default management interface can't be used for SSH due to VLAN restrictions. In those cases, Zscaler recommends that you add an additional interface just for management, so the first interface is used only for control connections to the cloud.
There are two ways to add a second management interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/unified/configuring-advanced-nss-settings#Additional).
- [Alternatively, you can manually configure the second management interface.](#second-management-manual)
[]To manually add a management interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Update the system configuration file `/etc/rc.conf` to configure the interface automatically after each system restart. To do this, run the following command:
sudo vi /etc/rc.conf
- Add the em2 interface to the list of network interfaces. Modify the line that starts with `network_interfaces` and change it to:
network_interfaces="em0 em1 em2 lo0"
- Add a new line at the end of the file:
ifconfig_em2="<subnet-ip-address>"
Ensure that you replace <subnet-ip-address> with the IP address of the subnet. For example:
ifconfig_em2="192.168.1.100/24”
- The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN for the newly added em2 interface, add the following lines at the end of the file:
static_routes="em2"
route_em2="-net <destination-subnet> <gateway-ip-address>"
Replace <destination-subnet> with the IP address of the destination subnet, and replace <gateway-ip-address>** **with the appropriate gateway IP address. For example:
static_routes="em2"
route_em2="-net 198.51.100.0/24 192.168.1.3"
- Reboot the VM.
- To verify the changes, ping the newly added subnet gateway and run the following command to print the route information:
sudo netstat -rn
[]The NSS typically uses the service interface to download logs from the Nanolog in the Zscaler cloud and send them to the security information and event management (SIEM) system.
Some organizations might need to use one interface to connect to the Zscaler cloud and another interface to connect to the SIEM. For example, an organization might have a SIEM in a management LAN that is not routed to the internet, and it might also have a service LAN that is routed to the internet but not to the management LAN, as shown in the following diagram.
![Diagram of one interface connecting to the Zscaler cloud and another interface connecting to the SIEM. ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/mgmt_service_lan_siem_nss_diagram.png.png)
If your organization has a similar requirement, you can configure a second service interface. You can then use one interface to connect to the Zscaler cloud to download the logs and a different interface to send the logs to the SIEM located in the management LAN.
There are two ways to add a second service interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/unified/configuring-advanced-nss-settings#Additional).
- [Alternatively, you can manually configure the second service interface.](#second-service-manual)
[]To manually add a second service interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Copy the `sc.conf` file.
cp /sc/conf/sc.conf /sc/conf/sc.conf.old
- Use the vi Editor to edit the `sc.conf` file. Run the following command:
vi /sc/conf/sc.conf
- Add the following lines to the file, replacing the sample values in red per your configuration:
smnet_dev=em2=zs1:192.168.223.41/24
smnet_route=10.0.0.0/8/192.168.223.1
In this example, em2=zs1 is the second service interface and 192.168.223.41/24 is the service IP address with the subnet mask. If your SIEM is in the same subnet, then the second line is not required. If your SIEM is in a different subnet, add `smnet_route` and define values in the second line. For example, to reach 10.0.0.0/8, use gateway 192.168.223.1.
- Save the changes in the file and then restart the NSS by running the following command:
sudo nss restart
- Verify if the NSS is using the second service interface by running the following command:
sudo nss dump-config
[]To configure a second management interface and service interface, first ensure that you run the following** **command to set your network settings:
sudo nss configure
Then, run the following command to specify the IP addresses for the additional interfaces and their corresponding routes:
sudo nss configure split-interface
****![Screenshot of FreeBSD command prompt showing the command sudo nss configure split-interface](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/NSS%20sudo%20route%201.png)
****
During a split-interface configuration, the NSS asks for an `smnet_route`. If your SIEM is in a different network compared to the NSS smnet interface (em3=zs1) subnet, you can enter specific routes for feeds.
See the following example:
[root@NSS /sc/update]# nss configure split-interface
ifconfig_em2 (Internal Management interface IP address with netmask) [1.1.1.1/23]:
route_net:-net 1.1.1.2/12 2.1.1.1 (Options <c:change, d:delete, n:no change>) [n]
Do you wish to add a new route_net? <n:no y:yes> [n]:
smnet_dev=em3 (Internal Service interface IP address with netmask) [10.10.35.20/24]:
Do you wish to add a new smnet_route? <n:no y:yes> [n]: y
Atleast one entry required for smnet_route
smnet_route (Static route for Siem N/w ,e.g (network/subnet/gateway): 172.12.1.0/21/10.10.35.1) []: 1.3.2.1/2/2.2.1.2
Do you wish to add a new smnet_route? <n:no y:yes> [n]: 2.1.2.3/2/43.3.3.2
[]If you have a local NTP Server, you can configure the NSS to synchronize time with that server:
- Run the following as root:
crontab -e
- Add the following command:
PATH=/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/usr/games:/sc/update:/home/zsroot/bin:/sc/update
- Add the following command:
*/10 * * * * ntpdate <ntp-server-name>
Replace <ntp-server-name> with your local NTP server's FQDN or IP address.
- Save and exit.
The time synchronization command runs every 10 minutes. You can find logs for the NTP process in `/var/log/cron.`
[]Some customers might have a [no default route environment](/unified/implementing-zscaler-no-default-route-environments). This prevents the NSS from establishing connections to the Zscaler cloud. For this scenario, you can configure the NSS in explicit proxy mode, so that it tunnels all Zscaler cloud-bound connections through a proxy. These include [network connections](https://config.zscaler.com/zscaler.net/nss) and TCP connections from the NSS to the:
- Nanolog (SMSM)
- Zscaler Central Authority (CA) (SMCA)
- Update server (SMCDSS) for software updates
- Kafka server for audit log streaming
Connections from the NSS to the SIEM are not tunneled.
The NSS in explicit proxy mode can tunnel Zscaler cloud-bound connections. Based on your configuration, you can tunnel these connections without the need for internet-facing DNS resolution.
If you configure the `dnsoverproxy` flag to `1`, then the NSS in explicit proxy mode makes a CONNECT request to the following domains and the explicit proxy performs the name resolution:
- msmca.<cloudname> for the connection to the Zscaler CA
- zdistribute.<cloudname> for the connection to the update server
- kproxy.hdeu1.zdataservices.net for the connection to the Kafka server
If you configure the `dnsoverproxy` flag to `0`, then the NSS needs DNS resolution for the connections to the current master CA IP address, update server, and Kafka server.
NTP connections are not tunneled. The NSS needs DNS resolution for the NTP server. To learn more, see [Configuring a Local NTP Server](/unified/configuring-advanced-nss-settings#Local).
To configure the NSS in explicit proxy mode:
- Run the `nss configure` command to configure the two network interfaces.
- Run the `nss configure proxy` command. For example:
[root@NSS /usr/home/zsroot]# nss configure proxy
proxyserver (Proxy Host ) [10.81.153.26]:
proxyport (Proxy Port ) [443]:
dnsoverproxy (DNS over proxy: 0/1 ) []: 1
Successfully configured proxy
To undo this configuration, you can use `remove`:
nss configure proxy remove
-
Run the `sudo nss restart` command to restart the NSS service.
When the NSS starts, it tries to connect to the Zscaler CA or Nanolog using the proxy it configured.
-
Run the `nss troubleshoot netstat` command to verify the proxy (e.g., 10.81.153.26) connections for the Zscaler CA and Nanolog.
[See image.](#nss-explicit-proxy-mode-tcp-connections)
[]![Screenshot of established TCP connections to the Zscaler CA and Nanolog ](/downloads/tech-pubs-drafts/zia-draft-articles/draft-configuring-advanced-nss-settings-doc-51613/zia-nss-explicit-proxy-mode_0.png)
[]To update your NSS VM hostname:
- Log in to your NSS VM.
- Edit the file `/etc/rc.conf` using the vi Editor.
[zsroot@New_Hostname ~/$ vi /etc/rc.conf
- Add the hostname entry to the file.
hostname=<name>
- Run the `reboot` command.
root@New_Hostname:/usr/home/zsroot # reboot
- After the NSS restarts, your new hostname appears.
[]You can restrict SSH access based on IP/Subject using the following configuration in `sshd_config`:
AllowUsers zsroot@10.66.70.*
In this example, SSH is allowed only from the source IP range 10.66.70.0/24. Then, run the following** **command to make the configuration change effective:
service sshd restart
[]To set up key-based authentication to the NSS on ESX:
- Create a .ssh directory in the home directory:* *`/home/zsroot/` under the user` root`*.*
- Upload your user public key file to the file `authorized_keys` under the directory `/home/zsroot/.ssh.`
- Adjust the file `/etc/ssh/sshd_config` with the following updates. Make a backup of this file before changing it.
ChallengeResponseAuthentication no
PasswordAuthentication no
These entries are set to `yes` by default. You can set them to `no`** **or comment them out.
- Use the following command to restart the sshd service:
service sshd restart
Replace option `restart` with `stop` and `start` as required.
- Test the new configuration on the client side using SSH (e.g., PuTTY).
[]
You can use the following commands within the virtual machine (VM) console for your platform in order to configure and troubleshoot the NSS server. By default, root login is not permitted, so admins must use the `sudo` utility to run a command with higher privileges.
- To start the service:
sudo nss start
- To stop the service:
sudo nss stop
- To restart the service:
sudo nss restart
- To smoothly shut down the operating system:
sudo nss halt
- To change the network configuration (i.e., IP addresses, gateway information) for the service:
sudo nss configure
To learn more, see the [NSS deployment guide](/unified/deploying-nss-virtual-appliances) for your platform.
- To configure additional interfaces:
sudo nss configure split-interface
To learn more, see [Configuring the Additional Interfaces from the Console](/unified/configuring-advanced-nss-settings#Additional).
- To configure an explicit proxy:
sudo nss configure proxy
To learn more, see [Configuring NSS in Explicit Proxy Mode](/unified/configuring-advanced-nss-settings#proxy).
- If you configured additional interfaces using the `sudo nss configure split-interface` command and want to remove the configuration:
sudo nss configure split-interface --wipe
- To remove the network settings that were configured using the `sudo nss configure` command:
sudo nss configure --wipe
- To display the configuration file that was changed using the `sudo nss configure` command:
sudo nss dump-config
- To install NSS certificates from a specified certificate bundle file:
sudo nss install-cert <certificate bundle file>
- To check if a new NSS version is available:
sudo nss checkversion
- To manually update the NSS to the latest version:
sudo nss update-now
- To force the NSS to update, regardless of whether a new version is available:
sudo nss force-update-now
- To check the firewall configuration:
sudo nss test-firewall
This command does active firewall configuration probing by attempting to resolve the DNS names and establishing outbound connections to the Zscaler cloud. This command doesn't reset the management IP interface, so you can run it on an SSH connection.
- To view troubleshooting help command information:
sudo nss troubleshoot help
- To show the active connections on the service IP address:
sudo nss troubleshoot netstat
The output is similar to that of the netstat utility.
- To show the connections and their status:
sudo nss troubleshoot connection
This command probes the connection status over a period of time and indicates whether the connections are stable or flapping.
- To show the status of the NSS feeds:
sudo nss troubleshoot feeds
This command probes the status of the feeds and determines if the logs are queued due to the slow consumption of logs by the security information and event management (SIEM) system.
- To generate diagnostic information to send to Zscaler Support:
sudo nss collect-diagnostics
This command collects the configuration, vital statistics regarding the health of the NSS, and error statistics, and then downloads the data to a local file. This file can be emailed to Zscaler Support for troubleshooting purposes.
- To reset the network configuration:
sudo nss reset-network
- To change the SNMP admin user configuration:
sudo nss snmp-admin-configure
- To change the SNMP trap configuration:
sudo nss snmp-trap-configure
- To automatically start the NSS after reboot:
sudo nss enable-autostart
- To disable the automatic start of the NSS after reboot:
sudo nss disable-autostart
- To set up and enable MCAS:
sudo nss configure-mcas2
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. To learn more, see [Integrating with Microsoft Cloud App Security](/unified/integrating-microsoft-cloud-app-security) (MCAS).
- To disable MCAS:
sudo nss disable-mcas
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. You can re-enable MCAS by re-issuing the `sudo nss configure-mcas2` command.
Enabling Remote Access
An admin can request remote assistance and allow Zscaler Support to log in to their NSS server without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your NSS server:
sudo nss support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your NSS server.
- To disable Zscaler Support access to your NSS server:
sudo nss support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your NSS server:
sudo nss support-access-status
This checks the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your NSS server.
- To enable a remote debugging session:
sudo nss enable-remote-debugging
- To disable a remote debugging session:
sudo nss disable-remote-debugging
Error Codes
The following are error codes that you might encounter when executing an `sudo nss update-now` command:
| Error Code | Description |
| ---------- | ----------- |
| Error Code 96 | Invalid client certificate |
| Error Code 97 | Timeout occurred while contacting upgrade server |
| Error Code 99 | A problem occurred while downloading and installing the latest version. The `sudo force-update-now` command needs to be explicitly issued. |
Use Case
You can use the following commands to check the DNS resolution issues on the service interface and routes to the surface interface.
- To check the reachability of a server IP address using ICMP:
/sc/bin/smmgr -ys smnet='ping <IP address or Domain Name>'
- To print the server interface IP config details:
/sc/bin/smmgr -ys smnet=ifconfig
- To check the DNS resolution of a hostname:
/sc/bin/smmgr -ys smnet='route'/sc/bin/smmgr -ys host="<Domain Name>" -ys connect=dns
- To check the communication or port reachability of a server:
/sc/bin/smmgr -ys host="<FQDN of SIEM server>" -ys port=<Listening port> -ys connect=tcp
What happens if the NSS goes down?
In the event of a connection loss between the NSS server and the cloud Nanolog, the cloud retransmits the logs to the NSS up to a maximum of one hour. If the NSS is down for more than an hour, the logs falling out of the one-hour window aren't retrieved by the NSS.