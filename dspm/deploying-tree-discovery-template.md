# Deploying the Tree Discovery Template
Source: https://help.zscaler.com/dspm/deploying-tree-discovery-template
PDF: https://help.zscaler.com/pdf/com/en/1517346.pdf

After adding the [tenant details](/dspm/adding-tenant-details), deploy the tree discovery template.
This template:
- Includes policies and permissions to create the service principal, [resource discovery role](/dspm/iam-roles-and-permissions-microsoft-azure) with required permissions, and managed identities.
- Assigns the service principal with permission to access resources in the Microsoft Entra tenant.
- Generates the application ID and client secret that are required for the service principal to connect to the Microsoft Entra tenant.
To deploy the tree discovery template:
- [1. Download and modify the template.](#step2tddownload)
- [2. Initialize the template.](#localsystemstep2)
- [3. Deploy the template.](#runtheterraform-commands)
- [][4. Grant API permissions in the Azure portal.](#step2azureportal)
- [5. Validate the template in the DSPM Admin Portal.](#dspmconnecttenant)
-
[]In the **Connect to the Tenant** section, click **Tree Discovery** to download the template as a ZIP file. Extract the file to your local system and create a new folder to store the extracted files. The ZIP file contains two Terraform files (`backend.tf` and `azure_tf_basic.tf`).
[See image.](#downloadtreediscovery)
-
Update the following details in the `backend.tf` file:
- **resource_group_name**: Enter the [resource group name](#prereqresources).
- **storage_account_name**: Enter the [storage account name](#prereqresources).
- **container_name**: Enter the [container name](#prereqresources) where the Terraform state files must be stored.
[See image.](#azurebackendfile)
[]
Use any of the following methods:
- [Cloud Shell](#runcloudshell)
- [Command Prompt](#run-tree-discovery-template)
- []Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
-
Connect to the Microsoft Entra tenant by running the following command:
`az login --tenant <[tenant ID](#tenantID)>`
[See image.](#azurelogintenant)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#authorizationpage)
The command output returns the subscriptions available.
[]After the template is deployed, a service principal or application is created in the Microsoft Entra tenant. You need to grant API permissions to the service principal to access resources within the tenant.
- Sign in to the [Azure portal](https://portal.azure.com/) and go to **Microsoft Entra ID**.
-
In the left-side navigation, go to **Manage** > **App registrations**.
[See image.](#appresgistrations)
-
Select the **Owned applications** tab.
[See image.](#ownedapp)
- In the table, search for and select the [service principal](#serviceprincipal).
-
In the left-side navigation, select **API permissions**.
[See image.](#apipermissions)
-
Click **Grant admin consent for <tenant name>.**
[See image.](#grantmgtaccount)
-
In the **Grand admin consent confirmation** window, click **Yes.**
[See image.](#approvemgtaccount)
[]
- In the DSPM Admin Portal, under **Connect to the Tenant**:
- **Application ID**: Enter the [client ID](#appclientsecret).
- **Client Secret**: Enter the [client secret](#appclientsecret).
-
Click **Validate**.
[See image.](#validateclientidandsecret)
DSPM validates the template deployment by verifying the application ID, client secret, and the custom roles created. If the validation is successful, you are directed to the [Orchestrator & Monitoring** **Scope](/dspm/selecting-orchestrator-and-monitoring-scope) section.
If there is any issue while deploying the template, an error is displayed. Rerun the template. To learn more, see [Resolving Configuration Issues for Microsoft Azure](/dspm/resolving-configuration-issues-microsoft-azure).
- []Sign in to the Azure portal, and click **Cloud Shell**.
-
In the **Welcome to Azure Cloud Shell** window, select **Bash **or **PowerShell**, as required.
[See image.](#selectpowershell)
-
In the **Getting started** window:
- Select **Mount storage account**.
- Select the storage account subscription from the list.
- Click **Apply**.
[See image.](#gettingstarted-selectsubscription)
-
In the **Mount storage account** window, select **Select existing storage account **and click **Next**.
[See image.](#mountstorage-account)
-
In the **Select storage account** window:
- **Subscription**: Select the subscription where the storage account is created.
- **Resource group**: Select the resource group from the list.
- **Storage account name**: Select the storage account.
- **File share**: Click **Create a file share **and enter a name for the new file.
- Click **Select**.
[See image.](#select-storage-account)
- Use any of the following:
- [Azure PowerShell](#powershell)
- [Bash](#deploy-template-bash)
-
[]Run the following commands to prepare the PowerShell environment:
-
To switch to the clouddrive folder:
`cd clouddrive`
-
To create a DSPM folder within the clouddrive folder and switch to the newly created DSPM folder:
`md dspm_onboarding
cd dspm_onboarding`
-
To create the logs and tree discovery folders:
`md logs
md tree discovery`
-
To verify if all the folders are created:
`ls`
-
To switch to the newly created tree discovery folder:
`cd tree discovery`
[See image.](#makedirectories)
-
Zip the modified template and upload the folder:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
[See image.](#upload-template-file)
- Run the following commands:
-
To extract the ZIP folder:
`expand -archive -path <folder name.zip>`
-
To switch to the folder within the ZIP folder:
`cd ./<folder name>/dspm-azure/`
- []Run the following commands to prepare the Bash environment:
-
To switch to the clouddrive folder:
`cd clouddrive`
-
To create a DSPM folder within the clouddrive folder and switch to the newly created DSPM folder:
`mkdir dspm_onboarding
cd dspm_onboarding`
-
To create the logs and tree discovery folders:
`mkdir logs
mkdir tree discovery`
-
To verify if all the folders are created:
`ls`
[See image.](#prepare-powershell-envi)
-
To switch to the newly created folder:
`cd tree discovery`
- Zip the modified template and upload the folder:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
- Run the following commands:
-
To extract the ZIP folder:
`unzip <folder name.zip>`
-
To switch to the folder within the ZIP folder:
`cd ./<folder name>/dspm-azure/`
[]Run the following commands:
-
To set the subscription where the storage containers containing the Terraform state files are stored:
`az account set --subscription <subscription ID>`
-
(Optional) To verify if the subscription is accurately set:
`az account show`
-
To initialize the working directory and apply Terraform configuration:
`terraform init`
[See image.](#inittf)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes` and press `Enter`.
[]The command output returns the client ID and client secret that DSPM requires to connect to the Microsoft Entra tenant.
[See image.](#appIDclientsecret)
[]![The backend.tf file opened in visual studio code with annotation around resource group name, storage account name, and container name.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-backend-tf-file.png)
[]![Command to login to the tenant with annotation around it.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-connect-to-azure.png)
[]![Microsoft Azure authorization page listing the accounts.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azureauthorizationpage.png)
[]![Azure portal left-side navigation with annotation around app registrations.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-entra-id-app.png)
[]![App registration page displaying All applications, Owned applications, Deleted applications tab and annotation around Owned applications.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-owned-applications.png)
[]![Application left-side navigation with annotation around API permissions.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dsom-azure-app-permissions.png)
[]![The API permissions page with annotation around Grant admin consent for the selected application.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-grant-permissions.png)
[]![Grant admin consent confirmation window with annotation around Yes.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dsom-grant-admin-consent.png)
[]![Connect to the Tenant section with annotation around Tree Discovery button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/deploy-azure-tree-discovery-template/dspm-download-tree-discvery-template.png)
[]![The Connect to the Tenant section displaying the Tree Discovery template, Application ID, Client Secret, and annotation around Validate button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/deploy-azure-tree-discovery-template/dspm-validate-tree-discovery-template.png)
[]![Welcome to Azure Cloud Shell window with Bash and Powershell options.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azure-select-powershell.png)
[]![The command prompt section with the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-terraform-init_0.png)
[]![The Getting started window in the Azure portal to select a subscription and storage account.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/awzure-powershell-getting-started.png)
[]![Select storage account window to select the subscription, resource group, storage account name, and create a file share.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/select-storage-account.png)
[]![The Mount storage account window with Select existing storage account option selected.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/select-existing-storage-account.png)
[]![The powershell prompt with commands to created directories for logs, tree_discovery, and azure_onboarding.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azure-logs-tree-discovery-files.png)
[]![The PowerShell prompt displaying the list of directories created and success message for uploading a file.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azure-upload-tree-discovery.png)
[]![The PowerShell prompt with the list of directories created.](/downloads/tech-pubs-drafts/dspm-draft-articles/onboarding-microsoft-entra-tenant-draft/azure-logs-tree-discovery-files.png)
[]![The output of tree discovery template deployment with client ID and client secret.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-clientid-secret-key.png)