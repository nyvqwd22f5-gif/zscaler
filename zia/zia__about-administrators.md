# About Administrators
Source: https://help.zscaler.com/zia/about-administrators
PDF: https://help.zscaler.com/pdf/com/en/1399846.pdf

[Watch a video about Administrators, including how to add new administrators.](https://fast.wistia.net/embed/iframe/gk4kabtv85)
Zscaler’s[ role-based administration](/zia/configuring-role-based-administration) enables you to control what different admins can do in the ZIA Admin Portal. You can delegate responsibilities among admins and granularly control their level of access to the ZIA Admin Portal to ensure they do not create conflicting policies and settings. To learn more about other use cases for role-based administration, see [Role-Based Administration Configuration Examples](/zia/examples-role-based-administration).
To facilitate role-based administration, each admin account comprises a role and scope:
- Using an [admin role](/zia/adding-admin-roles) or [SD-WAN partner API role](/zia/adding-partner-admins), you can specify which features admins can access in the ZIA Admin Portal.
- Using an [admin scope](/zia/about-admin-scope), you can specify which areas of the organization (for example, which departments or which locations) admins can configure policies or settings in the ZIA Admin Portal.
Role-based administration provides the following benefits and enables you to:
- Configure security policies in the ZIA Admin Portal, with help from the CISO (specified through role).
- Configure security policies for the entire organization (specified through scope).
- Configure access policies relevant to productivity and compliance (specified through role), only for a specific location or department (specified through scope).
Zscaler provides a default admin account, full access to the ZIA Admin Portal and scope. As a default admin, you can:
- Enable or disable the default admin account status, but you cannot delete the account.
- Add as many additional admins as necessary to meet the specific needs of your organization (only with role-based administration).
- [Edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) and [delete](/zia/deleting-admins) admins as necessary at any time.
Also, depending on their admin role and scope, configured admins can add, edit, or delete admin accounts with a lower [rank](/zia/about-admin-rank).
Zscaler recommends you log in with the new default admin account (DEFAULT ADMIN) and delete the deprecated default admin (DEFAULT ADMIN (Deprecated)). [See image.](#seeimage)
The new default admin login ID uses the following format:
admin@<Organization ID>.<Zscaler Cloud>.net
As a best practice, the new default admin can't be used to log in to the Zscaler service and browse the internet. Also, password reset is only supported for the new default admin.
Configuring an admin is one of the tasks you must complete when configuring role-based administration. To learn more, see [Configuring Role-based Administration](/zia/configuring-role-based-administration).
About the Administrators Page
On the Administrators page, you can only edit an existing admin's scope if you are subscribed to ZIdentity. The admins are configured in the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
On the Administrators page (Administration > Administrator Management), you can do the following:
- [Add an admin](/zia/adding-admins).
- [Add an SD-WAN partner API client](/zia/adding-partner-admins).
- [Add an Executive Insights App admin](/zia/adding-executive-insights-app-admin).
- Search for a configured admin.
- View a list of all admins configured for your organization. For each admin, you can see the following details:
- **Login ID**: The ZIA Admin Portal login ID for the admin.
- **Name**: The name of the admin.
- **Role**: The admin's level of access to the ZIA Admin Portal.
- **Status**: The status of the admin.
- **Scope**: The areas of the organization the admin can manage in the ZIA Admin Portal.
- **Login Type**: Lists if SAML single sign-on (SSO) login, direct password access login, or both are enabled for the admin.
- **Comments**: Displays any comments regarding the admin, if available.
- **Password Expired**: Displays whether the admin's password has expired if password expiration is enabled for admins.
- **Type**: Displays whether the admin's type of role is a Standard Admin, SD-Wan partner API, Executive App Admin, or Standard & Executive App Admin.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit a default admin or a configured admin](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- Go to the [Auditors page](/zia/about-auditors).
- Go to the [Administrator Management page](/zia/about-administrator-management).
![Screenshot highlighting the DEFAULT ADMIN and DEFAULT ADMIN (Deprecated).   ](/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/ZIA-about-administrator-management-page.png)
[]![Screenshot highlighting the different features on the Administrators page.](/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/ZIA-about-administrators-default-admin.png)