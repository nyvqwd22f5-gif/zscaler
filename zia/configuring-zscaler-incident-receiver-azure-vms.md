# Configuring the Zscaler Incident Receiver for Azure VMs
Source: https://help.zscaler.com/zia/configuring-zscaler-incident-receiver-azure-vms
PDF: https://help.zscaler.com/pdf/com/en/1455536.pdf

Before you can use a [Zscaler Incident Receiver](/zia/about-zscaler-incident-receiver), you must configure the virtual machine (VM) image for the Incident Receiver on an Azure VM, an Amazon Web Services (AWS) EC2 instance, or an on-premises VM. To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/zia/configuring-zscaler-incident-receiver-for-ec2) and [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver).
Before you begin deployment, contact Zscaler Support to obtain the Incident Receiver virtual hard disk (VHD) shared access signature (SAS) token. Without it, you cannot set up the Incident Receiver.
Deploying a Zscaler Incident Receiver VM on Azure
To deploy a Zscaler Incident Receiver VM on Azure:
- [1. Ensure You Meet the Requirements.](#step-1-requirements)
- [2. Create a Resource Group and Storage Account in Azure.](#step-2-create-rgroup-storage-acct)
- [3. Use Azure Storage Explorer to Copy the Incident Receiver VHD file to Your Azure Storage Account.](#step-3-copy-vhd-file)
- [4. Create and Configure a Security Group in Azure.](#step-4-security-group)
- [5. Launch an Azure VM to Host the Incident Receiver VM.](#step-5-launch-instance)
- [6. Configure the Incident Receiver VM.](#step-6-configure-vm)
Updating and Customizing a Deployed Zscaler Incident Receiver VM
With your Incident Receiver VM running, you can update and customize the VM based on your organization's needs.
- [Update the Incident Receiver VM](#update-incident-receiver)
- [Run the Incident Receiver VM in Explicit Proxy Mode](#explicit-proxy)
- [Run the Incident Receiver VM with Mutual Transport Security Enabled](#mutual-transport-security)
- [Configure the Zscaler Incident Receiver VM to Allow Multiple SFTP Connections](#multiple-sftp-connections)
- [Enable Remote Access for Zscaler Support](#enable-remote-access)
- [Upgrade SSH Key to ED25519](#upgrade-ssh-key)
- [Install a New Server Certificate](#install-new-cert)
Zscaler Incident Receiver Commands
You can use the following commands to configure, update, and troubleshoot your VM.
| **Command** | **Description** |
| ----------- | --------------- |
| `sudo zirsvr stop` | Stops the Zscaler Incident Receiver service. |
| `sudo zirsvr start` | Starts the Zscaler Incident Receiver service. |
| `sudo zirsvr update-now` | Updates the Zscaler Incident Receiver service. The service must be stopped before you can run this command. |
| `sudo zirsvr configure-sftp` | Updates the SFTP server that the Incident Receiver uses. |
| `sudo zirsvr restart` | Restarts the Zscaler Incident Receiver service. |
| `sudo zirsvr status` | Displays whether the Zscaler Incident Receiver service is running or stopped. |
| `sudo zirsvr force-update-now` | Forces the Zscaler Incident Receiver service to update to the latest version regardless of what version is on the VM. The service is automatically stopped before the update begins. |
| `sudo zirsvr troubleshoot` | Runs a series of checks to help troubleshoot issues, such as checking the installed certificate, the Zscaler cloud server configuration, all services, and whether or not an update is needed. |
| `sudo zirsvr collect-diagnostics` | Creates a file with diagnostic information to send to Zscaler Support for troubleshooting purposes. |
| `sudo zirsvr configure-syslog-server` | Configures external syslog server forwarding on the Zscaler Incident Receiver to forward file SFTP events and to log any critical changes to the configuration files monitored by the Incident Receiver. The external syslog server forwarding happens over UDP port 514, which cannot be modified. |
| `sudo zirsvr create-server-cert-csr` | Creates a new server certificate to be downloaded to the Incident Receiver. |
| `sudo zirsvr install-server-cert` | Installs server certificates. |
| `sudo zirsvr update-sshkey` | Creates a new SSH key and updates Zscaler Incident Receiver to use the new SSH key as authentication. |
[]To deploy the Zscaler Incident Receiver on an Azure VM, you need:
- The Zscaler Incident Receiver VHD SAS token.
- An Azure VM with a minimum of two CPUs and 8 GB of RAM (e.g., a D2as v4 Azure instance) to host the Incident Receiver VM.
- Access to a storage server that supports Secure File Transfer Protocol (SFTP)/Secure Copy Protocol (SCP) and public key authentication. You must also have a preconfigured account that allows write access to the server’s intended directory. You link the SFTP server to the Incident Receiver VM when you configure storage options later in the process.
The VHD file includes minimum specifications for various settings (e.g., disk size and network interface). You can increase those specifications as needed.
- (Optional) A static public IP address for the Incident Receiver VM.
Zscaler recommends using a static IP address to ensure that the IP address does not change when the VM reboots. Alternatively, you can associate the IP address with a fully qualified domain name (FQDN) and then use the FQDN when [configuring the Incident Receiver](/zia/modifying-zscaler-incident-receiver) in the Zscaler Internet Access (ZIA) Admin Portal.
- A [security group](/zia/configuring-zscaler-incident-receiver-azure-vms#security-group-substep) configured on the Azure instance to allow inbound Internet Content Adaptation Protocol (ICAP) messages from the Feed Central Cloud (FCC) cloud to the correct TCP port on the Incident Receiver VM (e.g., port 1344).
- A [Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver) added in the ZIA Admin Portal. You need this configuration to complete the VM setup.
- For Zscaler Incident Receiver to check your network connectivity and get access to and from your IP address, your firewalls must be enabled for the appropriate location. To understand the needed access requirements, see [DLP Incident Receiver Connections](https://config.zscaler.com/zscaler.net/dlp-incident-receiver).
- You must allow a direct IP-based connection to the Zscaler Hub IPs so the Incident Receiver can connect to the IP directly. To learn more, see [Zscaler Hub IP Addresses](https://config.zscaler.com/zscaler.net/hubs).
[]Before you can deploy an Incident Receiver in Azure, you must first create a resource group to hold all resources for the Incident Receiver VM, as well as a storage account for the Incident Receiver VHD file.
- [a. Create a resource group.](#step-2a-create-resource-group)
- [b. Create a storage account.](#step-2b-create-storage-account)
[][]
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Resource groups**.
[See image.](#resource-groups-icon)
The **Resource groups** page appears.
[See image.](#resource-groups-page)
- Click **Create**. The **Create a resource group** page appears.
- On the **Create a resource group** page:
- **Subscription**: From the drop-down menu, select the Azure subscription for the resource group.
- **Resource group**: Enter a name for the resource group.
- **Region**: From the drop-down menu, select the geographical Azure location for the resource group.
All resources that you create for the Incident Receiver must use the region you select here.
- Select the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#resource-review-create)
You return to the **Resource groups** page, and the resource group you created is displayed in the list of resource groups.
[]![Azure Portal Resource groups icon](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzurePortal_ResourceGroups.png)
[]![Azure Portal Resource groups page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateResourceGroupsPage.png)
[]![Azure resource group review and create page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateResourceGroups_CreateAResouceGroupPage_ReviewPlusCreateTab_ClickCreate.png)
[]
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Storage accounts**.
[See image.](#storage-accounts-icon)
The **Storage accounts** page appears.
[See image.](#storage-accounts-page)
- Click **Create**. The **Create a storage account** page appears.
- On the **Create a storage account** page:
- **Subscription**: From the drop-down menu, select the Azure subscription for the storage account.
- **Resource group**: From the drop-down menu, select the resource group for the Incident Receiver.
- **Storage account name**: Enter a name for the storage account.
- **Region**: From the drop-down menu, select the same geographical Azure region used for the Incident Receiver resource group.
- Keep the default selections for the rest of the options on the **Basics** tab, then click the **Networking** tab.
[See image.](#storage-accounts-basics-tab)
- On the **Networking** tab, ensure that the **Enable public access from all networks** option is selected.
- Select the **Review** tab, review your selections, then click **Create**.
[See image.](#storage-account-review-create)
After the storage account deployment is complete, a confirmation page appears.
[See image.](#storage-account-deployment-complete)
[]![Azure Portal storage accounts icon](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzurePortal_StorageAccounts.png)
[]![Azure Portal Resource groups page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateStorageAccountPage.png)
[]![Azure storage account basics tab](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateStorageAccount_BasicTab.png)
[]![Azure storage account review and create page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateStorageAccount_Review_Create.png)
[]![Azure storage account deployment complete page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateStorageAccount_Deployment_Complete.png)
[]To copy the Incident Receiver VHD file to your Azure storage account using Azure Storage Explorer:
- To ensure the fastest copy time, select the appropriate URL for your region:
- **USA**: https://zirsvrazureprod.blob.core.windows.net/
- **Europe**: https://zirsvrazureprodeu.blob.core.windows.net/
- **Australia**: https://zirsvrazureprodau.blob.core.windows.net/
- Download and launch [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/).
- Click the **Add Account** icon (plug icon).
[See image.](#azure-storage-explorer-plug)
The **Select Resource** window appears.
- In the **Select Resource** window, select **Storage account or service**.
[See image.](#storage-account-or-service)
- Click **Next**.
- Select **Shared access signature URL (SAS)**.
[See image.](#azure-storage-explorer-connect)
- Click **Next**.
- On the **Enter Connection Info** page, in the **Service URL **field**,** enter the **Service URL** and SAS token received from the Zscaler Support team.
[See image.](#azure-storage-explorer-sas)
The other fields automatically fill in.
- Click **Next**.
- A connection summary appears. Review it and click **Connect**.
- After the connection is successful, in the left-side navigation, go to **Storage Accounts** > **zirsvrstorageprod** > **Blob Containers** > **zir-image**. The VHD file is located here.
[See image.](#copy-latest-vhd)
- Highlight the VHD file and click **Copy**.
- In the left-side navigation, go to the storage account you created and click** Paste** to add the VHD to your blob containers. The transfer can take some time. The **Activities** tab at the bottom lets you know when the transfer is complete.
- Log in to the Azure Management portal.
- Go to your destination blob container. The VHD file appears in the blob container.
[]![Screenshot of the Add Account Icon (plug icon) in the Azure Storage Explorer](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzureStorageExplorer_PlugIcon.png)
[]![Screenshot of the Add Storage account or Service page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzureStorageExplorer_SelectResource.png)
[]![Screenshot of the Connect window in the Azure Storage Explorer with SAS URI selected](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzureStorageExplorer_SelectConnectionMethod.png)
[]![Screenshot of Attach with SAS URL window in the Azure Storage Explorer](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzureStorageExplorer_EnterConnectionInfo.png?1684246016)
[]![Screenshot of the latest VHD file.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzureStorageExplorer_VHD_File.png)
[]To create a security group in Azure:
- [a. Create a security group.](#step-4a-create-security-group)
- [b. Add inbound security rules.](#step-4b-add-inbound-rules)
- [c. Add outbound security rules.](#step-4c-add-outbound-rules)
To learn more, refer to the [Microsoft Azure documentation.](https://learn.microsoft.com/en-us/azure/virtual-network/manage-network-security-group)
[]
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Network security groups**.
[See image.](#network-security-groups-icon)
The **Network security groups** page appears.
- Click **Create**. The **Create network security group** page appears.
- In another tab, browse to [config.zscaler.com](http://config.zscaler.com). The **Zscaler Config** page appears.
- From the **Cloud** drop-down menu at the top left of the page, select your organization's Zscaler cloud.
- Go to **DLP Incident Receiver**.** **In the **Source** column of the table, click **Zscaler Hub IP Addresses**. The **Hub IP Addresses** page appears, listing all of the outbound connections that you must configure for the Zscaler Incident Receiver to communicate with the Zscaler cloud.
[See image.](#hub-ip-addresses-page)
- As needed, click **Copy IPs** in the **Required**, **Recommended**, and **Combined** columns so you can add those IP addresses to the security group.
- Return to the **Create network security group** page in the Azure Management portal.
- On the **Create network security group** page:
- **Subscription**: From the drop-down menu, select the Azure subscription for the security group.
- **Resource group**: From the drop-down menu, select the resource group for the Incident Receiver.
- **Name**: Enter a name for the security group.
- **Region**: From the drop-down menu, select the same geographical Azure region used for the Incident Receiver resource group.
[See image.](#create-network-security-page)
- Select the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#security-group-review-create)
- On the confirmation page that appears, click **Go to resource**.
[See image.](#security-group-deploy-complete)
[]
- Return to the Azure Management portal. In the left-side navigation, click **Inbound security rules**.
[See image.](#inbound-rule-left-panel)
- On the **Inbound security rules** page, click **Add**. The **Add inbound security rule** panel appears.
[See image.](#add-new-inbound-rule)
-
In the **Add inbound security rule** panel:
- **Source**: From the drop-down menu, select **IP Addresses**.
- **Source IP addresses/CIDR ranges**: Add the incoming traffic IPs for the Zscaler Incident Receiver VM. Ensure that you add the IPs that you copied from the Zscaler **Hub IP Addresses** page earlier.
- **Source port ranges**: Enter the source port ranges to use for inbound traffic.
- **Destination**: Select the destination from the drop-down menu.
- **Service**: From the drop-down menu, select **Custom**.
- **Destination port ranges**: Enter the TCP port 1344 for inbound traffic for the Incident Receiver.
- **Protocol**: Select **TCP**.
- **Action**: Select **Allow**.
- **Priority**: Enter a priority ranking for the inbound security rule.
- **Name**: Enter a name for the inbound security rule.
- **Description**: (Optional) Enter a description for the inbound security rule.
[See image.](#inbound-rules-populated)
- Click **Add**.
The rule you created is displayed in the list on the **Inbound security rules** page.
[See image.](#inbound-rule-created)
[]
- Return to the Azure Management portal. In the left-side navigation, click **Outbound security rules**.
[See image.](#outbound-rule-left-panel)
- On the **Outbound security rule** page, click **Add**. The **Add outbound security rule** panel appears.
[See image.](#add-new-outbound-rule)
-
In the **Add outbound security rule** panel:
- **Source**: From the drop-down menu, select **IP Addresses**.
- **Source IP addresses/CIDR ranges**: Add the outgoing traffic IPs for the Zscaler Incident Receiver VM.
- **Source port ranges**: Enter the source port ranges to use for outbound traffic.
- **Destination**: Select the destination from the drop-down menu.
- **Service**: From the drop-down menu, select **Custom**.
- **Destination port ranges**: Enter the TCP port to use for outbound traffic for the Incident Receiver.
- **Protocol**: Select **TCP**.
- **Action**: Select **Allow**.
- **Priority**: Enter a priority ranking for the outbound security rule.
- **Name**: Enter a name for the outbound security rule.
- **Description**: (Optional) Enter a description for the outbound security rule.
[See image.](#outbound-rules-populated)
- Click **Add**.
The rule you created is displayed in the list on the **Outbound security rules** page.
[See image.](#outbound-rule-created)
[]![Azure Portal Network security groups icon](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_AzurePortal_NetworkSecurityGroups.png)
[]![Azure Portal Network security groups page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateANetworkSecurityGroupPage_BasicsTab_PopulatedFields.png)
[]![Zscaler Hub IP Addresses page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-hub-ip-addresses-page.png)
[]![Azure Portal review and create Network security groups page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateANetworkSecurityGroupPage_ReviewAndCreateTab.png)
[]![Azure Portal Network security group deployment complete page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateANetworkSecurityGroup_DeploymentCompleteMessage.png)
[]![Azure Portal select inbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_SelectInboundSecurityRules.png)
[]![Azure Portal add new inbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_AddNewInboundSecurityRule.png)
[]![Azure Portal new inbound security rule fields populated](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/AddNewInboundSecurityRule_Populated.png)
[]![Azure Portal newly created inbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_AddNewInboundSecurityRule_Created.png)
[]![Azure Portal select outbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_SelectOutboundSecurityRules.png)
[]![Azure Portal add new outbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_AddNewOutboundSecurityRule_Panel.png)
[]![Azure Portal new outbound security rule fields populated](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/AddNewOutboundSecurityRule-Populated.png)
[]![Azure Portal newly created outbound security rule](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_NetworkSecurityGroup_AddNewOutboundSecurityRule_Created.png)
[]To create the Incident Receiver VM, you must first create a managed disk that you then use to launch the Azure VM instance that hosts the Incident Receiver.
- [a. Create a managed disk.](#step-5a-create-managed-disk)
- [b. Create a VM to host the Incident Receiver.](#step-5b-create-vm)
[]
- Log in to the Azure Management portal.
- Click **Create a resource**, then use the search bar to find `Managed Disks`.
- On the search results page, click **Create > Managed Disks**.
[See image.](#create-managed-disk)
The **Create a managed disk** page appears.
[See image.](#create-managed-disk-page)
- On the **Create a managed disk** page, select the **Basics** tab if needed.
-
On the **Basics** tab:
- **Subscription**: From the drop-down menu, select the Azure subscription for the managed disk.
- **Resource group**: From the drop-down menu, select the resource group you are using for the Incident Receiver.
- **Disk name**: Enter a name for the managed disk.
- **Region**: From the drop-down menu, select the same geographical Azure region used for the Incident Receiver resource group.
- **Availability zone**: From the drop-down menu, select an Azure availability zone, as needed for your organization.
- **Source type**: From the drop-down menu, select **Storage blob**.
- Under the **Source blob**, click **Browse**, then go to the storage account where the Incident Receiver VHD file is stored.
- Select the VHD file, then click **Select**.
[See image.](#select-vhd-file)
- On the **Create a managed disk** page, for the **OS type** option, select **Linux**.
Zscaler supports only Linux as the operating system for Azure instances of the Incident Receiver.
- From the **Security type** drop-down menu, select **Standard**.
- For the **VM generation** option, select **Generation 1**.
Zscaler supports only Generation 1 VMs for Azure instances of the Incident Receiver.
- For the **Size** option, click **Change size**. The **Select a disk size** page appears.
- From the **Storage type** drop-down menu, select **Premium SSD (locally-redundant storage)**.
- In the **Custom disk size (GiB)** field, enter `500`.
- Click **OK**.
[See image.](#select-disk-size)
- On the **Create a managed disk** page, select the **Networking** tab.
- Select **Disable public and private access**.
- Select the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#managed-disk-review-create)
- On the confirmation page that appears, click **Go to resource**.
[See image.](#managed-disk-deploy-complete)
[]![Azure Portal create managed disk](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_CreateManagedDisk.png)
[]![Azure Portal create managed disk page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_CreateManagedDiskPage_Empty.png)
[]![Azure storage account file selection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_CreateManagedDisk_VHD-StorageAccount.png)
[]![Azure disk size selection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_CreateManagedDisk_SelectADiskSize.png)
[]![Azure managed disk creation](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_ReviewAndCreate.png)
[]![Azure managed disk completed deployment](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_DeploymentComplete.png)
[]
- On the overview page for the managed disk you created, click **Create VM**.
[See image.](#managed-disk-create-vm)
The **Create a virtual machine** page appears.
[See image.](#create-virtual-machine-page)
- Ensure that the **Subscription** and **Resource group** options match the options you selected when creating the managed disk.
- In the **Virtual machine name** field, enter a name for the VM.
- From the **Size** drop-down menu, select **See all sizes**. The **Select a VM size** page appears.
- Select **D2as_v4** from the list, then click **Select**.
[See image.](#create-vm-size-page)
- On the **Create a virtual machine page**, in the **Public inbound ports** section, select **None**.
- From the **License type** drop-down menu, select **Other**.
- Select the **Networking** tab. Then, for the **NIC network security group** option, select **Advanced**.
- From the **Configure network security group** drop-down menu, select the network security group you created earlier.
- Select the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#create-vm-review-create)
- On the confirmation page that appears, click **Go to resource**.
[See image.](#create-vm-deploy-complete)
- On the resource page that appears, click **Serial console**.
[See image.](#vm-select-serial-console)
The **Serial console** page for the VM appears, showing the console output for the Incident Receiver.
[See image.](#vm-serial-console-output)
The VM deployment takes several minutes. When a prompt to change the zsroot password appears in the serial console output, the Incident Receiver is ready to be configured.
[]![Azure Portal create managed disk](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_ManagedDiskOverview_CreateVM-Button.png)
[]![Azure virtual machine creation](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_CreateAVirtualMachine_BasicTab_Empty.png)
[]![Azure VM size selection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_SelectVMSizePage.png)
[]![Azure VM review and create](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_ReviewAndCreate.png)
[]![Azure VM deployment complete](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreateVM_DeploymentComplete.png)
[]![Azure VM serial console selection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreatedVM_SerialConsoleOption.png)
[]![Azure VM Serial Console Output](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_CreatedVM_SerialConsole_Output_ZIRSVR-password.png)
[]To configure the Incident Receiver VM:
- Ensure that you have [added a Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver) in the ZIA Admin Portal. You need this configuration to complete the VM setup.
- Log in to the VM as user `zsroot`. The initial root password for this user is randomly generated.
- Change the root password:
- Enter the following command:
`		sudo zirsvr change-password`
[See image.](#change-password-command-image)
- Enter the initial root password, which was randomly generated for you.
- Enter a new root password.
[See image.](#new-root-pass-image)
- Re-enter the new root password.
- In the ZIA Admin Portal, go to **Administration** > **DLP Incident Receiver**. Then select the **Zscaler Incident Receiver** tab.
- Locate the Zscaler Incident Receiver you added previously. In the** Certificate **column, click **Download**.
[See image.](#download-certificate-image)
- Copy the certificate .zip file to the VM and install it:
- The following example uses SCP to copy the file:
`		scp <certificate_zip_filename> zsroot@<ip>:/home/zsroot`
For example: `scp IncidentReceiverCertificate.zip zsroot@10.66.108.100:/home/zsroot`
- Enter the following command to install the SSL certificate:
`		sudo zirsvr configure ~/<certificate_zip_filename>`
For example: `sudo zirsvr configure ~/IncidentReceiverCertifcate.zip`
- For `icaps_port`, enter the Zscaler Incident Receiver port number that you previously added to the Zscaler Incident Receiver URI in the ZIA Admin Portal.
(Optional) You can enter a different port number to change the Incident Receiver’s port number. However, you must also update the Incident Receiver’s URI in the ZIA Admin Portal to include the new port number. To learn more, see [Adding a Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver).
[See image.](#icaps-port-image)
- []Specify that your Azure Incident Receiver uses SFTP storage, then configure the storage server and public key authentication:
- [Configuring SFTP storage](#sftp-storage)
By default, the Incident Receiver Health Check is enabled. The health check notes if there are any changes in behavior and is set to 5 minute intervals. To verify the Health Check is working, you receive the Health Status JSON `<systmld>_<iphash>_ir_health_status_timestamp.json` file in your evidence folder. If you would like to disable the Health Check, contact Zscaler Support.
- [Example of health check file](#example-health-check)
After Zscaler Incident Receiver is configured properly, it:
- Downloads the latest build
- Installs the certificate you specified
- Checks whether the service is configured correctly
- Starts the service
[See image.](#console-successful)
After the Zscaler Incident Receiver service has started, you can add it to the Data Loss Prevention (DLP) policy rule. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
You can log in to the storage server to see information about DLP policy violations. For each policy violation, the storage server creates a directory containing the policy-violating file and a JSON file for the DLP policy scan metadata.
[Download a sample JSON file for Endpoint DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/ENDPOINT-DLP-IR-METADATA.json)
[Download a sample JSON file for DLP policy with and without content inspection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-example-1-27.json)
[Download a sample JSON file for DLP policy with Evaluate All Rules mode enabled](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-evaluate-all-rules-enabled-example_08.15.25.json)
[Download a sample JSON file for SaaS Security DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/SaaS-Security-DLP-IR-METADATA.json)
[]
`{
"ipAddress":"10.66.103.169",
"version":"6.3.2404",
"updatedAt":"1726848892",
"systemId":"65533",
"lastIncidentReceivedAt":"1726828921",
"lastFileUploadSuccessAt":"1726828921",
"storageType": "SFTP",
"storageLocation":"/sc/temp",
"healthcheckIntervalInSec":"300"
}`
[]![Changing the root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/change-password.png)
[]![Entering the new root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-new-password.png)
[]![Download the Zscaler Incident Receiver certificate](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/ZIA-Download-Incident-Receiver-Certificate.png)
[]![Entering the port number for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-icaps-port.png)
[]![Console output for a successful Incident Receiver deployment](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA-ZIR_Azure_ConsoleSuccessfulDeployment.png)
[]
When you are using your Incident Receiver with Workflow Automation, use the information for your Filewatcher VM when configuring the SFTP storage. To learn more, see [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure).
- To specify that the Incident Receiver forwards data to the SFTP storage, enter `SFTP`.
- For `storage_sftp_fqdn`, enter the FQDN for the storage server.
- For `storage_sftp_port`, enter the upload port of the SFTP server.
- For `storage_dir`, enter the storage server directory.
- For `storage_sftp_username`, enter a username for storage server login.
- To set up the public key, enter a password for the username. This password is used temporarily and is not saved.
[See image.](#configure-storage-server-Azure-sftp-image)
If the SFTP server doesn't allow password-based authentication, you receive an error that the service is unable to update the public key on the server. If you receive that error, add the contents of the public key to the `authorized_keys` file on the SFTP server:
- Copy the contents from the file `/.ssh/id_ed25519.pub`.
- On the SFTP server, add the copied content to the end of the following file: `/.ssh/authorized_keys`.
- On the Incident Receiver VM, enter the following command:
`	sudo zirsvr configure ~/<certificate_zip_filename>`
[]![Configuring the SFTP storage server for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-azure-vms/ZIA_ZIR_Azure_SFTP_Storage.png)
[]If you have successfully configured the service, the service automatically downloads the latest build before it starts. To manually update the service:
- Enter the following command to stop the service:
`	sudo zirsvr stop`
- Enter the following command to install the update:
`	sudo zirsvr update-now`
- Enter the following command to start the service:
`	sudo zirsvr start`
[]If you receive an error for an expired certificate, you must install a new server certificate. To do so:
-
Run the following command to verify your server certificate is expired:
`sudo zirsvr troubleshoot `
-
Run the following command to create a certificate signing request:
`sudo zirsvr create-server-cert-csr`
- Send the certificate to a well-known CA for signing.
-
Run the following command to install the server certificate:
`sudo zirsvr install-server-cert`
-
Run the following command to restart the Incident Receiver and update the server certificate:
`sudo zirsvr restart`
[]To run the Incident Receiver in explicit proxy mode:
- Log in to the VM as user `zsroot`.
-
Enter the following command:
`sudo zirsvr configure-proxy`
- For `Do you require a proxy server configuration?` enter `y` and press `Enter`.
- For `proxyserver` enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport` enter your proxy port number (e.g., `1344`) and press `Enter`.
The VM then tests the connection. When it is successful, the configuration is complete.
To remove the explicit proxy configuration:
- Enter the following command:
`	sudo zirsvr configure-proxy`
- For `Do you require proxy server configuration?` enter `n` and press `Enter`.
- For `Do you want to delete current proxy configuration?` enter `y` and press `Enter`.
Requirements for Explicit Proxy Mode
If you're using explicit proxy mode, DNS and Network Time Protocol (NTP) connections are not tunneled, meaning you need an internal DNS server to run in this mode. The Zscaler Incident Receiver must have DNS resolution for the current Master Certificate Authority (CA) IP, the update server, and the NTP server. The Zscaler Incident Receiver host also must be able to query a DNS server to resolve the following:
- smcacluster.<cloudname>
- update1.<cloudname>
- update2.<cloudname>
- zdistribute.<cloudname>
- The NTP server. By default, the VM has the following FQDNs for NTP servers configured:
- 0.freebsd.pool.ntp.org
- 1.freebsd.pool.ntp.org
- 2.freebsd.pool.ntp.org
You can override these FQDNs to your internal IP address in your DNS server configuration or using other methods.
In addition, since the proxy configuration doesn't allow authentication, you must configure the proxy server to allow specific IP/MAC addresses without user and password authentication.
[]You can use the Mutual Transport Layer Security (MTLS) method to support client authentication for the Zscaler Incident Receiver. MTLS is a method for mutual authentication. It ensures that parties at each end of the connection are who they claim to be. Zscaler provides the MTLS CA Certificate for the Zscaler Incident Receiver, and you have the option to enable mutual authentication for the Zscaler Incident Receiver, which then uses this certificate for client authentication.
To run the Incident Receiver VM with mutual transport security enabled:
- Log in to the VM as user `zsroot`.
- Enable MTLS by updating the *icap_mtls_enabled* parameter to 1 (`icap_mtls_enabled=1`). By default, this parameter is disabled.
- Enter the following command to restart the Zscaler Incident Receiver service:
`	sudo zirsvr restart`
[]If you notice that SFTP upload is slower than expected, or if you notice that the Zscaler Incident Receiver internal queue is full, you can configure the Zscaler Incident Receiver VM to allow multiple simultaneous SFTP connections. You can find the logs for the Incident Receiver internal queue at `/sc/log/zirsvr.log`.
To configure this setting:
- Log in to the VM as user `zsroot`.
- Specify the number of simultaneous SFTP connections by updating the `storage_sftp_conn_max` parameter to a value from one to 16 (e.g., `storage_sftp_conn_max=2`). By default, this parameter has a value of 1.
- Enter the following command to restart the Zscaler Incident Receiver service:
`	scp sudo zirsvr restart`
- Before enabling this setting in your production environment, be sure to conduct thorough end-to-end testing.
- If changing this setting does not solve the problem of the Zscaler Incident Receiver internal queue filling up, you might also need to change the specifications on your SFTP server to ensure faster throughput, or you might need to configure multiple incident receivers with load balancing.
- If you need assistance enabling this setting in your environment, contact Zscaler Support.
[]An admin can request remote assistance and allow Zscaler Support to log in to an Incident Receiver without having to open a firewall connection for inbound traffic. This feature is disabled by default. You must explicitly enable it for the duration that you require remote support assistance.
- To enable Zscaler Support to access your Incident Receiver, enter the following command:
`	sudo zirsvr support-access-start`
This command creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Incident Receiver.
- To disable Zscaler Support access to your Incident Receiver, enter the following command:
`	`sudo zirsvr support-access-stop``
This command brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Incident Receiver, enter the following command:
`	sudo zirsvr support-access-status`
[]
If your organization requires you to update your SSH key, upgrade to the ED25519 key. To upgrade:
-
Run the following command:
`sudo zirsvr troubleshoot`
If you see the following warning, you must update your SSH key:
`Checking SFTP server connection
External SFTP server is configured as ...
SFTP server is setup correctly, connection, read, and write are all successful. However, disk quota is not checked.
Warning: SFTP is configured with older key type "rsa", consider upgrading it to newer keytype "ed25519" using command "sudo zirsvr update-sshkey". If your SFTP server is a Windows based server, please read SFTP server's Admin Guide.`
You can do a snapshot of your VM before executing the following command.
-
Run the following command:
``sudo zirsvr update-sshkey``
If the SSH key was migrated correctly:
- It creates an SSH key with ED25519 to the file `authorized_keys` under the directory `/home/zsroot/.ssh`.
- It adjusts the file `/sc/conf/sc.conf` to use the new ED25519 key.
-
On a Linux-based SFTP server, it uses a new public key.
If your SFTP server doesn't support ssh-copy-id, you receive a message that the operation was unsuccessful. To update the SSH public key with the new ED25519 key, contact Zscaler Support.