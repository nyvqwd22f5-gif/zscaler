# Managing Monitoring Scope for Microsoft Azure
Source: https://help.zscaler.com/dspm/managing-monitoring-scope-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1479316.pdf

The monitoring scope refers to the Azure target subscriptions that are onboarded. When new subscriptions are added to your Microsoft Entra tenant, you can onboard and add these new subscriptions to the monitoring scope.
You can also enable autodetection, which allows DSPM to automatically detect and onboard any new subscriptions that are added in the future. This eliminates the need to manually onboard new subscriptions to DSPM.
Prerequisites
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or a custom role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
Managing Monitoring Scope
To add new subscriptions to the monitoring scope:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the tenant for which you want to add new target subscriptions.
-
Click **Manage**, and then select **Monitoring and Autodetect** from the drop-down menu.
[See image.](#monitoring-autodetect)
-
On the **Add Subscriptions to Monitoring Scope** page, select the subscriptions that you want to be monitored.
Enable **Autodetection,** so DSPM can automatically detect and onboard any new subscriptions that are added in the future. Click **Next**.
Once a subscription has been added to the monitoring scope, you cannot remove it from the monitoring scope. If you want to stop monitoring a subscription, you need to delete the subscription from the DSPM tenant. To learn more, see[ Deleting an Onboarded Tenant](/dspm/deleting-onboarded-tenant).
[See image.](#selectsubscriptions)
-
On the **Assign Business Units** page, change the [business unit](/dspm/about-business-units) for the management group if required, then click **Next**.
[See image.](#assignbu)
- On the **Apply Changes** page:
- [Monitoring Scope](#monitoringscope)
- [Autodetection](#autodetection)
- Click **Done**.
The new subscriptions are added to the monitoring scope. You can view the tenant's onboarded subscriptions on the [Subscriptions tab](/dspm/viewing-onboarded-accounts-and-subscriptions).
[]The onboarding template contains the policies and permissions required to create custom roles in the Microsoft Entra tenant providing DSPM with read-only access to collect data for various services.
To download and run the template, do the following:
- [i. In the DSPM Admin Portal](#dspmadmin)
- [ii. On the Local System](#localsystem)
[]Click **Azure Onboarding** to download the template as a .zip file. Extract the file to your local system and create a new folder to store the extracted files. The .zip file contains multiple Terraform files that contain policies and permissions required for the DSPM to connect to the Microsoft Entra tenant.
[See image.](#downloadazure)
[]Run the template in the Microsoft Entra tenant using the CLI app:
-
Update the **backend.tf file **with the name of the storage containers that you used while [onboarding the tenant](/dspm/onboarding-microsoft-azure-tenant) to store the Terraform state files.
- **resource_group_name**: Enter the resource group name.
- **storage_account_name**: Enter the storage account name.
- **container_name**: Enter the container name.
[See image.](#backendfileupdate)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
- Run the following commands:
-
To connect to your Microsoft Entra tenant:
`az login --tenant <tenant ID>`
[See image.](#azuretenantconnect)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
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
[See image.](#terraforminit)
-
To verify the changes in the Terraform configuration:
`terraform plan`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
-
To run the Terraform script:
`terraform apply`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
Under **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#terraformapply)
For **Enter IP**, enter the IP address of the system on which you are running the template.
[]Review the list of management groups that you selected for autodetection.
[See image.](#applychangespage)
[]![Select monitoring scope](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-add-subscriptions-page.png)
[]![Assign business unit](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/assign-bus.png)
[]![Download the onboarding template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-azure-onboarding-template.png)
[]![Connect to the Azure tenant](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-azure-connect-to-azure.png)
[]![Initialize the terraform configuration](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-azure-terraform-init.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-azure-backend-tf-file.png)
[]![Apply the Terraform configuration](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-azure-apply-tf.png)
[]![Download the onboarding template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-apply-changes.png)
[]![Select Monitoring and Auto-detect](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-monitoring-scope-microsoft-azure/dspm-monitoring-autodetect.png)