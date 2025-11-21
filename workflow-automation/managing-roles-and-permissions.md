# Managing Roles and Permissions
Source: https://help.zscaler.com/workflow-automation/managing-roles-and-permissions
PDF: https://help.zscaler.com/pdf/com/en/1471471.pdf

Workflow Automation enables you to create roles and assign permissions for the admins to access the various features of the Workflow Automation application. Doing so provides you with the flexibility to control admin permissions based on roles. Permissions allow you to control an admin's access to the major features of the Workflow Automation Admin Portal.
Configuring roles and permissions is one of the tasks you must complete before configuring admin assignments in the portal. During an admin assignment, only admins with full access to Workflow Automation can configure roles and assign them to admins who have restricted workflow access. You can assign multiple roles to an admin. To learn more, see [Managing Admins](/workflow-automation/managing-admins).
For each role, you can configure the following permissions for the different features of Workflow Automation:
- **Delete**: This role allows admins to delete the feature. This permission is only available for the Incidents feature.
- **Edit**: This role allows admins to edit the feature.
- **View**: This role only allows admins to view the feature. Admins cannot edit the data.
- **None**: This role provides admins with no access to the feature.
The Roles page provides the following default roles for the admins. You cannot edit or delete these roles. Admins with full access to Workflow Automation can create additional roles.
- **DLP Super Admin**: This role provides users with full access (i.e., edit access) to all features related to Data Loss Prevention (DLP) incidents. It can also delete incidents.
- **DLP Admin**: This role provides users with full access to all DLP incident-related features except Audit Logs, API Management, and Integrations.
- **DLP Incident Manager**: This role provides users with full access to incident-management features, such as viewing incident details and notifying users, as well as adding approvers.
If you are subscribed to ZIdentity, you can assign the configured roles to a user only from the ZIdentity Admin Portal. To learn more, see [About Administrative Entitlements](/zidentity/about-administrative-entitlements).
On the Roles page, you can perform the following actions:
- [Adding Roles and Permissions](#add-roles-permissions)
- [Editing Roles and Permissions](#edit-roles-permissions)
- [Viewing Roles and Permissions](#view-role-and-role-details)
[]To add a role and configure permissions:
- Go to **Setup** > **Roles and Permissions**. The **Roles** page appears, listing all the roles configured for your organization, including the default roles.
- On the **Roles** page, click **Add More**. The **Add Role** window appears.
- In the **Add Role** window:
- **Role**: Enter a name for the role.
- **Product**: The product is **DLP** by default, and you cannot change it.
-
Select permissions for the following categories. For each category, you can assign **Delete**, **Edit**, **View**, or **None** access permissions:
The delete access permission is only available for the Incidents category. The delete access permission is the highest permission and includes full access to the feature—edit permission and delete permission.
- **Analytics**: Enables you to manage the **Incidents Analytics** page, which allows you to monitor and analyze the incident data from a single location at an organizational level.
- **Incidents**: Enables you to manage the **Incidents** and **Incident Details** pages, which capture the transactions that have violated the Data Protection policies.
- **Workflows and Mappings**: Enables you to add workflows to enable remediation actions against an incident without manual user intervention. A workflow mapping specifies the incidents that are associated with the workflow.
- **Workflow Templates**: Enables you to manage workflow templates, which you can use to create workflows for DLP incidents.
- **Incident Group and Mappings**: Enables you to group individual incidents so that you can manage them from a single location. You can also map incident groups to one or more of the incident attributes available in an incident transaction.
- **Priorities**: Enables you to assign a priority of critical, high, medium, or low to all the different incident groups for the organization.
- **Notification Templates**: Enables you to add and map the notification templates to manage all incidents. Notifications are sent when an admin notifies the end user of an incident and escalates an incident to an approver.
- **Survey Templates**: Enables you to configure the survey template format for the survey that a user or approver must complete when responding to an incident notification.
- **Template Mappings**: Enables you to configure template mappings for incident and digest templates. The mappings determine which templates should be used for incident notifications and for the digest notifications.
- **API Management**: Enables you to manage the **API Keys** page, which provides a repository where an organization can store created API keys.
- **Audit Logs**: Enables you to filter and view records of all the admin actions that occurred in the Workflow Automation Admin Portal and APIs.
- **Labels**: Enables you to add and assign labels to the incidents that have occurred in your organization.
- **Integrations**: Enables you to add integration users for integrating Workflow Automation with a ticketing application to create and assign tickets to a user.
- **Account Settings**: Enables you to manage user digest notifications, DLP admin digest notifications, and globally unique identifiers (GUIDs) for your organization.
- **Notification Center**: Enables you to access the **Notification Center **page, which displays alerts that affect the operation of Workflow Automation.
- **Approvers**: Enables you to configure the approvers. During the investigation of an incident, you can escalate the incident to an approver for their review.
[See image.](#add-role-window-image)
- Click **Save.**
[]When managing roles, you can view roles and the details for a role.
- [Viewing Roles](#view-roles-permissions)
- [Viewing Role Details](#view-role-details)
[]To view a role, go to **Setup** > **Roles and Permissions**. The **Roles** page appears, listing all the roles configured for your organization, including the default roles. For each role, you can view the following information:
- **Role**: The name of the role.
- **Edit Access**: The features for which edit access is enabled.
- **View Only Access**: The features for which view-only access is enabled.
[See image.](#view-roles-page)
[]To view role details:
- Go to **Setup** > **Roles and Permissions**. The **Roles** page appears, listing all the roles configured for your organization.
-
In the **Action** column next to the role you want to view, click the **View** icon. The **View Permissions **window appears, displaying the details for the role.
[See image.](#view-permissions-window)
[]To edit a role:
- Go to **Setup** > **Roles and Permissions**. The **Roles** page appears, listing all the roles configured for your organization.
- In the **Action** column next to the role you want to edit, click the **Edit** icon. The **Edit Permissions** window appears.
[See image.](#edit-icon-roles)
- In the **Edit Permissions **window, modify permissions for any category.
- Click **Save**.
To delete a role, click the **Delete** icon in the **Action** column next to the role and then click **Yes** in the dialog window that appears.
[]![Add Role Window](/downloads/workflow-automation/setup/managing-roles-and-permissions/WA-Add-Role-Window.png)
[]![Roles page](/downloads/workflow-automation/setup/managing-roles-and-permissions/WA-Roles-PG-Viewing-Roles_0.png)
[]![View Permissions Window](/downloads/workflow-automation/setup/managing-roles-and-permissions/WA-View-Permissions-Window_0.png)
[]![Roles Page - Edit icon](/downloads/workflow-automation/setup/managing-roles-and-permissions/WA-Roles-PG-Editing-Roles_0.png)