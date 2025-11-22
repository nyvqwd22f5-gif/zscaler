# Authorizing a Custom Zscaler Connector for Microsoft Applications
Source: https://help.zscaler.com/unified/authorizing-custom-zscaler-connector-microsoft-applications
PDF: https://help.zscaler.com/pdf/com/en/1493001.pdf

The Zscaler service supports custom, client-side connector onboarding for access to the following Microsoft applications: Exchange, Microsoft Information Protection (MIP) Labels, OneDrive, SharePoint, Microsoft Azure Blob Storage, and Teams. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access your Microsoft applications.
When you create a custom connector for a Microsoft application, you must provide the Client ID, Client Secret, and Tenant ID in the Admin Portal so that the Zscaler service can access the application.
To create a custom connector for a Microsoft application:
- [][1. Create the custom connector and client secret.](#create-custom-connector)
- [2. Generate API permissions for the connector.](#generate-permissions-for-connector)
- [3. Add role assignments (for Microsoft Azure Blob Storage only).](#add-role-assignments)
- [4. Create Private Key JSON file (Microsoft SharePoint only).](#jsonsp)
- [5. Authorize the custom connector.](#authorize-custom-connector)
- [6. Register application for admin management (Microsoft Copilot only).](#copilot)
When creating custom connectors, provide the following application-specific API permissions to ensure that the Zscaler service has the access it needs.
- [API Permissions for Microsoft Applications](#api-permissions)
[]This section covers how to register your Internet & SaaS API client application in Microsoft Entra ID and configure the client credentials.
- [a. Register the application or service.](#register-client)
- [b. Configure and copy the client secret.](#configure-client-credentials)
[]
- Sign in to [Azure portal](https://azure.microsoft.com/).
- In the **Azure Services** section, click **App registrations**.
The **App registrations **page is displayed.
-
Click **New registration**.
[See image.](#client-app-new-registration-button)
The **Register an application** window opens.
-
In the **Register an application** window:
- **Name**: Enter a name for the application that is representative of the Zscaler connection you are creating (e.g., `Zscaler OneDrive Connector`).
- **Supported account types**: Ensure that this option is set to the **Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant)** value.
- **Redirect URI (optional)**: Select **Web** as the platform, then provide the URL of the Zscaler account (i.e., `https://console.zscaler.com`). Save the URL for later use.
[See image.](#client-app-registration-window)
-
Click **Register**.
The application is registered and the application's **Overview** page is displayed. Copy the **Application (client) ID** and **Directory (tenant) ID** values from the **Overview** page and save them for later use.
[See image.](#client-app-id)
[]
-
Go to **Certificates & secrets** in the left-side navigation of the app and then click **New client secret** on the **Client secrets** tab.
[See image.](#new-client-secret-button)
The **Add a client secret** pane opens.
-
In the **Add a client secret** pane:
- **Description**: Provide information about the client's secret.
- **Expires**: Select the appropriate expiration time from the drop-down menu.
[See image.](#client-secret-window)
-
Click **Add**.
The client secret value is generated and displayed.
-
Copy the secret value immediately and save it for later use.
The client secret value is displayed only once and cannot be retrieved after you navigate away from the page.
[See image.](#client-secret)
[]You must assign [specific API permissions](#api-permissions-section) for each Microsoft connector you create for the Zscaler service.
- Go to **API permissions** in the left-side navigation and then click **Add a permission** under **Configured permissions**.
The **Request API permissions** pane is displayed.
[See image.](#request-api-permissions-pane)
- On the **Microsoft APIs** tab, click an API to assign permissions (i.e., **Microsoft Graph**). To learn more, see the [complete list of API permissions](#api-permissions-section).
- Click **Application permissions**.
[See image.](#app-permissions-button)
- In the **Select permissions** list, select each [necessary permission](#api-permissions-section) for the connector.
- Click **Add permissions**.
[See image.](#add-permissions-button)
The permissions appear in the **Configured permissions** list on the **API permissions** page.
[See image.](#configured-permissions-page)
- If admin consent is required (such as SharePoint permissions), select **Grant admin consent**.
- In the** Grant admin consent** confirmation window, select **Yes**.
[]If you are setting up a custom connector for Microsoft Azure Blob Storage, you must add additional role assignments in Azure to ensure that the Zscaler service can properly access the application.
-
Go to **Azure Services** > **Enterprise Applications**.
[See image.](#enterprise-applications)
-
Copy the **Tenant ID** and the **Application name** matching the ID from when you created the custom connector and client secret.
[See image.](#application-name-ID-add-role)
-
Go back to the Azure portal home page, then go to **Subscriptions **and select your subscription.
[See image.](#azure-portal-subscriptions)
-
Go to **Access Control (IAM)** > **Role Assignments** > **Add **> **Add role assignment**.
[See image.](#add-role-assignment-azure)
- Search `Storage Contributor`. Select **Storage Blob Data Contributor** and **Storage Account Contributor** and then click **Next**. You must do this separately for each role.
-
Click **Select members** and add the application as a member to **Storage Blob Data Contributor** and **Storage Account Contributor**, then select **Review + assign**.
[See image.](#select-members-add-role)
[]If you are adding SharePoint as a SaaS Application tenant to Internet & SaaS, you need to create a private key JSON file and upload your public certificate to Azure.
- [][][a. Create a self-signed certificate.](#sp_selfsigned)
- [b. Upload the certificate file to the created client connector.](#jsonspo_upload)
- [c. Create a private key JSON file.](#jsonspo_create)
- []Go to your certificate uploaded on the Azure portal. For help viewing this, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/sharepoint/administration/view-certificates).
-
Enter and run the following command on the PFX file to obtain the public certificate where <certname> is the name of the certificate in the previous step. The command asks for your source keystore password which you set in a [previous step](#first_script2):
``openssl pkcs12 -in ``<certname>``.pfx``
-
Enter and run the following command to obtain your decrypted private key:
``openssl pkcs12 -in ``<certname>``.pfx -nocerts -nodes -out``
-
Create a new file with the following format and paste in the private key and certificate:
`{“private_key”: ”<Private Key>”,
“public_cert”: ”<Certificate>”
}`
Format the private key and certificate as one line between the parentheses. Enter \n for every line break from the original formatting. See the following example:
`{ "private_key":"-----BEGIN PRIVATE KEY-----\nXXXXXXXXXXXXXXXXXX\nXXXXXXXXXXXXXXXXXX\nXXXXXXXXXXXXXXXXXX\n-----END PRIVATE KEY-----\n",
"public_cert":"-----BEGIN CERTIFICATE-----\nXXXXXXXXXXXXXXXXXX\nXXXXXXXXXXXXXXXXXX\nXXXXXXXXXXXXXXXXXX\n-----END CERTIFICATE-----\n"
} `
- Save the file in the JSON format.
-
[]In the Azure portal, go to **App registrations** and click on the client connector you created. In the left-side navigation, go to **Manage** > **Certificates & secrets**.
[See image.](#jsonspo_reg)
-
Click the **Certificates** tab and then click **Upload certificate**.
[See image.](#jsonspo_uploadcert)
- In the **Description** field, enter a description for the certificate.
- Upload the public certificate CER file and click **Add**.
- []Open the terminal on your computer.
-
[][]Execute the following script:
`Keytool -genkey -alias selfsigned -keyalg RSA -keypass <keypassword> -storepass <keystorepass> -keystore Keystore.pfx -keysize 2048 -validity 1461`
-
Enter your custom information and press `Enter`.
[See image.](#sp_custom)
-
Execute the following script:
`Keytool -export -keystore keystore.pfx -alias selfsigned -file ketstore.cer`
-
Enter the source keystone password that you set in the [first script](#first_script).
You will have two files ready: `keystore.pfx` and `keystore.cer`.
[][]To complete the app registration for Copilot, run the following script in Azure via Power Platform API or PowerShell for Power Platform administrators. Use the **Zscaler Connector ID** you [copied earlier](#connect):
`$appId = "<Zscaler Connector ID>"
# Login interactively with a tenant administrator for Power Platform
Add-PowerAppsAccount -Endpoint prod -TenantID $tenantId
# Register a new application, this gives the SPN/client application the same permissions
New-PowerAppManagementApp -ApplicationId $appId`
[]![Examples of the custom information questions such as first and last name](/downloads/zia/adding-saas-application-tenants/sp_custom.png)
[]![Left-side navigation for Azure](/downloads/zia/adding-saas-application-tenants/SP%20Certificates%20Secrets.png)
[]![Certificates page with annotations around Upload certificate button](/downloads/zia/adding-saas-application-tenants/SP%20Upload%20Cert.png)
[]
![Azure Portal with annotations around Enterprise Applications](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/azure-portal-enterprise-applications.png)
[]![Application ID](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/application-name-ID-add-role.png)
[]![Subscriptions page with annotation around Subscription name](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/azure-portal-subscriptions.png)
[]![Add role to subscription with annotations around the navigation links and Add button](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/add-role-assignment-azure.png)
[]![Add role assignment](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/select-members-add-role.png)
[]![Request API permissions pane in Microsoft Entra ID](/downloads/tech-pubs-drafts/zia-draft-articles/authorizing-custom-zscaler-connector-microsoft-applications-doc55384/ZIA-Azure-Request-API-Permissions.png)
[]![Request API permissions page with annotation around Application permissions option](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-Request-API-Permissions-AppPermissions.png)
[]![Request API permissions page with annotations around People.Read.All permission and Add permissions button](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-Request-API-Permissions-AddPermissionsButton.png)
[]![Configured permissions page with annotation around People.Read.All permission](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-Request-API-Permissions-PermissionCreated.png)
[]To authorize a custom connector, you must first manually update the Azure login URL to grant permissions for the application on the tenant. After that, you must provide the Client ID, Client Secret, and Tenant ID in the Admin Portal so that the Zscaler service can access the application. You can create custom connectors for Microsoft SaaS application tenants or for MIP accounts.
- [Creating a Custom Connector for a SaaS Application Tenant](#saas-application-tenant)
- [Creating a Custom Connector for an MIP Account](#mip-account)
[]
- In the Admin Portal, go to **Policies **>** Common Configuration **>** Out-of-Band CASB **>** SaaS Application Tenants**.
- Click **Add SaaS Application Tenant**.
The **Add SaaS Application Tenant** page is displayed.
- Under **Choose the SaaS Application Provider**, select a Microsoft SaaS application.
- In the **Tenant Name** field, provide a name.
- Copy the following URL and paste it in a separate browser tab: `https://login.microsoftonline.com/common/adminconsent?client_id``<client_id>``&state=administration/add-casb-tenants&redirect_uri``<redirect_uri>`.
- In the URL, replace the `client_id` parameter with the **Application (client) ID** that you copied earlier, and replace the `redirect_uri` with the **Redirect URI** that you copied earlier.
- Press `Enter` on your keyboard.
A Microsoft window appears listing the permissions requested by the Zscaler service.
[See image.](#msft-permissions-window)
- Click **Accept**.
You return to the **Add SaaS Application Tenant** page.
- In the **Authorize the SaaS Application** section, select **Custom** for the **SaaS Connector**.
-
[]Enter the values for the **Client ID**, **Client Secret**, and **Tenant ID** that you copied earlier, then click **Authorize**.
[See image.](#saas-app-tenant-authorize)
If you're onboarding SharePoint, also upload the JSON file you created and formatted in the [previous section](#sp_json2).
If you're onboarding Copilot, copy the **Zscaler SaaS Connector** for use in the [next section](#copilot2).
- In the Admin Portal, click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
After adding the tenants, you can configure the Data at Rest Scanning [DLP policy](/unified/about-saas-security-api-dlp), [Malware Detection policy](/unified/about-saas-security-api-malware-detection), and [Scan Configuration](/unified/about-saas-security-api-scan-configuration). You can also view reports and data for the tenants in the SaaS Security [Report](/unified/about-saas-assets-summary-report), [Insights](/unified/saas-security-insights), and [Logs](/unified/about-saas-security-insights-logs).
- []Go to **Policies **>** Data Protection **>** Common Resources** >** MIP Labels**.
-
In the **Microsoft Information Protection (MIP) Labels** tab, click **Add MIP Account**.
The **Add MIP Account **window appears.
[See image.](#add-mip-account-window)
- Copy the following URL and paste it in a separate browser tab: `https://login.microsoftonline.com/common/adminconsent?client_id=<client_id>&state=administration/mip-labels&redirect_uri=``<redirect_uri>`.
- In the URL, replace the `client_id` parameter with the **Application (client) ID** that you copied earlier, and replace the `redirect_uri` with the **Redirect URI** that you copied earlier.
- Press `Enter` on your keyboard.
A Microsoft window appears listing the permissions requested by the Zscaler service.
[See image.](#msft-permissions-window-mip)
- Click **Accept**.
- Return to the **Add MIP Account **window.
- Select **Custom** for the **SaaS Connector**.
-
Enter the values for the **Client ID**, **Client Secret**, and **Tenant ID** that you copied earlier, then click **Validate**.
[See image.](#mip-account-authorize)
The **Add MIP Account** window reappears, displaying the next window for account details.
[See image.](#AccountDetails)
- In the **Add MIP Account** window, under **Account Name**, enter a name you want to associate with the Microsoft account. It must be unique.
-
Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
The MIP account is added to the Admin Portal. The MIP Account displays a status of **Validation Successful **if the account is authorized. It displays a status of **Validation Failed** if the account is not authorized. If the status on the MIP account is **Validation Failed**, you can try the authorization process again by clicking **Reauthorize** on the **Edit MIP Account** window.
- [Change the Label Retrieval field](/unified/retrieving-mip-labels-microsoft-mip-account) for the MIP account.
[]![Add MIP Account authorization window](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/ZIA-Add-MIP-Account-Window-with-Custom.png)
[]![Entering MIP Account details](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/ZIA-Add-MIP-Account-Window-Account-Details.png)
[]![Add MIP Account authorization page in the ZIA Admin Portal and annotation around Validate button](/downloads/zia/documentation-knowledgebase/policies/data-loss-prevention/adding-mip-account/ZIA-CustomMS-MIP-Validate.png)
[]![Microsoft permissions authorization page](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-MSFT-permissions-window.png)
[]![Microsoft app permissions authorization page](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-MSFT-permissions-window.png)
[]![SaaS Application Tenant authorization page in the ZIA Admin Portal](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-CustomMS-Tenant-Authorize.png)
[][]In the following API tables, you need to select a different application from the **Request API permissions** page for each row of the **Microsoft API** column. For example, Azure requires selecting the same **user_impersonation** permission for both **Azure Storage** and **Windows Azure Service Management**.
[See image.](#api_table)
- [Copilot](#copilotapi)
- [Exchange](#exchange)
- [Microsoft Azure Blob Storage](#Azure-blob-storage)
- [Microsoft Information Protection (MIP)](#mip)
- [OneDrive](#onedrive)
- [SharePoint](#sharepoint)
- [Teams](#teams)
[]![Request API permissions pane in Microsoft Entra ID](/downloads/tech-pubs-drafts/zia-draft-articles/authorizing-custom-zscaler-connector-microsoft-applications-doc55384/ZIA-Azure-Request-API-Permissions.png)
[]
| Microsoft API | Microsoft Permissions | Associated Zscaler Actions |
| ------------- | --------------------- | -------------------------- |
| Microsoft Graph APIs | Sites.Read.All | Scanning |
| User.Read.All | Scanning |
[]
-
-
-
-
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| Azure Storage | user_impersonation | Discover Storage AccountScanning |
| Windows Azure Service Management | user_impersonation | Discover Storage AccountScanning |
[]
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| Microsoft Graph | Mail.ReadWrite | Apply Email Tag Label |
| MailboxSettings.Read | Scanning |
| Directory.Read.All | Scanning |
| User.Read.All | Scanning |
| Mail.Send | Quarantine |
| Organization.Read.All | Scanning |
| AuditLog.Read.All | Scanning |
| Member.Read.Hidden | Scanning |
| Reports.Read.All | Scanning |
[]
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| Microsoft Graph | InformationProtectionPolicy.Read.All | Scanning |
| Microsoft Information Protection Sync Service | UnifiedPolicy.Tenant.Read | Scanning |
| Microsoft Rights Management Services | Content.DelegatedWriter | Apply MIP Labels to File |
| Content.Writer | Apply MIP Labels to File |
| Content.SuperUser | Scanning |
| Content.DelegatedReader | Scanning |
[]
-
-
-
-
-
-
-
-
-
-
-
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| Office 365 Management APIs | ActivityFeed.Read | Scanning |
| Microsoft Graph | People.Read.All | Scanning |
| Group.Read.All | Scanning |
| Sites.Manage.All | Scanning |
| Sites.ReadWrite.All | Remove SharingRestore Quarantined FileRemove External CollaboratorsRemove External Collaborators and Shareable LinkRemove Public Shareable LinkRemove Internal Shareable LinkQuarantineQuarantine to User Root FolderRemove File |
| Files.ReadWrite.All | Scanning and QuarantineQuarantine to User Root Folder |
| Directory.Read.All | Scanning |
| GroupMember.Read.All | Scanning |
| Organization.Read.All | Scanning |
| AuditLog.Read.All | Scanning |
| Application.Read.All | Scanning |
| Reports.Read.All | Scanning |
[]
-
-
-
-
-
-
-
-
-
-
-
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| SharePoint API | Sites.Read.All | Scanning |
| Office 365 Management APIs | ActivityFeed.Read | Scanning |
| Microsoft Graph | People.Read.All | Scanning |
| Group.Read.All | Scanning |
| Sites.Manage.All | Scanning |
| Sites.ReadWrite.All | Remove SharingRestore Quarantined FileRemove External CollaboratorsRemove External Collaborators and Shareable LinkRemove Public Shareable LinkRemove Internal Shareable LinkQuarantineQuarantine to User Root FolderRemove File |
| Files.ReadWrite.All | Scanning and QuarantineQuarantine to User Root Folder |
| Directory.Read.All | Scanning |
| GroupMember.Read.All | Scanning |
| Organization.Read.All | Scanning |
| AuditLog.Read.All | Scanning |
| Application.Read.All | Scanning |
| Reports.Read.All | Scanning |
[]
[](/workflow-automation/what-workflow-automation)[](/workflow-automation/what-workflow-automation)
-
-
-
-
-
-
-
-
-
- [](/workflow-automation/what-workflow-automation)
-
[](/workflow-automation/what-workflow-automation)
| Microsoft API | Microsoft Permission | Associated Zscaler Actions |
| ------------- | -------------------- | -------------------------- |
| Office 365 Management APIs | ActivityFeed.Read | Scanning |
| Microsoft Graph | TeamMember.Read.All | Scanning |
| Chat.UpdatePolicyViolation.All | Block Message |
| TeamsAppInstallation.ReadForUser.All | Scanning |
| TeamsAppInstallation.ReadWriteSelfForUser.All | Notify User (ZscalerWorkflow Automation) |
| TeamsAppInstallation.ReadWriteAndConsentForTeam.All | Notify User (ZscalerWorkflow Automation) |
| Sites.Selected | Scanning |
| TeamsActivity.Read.All | Scanning |
| TeamsAppInstallation.ReadForChat.All | Scanning |
| ChannelSettings.Read.All | Scanning |
| Channel.ReadBasic.All | Scanning |
| People.Read.All | Scanning |
| Group.Read.All | Scanning |
| Sites.Read.All | Scanning |
| Sites.ReadWrite.All | Remove SharingRestore Quarantined FileRemove External CollaboratorsRemove External Collaborators and Shareable LinkRemove Public Shareable LinkRemove Internal Shareable LinkQuarantineQuarantine to User Root FolderRemove File |
| ChatMessage.Read.All | Scanning |
| Directory.Read.All | Scanning |
| User.Read.All | Scanning |
| ChannelMember.Read.All | Scanning |
| GroupMember.Read.All | Scanning |
| Files.Read.All | Scanning |
| Team.ReadBasic.All | Scanning |
| Chat.Read.All | Scanning |
| ChannelMessage.Read.All | Scanning |
| ChannelMessage.UpdatePolicyViolation.All | Notify User (ZscalerWorkflow Automation)Notify User |
| Organization.Read.All | Scanning |
| AuditLog.Read.All | Scanning |
| Chat.ReadBasic.All | Scanning |
| Application.Read.All | Scanning |
| ChatMember.Read.All | Scanning |
| TeamsAppInstallation.ReadForTeam.All | Notify User (ZscalerWorkflow Automation) |
| Reports.Read.All | Scanning |
[]![App registrations page with annotation around New registration button](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-NewRegistration.png)
[]![App registration window in Microsoft Entra ID](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-RegisterAnApplication.png)
[]![OneDrive Overview page with annotations around Application (client) ID and Directory (tenant) ID](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-CopyClientTenantID.png)
[]![OneDrive Connector Certificates & secrets with annotations around certificates & secrets and New client secret](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-CertsAndSecrets-NewClientSecret.png)
[]![Add a Client Secret window with Description and Expires fields](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-CertsAndSecrets-AddSecret.png)
[]![Client secret tab selected with annotation around copy Value button](/downloads/zia/policies/saas-security-api/authorizing-custom-zscaler-connector-microsoft-apps/ZIA-Azure-CopyClientSecret.png)