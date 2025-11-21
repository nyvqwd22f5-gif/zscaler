# Adding Executive Insights App Admins
Source: https://help.zscaler.com/zia/adding-executive-insights-app-admins
PDF: https://help.zscaler.com/pdf/com/en/1401191.pdf

[Watch a video about Executive Insights App Administrators.](https://fast.wistia.net/embed/iframe/ec953gtt44)
The Executive Insights App admin has access to the Executive Insights App, but not the ZIA Admin Portal. If you want to give an admin access to the Executive Insights App along with other permissions and functional scopes in the ZIA Admin Portal, you can create an [admin role](/zia/adding-admin-roles) with **Enable Permissions for Executive Insights App** selected, and then assign the new role to the admin.
To add an Executive Insights App admin:
- Go to **Administration **> **Administrator Management**.
- Click **Add Executive Insights App Administrator**.
The **Add Executive Insights App Administrator** window appears.
- In the **Add Executive Insights App Administrator** window:
- **Login ID**: Enter the admin's login ID. The Zscaler service uses this ID to identify the admin's activity. The domain names you provided to Zscaler appear in the drop-down menu.
- **Email**: Enter the admin's valid business email address. This email address will receive the Executive Insights App download email after the admin account is added, and is also required to initiate the authentication on the Executive Insights App.
When you update an admin's email address, all the devices that are registered with the old email address get unauthorized. Ensure to reauthorize the devices by registering with the new email address.
- **Name**: Enter a name for the admin.
- **Role**: The admin uses the default Executive Insights App role. It has **Enable Permissions for Executive Insights App** selected, which gives the admin the permissions and scope required to access the Executive Insights App. You can't modify this field, but you can edit the role. To learn more, see [Editing the Default Executive Insights App Role](/zia/editing-default-executive-insights-app-role).
- **Status**: Enable or disable the admin. If you disable the admin, the password is automatically cleared. So, when you re-enable the status of the disabled admin, you must set a new password. If SAML is enabled, then setting a password is optional. You can save your changes only after the admin authentication is complete.
- **Scope**: The admin requires an **Organization** scope to access the Executive Insights App. You can't modify this field.
- **Executive Insights App Access**: Allows the admin access to the Executive Insights App. You can't modify this field.
- **Authorized Mobile Devices**: Displays the admin’s devices that are authorized to use the Executive Insights App. Admins can register up to 8 devices. You can click the **Unauthorize** icon to remove and unauthorize the device. Only one device can be unauthorized at a time.
[See image.](#seeimage1)
For each device, you can see its name, ID, and registration date. This field is only visible if you're editing an admin with **Executive Insights App Access** enabled.
Zscaler recommends you to log out of the Executive Insights App before uninstalling it from a registered device.
- **Comments**: (Optional) Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **Security Updates**:** **Enable if you want the admin to receive the latest information on vulnerabilities and threats that may affect your organization.
- **Service Updates**:** **Enable if you want the admin to receive new Zscaler service and product enhancements, including new data center notification and cloud release information.
- **Product Updates**:** **Enable if you want the admin to receive communication regarding important changes and updates for the Zscaler service.
[See image.](#seeimage2)
- Click **Save**.
The **Confirm Sending the Executive Insights App Download Email** window appears.
- In the **Confirm Sending the Executive Insights App Download Email **window, click **Send** to send the admin an email with download instructions for the Executive Insights App.
- [Activate the change](/zia/saving-and-activating-changes-admin-portal).
You can [edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) or [delete](/zia/deleting-admins) admins at any time.
[]![Screenshot of the Unauthorize icon under Authorized Mobile Devices](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-executive-insights-app-admin/ZIA-Authorized-Mobile-Devices-Unauthorize-Icon.png)
[]![All fields in the Add Executive Insights App Administrator window.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-executive-insights-app-admins/ZIA-Add-Executive-Insights-App-Administrator.png)