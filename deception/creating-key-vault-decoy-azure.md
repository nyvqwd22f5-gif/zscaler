# Creating a Key Vault Decoy in Azure
Source: https://help.zscaler.com/deception/creating-key-vault-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531494.pdf

A key vault is a service in Microsoft Azure that allows you to securely store and retrieve secrets such as passwords, API keys, cryptographic keys, etc. You can create a key vault decoy that includes enticing credential files with URLs to the [Threat Intelligence (TI) decoys](/deception/about-threat-intelligence-decoys) containing random user names and passwords. These decoys act as cloud lures.
Prerequisites
Before creating a key vault decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Key Vault Decoy
To create a key vault decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Key Vault**.
-
Click **Add Decoy**.
[See image.](#zd-azure-tab-kv)
The **Key Vault Decoy** window appears.
-
In the** Key Vault Decoy** window:
- **Name**: Enter a name for the key vault decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the key vault decoy.
[See image.](#zd-add-key-vault-azure)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-kv)
The **Cloud Shell** window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy key vault decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-kv)
If you want to add multiple key vault decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the key vault decoy is added to Microsoft Azure. The key vault decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). The deployment status is indicated by the icon next to the name of the decoy in the key vault decoys table (Deceive > Cloud Deception > Azure > Key Vault) within the Zscaler Deception Admin Portal. To learn how to configure lures using key vault decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Key Vault tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-key-vault-decoy-azure/deception-add-decoy-key-vault.png)
[]![A screenshot capturing the Key Vault Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-key-vault-decoy-azure/deception-key-vault-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-kv.png)