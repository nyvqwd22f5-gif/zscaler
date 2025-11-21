# Deploying the Azure Onboarding Template
Source: https://help.zscaler.com/dspm/deploying-azure-onboarding-template
PDF: https://help.zscaler.com/pdf/com/en/1517981.pdf

After configuring the [orchestrator and monitoring scope](/dspm/selecting-orchestrator-and-monitoring-scope), deploy the Azure onboarding template. The onboarding template includes policies and permissions to create [custom roles](/dspm/iam-roles-and-permissions-microsoft-azure) that provide DSPM with access to the resources in the tenant.
To download and deploy the template, do the following:
- [1. Download and modify the template.](#grantpermidspm)
- [][2. Initialize the template.](#step4-deployonboardingtemplate)
- [3. Deploy the template.](#step4run-terraform-commands)
- [4. Validate the template in the DSPM Admin Portal.](#validate-template-deployment-indspm)
After completing the onboarding process, you can configure the scan settings. To learn more, see [About Scan Settings](/dspm/about-scan-settings).
[]
[]DSPM validates the template deployment every hour by checking the roles created and permissions granted.
Click **Validate** to verify if the template is deployed. This process takes a couple of minutes to complete. [See image.](#clickvalidate)
An error message appears if there is any issue while deploying the template. [See image.](#validateerror) To learn more, see [Resolving Configuration Issues for Microsoft Azure](/dspm/resolving-configuration-issues-microsoft-azure).
If the template is successfully deployed, you are directed to the [Overview ](/dspm/viewing-tenant-onboarding-status)page to view the status of the onboarded tenant.
[]Use any of the following methods:
- [Cloud Shell](#step4-deploytemplate)
- [Command Prompt](#step4command-prompt)
-
[]In the **Grant Permissions** section, click **Azure Onboarding** to download the template as a ZIP file. Extract the file to your local system and create a new folder to store the extracted files. The ZIP file contains multiple Terraform files.
[See image.](#validateonboardingtemplate)
-
Update the following details in the `backend.tf` file:
- **resource_group_name**: Enter the [resource group name](#prereqresources).
- **storage_account_name**: Enter the [storage account name](#prereqresources).
- **container_name**: Enter the [container name](#prereqresources) where the Terraform state files are stored.
[See image.](#onboardinbackendfile)
- []Sign in to the Azure portal, and click **Cloud Shell**.
-
In the **Welcome to Azure Cloud Shell** window, select **Bash **or **PowerShell**, as required.
[See image.](#azurecloudshellwindow)
-
In the **Getting started** window:
- Select **Mount storage account**.
- Select the storage account subscription from the list.
- Click **Apply**.
[See image.](#gettingstartedwindow-azure)
- In the **Mount storage account** window, select **Select existing storage account **and click **Next**.
-
In the **Select storage account** window:
- **Subscription**: Select the subscription where the storage account is created.
- **Resource group**: Select the resource group from the list.
- **Storage account name**: Select the storage account.
- **File share**: Click **Create a file share **and enter a name for the new file.
- Click **Select**.
[See image.](#select-storage0account-azure)
- Use any of the following:
- [Azure PowerShell](#step4-powershell)
- [Bash](#step-4-deploy-template-bash)
- []Run the following commands to prepare the PowerShell environment:
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
- Zip the modified template and upload the folder:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
- Run the following commands :
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
-
To switch to the newly created folder:
`cd tree discovery`
- Zip the modified template and upload the folder:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
- Run the following commands:
-
To extract the zip folder:
`unzip <folder name.zip>`
-
To switch to the folder within the zip folder:
`cd ./<folder name>/dspm-azure/`
[]Run the following commands:
-
To set the subscription where the storage containers containing the Terraform state files are stored:
`az account set --subscription <subscription ID>`
-
(Optional) To verify if the subscription is accurately set:
`az account show`
-
To update the Terraform configuration to use the latest Azure and Terraform versions:
`terraform init -upgrade`
-
To initialize the working directory and apply Terraform configuration:
`terraform init`
[See image.](#intializeterraform)
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To run the Terraform script:
`terraform apply`
Under **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#applytfconfig)
For **Enter IP**, enter the IP address of the system on which you are running the template.
[]After deploying the onboarding template, the following resources are created in the Microsoft Entra tenant:
[][List of resources](#template-resources)
- []Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
-
Connect to the Microsoft Entra tenant by running the following command:
`az login --tenant <[tenant ID](#tenantID)>`
[See image.](#azurelogin-tenant)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#azureauthenticatepage)
The command output returns the subscriptions available.
- []Custom role for orchestrator: Custom role for orchestrator instance.
- Custom role for target: Custom role for target accounts.
- Custom role for scanner: Custom role for scanner instance.
- Resource group: Logical grouping to manage resources.
- Key vault: Vault to store secrets.
- Managed identities for orchestrator and scanner: Managed identities for orchestrator and scanner instance.
- Virtual machine scale sets: Scale sets for orchestrator instance.
- Network security groups: Used to manage network traffic to virtual machine instances.
- Virtual networks: Virtual network to run virtual machines.
- Storage Accounts
- Blob containers for storing diagnostic logs
- Queue to receive scan requests from DSPM. The storage account is created to receive communication from DSPM IPs.
- Subnets: Used to deploy Azure resources.
- VNET peering: Virtual network peering used to ensure that the communication between orchestrator and scanners are private.
- NAT gateway: Network address translation gateway used to provide outbound internet connectivity to orchestrator or scanner instances.
[]![Welcome to Azure Cloud Shell window with Bash and Powershell options.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azure-select-powershell_0.png)
[]![The Getting started window in the Azure portal to select a subscription and storage account.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/awzure-powershell-getting-started_0.png)
[]![Select storage account window to select the subscription, resource group, storage account name, and create a file share.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/select-storage-account_0.png)
[]![The command prompt with az login command annotated.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-connect-to-azure.png)
[]![The Azure Authorization page with list of accounts to select from.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azureauthorizationpage.png)
[]![Onboarding steps with expansion of Grant Permissions section.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-grant-permissions-azure.png)
[]![The backend.tf file opened in visual studio code with annotation around resource group name, storage account name, and container name.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-backend-tf-file.png)
[]![The command prompt section with the output of terraform init command.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-terraform-init_0.png)
[]![The output of Terraform apply command to confirm the actions.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-apply-tf.png)
[]![The Grant Permissions section with annotations around the error.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-orchvalidate-error.png)
[]![Grant Permissions section with annotation around Validate button.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-grnt-permi-validate.png)