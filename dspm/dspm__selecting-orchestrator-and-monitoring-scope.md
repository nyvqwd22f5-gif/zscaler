# Selecting the Orchestrator and Monitoring Scope
Source: https://help.zscaler.com/dspm/selecting-orchestrator-and-monitoring-scope
PDF: https://help.zscaler.com/pdf/com/en/1517986.pdf

After deploying the [tree discovery template](/dspm/deploying-azure-tree-discovery-template), select the network configuration, orchestrator, and monitoring scope.
Under **Orchestrator & Monitoring Scope**:
- [1. Select the network configuration.](#SelectNetworkConfiguration)
- [2. Configure the orchestrator.](#configureorchestrator-azure)
- [3. Set the monitoring scope.](#configuremonitoringscope-azure)
To modify the configured accounts, click **Reset**.
When you have configured the network and scopes successfully, you are directed to the [Additional Configuration](/tech-pubs-drafts/selecting-orchestrator-and-monitoring-scope-draft#additional-configuration-step) section.
[]In the **Additional Configuration** section, you can configure [custom tags](/dspm/managing-custom-tags) and [evidence storage](/dspm/managing-evidence-configuration). Click **Skip This Step **to configure the additional details after completing the onboarding process and go to [Deploy Orchestrator](/dspm/deploying-orchestrator-template) section.
[See image.](#additional-con-section)
- [Custom Tags](#singleaccount-customtags)
- [Evidence Storage](#singleacct-evidence)
After the configuration is completed, you are directed to the [Grant Permissions](/dspm/deploying-azure-onboarding-template) section to deploy the orchestrator template.
[]DSPM discovers files and tables containing sensitive data and generates snippets of evidence data to investigate and validate the findings. You can choose an existing storage account container or add a new one to store these evidence snippets.
The storage account container cannot be changed after it is added.
To add evidence storage:
- Click **Add Evidence Storage**.
-
On the **Evidence Configuration** page, select one of the following storage types:
- [Custom Managed Container](#single-custom-evidence)
- [Zscaler Managed Container](#single-zscaler-evidence)
[See image.](#evidenceconfig-zscaler)
[]You can use an existing storage account container to configure evidence data. DSPM uploads the snippet of evidence data into the specified container.
- **Storage Account Resource ID**: The resource ID of the storage account.
- **Container Name**: The name of the container.
- **Key Vault Resource ID**: The resource ID of the key vault. This key vault is used to encrypt the evidence data in the container.
[See image.](#evidenceconfig-custom)
[]DSPM creates a storage container in the orchestrator account to upload the snippet of evidence data.
[]Custom tags are attached to resources created by DSPM for easy identification.
To add custom tags:
- Click **Add Custom Tags**.
-
On the **Add Custom Tags** page, enter a key and value pair for the tag.
Ensure to [follow the guidelines](/dspm/managing-custom-tags) while entering key-value pairs for custom tags.
-
Click **Add More**, and enter key-value pairs to add more tags.
[See image.](#addcustomtags)
- Click **Done**.
You can add up to 15 tags to Private DNS zone resources. If only numerical values are included in the tag, they do not count towards the 15-tag limit, allowing for additional tags to be added.
For Managed Identity, only predefined tags are added.
[]You can choose any of the following network configurations:
- **Zscaler**: Use Zscaler resources to deploy the orchestrator and monitoring scope.
- **Custom**: Use your organization's resources to deploy the orchestrator and monitoring scope.
[See image.](#byon_config)
Changing the network configuration resets the existing configurations.
[]To configure the orchestrator, click **Configure Orchestrator**.
The orchestrator configuration depends on the network configuration you chose earlier.
- [If you selected the Zscaler network configuration](#zscaler_configuration)
- [If you selected the custom network configuration](#custom_configuration)
-
[]On the **Configure an Orchestrator Subscription** page:
- Select a subscription to deploy the orchestrator template.
- **Select Orchestrator Region**: Select the region.
-
[]**Storage Account Name**: Enter a unique name for the storage account. This storage account is created while deploying the [onboarding template](#azureonboardingtemplate) and is used to store the activity logs of the target subscriptions. DSPM validates the uniqueness of the storage account name. If the name is already registered with [Microsoft.Storage](#reg-microsoft-storage), DSPM displays an error message. [See image.](#storage-account-name-error)
The storage account name must not exceed 16 characters.
-
Select the **Deploy private endpoint for secure communication** checkbox to establish a private connection between DSPM and Azure resources. This restricts communication over public IP addresses.
You can also establish or remove the private connection after onboarding the tenant. On the **Overview **page, select **Manage Private Endpoint** from the **Manage **drop-down menu, and then select or deselect the checkbox.
[See image.](#configureorchsubscription)
- Click **Next**.
-
On the **Select which services to monitor** page, select the services that DSPM must monitor. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
- The **Unmanaged Database** service is disabled for Zscaler network configuration.
- DSPM automatically excludes Azure Storage accounts used for storing logs.
[See image.](#zscaler-services)
-
On the **Configure Regions for monitoring and scanner's configuration** page, select the regions that DSPM must monitor. DSPM creates and deploys resources required for scanning only in the selected regions.
Remember the [regions](#setdeploymentpage) that you selected as you need to specify them while deploying the orchestrator template.
[See image.](#configure-regions)
- Click **Done**.
-
[]On the **Configure an Orchestrator Subscription** page, select a subscription to deploy the orchestrator template, then provide the following details:
- **Select Orchestrator Region**: Select the region.
- **Subnet ID**: Enter the subnet where the orchestrator instances must be launched.
- **Network Security Group ID**: Enter the network security group for the orchestrator instance.
-
**Storage Account Name**: Enter a unique name for the storage account. This storage account is created while deploying the [onboarding template](#azureonboardingtemplate) and is used to store the activity logs of the target subscriptions. DSPM validates the uniqueness of the storage account name if [Microsoft.Storage](#reg-microsoft-storage) is registered. If the storage account name already exists, DSPM displays an error message. [See image.](#byon_storage-account-name-error)
The storage account name cannot exceed 16 characters.
-
Select the **Deploy private endpoint for secure communication** checkbox to establish a private connection between DSPM and Azure resources. This restricts communication over public IP addresses.
You can also establish or remove the private connection after onboarding the tenant. On the **Overview **page, select **Manage Private Endpoint** from the **Manage **drop-down menu, and then select or deselect the checkbox.
[See image.](#byonconfigureorchsubscription)
- Click **Next**.
-
On the **Select which services to monitor** page, select the services that DSPM must monitor. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
DSPM automatically excludes Azure Storage accounts used for storing logs.
[See image.](#byon-services)
-
On the **Configure Regions for monitoring and scanner's configuration** page:
-
For **Storage account**, specify whether you want to create storage accounts for each region or provide your own existing storage account details.
If you want to use your own existing storage account for scanning logs, disable this option and provide storage account details for each region. When enabled, DSPM follows the standard workflow by creating the storage account for scan logs.
This option is available only if **Storage** was selected on the [Select which services to monitor](#selectservices-to-monitor) page.
- Choose the regions that DSPM must monitor and enter the following details for each selected region. DSPM creates and deploys resources required for scanning only in the selected regions.
- **Subnet ID**: Enter the subnet where the scanner instances must be launched.
- **Network Security Group ID**: Enter the network security group for the scanner instance.
- **Postgres Delegated Subnet ID**: (Optional) Enter the Postgres subnet ID for the scanner instance. This option is available only if **Database** was selected on the [Select which services to monitor](#selectservices-to-monitor) page.
- **Storage Account Resource ID**: Enter the storage account name or account resource ID where you want to store the scanning logs.
Remember the [regions ](#setdeploymentpage)that you selected as you need to specify them while deploying the orchestrator template.
[See image.](#byonconfigure-regions)
- Click **Done**.
-
[]Click **Set Monitoring Scope**.
[See image.](#setmonitoringscopebutton)
-
On the **Configure Monitoring Scope** page:
- Select the target subscriptions that DSPM must monitor.
- Select the management group if all subscriptions must be scanned.
- Select **Autodetection** at the management group level if you want DSPM to automatically include and scan new subscriptions that are added to the management group in the future. This eliminates the need to manually onboard new subscriptions.
[See image.](#configuremonitoringscopepage)
- Click **Next.**
-
On the **Assign Business Units** page, assign a [business unit](/dspm/about-business-units) to the management group. All the subscriptions within the management group are mapped to the selected business unit.
[See image.](#assignbusinessunitspage)
The default business unit is assigned to the management group. You can [change the business unit](/dspm/changing-bu-mapping) for the management group if required, after completing the onboarding process.
- Click **Done**.
[]![The orchestrator & monitoring scope section with annotations around Network Configurations.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-network-configuration.png)
[]![The Configure an Orchestrator Subscription page displaying the hierarchy of the subscriptions and an error.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-storage-account-error01.png)
[]![The Configure an Orchestrator Subscription page displaying the hierarchy of the subscriptions and an error.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-storage-account-error01.png)
[]![Configure an Orchestrator Subscription page displaying the selected subscription, region, and storage account name.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-azure-configure-orch.png)
[]![The Configure an Orchestrator Subscription with the list of subscriptions, selected orchestrator subscription, orchestrator region, subnet ID, network security group ID, and storage account name.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/custom-dspm-configure-orch.png)
[]![The Orchestrator & Monitoring Scope section with annotation around Set Monitoring Scope button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-set-monitoring-scope-azure.png)
[]![The Configure Monitoring Scope section with the list of subscriptions selected for monitoring within the tenant.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-configure-monitoring-scope01.png)
[]![The Assign Business Units page with the subscriptions hierarchy and annotation around the list of business units.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-assign-bu01.png)
[]![The Add Custom Tags page with list of tags added.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-azure-customtags.png)
[]![The Configure Regions page with list of DSPM supported and selected regions.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-configure-regions-for-monitoring.png)
[]![The Configure regions for monitoring and scanner's configuration page with the list of Regions to monitor along with their subnet ID, Network Security Group ID, Postgres Delegated Subnet ID, and Storage Account Resource ID.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-byon-configure-regions-for-monitoring.png)
[]![The Azure services page with list of all supported services.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dsom-custom-services.png)
[]![The Azure services page with list of all supported services.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-azure-select-services.png)
[]
![The Additional Configuration section with annotation around Skip This Step.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-skip-this-step.png)
[]![The Evidence Configuration page for the customer managed container.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-azure-custom-evidence-config.png)
[]
![The Evidence Configuration page for the Zscaler managed container.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/selecting-orchestrator-and-monitoring-scope/dspm-zscaler-azure-evidence-config.png)