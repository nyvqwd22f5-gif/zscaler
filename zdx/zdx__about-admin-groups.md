# About Admin Groups
Source: https://help.zscaler.com/zdx/about-admin-groups
PDF: https://help.zscaler.com/pdf/com/en/1507736.pdf

Admin groups are created when you enable SCIM Auto Provisioning on the Administrator Management page. When enabled, they are auto-provisioned based on the user's SCIM group. You can then associate the admin group with admin scopes and roles. With Zscaler role-based administration, you can create Admin Groups to meet the needs of your organization. You can create, edit, or delete an admin group to better manage your use of admin groups.
Admin Groups provide the following benefits and enable you to:
- Configure admin groups in the ZDX Admin Portal for specific admin roles (specified by role).
- Configure admin groups for different administrators for the entire organization, location, or department (specified by scope).
Prerequisites
In order to view the Admin Groups page, make sure the following prerequisites are met:
- Have Full or View access to Administrator Management to access the Admin Groups page. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Enable SCIM Auto Provisioning on the Administrator Management page. To learn more, see [Configuring Administrator Management Settings](/zdx/configuring-administrator-management-settings).
About the Admin Groups Page
You can view the different admin groups that have been set up, including their details, on the Admin Group page.
On the Admin Groups page (Administrator > Administrator Management > Administrator > Admin Groups tab), you can do the following:
- [Add an admin group.](/zdx/managing-admin-groups)
- Search for an admin group.
- View a list of admin groups with the following information:
- **Group Name**: The SCIM group name.
- **Scope**: The type of admin scope. To learn more, see [Understanding the Admin Scope](/zdx/understanding-admin-scope).
- **Role**: The type of admin role. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- **Comments**: Any comments to describe the admin group.
- **Actions**: The actions you can use to manage the admin group.
-
[View, edit, or delete an admin group.](/zdx/managing-admin-groups)
Based on the Admin Group and your ZDX admin's scope and role, you can have different actions. For example, if you have a scope based on an HR department, then you can view admin groups outside the HR department. You cannot add, edit, or delete them. You can view them.
- Go to the [Administrator Management](/zdx/configuring-saml-zdx-admins) page or [Admins](/zdx/about-administrators) tab.
![Admin Groups Page](/downloads/zdx/administration/admin-configuration/about-admin-groups/ZDX-Admin-Groups-Outline-1.png)