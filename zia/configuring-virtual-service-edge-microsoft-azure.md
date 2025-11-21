# Configuring Virtual Service Edge for Microsoft Azure
Source: https://help.zscaler.com/zia/configuring-virtual-service-edge-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1401636.pdf

Zscaler supports standalone Virtual Service Edge for production deployments on Microsoft Azure.
Configuring a Standalone Virtual Service Edge
To configure a standalone Virtual Service Edge:
- [1. Ensure that you meet all of the requirements.](#step-1)
- [2. Add the Virtual Service Edge instance.](#add-vse-instances)
- [3. Download the Virtual Service Edge certificates.](#downloading-vse-certificates)
- [4. Create the VM instance and validate the configuration.](#step-4)
- [5. Create a Firewall Filtering rule to bypass Azure LB IP addresses.](#step-5)
- [6. Configure and start Virtual Service Edge on the VM instance.](#step-6)
Associating Multiple Virtual Service Edges with Azure LB
To associate a single Virtual Service Edge VM with Azure LB, skip the first two steps. To associate multiple Virtual Service Edges with Azure LB:
- [1. Create an availability set in your Azure account.](#availability-set)
- [2. Create Virtual Service Edge VMs using the PowerShell deployment script with availability set parameter.](#deployment-avset)
- [3. Associate Virtual Service Edge with Azure LB.](#associate-VSE-LB)
You can forward the traffic to the Azure LB virtual IP after creating load balancing rules.
Zscaler recommends Azure's [best practices](https://docs.microsoft.com/en-us/azure/security/fundamentals/iaas) for securing VMs.
If you face any issues with Virtual Service Edge, you can [Troubleshoot Virtual Service Edge](/zia/troubleshooting-virtual-zens).
[]To associate Virtual Service Edge with Azure LB:
- [a. Create an Azure LB in the resource group.](#azure-lb-resource-group)
- [b. Create a backend pool and link Virtual Service Edge VMs.](#backend-pool)
- [c. Create health probes for the ports.](#health-probes)
- [d. Create load balancing rules.](#load-balancing-rules)
[]You need the following to deploy Virtual Service Edge over your virtual machine (VM):
- A subscription to Virtual Service Edge.
- VM specifications:
- VM Size: Standard_A4m_v2CPU.
- CPU: 4 CPU cores. Each CPU core independently handles a portion of the traffic for the Virtual Service Edge.
- Instance Memory: 32 GB for production.
- Storage account: General Purpose.
- Storage Type: Premium SSD.
- Data disk size: 500 GB.
- Network Specs:
- Two network interfaces.
- The first network interface is the management IP address. It's used to control connections to the Zscaler cloud and make an SSH connection to the Virtual Service Edge VM for configuration and management. You can customize the deployment and define a separate IP address for the SSH connection to the Virtual Service Edge VM.
- The second network interface is the service IP address.
-
Two public IPs.
The two public IPs are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
-
Firewall Requirements: It's mandatory to deploy the Virtual Service Edge instance behind a VM network security group. The Virtual Service Edge instance only requires outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, go to the following URL:
https://config.zscaler.com/<zscaler cloud name>/zia-v-sedge.
You can find the <zscaler cloud name> in the URL you use to log in to the ZIA Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge. ​​​​​​
[]To add a Virtual Service Edge instance:
- Go to **Administration **> **Virtual Service Edges**.
-
Click **Add Virtual Service Edge**.
The **Add Virtual Service Edge** window appears.
- In the **Add Virtual Service Edge** window:
- **Name**: Enter a name for the Virtual Service Edge.
- **Status**: Choose to enable or disable the Virtual Service Edge. The default status is **Enabled**.
-
**Deployment Status**: Choose either **In Production** or **Trial**. The default deployment status is **In Production**.
**In Production** represents Virtual Service Edge instances deployed for production purposes, and **Trial** represents Virtual Service Edge instances deployed for internal uses or testing purposes.
The trial Virtual Service Edge instances are upgraded first during a maintenance window, followed by production Virtual Service Edge instances. This setting does not affect the behavior, functionality, or performance of the Virtual Service Edge instance, and it helps Zscaler prioritize production Virtual Service Edge instances over trial if an issue or a bug affects Virtual Service Edge instances.
- **Your Used Virtual Service Edges**: You can see the total number of Virtual Service Edges as well as the available number of subscriptions. You can't modify this field.
- **Proxy IP Address**: Enter the IP address to which you’ll forward the traffic. All user and server workload traffic is forwarded to the proxy IP address of the Virtual Service Edge. If the Virtual Service Edge has to receive and service traffic from users or workloads over the internet, ensure that this IP address has access to the internet as well as users.
- **Subnet Mask**: Enter the corresponding subnet mask.
- **Default Gateway**: Enter the IP address of the default gateway to the internet.
- **Load Balancer IP Address**: Appears only when **Cluster** is selected as the deployment mode. Enter the IP address of the load balancer.
-
**Deployment Mode**: Select either **Cluster **or **Standalone **if you have the VMware ESXi platform. Otherwise, select only **Standalone**.
If clustering fault tolerance is required, ensure to have an external load balancer for **Standalone** deployment.
-
**IPSec Local Termination**: Enable this option to terminate IPSec traffic from the client at the Virtual Service Edge node. By default, this option is disabled.
If you select the deployment mode as **Cluster**, this option becomes read-only and displays the actual status of IPSec Local Termination of the Virtual Service Edge in the cluster. If you want to change the IPSec Local Termination status of the Virtual Service Edge in a cluster, you can do it from the **Administration** > **Virtual Service Edges** > **Virtual Service Edge Clusters** page. To learn more, see [Adding Virtual Service Edge Clusters](/zia/adding-virtual-service-edge-clusters).
[See image.](#add-vzen-instance)
-
**Zscaler Initiated On-Demand Support Tunnel**: Enable this option to allow Zscaler to establish a support tunnel whenever required. This option is disabled by default.
If this option is enabled, you cannot establish a support tunnel from the ZIA Admin Portal. Also, the **Establish Support Tunnel** option is grayed out.
-
**Establish Support Tunnel**: Enable this option to allow the service to establish a support tunnel for Zscaler Support to access the Virtual Service Edge. This option is disabled by default.
This option is available only when the **Zscaler Initiated On-Demand Support Tunnel** is disabled.
-
**Virtual Service Edge ID**: You can see the Virtual Service Edge ID used by Zscaler to identify and access the Virtual Service Edge using the established support tunnel.
[See image.](#add-vse-support-info)
- Click **Save**.
- [Activate the change](/zia/saving-and-activating-changes-admin-portal).
Azure reserves five IP addresses within each subnet. These are x.x.x.0-x.x.x.3 and the last address of the subnet. x.x.x.1-x.x.x.3 is reserved in each subnet for Azure services.
- x.x.x.0: Network address.
- x.x.x.1: Reserved by Azure for the default gateway.
- x.x.x.2, x.x.x.3: Reserved by Azure to map the Azure DNS IPs to the VNet space.
- x.x.x.255: Network broadcast address.
[]To download a Virtual Service Edge certificate:
- Go to **Administration **>** Virtual Service Edges**.
-
In the** SSL Certificate** column, click **Download** for the [Virtual Service Edge that you added](/zia/adding-virtual-service-edge-instances) previously, and then save the certificate.
[See image.](#Image-download-ssl)
If you're downloading multiple certificates, you might want to change the certificate name so that you can differentiate between them. For example, if the Virtual Service Edge instances in a cluster are called VSE1 and VSE2, you can rename the certificate's ZIP files to VSE1.zip and VSE2.zip.
[]![Screenshot of the ZIA Add Virtual Service Edge window with IPSec Local Termination](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/adding-virtual-service-edge-instances/ZIA-Add-Virtual-Service-Edge-Deployment-Status.png)
[]![Screenshot of the ZIA Add Virtual Service Edge window with Support Information](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/adding-virtual-service-edge-instances/ZIA-Add-Virtual-Service-Edge-Support-Information.png)
[]![Screenshot of the SSL Certificate column and download link on the Virtual Service Edge page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/downloading-virtual-service-edge-certificates/ZIA-Virtual-Service-Edge-SSL-Certificate-v6.2.png?1662123037)
[]Create a new virtual machine (VM) instance using the Virtual Service Edge image:
- Log in to the [Azure Portal](https://portal.azure.com/).
- Create a virtual network.
- In the Azure portal, go to **Home** > **Resource Groups** and select your resource group.
-
In the left-side navigation, click **Virtual networks**.
Alternatively, on the **Home** page, in the **Search** field, search for the virtual networks.
-
On the **Virtual networks** page, click **Create**.
The **Create virtual network** page appears.
- On the **Create virtual network** page, on the **Basics** tab:
- **Resource group**: Select the desired resource group.
- **Virtual network name**: Enter a name for the virtual network.
- **Region**: Select the region that has your Virtual Service Edge image.
-
Go to the **IP addresses** tab.
By default, the subnet is 16 and it's named `default`. If required, click **Edit** icon for the subnet and make the necessary changes.
- Click **Review + create **to validate the network and review the configuration.
-
Click **Create** to create the virtual network.
[See image.](#azure-vse-vnet)
- Create public IP addresses for the service network interface.
-
In the left-side navigation, click **Public IP addresses**.
Alternatively, on the **Home** page, in the **Search** field, search for the public IP addresses.
-
On the **Public IP addresses** page, click **Create**.
The **Create public IP address** page appears.
- On the **Create public IP address** page, on the **Basics** tab:
- **Resource group**: Select the desired resource group.
- **Region**: Select the region that has your Virtual Service Edge image.
- **Name**: Enter a name for the public IP address.
- **IP Version**: Select **IPv4**.
- **SKU**: Select **Standard**.
- **IP address assignment**: Select **Static**.
- Click **Review + create **to validate the public IP address and review the configuration.
-
Click **Create** to create the public IP address.
[See image.](#azure-public-ip)
- Create a service network interface (NIC).
-
In the left-side navigation, click **Network interfaces**.
Alternatively, on the **Home** page, in the **Search** field, search for the network interfaces.
-
On the **Network interfaces** page, click **Create**.
The **Create** **network interface** page appears.
- On the **Create** **network interface** page, on the **Basics** tab:
- **Resource group**: Select the desired resource group.
- **Name**: Enter a name for the network interface.
- **Region**: Select the region that has your Virtual Service Edge image.
- **Virtual network**: Select the virtual network created in the preceding step.
- **Subnet**: Select the subnet created in the preceding step.
- **IP Version**: Select **IPv4**.
- **Private IP address assignment**: Select **Dynamic**.
- Click **Review + create **to validate the NIC and review the configuration.
-
Click **Create** to create the NIC.
[See image.](#azure-create-nic)
-
Create a VM.
-
On the **Home** page, in the **Search** field, search for Marketplace and select it.
[See image.](#azure-home-page)
-
On the **Marketplace** page, in the **Search** field, search for [`Zscaler Internet Access Virtual Service Edge`](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/zscaler1579058425289.preview-zscaler-zia-vse?tab=overview).
[See image.](#azure-marketplace)
- Select the **Zscaler Internet Access Virtual Service Edge** VM.
-
On the **Zscaler Internet Access Virtual Service Edge** VM page, click **Create**.
[See image.](#azure-zia-vse-vm)
- On the **Create** **a** **virtual machine** page, on the **Basics** tab:
- **Resource group**: Select the desired resource group.
- **Virtual machine name**: Enter a name for the VM.
- **Region**: The region of the VM is automatically populated. You can't edit it.
- **Availability options**: Select either **No infrastructure redundancy required **(for VMs without Azure Load Balancer (LB)) or **Availability set **(for VMs with Azure LB).
- **Security type**: The security type is automatically set to **Standard**. You can't edit it.
- **Image**: The image is set to **Zscaler Internet Access Virtual Service Edge - x64 Gen1** by default. You can't edit it.
- **VM architecture**: The architecture is set to **x64 **by default. You can't edit it.
- **Size**: Select **Standard_A4m_v2**.
- **Authentication type**: Select either **SSH public key **or **Password**.
- **Username**: Enter `zsroot`.
-
**SSH public key source**: Select **Generate new key pair**.
This field appears only if you select **SSH public key**.
-
**Key pair name**: Enter the key pair name.
This field appears only if you select **SSH public key**.
-
**Password**: Enter the password.
This field appears only if you select **Password**.
- **Public inbound ports**: Select **Allow selected ports**.
- On the **Create** **a** **virtual machine** page, on the **Networking** tab:
- **Virtual network**: The virtual network created in the preceding step is automatically populated.
- **Subnet**: The subnet created in the preceding step is automatically populated.
- **Public IP**: Click **Create new **to create a public IP.
- **Name**: Enter the name for the public IP.
- **SKU**: Select **Standard**.
- **Assignment**: Select **Static**.
- **NIC network security group**: Select **Basic**.
- **Public inbound ports**: Select **Allow selected ports**.
- **Select inbound ports**: Select **SSH (22)**.
- Click **Review + create **to validate the VM and review the configuration.
-
Click **Create** to create the VM.
The **Generate new key pair** window appears.
- In the **Generate new key pair **window, click **Download private key and create resource**.
[See image.](#azure-create-vm)
The VM deployment takes about two minutes.
- After the VM is deployed to the resource group that has your Virtual Service Edge image, click **Go to resource**.
- Click **Stop** to stop the VM.
- After the VM is stopped, go to the **Network settings** of the VM.
-
On the **Network settings** page, click **Attach network interface** to attach the second NIC created in the preceding step.
[See image.](#azure-attach-nic)
- Attach the public IP address to the service NIC.
- Go to the **Network interfaces** page, locate and select the NIC created in the preceding step.
-
Click **IP configurations** in the **Settings** section.
[See image.](#azure-nic-ip-config)
- Locate and select the public IP created in the preceding step.
- In the **Edit IP configuration** window:
- **Associate public IP address**: Select the checkbox.
- **Public IP address**: Select the public IP created in the preceding step.
-
Click **Save**.
[See image.](#edit-ip-config)
- Go to the **Virtual machines** page, locate and select the VM created in the preceding step.
- Click **Start** to start the VM.
[See image.](#resource_group_image)
-
Manually configure the network security groups' settings. You can find more details about the outbound connection requirements at https://config.zscaler.com/<zscaler cloud name>/zia-v-sedge. The <zscaler cloud name> can be found in the URL you use to log in to the ZIA Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge. To connect to your instance via SSH, you're required to open port 22 for inbound connections. In production, you should authorize only a specific IP address or range of addresses to access your instance and not use 0.0.0.0. If you use a NAT gateway, you can disassociate and delete the two public IP addresses.
[See image.](#network_security_group_image)
[]![Screenshot of Azure Create Virtual Network Page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-VSE-Virtual-Network.png)
[]![Screenshot of Azure Create Public IP Address Page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Public-IP-Address.png)
[]![Screenshot of Azure Network Interface Page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Network-Interface-Create-NIC.png)
[]![Azure Create Virtual Machine Page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-VM-Create-VM.png)
[]![Azure Edit IP Configuration Page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-microsoft-azure/ZIA-Azure-Resource-Group-Edit-IP-Config.png)
[]![Azure VM Network Settings Page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-microsoft-azure/ZIA-Azure-VM-Network-Settings-Attach-Network-Interface.png)
[]![Screenshot of Azure Resource Group IP Configuration Page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Resource-Group-IP-Config.png)
[]![Azure Portal Home page](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Microsoft-Azure-Portal-Home-page.png)
[]![Azure Portal Marketplace Page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-microsoft-azure/Microsoft-Azure-Portal-Marketplace-Page.png)
[]![Azure Portal Marketplace Page](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-microsoft-azure/Microsoft-Azure-Portal-Marketplace-Page-ZIA-VSE-VM.png)
[]![Screenshot of the Resource Group page in the Azure Portl](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/Azure-Resource-Group-Resources.png)
[]![Screenshot of the Zscaler Network Security Group settings in Azure](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/zia-azure-vzen-inbound-outbound.PNG)
[]Zscaler performs ICMP and HTTP monitoring from the Azure LB to the Virtual Service Edge to monitor the health of the Virtual Service Edge and ensure that traffic is distributed appropriately. For health probes to work, you must create a Firewall Filtering policy rule to allow Azure proxy and load balancer IP addresses.
To create a Firewall filtering rule to bypass Azure LB IP addresses:
- Go to **Policy** > **Firewall Control**.
- Click **Add Firewall Filtering Rule**.
The **Add Firewall Filtering Rule **window appears.
- In the **Source IP** tab, under **IP Addresses** add the following IP addresses from Azure:
- Proxy IP address
- Load balancer IP address
- Under **Action**, select **Allow**.
- Complete the configuration for the new rule as detailed in [Configuring Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy).
[]The following Virtual Service Edge configuration steps are run through an SSH terminal connection.
To configure the Virtual Service Edge on the VM:
- Configure the network.
- Select the Virtual Service Edge VM and click either **Power On** or **Power On the virtual machine**.
-
In the Azure Web Console, enter the following credentials in the FreeBSD command prompt to log in:
Username: `zsroot`
Password: `zsroot`
The following guidelines apply:
- Zscaler strongly recommends that you change this default password by running the `passwd` command.
- Direct root login is not permitted. Administrators must use the `sudo` utility to run a command with higher privileges.
-
Run the `sudo vzen configure-network` command, and then enter the following details:
- Address of the DNS server (e.g., 10.84.0.100) used for name resolution of Zscaler cloud domains and also for domain names in the proxy traffic.
- Hostname of the Virtual Service Edge.
The Virtual Service Edge management IP, gateway IP for management, and resolvers are obtained from DHCP.
This command does not allow you to modify the management IP and gateway IP.
- Install the SSL certificate of the Virtual Service Edge instance. This is the certificate that you downloaded from the ZIA Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service.
When you configure a Virtual Service Edge, ensure that you upload the correct certificate for the Virtual Service Edge instance.
To install the SSL certificate of the Virtual Service Edge instance:
- Navigate to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- In the Azure Web Console, log in with the following credentials:
Username: zsroot
Password: zsroot
- Go to the Azure Web Console or use SSH to connect to the management IP address.
-
Run the command, sudo vzen install-cert <cert-bundle.zip>.
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
- (Optional) if you want to use an SNMP management system to monitor the Virtual Service Edge cluster, [enable SNMP for Virtual Service Edge](/zia/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
- Run the command, sudo vzen snmp-admin-configure.
- Enter a user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries only from this user name.
- Enter the password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify the authentication protocol that the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method that the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
- Run the command, sudo vzen snmp-trap-configure.
- When asked which traps you want to configure, specify v3 traps.
- Enter the IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- Enter a user name for the SNMP management system.
- Enter the password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify the authentication protocol that the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method that the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
- Download the Virtual Service Edge build and start the Virtual Service Edge.
- Go to the Azure Web Console or use SSH to connect to the management IP address.
- Run the following command to download the Virtual Service Edge build: sudo vzen download-build.
The initial build is around 1 GB, so it may take a while depending on your Internet connection. The downloaded build is automatically installed. The Virtual Service Edge automatically starts after the installation is complete.
- Verify the configuration.
- Go to the Azure Web Console or use SSH to connect to the management IP address.
- Run the sudo vzen status command.
The output should display that the Virtual Service Edge service and load balancer are running.
[See image.](#Image9)
- Run the sudo vzen troubleshoot connection | grep 9422 command.
The output should display an established connection.
[][![Screenshot of SSH port showing that the VZEN service and load balancer are running](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/virtual-zens/how-do-i-configure-vzen-clusters/ssh_and_vzen_status_screenshot.png)
]
[]To create an Azure LB in the resource group:
- In the Azure portal, go to **Home** > **Resource Groups** and select your resource group.
- Click **Add **> **Add Load Balancer**.
Alternatively, on the **Home** page, in the **Search** field, search for the load balancer.
- On the **Create Load Balancer** page:
- **Subscription**: Select your subscription.
- **Resource group**: Select the resource group in which you want to create the load balancer.
- **Name**: Enter a load balancer name.
- **Region**: Enter the same region as the Virtual Service Edge.
- **Type**: Select either **Internal** (for private IP) or **Public **(for public IP)** **option.
- **SKU**: Select the **Standard** option.
- **Public IP address**: Select **Create new**. If you have an existing Public IP that you would like to use, select **Use existing**.
-
**Public IP address name**: Enter a public IP address name.
The public IP addresses of the VMs should be according to the SKU selection. By default, the VMs are created with the Standard SKU public IP addresses.
- **Assignment**: Select **Static**.
- **Add a public IPv6 address**: Select **No**.
- In the **Review + create** tab, click **Create**.
[]To create a backend pool and link Virtual Service Edge VMs to it:
- In the load balancer, click **Backend pools**.
-
Click **Add**.
The **Add backend pool** page appears.
- On the **Add backend pool** page:
- **Name**: Enter a backend pool name.
- **Virtual network**: Select the virtual network in which the Virtual Service Edge VMs and load balancers are created.
- **IP version**: Select **IPv4**.
-
**Associate to**: Select **Virtual machine**.
- **Virtual Machine**: Select the Virtual Service Edge VM that you want to link to the backend pool.
- **IP address**: Select the corresponding service IP address.
You can associate up to 500 virtual machines to a backend pool, provided they are in the same availability set.
- Click **Add**.
[]To create health probes for ports:
- In the load balancer, click **Health probes**.
-
Click **Add**.
The **Add health probe** page appears.
- On the **Add health probe** page:
- **Name**: Enter a health probe name.
- **Protocol**: Select the protocol.
- **Port**: Enter the port number that you want to monitor.
- **Interval**: Enter the interval in seconds between each probe attempt.
- **Unhealthy threshold**: Enter the consecutive number of probe failures that must occur before the Virtual Service Edge VM is considered unhealthy.
- Click **Ok**.
[]To create load balancing rules:
- In the load balancer, click **Load balancing rules**.
-
Click **Add**.
The **Add load balancing rule** page appears.
- On the **Add load balancing rule** page:
- **Name**: Enter a load balancing rule name.
- **IP Version**: Select **IPv4**.
- **Frontend IP address**: Select the load balancer's frontend IP address.
- **Protocol**: Select the protocol.
- **Port**: Enter the same port number that is exposed in the health probe.
- **Backend port**: Enter the same port number that is exposed in the health probe.
- **Backend pool**: Select the backend pool.
- **Health probe**: Select the health probe.
- **Session persistence**: Select a session persistence value based on your requirement. The values can be **None**, **Client IP**, or **Client IP and protocol**.
- **Idle timeout (minutes)**: Don't make any changes to the default value, **4**.
- **Floating IP (direct server return)**: Don't make any changes to the default value, **Disabled**.
- Click **Ok**.
[]To create availability sets in your Azure account:
- In the Azure Web Console, go to **Home** > **Resource Groups** and select your resource group.
- Click **Add **> **Availability sets**.
Alternatively, on the **Home** page, in the **Search** field, search for the availability sets.
-
On the **Availability sets** page, click **Add**.
The **Create availability sets** page appears.
- On the **Create availability sets** page:
- **Subscription**: Select your subscription.
- **Resource group**: Select the resource group in which you want to create the availability sets.
- **Name**: Enter a name for the availability sets.
- **Region**: Select the region.
- **Fault domains**: Select the number of Virtual Service Edge VMs in a fault domain.
- **Update domains**: Select the number of Virtual Service Edge VMs in an update domain.
- **Use manage disks**: Select **No (Classic)**.
- Click **Review + create**.
[]To create Virtual Service Edge VMs using the deployment script with the availability set parameter:
-
Populate the values in conf_file.txt.
- [See the table for the description of each value.](#avset-value_table)
- [See sample file.](#avset-sample-file)
Ensure that you associate all Virtual Service Edge VMs with availability set to the same location.
-
Run the following script.
deployment_script.ps1 config_file.txt
- [See sample deployment script file.](#avset-deployment-script-sample-file)
-
In the pop-up window, enter your Azure credentials to run the script.
[See image.](#avset-Azure_image2)
-
After completing the previous steps, verify that you have the following resources:
- A clone of the two VHD files in the destination container.
- Two public IPs.
- Two NICs.
- A VNet/Subnet.
- A network security group.
- Virtual Service Edge VM.
[See image.](#avset-resource_group_image)
-
Manually configure the network security groups' settings. By default, the script creates the outbound connection rules to any IP address. You can find more details about the outbound connection requirements at https://config.zscaler.com/<zscaler cloud name>/zia-v-sedge. The <zscaler cloud name> can be found in the URL you use to log in to the ZIA Admin Portal. For example, if you log in to admin.zscaler.net, then go to https://config.zscaler.com/zscaler.net/zia-v-sedge. To connect to your instance via SSH, you're required to open port 22 for inbound connections. In production, you should authorize only a specific IP address or a range of IP addresses to access your instance and not use 0.0.0.0. If you use a NAT gateway, you can disassociate and delete the two public IP addresses.
[See image.](#avset-network_security_group_image)
- Ensure that the deployment script completes the following:
- Optionally, creates 2 public IP addresses.
- Associates the VM to an existing/new virtual network (VNet) and subnet.
- Creates and associates a new network security group to the VM.
- Copies the OS and data disk VHD files to a final storage account from which the VM is provisioned. If you are using PowerShell, then the script clones the VHD files. This ensures that the original VHD files aren't attached to the VM and can be used to start additional Virtual Service Edge VMs in the future. You can delete the original VHD files, if necessary.
- Attaches the OS and data disks to the Virtual Service Edge VM.
- Starts the Virtual Service Edge VM.
[]
| Value | Description |
| ----- | ----------- |
| name | Name of the instance. |
| location | Location to deploy the instance. |
| rgname | Name of the destination resource group containing the VM instance. |
| createrg | N if the resource group is allocated already. Y if it needs to be provisioned. |
| storename | Name of the destination storage account to create the instance disks. |
| createstorage | N if the storage account is already provisioned. Y if it needs to be provisioned. |
| vnetname | Name of the virtual network to which this instance is associated. Creates a VNet if the one with a specified name doesn't exist. |
| vnetprefix | IP address range in CIDR for the virtual network. |
| vnetrg | If the virtual network is in a different resource group, specify the resource group name here, or else remove this line from the config. Though the network and VM instance can be in different resource groups, they should be in the same region. |
| mgmtsubnetname | Name of the subnet hosting management interface. |
| mgmtsubnetprefix | CIDR prefix for the management interface subnet. |
| svcsubnetname | Name of the subnet in the virtual network to which the service interface is associated. |
| svcsubnetprefix | CIDR prefix for the subnet of the service interface. |
| niccount | Number of NICs to attach to the instance. You can have 2 unless advanced deployment is in place. |
| vmsize | Instance type according to azure machine specifications. |
| avset | Availability set for VM provisioning, ignore if not used. |
| srcOsURI | URI of the OS disk copied in the previous step. <Path to copied OS disk, the disk blob copied from Zscaler including the vhd file name> |
| dstStorageURI | URI of the storage account to which the OS disk is copied. The URI should not include the ending forward slash. |
| dstContainer | The name of the container to which the OS disk VHD file is copied. |
[]name=vzen57shaunak_aug29
location=westus
rgname=shaunakdesh
createrg=n
storename=57vzenshaunak
createstorage=n
vnetname=57vzenshaunak_2
vnetprefix=10.2.0.0/16
mgmtsubnetname=57vzensub_2
mgmtsubnetprefix=10.2.0.0/24
svcsubnetname=57vzensub_3
svcsubnetprefix=10.2.0.0/18
niccount=2
vmsize=Standard_A4m_v2
avset=vzenshaunak_set
dstStorageURI=https://57vzenshaunak.blob.core.windows.net
dstContainer=57vzenshaunak1
srcOsURI=https://57vzenshaunak.blob.core.windows.net/57vzenshaunak1/zsos24_vse_rev3.vhd
[]#Test if the azure powershell modules are present on the system
$scmd="Connect-AzAccount"
$cmdout=Get-Command $scmd -eA SilentlyContinue -EV $serr -OV $sout
if(!$cmdout.CommandType) {
echo "Required powershell modules are missing. Please install the azure modules and retry"
exit
}
#Sign in for this session
Connect-AzAccount
#Fetch the config file to be loaded
if( $args[0] -ne $null ){
$filename=$args[0]
}
else
{
$filename="./config.txt"
}
$SubSelect = 'n'
Set-Item Env:\SuppressAzurePowerShellBreakingChangeWarnings "true"
Do {
$subs=Get-AzSubscription
echo "Listing available subscriptions in your account"
$subid=0
$ProvisionSub=99999
foreach ($sub in $subs) {
echo "Subscription $subid :"
echo $sub
$subid++
}
if($subid -ge 1)
{
$ProvisionSub=Read-Host -Prompt "Select one of the above for provisioning"
}
else
{
$ProvisionSub=0
}
echo "Selected subscription for provisioning :"
echo $subs[$ProvisionSub]
$SubSelect=Read-Host -Prompt "Enter `"y`" to continue with this subscription or `"n`" to choose again"
} While($SubSelect -eq 'n' -or $SubSelect -eq 'N')
if($SubSelect -ne 'y' -and $SubSelect -ne 'Y') {
echo "You did not choose a subscription to deploy in, script will exit now"
exit
}
$subscription=$subs[$ProvisionSub]
echo "Script will continue to provision in the selected subscription $subscription "
Set-AzContext -SubscriptionId $subscription.Id
echo "Azure Subscription for current session set to the following"
Get-AzContext
$select=Read-Host -Prompt "Do you wish to continue(y/n):"
if($select -ne 'y' -or $select -ne 'Y')
{
echo "Script terminating per user input"
exit
}
echo "Provisioning will continue with the selected subscription"
if ( -not (Test-Path $filename))
{
echo "Config file not found at $filename"
exit
}
else
{
echo "Found the configuration file, populating deployment variables from $filename"
}
#Sanity run, set this to n when running actual creation
$sanityrun='n'
#Initialize config entries from the configuration file provided
$name=''
$rgname=''
$niccount=1
$rgcreate="n"
$storename=''
$mgmtsubnetname=''
$svcsubnetname=''
$vnetname=''
$vnetprefix=''
$mgmtsnetprefix=''
$svcsubnetprefix=''
$vmsize=''
$location=''
$osimage=''
$dstStorageURI=''
$datadisk="Copy"
$datadisksize=0
$datadisksrcURI=''
$osdisksrcURI=''
$dataimageURI=''
$dstContainer=''
$vnetrgname=''
$avsetname=''
$avcheck="No"
#Parse the config file provided and load the values
foreach ($line in Get-Content $filename) {
if($line -match "^#.*") {
#Commented
continue
}
if( [string]::IsNullOrWhitespace($line)) {
#Empty line
continue
}
$entries=$line.split("=",2,[StringSplitOptions]'RemoveEmptyEntries')
#$entries=$line.split("=")
$e1=$entries[0]
$e2=$entries[1]
Write-Host $e1 $e2 -Separator ","
$key=$e1.Trim()
$value=$e2.Trim()
#echo "Got entries" $entries[0] "->" $entries[1]
if($key -eq "name") {
$name=$value
continue
}
if($key -eq "avset") {
$avsetname=$value
continue
}
if($key -eq "rgname") {
$rgname=$value
continue
}
if($key -eq "vnetrg") {
$vnetrgname=$value
continue
}
if($key -eq "createrg") {
$rgcreate=$value
continue
}
if($key -eq "storename") {
$storename=$value
continue
}
if($key -eq "createstorage") {
$storecreate=$value
continue
}
if($key -eq "mgmtsubnetname") {
$mgmtsubnetname=$value
continue
}
if($key -eq "svcsubnetname") {
$svcsubnetname=$value
continue
}
if($key -eq "vnetname") {
$vnetname=$value
continue
}
if($key -eq "niccount") {
$niccount=$value
continue
}
if($key -eq "vnetprefix") {
$vnetprefix=$value
continue
}
if($key -eq "mgmtsubnetprefix") {
$mgmtsnetprefix=$value
continue
}
if($key -eq "svcsubnetprefix") {
$svcsubnetprefix=$value
continue
}
if($key -eq "vmsize") {
$vmsize=$value
continue
}
if($key -eq "location") {
$location=$value
continue
}
if($key -eq "dstStorageURI") {
$dstStorageURI=$value
continue
}
if($key -eq "srcOsURI") {
$osimage=$value
continue
}
if($key -eq "osuri") {
$osdisksrcURI=$value
continue
}
if($key -eq "sastok") {
$sastok=$value
continue
}
if($key -eq "attach") {
$attachdisk=$value
continue
}
if($key -eq "dstContainer") {
$dstContainer=$value
continue
}
}
echo "Name=$name Rgname=$rgname Location=$location"
if($vnetrgname -eq '')
{
$vnetrgname=$rgname
}
$loclist=Get-AzLocation
$loccheck=0
foreach($loc in $loclist.Location){
if($loc -like $location){
$loccheck=1
}
}
if($loccheck -eq 1){
Write-Host "The virtual instance will be deployed in $location"
} else {
Write-Error -Message "The location provided in configuration file :- $location is not a valid input. Please correct the same and rerun the script"
exit
}
#Fetch resource group and storage account configured in the conf file
$rg=Get-AzResourceGroup -ResourceGroupName $rgname -ev notPresent    -ea 0
$rgcreatechoice='n'
$storecreatechoice='n'
#If resource group does not exist, provision it before proceeding
if($rg.ProvisioningState -ne "Succeeded") {
echo "The resource group $rgname does not exist, do you wish to create it in $location(y/n):"
$rgcreatechoice=Read-Host
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y') {
echo "Creating resourcegroup $rgname in $location"
$rg=New-AzResourceGroup -Name $rgname -Location $location
if($rg.ProvisioningState -ne "Succeeded") {
echo "Error creating resource group. Script will exit now"
exit
}
echo "Created resource group. Continuing to provision the storage account"
$storecreatechoice='y'
}else
{
echo "Resource group specified does not exist in the selected subscription. Exiting"
exit
}
}
if($rgcreatechoice -eq 'n')
{
$store=Get-AzStorageAccount -ResourceGroupName $rgname -Name $storename -ev stnotPresent -ea 0
if($store.ProvisioningState -ne "Succeeded"){
echo "The Storage account provided `"$storename`" doesn't exist in $rgname"
echo "Do you wish to provision the storage account now(y/n):"
$storecreatechoice=Read-Host
if($storecreatechoice -ne 'y' -or $storecreatechoice -ne 'Y'){
echo "VM creation cannot continue without storage account. Exiting."
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y'){
echo "Resource group $rgname was provisioned in $location while script executed"
echo "Please delete it if no longer in use"
}
exit
}
}
}
$storetype='Standard_LRS'
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Preparing to provision storage account $storename in resource group $rgname"
echo "Do you need geo redundant store or locally reduntant store"
echo "Enter 1 for geo reduntant(Standard_GRS) or 2 for locally reduntant(Standard_LRS), if you need"
echo "other options, enter `"n`" to exit now and provision the storage account manually "
echo "Enter your choice: "
$storetypechoice=Read-Host
if($storetypechoice -eq 1)
{
echo "Store type set to Standard_GRS"
$storetype="Standard_GRS"
}
if($storetypechoice -eq 2)
{
echo "Store type set to Standard_LRS"
$storetype="Standard_LRS"
}
if($storetypechoice -eq 'n' -or $storetypechoice -eq 'N')
{
echo "Exiting deployment as per user input"
exit
}
echo "Creating storage account. This is a long operation. Please wait till it completes."
$store=New-AzStorageAccount -ResourceGroupName $rgname -Name $storename -Location $location -SkuName $storetype
}
if($store.ProvisioningState -ne "Succeeded")
{
echo "Storage account creation did not complete successfully. Exiting deployment"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y'){
echo "Resource group $rgname was provisioned in $location. Please delete it manually if not needed"
}
exit
}else
{
#Check if the container exists in target account
$containercheck=Get-AzStorageContainer -Name $dstContainer -Context $store.Context -ErrorAction SilentlyContinue
if($containercheck.Name -ne $dstContainer)
{
#Create Storage container with the provided name
echo "Storage account creation successful, creating container for disk storage."
New-AzStorageContainer -Name $dstContainer -Permission Off -Context $store.Context
}
}
#Availability set check
if($avsetname -ne '') {
$avset=Get-AzAvailabilitySet -Name $avsetname -ResourceGroupName $rgname -ErrorAction SilentlyContinue
if($avset.Name -eq $avsetname) {
if($avset.Managed) {
echo "This availability set is not supported by the vm type being deployed,"
echo "Please use a classic availability set to deploy this VM"
exit
}
echo "Availability set present, vm instance will be provisioned within availability set"
$avcheck="Yes"
sleep 10
}
}
if($avcheck -eq "No" -and $avsetname -ne '') {
echo "Creating availability set for the VM"
$avset=New-AzAvailabilitySet -Name $avsetname -ResourceGroupName $rgname -Location $location -Sku classic
sleep 10
if($avset.Name -eq $avsetname) {
echo "Created availability set, deployment in progress"
sleep 5
}else
{
echo "Deployment will stop now, failed to create availability set"
echo "To deploy, create a classic availability set in the required resource group"
echo "And execute the script again"
exit
}
$avcheck="Yes"
}
#Network configuration for the virtual machine
#create the interface names
$nicnames=@()
if($niccount -gt 0) {
echo "Creating $niccount nic names"
for($i=0; $i -lt $niccount; $i++) {
$nicname=$name+"_nic_"+$i
$nicnames+=$nicname
}
}else {
echo "The vm needs at least 1 interface to be configured, current value is $niccount"
echo "Script will exit now. Please correct the config file as per recommendations and try again"
exit
}
$ipnames=@()
if($niccount -gt 0) {
echo "Creating $niccount ip names"
for($i=0; $i -lt $niccount; $i++) {
$ipname=$name+"_ip_"+$i
$ipnames+=$ipname
}
}
if($vnetrgname -ne $rgname){
#Validate the resource group for provisioning vnet exists
}
$vnet=Get-AzVirtualNetwork -Name $vnetname -ResourceGroupName $vnetrgname -ev vnetError -ea 0
$vnetcreate='n'
if($vnet.ProvisioningState -eq "Succeeded")
{
echo "VirtualNetwork $vnetname exists, checking for subnet"
$mgmtsnet=Get-AzVirtualNetworkSubnetConfig -Name $mgmtsubnetname -VirtualNetwork $vnet -ev snetPresent -ea 0
$svcsnet=Get-AzVirtualNetworkSubnetConfig -Name $svcsubnetname -VirtualNetwork $vnet -ev snetPresent -ea 0
}else
{
echo "Do you wish to create the Virtual Network as per the configuration provided"
$vnetcreate=Read-Host -Prompt "Enter y/n"
if($vnetcreate -ne 'y' -and $vnetcreate -ne 'Y')
{
echo "Virtual Network configuration for the VM instance is not provisioned"
echo "This script will now exit"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
echo "New Virtual network $vnetname with prefix $vnetprefix will be created in $location"
$vnetcreate=Read-Host -Prompt "Do you wish to continue (y/n)"
if($vnetcreate -ne 'y' -and $vnetcreate -ne 'Y')
{
echo "Script will exit now as per user input"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
$mgmtsnet=New-AzVirtualNetworkSubnetConfig -Name $mgmtsubnetname -AddressPrefix $mgmtsnetprefix -ev sNetCreate -ea 0
if($mgmtsnetprefix -ne $svcsubnetprefix) {
$svcsnet=New-AzVirtualNetworkSubnetConfig -Name $svcsubnetname -AddressPrefix $svcsnetprefix -ev sNetCreate -ea 0
$vnet=New-AzVirtualNetwork -Name $vnetname -ResourceGroupName $vnetrgname -Location $location -AddressPrefix $vnetprefix -Subnet $mgmtsnet,$svcsnet -ev vNetCreate -ea 0
}
else
{
$vnet=New-AzVirtualNetwork -Name $vnetname -ResourceGroupName $vnetrgname -Location $location -AddressPrefix $vnetprefix -Subnet $mgmtsnet -ev vNetCreate -ea 0
$svcsnet=$mgmtsnet
}
}
if($vnet.ProvisioningState -ne "Succeeded"){
echo "Virtual network creation failed or script was unable to fetch"
echo "the Virtual network configuration. Please check the configuration"
echo "for possible errors and execute the script further"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
$snetcreate='n'
$mgmtsnet=Get-AzVirtualNetworkSubnetConfig -Name $mgmtsubnetname -VirtualNetwork $vnet -ev sNetPresent -ea 0
if($mgmtsnet.ProvisioningState -ne "Succeeded") {
echo "A subnet $mgmtsubnetname with the required configuration $mgmtsnetprefix"
echo "Was not found in $vnetname "
echo "The instance provisioning will exit if subnet is not created"
$snetcreate=Read-Host -Prompt "Do you wish to create it now (y/n)"
if($snetcreate -ne 'y' -and $snetcreate -ne 'Y') {
echo "You have chosen not to provision the subnet"
echo "The script will exit now"
echo "Please make sure all prerequisites are met and "
echo "execute the script to provision the instance"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
$mgmtsnet=New-AzVirtualNetworkSubnetConfig -Name $subnetname -AddressPrefix $snetprefix -ev sNetCreate -ea 0
Set-AzVirtualNetworkSubnetConfig -Name $mgmtsubnetname -VirtualNetwork $vnet -ev sNetAssign -ea 0
}
$svcsnet=Get-AzVirtualNetworkSubnetConfig -Name $svcsubnetname -VirtualNetwork $vnet -ev sNetPresent -ea 0
if($svcsnet.ProvisioningState -ne "Succeeded") {
echo "A subnet $svcsubnetname with the required configuration $svcsnetprefix"
echo "Was not found in $vnetname "
echo "The instance provisioning will exit if subnet is not created"
$snetcreate='n'
$snetcreate=Read-Host -Prompt "Do you wish to create it now (y/n)"
if($snetcreate -ne 'y' -and $snetcreate -ne 'Y') {
echo "You have chosen not to provision the subnet"
echo "The script will exit now"
echo "Please make sure all prerequisites are met and "
echo "execute the script to provision the instance"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
$svcsnet=New-AzVirtualNetworkSubnetConfig -Name $svcsubnetname -AddressPrefix $svcsnetprefix -ev sNetCreate -ea 0
Set-AzVirtualNetworkSubnetConfig -Name $svcsubnetname -VirtualNetwork $vnet -ev sNetAssign -ea 0
}
if(($mgmtsnet.ProvisioningState -ne "Succeeded") -or ($svcsnet.ProvisioningState -ne "Succeeded")){
echo "Subnet provisioning failed"
echo "Deployment cannot continue"
if($rgcreatechoice -eq 'y' -or $rgcreatechoice -eq 'Y' ){
echo "Resource group $rgname was provisioned in $location "
echo "It can be removed if not in use"
}
if($storecreatechoice -eq 'y' -or $storecreatechoice -eq 'Y'){
echo "Storage account $storename was provisoned by this script"
echo "It can be removed if not used"
}
exit
}
if($sanityrun -eq 'y'){
Write-Host "Exiting sanity check" -Foreground Green
exit
}
#Start creation of the VM object
echo "Creating the vm object...."
#$cred=Get-Credential
if($avcheck -eq "Yes") {
$vm = New-AzVMConfig -VMName $name -VMSize $vmsize -AvailabilitySetId $avset.Id
}else
{
$vm = New-AzVMConfig -VMName $name -VMSize $vmsize
}
#$vm = Set-AzureRmVMOperatingSystem -VM $vm -Linux -ComputerName $name -Credential $cred
#Create interfaces and ip objects as per config file
$nics=@()
$pip=@()
$pipopt='n'
echo "Do you wish to allocate public ip address to the instance"
$pipopt=Read-Host -Prompt "Enter y or n to proceed"
echo "Generating interface configuration and attaching ip addresses...."
if($pipopt -eq 'y' -or $pipopt -eq 'Y'){
for($i=0; $i -lt $niccount ; $i++) {
$pip=New-AzPublicIpAddress -Name $ipnames[$i] -ResourceGroupName $rgname -Location $location -AllocationMethod Dynamic
#$nic=New-AzureRmNetworkInterface -Name $nicnames[$i] -ResourceGroupName $rgname -Location $location -SubnetId $svcsnet.Id -PublicIpAddressId $pip.Id
if($i -eq 0) {
$nic=New-AzNetworkInterface -Name $nicnames[$i] -ResourceGroupName $rgname -Location $location -SubnetId $mgmtsnet.Id -PublicIpAddressId $pip.Id
$vm = Add-AzVMNetworkInterface -VM $vm -Id $nic.Id -Primary
}else
{
$nic=New-AzNetworkInterface -Name $nicnames[$i] -ResourceGroupName $rgname -Location $location -SubnetId $svcsnet.Id -PublicIpAddressId $pip.Id
}
$vm = Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
echo "Nics = $nics"
}
}
else {
for($i=0; $i -lt $niccount ; $i++) {
if($i -eq 0) {
$nic=New-AzNetworkInterface -Name $nicnames[$i] -ResourceGroupName $rgname -Location $location -SubnetId $mgmtsnet.Id
$vm = Add-AzVMNetworkInterface -VM $vm -Id $nic.Id -Primary
}
else
{
$nic=New-AzNetworkInterface -Name $nicnames[$i] -ResourceGroupName $rgname -Location $location -SubnetId $svcsnet.Id
}
$vm = Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
echo "Nics = $nics"
}
}
#Setting up disks for the VM
clear
echo "Setting up the disks."
$osdiskname=$name+"_"+"osdisk.vhd"
$blob="$dstStorageURI/$dstContainer"
$osDiskUri = "$blob/$osdiskname"
$osimageUri = "$osimage"
echo "Disk info for the VM "
echo "OS Disk : $osdiskname"
echo "Blob : $blob"
echo "OS disk URI : $osDiskUri"
sleep 10
clear
echo "Copying disks to the path"
$storecontext=$store.Context
Start-AzStorageBlobCopy -AbsoluteUri $osimageUri -Context $storecontext -DestContainer $dstContainer -DestBlob $osdiskname
$osstatus=Get-AzStorageBlobCopyState -Context $storecontext -Blob $osdiskname -Container $dstContainer
While($osstatus.Status -ne "Success") {
sleep 20
$osstatus=Get-AzStorageBlobCopyState -Context $storecontext -Blob $osdiskname -Container $dstContainer
if($osstatus.Status -ne "Pending") {
Break
}
}
$vm=Set-AzVMOSDisk -VM $vm -Name $osdiskname -VhdUri $osDiskUri -CreateOption Attach -Linux
#Create the azure Virtual machine
clear
echo "Disk setup completed, vm object generated succesfully. Creating the instance."
New-AzVM -ResourceGroupName $rgname -Location $location -VM $vm -Verbose
[]![Screenshot of the MIcrosoft Azure sign in window](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-azure/zia-azure-nss-credentials.png)
[]![Screenshot of the Resource Group page in the Azure Portl](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/ZIA-AP-Resource-Group-Final.PNG)
[]![Screenshot of the Zscaler Network Security Group settings in Azure](/downloads/zia/traffic-forwarding/service-edges/virtual-zen/configuring-vzen-microsoft-azure/zia-azure-vzen-inbound-outbound.PNG)