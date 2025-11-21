# Managing Application Details and Client Secret
Source: https://help.zscaler.com/dspm/managing-application-details-and-client-secret
PDF: https://help.zscaler.com/pdf/com/en/1479331.pdf

While [onboarding a Microsoft Entra tenant](/dspm/onboarding-microsoft-azure-tenant), a service principal or application is created within the Microsoft Entra tenant. The service principal defines the policies and permissions required for DSPM to access specific resources within the onboarded Microsoft Entra tenant. The service principal is identified by a unique identifier called the application or the client ID, along with a client secret used as a password.
You can update the application details and client secret of the service principal as required.
Updating Application Details
If the service principal is accidentally deleted, DSPM's access to the onboarded tenant is impacted, and all the onboarded subscriptions within the tenant move to the [Needs Attention](/dspm/viewing-tenant-onboarding-status) state. To restore access, you must update the application details.
Prerequisite
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Change Application Details permissions.
Updating Application Details
To update the application details:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the tenant for which you want to update the application details.
- Select the **Roles and Templates** tab.
-
Download and run the **Tree Discovery** template:
[See image.](#treediscovery)
- [a. In the DSPM Admin Portal](#step2tddownload)
- [b. On the Local System](#localsystemstep2)
- [c. In the Microsoft Entra Tenant](#step2azureportal)
-
Click **Manage** and then select **Change Application Details.**
[See image.](#changeappdet)
- In the **Change Application Details** window, enter the client ID and client secret [generated in the CLI app](#appclientsecret):
- **Application ID**: Enter the client ID.
- **Client Secret**: Enter the client secret.
-
Click **Validate**.
[See image.](#appdetailswindow)
DSPM validates the template deployment by verifying the application ID, client secret, and the custom roles created. If the validation is successful, a message appears indicating that the connection is established.
- Click **Done**.
-
On the **Roles and Templates** tab, download and run the **Azure Onboarding **template:
[See image.](#onboardingtemplate)
- [a. In the DSPM Admin Portal](#grantpermidspm)
- [b. On the Local System](#onboardinglocalsystem)
After the template is successfully deployed, DSPM's access to the Microsoft Entra tenant is restored, and the onboarded subscriptions move to the Successfully Configured state.
Updating the Client Secret
The client secret ID in Microsoft Azure is a confidential string that is used as a password for the service principal or application. It comes with an expiration date and must be renewed for the service principal to remain functional. You can update the client secret ID that you provided while [onboarding a tenant](/dspm/onboarding-microsoft-azure-tenant).
Prerequisite
- You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Change Application Details permissions in the DSPM Admin Portal.
- Ensure that you have added a [new client secret](#clientsecret) for the service principal in the Microsoft Entra tenant.
Updating the Client Secret
To update the client secret ID:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the tenant for which you want to update the client secret.
-
Click **Manage** and then select **Change Application Details.**
[See image.](#change-app-det)
-
In the **Change Application Details** window, for **Client Secret**, paste the [string copied](#secretstring) from the Microsoft Entra tenant.
[See image.](#validate-client-secret)
-
Click **Validate**.
DSPM validates the updated client secret by verifying it against the service principal and application ID. If the validation is successful, a message appears indicating that the connection is established.
If the client secret is invalid, or it does not match the service principal, an error is displayed.
[See image.](#invalid-client-secret)
-
Click **Done**.
The client secret is updated for the service principal.
[]To add a new client secret:
- Sign in to the [Microsoft Azure portal](https://portal.azure.com/) and go to **Microsoft Entra ID**.
-
In the left-side navigation, select **App registrations**.
[See image.](#appregistrations)
- Select the **Owned applications** tab.
- Search for and select the [service principal](/dspm/onboarding-microsoft-azure-tenant) you created while onboarding.
-
In the left-side navigation, select **Certificates & secrets**.
[See image.](#certificatessecrets)
-
On the **Client secrets** tab, click **New client secret**.
[See image.](#newclientsecret)
-
In the **Add a client secret** page:
- **Description**: Enter a description for the client secret.
- **Expires**: Select the expiry date from the drop-down menu.
[See image.](#addcspage)
- Click **Add**.
-
[]In the **Client secrets** table, under **Value**, click the copy icon to copy the string to the clipboard.
[See image.](#copysecretkey)
[]Click **Tree Discovery** to download the template as a .zip file. Extract the file to your local system and create a new folder to store the extracted files. The .zip file contains two Terraform files (backend.tf and azure_tf_basic.tf).
[See image.](#tdtemplatefile)
[]Run the template in the Microsoft Entra tenant using the CLI app:
-
Update the downloaded **backend.tf** file with the storage container names where you want to store the Terraform state files.
- **resource_group_name**: Enter the resource group name.
- **storage_account_name**: Enter the storage account name.
- **container_name**: Enter the container name.
[See image.](#editbackendtd)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
- Run the following commands:
-
To connect to your Microsoft Entra tenant:
`az login --tenant <tenant ID>`
[See image.](#azlogintd)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#azautohrization)
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
[See image.](#tdinit)
-
To verify the changes in the Terraform configuration:
`terraform plan`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
-
To run the script:
`terraform apply`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
Under **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#tdapply)
[]The command output returns the client ID and client secret that is required to connect DSPM with the Microsoft Entra tenant.
[See image.](#clientidsecret)
[]After the template is successfully deployed, a service principal or application is created in the Microsoft Entra tenant. You need to grant API permissions to the service principal to access resources within the Microsoft Entra tenant.
To grant API permissions:
- Sign in to the [Microsoft Azure portal](https://portal.azure.com/) and go to **Microsoft Entra ID**.
-
In the left-side navigation, select **App registrations**.
[See image.](#appregistration)
-
Select the **Owned applications** tab.
[See image.](#ownedapp)
- In the table, search for and select the service principal.
-
In the left-side navigation, select **API permissions**.
[See image.](#apipermissions)
-
Click **Grant admin consent for <tenant name>.**
[See image.](#grantapipermi)
-
In the **Grand admin consent confirmation** popup, click **Yes.**
[See image.](#grantconsent)
[]Click **Azure Onboarding** to download the template as a .zip file and extract it to your local system.
The .zip file contains multiple Terraform files that contain policies and permissions required for the DSPM to connect to the Microsoft Entra tenant.
[]Run the template in the Microsoft Entra tenant using the CLI app:
-
Update the downloaded **backend.tf** file with the storage container names where you want to store the Terraform state files.
- **resource_group_name**: Enter the resource group name.
- **storage_account_name**: Enter the storage account name.
- **container_name**: Enter the container name.
[See image.](#onbupdatebacken)
- Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
- Run the following commands:
-
To connect to your Microsoft Entra tenant:
`az login --tenant <tenant ID>`
[See image.](#azloginonb)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#azauthorizaonb)
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
[See image.](#initonb)
-
To verify the changes in the Terraform configuration:
`terraform plan`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
-
To run the script:
`terraform apply`
For **Enter a value**: Enter the regions where you want to deploy the template in the following format:
`["region name1", "region name2", "region name3"]`
Under **Do you want to perform these actions?**, enter `yes` and then press `Enter`.
[See image.](#applyonb)
[]![Download the Tree Discovery template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-roles-template-tree-discovery.png)
[]![Extract the downloaded .zip file](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-treediscovery-template-files.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-backend-tf-file.png)
[]![Run the command to connect to the Azure AD tenant](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-connect-to-azure.png)
[]![Select your Azure account](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/azureauthorizationpage.png)
[]![Initialize the working directory](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-terraform-init.png)
[]![Apply the configuration](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-apply-tf.png)
[]![Copy the generated Client ID and Client Secret](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-clientid-secret-key.png)
[]![Select App registrations](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-entra-id-app.png)
[]![Application in the Azure AD](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-owned-applications.png)
[]![Grant API permissions to the application](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dsom-azure-app-permissions.png)
[]![Grant admin consent for the service principal](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-grant-permissions.png)
[]![Grant consent confirmation](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dsom-grant-admin-consent.png)
[]![Update the backend file](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-backend-tf-file.png)
[]![Initialize the working directory](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-terraform-init.png)
[]![Connect to the Azure AD](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-connect-to-azure.png)
[]![Select your Azure account](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/azureauthorizationpage.png)
[]![Apply the Terraform configuration](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-apply-tf.png)
[]![Select Change Application Details](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-manage-change-app-details.png)
[]![Change Application Details window](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-azure-app-details-window_0.png)
[]![Download the onboarding template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-roles-template-azure-onboarding.png)
[]![Select App registrations](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/updating-client-secret/dspm-azure-app-registrations.png)
[]![Update certificates and secrets](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/updating-client-secret/dspm-certificates-secrets.png)
[]![Add new client secret](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/updating-client-secret/dspm-azure-create-secret.png)
[]![Add a client secret page](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/updating-client-secret/dspm-azure-add-a-clientsecret-pae.png)
[]![Copy the secret key](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/updating-client-secret/dspm-azure-copy-to-clipboard.png)
[]![Validate the new Client Secret](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-validate-client-secret.png)
[]![Invalid Client Secret](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-invalid-client-secret.png)
[]![Change Application Details](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/managing-application-details/dspm-manage-change-app-details.png)