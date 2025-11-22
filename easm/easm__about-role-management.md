# About Role Management
Source: https://help.zscaler.com/easm/about-role-management
PDF: https://help.zscaler.com/pdf/com/en/1503616.pdf

EASM supports role-based access control (RBAC), allowing you to assign specific permissions and privileges to users for managing [EASM organizations](/easm/creating-managing-organizations) according to their roles. You can create tailored administrator roles with the necessary access permissions for specific EASM organizations and assign these roles to designated users.
Role Management provides the following benefits and enables you to:
- Enhance security with RBAC by granting users access only to the specific data and features needed for their roles, minimizing the risk of unauthorized access and ensuring compliance with security policies.
- Simplify and streamline user permission management by enabling administrators to quickly create, assign, and customize roles, ensuring that access levels are consistently aligned with organizational requirements.
While role management is supported in the EASM Admin Portal, role assignment to users takes place in Zscaler's centralized identity management platform, ZIdentity. To learn more, see [Managing Entitlements](/zidentity/managing-entitlements) and [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups#admin-entitlements).
About the Role Management Page
On the Role Management page (Administration > Role Management), you can do the following:
- [Add an administrator role.](/easm/creating-managing-roles)
- View the list of administrator roles configured. For each role, you can view the following information:
- **Name**: The name of the administrator role.
- **Permissions**: The permissions to the EASM Admin Portal (Full Access or View Only) configured for the role.
- **Organizations**: The list of custom EASM organizations that are within the scope of the role.
- **Description**: Additional information about the role.
-
[Edit or delete configured administrator roles.](/easm/creating-managing-roles)
If you have view-only permission to the organization, a **View** icon appears instead.
- Search for an administrator role.
![Role management page in EASM](/downloads/easm/administration/about-role-management/about-role-management_0.png)