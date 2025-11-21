# Managing Services
Source: https://help.zscaler.com/dspm/managing-services
PDF: https://help.zscaler.com/pdf/com/en/1517576.pdf

After [onboarding a tenant](/dspm/onboarding-microsoft-azure-tenant), you can select the services that must be scanned by DSPM. DSPM permissions are restricted to monitor and scan the data only in the selected services.
To select the services:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account.
-
Click **Manage**, and then select **Manage Services**.
[See image.](#manageservices)
-
On the **Manage Services to Monitor** page, select the services that must be monitored and scanned.
[See image.](#manageservicestomonitor)
The **Unmanaged Database** option is enabled only if the organization or tenant was onboarded via [custom configuration](/dspm/onboarding-microsoft-azure-tenant).
- Click **Next**.
-
In the **Configure regions for monitoring and scanner's configuration **page, select the region where the orchestrator template must be deployed and provide the corresponding region details based on the network configuration selected.
[See image.](#configureregions-monitoring)
-
On the **Apply Changes** page, download and deploy the template.
[See image.](#download-azure-template)
[]![Manage menu listing all the actions available for a tenant and annotation around Manage Services option.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-services/dspm-manage-services.png)
[]![Manage Services to Monitor page with a list of Azure services.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-services/dspm-manage-azure-services.png)
[]![The Configure regions page listing the DSPM supported regions that must be monitored.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-services/dspm-configure-reg-byon-manage-services.png)
[]![The Apply changes page showing the Azure Onboarding template that must be downloaded and deployed.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-services/dspm-azure-onboarding-template.png)