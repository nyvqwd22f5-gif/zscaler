# Configuring Advanced Configuration for Admins
Source: https://help.zscaler.com/zia/configuring-advanced-configuration-admins
PDF: https://help.zscaler.com/pdf/com/en/1402406.pdf

You can configure the action to be taken against the admin account when an admin *user* *account* is deleted using SCIM.
Actions on users through SCIM are reflected in the ZIA Admin Portal. For example, disabling a user through SCIM disables both the admin user and its linked user account in the ZIA Admin Portal. Configuring the action for deleted users only affects deleted users, and does not affect disabled users.
To configure advanced configuration for admins:
- Go to **Administration** > **Administrator Management**.
- Click the **Administrator Management** tab.
- On the **Administrator Management** page, in the **Advanced Configuration** section, choose one of the following options from the **Admin Account** **Action When SCIM Deletes Linked User Account **drop-down menu:
- Select** Delete** if you want to allow SCIM to delete the admin user and its linked user account.
- Select** Do Nothing** if you do not want to allow SCIM to delete the admin user and its linked user account. SCIM will return error 409 (Admin user cannot be deleted). **Do Nothing** is the default.
[See image.](#Configuration_Management_Section)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[![Selecting the Advanced Configuration option on the Administr](/downloads/zia/authentication-administration/administrator-role-management/configuring-advanced-configuration-admins/ZIA-Administrator-Management-Page-Advanced-Configuration-Section.png)
]