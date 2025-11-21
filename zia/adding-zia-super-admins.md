# Adding ZIA Super Admins
Source: https://help.zscaler.com/zia/adding-zia-super-admins
PDF: https://help.zscaler.com/pdf/com/en/1399721.pdf

The super admin [role](/zia/adding-admin-roles) is a default role Zscaler provides. The super admin role has full access to the ZIA Admin Portal and Executive Insights App. This role is assigned to the default admin, but you can assign this role to other admins as necessary. To learn more about admins and roles, see [About Administrators](/zia/about-administrators).
To add a super admin:
- Go to **Administration **> **Administrator Management**.
- Click **Add Administrator**.
The **Add Administrator** window appears.
- In the **Add Administrator** window:
- **Login ID**: Enter the login ID the admin uses to log in from your SSO provider portal, and select the appropriate domain name. The domain names you provided to Zscaler appear in the drop-down menu.
- **Email**: Enter the admin's valid business email address. This email address will receive the Executive Insights App download email after the admin account is added, and it's also required to initiate the authentication on the Executive Insights App.
- **Name**: Enter a name for the admin.
- **Role**: Choose **(0) Super Admin** from the drop-down menu. If you’ve enabled [Admin Rank](/zia/about-admin-rank), your assigned admin rank determines the roles you can select.
[See image.](#img1)
- **Status**: Enable or disable the admin. If you disable the admin, the password is automatically cleared. So, when you re-enable the status of the disabled admin, you must set a new password. If SAML is enabled, then setting a password is optional. You can save your changes only after the admin authentication is complete.
- **Scope**: Choose an [admin scope](/zia/about-admin-scope) to specify which areas of the organization the admin can manage in the ZIA Admin Portal. Your assigned scope determines the scopes you can choose from drop-down menu for this new admin.
- **Organization**: The admin can manage everything in the ZIA Admin Portal.
- **Department**: Choose which departments the admin can manage in the ZIA Admin Portal. You can select a maximum of 2,048 departments.
- **Location**: Choose which locations the admin can manage in the ZIA Admin Portal.
- **Location Group**: Choose which location groups the admin can manage in the ZIA Admin Portal.
ZDX only supports **Organization** and **Location** scopes. So if you have the same admin in ZIA and ZDX, and you change the ZIA admin scope to **Department** or **Location Group**, the [ZDX admin scope](/zdx/adding-zdx-admins) will change to **Organization**.
- **Executive Insights App Access**: Enable to allow an admin access to the Executive Insights App. To enable this setting, the admin requires an **Organization** admin scope and an [admin role](/zia/adding-admin-roles) with **Enable Permissions for Executive Insights App** selected.
- **Authorized Mobile Devices**: Displays the admin’s devices that are authorized to use the Executive Insights App. Admins can register up to 5 devices. You can click the **Unauthorize** icon to remove the device. Only one device can be unauthorized at a time.
[See image.](#seeimage2)
For each device, you can see its name, ID, and registration date. This field is only visible when editing an existing admin with **Executive Insights App Access** enabled.
Consider the following when you're updating an admin's email or role:
- If you're updating an email address, any devices for the admin will be unauthorized and must be registered with the new address.
- If you're updating a role to another one with **Enable Permissions for Executive Insights App** selected, any devices for the admin will be unauthorized.
- If you're updating a role to one without **Enable Permissions for Executive Insights App** selected or update an admin's scope to one other than **Organization**, the admin no longer will have access to the app, and any devices will be unauthorized.
- **Comments**: (Optional) Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **Security Updates**:** **Enable if you want the admin to receive the latest information on vulnerabilities and threats that may affect your organization.
- **Service Updates**:** **Enable if you want the admin to receive new Zscaler service and product enhancements, including new data center notification and cloud release information.
- **Product Updates**:** **Enable if you want the admin to receive communication regarding important changes and updates for the Zscaler service.
- **Password Based Login**: Enable to allow the admin to log in to the ZIA Admin Portal directly using a password. You can use this authentication method with [SAML single sign-on](/zia/configuring-saml-admins).
- **Password**: Enter a password for the admin. It can be 8 to 100 characters and must contain at least one number, one special character, and one uppercase letter.
- **Confirm Password**: Re-enter the password to confirm.
[See image.](#seeimage3)
- Click **Save**.
If **Executive Insights App Access** is enabled, the **Confirm Sending the Executive Insights App Download Email** window appears.
- If the ****Confirm Sending the Executive Insights App Download Email ****window appears, click **Send** to send the admin an email with download instructions for the Executive Insights App. You can [resend](/zia/resending-executive-insights-app-download-instructions) these instructions anytime.
[See image.](#seeimage4)
- [Activate the change](/zia/saving-and-activating-changes-admin-portal).
You can [edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) or [delete](/zia/deleting-admins) admins at any time.
[]![The Add icon to add a new admin role.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-zia-admins/ZIA-Role-Add-Icon.png)
[]![Screenshot of the Unauthorize icon under Authorized Mobile Devices.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-executive-insights-app-admin/ZIA-Authorized-Mobile-Devices-Unauthorize-Icon.png)
[]![A configured admin in the Add Administrator window.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-zia-admins/ZIA-Add-Administrator-Window.png)
[]![The Send button in the Confirm Sending the Executive Insights App Download Email window.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-zia-admins/ZIA-Confirm-Sending-the-Executive-Insights-App-Download-Email.png)