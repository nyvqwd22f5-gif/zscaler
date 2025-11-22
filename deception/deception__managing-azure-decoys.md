# Managing Azure Decoys
Source: https://help.zscaler.com/deception/managing-azure-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531509.pdf

You can manage your Microsoft Azure decoys from the Zscaler Deception Admin Portal. All decoys created from the Deception Admin Portal are tabulated under their respective decoy category tabs. Each table shows the details associated with each decoy in the category and also shows its deployment status. You can also edit or delete decoys by using the respective options from the decoys table.
Checking Deployment Status
At the time of integration, Zscaler Deception deploys a health check function on Azure. This function periodically checks all decoy resources deployed on Azure and updates their status to the Deception Admin Portal every 15 minutes. You can check the deployment status indicated by the icon next to the name of the decoy in the decoys table. The following icons are used to show the status of the decoys:
- ![Green status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-green-status-icon.png)
– Indicates a deployed state.
- ![Orange status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-orange-status-icon.png)
– Indicates an inactive state. This means the decoy no longer exists on Azure or one of its properties used to reference does not exist. This happens when the decoy or its resources are manipulated directly from Azure.
- ![Grey status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-grey-icon.png)
– Indicates a pending deployment state. This means that the decoy has been created or modified in the Deception Admin Portal, but the deployment script to propagate changes to the Azure Cloud has not been initiated.
- ![Red status icon](/downloads/deception/deceive/cloud-deception/aws-decoys/zscaler-deception-red-status-icon_0.png)
– Indicates a pending deletion state. This means that the decoy has been deleted from the Deception Admin Portal, but the deployment script to propagate changes to the Azure Cloud has not been initiated.
[See image.](#zd-azure-decoy-status)
Editing or Deleting Azure Decoys
You can edit or delete the Azure decoys that you configured in the Deception Admin Portal. Such changes made to the Azure decoys in the Deception Admin Portall are propagated to the Azure Cloud only after running the deployment script on the Azure Cloud Shell.
Prerequisites
Obtain the PowerShell command using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Editing an Azure Decoy
To edit an Azure decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure**.
- Select the relevant decoy category tab. For example, if you want to edit a user decoy, select the **User **tab.
-
Make sure that the decoy you want to edit is in the **Not Deployed** state, and then click the **Edit **icon.
[See image.](#zd-decoy-tabs-azure)
- Modify the decoy details as per your requirements.
- Click **Save**.
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#zd-launch-powershell-azure-setup-another)
The **Cloud Shell **window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy the preferred decoy and press `Enter`.
[See image.](#zd-run-script-setup-azure)
Upon successful execution of the script, the changes are propagated to the Azure Cloud.
Deleting an Azure Decoy
To delete an Azure decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure**.
- Select the relevant decoy category tab. For example, if you want to delete a user decoy, select the **User **tab.
-
Locate the decoy you want to delete, and click the **Delete **icon.
[See image.](#zd-decoy-tabs-azure-del)
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#zd-launch-powershell-azure-setup-another-delete)
The **Cloud Shell **window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy the preferred decoy and press `Enter`.
[See image.](#zd-run-script-setup-azure-delete)
Upon successful execution of the script, the changes are propagated to the Azure Cloud.
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/prerequisites-azure-decoy-deployment/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/setting-cloud-deception-microsoft-azure/zscaler-deception-azure-powershell-script-run.png)
[]![A screenshot captruting various Azure decoy tabs](/downloads/deception/deceive/cloud-deception/azure/managing-azure-decoys/deception-edit-a-decoy-option.png)
[]![A screenshot captruting various Azure decoy tabs](/downloads/deception/deceive/cloud-deception/azure/managing-azure-decoys/deception-delete-cloud-decoy-option.png)
[]![A screenshot capturing Azure Decoy Status Icons](/downloads/deception/deceive/cloud-deception/azure/managing-azure-decoys/deception-status-decoys-azure.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/prerequisites-azure-decoy-deployment/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/setting-cloud-deception-microsoft-azure/zscaler-deception-azure-powershell-script-run.png)