# Integrating with Slack
Source: https://help.zscaler.com/unified/integrating-slack
PDF: https://help.zscaler.com/pdf/com/en/1515286.pdf

You can connect your Slack organization to Zscaler 3rd-Party App Governance to gain continuous visibility and governance for third-party apps installed in the Slack environment, including automation of your vetting and governance processes.
Prerequisite
A user with Admin or Owner roles is required to connect 3rd-Party App Governance to Slack workspace**.**
Connecting Slack to 3rd-Party App Governance
To connect Slack to 3rd-Party App Governance:
- Click the **Connect** icon in the left-side navigation.
[See image.](#Connect_Button)
The **Integrations** window appears.
-
In the **Integrations** window, click **Add **next to **Slack.**
[See image.](#Slack-Integration-Window)
You are redirected to the** Add SaaS Application Tenant** page in the Admin Portal.
- Enter the tenant details and complete the configuration steps required for adding a new SaaS application tenant. To learn more, see [Adding SaaS Application Tenants](/unified/adding-saas-application-tenants).
You must select the **App Governance** checkbox to enable the App Governance feature for the tenant.
The Add SaaS Application Tenant page closes after successful addition of the new tenant. After connection is achieved, it might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the integration is still being processed. After integration is completed, a success message appears, and the number of integrations is updated. You then receive an email from Zscaler when the integration is ready for further review. To learn more about the integration statuses of a tenant, see [Status](#Integration-Status).
Viewing and Managing Slack Integration
You can click **Slack **in the** Integrations **window** **to expand and view the list of added tenants along with information such as the tenant name, enabled features, first connected time, last synced time, and integration status.
- **Tenant**: The name of the tenant integrated with 3rd-Party App Governance.
- **Enabled Features**: The feature that is enabled for the tenant. It can be [App Governance](/unified/what-3rd-party-app-governance), [SSPM Scan](/unified/what-advanced-posture-management), or both.
- **First Connected**: The date and time the tenant was added, and the person who added the tenant.
- **Last Synced**: The date and time the tenant was last synced. If the tenant has yet to sync, **N/A** displays. If the duration of the sync is excessive, the last sync time is highlighted in red.
When there are multiple tenants, 3rd-Party App Governance displays the last sync with the most excessive time duration to indicate an issue so you can expand, view the tenant, and take the relevant actions.
- []**Status**: The integration status of the tenant. One of the following statuses displays:
- **Error**: Failure to achieve a connection. The error message displays the reason for the failure. Contact Zscaler Support if you require further assistance.
- **In progress**: Connection is achieved and 3rd-Party App Governance is ingesting the relevant data. It might take a while to pull and ingest all relevant application data depending on the size of your tenant. During this time, a message displays indicating that the tenant is still being processed. You then receive an email from Zscaler when the tenant is ready for further review.
- **Success**: The integration is completed successfully.
[See image.](#Slack-Integrations-List)
Reconnecting Slack to 3rd-Party App Governance
You might need to reconnect Slack to 3rd-Party App Governance if an error displays (e.g., `Grant Expired`). To reconnect Slack to 3rd-Party App Governance:
- Click **Slack **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Reconnect **icon next to the relevant integration.
[See image.](#Slack-Integration-Reconnect-icon)
A confirmation window appears.
- Click **Confirm** to continue.
A consent window appears. After consent is granted, the connection is updated.
The** Reconnect** option is available only for legacy tenants. The existing tenants onboarded via the 3rd-Party App Governance Admin Portal are called legacy tenants.
Editing a Slack Connection
You can edit a Slack connection to 3rd-Party App Governance. To edit a Slack connection:
- Click **Slack **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Edit **icon next to the relevant integration.
[See image.](#Slack-Integration-Edit-icon)
You are redirected to the **Add SaaS Application Tenant** page in the Admin Portal.
- Edit the tenant details as required and click **Save**.
The connection is updated. The Add SaaS Application Tenant page closes after a successful update.
Deleting a Slack Connection
You can delete a Slack connection to 3rd-Party App Governance. To delete a Slack connection:
- Click **Slack **in the** Integrations **window** **to expand and view the list of added integrations.
-
Click the **Delete **icon next to the relevant integration.
[See image.](#Slack-Integration-Delete-icon)
A confirmation window appears.
- Click **Confirm** to continue.
The following steps are not required for legacy connections.
You are redirected to the [SaaS Application Tenants page](/unified/about-saas-application-tenants) in the Admin Portal.
- Click the **Delete **icon next to the relevant tenant.
A confirmation window appears.
- Click **OK**.
The connection is deleted. The SaaS Application Tenants page closes after successful deletion.
Permissions and Data Collected
The following table lists the permissions and data collected after integration:
Although the app is requesting an "Administer a workspace" permission, 3rd-Party App Governance is utilizing a very limited set of APIs granted by this permission, designed only to read audit and activity logs.
| **Which permissions do we use?** | **What data do we get?** |
| -------------------------------- | ------------------------ |
| View information about your identity. | Basic information of the user connecting to the application |
| View the name, email domain, and icon for workspaces your Slack app is connected to: `team:read` | Basic information about the workspace, such as name, domain, email domain, and icon |
| View people in a workspace: `users:read` | Basic information of users in your workspace |
| View email addresses of people in a workspace: `users:read.email` | Email addresses of users in your workspace |
| View user groups in a workspace: `usergroups:read` | List of user groups in your workspace |
| Administer a workspace: `admin` | Collect workspace access logs and applications (integrations) activities such as consent, revoke, and others. This allows you to measure app usage, and detect suspicious app activity, permission anomalies, and others. |
[]![Connect Icon allows you to add new integrations](/downloads/zia/apptotal/getting-started/connecting-your-platforms/slack-integration/Connect_Button.png)
[]
[]![The Slack Integrations Window showing the Add button](/downloads/tech-pubs-drafts/zia-draft-articles/integrating-slack-draft-doc-56246/Slack_Add_Redirect.png)
[]![The Slack Integrations List allows you to view the number of integrations and tenant details](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-slack/Slack_View_Integrations_List.png)
[]![The Slack Integration Reconnect icon allows you to reconnect Slack to 3rd-Party App Governance](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-slack/Reconnect_Icon.png)
[]![The Slack Integration Edit Icon allows you to edit a Slack connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-slack/Microsoft_Edit_Icon.png)
[]![The Slack Integration Delete Icon allows you to delete a Slack connection](/downloads/zia/apptotal/getting-started/connecting-your-platforms/integrating-with-slack/Microsoft_Delete_Icon.png)