# Integrating with Google Workspace
Source: https://help.zscaler.com/unified/integrating-google-workspace
PDF: https://help.zscaler.com/pdf/com/en/1515266.pdf

You can connect your Google Workspace organization to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in the Google Workspace environment, including automation of your vetting and governance processes.
Prerequisite
A user with Google Admin privileges is required to connect 3rd-Party App Governance to Google Workspace.
Some organizations prefer to use a dedicated service account for new service integrations. We recommend following your standard practice when connecting new services to your business applications.
Connecting Google Workspace to 3rd-Party App Governance
To connect Google Workspace to 3rd-Party App Governance:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect-Button)
The **Integrations** window appears.
-
In the **Integrations** window, click **Add** next to **Google Workspace**.
[See image.](#Google-Workspace-Integration-Window)
You are redirected to the** Add SaaS Application Tenant** page in the Admin Portal.
- Enter the tenant details and complete the configuration steps required for adding a new SaaS application tenant. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
You must select the **App Governance** checkbox to enable the App Governance feature for the tenant.
The Add SaaS Application Tenant page closes after successful addition of the new tenant. After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the integration is still being processed. After integration is completed, a success message appears, and the number of integrations is updated. You then receive an email from Zscaler when the integration is ready for further review. To learn more about the integration statuses of a tenant, see [Status](#Integration-Status).
Viewing and Managing Google Workspace Integration
You can click **Google Workspace**** **in the** Integrations **window to expand and view the list of added tenants along with information such as the tenant name, enabled features, first connected time, last synced time, and integration status.
- **Tenant**: The name of the tenant integrated with 3rd-Party App Governance.
- **Enabled Features**: The feature that is enabled for the tenant. It can be [App Governance](/unified/what-3rd-party-app-governance), [SSPM Scan](/unified/what-advanced-posture-management), or both.
- **First Connected**: The date and time the tenant was added, and the person who added the tenant.
- **Last Synced**: The date and time the tenant was last synced. If the tenant has yet to sync, **N/A** displays. If the duration of the sync is excessive, the last sync time is highlighted in red.
When there are multiple tenants, 3rd-Party App Governance displays the last sync with the most excessive time duration to indicate an issue so you can expand, view the tenant, and take the relevant actions.
- []**Status**: The integration status of the tenant. One of the following statuses displays:
- **Error**: Failure to achieve a connection. The error message displays the reason for the failure. Contact Zscaler Support if you require further assistance.
- **In progress**: Connection is achieved and 3rd-Party App Governance is ingesting the relevant data. It might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the tenant is still being processed. You then receive an email from Zscaler when the tenant is ready for further review.
- **Success**: The integration is completed successfully.
[See image.](#Google-Workspace-Integrations-List)
Reconnecting Google Workspace to 3rd-Party App Governance
You might need to reconnect Google Workspace to 3rd-Party App Governance if an error displays (e.g., `Grant Expired`). To reconnect Google Workspace to 3rd-Party App Governance:
- Click **Google Workspace**** **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Reconnect **icon next to the relevant integration.
[See image.](#Google-Workspace-Integration-Reconnect-Icon)
A confirmation window appears.
- Click **Confirm** to continue.
A consent window appears. After consent is granted, the connection is updated.
The** Reconnect** option is available only for legacy tenants. The existing tenants onboarded via the 3rd-Party App Governance Admin Portal are called legacy tenants.
Editing a Google Workspace Connection
You can edit a Google Workspace connection to 3rd-Party App Governance. To edit a Google Workspace connection:
- Click **Google Workspace **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Edit **icon next to the relevant integration.
[See image.](#Google-Workspace-Integration-Edit-Icon)
You are redirected to the **Add SaaS Application Tenant** page in the Admin Portal.
- Edit the tenant details as required and click **Save**.
The connection is updated. The Add SaaS Application Tenant page closes after a successful update.
Deleting a Google Workspace Connection
You can delete a Google Workspace connection to 3rd-Party App Governance. To delete a Google Workspace connection:
- Click **Google Workspace**** **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Delete **icon next to the relevant integration.
[See image.](#Google-Workspace-Integration-Delete-Icon)
A confirmation window appears.
- Click **Confirm** to continue.
The following step is not required for legacy connections.
You are redirected to the [SaaS Application Tenants page](/unified/about-saas-application-tenants) in the Admin Portal, where a confirmation window appears.
- Click **OK**.
The connection is deleted. The SaaS Application Tenants page closes after successful deletion.
Permissions and Data Collected
The following table lists the permissions and data collected after integration:
| **Which permissions do we use?** | **What data do we get?** |
| -------------------------------- | ------------------------ |
| View audit reports for your G Suite tenant:`https://www.googleapis.com/auth/admin.reports.audit.readonly` | Admin, Token, and Login activity audit reports |
| View usage reports for your G Suite tenant:`https://www.googleapis.com/auth/admin.reports.usage.readonly` | Login activity reports |
| View groups in your tenant:`https://www.googleapis.com/auth/admin.directory.group.readonly` | A list of groups in your Google tenant |
| See info about users in your tenant:`https://www.googleapis.com/auth/admin.directory.user.readonly` | A list of users in your Google tenant |
| View data access permissions for users in your tenant:`https://www.googleapis.com/auth/admin.directory.user.security` | OAuth grants your users access to 3rd-party applications |
Troubleshooting
The error message `This app is blocked` appears when connecting 3rd-Party App Governance to your Google Workspace.
[See image.](#Error-Message)
Occasionally, company settings might prevent connecting to third-party apps without explicitly trusting them.
To resolve this issue, add 3rd-Party App Governance to your Google Workspace trusted apps.
To manually trust the integration:
-
In the Google Admin Console, go to **Security** > **API Controls**.
Google Administrative privileges are required for accessing the Google Admin Console.
-
Under **App Access Control**, select **Manage Third-Party App Access**.
-
Click **Configure a new app**.
-
Enter the following client ID: `1017448667100-p63ee1484o66sdnfreusoafl8hp9oci5.apps.googleusercontent.com`.
-
Make sure **Trusted: can access all Google services** is selected, and then click **Configure**.
-
Go* *back to the 3rd-Party App Governance Connect page and connect to Google Workspace again.
[]![Connect Icon allows you to add new integrations](/downloads/zia/apptotal/getting-started/connecting-your-platforms/google-workspace-integration/Connect_Button.png)
[]![The Google Workspace Integrations Window showing the Add button](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-google-workspace/GoogleIntegration_Add_Redirect.png)
[]![The Google Workspace Integrations List allows you to view the number of integrations and tenant details](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-google-workspace/Google_View_Integrations_List.png)
[]![The Google Workspace Integration Reconnect icon allows you to reconnect Google Workspace to 3rd-Party App Governance](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-google-workspace/Reconnect_Icon.png)
[]![The Google Workspace Integration Edit Icon allows you to edit a Google Workspace connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-google-workspace/Google_Edit_Icon.png)
[]![The Google Workspace Integration Delete Icon allows you to delete a Google Workspace connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-google-workspace/Google_Delete_Icon.png)
![Error Message indicating the app is blocked](/downloads/zia/apptotal/getting-started/connecting-your-platforms/google-workspace-integration/This%20app%20is%20blocked.png)
[]