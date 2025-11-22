# Configuring the Index Tool with Azure
Source: https://help.zscaler.com/zia/configuring-index-tool-azure-vms
PDF: https://help.zscaler.com/pdf/com/en/1467486.pdf

To create index templates for DLP dictionaries (i.e., [Exact Data Match (EDM)](/zia/about-exact-data-match) and [Indexed Document Match (IDM)](/zia/about-indexed-document-match) templates), you must configure the virtual machine (VM) image for the Index Tool with Azure, Amazon Web Services (AWS), or VMware.
To learn more, see [Configuring the Index Tool with Amazon Web Services](/zia/configuring-index-tool-amazon-web-services) and [Configuring the Index Tool with VMware](/zia/configuring-index-tool).
- Before you begin deployment, contact Zscaler Support to obtain the Index Tool VHD shared access signature (SAS) token. Without it, you cannot set up the Index Tool.
- Since the Index Tool provides access to highly sensitive information, ensure that everyone who has access to it is authorized and authenticated.
Deploying a Zscaler Index Tool VM on Azure
To deploy a Zscaler Index Tool VM on Azure:
- [1. Ensure that you meet all of the requirements.](#step-1-requirements)
- [2. Create a resource group and storage account in Azure.](#step-2-create-rgroup-storage-acct)
- [3. Use Azure Storage Explorer to copy the Index Tool VHD file to your Azure storage account.](#step-3-copy-vhd-file)
- [4. Launch an Azure VM to host the Index Tool VM.](#step-4-launch-instance)
- [5. Configure the Index Tool VM.](#step-5-configure-vm)
Updating and Customizing a Deployed Zscaler Index Tool VM
With your Index Tool VM running, you can update and customize the VM based on your organization's needs.
- [Update the Index Tool VM](#update-index-tool)
- [Run the Index Tool VM in explicit proxy mode](#explicit-proxy)
- [Configuring the Index Tool Service to run without elevated privileges](#run-without-elevated-privileges)
- [Enabling Remote Access for Zscaler Support](#enable-remote-access)
Index Tool VM Commands
The following commands can be used to configure, update, and troubleshoot your VM.
| **Command** | **Description** |
| ----------- | --------------- |
| `sudo zadp stop` | Stops the Zscaler Index Tool service. |
| `sudo zadp start` | Starts the Zscaler Index Tool service. |
| `sudo zadp update-now` | Updates the Zscaler Index Tool service. The service must be stopped before you can run this command. |
| `sudo zadp restart` | Restarts the Zscaler Index Tool service. |
| `sudo zadp status` | Displays whether the Zscaler Index Tool service is running or stopped. |
| `sudo zadp force-update-now` | Forces the Zscaler Index Tool service to update to the latest version regardless of what version is on the VM. The service is automatically stopped before the update begins. |
| `sudo zadp troubleshoot` | Runs a series of checks to help troubleshoot issues, such as checking the installed certificate, the zcloud server configuration, all services, and whether or not an update is needed. |
| `sudo zadp collect-diagnostics` | Creates a file with diagnostic information to send to Zscaler Support for troubleshooting purposes. |
| `sudo zadp configure-syslog-server` | Configures external syslog server forwarding on the Zscaler Index Tool to forward file SFTP events and to log any critical changes to the configuration files monitored by the Index Tool. The external syslog server forwarding happens over UDP port 514, which cannot be modified. |
[]To deploy the Zscaler Index Tool on an Azure VM, you need:
- The Zscaler Index Tool VHD SAS token.
- If your index templates include less than 300 million records, Zscaler recommends the following minimum configuration:
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 16 GB (i.e., Standard_D4_v4 or Standard_D8_v4).
- If your index templates include more than 300 million records, Zscaler recommends the following minimum configuration:
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 64 GB (i.e., Standard_E8-4ds_v4 or Standard_E8as_v4).
The VHD files include minimum specifications for various settings (e.g., disk size and network interface). You can increase those specifications as needed.
- A [Zscaler Index Tool](/zia/about-index-tool) added in the ZIA Admin Portal. You need this configuration to complete the VM setup.
[]As a first step in deploying an Index Tool in Azure, you must first create a resource group to hold all resources for the Index Tool VM, as well as a storage account for the Index Tool VHD file.
- [a. Create a Resource Group](#step-2a-create-resource-group)
- [b. Create a Storage Account](#step-2b-create-storage-account)
[]
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Resource groups**.
[See image.](#resource-groups-icon)
The **Resource groups** page is displayed.
[See image.](#resource-groups-page)
- Click **Create**. The **Create a resource group** page is displayed.
- In the **Create a resource group** page:
- **Subscription**: Select the Azure subscription for the resource group from the drop-down menu.
- **Resource group**: Enter a name for the resource group.
- **Region**: Select the geographical Azure location for the resource group from the drop-down menu.
All resources that you create for the Index Tool must use the region you select here.
- Click the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#resource-review-create)
You return to the **Resource groups** page, and the resource group you created is displayed in the list of resource groups.
[]![Azure Portal Resource groups icon](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZIR_AzurePortal_ResourceGroups.png)
[]![Azure Portal Resource groups page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZIR_Azure_CreateResourceGroupsPage.png)
[]![Azure resource group review and create page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateResourceGroups_CreateAResouceGroupPage_ReviewPlusCreateTab_ClickCreate.png)
[]
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Storage accounts**.
[See image.](#storage-accounts-icon)
The **Storage accounts** page is displayed.
[See image.](#storage-accounts-page)
- Click **Create**. The **Create a storage account** page is displayed.
- In the **Create a storage account** page:
- **Subscription**: Select the Azure subscription for the storage account from the drop-down menu.
- **Resource group**: Select the resource group for the Index Tool from the drop-down menu.
- **Storage account name**: Enter a name for the storage account.
- **Region**: Select the same geographical Azure region used for the Index Tool resource group.
- Keep the default selections for the rest of the options on the **Basics** tab, then click the **Networking** tab.
[See image.](#storage-accounts-basics-tab)
- On the **Networking** tab, ensure that the **Enable public access from all networks** option is selected.
- Click the **Review** tab, review your selections, then click **Create**.
[See image.](#storage-account-review-create)
A confirmation page is displayed after the storage account deployment is complete.
[See image.](#storage-account-deployment-complete)
[]![Azure Portal storage accounts icon](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzurePortal_StorageAccounts.png)
[]![Azure Portal Resource groups page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateStorageAccountPage.png)
[]![Azure storage account basics tab](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateStorageAccount_BasicTab.png)
[]![Azure storage account review and create page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateStorageAccount_Review_Create.png)
[]![Azure storage account deployment complete page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateStorageAccount_Deployment_Complete.png)
[]To deploy the Index Tool on Azure, you'll need two separate VHD files: one for the OS, and one for data. Additionally, there are two different options available for each VHD file, to support 600 GB and 1,100 GB disk sizes on the Azure VM.
To use Azure Storage Explorer to copy the Index Tool VHD files to your Azure storage account:
- Select the appropriate URL for your region to ensure the fastest copy time:
- **USA**: https://zadpazureprod.blob.core.windows.net/
- **Europe**: https://zadpazureeu.blob.core.windows.net/
- **Australia**: https://zadpazureau.blob.core.windows.net/
- Download and launch [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/).
- Click the **Add Account** icon (**plug** icon).
[See image.](#azure-storage-explorer-plug)
The **Select Resource** window appears.
- In the **Select Resource** window, select **Storage account or service**.
[See image.](#storage-account-or-service)
- Click **Next**.
- Select **Shared access signature URL (SAS)**.
[See image.](#azure-storage-explorer-connect)
- Click **Next**.
- In the **Enter Connection Info** page, in the **Service URL field,** enter the **Service URL** and SAS token received from the Zscaler Support team.
[See image.](#azure-storage-explorer-sas)
The other fields automatically fill in.
- Click **Next**.
- A connection summary appears. Review it and click **Connect**.
- After the connection is successful, in the left-side navigation, go to **Storage Accounts** > **<display name>** > **Blob Containers** > **zir-image**. The VHD files are located here.
- Select the blob container that corresponds to the disk size on the VM you are going to create (i.e., 600 GB or 1,100 GB).
[See image.](#copy-latest-vhd)
- Highlight the data VHD file and click **Copy**.
- In the left-side navigation, go to the storage account you created, and click** Paste** to add the VHD to your blob containers. The transfer can take some time. The **Activities** tab at the bottom lets you know when the transfer is complete.
- Repeat step m through step n for the OS VHD file.
- Log in to the Azure Management portal.
- Go to your destination blob container. The VHD files appear in the blob container.
- Select the blob container, then select the context menu for the data VHD file. Click **Properties**.
[See image.](#data-vhd-properties)
- On the properties page for the VHD file, next to the URL field, click **Copy to clipboard**.
[See image.](#data-vhd-copy-to-clipboard)
- Save the copied URL; you need it when you set up your VM later.
- Repeat step r through step t for the OS VHD file.
[]![Screenshot of the Add Account Icon (plug icon) in the Azure Storage Explorer](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_PlugIcon.png)
[]![Screenshot of the Add Storage account or Service page.](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_SelectResource.png)
[]![Screenshot of the Connect window in the Azure Storage Explorer with SAS URI selected](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_SelectConnectionMethod.png)
[]![Screenshot of Attach with SAS URL window in the Azure Storage Explorer](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_EnterConnectionInfo.png)
[]![Screenshot of the latest VHD file.](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_VHD_Files.png)
[]![Screenshot of the context menu for VHD files](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_VHD_ContextMenu.png)
[]![Screenshot of the copy to clipboard button](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_AzureStorageExplorer_VHD_CopyToClipboard.png)
[]To create the Index Tool VM, you first download a JSON parameter file, and then use that file to deploy the Azure VM instance that hosts the Index Tool.
- Download the JSON parameter file.
[Download the Azure Resource Manager (ARM) template JSON parameter file](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/azure_zadp_arm_ver_1.0.1.json)
- Log in to the Azure Management portal.
- In the **Azure services** section, click **Deploy a custom template**.
[See image.](#deploy-custom-template)
The **Custom deployment** page is displayed.
- Click **Build your own template in the editor**.
[See image.](#build-template-in-editor)
The **Edit template** page is displayed.
- Click **Load file** field, then go to the JSON parameter file you downloaded earlier.
- Click **Save**.
[See image.](#edit-template-save)
The **Custom deployment** page is displayed.
[See image.](#custom-deployment-page-unpopulated)
- On the **Custom deployment** page:
- **Subscription**: Select the Azure subscription for the Index Tool from the drop-down menu.
- **Resource group**: Select the resource group for the Index Tool from the drop-down menu.
- **Region**: Select the same geographical Azure region used for the Index Tool resource group.
- **VM Name**: Specify the name of the VM for the Index Tool.
- **VHD Location-OS**: Specify the Azure storage account URL for the OS VHD file. This is the URL you copied when setting up the storage account.
- **VHD Location-Data**: Specify the Azure storage account URL for the data VHD file. This is the URL you copied when setting up the storage account.
- **Disk Size**: Specify the size of the OS and data VHD files, in gigabytes (i.e., `600` or `1100`).
- **VM Size**: Select a size for the VM from the drop-down menu. If you are using 1,100 GB VHD files, select an E8 VM.
- **Virtual Network Type**: Select whether to use a new or existing virtual network from the drop-down menu.
- **Virtual Network Name**: If you are using an existing virtual network, specify its name.
- **Virtual Network Resource Group**: If you are using an existing virtual network, specify the name of its resource group.
- **Subnet Name**: If you are using an existing virtual network, specify the name of its subnet.
- **Whitelist Outbound Zscaler IP Addresses**: Select a Zscaler cloud to allowlist its IP addresses. To learn more, browse to [config.zscaler.com](http://config.zscaler.com), then click **Zscaler Index Tool Requirements**.
- Click the **Review + Create** tab, wait for the **Validation passed** message to appear, then click **Create**.
[See image.](#create-vm-review-create)
- On the confirmation page that is displayed, in the **Deployment details** section, click the name of the VM you created.
[See image.](#create-vm-deploy-complete)
- On the overview page for the VM, click **Serial console** in the pane on the left side of the page.
[See image.](#vm-select-serial-console)
The **Serial console** page for the VM is displayed, and you see the console output for the Index Tool.
[See image.](#vm-serial-console-output)
The VM deployment takes several minutes. The Index Tool is ready to be configured when you see the prompt to change the zsroot password in the serial console output.
[]![Azure custom template deployment button](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_DeployCustomTemplateButton.png)
[]![Azure build your own template button](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_BuildTemplateInEditorButton.png)
[]![Azure save template button](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_SaveTemplateButton.png)
[]![Azure custom deployment page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CustomDeploymentPage.png)
[]![Azure VM review and create](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateVM_ReviewAndCreate.png)
[]![Azure VM deployment complete](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreateVM_DeploymentComplete.png)
[]![Azure VM serial console selection](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreatedVM_SerialConsoleOption.png)
[]![Azure VM Serial Console Output](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/ZIA-ZADP_Azure_CreatedVM_SerialConsole_Output.png)
[]To configure the Index Tool VM:
- Ensure that you have [added a Zscaler Index Tool](/zia/adding-index-tool-configuration) in the ZIA Admin Portal. You need this configuration to complete the VM setup.
- Log in to the VM as user `zsroot`. The initial root password for this user is randomly generated.
- Change the root password:
- Enter the following command:
sudo zadp change-password
[See image.](#change-password-command-image)
- Enter the initial root password, the one that was randomly generated for you.
- Enter a new root password.
[See image.](#new-root-pass-image)
- Re-enter the new root password.
After the password is changed, you need to log in to `zsroot` again using the new password.
- Go back to the ZIA Admin Portal, and go to **Administration** > **Index Tool**.
- Locate the [Index Tool Configuration](/zia/about-index-tool) you added previously, and under the **SSL Certificate** column click **Download**.
[See image.](#DownloadCert)
- Copy the SSL client certificate.zip file to the VM and install it:
- In this example, scp is used to copy the file:
scp <SSL_certificate_zip_filename> zsroot@<vm_ip>:~/
For example: `scp EdmClientCertificate.zip zsroot@10.66.108.100:~/`
- Enter the following command to install the SSL certificate:
`sudo zadp configure <SSL_certificate_zip_filename>`
For example: `sudo zadp configure EdmClientCertificate.zip`
- Enter the domain name that is used for the Index Tool's fully qualified domain name (FQDN). For example, if the Index Tool is reachable from `indextool.mycompany.com`, then the domain name entered here is `mycompany.com`. The self-signed certificate would be generated for `*.mycompany.com`.
[See image.](#VM_CLI5)
- Enter a passphrase, then re-enter the passphrase to confirm it.
[See image.](#VM_CLI6)
- You are prompted to enter the full path name to the text file where the passphrase is stored. You can also press `Enter` twice to accept the default location and file, `/home/zsroot/zscaler_zadp_webui_certificate_pass.txt`.
[See image.](#VM_CLI7)
After the service is configured properly, the service:
- Checks if the network is configured correctly.
- Installs the SSL client certificate you specified.
- Generates a self-signed SSL server certificate. If you need to install a custom server certificate, see the next step.
- Downloads the latest install package.
- Starts the service.
- (Optional) If you need to install a self-signed or custom SSL server certificate:
- Enter the following command to install the server certificate:
`sudo zadp install-server-cert`
- Enter the full path to the PEM-formatted certificate file.
- Enter the following command to restart the Index Tool service:
`sudo zadp restart`
Go to https://<IP Address of the Index Tool VM> to access the Index Tool. After the Index Tool service has started, you can log in with your ZIA Admin Portal login credentials and create Index Templates to use when creating DLP dictionaries. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template) and [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template).
[]![Changing the root password for the Zscaler Index Tool VM](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/change-password.png)
[]![Entering the new root password for the Zscaler Index Tool VM](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-zscaler-index-tool-azure-vms/enter-new-password.png)
[]![The Download link for the Index Tool SSL Certificate in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/configuring-index-tool/ZIA-Download-Index-Tool-SSL-Certificate.png)
[]![zia-indextool-vm7.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm7.png)
[]![zia-indextool-vm8.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm8.png)
[]![zia-indextool-vm9.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm9.png)
[]When you have successfully configured the service, the service automatically downloads the latest build before it starts. To manually update the service:
- Enter the following command to stop the service:
sudo zadp stop
- Enter the following command to install the update:
sudo zadp update-now
- Enter the following command to start the service:
sudo zadp start
[]To run the Index Tool in explicit proxy mode:
- Log in to the VM as user `zsroot`.
- Enter the following command:
`sudo zadp configure-proxy`
- For `Do you require a proxy server configuration?`, enter `y` and press `Enter`.
- For `proxyserver`, enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport`, enter your proxy port number (e.g., `9443`) and press `Enter`.
The VM then tests the connection and when this is successful, the configuration is complete.
To remove the explicit proxy configuration:
- Enter the following command:
`sudo zadp configure-proxy`
- For `Do you require proxy server configuration?`, enter `n` and press `Enter`.
- For `Do you want to delete current proxy configuration?`, enter `y` and press `Enter`.
Requirements for Explicit Proxy Mode
If you're using explicit proxy mode, DNS and NTP connections are not tunneled, meaning, you need an internal DNS server to run in this mode. The Index Tool needs to have DNS resolution for the current Master CA IP, update server, and the NTP server. The Index Tool host also must be able to query a DNS server to resolve the following settings:
- smcacluster.<cloudname>
- update1.<cloudname>
- update2.<cloudname>
- zdistribute.<cloudname>
- The NTP server. By default, the Index Tool VM has the following FQDNs for NTP servers configured:
- 0.freebsd.pool.ntp.org
- 1.freebsd.pool.ntp.org
- 2.freebsd.pool.ntp.org
You can override these FQDNs to your internal IP address in your DNS server configuration or using other methods.
In addition, since the proxy configuration doesn't allow authentication, you need to configure the proxy server to allow specific IP/MAC addresses without user and password authentication.
The proxy server must also allow SSL bypass for communication from the VM to a specific set of IP addresses. These IPs are listed at config.zscaler.com/<cloudname>.net/edm. You can find your cloud name in the URL that your admins use to log in to the Zscaler service. For example, if an organization logs in to admin.zscalertwo.net, then that organization's cloud name is zscalertwo. So, you would go to config.zscaler.com/zscalertwo.net. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
[]To configure the Index Tool service to run without elevated privileges:
- Log in to the VM as user `zsroot`.
- Enter the following command to stop the service:
sudo zadp stop
- Open the `/sc/conf/sc.conf` file and update the value for `zadp_ui_port` to a port number higher than 1,000.
- Enter the following command to restart the service:
sudo zadp start
[]An admin can request remote assistance and allow Zscaler Support to log in to an Index Tool without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your Index Tool:
sudo zadp support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Index Tool.
- To disable Zscaler Support access to your Index Tool:
sudo zadp support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Index Tool:
sudo zadp support-access-status