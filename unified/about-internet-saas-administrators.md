# About Internet & SaaS Administrators
Source: https://help.zscaler.com/unified/about-internet-saas-administrators
PDF: https://help.zscaler.com/pdf/com/en/1490811.pdf

Zscaler’s[ role-based administration](/unified/configuring-role-based-administration) enables you to control what different admins can do in the Admin Portal. You can delegate responsibilities among admins and granularly control their level of access to the Admin Portal to ensure they do not create conflicting policies and settings.
To facilitate role-based administration, each admin account comprises a role and scope:
- Using an [admin role](/unified/adding-admin-roles) or [SD-WAN partner API role](/unified/adding-partner-admins), you can specify which features admins can access in the Admin Portal.
- Using an [admin scope](/unified/about-admin-scope), you can specify which areas of the organization (for example, which departments or which locations) admins can configure policies or settings in the Admin Portal.
Role-based administration provides the following benefits and enables you to:
- Configure security policies in the Admin Portal, with help from the CISO (specified through role).
- Configure security policies for the entire organization (specified through scope).
- Configure access policies relevant to productivity and compliance (specified through role), only for a specific location or department (specified through scope).
Zscaler provides a default admin account, full access to the Admin Portal and scope. As a default admin, you can:
- Enable or disable the default admin account status, but you cannot delete the account.
- Add as many additional admins as necessary to meet the specific needs of your organization (only with role-based administration).
- Edit and delete admins as necessary at any time.
Also, depending on their admin role and scope, configured admins can add, edit, or delete admin accounts with a lower [rank](/unified/about-admin-rank).
Zscaler recommends you log in with the new default admin account (DEFAULT ADMIN) and delete the deprecated default admin (DEFAULT ADMIN (Deprecated)). [See image.](#seeimage)
The new default admin login ID uses the following format:
admin@<Organization ID>.<Zscaler Cloud>.net
As a best practice, the new default admin can't be used to log in to the Zscaler service and browse the internet. Also, password reset is only supported for the new default admin.
Configuring an admin is one of the tasks you must complete when configuring role-based administration. To learn more, see [Configuring Role-Based Administration](/unified/configuring-role-based-administration).
About the Administrators Page
On the Administrators page, you can only edit an existing admin's scope. The admins are configured in ZIdentity. To learn more, see [ZIdentity Admin, User, & Role Management](/unified/administration/zidentity/admin-user-role-management).
On the Administrators page (Administration > Admin Management > Administrator Management > Internet Access Administrators), you can do the following:
- [Add an SD-WAN partner API client](/unified/adding-partner-admins).
- Search for a configured admin.
- View a list of all admins configured for your organization. For each admin, you can see the following details:
- **Login ID**: The Admin Portal login ID for the admin.
- **Name**: The name of the admin.
- **Role**: The admin's level of access to the Admin Portal.
- **Scope**: The areas of the organization the admin can manage in the Admin Portal.
- **Login Type**: Lists if SAML single sign-on (SSO) login, direct password access login, or both are enabled for the admin.
- **Comments**: Displays any comments regarding the admin, if available.
- **Password Expired**: Displays whether the admin's password has expired if password expiration is enabled for admins.
- **Status**: The status of the admin.
- **Type**: Displays whether the admin's type of role is a Standard Admin, SD-Wan partner API, Executive App Admin, or Standard & Executive App Admin.
- [Modify the table and its columns](/unified/using-tables).
- [Edit a default admin or a configured admin](/unified/editing-internet-saas-admins).
- Go to the [Auditors](/unified/about-auditors) page.
- Go to the [Administrator Management](/unified/understanding-administrator-management-settings) page.
![Administrators page in the Admin Portal](/downloads/unified/administration/internet-saas/admin-user-role-management/administrators/about-administrators/administrators-page.png)
[]![Screenshot highlighting the different features on the Administrators page.](/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/ZIA-about-administrators-default-admin.png)