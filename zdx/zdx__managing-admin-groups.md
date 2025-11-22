# Managing Admin Groups
Source: https://help.zscaler.com/zdx/managing-admin-groups
PDF: https://help.zscaler.com/pdf/com/en/1507751.pdf

If you have the Full permission level for Administrator Management and you have SCIM Auto Provisioning enabled on the Administrator Management page, you can manage (add, edit, or delete) Admin Groups. If there is an admin group outside your scope or role, you can view an admin group. You can assign an admin scope or role to an admin group to organize your admins into groups and provide limitations and access to certain features of the ZDX Admin Portal.
An admin group consists of the following:
- Group Selection: A SCIM group based on what you have uploaded to the Administrator Management page. To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins).
- Role: A ZDX role is associated with the admin group to provide limitations and access to the ZDX Admin Portal. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Scope: An admin scope is associated with the admin group to provide limitations and access to granular details of your organization's users. To learn more, see [Understanding the Admin Scope](/zdx/understanding-admin-scope).
On the Admin Groups page (Administration > Administration Controls > Administrator Management > Admin Groups), you can perform the following actions:
- [Add an Admin Group](#ADDAdminGroup)
- [Edit an Admin Group](#EDITAdminGroup)
- [Delete an Admin Group](#DELETEAdminGroup)
- [View an Admin Group](#VIEWAdminGroup)
Depending on your scope and role, you might be unable to configure an admin group and instead only view an admin group.
[]
To add an admin group:
-
Click **Add Admin Group**.
The **Add Admin Group **window appears.
[See image.](#AddAdminGroup)
- In the **Add Admin Group** window:
- **Group Selection**: Select a SCIM group to associate a role and scope to.
- **Role**: Select a [ZDX role](/zdx/adding-zdx-roles) that you have created.
- **Scope**: Select Organization, Department, Application, or Location. Organization is selected by default.
- Click **Save**.
[]
To edit an admin group:
-
Click the **Edit** icon of an admin group.
The **Edit Admin Group **window appears.
[See image.](#EditAdminGroup)
- In the **Edit Admin Group** window:
- **Group Selection**: Select an SCIM group to associate a role and scope with.
- **Role**: Select a [ZDX role](/zdx/adding-zdx-roles) that you have created.
- **Scope**: Select Organization, Department, Application, or Location.
- Click **Save**.
[]
To delete an admin group:
-
Click the **Delete** icon of an admin group.
The **Warning **window appears.
[See image.](#DeleteAdminGroup)
- In the **Warning** window, click **Delete** to confirm the deletion of the selected admin group.
[]
To view an admin group:
-
Click the **View** icon of an admin group.
The **View Admin Group **window appears.
[See image.](#ViewAdminGroup)
- In the **View Admin Group** window, you can view:
- **Group Selection**: The name of the SCIM group.
- **Role**: The ZDX role associated with the admin group.
- **Scope**: The scope associated with the admin group.
- Click **Save**.
[]
![Add Admin Group Window](/downloads/zdx/administration/admin-configuration/managing-admin-groups/ZDX-Admin-Groups-Add.png)
[]
![Edit Admin Group Window](/downloads/zdx/administration/admin-configuration/managing-admin-groups/ZDX-Admin-Groups-Edit.png)
[]
![Delete Confirmation Window](/downloads/zdx/administration/admin-configuration/managing-admin-groups/ZDX-Admin-Groups-Delete.png)
[]
![View Admin Group Window](/downloads/zdx/administration/admin-configuration/managing-admin-groups/ZDX-Admin-Groups-View.png)