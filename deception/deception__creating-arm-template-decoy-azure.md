# Creating an ARM Template Decoy in Azure
Source: https://help.zscaler.com/deception/creating-arm-template-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531495.pdf

Azure Resource Manager (ARM) templates are JSON files that define the infrastructure and configuration for your project. It is an Infrastructure as Code (IaC) solution to create, update, and deploy Microsoft Azure resources. You can create ARM template decoys with embedded lures for other Azure identity-based decoys such as user decoys, service principal decoys, and Azure IaaS URLs that belong to key vault and storage account file shares. The ARM template decoys act as cloud lures. The ARM template decoys can detect the following attack paths:
- Plaintext Credentials: Adversaries look at ARM template specs for exposed credentials.
- Deployment History: Create a failed deployment from this template. Adversaries look at deployment histories to find templates (which might have been deleted) with exposed credentials.
Prerequisites
Before creating an ARM decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating an ARM Template Decoy
To create an ARM template decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **ARM Template**.
-
Click **Add Decoy**.
[See image.](#zd-azure-tab-arm)
The **ARM Template Decoy** window appears.
-
In the **ARM Template** **Decoy** window:
- **Name: **Enter a name for the ARM template decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the ARM template decoy.
- **Azure User**: Select an Azure user decoy that must be added to the pseudo-entry in Azure history. This user must be from the selected subscription.
- **Azure Service Principal**: Select an Azure service principal decoy that must be added to the pseudo-entry in Azure history. This service principal must be from the selected subscription.
- **Azure Key Vault**: Select an Azure key vault decoy that must be added to the pseudo-entry in Azure history. This key vault must be from the selected subscription.
- **Azure File Share**: Select an Azure file share decoy that must be added to the pseudo-entry in Azure history. This file share must be from the selected subscription.
- **Create Deployment History**: Enable to add a pseudo-entry mimicking a deployment in Azure’s history.
[See image.](#zd-arm-template-decoy-add)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-arm)
The **Cloud Shell** window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy ARM template decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-arm)
If you want to add multiple ARM template decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the ARM template decoy is added to Microsoft Azure. The ARM template decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). The deployment status is indicated by the icon next to the name of the decoy in the ARM template decoys table (Deceive > Cloud Deception > Azure > ARM Template) within the Zscaler Deception Admin Portal. To learn how to configure lures using ARM template decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the ARM Template tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-arm-template-decoy-azure/deception-add-arm-decoy.png)
[]![A screenshot capturing the ARM Template Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-arm-template-decoy-azure/deception-arm-template-decoy-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-arm.png)