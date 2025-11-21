# Creating a Managed Identity Decoy in Azure
Source: https://help.zscaler.com/deception/creating-managed-identity-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531490.pdf

Managed identities provide an automatically managed identity in Azure AD (Entra ID) for applications to use when connecting to resources that support Azure AD (Entra ID) authentication. You can create a managed identity decoy (user-defined) that has access to all other decoy resources in a decoy resource group (Decoys Resource Group) [configured by Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure). This managed identity decoy can be attached to your production resources. It can also be included in your deployment templates to add deception capabilities to your production resources. If an adversary compromises any of the production resources, they will be lured toward the decoys.
To learn about the list of Azure services that can be attached to managed identities, refer to the [Microsoft Technical Documentation](https://www.google.com/url?q=https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/managed-identities-status%23services-supporting-managed-identities&sa=D&source=docs&ust=1690783640140469&usg=AOvVaw23RfBJmYz2ZT5ILux1DJoh).
Deception does not associate the managed identity with any production resources.
Prerequisites
Before creating a managed identity decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Managed Identity Decoy
To create a managed identity decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Managed Identity**.
-
Click **Add Decoy**.
[See image.](#zd-azure-mi-tab)
The** Managed Identity Decoy** window appears.
-
In the** Managed Identity Decoy** window:
- **Name**: Enter a name for the managed identity decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the managed identity decoy.
[See image.](#zd-managed-identity)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-poweshell-option-azure-managed-identity)
The **Cloud Shell **window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy managed identity decoys and press `Enter`.
[See image.](#zd-azure-script-managed-identity)
If you want to add multiple managed identity decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the managed identity decoy is added to Microsoft Azure under the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). The deployment status is indicated by the icon next to the name of the decoy in the managed identity decoys table (Deceive > Cloud Deception > Azure > Managed Identity) within the Zscaler Deception Admin Portal. To learn how to configure lures using managed identity decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Managed Identity tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-managed-identity-decoy-azure/deception-add-decoy-managed-identity.png)
[]![A screenshot capturing Managed Identity Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-managed-identity-decoy-azure/deception-managed-identity-decoy-window.png)
[]![A screenshot captruing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-mi.png)