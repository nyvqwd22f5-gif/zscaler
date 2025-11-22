# Deleting an Entra ID Tenant Connection
Source: https://help.zscaler.com/itdr/deleting-entra-id-tenant-connection
PDF: https://help.zscaler.com/pdf/com/en/1531775.pdf

You can delete the Entra ID tenant connections configured in the Zscaler ITDR Admin Portal. All Entra ID tenants connected to the ITDR Admin Portal are listed on the Entra ID page.
To delete an Entra ID tenant connection:
- Go to **ITDR** > **Manage **> **Entra ID**.
-
Locate the Entra ID tenant that you want to delete.
Confirm if the tenant is connected to the ITDR Admin Portal by checking if the **Tenant ID**, **Client ID**, and **Storage Account **values** **are populated for the tenant. If the values are populated, the tenant is connected with the ITDR Admin Portal. Otherwise, the the tenant is not connected.
-
Click the **Delete **icon for the tenant under the **Actions **column.
[See image.](#delete-tenant-itdr)
-
In the confirmation window, click **OK**.
The Entra ID tenant is removed from the ITDR Admin Portal.
-
If the tenant is connected with the ITDR Admin Portal, complete the removal of resources deployed by Zscaler ITDR in Entra ID by following these steps:
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#cloud-shell-option)
The **Cloud Shell **window appears.
- In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/itdr/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/itdr/obtaining-deployment-script-azure#zd-manual-download-script).
-
Enter the option to undeploy resources and press `Enter`.
[See image.](#undeploy-resources-shell)
Upon successful execution of the script, the resources deployed by ITDR are removed from the Entra ID tenant.
[]
![The Delete option for Entra ID tenant](/downloads/itdr/scan-configuration/entra-id-posture-scan/deleting-entra-id-tenant-connection/itdr-entra-ID-delete-tenant.png)
[]
![The Cloud Shell option in Azure](/downloads/itdr/scan-configuration/entra-id-posture-scan/deleting-entra-id-tenant-connection/zscaler-deception-azure-powershell-launch%20(1).png)
[]
![The Undeploy Resources option in Azure](/downloads/itdr/scan-configuration/entra-id-posture-scan/deleting-entra-id-tenant-connection/itdr-undeploy-deploy-resources-itdr.png)