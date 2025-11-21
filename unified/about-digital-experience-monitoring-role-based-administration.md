# About Digital Experience Monitoring Role-Based Administration
Source: https://help.zscaler.com/unified/about-digital-experience-monitoring-role-based-administration
PDF: https://help.zscaler.com/pdf/com/en/1490841.pdf

With role-based administration, organizations can easily add admins and assign them multiple or specific roles with different levels of access. It is possible to add admins in Digital Experience Monitoring who are also Internet & SaaS admins.
Adding admins and assigning them roles is done via the ZIdentity Admin Portal. To learn more, see [Adding Users](/zslogin/adding-users) and [About Administrative Entitlements](/zslogin/about-administrative-entitlements).
Digital Experience Monitoring role-based administration provides the following benefits and enables you to:
- Facilitate, organize, and manage administration roles for specified responsibilities and permissions.
- Assign admins to multiple or specific roles with varying levels of access.
- Provide obfuscation permissions to limit functionalities as required.
Admin roles must be assigned in the context of each service. For example, an Internet & SaaS admin can't access Digital Experience Monitoring features if their organization is not using the Digital Experience Monitoring service.
Attributes configured for Digital Experience Monitoring (excluding Login ID) are overwritten across all admin profiles. If you create an admin profile for Digital Experience Monitoring using the same credentials used in an Internet & SaaS admin profile, all attributes except Login ID created in Digital Experience Monitoring overwrite the attributes in Internet & SaaS.
About Digital Experience Monitoring Admin Roles
Depending on your permissions, certain functions are limited. For example, an admin cannot edit their own role. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
For each admin, you can choose from one of the following predefined roles:
- **ZDX Super Admin**: An admin with this role has read, add, edit, delete, and manage permissions in the Admin Portal. The default admin account uses this role.
- **ZDX Read-Only Admin**: An admin with this role only has read permissions in the Admin Portal.
- **ZDX Service Desk Tier 1**: An admin with this role has read permissions to the Users Dashboard and access to the User Search portal. To learn more, see [Understanding the Service Desk role](/unified/understanding-digital-experience-monitoring-service-desk-role-0).
If you are an admin with Super Admin level privileges, you can also create a custom admin role for your organization. Zscaler recommends that you add roles before admins are added, because you must select a role for each admin that is created.
About the Role Management Page
On the Role Management page (**Administration **> **Admin Management** > **Role-Based Access Control** > **Digital Experience**), certain options are not available due to read-only permissions. Instead, you can manage and configure those options using ZIdentity.
On the Role Management page for a ZDX Super Admin, you can do the following:
- [Add a new role](/unified/adding-digital-experience-monitoring-roles).
- Export a CSV file of admin roles.
- Search for a role.
- View a list of all admin roles that are configured for your organization. For each role, you can see:
- **Name**: The name of the admin role.
- **Full Access**: Which Full Access the admin role has.
- **View-Only Access**: Which View-Only Access the admin role has.
- **Visible**: Which information the admin role can view.
- **Obfuscated**: Which information the admin role cannot view.
- **Functional Scope**: Which scope is assigned to the admin role.
- **Type**: The type of admin role.
- Edit or delete a Configured Admin Role.
![Role Management page](/downloads/unified/administration/digital-experience-monitoring/admin-user-role-management/about-digital-experience-monitoring-role-based-administration/role-management-page-main_1.png)