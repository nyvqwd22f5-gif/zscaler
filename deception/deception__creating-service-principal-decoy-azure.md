# Creating a Service Principal Decoy in Azure
Source: https://help.zscaler.com/deception/creating-service-principal-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531489.pdf

Service principals are identities created for use with applications, hosted services, and automated tools to access Microsoft Azure resources. You can create service principal decoys with credentials attached to them. Any attempt to sign in using the credentials of the service principals will be detected as an attack or compromise. These service principal decoys have access to all other Azure decoys that are part of the decoy resource group (Decoys Resource Group) [configured by Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure). The most effective way to lure attackers using decoy users is to add these decoy users to a [landmine policy](/deception/about-policies).
Prerequisites
Before creating a service principal decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Service Principal Decoy
To create a service principal decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Service Principal**.
-
Click **Add Decoy**.
[See image.](#zd-azure-sp-tab)
The **Service Principal Decoy** window appears.
-
In the **Service Principal Decoy** window:
- **Name**: Enter a name for the service principal decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Description**: Enter a description relevant to the service principal decoy.
[See image.](#zd-azure-service-principal)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell)
The **Cloud Shell **window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy service principal decoys and press `Enter.`
[See image.](#zd-azure-deployment-script)
If you want to add multiple service principal decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
-
Enable Azure AD (Entra ID) diagnostic settings:
-
In the Azure Portal, click **Azure Active Directory**.
[See image.](#zd-ad-option-azure-sp)
- Go to** Monitoring **> **Diagnostic settings**.
-
Click **Add diagnostic setting**.
[See image.](#zd-ds-add-option-azure-sp)
The **Diagnostic setting **window appears.
- In the **Diagnostic setting **window:
- Enter a **Diagnostic setting** name.
- Under the **Logs **section, select the **ServicePrincipalSignInLogs** checkbox to configure a data source for sending the logs to the logging storage account created as a part of the integration.
-
Under the **Destination details **section, select the **Archive to storage account **checkbox,** **and select the storage account created as part of the integration from the **Storage account **drop-down menu.
[See image.](#zd-ds-configuration-azure-sp)
- Click **Save**.
This configuration is not handled via the deployment script, as enabling diagnostic settings via API requires a P1 or P2 subscription.
Upon successful execution of the script, the service principal decoy is added to Microsoft Azure under the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). In addition, a **Client ID **is also associated with the service principal automatically. The deployment status is indicated by the icon next to the name of the decoy in the service principal decoys table (Deceive > Cloud Deception > Azure > Service Principal) within the Zscaler Deception Admin Portal.
To learn how to configure lures using service principal decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Service Principal tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-service-principal-decoy-azure/deception-add-decoy-button.png)
[]![A screenshot capturing the Azure Service Principal Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-service-principal-decoy-azure/deception-service-principal-app.png)
[]![A screenshot captruing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-sp.png)
[]![A screenshot capturing the Azure AD option within Azure Portal](/downloads/deception/deceive/cloud-deception/azure/creating-user-decoy-azure/zscaler-deception-azure-ad.png)
[]![A screenshot capturing the Diagnostic Settings in Azure Portal](/downloads/deception/deceive/cloud-deception/azure/creating-user-decoy-azure/zscaler-deception-add-diagnostic-setting.png)
[]![A screenshot capturing the Diagnostic Settings Configuation in Azure](/downloads/deception/deceive/cloud-deception/azure/creating-service-principal-decoy-azure/zscaler-deception-ds-Azure-service-principal.png)