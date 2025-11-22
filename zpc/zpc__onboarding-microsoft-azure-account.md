# Onboarding a Microsoft Azure Account
Source: https://help.zscaler.com/zpc/onboarding-microsoft-azure-account
PDF: https://help.zscaler.com/pdf/com/en/1394161.pdf

Zscaler Posture Control (ZPC) supports onboarding a Microsoft Azure cloud account. When onboarded, ZPC provides insight into your account's security posture. ZPC provides two automation bash scripts, the initial script and the onboarding script, that you can run on your Microsoft Azure Cloud Shell to onboard your cloud accounts.
- [Initial script](#initial-script)
- [Onboarding script](#onboarding-script)
To onboard a Microsoft Azure account to ZPC:
- [1. Ensure all prerequisites are met.](#azure-prerequisite)
- [2. Onboard a Microsoft Azure account.](#azure-onboard)
After you onboard a cloud account, verify that the status is displayed as "Success" on the Cloud Accounts page, indicating that the onboarding is successful and configuration metadata is collected. If there are any issues or if no resources are found in the Azure account while onboarding, the status is displayed as "Role/Resource not Found." To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts).
In addition to onboarding your Microsoft Azure accounts to ZPC, you can configure ZPC to collect additional configuration metadata:
- Set up vulnerability scanning for your Microsoft Azure cloud workloads and container registries. To learn more, see [Configuring Vulnerability Scanning for Cloud Accounts](/zpc/configuring-vulnerability-scanning-cloud-accounts).
- Connect your Azure Kubernetes Service (AKS) clusters with ZPC to gain visibility into your cluster security posture. To learn more, see [Onboarding an Azure Kubernetes Service Cluster](/zpc/onboarding-azure-kubernetes-service-cluster).
Updating Microsoft Azure Credentials
The onboarding script creates a service principal that ZPC uses to collect Microsoft Azure configuration metadata. The service principal credentials expire in one year. When these credentials expire, you need to create new credentials and provide them on the ZPC Admin Portal. ZPC can continue metadata collection and offer security posture for your Azure cloud accounts only after you update the credentials.
To update Microsoft Azure Credentials on ZPC:
- [1. Create new service principal credentials on Microsoft Azure.](#create-new-credentials)
- [2. Update the ZPC Admin Portal with the new credentials.](#update-zpc-ui-new-credentials)
[]
- Access the [Microsoft Azure Portal](https://portal.azure.com/) and select the subscription where the service principal was created.
- Launch the **Cloud Shell** on the Azure portal.
- Run the following command to reset the credentials for the service principal:
az ad sp credential reset --id "<Service Principal ID>" --query=[appId,password] --years=2 --out json
To find the service principal ID on Azure, run the following command:
az ad sp list --display-name "ZscalerCollector-" --query "[0].appId" --out tsv
If you have onboarded your cloud account after January 2023, run the following command to find the service principal ID:
az ad sp list --display-name "ZPC_" --query "[0].appId" --out tsv
[]
- On the ZPC Admin Portal, go to **Administration** > **Organizations**.
- Click the **Actions** icon, then click **Update Azure Credentials**.
- Enter the newly created password for the service principal, then click **Save**.
[]
The initial script assigns predefined and custom roles to a dedicated service principal. ZPC uses the service principal to read your Microsoft Azure deployment's subscriptions, management groups, and organization structure. This information is displayed on the ZPC Admin Portal. The initial script does the following:
- Creates a custom role with the name `CSP_READ_ORG` in the subscription where the script is run.
- Assigns the `Microsoft.Management/managementGroups/descendants/read` permission to the newly created custom role.
- Creates a new service principal with the name `ZPC_${TENANT_HASH}` and assigns the following roles:
- `Management Group Reader`
- `Key Vault Reader`
- `CSP_READ_ORG`
- Assign the following predefined Microsoft Azure read-only roles to the Service Principal:
- [See roles.](#predefined-azure-roles)
[]
The onboarding script creates a new custom role and assigns necessary permissions to th role. This custom role is assigned to the previously created service principal in the selected subscriptions and management groups scope. The onboarding script does the following:
- Creates a new custom role with the name `ZPC-${TENANT_HASH}` in the same subscription that the initial script was run on.
- Assigns the following definitions to the custom role:
- Actions:
- `*/read`
- `Microsoft.Compute/disks/read`
- `Microsoft.Compute/virtualMachines/read`
- NotActions:
- `Microsoft.Storage/storageAccounts/blobServices/*/read`
- `Microsoft.Storage/storageAccounts/fileServices/*/read`
- `Microsoft.Storage/storageAccounts/queueServices/*/read`
If you have granted vulnerability scanning permissions, the following actions are added to the role definition:
- `Microsoft.Compute/snapshots/beginGetAccess/action`
- `Microsoft.Compute/snapshots/endGetAccess/action `
- `Microsoft.Compute/snapshots/read`
- `Microsoft.Compute/snapshots/write`
- `Microsoft.Compute/snapshots/delete`
- Assigns the custom role to the `ZPC_${TENANT_HASH}` service principal with the selected subscriptions and management group scope.
[]
You need to meet the following prerequisites before onboarding a Microsoft Azure account:
To view identity information on ZPC, make sure you have an Azure Active Directory premium (P1) license.
- You need to be a ZPC Administrator. To learn more, see [About Administrators](/zpc/about-administrators).
- You need to be Microsoft Azure Global Administrator.
The Microsoft Azure Global Administrator role is only required to onboard the cloud account. You can revoke this role after you are done onboarding.
- Make sure you have access to a Root Management Group (the default name is Tenant Root Group). To learn more, see the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/governance/management-groups/overview#root-management-group-for-each-directory).
- Make sure all Azure subscriptions are accessible:
- Go to **Azure Active Directory**.
- In the left-side navigation, select **Properties**.
- Under **Access management for Azure resources**, toggle to **Yes**.
[See image.](#grant-access-management-resources)
- Click the **Save** icon.
- Sign out and sign back in to Azure to refresh access.
[]
To onboard a Microsoft Azure account:
- Go to **Administration** > **Cloud Accounts**.
- Click **Add Account**.
- Under **Select Cloud Type**, click the **Azure** tile.
- On the **Configuration** page, you can:
- View the prerequisites for running the configuration script. The configuration bash script lists all the Azure accounts.
- Copy the configuration bash script.
- Access the [Microsoft Azure Portal](https://portal.azure.com/) and select the subscription where the roles can be created.
- Click the **Cloud Shell** icon and select **Bash**.
- Paste and run the script command you copied earlier.
- After the script is deployed, in the ZPC Admin Portal, click **Next**.
[See image.](#azure-config-tab)
- Select the Microsoft Azure accounts you want to onboard to ZPC.
[See image.](#azure-select-accounts)
- Select your business unit from the drop-down menu.
[See image.](#azure-select-business-units)
- On the **Deploy Template** page, you can:
- View the prerequisites for running the deploy template bash script. The deploy template script onboards all selected Azure accounts to ZPC.
- Copy the deploy template bash script.
- Access the [Microsoft Azure Portal](https://portal.azure.com/) and run the script command you copied eariler.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[See image.](#azure-deploy-script)
[]
![View the configuration page for onboarding an Azure account.](/downloads/zpc/administration/cloud-accounts/internal-onboarding-microsoft-azure-account/zpc-azure-configuration.png)
[]
![View the select accounts page for Azure onboarding.](/downloads/zpc/administration/cloud-accounts/internal-onboarding-microsoft-azure-account/zpc-azure-account-selection.png?1673969533)
[]
![View the select business units page for Azure onboarding.](/downloads/zpc/administration/cloud-accounts/internal-onboarding-microsoft-azure-account/zpc-azure-select-business-units.png)
[]
![View the deploy template page for Azure onboarding.](/downloads/zpc/administration/cloud-accounts/internal-onboarding-microsoft-azure-account/zpc-azure-deploy-script.png)
[]
![View the Azure resources access toggle](/downloads/zpc/administration/cloud-accounts/onboarding-microsoft-azure-account/zpc-access-management-resources.png?1654181773)
[]
Azure Active Directory Graph roles:
| **Predefined Role Name** | **Role ID** |
| ------------------------ | ----------- |
| Azure Active Directory Graph | 00000002-0000-0000-c000-000000000000 |
| Directory.Read.All | 5778995a-e1bf-45b8-affa-663a9f3f4d04 |
| Policy.Read.All | 6c2d1b1d-a490-4178-ba6b-7efceda9129b |
Microsoft Graph roles:
| **Predefined Role Name** | **Role ID** |
| ------------------------ | ----------- |
| Application.Read.All | 9a5d68dd-52b0-4cc2-bd40-abcf44ac3a30 |
| AuditLog.Read.All | b0afded3-3588-46d8-8b3d-9842eff778da |
| Directory.Read.All | 7ab1d382-f21e-4acd-a863-ba3e13f7da61 |
| Reports.Read.All | 230c1aed-a721-4c5d-9cb4-a90514e508ef |
| UserAuthenticationMethod.Read.All | 38d9df27-64da-44fd-b7c5-a6fbac20248f |