# About Users & Roles
Source: https://help.zscaler.com/deception/about-users-roles
PDF: https://help.zscaler.com/pdf/com/en/1531598.pdf

You can provision users and assign predefined roles to them. Each predefined role has specific permissions that allow users to access and manage various modules in the Zscaler Deception Admin Portal.
Provisioning users and assigning roles provide the following benefits and enable you to:
- Add and manage user accounts.
- Manage and control users' access to the Deception Admin Portal by assigning specific roles and privileges based on their responsibilities within the organization.
- Leverage predefined roles and create custom roles with granular permissions to restrict user access to specific resources in the Deception Admin Portal.
- Manage user permissions easily by using repeatable role assignments.
- Leverage user-role and role-privileges relationships to audit user privileges and implement changes quickly.
Predefined Roles
The following predefined roles are available:
| **Role** | **Description** |
| -------- | --------------- |
| Super admin | This role has the highest level of privilege and has complete control over users, roles, APIs, modules, audit logs, etc. |
| Administrator | Configure Decoy Connector and decoys, analyze events, and orchestrate actions. |
| Analyst | Investigate events, block or add an attacker to an allowlist, and export logs. |
| Responder | Analyze events and orchestrate actions. |
In addition to the predefined roles, you can also create custom roles. You must have super admin privileges to add custom roles.
If you cannot add custom roles, then your organization has a standard subscription. Contact Zscaler Support to upgrade your subscription.
About the Users & Roles Page
On the Users & Roles page (Settings > Users & Roles), you can see the following tabs:
- [Users](#deception-user-role-about-user)
- [Roles](#deception-user-role-about-role)
- [IdP Providers](#deception-sso-tab-user-roles)
- [Zscaler Remote Assistance](#deception-view-support-user-details)
- [Settings](#deception-view-user-roles-settings-tab)
![View tabs on the Users & Roles page](/downloads/deception/administration/about-users-roles/deception-view-users-and-roles-page-tabs-2.png)
[]On the Users page (Settings > Users & Roles > Users), you can do the following:
- [View a list of configured users.](#deception-view-user-details)
- [Add a user.](#deception-add-new-user-admin-portal)
- [Export user configuration details.](#deception-export-user-details-csv)
- [Enable email alert notifications for a user.](#deception-enable-email-notifications-events)
- [View user account activity information.](#deception-view-user-activity-info)
- [Edit and delete a user.](#deception-edit-delete-user-account)
[]For each user, you can view:
- **Name**: The name of the user.
- **Login ID**: The email login ID of the user.
- **Contact Info**: The email ID of the user.
- **Roles**: The role assigned to the user.
- **Last Login**: The last time (in days or months) that the user logged in.
[See image.](#deception-view-user-details-image)
[]You can add a new user account to the Deception Admin Portal. Users can access and manage different modules in the Deception Admin Portal based on the roles assigned to them.
To add a new user:
- Go to **Settings** > **Users & Roles** > **Users**.
-
Click **Add User**.
[See image.](#add-user-option)
-
In the **User Details** window:
- **Login ID**: Enter the login ID of the user. It must be an email ID.
- **Email**: Enter the email of the user. Emails to the user are sent to this address.
- **Name**: Enter the name of the user. The name appears when the user logs in to the Deception Admin Portal.
-
**Disable Password Login**: Select to disable the login process using a locally set password, but allow users to sign in via one of the single sign-on (SSO) options.
If this option is not selected, the [Reset 2FA](/deception/resetting-two-factor-authentication) and [Change Password](/deception/changing-password) options will not be available on the [Account Settings](/deception/about-account-settings) page.
- **Blocked**: Enable to block an existing user from accessing the Deception Admin Portal.
- **Roles**: Select one or more predefined user roles from the drop-down menu. The role defines the level of access the user has to the Deception Admin Portal. If you assign more than one role to a user, then the user has permissions for all the configured roles.
- **Notify Only**: Enable if you want the user to receive only email notifications and not access the Deception Admin Portal.
- **Time Zone**: Select a time zone from the drop-down menu. Alert timestamps are displayed according to the selected time zone.
- **Session Inactivity Timeout**: Select a time duration after which an inactive user session is logged out. By default, this is set to 30 minutes.
[See image.](#add-user-details)
-
Click **Save**.
The user is added and an email is sent to the user to configure the password.
[See image.](#new-user-added)
For ZIdentity-Enabled Customers
If ZIdentity is enabled, you can't add users in the Deception Admin Portal. You have to create users in the ZIdentity Admin Portal.
To configure users:
- Go to **Settings** > **Users & Roles** > **Users**.
-
Click **Add Users**.
[See image.](#deception-zidentity-config-user)
You are redirected to the ZIdentity Admin Portal.
- Go to **Directory > Users **and add users and then assign the user to the Deception service. To learn more, see [Adding Users](/zidentity/adding-users) and [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups).
[]You can export the user configuration details as a CSV file.
To export the user configuration details:
- Go to **Settings** > **User & Roles** > **Users**.
-
Click **Export users (CSV)**.
[See image.](#deception-export-user-details-csv-image)
A CSV file with the user configuration details is downloaded to your system.
[]You can enable email alert notifications to generate emails when a warning or critical event occurs in the Deception Admin Portal. Email alert notifications help you to track specific activities, view event details, and take necessary actions.
Only super admins can enable email alert notifications. All users configured in the Deception Admin Portal can disable email alert notifications for their account, but they must have super admin privileges to enable notifications.
To enable email alert notifications for a user:
- Go to **Settings** > **User & Roles** > **Users**.
-
Locate the user you want, and click the **Envelope** icon.
[See image.](#envelope-icon)
- In the **Email Notifications Preferences** window:
- **Enable Notifications**: Select to enable notifications.
- Under **Fine-Tune Notifications**:
- **License**: Enable to generate email alert notifications when the license is about to expire.
- **Security Alerts**: Enable to generate alerts when user settings are changed (e.g., when a password is disabled globally).
- **System Health**: Enable to generate alert email notifications when a component in the Deception Admin Portal (e.g., Decoy Connector) is down or when there are network connectivity issues.
-
**Zero Trust**: Enable to generate email alert notifications whenever there is an IP address or FQDN conflict between the Zero Trust Network decoys and any of the existing systems in the ZPA service. To learn more, see [Creating Zero Trust Network Decoys](/deception/creating-zero-trust-networks-decoy).
This notification is applicable if Zscaler Deception is configured in a SaaS environment.
[See image.](#email-notification)
- Click **Save**.
[]You can view activity information such as the number of failed login attempts, user creation time, user last login time, and user last password reset time.
[See image.](#deception-view-user-activity-info-image)
[]You can edit or delete a user in the Deception Admin Portal.
Editing a User
To edit a user:
- Go to **Settings** > **Users & Roles** > **Users**.
-
Locate the user that you want to modify, and click the **Edit** icon.
[See image.](#deception-edit-icon-users)
-
In the **User Details** window, modify the required fields.
[See image.](#deception-modify-user-details)
If ZIdentity is enabled, you can't edit the user details in the Deception Admin Portal. You can edit only the time zone and session inactive timeout. You must manage a user from the ZIdentity Admin Portal. To learn more, see [About Attributes](/zidentity/about-attributes).
[See image.](#deception-zidentity-edit-user)
- Click **Save**.
Deleting a User
To delete a user:
- Go to **Settings** > **Users & Roles** > **Users**.
-
Locate the user that you want to delete, and click the **Delete** icon.
[See image.](#deception-delete-icon-users)
-
In the confirmation window, click **OK**.
A confirmation message appears to indicate that the user is deleted from the Deception Admin Portal.
[]On the Roles page (Settings > Users & Roles > Roles), you can do the following:
- [View a list of predefined and custom roles.](#deception-view-role-predefined-custom-details)
- [Add a custom role.](#deception-user-role-add-role)
- [Edit or delete a role.](#deception-edit-delete-custom-role)
[]For each role, you can view:
- **Name**: The name of the role.
- **Description**: The description of the role.
- **Users**: The number of users who are assigned the role.
-
**Permissions**: The number of permissions or privileges the role has.
[See image](#deception-view-roles-predefined-custom-image)
[]In addition to predefined roles, you can add a custom role and configure permissions per your requirements. Based on the permissions configured for the role, users can access and manage modules in the Deception Admin Portal.
Not all Zscaler Deception subscription plans have privileges to create custom roles. You must have super admin privileges to add a custom role. Multiple roles can be assigned to a single user.
- Go to **Settings** > **Users & Roles** > **Roles**.
-
Click **Add Role**.
[See image.](#add-roles-option)
If you get an error message after clicking **Add Role** that says custom roles are not available for your plan, then your organization has a standard subscription and you cannot add custom roles. Contact Zscaler Support to upgrade your subscription.
- In the **Role Details** window:
- **Name**: Enter the name of the role.
- **Description**: Enter a description of the role. The description can include information about the privileges the role has, the purpose for creating the role, etc.
-
**Permissions**: Select the read or write permissions that you want to assign to this role from the drop-down menu.
The **Read:ListUsers** and **Read:Appliances** permissions are mandatory to access modules in the Deception Admin Portal.
-
**Users**: Select the users to whom you want to assign this role.
You can leave this field blank and add the users later.
[See image.](#role-details)
If ZIdentity is enabled, you can only configure a custom role, but can't assign it to any users. You must assign roles in the ZIdentity Admin Portal. To learn more, see [About ZIdentity Admin Roles](/zidentity/about-zidentity-admin-roles).
-
Click **Save**.
The role is added to the **Roles** table.
[See image.](#role-added)
[]You can edit or delete a custom role in the Deception Admin Portal.
You cannot edit or delete the predefined roles.
Editing a Role
To edit a custom role:
- Go to **Settings **> **Users & Roles** > **Roles**.
-
Locate the custom role you want to modify, and click the **Edit** icon.
[See image.](#deception-edit-role)
-
In the **Role Details** window, modify the required fields.
[See image.](#deception-modify-role-details)
- Click **Save**.
Deleting a Role
To delete a custom role:
- Go to **Settings **> **Users & Roles** > **Roles**.
-
Locate the custom role you want to delete, and click the **Delete** icon.
[See image.](#deception-delete-role)
- In the confirmation window, click **OK**.
[]On the IdP Providers page (Settings > Users & Roles > IdP Providers), you can configure identity providers (IdPs) to support single sign-on (SSO) for users in Deception. To learn more, see [About Identity Providers](/deception/about-identity-providers).
[See image.](#deception-sso-tab-image)
[]On the Zscaler Remote Assistance page (Settings > Users & Roles > Zscaler Remote Assistance), you can view the details of Zscaler Support users who can access the Deception Admin Portal.
To view the support users' details, go to **Settings** > **Users & Roles** > **Zscaler Remote Assistance**.
The following support user details appear:
- **Name**: The name of the user.
- **Login ID**: The email login ID of the user.
- **Role**: The role (Read-only or Admin) assigned to the user.
- **Created At**: The number of days since the user account was provisioned.
- **Last Login**: The last time (in days or months) that the user logged in.
[See image.](#deception-support-users-tab)
[]On the Settings page (Settings > Users & Roles > Settings), you can configure user authentication settings and disable support users from accessing the Deception Admin Portal. To learn more, see [Configuring User Authentication Settings](/deception/configuring-user-authentication-settings) and [Disabling Support User Access](/deception/disabling-support-user-access).
[See image.](#deception-user-role-settings-tab-image)
[]![View user details](/downloads/deception/administration/about-users-roles/deception-user-view-details-2.png)
[]![Export user details](/downloads/deception/administration/about-users-roles/deception-export-user-details-csv-2.png)
[]![Configure email alert for a user](/downloads/deception/administration/about-users-roles/zscaler-deception-config-email-alert-user-4.png)
[]![Select email alert notification preferences](/downloads/deception/administration/configuring-email-alert-notifications-user/zscaler-deception-configure-email-notify-pref.png)
[]![Add a new user](/downloads/deception/administration/about-users-roles/zscaler-deception-add-new-user-option-2.png)
[]![Configure a new user](/downloads/deception/administration/adding-user/zscaler-deception-configure-new-user-details-4.png)
[]![View the new user ](/downloads/deception/administration/about-users-roles/zscaler-deception-new-user-added-5.png)
[]![Add user if ZIdentity is enabled](/downloads/deception/administration/about-users-roles/zscaler-deception-about-user-zidentity-enabled-2.png)
[]![View user activity](/downloads/deception/administration/about-users-roles/deception-view-user-activity-info-2.png)
[]![Edit user details](/downloads/deception/administration/about-users-roles/zscaler-deception-edit-user-acc-4.png)
[]![Modify user details](/downloads/deception/administration/editing-or-deleting-user/zscaler-deception-edit-user-acc-details-1.png)
[]![Edit user details if ZIdentity is enabled](/downloads/deception/administration/editing-or-deleting-user/zscaler-deception-zidentity-edit-delete-user-1.png)
[]![Delete a user](/downloads/deception/administration/about-users-roles/zscaler-deception-delete-user-acc-5.png)
[]![View predefined and custom roles](/downloads/deception/administration/about-users-roles/deception-roles-view-details-2.png)
[]![Add a new role](/downloads/deception/administration/about-users-roles/zscaler-deception-add-role-option-3.png)
[]![Configure role details](/downloads/deception/administration-and-authentication/adding-role/zscaler-deception-role-details.png)
[]![New role added](/downloads/deception/administration/about-users-roles/zscaler-deception-role-added-2.png)
[]![Edit a role](/downloads/deception/administration/about-users-roles/zscaler-deception-edit-custom-role-1.png)
[]![Modify role details](/downloads/deception/administration/editing-or-deleting-role/zscaler-deception-modify-custom-role.png)
[]![Delete a role](/downloads/deception/administration/about-users-roles/zscaler-deception-delete-custom-role-2.png)
[]![View IdP details](/downloads/deception/administration/about-users-roles/deception-idp-tabs-1.png)
[]![View support user details](/downloads/deception/administration/about-users-roles/zscaler-deception-support-users-page-1.png)
[]![View Authentication Settings details](/downloads/deception/administration/about-users-roles/zscaler-deception-support-users-page-3.png)