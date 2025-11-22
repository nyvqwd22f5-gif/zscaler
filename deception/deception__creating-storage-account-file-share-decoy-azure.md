# Creating a Storage Account File Share Decoy in Azure
Source: https://help.zscaler.com/deception/creating-storage-account-file-share-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531493.pdf

A storage account file share in Microsoft Azure is a file share service mountable on endpoints and can be Server Message Block (SMB) protocol or Network File System (NFS) protocol. Zscaler Deception allows you to create storage account file share decoys that include decoy file datasets and mount them on endpoints to lure adversaries.
Prerequisites
Before creating a storage account file share decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Storage Account File Share Decoy
To create a storage account file share decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Storage Account File Share**.
-
Click **Add Decoy**.
[See image.](#zd-azure-safs-tab)
The **Storage Account File Share Decoy** window appears.
-
In the **Storage Account File Share Decoy** window:
- **Name**: Enter a name for the storage account file share decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Storage Account**:** **Enter the name of the storage account to which you want to add the file share.
- **Description**: Enter a description relevant to the storage account file share decoy.
- **File Dataset**: Select a file dataset that you want to be hosted in the file share.
[See image.](#zd-add-safs-azure)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com).
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-fs)
The **Cloud Shell **window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy storage account file share decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-fs)
If you want to add multiple storage account file share decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the storage account file share decoy is added to Microsoft Azure. The file share decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). The deployment status is indicated by the icon next to the name of the decoy in the storage account file share decoys table (Deceive > Cloud Deception > Azure > Storage Account File Share) within the Zscaler Deception Admin Portal. To learn how to configure lures using storage account file share decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Storage Account File Share tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-storage-account-file-share-decoy-azure/deception-add-decoy-safs.png)
[]![A screenshot capturing the Storage Account File Share Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-storage-account-file-share-decoy-azure/deception-safs-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-safs.png)