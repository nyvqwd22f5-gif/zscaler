# Adding Risk360 Admin Roles
Source: https://help.zscaler.com/unified/adding-risk360-admin-roles
PDF: https://help.zscaler.com/pdf/com/en/1530704.pdf

Configuring the Risk360 admin role is one of the tasks you must complete when configuring role-based administration.
Prerequisites
When configuring roles:
- You must have the proper permissions to configure a role.
- You must have organizational scope.
Adding Admin Roles
To configure admin roles:
- Go to **Administration **> **Admin Management** > **Role Based Access Control > Risk360**.
- Click **Add Risk360 Role**.
The **Add Risk360 Role** window appears.
- In the **Add Risk360 Role** window:
- **Name**: Enter a name** **for the admin role.
- **Permissions**: Permissions allow you to control an admin's access to the major Risk360 features. For each admin, you must select permissions in the following categories:
- [Dashboard](#dashboard-access)
- [Administrator Management](#administrators-access)
- [User Management](#user-management)
- [Remote Assistance Management](#remote-assist)
[See image.](#add-role-wind-img)
- Click **Save**.
You can edit or delete admin roles at any time.
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
[]In **Remote Assistance Management**, admins can allow Zscaler Support to securely and remotely log in to your Admin Portal.
Choose one of the following permissions:
- **Full**: Allows admins to access the Remote Assistance.
- **View** **Only**: Allows admins to view the Remote Assistance.
- **None**: Doesn’t allow access to the Remote Assistance.
![Add Risk360 Roles Window](/downloads/risk360/authentication-administration/administration-role-management/adding-admin-roles-risk360/Risk360-adding-roles-window_0_0.png)
[]