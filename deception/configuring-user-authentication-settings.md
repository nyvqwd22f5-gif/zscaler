# Configuring User Authentication Settings
Source: https://help.zscaler.com/itdr/configuring-user-authentication-settings
PDF: https://help.zscaler.com/pdf/com/en/1531738.pdf

You can configure user authentication settings from the Settings page. You can disable password-based authentication if single sign-on (SSO) is enabled, modify the password expiration period, and modify two-factor authentication (2FA) one-time password (OTP) duration.
Any changes made to these settings are applied to all users.
Disabling Password-Based Authentication
If you have enabled SSO for users, then you can disable authentication to the Zscaler ITDR Admin Portal via local credentials (user passwords stored in Zscaler ITDR).
Make sure that you have configured at least one SSO feature and tested it before disabling password-based authentication.
To disable password-based authentication:
- Go to **Settings** > **Users & Roles** > **Settings**.
- Select **Disable password login**.
[See image.](#itdr-disable-password-authentication)
- Click **Save**.
After you disable the password-based authentication, you cannot log in to the portal using your local username and password.
Modifying the Password Expiration Period
By default, the password expiration period is 90 days. You can modify the password expiration period for all users.
To modify the password expiration period:
- Go to **Settings** > **Users & Roles** > **Settings**.
- In **Password expiration (in days)**, enter the password expiration period in days.
[See image.](#itdr-modify-password-expiry-period)
- Click **Save**.
After you configure the password expiration period, it is applied to all users from the day their account was created. Users older than the password expiration period are prompted to reset their passwords.
Modifying Two-Factor Authentication One-Time Password Duration
When signing into the ITDR Admin Portal for the first time, each user must configure 2FA using an authenticator app. Each OTP is valid for a time window of 30 seconds.
To accommodate possible clock skew between the ITDR Admin Portal and the authenticator app, OTPs submitted from the previous and next two windows are accepted, by default. If you encounter OTP errors due to clock skew, you can increase the number of windows.
To modify the OTP duration:
- Go to **Settings** > **Users & Roles** > **Settings**.
- Under **One-Time Password window**, enter a number.
[See image.](#itdr-modify-otp-duration)
- Click **Save**.
Zscaler recommends not modifying the default OTP duration. However, you can increase the window number by 1 until the clock skew problem is resolved.
[]![Disable password login](/downloads/itdr/authentication/authentication-settings/configuring-user-authentication-settings/itdr-disable-password-auth_1.png)
[]![Modify password expiry period](/downloads/itdr/authentication/authentication-settings/configuring-user-authentication-settings/itdr-modify-password-expiry-period_1.png)
[]![Modify OTP duration](/downloads/itdr/authentication/authentication-settings/configuring-user-authentication-settings/itdr-modify-otp-duration-1.png)