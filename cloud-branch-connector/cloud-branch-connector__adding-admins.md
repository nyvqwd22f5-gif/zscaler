# Adding Admins
Source: https://help.zscaler.com/cloud-branch-connector/adding-admins
PDF: https://help.zscaler.com/pdf/com/en/1420596.pdf

Admins can manage users in the Zscaler Cloud & Branch Connector Admin Portal. They can create new admins, reassign roles to existing admins, and more. Zscaler recommends that you add roles before adding admins, because you need to select a role for each admin that you add. Furthermore, when configuring admins:
- You must have permission to do so, as described in [Adding Admin Roles](/cloud-branch-connector/adding-admin-roles).
- Your scope limits the scope that you can assign to other admins.
Adding Admins
If you are subscribed to ZIdentity, some of the following options are only configurable within the ZIdentity Admin Portal. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
To add an admin:
- Go to **Administration **> **Administrator Management **>** Administrators**.
- Click **Add Admin**.
The **Add Admin **window appears.
- In the **Add Admin** window:
- **Login ID**: Enter your Cloud & Branch Connector Admin Portal login ID.
- **Email**: Enter the admin's valid business email address.
- **Name**: Enter a name for the admin.
- **Role**: Select the role from the options available,** Read-Only Admin** or **Super Admin**. You can also search for roles or add a new role by clicking the **Add **icon.
- **Status**: Enable or disable the admin. If you disable the admin, the password is automatically cleared. If you re-enable the status of the disabled admin, you must set a new password.
- **Scope**: Select an admin scope to specify which areas of the organization the admin can manage in the portal. Your assigned scope determines the scopes you can choose from the drop-down menu for this new admin.
- **Organization**: The admin can manage everything in the portal.
- **Location**: Select which locations the admin can manage in the portal.** **If **Allow for Creation of New Locations** is enabled, you can select **None**. When a new location is created, the new location is added to the admin's scope.
- **Allow for Creation of New Locations**: Enable to allow the admin access to create new locations and edit locations they create. To enable this setting, the admin requires a **Location **admin scope.
- **Comments**: (Optional) Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **Password**: Enter a password for the admin. It can be 8 to 100 characters and must contain at least one number, one special character, and one uppercase letter.
- **Confirm Password**: Re-enter the password to confirm.
[See image.](#img1)
- Click **Save **and** **[activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![The Add Cloud Admin window accessed from the Administrator page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/adding-admins-draft-doc-51903/Add%20Admin%20Window.png)