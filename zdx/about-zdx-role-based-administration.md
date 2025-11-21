# About ZDX Role-Based Administration
Source: https://help.zscaler.com/zdx/about-zdx-role-based-administration
PDF: https://help.zscaler.com/pdf/com/en/1358781.pdf

[Watch a video about roles in ZDX](https://fast.wistia.net/embed/iframe/aouq1i024g)
With role-based administration, organizations can easily add admins and assign them multiple or specific roles with different levels of access. It is possible to add admins in ZDX who are also admins in Zscaler Internet Access (ZIA).
ZDX Role-Based Administration provides the following benefits and enables you to:
- Facilitate, organize, and manage administration roles for specified responsibilities and permissions.
- Assign admins to multiple or specific roles with varying levels of access.
- Provide obfuscation permissions to limit functionalities as required.
Admin roles must be assigned from within each portal. Also, your ZIA Admin Portal credentials can’t be used to log in to the ZDX Admin Portal. For example, a ZIA admin can't log in to the ZDX Admin Portal if their organization is not using that service.
Attributes configured in ZDX (excluding Login ID) are overwritten across all admin profiles. If you create an admin profile for ZDX using the same credentials used in a ZIA admin profile, all attributes except Login ID created in ZDX overwrite the attributes in ZIA. To learn more, see [Adding ZDX Admins](/zdx/adding-zdx-admins) and [Adding ZIA Admins](/zia/adding-zia-admins).
About ZDX Roles
Depending on your permissions in each portal, certain functions are limited. For example, an admin cannot edit their own role. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
For each admin, you can choose from one of the following predefined roles:
- **ZDX Super Admin**: An admin with this role has read, add, edit, delete, and manage permissions in the ZDX Admin Portal. The default admin account uses this role.
- **ZDX Read-Only Admin**: An admin with this role only has read permissions in the ZDX Admin Portal.
- **ZDX Service Desk Tier 1**: An admin with this role has read permissions to the Users Dashboard and access to the User Search portal. To learn more, see the [Understanding the ZDX Service Desk Role](/zdx/about-zdx-service-desk-role).
If you are an admin with ZDX Super Admin level privileges, you can also create a custom ZDX Role for your organization. Zscaler recommends that you add roles before adding admins, because you must select a role for each admin that you create.
About the Role Management Page
On the Role Management page, certain options are not available if you are subscribed to ZIdentity due to read-only permissions. Instead, you can manage and configure the options on the ZIdentity Admin Portal. To learn more, see [Accessing and Navigating the ZIdentity Admin Portal](/zslogin/accessing-and-navigating-zslogin-admin-portal).
On the Role Management page for a ZDX Super Admin (Administration > Role Management), you can do the following:
- [Add a new role](/zdx/adding-zdx-roles).
- Export a CSV file of ZDX roles.
- Search for a role.
- View a list of all admin roles that are configured for your organization. For each role, you can see:
- **Name**: The name of the role.
- **Full Access**: Which Full Access the role has.
- **View-Only Access**: Which view-only access the role has.
- **Visible**: Which information the role can view.
- **Obfuscated**: Which information the role cannot view.
-
**Actions**: Displays which actions you can take for the role.
ZDX roles to which you have Full access are indicated by the **Edit** and **Delete** icon. If you have view-only access, then the ZDX Role shows a **View** icon and you cannot edit or delete them.
- [Edit, delete, or view the ZDX Role details](/zdx/managing-zdx-roles).
![Role Management - Add ZDX Role](/downloads/zdx/administration/admin-configuration/about-zdx-role-based-administration/zdx-rolemanagement-numbers-updated_0.png)