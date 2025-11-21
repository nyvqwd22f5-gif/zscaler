# Adding Admins in Risk360
Source: https://help.zscaler.com/risk360/adding-admins-risk360
PDF: https://help.zscaler.com/pdf/com/en/1457106.pdf

This article describes how to add admins for the Risk360 Admin Portal.
Adding Admins
To add an admin:
- Go to **Administration **> **Administration Management **> **Administrators**.
- Click **Add Risk360 Admin**.
The **Add Administrator** window appears.
- In the **Add Administrator** window:
- **Login ID**: Enter the login ID the admin uses to log in and select the appropriate domain name. The domain names you provide to Zscaler appear in the drop-down menu.
- **Email**: Enter the admin's email address.
- **Name**: Enter a name for the admin.
- **Role**: Choose a role to specify the admin's level of access to the Risk360 Admin Portal. You can also search for roles or click the **Add **icon to add a new role. Select one of the following predefined roles for the admin:
- **RA Read-only Admin**: Provides admin read-only access to the Risk360 Admin Portal.
- **RA Super Admin**: Provides admin full access to the Risk360 Admin Portal.
- **Status**: Enable or disable the admin. If you disable the admin, the password is automatically cleared. So, when you re-enable the status of the disabled admin, you must set a new password. If SAML is enabled, then setting a password is optional. You can save your changes only after the admin authentication is complete.
- **Scope**: Choose the admin scope to specify which areas of the organization the admin can manage in the Risk360 Admin Portal. Currently, only one scope (i.e., **Organization**) is available for admins that provides the ability to manage all areas in the Risk360 Admin Portal.
- **Executive Insights App Access**: Currently, this field is grayed out.
- **Comments**: (Optional) Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **Security Updates**:** **Enable if you want the admin to receive the latest information on risks, vulnerabilities, and threats that might affect your organization.
- **Service Updates**:** **Enable if you want the admin to receive new Zscaler service and product enhancements, including new data center notifications and cloud release information.
- **Product Updates**:** **Enable if you want the admin to receive communication regarding important changes and updates for the Zscaler service.
- **Password**: Enter a password for the admin. It can be 8 to 100 characters and must contain at least one number, one special character, and one uppercase letter.
- **Confirm Password**: Re-enter the password to confirm.
[See image.](#seeimage3)
- Click **Save **and** **[activate the change](/risk360/saving-and-activating-changes-risk360-admin-portal).
The admin is successfully created. You can share the login credentials (Login ID and Password) with the admin.
You can [edit or delete](/risk360/editing-or-deleting-items-risk360) admins at any time.
[]![A configured admin in the Add Administrator window.](/downloads/risk360/authentication-administration/administration-role-management/adding-admins-risk360/Risk360-Adding%20-administrator-window_0.png)