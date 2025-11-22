# Configuring Security Settings for Users
Source: https://help.zscaler.com/zidentity/configuring-security-settings-users
PDF: https://help.zscaler.com/pdf/com/en/1503381.pdf

This article describes how to configure Security Settings for users.
A user must be added before configuring the security settings. To learn more, see [Adding Users](/zidentity/adding-users).
To configure the security settings:
- Go to **Directory **> **Users**.
- Click the **Edit **icon for the user you want to configure the security settings.
- In the **Edit User** window, select the **Security Settings** tab.
- **Change Password Settings:** Enable to modify the password configurations.
- From the **Password Option **drop-down menu, select the required option for the user's initial login:
- **Set by Administrator**: Select this option to set a password for the user:
- **Password**: Enter a password for the user.
- **Confirm Password**:** **Retype the user's password.
- **Prompt for Password Change After the Initial Log In**: This option is selected by default. The user needs to change the password by following the guidelines defined in the [password policy](/zidentity/configuring-password-policy).
- **Set By User**: Select this option if the user must set their own password to access the ZIdentity landing page. The user receives a password reset email. The user can choose and configure the required [authentication method](/zidentity/configuring-authentication-methods).
- **Auto-generated**: Select this option to auto-generate a password for the user:
- **Password**: Use the **Copy** and **View **icons to copy or view the password.
- **Prompt for Password Change After the Initial Log In**:** **This option is selected by default. The user needs to change the password by following the guidelines defined in the [password policy](/zidentity/configuring-password-policy).
- **Skip Second-Factor Authentication:** Enable if you want the user to skip second-factor authentication. For the **Skip Until **option, select the date and time up to when the user can skip second-factor authentication. Post this duration, the user must configure second-factor authentication.
- **MFA Authenticator: **Displays the MFA method configured for a user and the date and time it was last used to log in to ZIdentity Admin Portal. Click the **Delete **icon to remove the configured MFA option. The user is then prompted to reconfigure MFA the next time they log in to the ZIdentity Admin Portal.
[See image.](#3Security-settings)
-
Click **Update**.
The security setting is updated.
[]
![Security Settings tab displaying configured MFA Authenticators for users.](/downloads/zidentity/getting-started/setting-your-zscaler-account/3SecuritySettings.png)