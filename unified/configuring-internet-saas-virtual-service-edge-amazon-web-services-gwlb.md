# Configuring Internet & SaaS Virtual Service Edge for Amazon Web Services with GWLB
Source: https://help.zscaler.com/unified/configuring-internet-saas-virtual-service-edge-amazon-web-services-gwlb
PDF: https://help.zscaler.com/pdf/com/en/1495666.pdf

Zscaler supports standalone Internet & SaaS Virtual Service Edge for production deployments on Amazon Web Services (AWS) with Gateway Load Balancer (GWLB). An organization can deploy the Virtual Service Edge instance on an EC2 Instance, on AWS with GWLB.
Before you begin deployment, contact Zscaler Support to request a share of the Virtual Service Edge AMI. Provide your AWS account ID and AWS region in which you want the AMI, except for China, as the Virtual Service Edge AMI is unavailable in this region (alternatively, you can consider [China Premium Internet Access](/unified/china-premium-internet-access) for the China region). After deployment, the Virtual Service Edge VM receives automatic software updates from the Zscaler cloud.
- [1. Ensure to Meet All the Requirements](#step-1)
- [2. Add Virtual Service Edge Instance](/unified/adding-internet-saas-virtual-service-edge-instances)
- [3. Download Virtual Service Edge Certificates](/unified/downloading-virtual-service-edge-certificates)
- [4. Provision and Configure Two EC2 Instances on the AWS Console](#step-4)
- [5. Configure and Start Virtual Service Edge on the VM Instance](#step-5)
- [6. Create a Target Group with the Virtual Service Edge Service IP address](#target-group)
- [7. Create a GWLB Instance in Load Balancer (LB)](#gwlb-in-lb)
- [8. Create an Endpoint Service in VPC](#endpoint-service)
- [9. Create an Endpoint in VPC](#endpoint-vpc)
- [10. Add the Service Port to Both the Virtual Service Edges on the Admin Portal](#service-port-vse)
Testing Traffic
To test the traffic:
- Add a route to the endpoint.
- Create a route table in the same VPC and subnet where you created the EC2 instance (client machine):
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **VPC** > **Route Tables**.
- Click **Create route table**.
- In the **Create route table** window:
- **Name - *****optional***: Enter a name for the route table.
- **VPC**: Enter the same VPC used to create the EC2 instance.
- Click **Create route table**.
- Add a route to the route table:
- Click **Edit routes**.
- Click **Add route**, and do the following:
- **Destination**: Enter the required destination subnet or enter 0.0.0.0/0 to send all traffic.
- **Target**: Enter the Endpoint ID of the Endpoint created in VPC.
- Click **Save Changes**.
- Associate the route table to the subnet where we created the EC2 instance:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **VPC** > **Subnets**.
- Select the subnet where we created the EC2 instance.
- Click **Edit route table association**.
- In the **Route table ID** field, enter the route table ID of the route table created in the preceding step.
- Click **Save**.
- Send the traffic from the EC2 Instance.
- In the Admin Portal, go to **Logs** > **Insights** > **Web Insights** > **Logs**, and retrieve the logs for the last 15 minutes to verify logs for test traffic are present.
After you have verified your deployment, if you face any issues with Virtual Service Edge, see [Troubleshooting Internet & SaaS Virtual Service Edge](/unified/troubleshooting-virtual-service-edges).
[]You need the following to deploy Virtual Service Edge on AWS:
- A subscription to Virtual Service Edge
-
VM specifications:
- Instance Memory: 32 GB
- EBS Storage Volume Type: General Purpose SSD (recommended)
- Data disk size: 500 GB
Virtual Service Edge requires an Elastic Network Adapter (ENA)-enabled AWS EC2 instance.
The recommended AWS EC2 instance specifications are as follows:
| Instance Size | Memory | Cores | Network Bandwidth | Instance Storage (GB) |
| ------------- | ------ | ----- | ----------------- | --------------------- |
| m5.2xlarge | 32 GB | 8 | Up to 10 Gbps | EBS-Only |
| c5.4xlarge | 32 GB | 16 | Up to 10 Gbps | EBS-Only |
If the swap utilization is observed in one of the image types, use the other one.
- A key pair with a public key and a private key file. AWS stores the public key, and your organization stores the private key file.
- A virtual private cloud (VPC) for your AWS account
- A subnet consisting of a range of IP addresses in your VPC
- Network Specs
- Two network interfaces
- The first network interface is the management IP address. It's used to control connections to the Zscaler cloud and make an SSH connection to the Virtual Service Edge VM for configuration and management.
- The second network interface is the service IP address. It's used to proxy the user traffic.
-
Two Elastic IP addresses: to assign a public IP address with both network interfaces.
The two elastic IP addresses are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
-
Firewall Requirements: It's mandatory to deploy the Virtual Service Edge instance behind a VM network security group. The Virtual Service Edge instance requires only outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge.
The <Zscaler Cloud Name> can be found in the URL you use to log in to the Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
[]Follow the next steps to launch a new EC2 instance with a Virtual Service Edge AMI, configure two network interfaces with Elastic IP addresses, and configure the required security group settings.
-
On the top right corner of the screen, select the region in which you want to launch the instance.
[See image.](#region_img)
-
Create a new security group.
- []Go to the Amazon EC2 console.
- In the left-side navigation, go to **Network & Security** > **Security Groups**.
- Click the **Create Security Group** button, and configure the following fields:
- **Security Group Name**: Enter the name of the security group. Associate this security group with the two Network Interfaces you create in the EC2 Instance Provisioning Wizard.
- **Description**: Enter additional notes or information. The required description shouldn’t be longer than 255 characters.
- **VPC**: Enter the VPC to which the security group belongs.
-
In the **Inbound rules** section, click the **Add Rule** button, and configure the following connection requirements:
- **Type**: Select the type of inbound traffic.
- **Protocol**: This field is automatically populated based on the type of inbound traffic selection.
- **Port range**: Enter the port range for the inbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
- **Source**: Select the source type for the inbound rule and enter the source IP address.
- **Description - optional**: Enter additional notes or information.
[See image.](#inboundrule_img)
-
In the **Outbound rules **section, click the **Add Rule** button, and configure the following connection requirements:
- **Type**: Select the type of outbound traffic.
- **Protocol**: This field is automatically populated based on the type of outbound traffic selection.
- **Port range**: Enter the port range for the outbound rule. To view the port range for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/zia-v-sedge. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge.
- **Destination**: Select the destination type for the outbound rule and enter the destination IP address.
- **Description - optional**: Enter additional notes or information.
[See image.](#outboundrules_img)
- Click **Create**.
[See image.](#securitygroup_img)
-
Launch and complete two new EC2 Instances.
- Go to the Amazon EC2 Console.
- Under **Create Instance**, click the **Launch Instance** button.
- In the left-side navigation, click the **My AMIs** tab.
- In the left-side navigation, under **Ownership**, check the box **Shared with me.**
-
Locate the latest AMI shared with your account, and click the **Select** button.
[See image.](#nssami_img)
To see the Virtual Service Edge AMI on your AMI tab, you need to provide Zscaler with your AWS Account ID and region, except for China, as the Virtual Service Edge AMI is unavailable in this region. Zscaler privately shares the AMI with you.
-
Choose the EC2 Instance type recommended in the Admin Portal.
Zscaler’s EC2 instance type recommendation is based on the expected number of transactions, users, and the most economical option for the customer. If you are unable to select the recommended type, contact Zscaler Support for further guidance.
[See image.](#instancetypes_img)
- Click **Next: Configure Instance Details**.
-
In the **Subnet **drop-down menu, select the subnet in which the instance resides.
[See image.](#subnet_img)
-
Under **Network Interfaces**, click the **Add Device** button to add an additional network interface. Ensure to select the same subnet.
By default, the EC2 instance has one Network Interface (eth0), but Virtual Service Edge requires an additional interface (eth1) in the same subnet. The management interface (eth0) is used for control connections to the Zscaler cloud and to make an SSH connection to the Virtual Service Edge for configuration and management. The service interface (eth1) is used for proxy services.
[See image.](#networkinterfaces_img)
- Click **Next: Add Storage**.
-
Choose the recommended specifications given in the Admin Portal.
General Purpose SSD is recommended as the volume type.
[See image.](#addstorage_img)
- Click **Next: Add Tags**, and add any necessary tags.
- Click **Next: Configure Security Group**.
-
Click **Select an existing security group**, and choose the security group you created earlier. Under **Source**, change 0.0.0.0 to a specific IP address from which you want to enable access.
[See image.](#configsecurity_img)
- Click **Review and Launch **to review your information.
- Click **Launch**, and select a key pair.
- Click **Launch Instances**. The Launch Status page tells you if the launch was successful.
Ensure to repeat steps i through xvii to launch a second EC2 instance.
-
Create and associate two Elastic IP addresses.
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **Network & Security** > **Network Interfaces**.
-
Note down the Network Interface IDs of the network interfaces you created in the previous step. You need one of the IDs when associating an Elastic IP to the Network Interfaces.
[See image.](#networkinterfaceid_img)
- Go to **Network & Security** > **Elastic IPs**.
- Click the **Allocate new address** button to allocate a new Elastic IP address.
-
Click **Allocate**. Repeat the preceding step and this step to have two Elastic IP addresses.
[See image.](#allocation_ids_img)
- Right-click on one of the Elastic IP addresses, and click **Associate Address**.
-
On the **Associate Address** page:
- **Resource Type**: Select the **Network Interface **option.
- **Network interface**: Choose one of the Network Interface IDs you noted earlier.
You can choose to either fill in the **Network interface** field or the **Private IP** field.
[See image.](#associate_img)
- Click **Associate**.
Repeat steps vii, viii, and ix for the other Elastic IP address.
![Screenshot of Virtual Service Edge Instances on AWS with GWLB](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-VSE-EC2-Instances.JPG)
[]![AWS Instance Regions ](/downloads/unified/networking/internet-saas/traffic-forwarding/service-edges/virtual-service-edge/configuring-internet-saas-virtual-service-edge-amazon-web-services-gwlb/AWS-Region-Selection.png)
[]![Screenshot of fields for creation of security group. The group name is Zscaler NSS.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Security-Group.png)
[]![Screenshot of Inbound Rules Section in Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Inbound-Rules.png)
[]![Screenshot of AWS Outbound Rules Section in Security Group page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services/AWS-Outbound-rules.png)
[]![Screenshot of VSE AMI listed in MY AMIs tab](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-My-AMIs-VSE.png)
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
-
Configure the network.
- Select the Virtual Service Edge VM and click either **Power On** or **Power On the virtual machine**.
- On the SSH terminal, enter the following credentials in the FreeBSD command prompt to log in:
Username: zsroot
Password: zsroot
The following guidelines apply:
- Zscaler strongly recommends that you change this default password. Run the following command:
`passwd`
- Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
- Run the following command:
sudo vzen configure-network
Specify the following details:
- Address of the DNS server that is used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic. For example: 10.84.0.100.
- Hostname of the Virtual Service Edge.
The Virtual Service Edge management IP, gateway IP for management, and resolvers are obtained from DHCP.
This command does not allow you to modify the management IP and gateway IP.
- Install the SSL certificate of the Virtual Service Edge instance. This is the certificate that you downloaded from the Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service. When you configure a Virtual Service Edge, ensure that you upload the correct certificate for the Virtual Service Edge instance.
To install the SSL certificate of the Virtual Service Edge instance:
- Go to the SSL certificate that you saved.
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
- The user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries only from this user name.
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
[]To create a target group with the Virtual Service Edge's service IP address:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **EC2** > **Target Groups**.
- Click the **Create target group** button.
-
Choose the **IP addresses** target type.
[See image.](#create-target-groups)
-
Configure the following:
- **Target Group Name**: Enter a name for the target group.
- **Protocol**: Select **GENEVE** protocol.
- **Port**: Ensure the port is set to **6081**.
- **VPC**: Select the Virtual Service Edge's VPC.
- **Health check protocol**: Select the **TCP** protocol.
[See image.](#create-target-group-window)
-
In the **Advanced health check settings**:
- **Health check port**: Choose the **Override** option, and configure it to any unknown port (e.g., 5000).
- **Healthy threshold**: Enter a healthy threshold as per your organization's requirement.
- **Unhealthy threshold**: Enter an unhealthy threshold as per your organization's requirement.
- **Timeout**: Enter a timeout as per your organization's requirement.
- **Interval**: Enter an interval as per your organization's requirement.
[See image.](#advanced-health-check-settings)
- Click **Next**.
-
Configure the following to register the targets:
- **Network**: Select the same network as the Virtual Service Edge's VPC network.
-
**IPv4 addresses**: Enter the service IP addresses of both the Virtual Service Edges.
You can add more IP addresses by clicking **Add IPv4 address**.
- **Ports**: Ensure the port is set to **6081**.
[See image.](#register-targets)
- Click **Include as pending below**.
- Review the targets.
- Click **Create target group**.
[]![Screenshot of AWS Create Target Groups](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Target-Groups.JPG)
[]![AWS-Create-Target-Groups-Window.png](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Target-Groups-Window.png)
[]![Screenshot of AWS Advanced Health Check Settings](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Advanced-Health-Check-Settings.png)
[]![Screenshot of AWS Register Targets](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Register-Targets.JPG)
[]To create GWLB in LB:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **EC2** > **Load balancers**.
- Click **Compare and select load balancer type**.
-
Click **Create** for **Gateway Load Balancer**.
[See image.](#create-gwlb)
-
In the **Create Gateway Load Balancer **window:
- **Load balancer name**: Enter a name for the LB.
- **VPC**: Select the Virtual Service Edge's VPC.
- **Mappings**: Select the Virtual Service Edge's **Zone** and **Subnet**.
- **IP listener routing**: Select the target group created in the preceding step.
[See image.](#create-gwlb-window)
-
Review the summary.
[See image.](#gwlb-review-summary)
- Click **Create Load Balancer**.
[]![Screenshot of AWS Compare and select load balancer type](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Gateway-Loadbalancer.JPG)
[]![Screenshot of AWS Create Gateway Load Balancer Window](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Gateway-Load-Balancer.png)
[]![Screenshot of AWS GWLB Summary](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-GWLB-Summary.JPG)
[]To create an endpoint service in VPC:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **VPC** > **Endpoint services**.
- Click **Create endpoint service**.
-
In the **Create endpoint service **window:
- **Name - *****Optional***: Enter a name for the endpoint service.
- **Load balancer type**: Select the **Gateway** type.
- **Available load balancers**: Select the GWLB created in the preceding step.
[See image.](#create-endpoint-service-window)
-
In the **Additional Settings** section:
- **Require acceptance for endpoint**: Select the **Acceptance required** option.
- **Supported IP address types**: Select the **IPv4** option.
[See image.](#endpoint-service-additional-settings)
-
Click **Create**.
The endpoint service is created.
[]![Screenshot of AWS Create Endpoint Service Window](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Create-Endpoint-Service-Window.png)
[]![Screenshot of AWS Endpoint Service Additional Settings](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Endpoint-Service-Additional-Settings.png)
[]To create an endpoint in VPC:
- Go to the Amazon EC2 console.
- In the left-side navigation, go to **VPC** > **Endpoints**.
- Click **Create endpoint**.
-
In the **Endpoint settings** section:
- **Name - *****optional***: Enter a name for the endpoint.
- **Service category**: Select **Other endpoint services** category.
[See image.](#endpoint-settings)
- In the **Service settings** section, enter the service name of the endpoint service created in the preceding step in the **Service name** field.
-
Click **Verify service**.
[See image.](#endpoint-service-settings-verify)
- In the **VPC** field, select the Virtual Service Edge's VPC.
-
In the **Subnets** section:
- **Availability Zone**: Select the Virtual Service Edge's zone.
- **Subnet ID**: Choose the Virtual Service Edge's subnet ID.
[See image.](#endpoint-subnets)
-
Click **Create Endpoint**.
The endpoint is created.
- Go to **VPC** > **Endpoint services**.
- Select the endpoint service created in the preceding step.
- Go to the **Endpoint connections** tab.
- Select the endpoint created in step i.
-
In the **Actions** drop-down, select **Accept endpoint connection request**.
[See image.](#endpoint-services-accept-endpoint-connection-request)
[]![Screenshot of AWS Endpoint Settings](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Endpoint-Settings.JPG)
[]![Screenshot of AWS Endpoint Service Settings Verification](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Endpoint-Service-Settings-Verify.JPG)
[]![Screenshot of AWS Endpoint Subnets](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Endpoint-Subnet.JPG)
[]![Screenshot of AWS Endpoint Services with Accept Endpoint Connection Request Action](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-amazon-web-services-gwlb/AWS-Endpoint-Service-Acceptance.JPG)
[]To add a service port to both the Virtual Service Edges:
- Go to the /sc/sme/conf folder:
cd /sc/sme/conf
- Create a new file called `vzen_custom.conf`:
touch vzen_custom.conf
This step is not necessary if the `vzen_custom.conf` file is already there.
- Edit `vzen_custom.conf`:
vi vzen_custom.conf
- Enter the following port in the vzen_custom.conf file and save:
[SME]
serv_port=<Health check port configured>
[-end-of-SME-]
Ensure to enter the correct health check port (e.g., 5000) configured in Step 6.
- Restart the Virtual Service Edges:
sudo vzen restart
- Check the health status of the target groups created (EC2 > Target Groups).
Ensure that the status of the target groups is healthy.
- Forward your organization's traffic to GWLB.