# Creating an App Service Decoy in Azure
Source: https://help.zscaler.com/deception/creating-app-service-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531491.pdf

Microsoft Azure App Service is an HTTP-based service for hosting web applications, REST APIs, and mobile back ends. You can create an app service decoy application and lure attackers. The most effective way to lure attackers using app service decoys is to add these app service decoys to a [landmine policy](/deception/about-policies). The app service decoys can detect the following attack paths:
- Web Shell: You can host a web shell that adversaries use to execute commands. Any command executed via the web shell is detected and logged as an attack.
- Kudu Endpoint: Every app service hosts a buddy site or kudu endpoint that can be exploited by adversaries (if misconfigured) to execute commands on the host server hosting the app service. Any command executed via the kudu endpoint is detected and logged as an attack.
- Managed Identity: A managed identity is attached to the app service that has access to all other decoys in the decoy resource group. Adversaries can steal the token of this managed identity to attempt privilege escalation. Such attempts are detected and logged as an attack.
Prerequisites
Before creating an app service decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler [[variable:deception]](/deception/setting-cloud-deception-microsoft-azure)].
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating an App Service Decoy
To create an app service decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **App Service**.
-
Click **Add Decoy**.
[See image.](#zd-azure-as-tab)
The **App Service Decoy** window appears.
-
In the **App Service Decoy** window:
- **Name**: Enter a name for the app service decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the app service decoy.
[See image.](#zd-add-app-service)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-as)
The **Cloud Shell** window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy app service decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-as)
If you want to add multiple app service decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the app service decoy is added to Microsoft Azure under the Decoys Resource Group configured by [[variable:deception]] [during the integration](/deception/setting-cloud-deception-microsoft-azure). In addition, **URI **and **Source Control Manager URI** are generated and associated with the app service decoys automatically. The deployment status is indicated by the icon next to the name of the decoy in the app service decoys table (Deceive > Cloud Deception > Azure > App Service) within the Zscaler Deception Admin Portal. The **URI **and **Source Control Manager URI **values are also shown in the app service decoys table. To learn how to configure lures using app service decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the App Service tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-app-service-decoy-azure/deception-add-decoy-button-app-service.png)
[]![A screenshot capturing the App Service Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-app-service-decoy-azure/app-service-decoy-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-as.png)