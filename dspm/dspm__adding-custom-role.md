# Adding a Custom Role
Source: https://help.zscaler.com/dspm/adding-custom-role
PDF: https://help.zscaler.com/pdf/com/en/1474991.pdf

You can add custom roles and assign them to users to manage tasks in specific [modules or global modules](/dspm/dspm-modules-and-global-modules). The roles are automatically synced ZIdentity at regular intervals. You can also manually sync the roles from the [View Roles page](/zidentity/about-administrative-entitlements) in the ZIdentity Admin Portal.
You must add users and assign roles in the ZIdentity Admin Portal. To learn more, see [About Users](/zidentity/about-users).
Adding a Custom Role
To add a custom role:
- Go to **Administration **>** Authentication & Authorization > Access Roles**.
-
On the **Access Roles** page, click **Add Role**.
[See image.](#addrole)
The **Add Role** window appears.
-
In the **Add Role** window:
-
**Role Name**: Enter a unique name for the custom role.
The role name can include letters, numbers, or special characters (hyphen (-) or underscore (_)).
-
**Permissions: **Assign any of the following permissions:
- **Access**: Select the checkbox for tasks that users can perform in each module or global module.
- **View Only**: Select to provide view only access to specific modules or global modules.
- **None**: Select to restrict users from accessing or viewing specific modules or global modules.
For the Scan Settings module, you need to assign **Access** or **View Only** permissions for Cloud Accounts and permissions to start or stop the scan, or edit the scan settings. [See image.](#scan-settings-cloudaccounts)
[See image.](#save)
-
Click **Save**.
The custom role is created and displayed on the [Access Roles ](/dspm/about-roles)page. You can also go to the ZIdentity Admin Portal to view the custom role created to assign users.
[]![The Add Role window with Role Name field and permissions list](/downloads/dspm/administration/users-groups-roles/adding-custom-role/dspm-add-role-window_0.png)
[]![The Access Roles page with the list of predefined and custom roles and annotation around Add Role.](/downloads/dspm/administration/users-groups-roles/adding-custom-role/dspm-access-roles-add-role.png)
[]![The Permissions section with the list of global modules.](/downloads/dspm/administration/role-management/adding-custom-role/dspm-cloudaccounts-scan-settings.png)