# Managing Integration Users for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-integration-users-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1487456.pdf

Adding integration users on the Integration Users page is required if you are integrating Workflow Automation with a ticketing integration application (e.g., ServiceNow). When configuring workflows to automatically trigger tickets for ZDX alerts, admins must assign a user to remediate the alerts. The selected user must already exist on the Integrations Users page. There is no option to view or track the status of the ticket from Workflow Automation. Admins can access the ticketing integration application to track the specific ticket if they have the appropriate credentials for the application.
The user assigned to the ticket can manage that ticket within the ticketing integration application itself.
On the Integration Users page, you can do the following:
- [Add Integration Users](#adding-integration-users)
- [Integration Users](#view-integration-users)
[]To add an integration user:
- Go to **Setup** > **Integrations Users**. The **Integration Users** page appears, listing all the integration users that were added for your organization.
- On the **Integration Users** page, click **Add More**. The **Add User** window appears.
-
In the **Add User** window:
- **Integration**: Select the tenant ID associated with the ticketing integration application from the drop-down menu.
-
**Email**: Enter the email address for the user you want to associate with the ticketing integration application. You can only add users that are available in the ticketing integration application selected.
After you enter the email address, the **Name** and **Username** fields with values associated with that email address appear in the window.
[See image.](#add-integration-user-page)
- Click **Add User**.
[]To view integration users, go to **Setup** > **Integrations Users**. The **Integration Users** page appears, listing all the integration users that were added for your organization. For integration users, you can view:
- **Name**: The name of the user associated with the ticketing integration application.
- **Email ID**: The email ID for the user.
- **Integration Type**: The type of integration associated with the user.
- **Integration**: The tenant ID associated with the ticketing integration application.
[See image.](#Integration-Users-page-viewing-all)
[]![Adding an integration user on the Add User window in the Integration Users page. The Add User window has fields for Integration, Email, Name, and Username.](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-integration-users-zdx-alerts/WA-ZDX-Add-User-Window.png)
[]![Viewing integration users on the Integration Users page. The integration users are listed in a table that has columns for Name, Email ID, Integration Type, and Integration.](/downloads/workflow-automation/zscaler-digital-experience/setup/managing-integration-users-zdx-alerts/WA-ZDX-Integration-Users-Page-View-Initial.png)