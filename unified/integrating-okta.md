# Integrating with Okta
Source: https://help.zscaler.com/zia/integrating-okta
PDF: https://help.zscaler.com/pdf/com/en/1462171.pdf

You can connect your Okta organization to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in the Okta environment.
Okta integration consists of the following steps:
- [Creating a Dedicated Read-Only Service Account for 3rd-Party App Governance Integration](#Create-Account)
- [Getting the Okta API Token and Okta Domain](#Get-Token-domain)
- [Connecting Okta to 3rd-Party App Governance](#Connect-Okta)
Prerequisites
Ensure the following prerequisites are met:
- A user with Okta Admin privileges
- An Okta API token for an administrative account in your Okta organization
Zscaler recommends creating a dedicated service account for integration and assigning the minimum required privileges.
[]Creating a Dedicated Read-Only Service Account for 3rd-Party App Governance Integration
To create a dedicated read-only service account:
- Sign in to your Okta organization as a user with[ administrator privileges](https://help.okta.com/en-us/Content/Topics/Security/Administrators.htm?cshid=ext_Security_Administrators).
- In the Okta Admin console, go to** Directory **>** People**, and then click **Add person**.
- In the **Add Person** window, enter the information for the 3rd-Party App Governance service account, set the password, and then click **Save**.
- In the Okta Admin console, go to **Security **> **Administrators**, and then click **Add administrator**.
- Select the 3rd-Party App Governance service account, set the role to** Super Administrator**, and click **Save**.
- Sign out and sign in to your Okta Admin console with the newly created 3rd-Party App Governance service account.
[]Getting the Okta API Token and Okta Domain
To get your Okta API token and Okta domain:
- Sign in to the Okta Admin console.
Zscaler recommends that you sign in with the dedicated service account that you created for 3rd-Party App Governance integration.
- [Create an API token in Okta](https://developer.okta.com/docs/guides/create-an-api-token/main/).
- Note the API token you created. You will need it in the following steps.
For security reasons, you cannot view the API key in plain text. You must store the API key securely.
- From your Okta organization URL (e.g., yourdomain.okta.com), copy and save your Okta domain "yourdomain." Do not copy the entire Okta Admin console URL, or you can also just remove "-admin" from the URL.
[]Connecting Okta to 3rd-Party App Governance
To connect Okta to 3rd-Party App Governance:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect-Button)
The **Integrations** window appears.
-
In the **Integrations** window, click **Add **next to **Okta**.
[See image.](#Okta-Integration-Window)
You are redirected to the** Add SaaS Application Tenant** page in the ZIA Admin Portal.
- Enter the tenant details and complete the configuration steps required for adding a new SaaS application tenant. To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
You must select the **App Governance** checkbox to enable the App Governance feature for the tenant.
The Add SaaS Application Tenant page closes after successful addition of the new tenant. After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the integration is still being processed. After integration is completed, a success message appears, and the number of integrations is updated. You then receive an email from Zscaler when the integration is ready for further review. To learn more about the integration statuses of a tenant, see [Status](#Integration-Status).
Viewing and Managing Okta Integration
You can click **Okta **in the** Integrations **window** **to expand and view the list of added tenants along with information such as the tenant name, enabled features, first connected time, last synced time, and integration status.
- **Tenant**: The name of the tenant integrated with 3rd-Party App Governance.
- **Enabled Features**: The feature that is enabled for the tenant. It can be [App Governance](/zia/what-3rd-party-app-governance), [SSPM Scan](/zia/what-advanced-posture-management), or both.
- **First Connected**: The date and time the tenant was added, and the person who added the tenant.
- **Last Synced**: The date and time the tenant was last synced. If the tenant has yet to sync, **N/A** displays. If the duration of the sync is excessive, the last sync time is highlighted in red.
When there are multiple tenants, 3rd-Party App Governance displays the last sync with the most excessive time duration to indicate an issue so you can expand, view the tenant, and take the relevant actions.
- []**Status**: The integration status of the tenant. One of the following statuses displays:
- **Error**: Failure to achieve a connection. The error message displays the reason for the failure. Contact Zscaler Support if you require further assistance.
- **In progress**: Connection is achieved and 3rd-Party App Governance is ingesting the relevant data. It might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the tenant is still being processed. You then receive an email from Zscaler when the tenant is ready for further review.
- **Success**: The integration is completed successfully.
[See image.](#Okta-Integrations-List)
Updating the Okta Token
For a legacy connection, you can update an Okta token that is currently in use. The existing connections that were added via the 3rd-Party App Governance Admin Portal are called legacy connections. To update the Okta token:
- Click **Okta **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Edit** icon next to the token for the relevant integration.
[See image.](#Okta-Token-Edit-Icon)
- Update the token and click the check mark to save the changes.
A confirmation window appears.
- Click **Confirm** if you want to override the connection.
The connection is updated.
Editing an Okta Connection
You can edit an Okta connection to 3rd-Party App Governance. To edit an Okta connection:
- Click** Okta** in the** Integrations **window** **to expand and view the list of added integrations.
- Click the **Edit **icon next to the relevant integration.
You are redirected to the **Add SaaS Application Tenant** page in the ZIA Admin Portal.
- Edit the tenant details as required and click **Save**.
The connection is updated. The Add SaaS Application Tenant page closes after a successful update.
Deleting an Okta Connection
You can delete an Okta connection to 3rd-Party App Governance. To delete an Okta connection:
- Click **Okta** in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Delete **icon next to the relevant integration.
[See image.](#Okta-Integration-Delete-Icon)
A confirmation window appears.
- Click **Confirm** to continue.
The following steps are not required for legacy connections.
You are redirected to the [SaaS Application Tenants page](/zia/about-saas-application-tenants) in the ZIA Admin Portal.
- Click the **Delete **icon next to the relevant tenant.
A confirmation window appears.
- Click **OK**.
The connection is deleted. The SaaS Application Tenants page closes after successful deletion.
[]APIs and Data Collected
The following table lists the APIs used and the data collected after integration:
| **Which APIs do we use?** | **What data do we collect?** |
| ------------------------- | ---------------------------- |
| /users | List of users and their profile attributes, such as name, email, status, and time of last login |
| /users/…/roles | User role assignments (e.g., admin, super admin, user, etc.) |
| /groups | List of user groups which are configured in the tenant (e.g., “All employees,” “Accounting,” etc.) |
| /groups/…/users | The list of users associated with each of the above groups |
| /groups/…/apps | The list of apps associated with each of the above groups (e.g., “Salesforce” for the “Sales” group) |
| /apps | List of apps available in the tenant along with their metadata |
| /apps/…/users | List of users associated with each application |
| /apps/…/grants | For some types of applications, a list of permission scopes granted to the application |
| /api-tokens | List of API tokens that have been generated in the tenant, along with their metadata, such as token name, the user who generated it, and its creation and expiration dates |
[]![Connect Icon allows you to add new integrations](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-okta/Connect_Button.png)
[]![The Okta Integrations Window showing the Add button](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-okta/Okta_Add_Redirect1.png)
[]![The Okta Integrations List allows you to view the number of integrations and tenant details](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-okta/Okta_View_Integrations_List.png)
[]![The Okta Token Edit Icon allows you to update the Okta token](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-okta/Okta_Token_Edit_Icon.png)
[]![The Okta Integration Delete Icon allows you to delete an Okta connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-okta/Okta_Delete_Icon.png)