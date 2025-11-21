# Managing Resource Groups in Azure
Source: https://help.zscaler.com/deception/managing-resource-groups-azure
PDF: https://help.zscaler.com/pdf/com/en/1531616.pdf

You can view or delete resource groups created to hold decoys from the Zscaler Deception Admin Portal. The list of all resource groups created by Zscaler Deception in the Microsoft Azure portal is displayed on the Resource Group Management tab (Deceive > Cloud Deception).
[See image.](#resource-group-list)
To delete resource groups:
- Go to **Deceive **> **Cloud Deception **> **Resource Group Management**.
-
Locate the resource group that you want to delete, and click the **Delete **icon.
[See image.](#delete-icon-resource-group)
-
In the confirmation window, click **OK**.
If the deleted resource group was not already created in the Azure portal (indicated by **No **in the **Created **column), the deletion is complete and you can skip the following steps.
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#cloud-shell-option)
The **Cloud Shell **window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to sync settings and press `Enter`.
[See image.](#cloud-shell-sync-settings)
[]![List of all resource groups](/downloads/deception/deceive/cloud-deception/azure/managing-resrource-groups-azure/deception-resource-group-tab.png)
[]![List of resource groups with the option to delete a group highlighted](/downloads/deception/deceive/cloud-deception/azure/managing-resrource-groups-azure/deception-delete-resource-groups.png)
[]![Azure portal with option tolaunch Cloud Shell highlighted](/downloads/deception/deceive/cloud-deception/azure/managing-resrource-groups-azure/zscaler-deception-azure-powershell-launch%20(2).png)
[]![Running deployment script](/downloads/deception/deceive/cloud-deception/azure/managing-resrource-groups-azure/zscaler-deception-azure-powershell-script-run%20(2).png)