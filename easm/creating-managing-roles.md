# Creating & Managing Roles
Source: https://help.zscaler.com/easm/creating-managing-roles
PDF: https://help.zscaler.com/pdf/com/en/1503621.pdf

You can create tailored administrator roles with the necessary access permissions for specific organizations and assign these roles to the designated users. The users must be provisioned on Zscaler's centralized identity management platform, ZIdentity.
- Only super admins can create roles and assign permissions to organizations.
- While role management is supported in the EASM Admin Portal, user mapping to roles takes place in the ZIdentity Admin Portal. To learn more, see [Managing Entitlements](/zidentity/managing-entitlements) and [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups).
The following sections explain how you can create and manage administrator roles in the EASM Admin Portal.
[]Creating Roles
To create a new role:
- Go to **Administration** > **Role Management**.
-
Click **Administrator Role**.
The **Add Role** window appears.
- In the **Add Role** window:
- **Name**: Enter a name for the role.
-
**Permissions**: Select whether this role should have full access permissions, view-only permissions, or none to the specific organizations within the role's scope.
Full access permission allows creating and managing discovery profiles within the assigned organizations, whereas view-only permission allows admins to view discovery profiles within the assigned organizations.
- **Organization**: Select the organizations to which this role grants access.
- **Description**: Enter any additional information about the role.
- Click **Save**.
[See image.](#role-configuration)
Managing Roles
You can perform actions such as editing or deleting the administrator roles configured in the EASM Admin Portal.
Editing Roles
To edit a role:
- Go to **Administration** > **Role Management**.
-
Locate the role that you want to edit and click the **Edit** icon.
The **Edit Role** window appears.
- In the **Edit Role** window, make the required changes. To learn more about the individual field configurations in a role, see [Creating Roles](#creating-roles).
- Click **Save**.
Deleting Roles
Roles that are currently assigned to users cannot be deleted.
To delete a role:
- Go to **Administration** > **Role Management**.
- Locate the role that you want to delete and click the **Delete** icon.
- In the confirmation window, click **Yes**.
[]![The Add Role window where users can configure the different fields to create a new admin role in the EASM Admin Portal](/downloads/easm/administration/creating-managing-roles/admin-role-configuration_0.png)