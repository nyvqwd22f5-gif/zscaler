# About Audit Logs
Source: https://help.zscaler.com/workflow-automation/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1455406.pdf

The Audit Logs page records and displays the actions of every admin in the Workflow Automation Admin Portal and the actions that occur through the Workflow Automation APIs.
Audit logs provide the following benefits and enable you to:
- View alterations that are made in the Workflow Automation Admin Portal.
- View details on all the changes made by an admin.
- Detect and investigate suspicious activity and track unauthorized access to the Workflow Automation Admin Portal.
About the Audit Logs Page
On the Audit Logs page (Setup > Audit Logs), you can do the following:
- Select a time range for the audit logs displayed.
- Filter the audit logs by admin, action, module, or resource.
- Reset all the applied filters.
- Search for an audit log.
- View a list of actions that have occurred. For each action, you can see:
- **Timestamp**: The date and time when the action occurred.
- **Action**: The action that the admin performed in the Workflow Automation Admin Portal or the action performed by an API. Potential actions include:
- Insert
- Update
- Delete
- **Module**: The module for which an admin or API action was recorded. Potential modules include:
- API Keys
- Csv Upload
-
Customers
Changes made to the **Privacy and Security** section of the **Account Settings** page appear with this module.
- DLP
- Incident Group
- Integrations
- Template Mapping
- Workflow
- Workflow Definition
- **Resource**: The audited entity within a module. Potential resources include:
- Admin Configuration
- API Key
- Csv User Data
-
Customer
Changes made to the **Privacy and Security** section of the **Account Settings** page appear with this resource.
- Incident Group
- Incident Group Mapping
- Integration Configuration
- Template Mapping
- Workflow Definition
- Workflow Definition Mapping
- **Admin ID**: The login ID of the admin who performed the actions in the Workflow Automation Admin Portal. If the admin has a shared login ID, this field displays no value.
- **Change Notes**: The metadata of the configuration changes that occurred in the Workflow Automation Admin Portal.
- [View configuration changes.](#view-change)
[]To view the configuration changes, click the **View** icon next to an audit log entry. The **Change** window appears and the differences between the pre-changes configuration and post-changes configuration are highlighted.
There are three types of actions you can view:
-
Insert. The following image displays an example of a CSV upload insert:
[See image.](#insert-example)
- Update. The following image displays an example of an update to an incident group:
[See image.](#update-example)
- Delete. The following image displays an example of a deleted API key:
[See image.](#deleted-change)
![Audit Logs Page](/downloads/workflow-automation/setup/about-audit-logs/WA-about-audit-logs-main-page.png)
![Screenshot of the Audit Logs Page - Change window displaying an example configuration for Insert action](/downloads/workflow-automation/data-protection/setup/about-audit-logs/WA-about-audit-logs-csv-upload-insert-changes.png)
[]
[]![Screenshot of the Audit Logs Page - Change window displaying an example configuration for Update action](/downloads/workflow-automation/data-protection/setup/about-audit-logs/WA-about-audit-logs-csv-upload-update-changes.png)
![Screenshot of the Audit Logs Page - Change window displaying an example configuration for Delete action](/downloads/workflow-automation/data-protection/setup/about-audit-logs/WA-about-audit-logs-csv-upload-delete-changes.png)
[]