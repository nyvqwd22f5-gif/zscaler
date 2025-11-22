# About Roles
Source: https://help.zscaler.com/zpa/about-roles
PDF: https://help.zscaler.com/pdf/com/en/1483996.pdf

For each admin, you can choose from one of the following predefined roles:
- **ZPA Administrator**: An admin with this role has read, add, edit, and delete privileges in the ZPA Admin Portal. The default admin account uses this role.
- **ZPA Read Only Administrator**: An admin with this role only has read privileges in the ZPA Admin Portal.
If you are an admin that has ZPA Administrator privileges, you can also create a [custom admin role](/zpa/about-role/new) for your organization. You can only manage and add custom admin roles with an equal or lower level of privileges than your own. Zscaler recommends that you add roles before adding admins, because you must select a role for each admin that you create.
Roles provide the following benefits and enable you to:
- Configure role-based access control using predefined or custom role privileges for admins within your organization.
- Provide admins access to specific features in the ZPA Admin Portal based on assigned roles.
- Manage the predefined or custom role privileges for your organization.
If admin A has ZPA Administrator privileges and performs the following operations on admin B (another user with ZPA Administrator privileges), then all active sessions are revoked for admin B:
- Change the password.
- Disable an admin.
- Enable Force Password Reset.
- Delete an admin.
- Edit an admin's role.
If an admin with ZPA Administrator privileges performs the following operations on themselves, all active sessions excluding the current one are revoked:
- Change the password.
- Edit an admin’s role.
If an admin with ZPA Administrator privileges enables Force Password Reset on themselves, then all active sessions including the current ones are revoked.
Deleting admins with ZPA Administrator or ZPA Read Only Administrator role privileges is not supported for admins with custom roles (i.e., roles with access to specific ZPA features). An admin with a custom role that has fewer privileges cannot delete an admin with a custom role that has greater privileges.
About the Roles Page
On the Roles page (Configuration & Control > Administration Control > Roles), you can do the following:
- Refresh the Roles page to reflect the most current information.
- [Add a new role](/zpa/configuring-administrator-roles#add).
-
View a list of all admin roles that are configured for your organization. For each role, you can see:
- **Name**: The name of the role.
- **# of Admins with This Role**: The number of admins that are using the role.
- **# of API Keys with This Role**: The number of API keys that are using the role.
- **Description**: The description of the role, if available.
If the permissions for a custom role are missing, you must [edit the custom role](/zpa/configuring-administrator-roles#edit) and save the new permissions. A warning icon appears next to the role that indicates when permissions are missing for a custom role.
[See image.](#rolePermissionError)
- [Edit a role](/zpa/configuring-administrator-roles#edit).
- Delete a role.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Go to the [Administrators](/zpa/about-users) page to add new admins or manage existing admins.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your [user portals](/zpa/about-user-portals).
- Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
- Go to the [Disaster Recovery](/zpa/understanding-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery. You can also view and configure the [disaster recovery settings](/zpa/about-disaster-recovery-settings).
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
![Viewing and managing roles](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/about-roles/zpa-roles-page_0.png)
[]![Viewing the permissions error ](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/about-roles/zpa-roles-permission-issue.png)