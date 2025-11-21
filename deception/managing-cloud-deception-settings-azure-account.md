# Managing Cloud Deception Settings for an Azure Account
Source: https://help.zscaler.com/deception/managing-cloud-deception-settings-azure-account
PDF: https://help.zscaler.com/pdf/com/en/1531564.pdf

Editing an Azure Account
You can edit a Microsoft Azure account from the Zscaler Deception Admin Portal. Depending on whether the configurations are already propagated to Azure, the editing is either a single-step process (if the deployment script was never used on Azure) or a two-step process (if the deployment script was used at least once).
- [Step 1: In the Deception Admin Portal](#edit-admin-portal)
- [Step 2: In the Microsoft Azure Portal](#edit-azure-portal)
Deleting an Azure Account
You can delete Cloud Deception settings configured for a Microsoft Azure account from the Deception Admin Portal. Depending on if the configurations are already propagated to Azure, the deletion is either a single-step process (if the deployment script was never used on Azure) or a two-step process (if the deployment script was used at least once).
You can delete Azure Cloud Deception settings only if no Azure decoys are deployed. If you have already deployed Azure decoys, you must delete all decoys and run the deployment script first before deleting the settings.
- [Step 1: In the Deception Admin Portal](#zd-deception-portal-azure-delete)
- [Step 2: In the Microsoft Azure Portal](#zd-azure-portal-delete)
[]To initiate editing in the Deception Admin Portal:​​​​​
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Settings**.
-
Locate the account that you want to edit, and click the **Edit **icon.
[See image.](#edit-icon-image)
The **Azure Account Setting** window appears.
-
In the **Azure Account Setting **window:
- **Enabled**: Select to modify the status of Cloud Deception for the Azure account.
- **Region**: Select a new region for the Azure account from the drop-down menu.
- **Decoy Manager Resource Group**: Enter a new name or update the existing one.
[See image.](#edit-window-image)
- Click **Save**.
[]To complete editing in the Azure Portal:
- Sign in to the [Azure Portal](http://https//portal.azure.com).
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#cloudshell-edit-option)
The **Cloud Shell** window appears.
- In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to sync settings.
[]To initiate deletion in the Deception Admin Portal:​​​​​
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Settings**.
-
Locate the Azure account that must be deleted, and click the **Delete **icon.
[See image.](#zscaler-deception-azure-delete-option)
All fields are deleted, and the configuration is disabled in the Deception Admin Portal.
If you have never run the deployment script on Azure, then the deletion process is completed with this step. If you have already used the deployment script either to sync the settings or deploy decoys, then proceed to Step 2 to complete the deletion process.
[]To complete deletion in the Azure Portal:
- Sign in to the [Azure Portal](http://https//portal.azure.com).
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-powershell-launch-azure)
The **Cloud Shell** window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
-
When prompted to continue with deletion, enter `y` and press `Enter.`
If you enter `n` and press `Enter`, then the deletion process is aborted, and the configuration is enabled again in the Deception Admin Portal.
[See image.](#zd-delete-azure-prompt)
All resources created for [setting up Cloud Deception with Azure](/deception/setting-cloud-deception-microsoft-azure) are deleted.
In some cases, the deployment script might fail to remove the entries of the Azure resources that were marked for deletion in the Deception Admin Portal. For example, manually removing Azure resources deployed by Deception from the Azure cloud can fail to remove entries of resources from the Deception Admin Portal if the resources are interdependent. If the deployment script fails to remove these entries, you need to use the **Force Delete **option.
- [Steps to Force Delete Azure Settings](#force-delete-azure-settings)
- []In the Deception Admin Portal, go to **Deceive **> **Cloud Deception **> **Azure **> **Settings**.
-
Click **Force Delete**. This option appears when the deletion process is started.
[See image.](#force-delete-button)
-
Confirm your action.
The Azure resource entries are removed from the Deception Admin Portal.
[]![List of Azure accounts with the option to edit settings highlighted](/downloads/deception/deceive/cloud-deception/azure/managing-cloud-deception-settings-azure-account/deception-edit-azure-settings.png)
[]![Azure Account Setting window with editable fields highlighted](/downloads/deception/deceive/cloud-deception/azure/deleting-azure-deception-settings/deception-edit-fields.png)
[]![A screenshot capturing the prompt for deleting Azure resources](/downloads/deception/deceive/cloud-deception/azure/deleting-azure-deception-settings/zscaler-deception-azure-delete-script.png)
[]![A screenshot capturing the delete option in Azure Cloud Decpetion Settings](/downloads/deception/deceive/cloud-deception/azure/managing-cloud-deception-settings-azure-account/deception-delete-azure-settings.png)
[]![A screenshot capturing the option launch Cloud Shell in Azure](/downloads/deception/deceive/cloud-deception/azure/deleting-azure-deception-settings/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the prompt for deleting Azure resources](/downloads/deception/deceive/cloud-deception/azure/deleting-azure-deception-settings/zscaler-deception-azure-delete-script.png)
[]
![A screenshot highlighting the Force Delete option for Azure Settings](/downloads/deception/deceive/cloud-deception/azure/deleting-azure-deception-settings/zscaler-deception-force-delete-azure_0.png)