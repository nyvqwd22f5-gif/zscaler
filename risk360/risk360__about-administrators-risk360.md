# About Administrators in Risk360
Source: https://help.zscaler.com/risk360/about-administrators-risk360
PDF: https://help.zscaler.com/pdf/com/en/1457041.pdf

Risk360's [role-based administration](/risk360/configuring-role-based-administration-risk360) enables you to control what different admins can do in the Risk360 Admin Portal. You can delegate responsibilities among admins and granularly control their level of access to the Risk360 Admin Portal to ensure they do not create conflicting settings.
To facilitate role-based administration, each admin account comprises a role and scope:
- Using an [admin role](/risk360/about-role-management-risk360) you can specify which features admins can access in the Risk360 Admin Portal.
- Using an admin scope, you can specify which areas of the organization (e.g., which departments or which locations) admins can configure admins or settings in the Risk360 Admin Portal.
Role-based administration provides the following benefits and enables you to:
- Provide access to the features specific to an admin's role and scope.
- Add admins for the Risk360 Admin Portal.
Zscaler provides a default admin account, full access to the Risk360 Admin Portal, and scope. As a default admin, you can:
- Enable or disable the default admin account status, but you cannot delete the account.
- Add as many additional admins as necessary to meet the specific needs of your organization (only with role-based administration).
- Edit and delete admins as necessary at any time.
If you are subscribed to the ZIdentity service, the admins in the Risk360 Administrators page are listed as read-only. These admins are configured in the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
About the Administrators Page
On the Administrators page (Administration > Administration Management > Administrators), you can do the following:
- [Add an admin](/risk360/adding-admins-risk360).
- Search for a configured admin.
- View a list of all admins for the Risk360 Admin Portal. For each admin, you can see the following information:
- **Login ID**: The Risk360 Admin Portal login ID for the admin.
- **Name**: The name of the admin.
- **Role**: The admin's level of access to the Risk360 Admin Portal.
- **Status**: The status of the admin (Enabled or Disabled).
- **Scope**: The areas of the organization the admin can manage in the Risk360 Admin Portal.
- **Login Type**: Lists if SAML single sign-on (SSO) login, direct password access login, or both are enabled for the admin.
- **Comments**: Displays any comments regarding the admin, if available.
- **Password Expired**: Displays whether the admin's password has expired if [password expiration is enabled](/risk360/configuring-password-expiration-risk360) for admins.
- **Type**: Displays the admin type. Currently, there is only one admin type for the Risk360 Admin Portal.
- [Modify the table and its columns](/risk360/using-tables-risk360).
- View admin configuration details. Applicable only to the default admin account.
- [Edit](/risk360/editing-or-deleting-items-risk360) or [delete](/risk360/deleting-risk360-admins) a configured admin.
- Go to the [Administrator Management](/risk360/understanding-administrator-management-settings-risk360) page.
![Administrator Page](/downloads/risk360/authentication-administration/administration-role-management/understanding-administrator-management-settings-risk360/Risk360-administrator-page_0_0.png)