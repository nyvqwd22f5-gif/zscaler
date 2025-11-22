# Managing Orchestrator Network
Source: https://help.zscaler.com/dspm/managing-orchestrator-network
PDF: https://help.zscaler.com/pdf/com/en/1514781.pdf

You can modify the orchestrator network details when an existing orchestrator network is being decommissioned, deleted, or if an incorrect network was selected during onboarding. After changing the orchestrator network, you must rerun the orchestrator template to update the deployment. DSPM validates the template deployment and updates the [orchestrator status](/dspm/viewing-orchestrator-status) accordingly.
This option is available only when the DSPM Connection Status is failed for the custom network configuration type.
Prerequisites
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or a custom role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
Modifying the Orchestrator Network
To modify the orchestrator network configuration:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account.
-
From the **Manage** drop-down menu, select **Managing Orchestrator Networks**.
[See image.](#manage_orch_network)
- On the **Manage Orchestrator Networks** page, update the orchestrator network:
- [AWS](#aws)
- [Azure](#azure)
- Click **Done**.
After the templates are deployed, the regions are updated in the DSPM Admin Portal and subsequent data scans are performed on the resources in the selected regions.
- []**Select Orchestrator Region**: Select a region where you want to deploy the orchestrator template.
- **Subnet ARN**: Enter the subnet where the scanner instances must be launched.
-
**Security Group ID**: Enter the identifier (ID) of the security group that controls network traffic to and from the instances.
[See image.](#config_orch_details_aws)
- Click **Next**.
-
On the **Apply Changes** page, [download and run the orchestrator template](/dspm/onboarding-aws-organization#orchestrator-template-step4).
[See image.](#orch_apply_changes_aws)
- []**Select Orchestrator Region**: Select a region where you want to deploy the orchestrator template.
- **Subnet ID**: Enter the subnet where the scanner instances must be launched.
- **Network Security Group ID**: Enter the identifier (ID) of the security group that controls network traffic to and from the instances.
-
**Storage Account Name**: Enter a unique name for the storage account. This storage account is used to store the activity logs of the target subscriptions and is created while deploying the [onboarding template](/dspm/onboarding-microsoft-azure-tenant#azureonboardingtemplate). DSPM validates the uniqueness of the storage account name. If the name is already registered with [Microsoft.Storage](/dspm/onboarding-microsoft-azure-tenant#reg-microsoft-storage), DSPM displays an error message. [See image.](#byon_storage-account-name-error)
The storage account name must not exceed 16 characters.
[See image.](#config_orch_details_azure)
- Click **Next**.
-
On the **Apply Changes** page, [download and run the orchestrator template](/dspm/onboarding-microsoft-azure-tenant#grantpermission).
If you are using a new subnet from a different VNet, run the following command before deploying the new template:
`terraform destroy -target module.scale_set.azurerm_linux_virtual_machine_scale_set.orchestrator_scale_set`
[See image.](#orch_apply_changes_azure)
[]![Configuring Region Networks](/downloads/dspm/administration/cloud-account-management/managing-orchestrator-network/manage_orch_networks.png)
[]![Configuring Region Networks Page](/downloads/dspm/administration/cloud-account-management/managing-orchestrator-network/img_config_orch_details.png)
[]![Downloading the Azure Onboarding Template](/downloads/dspm/administration/cloud-account-management/managing-orchestrator-network/orch_applychanges.png)
[]![Configuring Region Networks Page](/downloads/dspm/administration/cloud-account-management/managing-orchestrator-network/config_orch_details_aws.png)
[]![Downloading the Azure Onboarding Template](/downloads/dspm/administration/cloud-account-management/managing-orchestrator-network/orch_apply_changes_aws.png)
[]![Storage Account name error](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-storage-account-error01.png)