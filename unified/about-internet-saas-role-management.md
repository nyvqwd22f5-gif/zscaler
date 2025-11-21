# About Internet & SaaS Role Management
Source: https://help.zscaler.com/unified/about-internet-saas-role-management
PDF: https://help.zscaler.com/pdf/com/en/1490816.pdf

The admin roles that are assigned to admins dictate the level of access they have to the Admin Portal. Zscaler provides a default super admin role which has full access to the Admin Portal and Executive Insights App. This role is assigned to the default admin, but you can assign this role to other admins as necessary. For each additional role you create, you must define the role's access by specifying:
- Admin rank
- Permissions
- Functional scope
Admins who have permission to manage roles can only add, edit, or delete roles with less scope and lower [rank](/unified/about-admin-rank). To learn more, see [Adding Admin Roles](/unified/adding-admin-roles) and [Adding SD-WAN Partner API Roles](/unified/adding-partner-admin-roles).
Configuring an admin is one of the tasks you must complete while configuring role-based administration. To learn more, see [Configuring Role-Based Administration](/unified/configuring-role-based-administration).
Role management provides the following benefits and enables you to:
- Configure admins for the Admin Portal based on their role and functional scope in the organization.
- Assign rank-based roles to admins to maintain hierarchy among the admins so that a lower-ranked admin can't modify the settings of an admin with a higher rank.
- View all the configured admins and their access levels, functional scope, rank, and other information.
The API role configured in the external OAuth 2.0 authentication server for a client application dictates the client application's permission and access to the different API categories in the Internet & SaaS API. You add the API role using the Admin Portal and then configure the external OAuth 2.0 authentication server to use that role. This enables the different APIs within the API categories of the Internet & SaaS API to be authenticated through the use of an OAuth 2.0 authentication server instead of the APIs passing an admin user, password, and API key.
Adding an API role is one of the tasks that you must complete before you can configure the external OAuth 2.0 authentication server. To learn more, see [Securing Internet & SaaS APIs with OAuth 2.0](/unified/securing-internet-saas-apis-oauth-2-0).
About the Role Management Page
Certain options on the Role Management page are not available for [ZIdentity](/zidentity/what-zidentity)-enabled tenants (e.g., adding an SD-WAN partner API role and adding an API role). To learn more, see [ZIdentity Administration](/zslogin/administration/).
On the Role Management page (Administration > Admin Management > Role Based Access Control > Internet & SaaS), you can do the following:
- [Add an admin role.](/unified/adding-admin-roles)
- [Add an SD-WAN partner API role.](/unified/adding-partner-admin-roles)
- [Add an API role.](/unified/adding-api-roles)
- Search for a configured admin role, SD-WAN partner API role, or API role.
- View a list of all admin roles, SD-WAN partner API roles, and API roles configured for your organization. For each role, you can view the following information:
- **Name**: The name of the role.
- **Admin Rank**: The assigned [admin rank](/unified/about-admin-rank) for the admin role. This is visible only if admin ranking is enabled in the [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking). Admin rank does not apply to SD-WAN partner API or API roles.
- **Full Access**: The areas of the Admin Portal where admins with this role have full access or, for API roles, the areas in the Internet & SaaS API to which the client application has full access.
- **View-Only Access**: The areas of the Admin Portal where admins with this role have view-only access or, for API roles, the areas in the Internet & SaaS API to which the client application has view-only access.
- **None Access**: The areas of the Admin Portal where admins with this role don't have any access or, for API roles, the areas in the Internet & SaaS API to which the client application doesn't have any access.
- **User Names**: This shows whether the usernames are visible or [obfuscated](/unified/obfuscating-user-names-admins) within the Zscaler service or APIs.
- **Device Information**: This shows whether the device information (i.e., device hostname, device name, and device owner) is visible or obfuscated within the Admin Portal or APIs.
- **Type**: The type of role. The admin role types are **Standard Admin**, **SD-WAN Partner API**, **Executive App Admin**, or **Standard & Executive App Admin**. The API role type is **API Client.**
- [Modify the table and its columns.](/unified/using-tables)
- [Edit the default Executive Insights App role.](/unified/editing-default-executive-insights-app-role)
- View a configured admin role with greater scope and higher rank, or an SD-WAN partner API role.
- Edit a configured admin role with less scope and lower rank, an SD-WAN partner API role, or an API role.
![The Role Management page in the ZIA Admin Portal highlighting the different features for adding admin roles](/downloads/zia/authentication-administration/administrator-role-management/role-management/about-role-management/zia-about-role-managament-main-page.png)