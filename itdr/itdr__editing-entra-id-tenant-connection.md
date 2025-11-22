# Editing an Entra ID Tenant Connection
Source: https://help.zscaler.com/itdr/editing-entra-id-tenant-connection
PDF: https://help.zscaler.com/pdf/com/en/1531776.pdf

You can edit the Entra ID tenant connections configured in the Zscaler ITDR Admin Portal. All Entra ID tenants connected to the ITDR Admin Portal are listed on the Entra ID page.
To edit an Entra ID tenant connection:
- Go to **ITDR** > **Manage **> **Entra ID**.
-
Locate the Entra ID tenant that you want to edit.
Confirm if the tenant is connected to the ITDR Admin Portal by checking if the **Tenant ID**, **Client ID**, and **Storage Account **values** **are populated for the tenant. If the values are populated, the tenant is connected with the ITDR Admin Portal. Otherwise, the tenant is not connected.
-
Click the **Edit **icon for the tenant under the **Actions **column.
[See image.](#edit-option-entra-id)
The **Tenant Details **window appears.
-
In the **Tenant Details** window, modify the fields as required.
[See image.](#tenant-details-window)
If the tenant is not connected with the ITDR Admin Portal, then you can edit all fields. However, if the tenant is connected with the portal, then you can only modify the **Scan Frequency**, **Scan Time**, and **Scan Timeout **fields.
- Sign in to the [Azure Portal](http://https//portal.azure.com) as a Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#cloud-shell-icon)
The **Cloud Shell** window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/itdr/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/itdr/obtaining-deployment-script-azure#zd-manual-download-script).
-
Enter the option to deploy the resources and press `Enter`.
[See image.](#deploy-resources-cloud-shell)
Upon successful execution of the script, the changes are propagated to the Entra ID tenant.
[]
![The Edit option for Entra ID Tenant](/downloads/itdr/scan-configuration/entra-id-posture-scan/editing-entra-id-tenant-connection/itdr-entra-ID-edit-tenant.png)
[]
![The Tenant Details window](/downloads/itdr/scan-configuration/entra-id-posture-scan/editing-entra-id-tenant-connection/Tenant%20Details.png)
[]
![The Cloud Shell icon in Azure Portal](/downloads/itdr/scan-configuration/entra-id-posture-scan/editing-entra-id-tenant-connection/zscaler-deception-azure-powershell-launch%20(1).png)
[]![The Deploy Resources option in Azure Cloud Shell](/downloads/itdr/scan-configuration/entra-id-posture-scan/editing-entra-id-tenant-connection/deploy-resources-itdr.png)