# Adding ZIdentity Admin Roles
Source: https://help.zscaler.com/unified/adding-zidentity-admin-roles
PDF: https://help.zscaler.com/pdf/com/en/1505641.pdf

This article describes how to assign roles and permissions to admins who manage the Admin Portal. These admins can manage users and entitlements on the assigned Zscaler services.
Prerequisites
You need to first [add users](/unified/adding-users-0) and [user groups](/unified/adding-user-groups) and then assign them with admin roles.
To assign admin roles:
- Go to **Administration **>** Admin Management **> **Role Based Access Control** > **Unified User Interface**.
- Click **Add Role**.
-
In the **Add Role** window:
- **Name**: Enter a name** **for the admin role.
- **Description (optional)**: Enter a description for the role.
- Select one of the following access levels for each of the modules in the Admin Portal:
- **Full**: Allows admins full access to the module.
- **View Only**: Allows admins to only view the details.
- **Restricted View**: Allows admins to view specific details in the module.
- **None**: Admins don't have access to the module.
- You can set the access levels for the following modules in the Admin Portal.
- [Admin Sign-On Policy](#sign-on-policy)
- [Authentication Methods](#password-policy)
- [Users & Groups](#users-groups)
- [User Credentials](#user-credentials)
- [External Identities](#external-identities)
- [Trusted IP Locations & Groups](#ip-locations)
- [Linked Services](#linked-tenants)
- [Authentication Session](#authentication-session)
- [Administrative Entitlements](#admin-entitlements)
- [Service Entitlements](#service-entitlements)
- [Audit Logs](#audit-logs)
- [Roles](#roles)
- [Guest Domains](#guestdomain)
- [Branding](#branding)
- [API Clients & Resources](#API-Clients-and-resources)
- [Executive Insights](#CXO-Insights)
- [Token Validator](#token-validator)
[See image.](#seeimage)
-
Click **Save**.
The role is successfully added and displayed on the Roles page.
[]![Add Role page with the list of roles and permissions in ZIdentity. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/adding-zidentity-admin-roles-doc-57090/Add-role.png)
[]Set the access level to **Administration > Admin Management > Administrator Management > Sign-On Policies**.
**Condition**: The role must also have Full or View Only access to [IP Locations](/unified/about-trusted-ip-locations) to manage or view Sign-On Policy.
[]Set the access level to:
- **Administration >** **Identity > ZIdentity > Password Complexity**
- **Administration** > **Identity **> **ZIdentity** > **Authentication Methods**.
[]Set the access level to
- **Administration** > **Identity **> **ZIdentity** > **Users**
- **Administration** > **Identity **> **ZIdentity** > **User Groups**
- **Administration** > **Identity **> **ZIdentity** > **Attributes**
**Condition**: This permission doesn't allow access to **Administration** > **Identity **> **ZIdentity** > **Users **>** Edit User **> **Security Settings**. [The role](/unified/admin-roles-and-permissions) must have Full or View Only access to User Credentials to manage or view the Security Settings of users.
[]Set the access level to **Administration** > **Identity **> **ZIdentity** > **Users **>** Edit User **> **Security Settings**.
**Condition**: The role must have Full or View Only access to [Users](/unified/about-users-0) and [Groups](/unified/about-user-groups) to manage or view the Security Settings of users.
[]Set the access level to **Administration** > **Identity **> **ZIdentity** > **External Identities**.
**Condition**: The Restricted View access allows View-Only access to External Identities but doesn't allow the role to view or access the **Bear Token** field (**Administration** > **Identity **> **ZIdentity** > **External Identities **>** Edit Primary **or** Secondary Identity Provider **>** Provisioning**).
[]Set the access level to **Infrastructure **> **Locations **> **Trusted** **IP** **Locations **and **Infrastructure **> **Locations **> **Trusted** **IP** **Location Groups**.
[]Set the access level to **Administration** > **System **> **Linked Services**.
[]Set the access level to the Authentication Session section in **Administration** > **Identity **> **ZIdentity** > **Authentication Session**.
[]Set the access level to **Administration** > **Entitlements **> **Administrative**.
**Conditions**:
- The admins that are assigned this role can access the configuration on the [Administrative Entitlements: Administrative](/unified/about-administrative-entitlements) page only for the services to which they are assigned as service admins, where their role includes the following permission set to Full:
- [Administration > Admin Management > Role Based Access Control > Unified User Interface](/unified/adding-zidentity-admin-roles) in the Admin Portal.
For example, you [assign a ZIdentity user as service admin](/unified/assigning-entitlements-users#admin-entitlements) for the Internet & SaaS and Private Applications services with roles that include [full administrative control](/unified/adding-admin-roles#administrators-access) for the Internet & SaaS service and [Read Only administrative control](/unified/configuring-administrator-roles#Administration) for the Private Applications service. When you assign this service admin as an admin for the ZIdentity, the admin only sees the Internet & SaaS service listed on the [About Administrative Entitlements](/unified/about-administrative-entitlements) page and not the Private Applications service, because the admin doesn't have full access to administrative controls of Private Applications service.
- Admins with **Full** access to users and groups can do the following on the [Administrative Entitlements](/unified/about-administrative-entitlements)** **page:
- View the users and user groups details.
- View all users and user group assignments.
- Assign users and user groups.
- Remove users and user group assignments.
- Admins with **View Only** access to users and groups can do the following on the [Administrative Entitlements](/unified/about-administrative-entitlements)** **page:
- View all users and user group assignments.
- Admins with **Restricted Full **access can:
- Access, view, and search administrative entitlements.
- View users and user groups of individual tenants if they have “Users and Groups - Full” or “Users and Groups - View” permission.
- View all users and user groups assignments
- Assign users, remove user assignments, assign user groups, and remove user group assignments if they have permission on individual tenants to manage administrators.
[]Set the access level to **Administration** > **Entitlements > Service**.
**Conditions**:
- Admins with **Full** access to users and groups can do the following on the [Service Entitlements](/unified/about-service-entitlements) page:
- View users and user groups and assignments.
- Assign users and user groups.
- Remove users and user group assignments.
- Admins with **View Only** access to users and groups can do the following on the [Service Entitlements](/unified/about-service-entitlements) page:
- View the subscribed services.
- View all users and user group assignments.
[]Set the access level to **Administration** > **System **> **Audit Logs**.
[]Set the access level to **Administration** > **Entitlements **> **ZIdentity Roles**.
**Condition**: To edit or delete admin roles that are currently assigned to admins, you must have Full access to [Administrative Entitlements](/unified/adding-zidentity-admin-roles#admin-entitlements) and Full or View Only access to [Users & Groups](#users-groups).
When configuring a ZIdentity role, an admin can only set the permission level equal to or less than their role scope. For example, if admin access is set to Full for Roles and View Only for IP Locations for a role, the admin assigned to that role can only add new roles with IP Locations to either View or None, but not as Full. This ensures that admins with lower scope and permission can't configure an admin with a higher scope and permission.
[]Set the access level to **Full**, **View Only**, or **None**.
[]Set the access level to **Administration **> **Account Management **> **Branding**.
[]Set the access level to **Administration **>** API Configuration** >** OneAPI **> **API Clients** and **Administration **>** API Configuration** >** OneAPI **> **API Resources**.
[]Set the access level to **Administration **> **Executive Insights**.
The Executive Insights role is assigned to the leadership team (chief executive officer (CEO), chief operating officer (COO), chief financial officer (CFO), etc.) in your organization, allowing them to access the [Executive Insights app](/zia/accessing-and-using-executive-insights-app).
[]Set the access level to **Integration **> **Token Validators**.