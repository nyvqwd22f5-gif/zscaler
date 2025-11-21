# Adding Admin Roles
Source: https://help.zscaler.com/risk360/adding-admin-roles-risk360
PDF: https://help.zscaler.com/pdf/com/en/1456996.pdf

Configuring the Risk360 admin role is one of the tasks you must complete when configuring role-based administration. To learn more, see Configuring [Role-Based Administration](/risk360/configuring-role-based-administration-risk360).
Prerequisites
When configuring roles:
- You must have the proper permissions to configure a role.
- You must have organizational scope.
Adding Admin Roles
To configure admin roles:
- Go to **Administration **>** Role Management**.
- Click **Add Risk360 Role**.
The **Add Risk360 Role** window appears.
- In the **Add Risk360 Role** window:
- **Name**: Enter a name** **for the admin role.
- **Permissions**: Permissions allow you to control an admin's access to the major features of the Risk360 Admin Portal. For each admin, you must select permissions in the following categories:
- [Dashboard Access](#dashboard-access)
- [Administrator Management](#administrators-access)
- [User Management](#user-management)
- [Remote Assistance Management](#remote-assist)
[See image.](#add-role-wind-img)
- Click **Save **and [activate the change](/risk360/saving-and-activating-changes-risk360-admin-portal).
You can [edit or delete](/risk360/saving-and-activating-changes-risk360-admin-portal) admin roles at any time.
[]In **Dashboard**, admins can view the Risk360 dashboard that enables real-time visibility into your organization's risk measurements and metrics in a range of areas.
Choose one of the following permissions:
- **View** **Only**: Allows admins to view the dashboard.
- **None**: Doesn’t allow access to the dashboard.
[]In **Administration Management**, admins can add other admins, create roles, and view user information.
Choose one of the following permissions:
- **Full**: Allows admins full access and editing privileges for the following pages.
- **Administrator Management**
- **Administrators**: Admins can add, edit, and delete admin accounts.
- **Auditors**: Admins can view the auditors.
- **Administrator Management**: Admins can configure password expiration and SAML single sign-on for admins.
- **Role Management**: Admins can only add, edit, and delete roles that have equal or lesser scope.
- **View Only**: Allows admins to view, but not edit, the following pages.
- Administrator Management
- Role Management
- **None**: Doesn’t allow admins access to **Administration Management**.
[]In **User Management**, admins can view users, groups, and department information.
Choose one of the following permissions:
- **View** **Only**: Allows admins to view the User Management page.
- **None**: Doesn’t allow access to the User Management page.
[]Enable to allow admins access to **Help** > **Remote Assistance**.
Choose one of the following permissions:
- **Full**: Allows admins to access the Remote Assistance.
- **View** **Only**: Allows admins to view the Remote Assistance.
- **None**: Doesn’t allow access to the Remote Assistance.
![Add Risk360 Roles Window](/downloads/risk360/authentication-administration/administration-role-management/adding-admin-roles-risk360/Risk360-adding-roles-window_0_0.png)
[]