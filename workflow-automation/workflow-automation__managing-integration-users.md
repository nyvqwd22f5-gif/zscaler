# Managing Integration Users
Source: https://help.zscaler.com/workflow-automation/managing-integration-users
PDF: https://help.zscaler.com/pdf/com/en/1457436.pdf

Adding integration users on the Integration Users page is required if you are integrating Workflow Automation with a ticketing integration application (e.g., ServiceNow and Jira Software). During the remediation of an incident on the Incident Details page in Workflow Automation, admins can perform a ticket action against an incident. This action creates and assigns a ticket in the ticketing integration application to a user and associates that ticket with the incident. When performing this ticket action, the admin must select a user who already exists on the Integration Users page. After the ticket is created in the ticketing integration application, the ticket information displays in the Ticket section on the Incident Details page. The Ticket section contains an incident link that enables the admins to access the ticketing integration application for that specific ticket if they have the appropriate credentials for the application.
The user assigned to the ticket can manage that ticket within the ticketing integration application itself.
Adding Integration Users
To add an integration user:
- Go to **Setup** > **Integration Users**. The **Integration Users** page appears, listing all the integration users who were added for your organization.
- On the **Integration Users** page, click **Add More**. The **Add User** window appears.
- In the **Add User** window:
- **Integration**: From the drop-down menu, select the tenant ID associated with the ticketing integration application (e.g., ServiceNow or Jira Software).
- **Email**: Enter the email address for the user whom you want to associate with the ticketing integration application. You can only add users who are available in the ticketing integration application selected. After you enter the email address, the **Name** and **Username** fields associated with that email address appear in the window.
[See image.](#add-integration-user-page)
- Click **Add User**.
Viewing Integration Users
To view integration users:
- Go to **Setup** > **Integration Users**. The **Integration Users** page appears, listing all the integration users who were added for your organization.
- For each integration user, you can view the following information:
- **Name**: The name of the user associated with the ticketing integration application.
- **Email ID**: The email ID for the user.
- **Integration Type**: The type of integration associated with the user. Integration types are **ServiceNow **and** JiraCloud**.
- **Integration**: The tenant ID associated with the ticketing integration application (e.g., ServiceNow or Jira Software).
[See image.](#Integration-Users-page-viewing-all)
[]![Integration Users Page - Add User window](/downloads/workflow-automation/setup/managing-integration-users/WA-Add-User-Window.png)
[]![Integration Users Page - View All Existing Users](/downloads/workflow-automation/setup/managing-integration-users/WA-Integration-Users-Page-View-All-Users.png)