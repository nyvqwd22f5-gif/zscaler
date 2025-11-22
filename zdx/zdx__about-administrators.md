# About Administrators
Source: https://help.zscaler.com/zdx/about-administrators
PDF: https://help.zscaler.com/pdf/com/en/1374826.pdf

[Watch a video about Administrators in ZDX.](https://fast.wistia.net/embed/iframe/eidy76se80)
Admins in ZDX can manage users, create new admins, and reassign existing admins. With Zscaler role-based administration, you can add as many additional admins as necessary to meet the specific needs of your organization. You can also edit and delete admins as necessary at any time. Also, depending on their admin role and scope, configured admins can add, edit, or delete admin accounts.
Administration provides the following benefits and enables you to:
- Configure administration in the ZDX Admin Portal (specified by role).
- Configure administration responsibilities between different administrators for the entire organization, location, or department (specified by scope).
- Configure administration roles relevant to productivity and compliance (specified by role).
On the Administrators page, the admins are listed as read-only if you are subscribed to ZIdentity. You can configure ZDX admins in the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity) and [About Administrative Entitlements](/zidentity/about-administrative-entitlements).
About the Administrators Page
You can view the different administrators that have been set up, including their details, on the Administrators page.
On the Administrators page (Administration > Administrator Management > Administrators), you can do the following:
- [Add a new ZDX Admin](/zdx/managing-zdx-admins).
- Export a CSV file of ZDX admins.
- Search for an admin. Enter a term in the search bar. To delete content in the search bar, click the **Delete** icon to cancel and reset.
- View a list of admins that are configured for your organization. For each admin, you can view:
- **Login ID**: The email address that is used to log in. You can sort this field by clicking the arrow in the title.
- **Name**: The name of the admin.
- **Role**: The role that the admin was assigned during configuration.
-
**Scope**: This can be **Organization**, **Location**, **Applications**, or **Department**.
If a user switches departments or locations, the user's data is reported as the latest configured department or location.
- **Login Type**: This can be a configured password for the ZDX Admin Portal or SAML.
- **Password Expired**: If the configured password has expired, this field indicates **True**. If the configured password has not expired, this field indicates **False**. To learn more, see [Configuring Password Expiration](/zdx/configuring-password-expiration).
- **Comments**: Any comments that were entered during configuration.
- **Status**: Indicates if the admin is currently **Enabled** or **Disabled**.
- **Actions**: The types of action you can take for the ZDX admin. Depending on your scope and role, you have different actions.
- [View, edit, or delete an admin's settings.](/zdx/managing-zdx-admins)
- Go to the [Administrator Management](/zdx/configuring-administrator-management-settings) page to configure admins, or go to the [Admin Groups](/zdx/about-admin-groups) page to manage admin groups.
![Overview of the Administrators Page in ZDX ](/downloads/zdx/administration/about-administrators/ZDX_AdministratorsPage_3_wadmingroup_outline.png)