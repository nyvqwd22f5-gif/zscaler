# Integrating with Salesforce
Source: https://help.zscaler.com/unified/integrating-salesforce
PDF: https://help.zscaler.com/pdf/com/en/1515281.pdf

You can connect your Salesforce organization to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in the Salesforce environment, including automation of your vetting and governance processes.
Prerequisite
A user with Admin privileges in the relevant Salesforce organization is required to connect 3rd-Party App Governance to your Salesforce organization.
Connecting Salesforce to 3rd-Party App Governance
To connect your Salesforce organization to 3rd-Party App Governance:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect-Button)
The **Integrations** window appears.
-
In the **Integrations** window, click **Add **next to **Salesforce.**
[See image.](#Salesforce-Integration-Window)
You are redirected to the** Add SaaS Application Tenant** page in the Admin Portal.
Click** Sandbox** to log in to your Salesforce Sandbox account.
- Enter the tenant details and complete the configuration steps required for adding a new SaaS application tenant. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
You must select the **App Governance** checkbox to enable the App Governance feature for the tenant.
The Add SaaS Application Tenant page closes after successful addition of the new tenant. After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the integration is still being processed. After integration is completed, a success message appears, and the number of integrations is updated. You then receive an email from Zscaler when the integration is ready for further review. To learn more about the integration statuses of a tenant, see [Status](#Integration-Status).
Viewing and Managing Salesforce Integration
You can click **Salesforce **in the** Integrations **window** **to expand and view the list of added tenants along with information such as the tenant name, enabled features, first connected time, last synced time, and integration status.
- **Tenant**: The name of the tenant integrated with 3rd-Party App Governance.
- **Enabled Features**: The feature that is enabled for the tenant. It can be [App Governance](/unified/what-3rd-party-app-governance), [SSPM Scan,](/unified/what-advanced-posture-management) or both.
- **First Connected**: The date and time the tenant was added, and the person who added the tenant.
- **Last Synced**: The date and time the tenant was last synced. If the tenant has yet to sync, **N/A** displays. If the duration of the sync is excessive, the last sync time is highlighted in red.
When there are multiple tenants, 3rd-Party App Governance displays the last sync with the most excessive time duration to indicate an issue so you can expand, view the tenant, and take the relevant actions.
- []**Status**: The integration status of the tenant. One of the following statuses displays:
- **Error**: Failure to achieve a connection. The error message displays the reason for the failure. Contact Zscaler Support if you require further assistance.
- **In progress**: Connection is achieved and 3rd-Party App Governance is ingesting the relevant data. It might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the tenant is still being processed. You then receive an email from Zscaler when the tenant is ready for further review.
- **Success**: The integration is completed successfully.
[See image.](#Salesforce-Integrations-List)
Reconnecting Salesforce to 3rd-Party App Governance
You might need to reconnect Salesforce to 3rd-Party App Governance if an error displays (e.g., `Grant Expired`). To reconnect Salesforce to 3rd-Party App Governance:
- Click **Salesforce **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Reconnect **icon next to the relevant integration.
[See image.](#Salesforce-Integration-Reconnect-Icon)
A confirmation window appears.
- Click **Confirm** to continue.
A consent window appears. After consent is granted, the connection is updated.
The** Reconnect** option is available only for legacy tenants. The existing tenants onboarded via the 3rd-Party App Governance Admin Portal are called legacy tenants.
Editing a Salesforce Connection
You can edit a Salesforce connection to 3rd-Party App Governance. To edit a Salesforce connection:
- Click **Salesforce **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Edit **icon next to the relevant integration.
[See image.](#Salesforce-Integration-Edit-Icon)
You are redirected to the **Add SaaS Application Tenant** page in the Admin Portal.
- Edit the tenant details as required and click **Save**.
The connection is updated. The Add SaaS Application Tenant page closes after a successful update.
Deleting a Salesforce Connection
You can delete a Salesforce connection to 3rd-Party App Governance. To delete a Salesforce connection:
- Click **Salesforce **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Delete **icon next to the relevant integration.
[See image.](#Salesforce-Integration-Delete-Icon)
A confirmation window appears.
- Click **Confirm** to continue.
The following steps are not required for legacy connections.
You are redirected to the [SaaS Application Tenants page](/unified/about-saas-application-tenants) in the Admin Portal.
- Click the **Delete **icon next to the relevant tenant.
A confirmation window appears.
- Click **OK**.
The connection is deleted. The SaaS Application Tenants page closes after successful deletion.
[]Permissions and Data Collected
The following table lists the permissions and data collected after integration:
| **Which permissions do we use?** | **What data do we get?** |
| -------------------------------- | ------------------------ |
| api | Manage user data via APIs. It allows access to the currently logged-in user’s account using APIs, such as REST API and Bulk API 2.0. This scope also includes `chatter_api`, which allows access to Connect REST API resources. |
| web | Manage user data via web browsers. It allows use of `access_token `on the web. This scope also includes Visualforce, allowing access to customer-created Visualforce pages. |
[]![Connect Icon allows you to add new integrations](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Connect_Button.png)
[]![The Salesforce Integrations Window showing the Add button](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Salesforce_Add_Redirect.png)
[]![The Salesforce Integrations List allows you to view the number of integrations and tenant details](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Salesforce_View_Integrations_List.png)
[]![The Salesforce Integration Reconnect Icon allows you to reconnect Salesforce to 3rd-Party App Governance](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Reconnect_Icon.png)
[]![The Salesforce Integration Edit Icon allows you to edit a Salesforce connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Microsoft_Edit_Icon.png)
[]![The Salesforce Integration Delete Icon allows you to delete a Salesforce connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-salesforce/Microsoft_Delete_Icon.png)