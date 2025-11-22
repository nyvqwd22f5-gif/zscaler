# About Cloud Deception with Azure
Source: https://help.zscaler.com/deception/about-cloud-deception-with-azure
PDF: https://help.zscaler.com/pdf/com/en/1531505.pdf

You can integrate Microsoft Azure with Zscaler Deception to set up various Azure-specific decoy resources in your environment to lure adversaries. Depending on the type of decoy and its configuration, an adversary can access, interact, or perform malicious operations with the cloud decoys in different ways. Such activities are logged as attacks. You can view and analyze the attack details from the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
Cloud Deception with Azure provides the following benefits and enables you to:
- Configure decoys that mimic legitimate Azure identities and IaaS resources such as Azure AD (Entra ID) users, service principals, managed identities, storage accounts, key vaults, etc.
- Lure internal and external adversaries to Azure decoy resources and proactively take remedial action.
- Leverage landmine policies such as cloud lures, session lures, browser lures, and certain file decoys to lure internal adversaries.
You can deploy Azure decoys to detect malicious activities originating from adversaries within or outside your organization, depending on the type and configuration of the decoys. For example, lures for Azure decoys configured using landmine policies detect malicious activities from users within an organization as the landmine policies are deployed in devices managed by your organization. On the other hand, Azure decoys with public visibility can detect malicious activities from external adversaries who enumerate them with various tools.
Deception uses a deployment script to set up the integration and deploy decoys in the Azure cloud. The script also deploys all necessary resources such as secrets, resource groups, function apps, etc. to manage Cloud Deception with Azure. A health check function app is also deployed that monitors and updates the health status of the deployed decoys to the Zscaler Deception Admin Portal every 15 minutes.
About the Cloud Deception Azure Page
On the Cloud Deception - Azure page (Deceive > Cloud Deception > Azure), you can do the following:
- View the list of all Azure accounts added to the Deception Admin Portal. For each Azure account, you can view:
- **Enabled**: Indicates if Cloud Deception is currently enabled for the account. A green check mark indicates it is enabled for the account, and a red X indicates that it is disabled.
- **Client ID**: The client ID assigned by Azure for decoy resources.
- **Tenant ID**: The tenant ID associated with the Azure account.
- **Subscription ID**: The subscription ID associated with the Azure account.
- **Decoy Access Role**: The role in Azure created by the deployment script to define access control for decoys.
- **Management Resource Group**: The resource group created by the deployment script in Azure to hold all necessary resources other than decoys to support Cloud Deception functionalities.
- **Health Check Function**: The function app installed by the deployment script for monitoring and updating the health status of the deployed decoys.
- **Marked for Deletion**: Indicates if the account is marked for deletion. A green check mark indicates that the account is marked for deletion, and a red X indicates that it is not.
- [Configure the integration between Azure and Deception](/deception/setting-cloud-deception-microsoft-azure).
- [Obtain the deployment script to run it on the Azure Cloud Shell](/deception/obtaining-deployment-script-azure).
- Configure the Azure decoys listed as follows:
- [User decoys](/deception/creating-user-decoy-azure)
- [Service Principal decoys](/deception/creating-service-principal-decoy-azure)
- [Managed Identity decoys](/deception/creating-managed-identity-decoy-azure)
- [App Service decoys](/deception/creating-app-service-decoy-azure)
- [Storage Account Container decoys](/deception/creating-storage-account-container-decoy-azure)
- [Storage Account File Share decoys](/deception/creating-storage-account-file-share-decoy-azure)
- [Key Vault decoys](/deception/creating-key-vault-decoy-azure)
- [ARM Template decoys](/deception/creating-arm-template-decoy-azure)
- [Container Registry decoys](/deception/creating-container-registry-decoy-azure)
- [VM Image decoys](/deception/creating-vm-image-decoy-azure)
- [Generative AI decoys](/deception/creating-generative-ai-decoy-azure)
- [Manage resource groups](/deception/managing-resrource-groups-azure).
-
View the regions associated with an account. The list of regions includes regions of the decoys deployed within the account.
[See image.](#region-settings)
-
[Manage Deception settings for an Azure account](/deception/managing-cloud-deception-settings-azure-account).
You can also check the status, edit, or delete your Azure decoys from the respective tabs. To learn more, see [Managing Azure Decoys](/deception/managing-azure-decoys).
![A screenshot of the Cloud Deception Azure page in the Zscaler Deception Admin Portal](/downloads/deception/deceive/cloud-deception/azure/about-cloud-deception-with-azure/deception-about-cloud-deception-new.png)
[]![A list of Azure regions along with their logging storage account details](/downloads/deception/deceive/cloud-deception/azure/about-cloud-deception-with-azure/deception-regions-azure.png)