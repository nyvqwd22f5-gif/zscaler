# Changing an Orchestrator Subscription
Source: https://help.zscaler.com/dspm/changing-orchestrator-subscription
PDF: https://help.zscaler.com/pdf/com/en/1479311.pdf

DSPM uses the [orchestrator template](/dspm/understanding-orchestrator) that is deployed on the Azure subscription to scan the data stores.
You can change the orchestrator subscription if the existing orchestrator subscription is being decommissioned, deleted, or if an incorrect subscription was selected while onboarding. When you change the orchestrator subscription, you must run the orchestrator template in the new subscription. DSPM validates the template deployment and updates the [orchestrator status](/dspm/viewing-orchestrator-status) accordingly.
Until the new orchestrator subscription is successfully validated, the following changes occur:
- The existing orchestrator is disabled.
- The DSPM connection status moves to the Waiting for Connection state and Configuration status moves to the Pending state.
- The data scans are stopped.
- The target subscriptions move to the Needs Attention state.
Prerequisites
Make sure the following prerequisites are met:
- Be assigned either an [administrator](/dspm/predefined-roles-and-permissions) role or any role with the Configure New Orchestrator permission in the DSPM Admin Portal.
-
Before redeploying the orchestrator template, you must add your system's IP address to the [Azure storage account](https://go.microsoft.com/fwlink/?LinkId=845586) and [Azure Key Vault](https://learn.microsoft.com/en-in/azure/key-vault/general/how-to-azure-key-vault-network-security)'s IP networks.
This is required when multiple users need to apply Terraform from different IP addresses.
Changing Orchestrator Subscription
To change the orchestrator subscription:
- Go to **Administration **> **Configuration** > **Cloud Accounts**.
- Select the tenant for which you want to change the orchestrator subscription.
-
Click **Manage** and then select **Configure New Orchestrator**.
[See image.](#configure-new-orch)
-
In the **New Orchestrator** window, read the caution and then select the **I understand** checkbox.
[See image.](#new-orch-window)
- Click **Continue**.
-
In the **Configure an Orchestrator subscription** page:
- Select a subscription on which you want to deploy the DSPM's orchestrator template.
- **Select Orchestrator Region**: Select a region where you want to deploy the orchestrator.
-
**Storage Account Name**: Enter a unique name for the storage account. This storage account is used to store the activity logs of the target subscriptions. It is created while running the onboarding template.
The storage account name cannot exceed 16 characters.
- Select the **Deploy private endpoint for secure communication** checkbox to establish a private connection between DSPM and Azure resources. This restricts communication over public IP addresses.
[See image.](#configure-orch-account-region)
- Click **Next**.
-
On the **Provide Permissions** page, download the template to run it in the Microsoft Entra tenant.
- Before running the template on the new orchestrator subscription, purge the previously deployed template by running the `terraform destroy` command.
- If the resource group is manually deleted:
- Import the following resources:
- `terraform import "module.control_plane[\"region\"].module.encryption_key.azurerm_key_vault_key.cmk_key""resourceID"`
- `terraform import "module.worker_plane[\"region\"].module.encryption_key.azurerm_key_vault_key.cmk_key""resourceID"`
- Purge the secret key vault:
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Key vaults**.
- Click **Manage deleted vaults**.
- On the **Manage deleted key vaults** page:
- **Subscription**: Select the existing orchestrator subscription.
- Select the secrets key vault check box and click **Purge**.
- [a. Download the orchestrator template.](#grantpermidspm)
- [b. Update and run the Terraform files.](#onboardinglocalsystem)
- Click **Done**.
DSPM validates the template deployment every hour by checking the roles that are created and permissions granted.
An error message appears if there is any issue while deploying the template. Rerun the template in the root account.
After the template is successfully deployed, the onboarded subscriptions move to the Successfully Configured state and DSPM begins the [data scan](/dspm/about-scan-settings). The DSPM Connection and Configuration Status for the orchestrator are displayed as successful. [See image.](#orchestrator-status)
You can view the orchestrator details on the [Overview](/dspm/viewing-tenant-onboarding-status) tab.
[]Click **Azure Onboarding **to download the template as a .zip file. Extract the file to your local system and create a new folder to store the extracted files. The .zip file includes multiple Terraform files that contain policies and permissions required for DSPM to connect to the Microsoft Entra tenant.
[See image.](#provide-permissionspage)
- []Update the following downloaded files:
-
**backend.tf**: Enter the name of the storage containers where you want to store the Terraform state files.
[See image.](#update-backendfile)
-
**terraform.tfvars**: Change the random_seed value.
Remember this seed value and use the same value when you deploy [new templates](/dspm/downloading-role-and-templates-microsoft-azure).
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform files.
- Run the following commands:
-
To connect to your Microsoft Entra tenant:
`az login --tenant <tenant ID>`
[See image.](#azure-login)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#select-azure-account)
The command output returns the subscriptions available within your Microsoft Entra tenant.
-
To set the subscription where you want to run the Terraform template:
`az account set --subscription <subscription ID>`
-
(Optional) To verify if the subscription is accurately set:
`az account show`
-
To initialize the working directory and apply Terraform configuration:
`terraform init`
[See image.](#terraform_init)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#terraform-apply)
[]![Select Configure new orchestrator](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/changing-orchestrator-subscription/dspm-configure-orchestrator.png)
[]![New orchestrator window](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/changing-orchestrator-subscription/dspm-new-orchestrator-window.png)
[]![Configure an orchestrator account](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/changing-orchestrator-subscription/dspm-change-orch-page.png)
[]![Configure the working directory](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-orchestrator-microsoft-azure/dspm-azure-terraform-init.png)
[]![Connect to the Azure tenant](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-orchestrator-microsoft-azure/dspm-azure-connect-to-azure.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-orchestrator-microsoft-azure/dspm-azure-backend-tf-file.png)
[]![Apply the configuration](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-orchestrator-microsoft-azure/dspm-azure-apply-tf.png)
[]![Select your Azure account](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-orchestrator-microsoft-azure/azureauthorizationpage.png)
[]![Viewing the orchestrator status](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/changing-orchestrator-subscription/dspm-orchestrator-subscription-status.png)
[]![Download and run the onboarding template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/changing-orchestrator-subscription/dspm-provide-permissions-page.png)