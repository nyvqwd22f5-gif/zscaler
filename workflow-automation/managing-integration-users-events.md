# Managing Integration Users for Events
Source: https://help.zscaler.com/workflow-automation/managing-integration-users-events
PDF: https://help.zscaler.com/pdf/com/en/1500271.pdf

Adding users on the Integration Users page is required if you are integrating Workflow Automation with a ticketing integration application (e.g., ServiceNow). When configuring workflows to automatically trigger tickets for events, admins must select an integration user who can be assigned to the ticket in the ticketing application. The selected user must already exist on the Integrations Users page. Admins can access the ticketing integration application to track the specific ticket if they have the appropriate credentials for the application. The user assigned to the ticket can manage that ticket within the ticketing integration application itself.
On the Integration Users page, you can do the following:
- [View Integration Users](#view-integration-users)
- [Add Integration Users](#adding-integration-users)
[]To add an integration user:
- Go to **Setup** > **Integrations Users**. The **Integration Users** page appears, listing all the integration users that were added for your organization.
- On the **Integration Users** page, click **Add More**. The **Add User** window appears.
-
In the **Add User** window:
- **Integration**: From the drop-down menu, select the tenant ID associated with the ticketing integration application (e.g., ServiceNow).
-
**Email**: Enter the email address for the user you want to associate with the ticketing integration application. You can only add users that are available in the ticketing integration application.
After you enter the email address, the **Name** and **Username** fields associated with that email address appear in the window.
[See image.](#add-integration-user-page)
- Click **Add User**.
[]To view integration users:
- Go to **Setup** > **Integrations Users**. The **Integration Users** page appears, listing all the integration users that were added for your organization.
-
For each integration user, you can view:
- **Name**: The name of the user associated with the ticketing integration application.
- **Email ID**: The email ID for the user.
- **Integration Type**: The type of integration associated with the user. The integration type is **ServiceNow**.
- **Integration**: The tenant ID associated with the ticketing integration application.
[See image.](#Integration-Users-page-viewing-all)
[]![Integration Users Page - Add User Window](/downloads/workflow-automation/business-insights/setup/managing-integration-users-events/WA-BI-Integration-Users-PG-Add-User-Window.png)
[]![Integration Users Page - View Existing Users](/downloads/workflow-automation/business-insights/setup/managing-integration-users-events/WA-BI-Integration-Users-PG-View-All.png)