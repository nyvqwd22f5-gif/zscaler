# About Roles
Source: https://help.zscaler.com/unified/about-roles
PDF: https://help.zscaler.com/pdf/com/en/1491581.pdf

For each admin, you can choose from one of the following predefined roles:
- **Administrator**: An admin with this role has read, add, edit, and delete privileges. The default admin account uses this role.
- **Read Only Administrator**: An admin with this role only has read privileges.
If you are an admin that has Administrator level privileges, you can also create a [custom admin role](/unified/configuring-administrator-roles) for your organization. You can only manage and add custom admin roles with an equal or lower level of privileges than your own. Zscaler recommends that you add roles before adding admins, because you must select a role for each admin that you create.
Roles provide the following benefits and enable you to:
- Configure role-based access control using predefined or custom role privileges for admins within your organization.
- Provide admins access to specific features in the Private Apps Admin Portal based on assigned roles.
- Manage the predefined or custom role privileges for your organization.
If admin A has Administrator privileges and performs the following operations on admin B (another user with Administrator privileges), then all active sessions are revoked for admin B:
- Change the password.
- Disable an admin.
- Enable **Force Password Reset**.
- Delete an admin.
- Edit an admin's role.
If an admin with Administrator privileges performs the following operations on themselves, all active sessions, excluding the current one are revoked:
- Change the password.
- Edit an admin’s role.
If an admin with Administrator privileges performs the following operations on themselves, all active sessions, including the current one are revoked: enable **Force Password Reset**.
Deleting admins with Administrator or Read Only Administrator role privileges is not supported for admins with custom roles (i.e., roles with access to specific Private App features). An admin with a custom role that has fewer privileges cannot delete an admin with a custom role that has greater privileges.
About the Roles Page
On the Roles page (Administration > Admin Management > Role Based Access Control > Private Access), you can do the following:
- [Add a new role](/unified/configuring-administrator-roles).
- View a list of all admin roles that are configured for your organization. For each role, you can see:
- **Name**: The name of the role.
- **# of Admins with this Role**: The number of admins that are using the role.
- **# of API Keys with this Role**: The number of API Keys that are using the role.
-
**Description**: The description of the role, if available.
If the permissions for a custom role are missing, you must [edit the custom role](/unified/configuring-administrator-roles) and save the new permissions. A warning icon appears next to the role that indicates when permissions are missing for a custom role.
[See image.](#rolePermissionError)
- [Edit a role](/unified/configuring-administrator-roles).
- Delete a role.
![Viewing and managing roles within the ZPA Admin Portal](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/about-roles/about-roles-page.png)
[]![Viewing the permissions error for a role within the Roles page](/downloads/unified/administration/private-applications/admin-user-role-management/admins-and-roles/about-roles/roles-missing-permissions.png)