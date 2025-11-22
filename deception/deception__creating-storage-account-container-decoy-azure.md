# Creating a Storage Account Container Decoy in Azure
Source: https://help.zscaler.com/deception/creating-storage-account-container-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531492.pdf

A storage account container in Microsoft Azure is a type of cloud storage used for storing unstructured data. You can create storage account container decoys and associate [file datasets](/deception/about-file-datasets) with them. Optionally, these storage account container decoys can be added to a [landmine policy](/deception/about-policies) to add lures on the endpoints. The storage account container decoys can detect the following attack paths:
- Public: Adversaries can enumerate public storage accounts using keywords related to an organization to find exposed storage account containers on the internet in an attempt to steal sensitive data.
- Private: Adversaries with compromised identities of your organization can target storage account containers that are accessible via the compromised identities.
Prerequisites
Before creating a storage account container decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Storage Account Container Decoy
To create a storage account container decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Storage Account Container**.
-
Click **Add Decoy**.
[See image.](#zd-azure-aws-tab)
The **Storage Account Container Decoy** window appears.
-
In the **Storage Account Container Decoy** window:
- **Name**: Enter a name for the storage account container decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Storage Account**: Enter the name of the storage account to which you want to add the container.
- **ACL**: Use the drop-down menu to select your preferred access control list for the container decoy:
- **Container**: Allows anonymous access to the container and blobs.
- **Blob**: Allows anonymous access only to the blobs.
- **Private**: Doesn't allow anonymous access to the container and blobs.
- **Description**: Enter a description relevant to the storage account container decoy.
- **File Dataset**: Select a file dataset that you want to be hosted within the container.
[See image.](#zd-add-sac-azure)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-sac)
The **Cloud Shell **window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy storage container decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-sac)
If you want to add multiple storage account container decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the storage container decoy is added to Microsoft Azure. The storage container decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). The deployment status is indicated by the icon next to the name of the decoy in the storage account container decoys table (Deceive > Cloud Deception > Azure > Storage Account Container) within the Zscaler Deception Admin Portal. To learn how to configure lures using storage container decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Storage Account Container tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-storage-account-container-decoy-azure/deception-sac-add-button.png)
[]![A screenshot capturing Storage Account Container Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-storage-account-container-decoy-azure/deception-sac-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run--sac.png)