# Adding ZIdentity Admin Roles
Source: https://help.zscaler.com/zidentity/adding-zidentity-admin-roles
PDF: https://help.zscaler.com/pdf/com/en/1499261.pdf

This article describes how to assign roles and permissions to admins who manage the ZIdentity Admin Portal. These admins can manage users and entitlements on the assigned Zscaler services.
Prerequisites
You need to first [add users](/zidentity/adding-users) and [user groups](/zidentity/adding-user-groups) and then assign them with admin roles.
Assigning Admin Roles
To assign admin roles:
- Go to **Administration **>** Entitlements **> **ZIdentity Roles**.
- Click **Add Role**.
-
In the **Add Role** window:
- **Name**: Enter a name** **for the admin role.
- **Description (optional)**: Enter a description for the role.
- Select one of the following access levels for each of the modules in the ZIdentity Admin Portal:
- **Full**: Allows admins full access to the module.
- **View Only**: Allows admins to only view the details.
- **Restricted View**: Allows admins to view specific details in the module.
- **None**: Admins don't have access to the module.
- You can set the access levels for the following modules in the ZIdentity Admin Portal:
- [Admin Sign-On Policy](#sign-on-policy)
- [Authentication Methods](#password-policy)
- [Users & Groups](#users-groups)
- [User Credentials](#user-credentials)
- [External Identities](#external-identities)
- [IP Locations & Groups](#ip-locations)
- [Linked Services](#linked-tenants)
- [Authentication Session](#authentication-session)
- [Administrative Entitlements](#admin-entitlements)
- [Service Entitlements](#service-entitlements)
- [Audit Logs](#audit-logs)
- [Roles](#roles)
- [Guest Domains](#guestdomain)
- [Remote Assistance](#remoteassist)
- [Branding](#branding)
- [API Clients & Resources](#API-Clients-and-resources)
- [Executive Insights](#CXO-Insights)
- [Token Validator](#token-validator)
[See image.](#seeimage)
-
Click **Save**.
The role is successfully added and displayed on the Roles page.
[]![Add Role page with the list of roles and permissions in ZIdentity. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/adding-zidentity-admin-roles-doc-57090/Add-role.png)
[]Set the access level to **Policy **> **Admin Sign**-**On.**
**Condition**: The role must also have Full or View Only access to [IP Locations](/zidentity/about-ip-locations) to manage or view Sign-On Policy.
[]Set the access level to:
- **Policy **> **Password**
- **Administration** > **Authentication **> **Authentication Methods**.
[]Set the access level to
- **Directory **> **Users**
- **Directory **> **User Groups**
- **Directory **> **Attributes**
**Condition**: This permission doesn't allow access to **Directory **> **Users **>** Edit User **> **Security Settings**. [The role](/zidentity/admin-roles-and-permissions) must have Full or View Only access to User Credentials to manage or view the Security Settings of users.
For ZIdentity tenants who have migrated to Experience Center, you must have at least the View Only permission for the Users and User Groups modules to submit a Zscaler Support ticket from within Experience Center.
[]Set the access level to **Directory **> **Users **>** Edit User **> **Security Settings**.
**Condition**: The role must have Full or View Only access to [Users](/zidentity/about-users) and [Groups](/zidentity/about-user-groups) to manage or view the Security Settings of users.
[]Set the access level to **Integration **> **External Identities**.
**Condition**: The Restricted View access allows View-Only access to External Identities but doesn't allow the role to view or access the **Bear Token** field (**Integration **> **External Identities **>** Edit Primary **or** Secondary Identity Provider **>** Provisioning**).
[]Set the access level to **Administration** > **Environment **> **IP Locations **and **Administration** > **Environment > IP Location Groups**.
[]Set the access level to **Administration** > **System **> **Linked Services**.
[]Set the access level to the Authentication Session section in **Administration **> **Authentication **> **Authentication Session**.
[]Set the access level to **Administration** > **Entitlements **> **Administrative**.
**Conditions**:
- The admins that are assigned this role can access the configuration on the [Administrative Entitlements: Administrative](/zidentity/about-administrative-entitlements) page only for the services to which they are assigned as service admins, where their role includes the following permission set to Full:
- [Administration > Administration Controls](/zia/adding-admin-roles#administrators-access) in the ZIA Admin Portal.
- [Configuration & Control > Administration Control > Administrators](/zpa/configuring-administrator-roles#Administration) in the ZPA Admin Portal.
- [Administrator Management](/zdx/adding-zdx-roles#AdministratorManagement) in the ZDX Admin Portal.
- [Administrator Management](/client-connector/adding-roles) in the Zscaler Client Connector Portal.
- [Administrator Management](/cloud-branch-connector/adding-admin-roles#administrator-management) in the Zscaler Cloud & Branch Connector Admin Portal.
For example, you [assign a ZIdentity user as service admin](/zidentity/assigning-entitlements-users-and-user-groups#admin-entitlements) for the ZIA and ZPA services with roles that include [full administrative control](/zia/adding-admin-roles#administrators-access) for the ZIA Admin Portal and [Read Only administrative control](/zpa/configuring-administrator-roles#Administration) for the ZPA Admin Portal. When you assign this service admin as an admin for the ZIdentity Admin Portal, the admin only sees the ZIA service listed on the [About Administrative Entitlements](/zidentity/about-administrative-entitlements) page and not the ZPA service, because the admin doesn't have full access to administrative controls in ZPA Admin Portal.
- Admins with **Full** access to users and groups can do the following on the [Administrative Entitlements](/zidentity/about-administrative-entitlements)** **page:
- View the users and user groups details.
- View all users and user group assignments.
- Assign users and user groups.
- Remove users and user group assignments.
- Admins with **View Only** access to users and groups can do the following on the [Administrative Entitlements](/zidentity/about-administrative-entitlements)** **page:
- View all users and user group assignments.
- Admins with **Restricted Full **access can:
- Access, view, and search administrative entitlements.
- View users and user groups of individual tenants if they have “Users and Groups - Full” or “Users and Groups - View” permission.
- View all users and user groups assignments
- Assign users, remove user assignments, assign user groups, and remove user group assignments if they have permission on individual tenants to manage administrators.
[]Set the access level to **Administration** > **Entitlements > Service**.
**Conditions**:
- Admins with **Full** access to users and groups can do the following on the [Service Entitlements](/zidentity/about-service-entitlements) page:
- View users and user groups and assignments.
- Assign users and user groups.
- Remove users and user group assignments.
- Admins with **View Only** access to users and groups can do the following on the [Service Entitlements](/zidentity/about-service-entitlements) page:
- View the subscribed services.
- View all users and user group assignments.
[]Set the access level to **Administration** > **System **> **Audit Logs**.
[]Set the access level to **Administration** > **Entitlements **> **ZIdentity Roles**.
**Condition**: To edit or delete admin roles that are currently assigned to admins, you must have Full access to [Administrative Entitlements](/zidentity/adding-zslogin-admin-roles#admin-entitlements) and Full or View Only access to [Users & Groups](#users-groups).
When configuring a ZIdentity role, an admin can only set the permission level equal to or less than their role scope. For example, if admin access is set to Full for Roles and View Only for IP Locations for a role, the admin assigned to that role can only add new roles with IP Locations to either View or None, but not as Full. This ensures that admins with lower scope and permission can't configure an admin with a higher scope and permission.
[]Set the access level to **Full**, **View Only**, or **None**.
[]Set the access level to **Full** or **None**.
[]Set the access level to **Administration **> **Environment **> **Branding**.
[]Set the access level to **Integration **> **API Clients** and **Integration **> **API Resources**.
[]Set the access level to **Administration **> **Executive Insights**.
The Executive Insights role is assigned to the leadership team (chief executive officer (CEO), chief operating officer (COO), chief financial officer (CFO), etc.) in your organization, allowing them to access the [Executive Insights app](/zia/accessing-and-using-executive-insights-app).
[]Set the access level to **Integration **> **Token Validators**.