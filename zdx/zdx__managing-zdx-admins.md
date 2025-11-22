# Managing ZDX Admins
Source: https://help.zscaler.com/zdx/managing-zdx-admins
PDF: https://help.zscaler.com/pdf/com/en/1479156.pdf

After you have the Full permission level for Administrator Management, you can manage and configure a ZDX Admin by adding, editing, or deleting a ZDX Admin. You can assign a scope to a ZDX Admin to provide limitations and access to certain areas within an organization. To learn more, see [Understanding the Admin Scope](/zdx/understanding-admin-scope).
To manage or configure a ZDX Admin (Administration > Administration Controls > Administrator Management),** **you can perform the following actions:
- [Add a ZDX Admin](#add-zdx-admin)
- [Edit a ZDX Admin](#edit-zdx-admin)
- [Delete a ZDX Admin](#delete-zdx-admin)
- [View a ZDX Admin](#view-zdx-admin)
Admin Caveats
When managing ZDX admins, be aware of the following caveats:
- [Creating a ZDX admin with same credentials in the ZIA Admin Portal](#same-credentials)
- [Changed ZDX admin scope for Department or Location](#department-location-change)
- [Password Expiration](#password-expiration)
[]
If a user switches departments or locations, the user's data is reported for the latest configured department or location.
[]
You can configure password expiration for ZDX admins in the ZDX Admin Portal and ZIA Admin Portal. Based on the settings configured, admins are reminded to change their password and shown the number of days their current password remains valid. If the password expires, admins must provide a new password to access the service.
To learn more, see [Configuring Password Expiration](/zdx/configuring-password-expiration) and [Customizing your Admin Account Settings](/zdx/customizing-your-admin-account-settings).
[]
If you create an admin user in the ZDX Admin Portal with the same credentials used to previously create an admin in the ZIA Admin Portal, the admin credentials for the new user in ZDX override what was created in ZIA, excluding the Login ID.
For example, if you used example@email.com to create an admin in ZIA and then create an admin with the same email in ZDX, the user credentials associated with that email in ZDX take priority and rewrite all credentials for that email in ZIA, excluding the Login ID. So, upon your next login to ZIA, the Login ID remains the same, but the admin's password will have changed.
To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration).
[]
To add a ZDX Admin:
-
Click **Add ZDX Admin**.
The **Add ZDX Admin** window appears.
[See image.](#Add-ZDX-Admin)
- In the **Add ZDX Admin** window:
-
**Login ID**: Enter an ID in the format of `<admin-name>``@``<company-name>``.com`*.*
This field cannot be overwritten, even if the other credentials are also used in the ZIA Admin Portal.
- **Email**: Enter a valid email for the admin.
- **Name**: Enter the name for the admin.
-
**Role**: Select a role from the available options. You can also search for roles or click the **Add **icon to [add a new role](/zdx/adding-zdx-roles). The predefined roles are **ZDX Read-only Admin**, **ZDX Service Desk Tier 1**, and **ZDX Super Admin**. To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration).
[See image.](#ZDXRole)
- **Status**: Select **Enabled **or **Disabled**.
- **Scope**: Select **Organization**, **Department**, **Applications**, or **Location**.
- **Comments**: (Optional) Add any comments about the admin.
-
**Set Password**: Create a password and enter it again to confirm it.
The password must contain at least 10 characters and include 1 number, 1 uppercase character, 1 lowercase character, and 1 special character. The password must not contain whitespace.
[See image.](#Set-Password)
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
You can edit a configured admin in the ZDX Admin Portal. Admins to whom you have access, based on your scope, are indicated by the **Edit **icon.
To edit an administrator:
-
Click the **Edit** icon.
The **Edit ZDX Admin** window appears.
[See image.](#Edit-ZDX-Admin)
- Edit the following fields as necessary:
- **Login ID**: The email address that is used to log in. This field cannot be edited.
- **Email**: The email address used to log in.
- **Name**: The name of the admin.
- **Role**: The role that the admin was assigned. To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration).
- **Status**: Select **Enabled** or **Disabled**.
- **Scope**: Select **Organization**, **Department**, **Applications**, or **Location**.
- **Comments**: Add additional comments as desired.
-
To change the password, enter a **New Password** and enter it again in the **Confirm Password** field.
The password must contain at least 10 characters and include 1 number, 1 uppercase character, 1 lowercase character, and 1 special character. The password must not contain whitespace.
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
You can delete a configured admin in the ZDX Admin Portal. Admins to whom you have access, based on your scope, are indicated by the **Delete **icon.
To delete an administrator:
-
Click the **Delete** icon.
The **Confirm Changes** window appears.
[See image.](#Delete-ZDX-Admin)
-
Click **Yes** to confirm you are deleting the admin. This removes the admin from the ZDX Admin Portal.
Upon deletion, a confirmation window briefly appears on the **Administrators** page.
- [Activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
You can view a configured admin outside your scope and role by clicking the **View** icon. If you have view permission for a configured admin, you cannot manage the configured admin (e.g., delete, edit, create).
[See image.](#View-ZDX-Admin)
[]
[![Add a ZDX Admin by entering the required fields](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/ZDX-AddAdmin.png)
]
[]
[![Role dropdown options displayed in the Add ZDX Admin window](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/ZDX-Search-Role.png)
]
[]
[![Set Password if Enabled](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/zdx-Set-Password.png)
]
[]
[![Editing a ZDX Admin ](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/ZDX-EditAdmin-1.png)
]
[]
![Confirm Deletion](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/ZDX-DeleteZDXAdmin-ConfirmChanges.png)
[]
![View ZDX Admin Window](/downloads/zdx/administration/admin-configuration/managing-zdx-admins/ZDX-ViewAdmin-1.png)