# Configuring Internet & SaaS Virtual Service Edge for Amazon Web Services
Source: https://help.zscaler.com/unified/configuring-internet-saas-virtual-service-edge-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1495661.pdf

Zscaler supports standalone Internet & SaaS Virtual Service Edge for production deployments on Amazon Web Services (AWS). An organization can deploy the Virtual Service Edge instance on an EC2 Instance, on AWS.
Before you begin deployment, contact Zscaler Support to request a share of the Virtual Service Edge AMI. Provide your AWS account ID and AWS region in which you want the AMI, except for China, as the Virtual Service Edge AMI is unavailable in this region (alternatively, you can consider [China Premium Internet Access](/unified/china-premium-internet-access) for the China region). After deployment, the Virtual Service Edge VM receives automatic software updates from the Zscaler cloud.
- [1. Ensure to Meet All the Requirements](#step-1)
- [2. Add the Virtual Service Edge Instance](/unified/adding-internet-saas-virtual-service-edge-instances)
- [3. Download the Virtual Service Edge Certificates](/unified/downloading-virtual-service-edge-certificates)
- [4. Use the AWS Console to Provision and Configure an EC2 Instance](#step-4)
- [5. Configure and Start Virtual Service Edge on the VM Instance](#step-5)
After you have verified your deployment, if you face any issues with Virtual Service Edge, see [Troubleshooting Internet & SaaS Virtual Service Edge](/unified/troubleshooting-virtual-service-edges).
[]You'll need the following to deploy Virtual Service Edge on AWS:
- A subscription to Virtual Service Edge
- VM specifications:
- Instance Memory
- 32 GB
- EBS Storage Volume Type
- General Purpose SSD (recommended)
- Data disk size: 500 GB
Virtual Service Edge requires Elastic Network Adapter (ENA)-enabled AWS EC2 instance.
The recommended AWS EC2 instance specifications are as follows:
| Instance Size | Memory | Cores | Network Bandwidth | Instance Storage (GB) |
| ------------- | ------ | ----- | ----------------- | --------------------- |
| m5.2xlarge | 32 GB | 8 | Up to 10 Gbps | EBS-Only |
| c5.4xlarge | 32 GB | 16 | Up to 10 Gbps | EBS-Only |
If the swap utilization is observed in one of the image types, use the other one.
- A key pair with a public key and a private key file. AWS stores the public key, and your organization stores the private key file.
- A virtual private cloud (VPC) for your AWS account
- A subnet consisting of a range of IP addresses in your VPC
- Network SpecsAdmin Portal
- Two network interfaces
- The first network interface is the management IP address. It's used to control connections to the Zscaler cloud and make an SSH connection to the Virtual Service Edge VM for configuration and management.
- The second network interface is the service IP address. It's used to proxy the user traffic.
- Two Elastic IP addresses: to assign a public IP address with both network interfaces.
The two elastic IP addresses are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
- Firewall Requirements: It's mandatory to deploy the Virtual Service Edge instance behind a VM network security group. The Virtual Service Edge instance requires only outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge.
The <Zscaler Cloud Name> can be found in the URL you use to log in to the Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
[]Follow the next steps to launch a new EC2 instance with a Virtual Service Edge AMI, configure two network interfaces with Elastic IP addresses, and configure the required security group settings.
- Select the instance region.
- On the top right corner of the screen, select the region in which you want to launch the instance.
[See image.](#region_img)
- Create a new security group.
- []Go to the Amazon EC2 console.
- On the side menu, go to **Network & Security** > **Security Groups**.
- Click the **Create Security Group** button, and configure the following fields:
- **Security Group Name**: Enter the name of the security group. Associate this security group with the two Network Interfaces you create in the EC2 Instance Provisioning Wizard.
- **Description**: Enter additional notes or information. The required description shouldn’t be longer than 255 characters.
- **VPC**: Enter the VPC to which the security group belongs.
[See image.](#securitygroup_img)
- In the **Inbound rules** section, click the **Add Rule** button, and configure the following connection requirements:
- **Type**: Select the type of inbound traffic.
- **Protocol**: This field is automatically populated based on the type of inbound traffic selection.
- **Port range**: Enter the port range for the inbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
The port range is automatically populated to All if the **Type** field selection is All traffic.
- **Destination**: Select the destination type for the inbound rule and enter the destination IP address.
- **Description - optional**: Enter additional notes or information.
To connect to your EC2 instance via SSH, you're required to open port 22 for inbound connections. In production, you should authorize only a specific IP address or range of addresses to access your instance and not use 0.0.0.0. To learn more, see [Authorizing Inbound Traffic for Your Linux Instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/authorizing-access-to-an-instance.html).
[See image.](#inboundrule_img)
- In the **Outbound rules **section, click the **Add Rule** button, and configure the following connection requirements:
- **Type**: Select the type of outbound traffic.
- **Protocol**: This field is automatically populated based on the type of outbound traffic selection.
- **Port range**: Enter the port range for the outbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
The port range is automatically populated to All if the **Type** field selection is All traffic.
- **Destination**: Select the destination type for the outbound rule and enter the destination IP address.
- **Description - optional**: Enter additional notes or information.
[See image.](#outboundrules_img)
- Click **Create**.
You can find more details about the outbound connection requirements on https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge. The <Zscaler Cloud Name> can be found in the URL you use to log in to the Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
- Launch and complete a new EC2 Instance.
- Go to the Amazon EC2 Console.
- Under **Create Instance**, click the **Launch Instance** button.
- On the side menu, click the **My AMIs** tab.
- On the side menu, under **Ownership**, check the box **Shared with me.**
- Locate the latest AMI shared with your account, and click the **Select** button.
[See image.](#nssami_img)
To see the Virtual Service Edge AMI on your AMI tab, you need to provide Zscaler with your AWS Account ID and region, except for China, as the Virtual Service Edge AMI is unavailable in this region. Zscaler privately shares the AMI with you.
- Choose the EC2 Instance type recommended in the Admin Portal.
- Zscaler's EC2 instance type recommendation is based on the expected number of transactions, users, and the most economical option for the customer. If you are unable to select the recommended type, contact Zscaler Support for further guidance.
[See image.](#instancetypes_img)
- Click **Next: Configure Instance Details**.
- In the **Subnet **drop-down menu, select the subnet in which the instance resides.
[See image.](#subnet_img)
- Under **Network Interfaces**, click the **Add Device** button to add an additional network interface. Ensure to select the same subnet.
- By default, the EC2 instance has one Network Interface (eth0), but Virtual Service Edge requires an additional interface (eth1) in the same subnet. The management interface (eth0) is used for control connections to the Zscaler cloud and to make an SSH connection to the Virtual Service Edge for configuration and management. The service interface (eth1) is used for proxy services.
[See image.](#networkinterfaces_img)
- Click **Next: Add Storage**.
- Choose the recommended specifications given in the Admin Portal.
- General Purpose SSD is recommended as the volume type.
[See image.](#addstorage_img)
- Click **Next: Add Tags, **and add any necessary tags.
- Click **Next: Configure Security Group**.
- Click **Select an existing security group**, and choose the security group you created earlier. Under **Source**, change 0.0.0.0 to a specific IP address from which you want to enable access.
[See image.](#configsecurity_img)
- Click **Review and Launch **to review your information.
- Click **Launch**, and select a key pair.
- Click **Launch Instances**. The Launch Status page tells you if the launch was successful.
- Create and associate two Elastic IP addresses.
- Go to the Amazon EC2 console.
- On the side menu, go to **Network & Security** > **Network Interfaces**.
- Note down the Network Interface IDs of the network interfaces you created in the previous step. You’ll need one of the IDs when associating an Elastic IP to the Network Interfaces.
[See image.](#networkinterfaceid_img)
- Go to **Network & Security** > **Elastic IPs**.
- Click the **Allocate new address** button to allocate a new Elastic IP address.
- Click **Allocate**. Repeat the preceding step and this step to have two Elastic IP addresses.
[See image.](#allocation_ids_img)
- Right-click on one of the Elastic IP addresses, and click **Associate Address**.
- On the **Associate Address** page, configure the following.
- **Resource Type**: Select the **Network Interface **option.
- **Network interface**: Choose one of the Network Interface IDs you noted earlier.
You can choose to either fill in the **Network Interface** section or the **Private IP** section.
[See image.](#associate_img)
- Click **Associate**.
Repeat the steps g, h, and i for the other Elastic IP address.
[]![Screenshot of instance region options to launch an EC2 instance](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/AWS%20Region%20Selection.png)
[]![Screenshot of fields for creation of security group. The group name is Zscaler NSS.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Create-Security-Group.PNG)
[]![Screenshot of Inbound Rules Section in Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Inbound-Rules.png)
[]![Screenshot of AWS Outbound Rules Section in Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Outbound-rules.png)
[]![Screenshot of VSE AMI listed in MY AMIs tab](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-My-AMIs-VSE.PNG)
[]![Screenshot of listed EC2 instance types](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Choose%20Instance.png)
[]![Screenshot of Configure Instance page with Subnet dropdown menu highlighted](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Configure%20Instance%20Details.png)
[]![Screenshot of Configure Instance page with two network interfaces](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Add%20Network%20Interface.png)
[]![Screenshot of storage device settings fields](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Add%20Storage.png)
[]![Screenshot of AWS Zscaler VSE security group selected](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Configure-Security-Group.PNG)
[]![Screenshot of two Network Interface IDs highlighted in AWS](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Network-Interface-IDs.PNG)
[]![Screenshot of two Elastic IPs and their Allocation IDs in AWS](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Elastic%20IP%20Addresses.png)
[]![Screenshot of Associate Address page in AWS with fields filled out](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-guide-aws/Associate%20Address%20page.png)
[]The following Virtual Service Edge configuration steps are run through an SSH terminal connection.
To configure the Virtual Service Edge on the VM:
- Configure the network.
- Select the Virtual Service Edge VM and click either **Power On** or **Power On the virtual machine**.
- On the SSH terminal, enter the following credentials in the FreeBSD command prompt to log in:
Username: zsroot
Password: zsroot
The following guidelines apply:
- Zscaler strongly recommends that you change this default password. Run the following command:
passwd
- Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
- Run the following command:
sudo vzen configure-network
Specify the following details:
- Address of the DNS server that is used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic. For example: 10.84.0.100.
- Hostname of the Virtual Service Edge.
The Virtual Service Edge management IP, gateway IP for management, and resolvers are obtained from DHCP.
This command does not allow you to modify the management IP and gateway IP.
- Install the SSL certificate of the Virtual Service Edge instance. This is the certificate that you downloaded from the Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service.
When you configure a Virtual Service Edge, ensure that you upload the correct certificate for the Virtual Service Edge instance.
To install the SSL certificate of the Virtual Service Edge instance:
- Navigate to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- On the SSH terminal, log in with the following credentials:
Username: zsroot
Password: zsroot
- Use SSH to connect to the management IP address.
- Run the following command:
sudo vzen install-cert <cert-bundle.zip>
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
- (Optional) if you want to use an SNMP management system to monitor the Virtual Service Edge cluster, [enable SNMP for Virtual Service Edge](/unified/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
- Run the following command:
sudo vzen snmp-admin-configure
Specify the following information:
- The user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries only from this username.
- The password that the Virtual Service Edge uses to authenticate the SNMP management system.
- An authentication protocol that the Virtual Service Edge uses to authenticate the SNMP user. Enter either MD5 or SHA1.
- An encryption method that the Virtual Service Edge uses to authenticate the SNMP user. Enter either DES or AES.
- Run the following command:
sudo vzen snmp-trap-configure
When asked which traps you want to configure, specify v3 traps.
Specify the following information:
- The IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- The user name for the SNMP management system.
- The password that the Virtual Service Edge uses to authenticate the SNMP management system.
- An authentication protocol that the Virtual Service Edge uses to authenticate the SNMP user. Enter either MD5 or SHA1.
- An encryption method that the Virtual Service Edge uses to authenticate the SNMP user. Enter either DES or AES.
- Download the Virtual Service Edge build and start the Virtual Service Edge.
- Use SSH to connect to the management IP address.
- Run the following command to download the Virtual Service Edge build:
sudo vzen download-build
The initial build is around 1 GB, so it may take a while depending on your internet connection. The downloaded build is automatically installed. The Virtual Service Edge automatically starts after the installation is complete.
- Verify the configuration.
- Use SSH to connect to the management IP address.
- Run the following command:
sudo vzen status
The output should display that the Virtual Service Edge service is running.
[See image.](#ssh-port-vzen)
- Run the following command:
sudo vzen troubleshoot connection | grep 9422
The output should display an established connection.
[]![Screenshot of SSH port showing that the VZEN service and load balancer are running](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/configuring-vzen-amazon-web-services/ZIA-SSH-VZEN-Status-AWS.png)