# NSS Deployment Guide for Microsoft Azure
Source: https://help.zscaler.com/unified/nss-deployment-guide-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1496676.pdf

Zscaler's [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service) can be deployed via Microsoft Azure. This guide describes the tasks required for NSS deployment, enabling you to stream either web logs or Firewall logs to a security information and event management (SIEM) system.
Prerequisites
Before you begin deployment, contact Zscaler Support to obtain the NSS VHD SAS token and the Azure Virtual Machine (VM) instance type recommendations.
Ensure you have a [subscription](/unified/viewing-subscriptions) to either NSS for Web or NSS for Firewall and review the following specifications and requirements:
- [VM Specs](#vm-specs)
- [Network Specs](#network-specs)
- [Firewall Requirements](#firewall-requirements)
Deploying NSS
To deploy NSS:
- [Step 1: Add an NSS Server and Download the SSL Certificate in the Admin Portal](#step-add-nss-server-download-ssl-certificate)
- [Step 2: Use Azure Storage Explorer or PowerShell to Copy the OS Disk VHD File to Your Azure Storage Account](#step-copy-os-disk-vhd-azure-storage-account)
- [Step 3: Create a Managed Disk and the VM Instance in the Azure Portal](#step-create-managed-disk-vm-instance)
- [Step 4: Configure and Start the NSS on the VM Instance](#step-configure-start-nss)
- [Step 5: Add NSS Feeds for Each NSS](#step-add-nss-feeds)
Zscaler recommends externally restarting the VM from the Azure Portal.
Post-Deployment Tasks
After you have verified your deployment, you can perform additional tasks:
- [Deploying Multiple NSS Virtual Machines for Reliability](#deploying)
- [Configuring Advanced NSS Settings](#Networking)
- [Troubleshooting the NSS](#Troubleshooting)
[]
- 2 CPU cores: NSS uses one core for the control plane and another core for the data plane. Only XEON CPUs are supported.
- Instance memory:
- 8 GB for up to 8K users
- 16 GB for up to 20K users
- 32 GB for up to 50K users
- 48 GB for up to 75K users
- 64 GB for more than 75K users
- Storage account: General Purpose
- []Two network interfaces:
- The first network interface is the management IP address. It is used to control connections to the Zscaler cloud and to make an SSH connection to the NSS VM for configuration and management. You can customize the deployment and define a separate IP address for the SSH connection to the NSS VM.
- The second network interface is the service IP address. It is used for data connections to the Zscaler cloud and the SIEM.
- Two public IP addresses. The two public IP addresses are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
- Bandwidth for log download: 11 Mbps for 10K users is an example average value.
[]It is mandatory to deploy the NSS instance behind a VM network security group. The NSS instance requires only outbound connections to the Zscaler cloud. It doesn't require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, refer to the Zscaler Cloud Configuration Requirements for your Zscaler cloud: https://config.zscaler.com/<Zscaler Cloud Name>/nss.
You can find the name of your Zscaler cloud in the URL you use to log in to the Zscaler service. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/nss](https://config.zscaler.com/zscaler.net/nss).
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
Communication from the NSS to the Zscaler cloud must be excluded from SSL inspection to ensure that the NSS can authenticate to the Nanolog cluster using mutual TLS.
Zscaler does not recommend or support forwarding outbound traffic from the NSS to or through the Internet & SaaS Public Service Edge as this can result in networking, latency, and administration issues.
[]
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
- From the **NSS Servers **tab, click **Add NSS Server**.
The **Add NSS Server** window appears.
- In the **Add NSS Server **window:
- **Name**: Enter a name for the NSS.
-
**Type**: The **NSS for Web **type is selected by default. To configure NSS for firewall logs, select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **Status**: The NSS is **Enabled** by default.
[See image.](#add_nss_server-img)
- Click **Save**.
- Click **Download** in the **SSL Certificate** column of the NSS server that you are configuring, and then save the certificate. You later upload the certificate to the Azure Portal.
[See image.](#ssl_cert_download_img)
[]![Screenshot of the Add NSS Server window in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-azure/ZIA-5.7-NSS-Server.png)
[]![Screenshot of the NSS Servers tab in the ZIA Admin Portal. The Download button under the SSL Certificate column is highlighted.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-azure/ZIA-5.7-NSS-Download-SSL%20Certificate.png)
[]Select the appropriate URLs for your region to ensure the fastest copy time.
-
-
-
| Value | Description |
| ----- | ----------- |
| osdisk | **USA**: https://znssprod.blob.core.windows.net/nss/znss_5_1_osdisk.vhd**Europe**: https://znssprodeu.blob.core.windows.net/nss/znss_5_1_osdisk.vhd**Australia**: https://znssprodau.blob.core.windows.net/nss/znss_5_1_osdisk.vhd |
You can use one of the following methods to copy the VHD file:
- [Azure Storage Explorer](#step-azure-storage-explorer)
- [PowerShell Scripts](#step-powershell-scripts)
[]To copy the VHD file to your Azure storage account:
- Make sure you have two storage accounts with NSS blob containers created in the Azure Portal. One is your template storage account and the other is your final destination storage account. Zscaler recommends you clone the VHD file to your final destination storage account that is associated with the VM. Keep your template storage account in case you'd like to deploy another NSS in the future.
- Download and launch [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/).
- Click on the **Add Account** icon (plug icon).
[See image.](#azure-storage-explorer-plug)
The **Select Connection Method** window appears.
- In this window, select **Storage account or service**.
[See image.](#storage-account-or-service)
- Click **Next**.
- In this window, select **Shared access signature URL (SAS)**.
[See image.](#azure-storage-explorer-connect)
- Click **Next**.
- On the **Enter Connection Info** page, enter the **Service URL** and SAS token received from the Zscaler Support team.
[See image.](#azure-storage-explorer-sas)
The other fields automatically fill in.
- Click **Next**.
- A connection summary appears. Review it and click **Connect**.
- After the connection is successful, in the left-side navigation, go to **Storage Accounts** > **Zscaler Storage (SAS)** > **Blob Containers** > **nss**. The VHD file is located here.
[See image.](#copy-latest-vhd)
- Highlight the VHD file and click **Copy**.
- In the left-side navigation, go to each of your personal storage accounts, and click** Paste** to add the VHD to your blob containers. The transfer can take some time. The **Activities** tab at the bottom tells you when the transfer is complete.
- Log in to the [Azure Portal](https://portal.azure.com/).
- Go to your destination blob container. The VHD file appears in the blob container.
[]![Azure Storage Explorer Plug Icon](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/Azure%20Plug%20Icon.png)
[]![Azure Storage Explorer Connect Window](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/Select-Connection-Method.png)
[]![Screenshot of Attach with SAS URL window in the Azure Storage Explorer](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia_azure_nss_enter_connection_info.png)
[]![Screenshot of the Add Storage account or Service page.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/Storage%20account%20or%20service.png)
[]![Screenshot of the latest VHD file.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia_azure_nss_vhd_file.png)
[]Before you begin:
- Make sure you have installed [Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/?view=azps-4.5.0) modules.
- Run PowerShell with administrator privileges.
- To allow PowerShell to run unsigned scripts, enter the following command:
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
- Download the VHD copy package files:
- [blob_copy.ps1](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/blob_copy.ps1)
- [copyconfig.txt](/downloads/zscaler-tech-pubs-style-guide/draft-articles/nss-deployment-guide-microsoft-azure-draft/copyconfig.txt)
The blob_copy.ps1 copies the VHD file from Zscaler’s Azure storage account to a general-purpose account specified in copyconfig.txt. The VHD file is approximately 500 GB and is used for the OS disk. After copying the VHD file, the script creates an Azure Managed Image based on the OS disk.
To copy the OS disk VHD file from Zscaler's Azure account:
- Make sure to pre-create or select a storage account, blob container, and location to which you want to copy the disk.
[See image.](#azure_portal_storage_account)
- Populate the values in copyconfig.txt. The following tables describe each value and the possible values for **location**.
- [See tables.](#table-location-values)
- Run the script using the PowerShell command:
powershell.exe .\blob_copy.ps1 '.\copyconfig.txt'
- In the pop-up window, enter your Azure credentials to start the script.
[See image.](#Azure_image)
Wait a few minutes for the VHD file to copy.
- After the script is completed successfully, the VHD file in the destination blob container appears.
[See image.](#destination-container)
[]
| Value | Description |
| ----- | ----------- |
| sastok | Contact Zscaler Support or your account team to receive the SAS token |
| store | Destination Azure general purpose account |
| name | Prefix for destination VHD file name |
| dest | Destination blob container name in the destination storage account |
| rgname | Creates or selects a resource group with this name |
| location | The Azure location for the destination container |
For the value **location**, the following are all the possible location names:
To get the latest location list, run the following PowerShell command:
`Get-AzureRmLocation | Format-Table`
| Location | Display Name |
| -------- | ------------ |
| australiacentral | Australia Central |
| australiacentral2 | Australia Central 2 |
| australiaeast | Australia East |
| australiasoutheast | Australia Southeast |
| brazilsouth | Brazil South |
| canadacentral | Canada Central |
| canadaeast | Canada East |
| centralindia | Central India |
| centralus | Central US |
| eastasia | East Asia |
| eastus | East US |
| eastus2 | East US 2 |
| francecentral | France Central |
| francesouth | France South |
| japaneast | Japan East |
| japanwest | Japan West |
| koreacentral | Korea Central |
| koreasouth | Korea South |
| northcentralus | North Central US |
| northeurope | North Europe |
| southcentralus | South Central US |
| southeastasia | Southeast Asia |
| southindia | South India |
| westus2 | West Central US 2 |
| uksouth | UK South |
| ukwest | UK West |
| westcentralus | West Central US |
| westeurope | West Europe |
| westindia | West India |
| westus | West US |
| westus2 | West US 2 |
[]![Screenshot of a storage account in the Azure Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-azure/ZIA-5.7-AP-Storage-Account.png)
[]![Screenshot of the MIcrosoft Azure sign in window](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment/nss-vm-deployment/nss-deployment-azure/zia-azure-nss-credentials.png)
[]![Screenshot of the file copied to the destination container.](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia_azure_nss_test_container.png)
[]Zscaler supports [Azure managed disks](https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview) for VM deployment. To deploy a VM using a managed disk:
- Log in to the [Azure Portal](https://portal.azure.com/).
-
Go to **Disks** and click **Create**.
The **Create a managed disk** wizard appears.
-
In the **Create a managed disk** wizard:
-
On the **Basics** tab, configure all fields per your deployment. The following fields require specific inputs:
- **Source type**: Select** Storage blob**.
- **Source blob**: Browse and select the OS disk that you copied in [this step](/unified/nss-deployment-guide-microsoft-azure#step-copy-os-disk-vhd-azure-storage-account) of the deployment guide.
- **OS type**: Select **Linux**.
- **Size**: Change the size to **512 GiB**. The storage type (e.g., Premium SSD LRS) and performance tier (e.g., P20 performance tier) shown in the following image are an example. Configure these fields per your requirements.
[See image.](#img-create-managed-disk)
- Click **Review + Create**.
A disk with your configured disk name is created.
- Go to **Disks** and select the newly created disk.
-
Click **Create VM**.
The **Create a virtual machine wizard** appears.
- In the **Create a virtual machine** wizard:
-
On the **Basics** tab, configure all fields per your deployment. To determine your appropriate size of VM, see the [table of VM types.](#table-vm-types)
[See image.](#img-create-vm-basics)
-
On the **Networking** tab, note that a **Virtual network**, or network interface (NIC), is created by default for the VM. After you create the VM, you must attach a second network interface to the VM.
[See image.](#img-create-vm-networking)
- Click **Review + create**.
- Verify your deployment:
- Log in to the VM using SSH. If you can log in, then your VM deployed successfully.
- In the Azure Portal, go to **Virtual machines** to verify that the value of the **Uses managed disks** column for your newly deployed VM is **Yes**.
- Attach a second network interface to your VM. To attach a second network interface, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-network-interface-vm).
[]
| VM Type | Memory | Cores | Bandwidth |
| ------- | ------ | ----- | --------- |
| Standard_D2_v4 | 8 GB | 2 | 1 GBPS |
| Standard_D4_v4 | 16 GB | 4 | 2 GBPS |
| Standard_D8_v4 | 32 GB | 8 | 4 GBPS |
| Standard_D16_v4 | 64 GB | 16 | 8 GBPS |
[]The following NSS configuration steps are run through an SSH terminal connection. The connection must use basic authentication. Use `zsroot`/`zsroot` when prompted for credentials.
Zscaler recommends changing the default password.
To configure the NSS virtual appliance on the VM:
- [a. Copy the SSL certificate.](#sslcertificate)
- [b. Remote log in to the VM instance.](#remote)
- [c. Install the SSL certificate.](#installssl)
- [d. Configure the NSS network settings.](#configurenss)
- [e. Download the NSS binaries.](#downloadnss)
- [f. Start the NSS.](#startnss)
- [g. Verify the configuration.](#verify)
- []Copy the downloaded file from the Admin Portal to the VM, using FTP, SCP, or SFTP.
- Look up the public hostname or IP address of your instance in the VM.
- []Use an SSH command such as follows to get shell access to the VM:
ssh zsroot@Public-Host-Name
- Use the following username/password: `zsroot`/`zsroot`.
[]NSS uses an SSL certificate to authenticate itself to the Zscaler service. Make sure that the SSL certificate is installed on only one active NSS VM at a time. Having multiple NSS VMs that use only one certificate causes cloud connection flapping, which disrupts the streaming of logs to the NSS.
- Copy the `NssCertificate.zip` file to the `/home/zsroot` root directory.
- Run the following command:
sudo nss install-cert NssCertificate.zip
- Check the configuration by running the following command:
sudo nss dump-config
-
[]Enter the command `netstat -rn` and note down the default gateway IP address. The following image is an example:
[See image.](#zia-nss-network-settings)
| Destination | Gateway |
| ----------- | ------- |
| Default | 10.3.0.1 |
| 127.0.0.1 | link#1 |
| 10.3.0.0/24 | link#3 |
| 10.3.0.12 | link#3 |
The first network interface (management network) is configured by default when you start the VM.
- Configure the NSS network (service interface only). You are then prompted for several IP configurations.
- Enter the command `sudo nss configure` and complete the following:
- Enter a name server (e.g., 168.63.129.16). You can either change (`C`), delete (`D`), or not change it (`N`). In this case, enter `N`.
- You can add a name server if you want. In this case, enter `N`.
- Enter the service interface IP address with netmask (smnet_dev). This is the private IP address of the second network interface (service interface - eth1) created in the VM. To get the private IP address, find the private IP of the second network interface you created in your Azure account:
- Go to the NSS VM configuration page.
- In the side menu, go to **Networking**,** **and select** **your second network interface.
- Copy the private IP address.
[See image.](#privateip)
- Enter the service interface default gateway IP address (smnet_dflt_gw). This is the default gateway IP address (e.g., 10.3.0.1). You can find it by running the command `netstat -rn`.
The following image shows an example output:
![Screenshot of sudo nss configure command output example](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/ZIA-microsoft-azure-configure-nss-network-settings.png)
[]![Screenshot of Nanolog Streaming Service (NSS) network settings configuration](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia_configure_nss_network_settings.png)
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
The absence of any one of the preceding connections, even after waiting a few minutes, usually indicates that there is a firewall configuration issue and the logs can't be streamed. To troubleshoot issues, see [Troubleshooting Deployed NSS Servers](/unified/troubleshooting-deployed-nss-servers).
[]![zia-azure-vm-privateip.png](/downloads/zia/zia-azure-vm-privateip.png)
[]An NSS feed specifies the data from the logs that the NSS sends to the SIEM. You can filter the data, so you send only the data you need to the SIEM. You can add one or more fields for the logs and one field for alerts. You can add up to 16 NSS feeds for each NSS. ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS to ensure optimal performance.) Each feed can have a different list of fields, a different format, and different filters. To learn more, see [Adding NSS Feeds](/unified/adding-nss-feeds).
[]![Create a managed disk wizard in Microsoft Azure](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia-nss-azure-managed-disks-wizard.png)
[]![Basics page in the Create a virtual machine wizard in Microsoft Azure](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia-nss-azure-create-VM-wizard-basics.png)
[]![Networking page in the Create a virtual machine wizard in Microsoft Azure](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-microsoft-azure/zia-nss-azure-create-VM-wizard-networking.png)
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