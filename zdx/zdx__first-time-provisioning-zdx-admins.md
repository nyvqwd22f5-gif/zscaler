# First Time Provisioning for ZDX Admins
Source: https://help.zscaler.com/zdx/first-time-provisioning-zdx-admins
PDF: https://help.zscaler.com/pdf/com/en/1358786.pdf

To onboard ZDX for your organization, first reach out to Zscaler Support. Support will set up a default admin role and send an email requesting the password be reset for that role. After you have reset that password, you can act as the first default admin to log in and begin creating other admins and roles for ZDX.
You will be able to see all functions of the ZDX Admin Portal due to the default admin role. This default admin role is necessary to onboard ZDX for your organization, but it is not recommended for day-to-day use. Zscaler recommends creating your own admin user for yourself. This should be used as your primary user details for better auditing and tracking in ZDX. The default admin user will still exist, but is not recommended for further use.
To complete first time provisioning and establish your own admin user details:
- Go to **Administration** > **Administration Management **to configure other admins and admin roles. To learn more, see [About ZDX Role-Based Administration](/zdx/about-zdx-role-based-administration).
- Click **Add New ZDX Role**. This role is to pair with the default admin created initially. Even though the default admin settings cannot be changed, a role type is still needed to allow the creation of other admins and role types. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
- Edit the new role to have the highest level of permissions:
- **Dashboard**: View Only
- **Configuration**: Full
- **Admin Management**: Full
- **User & Device Names**: Visible
- **Locations**: View Only
- **User Management**: View Only
- **Save** your changes.
- Click **Add New ZDX Admin**. This will be the admin user you will use as your own to manage the admin settings for your organization. To learn more, see [Adding ZDX Admins](/zdx/adding-zdx-admins).
[See image.](#Admin-Mgmt-Page-Click-Add-ZDX-Admin)
- Edit your admin user settings and set your role to the one you just created that has the highest levels of permissions.
- **Save** and [activate your changes](/zdx/saving-and-activating-changes-admin-portal).
Now that you've created your personal admin user, use these credentials to manage role-based administration for ZDX in your organization.
[![ZDX Admin Management page showing the button to Add a ZDX Admin](/downloads/zdx/administration/first-time-provisioning-zdx-admins/ZDX-Preview-ZIA_Administrator-Management_Add-ZDX-Admin_squircle.png)
]