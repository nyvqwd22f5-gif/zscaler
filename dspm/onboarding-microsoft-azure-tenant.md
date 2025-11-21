# Onboarding a Microsoft Entra Tenant
Source: https://help.zscaler.com/dspm/onboarding-microsoft-azure-tenant
PDF: https://help.zscaler.com/pdf/com/en/1479301.pdf

You can onboard a Microsoft Entra tenant or management group and their associated subscriptions. DSPM monitors and [scans](/dspm/about-scan-settings) the data stores (e.g., databases, virtual machines, storage accounts) in the onboarded subscriptions to identify sensitive data, misconfigurations, and vulnerabilities.
Onboarding Workflow
The onboarding process is illustrated in the following image:
[See image.](#onboarding-illustration)
Prerequisites
Make sure the following prerequisites are met:
- [In the Microsoft Entra Tenant](#entratenant-prereq)
- [On Your Local System](#local-system-prereq)
- [In the DSPM Admin Portal](#dspm-prereq)
Onboarding a Microsoft Entra Tenant
To onboard a Microsoft Entra tenant:
- [Provide Microsoft Entra tenant details.](/dspm/adding-tenant-details)
- [Deploy the tree discovery template.](/dspm/deploying-azure-tree-discovery-template)
- [Select the network configuration, orchestrator subscription and monitoring scope.](/dspm/selecting-orchestrator-and-monitoring-scope)
- [Deploy the onboarding template.](/dspm/deploying-azure-onboarding-template)
- []Orchestrator subscription: Identify an [orchestrator](/dspm/understanding-orchestrator) subscription on which the DSPM's orchestrator template is deployed to scan the data stores.
- [Roles and permissions](#prereq-roles-permissions)
- Virtual machine instance type: Ensure that you have the Standard_D2s_v3 virtual machine instance type in the region where the orchestrator template must be deployed. This is required to run the orchestrator instance.
-
[]Access management: Enable Access management for Azure resources. This is required to manage access to all subscriptions and management groups in the tenant. Management group is a container for Azure subscriptions. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/governance/management-groups/overview).
[See instructions.](#access-mgt)
-
[]Microsoft Storage Resource Provider: Register the Microsoft Azure Storage Resource Provider (Microsoft.Storage) in the subscription within which the orchestrator template is deployed. This is required for DSPM to validate the [storage account](#orch-storage-account) created while onboarding. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/common/authorization-resource-provider).
[See instructions.](#register-storage-account)
-
[]Storage containers: Identify the storage containers where Terraform state files must be stored. The state files are required to manage resources created by the DSPM Terraform templates and to [upgrade to new templates](/dspm/downloading-role-and-templates-microsoft-azure). You can also create the following new storage containers to store the state files:
- [Resource Group](#resourcegroup)
- [Storage Account](#storageaccount)
- [Storage Account Container](#container)
Ensure to store the state files safely to upgrade to new templates. If the state files are lost or accidentally deleted, purge the resources, download and rerun the onboarding templates.
[See instructions.](#Terraform-state-files-recovery)
[]Resource groups are logical containers that comprises a group of Azure resources. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).
[]To create a resource group:
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Resource groups**.
-
Click **+Create**.
[See image.](#resourcegrp-create)
- On the **Basics** tab:
- **Subscription**: Select the orchestrator subscription from the drop-down menu.
- **Resource group**: Enter a unique name for the resource group.
- **Region**: Select a region where the resource group must be created.
-
Click **Review + create**.
[See image.](#reviewcreateresourcegrp)
[]Storage accounts store data objects such as files, queues, tables, and Terraform state files. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview).
[]To create a storage account:
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Storage account**.
-
Click **+Create**.
[See image.](#createstorage)
- On the **Basics** tab:
- **Subscription**: Select your Azure subscription.
- **Resource group**: Select the [resource group that you created](#createresourcegroup).
- **Storage account name**: Enter a unique name for the storage account.
- **Region**: Select location where the storage account must be created.
-
Click **Review + create**.
[See image.](#reviewcreatestorageaccount)
[]A storage account container is a set of blobs similar to a directory in a file system. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction).
To create a storage account container:
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Storage account**.
- Locate the [storage account you created](#createstorageaccount) and click the storage account.
-
In the left-side navigation, under **Data storage**, select **Containers**.
[See image.](#storageaccountcotainer)
-
Click **+Container**.
[See image.](#createcontainer)
- In the **New container** drawer:
- **Name**: Enter a unique name for the container.
- **Anonymous access level**: Select the access level for the container.
-
Click **Create**.
[See image.](#createbutton)
- []Sign in to the [Azure portal](https://portal.azure.com/) and go to **Subscriptions**.
- Click the **Subscription name** on which you want to deploy the orchestrator template.
-
In the left-side navigation, go to **Settings** > **Resource providers**.
[See image.](#sub-resourceproviders)
-
Search for **Microsoft.Storage**, click the ellipsis and select **Register**.
[See image.](#register-storage)
- []Sign in to the [Azure portal](https://portal.azure.com/) and go to **Microsoft Entra ID**.
-
In the left-side navigation, go to **Manage > Properties.**
[See image.](#manage-properties)
-
Under **Access management for Azure resources**, click the toggle to **Yes**.
[See image.](#enable-access-management)
[]![Resource groups page showing a list of resource groups and an annotation around the Create option.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-create-resource-groups.png)
[]![Create a resource group page showing the Basics tab with annotation around Review + create button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azureresourcegroup-creat.png)
[]![Storage accounts page showing a list of storage accounts and an annotation around the Create option.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-create-storage-account.png)
[]![Create a storage account page showing the Basics tab with annotation around Review + create button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspmreviewandcreatestorage.png)
[]![ A storage account page with the left-side navigation that shows an annotation around the Containers page.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-storage-account-containers.png)
[]![A storage account page with the annotation around the Container option.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-create-container.png)
[]![New container drawer with fields filled out and annotation around the Create button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-container-create.png)
[]![Azure portal’s left-side navigation with annotations around the Settings category and the Resource providers page.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-resource-provider.png)
[]![Search results for Microsoft.Storage with annotations around the ellipses and the Register option.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-register-storageaccount1.png)
[]![Azure portal’s left-side navigation with annotations around the Manage category and the Properties page](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-manage-properties.png)
[]![Annotation around Access management for Azure resources section with toggle set to Yes.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-access-management.png)
- []Install the [latest versions](#latestversions) of Terraform and Azure CLIs to run the templates. To learn more, refer to the [Microsoft Technical Documentation](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).
- Zscaler recommends you to enable the debug logs feature to identify issues encountered while onboarding. To enable debug logs, run the following commands:
-
PowerShell
`$env:TF_LOG="TRACE"
$env:TF_LOG_PATH="<filepath>filename.log"`
-
Bash
`export TF_LOG="TRACE"
$ export TF_LOG_PATH="<filepath>filename.log"`
[]You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Add Accounts permissions in the DSPM Admin Portal.
- []Delete the following [resource groups](#resourcegroups-deletion) from the Azure portal:
- z-dspm-{integration-id}-auth-plane-rg
- z-dspm-{integration-id}-worker-plane-rg
- z-dspm-{integration-id}-control-plane-rg
- Purge key vaults:
- Go to **Key vaults** and select **Manage deleted vaults**.
- Select the subscription where the resource groups were created.
-
Select Key vaults with the following format:
`z-dspm-{integration-id}-secrets`
- Click **Purge**.
-
Delete the following roles from the orchestrator subscriptions:
- <role_name>-access-role
- <role_name>-analyzer-role
- <role_name>-orchestrator-role
You can find the role name from the **Roles and Templates** tab.
- Delete <role_name>-target-role from all the target subscriptions.
- Delete **Read organization tree **role from the management group.
- Delete **Key vault reader** assignment from DSPM Service principal in the management group.
-
Delete root level assignment in the management group by running the following command:
`az role assignment delete --assignee "Service principal Application ID" --role "Management Group Reader" --scope "/'`
- Delete the service principal created:
- Go to **Microsoft Entra ID**.
- In the left-side navigation, go to **Manage** > **App registrations**.
- Select **All applications**.
- Search for and delete the service principal.
- From the **Roles and Templates** tab, download the Tree Discovery template, add new backend details, and [run the template](#downloadanddeploy).
- From the **Roles and Templates** tab, download the Azure Onboarding template, add new backend details, and run the template.
[]You must have the following roles and permissions:
[](#keyvaultprereq)
| Onboarding Type | Role | Access Level |
| --------------- | ---- | ------------ |
| Tenant or Management group | Global Administrator | Root |
| Key Vault Administrator | Orchestrator subscription |
| Tenant | User Access Administrator | Root |
| Management group | Contributor | Orchestrator subscription |
| User Access Administrator | Management group |
[]The Key Vault Administrator role is required to perform operations on a key vault that stores secrets such as passwords, certificates, etc. and all objects in it. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-guide?tabs=azure-cli).
To assign the Key Vault Administrator role:
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Management groups**.
-
Select **Tenant Root Group**. This is the root management group that includes management groups and subscriptions of the Microsoft Entra tenant.
[See image.](#rootmgtgroup)
-
In the left-side navigation, select **Access control (IAM)**.
[See image.](#accesscontrol)
-
Click **Add** and then select **Add role assignment** from the drop-down menu.
[See image.](#addrole)
-
In the **Add role assignment** page:
-
On the **Role** tab, select **Key Vault Administrator **from the table and click **Next**.
[See image.](#addroleassignment)
-
On the **Members** tab, click **+Select members**.
- Locate the member you want to assign the role to and select the member name.
- Click **Select**.
[See image.](#rolemembers)
- Click **Next**.
- On the **Conditions** tab, add any condition as required and click **Next**.
- Click **Review+assign**.
A message appears indicating that the role was assigned to the selected member successfully.
[]
| Environment | Terraform Version | Azure CLI Version | PowerShell or Bash Version |
| ----------- | ----------------- | ----------------- | -------------------------- |
| Mac | v1.10.3 | 2.65.0 | version 3.2.57(1)-release (arm64-apple-darwin23) |
| Cloud Shell - Bash | v1.9.5 | 2.65.0 | version 5.1.8(1)-release (x86_64-pc-linux-gnu) |
| Cloud Shell - PowerShell | v1.9.5 | 2.65.0 | 7.4.5 |
| Windows - Command line | v1.7.5 | 2.67.0 | NA |
| Windows - PowerShell | v1.9.8 | 2.67.0 | 7.4.6 |
[]![Role assignment page with annotation around Add role assignment](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-add-role-assignment.png)
[]![Add role assignment page with the list of roles](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dpsm-asure-keyvault-administrator.png)
[]![Select the members you want to assign the role ](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-select-members.png)
[]![The tenant onboarding workflow with the steps to be followed across DSPM Admin Portal, Azure portal, and local system.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/Workflow_DSPM_Onboarding-Azure_v6%20(1).png)