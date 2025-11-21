# Configuring Virtual Service Edge for Amazon Web Services
Source: https://help.zscaler.com/zia/configuring-virtual-service-edge-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1402336.pdf

Zscaler supports standalone ZIA Virtual Service Edge for production deployments on Amazon Web Services (AWS). An organization can deploy the Virtual Service Edge instance on an EC2 Instance, on AWS.
Before you begin deployment, subscribe to the ZIA Virtual Service Edge AMI from the [AWS Marketplace AMIs](https://aws.amazon.com/marketplace/pp/prodview-ex2z2yzqrdsb6?applicationId=AWSMPContessa&ref_=beagle&sr=0-5) tab. The Virtual Service Edge AMI is unavailable in the China region (alternatively, you can consider [China Premium Internet Access](/zia/china-premium-internet-access) for the China region). After deployment, the Virtual Service Edge VM receives automatic software updates from the Zscaler cloud.
- [1. Ensure you meet all the requirements.](#step-1)
- [2. Add Virtual Service Edge instance.](/zia/adding-virtual-service-edge-instances)
- [3. Download Virtual Service Edge certificates.](/zia/downloading-virtual-service-edge-certificates)
- [4. Use the AWS console to provision and configure an EC2 instance.](#step-4)
- [5. Configure and start Virtual Service Edge on the VM instance.](#step-5)
After you verify your deployment, if you face any issues with the Virtual Service Edge, you can [Troubleshoot Virtual Service Edges](/zia/troubleshooting-virtual-service-edges).
[]You need the following to deploy Virtual Service Edge on AWS:
- A subscription to Virtual Service Edge
-
A VM with the following:
- Instance Memory: 32 GB
- EBS Storage Volume Type: General Purpose SSD (recommended)
- Data disk size: 500 GB
Virtual Service Edge requires an AWS EC2 instance with Elastic Network Adapter (ENA) enabled.
The recommended AWS EC2 instance specifications are as follows:
| Instance Size | Memory | Cores | Network Bandwidth | Instance Storage (GB) |
| ------------- | ------ | ----- | ----------------- | --------------------- |
| m5.2xlarge | 32 GB | 8 | Up to 10 Gbps | EBS-Only |
| r5.2xlarge | 64 GB | 8 | Up to 10 Gbps | EBS-Only |
If you observe swap usage in m5.2xlarge, use the larger instance type r5.2xlarge.
- A key pair with a public key and a private key file. AWS stores the public key and your organization stores the private key file.
- A virtual private cloud (VPC) for your AWS account
- A subnet consisting of a range of IP addresses in your VPC
- A network with the following specifications:
- Two network interfaces
- The first network interface is the management IP address. It's used to control connections to the Zscaler cloud and make an SSH connection to the Virtual Service Edge VM for configuration and management.
- The second network interface is the service IP address. It's used to proxy the user traffic.
-
Two Elastic IP addresses to assign a public IP address with both network interfaces.
The two Elastic IP addresses are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
-
A firewall that meets the necessary requirements: It's mandatory to deploy the Virtual Service Edge instance behind a VM network security group. The Virtual Service Edge instance requires only outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge.
You can find the <Zscaler Cloud Name> in the URL you use to log in to the ZIA Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge. To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
[]Follow the next steps to launch a new EC2 instance with a Virtual Service Edge AMI, configure two network interfaces with Elastic IP addresses, and configure the required security group settings:
-
Select the instance region.
In the top-right corner of the screen, select the region in which you want to launch the instance.
[See image.](#region_img)
- Create a new security group.
- []Go to the Amazon EC2 console.
- In the left-side navigation, go to **Network & Security** > **Security Groups**.
- Click **Create Security Group**. The **Create Security Group **page appears. Configure the following fields:
- **Security group name**: Enter the name of the security group. Associate this security group with the two network interfaces you create in the EC2 Instance Provisioning Wizard.
- **Description**: Enter additional notes or information up to 255 characters in length.
-
**VPC**: Enter the VPC to which the security group belongs.
[See image.](#securitygroup_img)
-
In the **Inbound rules** section, click **Add rule** and configure the following connection requirements:
- **Type**: Select the type of inbound traffic.
- **Protocol**: This field is automatically populated based on the type of inbound traffic you select.
-
**Port range**: Enter the port range for the inbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<zscaler-cloud-name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/zia-v-sedge](https://config.zscaler.com/zscaler.net/zia-v-sedge).
If you set **Type** to **All** **traffic**, the port range is automatically populated to **All**.
- **Source**: Select the source type for the inbound rule and enter the source IP address.
- **Description - optional**: Enter additional notes or information.
[See image.](#inboundrule_img)
To connect to your EC2 instance via SSH, you must open port 22 for inbound connections. In production, authorize only a specific IP address or range of addresses to access your instance. Do not use 0.0.0.0. To learn more, refer to the [AWS documentation](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html).
-
In the **Outbound rules **section, click **Add rule** and configure the following connection requirements:
- **Type**: Select the type of outbound traffic.
- **Protocol**: This field is automatically populated based on the type of outbound traffic you select.
-
**Port range**: Enter the port range for the outbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<zscaler-cloud-name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/zia-v-sedge](https://config.zscaler.com/zscaler.net/zia-v-sedge).
If you set **Type** to **All** **traffic**, the port range is automatically populated to **All**.
- **Destination**: Select the destination type for the outbound rule and enter the destination IP address.
- **Description - optional**: Enter additional notes or information.
[See image.](#outboundrules_img)
-
Click **Create**.
You can find more details about the outbound connection requirements on https://config.zscaler.com/<zscaler-cloud-name>/zia-v-sedge. You can find the <zscaler-cloud-name> in the URL you use to log in to the ZIA Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
-
Launch and complete a new EC2 Instance.
- Go to the Amazon EC2 Console.
- Under **Create Instance**, click **Launch Instance**.
-
In the right-side navigation, click the **Browse more AMIs** tab.
[See image.](#browse-more-amis)
-
Click the **AWS Marketplace AMIs** tab.
[See image.](#marketplace-ami)
- In the **Search** field, search for **Zscaler Internet Access Virtual Service Edge**.
-
From the search results, click **Select** for the **Zscaler Internet Access Virtual Service Edge **AMI.
[See image.](#zia-vse-ami)
-
In the **Zscaler Internet Access Virtual Service Edge **AMI, click **Subscribe now**.
[See image.](#zia-vse-ami-subscribe-now)
-
Choose the EC2 Instance type recommended in the ZIA Admin Portal (i.e., m5.2xlarge or the larger r5.2xlarge).
[See image.](#instancetypes_img)
Zscaler’s EC2 instance type recommendation is based on the expected number of transactions, users, and the most economical option for you. If you cannot select the recommended type, contact Zscaler Support for further guidance.
-
Select the SSH key pair for login.
[See image.](#keypair-login)
AWS Virtual Service Edges can only be accessed via SSH using the zsroot user and the private key corresponding to the selected key pair.
-
Click **Edit** next to the Network Settings. Then select the VPC and subnet in which the instance resides from the **VPC - *****required*** and **Subnet **drop-down menus, respectively.
[See image.](#subnet_img)
-
Under **Network interfaces**, click **Create network interface** to add another network interface. Be sure to select the same subnet.
[See image.](#networkinterfaces_img)
By default, the EC2 instance has one network interface (eth0), but a Virtual Service Edge requires an additional interface (eth1) in the same subnet. The management interface (eth0) is used for control connections to the Zscaler cloud and to make an SSH connection to the Virtual Service Edge for configuration and management. The service interface (eth1) is used for proxy services.
- Click **Configure storage**.
-
Choose the recommended specifications given in the ZIA Admin Portal.
[See image.](#addstorage_img)
General Purpose 3 (GP3 SSD) is recommended as the volume type.
-
Click **Names and tags**, name the EC2 instance, and add any necessary tags.
[See image.](#name-tags)
- Click **Edit** next to the Network Settings.
-
Click **Select an existing security group** and choose the security group you created earlier. Under **Source**, change 0.0.0.0 to a specific IP address from which you want to enable access.
[See image.](#configsecurity_img)
- Review your information.
- Click **Launch Instances**. The **Launch Status** page shows whether the launch is successful.
-
Create and associate two Elastic IP addresses:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **Network & Security** > **Network Interfaces**.
- Note down the network interface IDs of the network interfaces you created earlier. You need one of the IDs when associating an Elastic IP to the network interfaces.
[See image.](#networkinterfaceid_img)
- Go to **Network & Security** > **Elastic IPs**.
- Click **Allocate new address** to allocate a new Elastic IP address.
-
Click **Allocate**. Repeat the preceding step and this step to have two Elastic IP addresses.
[See image.](#allocation_ids_img)
- Right-click one of the Elastic IP addresses, and click **Associate Address**.
-
On the **Associate Address** page:
- **Resource type**: Select **Network interface**.
-
**Network interface**: Choose one of the network interface IDs you noted earlier.
You can choose to either fill in the **Network interface** section or the **Private IP** section.
[See image.](#associate_img)
- Click **Associate**.
Repeat steps xxiii, xxiv, and xxv for the other Elastic IP address.
[]![The AWS Launch an instance page with the Browse more AMIs](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Launch-Instances-Browse-More-AMIs.png)
[]![The AWS Choose an Amazon Machine Image (AMI) page with the AWS Marketplace AMIs tab](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Marketplace-AMIs.png)
[]![The AWS Marketplace AMI tab with the Zscaler Internet Access Virtual Service Edge AMI](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/ZIA-VSE-AMI-Select.png)
[]![The AWS ZIA Virtual Service Edge AMI with the Subscribe now button](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-ZIA-VSE-AMI.png)
[]![View of the instance region options to launch an EC2 instance](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Region-Selection.png)
[]![View of the Create security group page with basic details, inbound rules, and outbound rules.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/ZIA-AWS-Create-Security-Group.png)
[]![View of the Inbound Rules Section on the Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Inbound-Rules.png)
[]![View of the AWS Outbound Rules Section on the Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Outbound-rules.png)
[]![View of the listed EC2 instance types](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Choose-Instance-Type.png)
[]![AWS Key Pair Login](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Key-Pair.png)
[]![View of the Configure Instance page with Subnet dropdown menu highlighted](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Configure-Instance-Details.png)
[]![The AWS EC2 Network interfaces page with the Create network interface button](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-EC2-Network-Interfaces.png)
[]![View of the storage device settings fields](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Configure-Storage.png)
[]![AWS Names and Tags](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Names-Tags.png)
[]![View of the AWS Zscaler Virtual Service Edge security group selected](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Configure-Security-Group.png)
[]![The AWS Network interfaces section with Network interface IDs.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/ZIA-AWS-Network-Interface-IDs.png)
[]![View of two Elastic IPs and their Allocation IDs in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Elastic%20IP%20Addresses.png)
[]![View of the Associate Address page in AWS with fields filled out](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Associate%20Address%20page.png)
[]Run the following Virtual Service Edge configuration steps through an SSH terminal connection.
To configure the Virtual Service Edge on the VM:
- Configure the network.
-
Select the Virtual Service Edge VM and click **Start instance**.
[See image.](#vm-instance)
-
On the SSH terminal, enter the private key of the selected SSH key pair to connect to the zsroot user of the Virtual Service Edge.
Use the SSH command in the following format to connect to the zsroot user:
`ssh -i <ssh_key.pem> zsroot@<VSE_management_IP>`
[See image.](#ssh-login-zsroot-user)
Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
-
Run the following command:
`sudo vzen configure-network`
Specify the following details:
- Address of the DNS server that is used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic. For example: 10.84.0.100.
- Hostname of the Virtual Service Edge.
The Virtual Service Edge management IP, gateway IP for management, and resolvers are obtained from DHCP.
This command does not allow you to modify the management IP and gateway IP.
- Install the SSL certificate of the Virtual Service Edge instance. This is the certificate that you downloaded from the ZIA Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service.
When you configure a Virtual Service Edge, ensure that you upload the correct certificate for the Virtual Service Edge instance.
To install the SSL certificate of the Virtual Service Edge instance:
- Go to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- On the SSH terminal, log in with the following credentials:
Username: zsroot
Password: zsroot
-
Run the following command:
`sudo vzen install-cert <cert-bundle.zip>`
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
-
(Optional) If you want to use an SNMP management system to monitor the Virtual Service Edge cluster, [enable SNMP for Virtual Service Edge](/zia/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
Run the following command:
`sudo vzen snmp-admin-configure`
Specify the following information:
- The username for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries only from this username.
- The password that the Virtual Service Edge uses to authenticate the SNMP management system.
- An authentication protocol that the Virtual Service Edge uses to authenticate the SNMP user. Enter either MD5 or SHA1.
- An encryption method that the Virtual Service Edge uses to authenticate the SNMP user. Enter either DES or AES.
-
Run the following command:
`sudo vzen snmp-trap-configure`
When asked which traps you want to configure, specify v3 traps.
Specify the following information:
- The IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- The username for the SNMP management system.
- The password that the Virtual Service Edge uses to authenticate the SNMP management system.
- An authentication protocol that the Virtual Service Edge uses to authenticate the SNMP user. Enter either MD5 or SHA1.
- An encryption method that the Virtual Service Edge uses to authenticate the SNMP user. Enter either DES or AES.
- Download the Virtual Service Edge build and start the Virtual Service Edge.
- Use SSH to connect to the management IP address.
-
Run the following command to download the Virtual Service Edge build:
`sudo vzen download-build`
The initial build is around 1 GB, so it might take a while depending on your internet connection. The downloaded build is automatically installed. The Virtual Service Edge automatically starts after the installation is complete.
- Verify the configuration.
- Use SSH to connect to the management IP address.
-
Run the following command:
`sudo vzen status`
The output should display that the Virtual Service Edge service is running.
[See image.](#ssh-port-vzen)
-
Run the following command:
`sudo vzen troubleshoot connection | grep 9422`
The output should display an established connection.
[]![View of the SSH port showing that the VZEN service and load balancer are running](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/configuring-vzen-amazon-web-services/ZIA-SSH-VZEN-Status-AWS.png)
[]![AWS VM Instances](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-VM-Instance.png)
[]![SSH Terminal Login to zsroot User](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/SSH-Private-Key-Pair-Login.png)