# About Access Roles
Source: https://help.zscaler.com/dspm/about-access-roles
PDF: https://help.zscaler.com/pdf/com/en/1474981.pdf

A role determines the set of tasks that [users ](/zidentity/about-users)can perform based on the permissions. DSPM is enabled with ZIdentity as the identity and authentication management service. You need to add and manage users, user groups, and roles in the ZIdentity Admin Portal. To access the ZIdentity Admin Portal, go to **Administration **> **Authentication & Authorization > ZIdentity**. To learn more, see [About Users](/zidentity/about-users).
You can provision users and assign roles to them. Each role has specific permissions that allow users to access and manage various [modules ](/dspm/dspm-modules-and-global-modules)in the DSPM Admin Portal.
The Access Roles feature provides the following benefits and enables you to:
- Configure and manage role-based access control for users in your organization.
- Allow users to access specific modules and perform specific actions depending on the permissions.
- Create custom roles.
Predefined Roles
DSPM provides the following [predefined roles and permissions](/dspm/predefined-roles-and-permissions) that can be assigned to users. You can also [create custom roles](/dspm/about-roles) and add specific permissions.
- **Administrator**: The default super admin role with the highest level of privilege and has access to all DSPM modules and actions.
- **View-Only Administrator**: A default administrator role with View-Only access to all modules and the permission to export data.
- **Security Officer**: A role with View-Only access to all modules and permissions to perform actions across [Policies](/dspm/about-data-posture-policies), [Investigation](/dspm/about-investigation), and [Reports](/dspm/about-reports).
- **IT Administrator**: A role with administrative access to perform actions across [Cloud Accounts](/dspm/about-cloud-accounts), and [Integrations](/dspm/about-third-party-integrations).
- **Data Analyst**: A role with administrative and View-Only access to perform actions across [Policies](/dspm/about-data-posture-policies), [Investigation](/dspm/about-investigation), [Reports](/dspm/about-reports), [Alerts](/dspm/about-alerts), and [Evidence](/dspm/viewing-sensitive-data-details).
- **ZIA Viewer**: A role assigned to the ZIA user to [access the DSPM Admin Portal](/zia/accessing-zscaler-dspm-admin-portal-using-sso) from the ZIA Admin Portal's dashboard via SSO.
-
**DLP Policy Manager**: A role assigned to the ZIA user to access the DSPM Admin Portal from the ZIA Admin Portal's dashboard or Policy via SSO.
**About the Access Roles Page**
On the Access Roles page (Administration > Authentication & Authorization > Access Roles), you can do the following:
- View the list of predefined and custom roles. For each role, you can see:
-
**Role Name**: The name of the role. Click to view the modules assigned to the role.
[See image.](#rolewindow)
- **Role Type**: The type of role (**Predefined **or **Custom**).
- **Permission Count**: The number of permissions assigned to this role.
- [Add a custom role.](/dspm/adding-custom-role)
- Search for a specific role in the searchable columns.
- Export the data as a CSV file.
- [Modify the table rows and columns](/dspm/using-tables).
- [Edit a custom role](/dspm/editing-or-deleting-custom-role).
-
[Delete a custom role](/dspm/editing-or-deleting-custom-role).
You cannot edit or delete predefined roles.
- Sort the column data.
![View the Role Management page](/downloads/dspm/administration/users-groups-roles/about-roles/dspm-access-roles-page.png)
[]![View the modules and global modules assigned to the role](/downloads/dspm/administration/users-groups-roles/about-roles/dspm-role-details-window.png)