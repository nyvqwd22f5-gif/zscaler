# Creating a VM Image Decoy in Azure
Source: https://help.zscaler.com/deception/creating-vm-image-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531497.pdf

A virtual machine (VM) image is a collection of metadata and pointers to a set of VHDs (one VHD per disk) stored as page blobs in Azure Storage. You can create a VM image decoy snapshot (public or private) that creates a VM temporarily in Azure, adds a callback script for detection, and creates a snapshot. Adversaries enumerate public Azure snapshots with keywords related to your organization with the intention of stealing and accessing the file system to extract credentials and exfiltrate sensitive data by booting up the VM in their environment.
Prerequisites
Before creating a VM image decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a VM Image Decoy
To create a VM image decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **VM Image**.
-
Click **Add Decoy**.
[See image.](#zd-azure-user-tab)
The **VM Image** **Decoy** window appears.
-
In the **VM Image Decoy** window:
- **Name**: Enter a name for the VM image decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the VM image decoy.
- **Visibility**: Select **Public** from the drop-down menu** **if you want the VM image to be accessible to anyone using Disk URI. Otherwise, select **Private **to limit access to the VM image to internal adversaries.
[See image.](#zd-add-azure-vm-decoy)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-vm)
The **Cloud Shell **window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy VM image decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-vm)
If you want to add multiple VM image decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the VM image decoy is added to Microsoft Azure. The VM image decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). In addition, the **Disk URI** is generated and associated with the VM image automatically. The deployment status is indicated by the icon next to the name of the decoy in the VM image decoys table (Deceive > Cloud Deception > Azure > VM Image) within the Zscaler Deception Admin Portal. The **Disk URI** value is also shown in the VM image decoys table. To learn how to configure lures using VM image decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the User tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-vm-image-decoy-azure/deception-vm-image-decoy-add.png)
[]![A screenshot capturing the VM Image Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-vm-image-decoy-azure/deception0vm-image-decoy-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-vmi.png)