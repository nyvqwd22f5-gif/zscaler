# Adding Users for ZIdentity
Source: https://help.zscaler.com/unified/adding-users-zidentity
PDF: https://help.zscaler.com/pdf/com/en/1505396.pdf

This article describes how to add individual user accounts for ZIdentity. When adding users, a user can belong to up to 1,024 groups. You can use a [CSV file to add multiple users](/unified/importing-user-details-csv-file) at once.
You can also add and manage users via System for Cross-domain Identity Management (SCIM) and single sign-on (SSO) just-in-time (JIT) provisioning. To learn more, see [About External Identity Providers](/unified/about-external-identity-providers).
To add a user:
- Go to **Administration **> **Identity **> **ZIdentity **> **Users**.
-
Click **Add User**.
The **Add User** window appears.
- On the **General **tab:
- **Login ID**:** **Enter a user ID.** **The user ID consists of a username and domain name in email format (e.g., `username@domain.com`). The username must be unique, and its domain must belong to the organization.
- **First Name**: Enter the first name of the user.
- **Last Name**: Enter the last name of the user. The user's full name is created based on what you enter in the **First Name** and **Last Name **fields and is displayed in the **Name **field.
- **Primary Email**: Enter the primary email address of the user.
- **Same As Login ID**: Enable to include the primary email address.
- **Secondary Email**: Enter the secondary email address of the user.
- **Status**: Enable or disable the user.
-
**Department**: [Assign a department](/unified/adding-departments-0) to the user.
Department is a system-defined attribute.
-
**Assign Groups**: Select the [group](/unified/adding-user-groups) to which the user must be added.
[See image.](#zsl-generaltab)
If you would like to provide super admin privileges to users for ZIdentity and all the services linked to ZIdentity, you need to add those users to the `Zscaler Global Administrators` group. To learn more, see [About User Groups](/unified/about-user-groups).
-
On the **Security Settings** tab:
- **Change Password Settings: **Enable to modify the password configurations. This remains disabled until the user is added to ZIdentity. To learn more, see [Configuring Security Settings for Users](/unified/configuring-security-settings-users).
- **Skip Second Factor Authentication:** Select this option if you want the user to skip second-factor authentication.
- **Skip Until**: Select the date and time up to when the user can skip second-factor authentication. Post this duration, the user must configure second-factor authentication.
[See image.](#zsl-securitytab)
-
On the **Additional Attributes **tab, click **Create New Attributes** to [add new user attributes](/unified/adding-user-attributes) or assign the values for user attributes that are already created in the Admin Portal by admins.
[See image.](#zsl-additionalattrib)
-
Click **Save**.
The user details are displayed on the **Users** page.
[See image.](#zsl-entitlements)
[]![A screenshot of Add User drawer in ZIdentity](/downloads/zidentity/administration/users/adding-users/zidentity-add-user-drawer.png)
[]![A screenshot of Add user drawer showing Security Settings ](/downloads/zidentity/administration/users/adding-users/zidentity-security-settings-tab-users.png)
[]![A screenshot of Add User drawer showing options relating to attributes](/downloads/zidentity/administration/users/adding-users/zidentity-additional-attributes-tab-users.png)
[]![A screesnhot of Users page with newly added user highlighted](/downloads/zidentity/administration/users/adding-users/zidentity-user-added.png)