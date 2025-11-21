# Resetting the Login Credentials or MFA
Source: https://help.zscaler.com/zidentity/resetting-login-credentials-or-mfa
PDF: https://help.zscaler.com/pdf/com/en/1499351.pdf

You can reset the password or multi-factor authentication (MFA) when you've forgotten the credentials or when required.
- [Resetting the Password](#resettingpassword)
- [Resetting the Second-Factor Authentication](#resetsecondfactorauth)
[]
[Resetting the Password by Using the Self Recovery Option](#Reset-password-option)
[Resetting the Password by Requesting an Administrator](#requesting-admin)
[]
-
On the login page, enter your **Login ID**, then click **Next**.
[See image.](#welcome-screen)
-
On the next page, click **Having trouble logging in?**
[See image.](#2having-trouble)
-
Click **Reset Password**.
[See image.](#3reset-pass)
The link to reset the password is sent to your email address. This link remains valid for 15 minutes. After 15 minutes, you need to resend the link again.
- Open the email and click the link. You must verify with the registered MFA option for resetting a password.
-
On the second-factor authentication page, enter details for authentication type and click **Verify**. You can reset the password after successful verification.
[See image.](#4second-factor-auth)
-
On the **Reset Password **page:
- **New Password**: Enter a password.
- **Confirm New Password**: Re-enter the password to confirm.
[See image.](#5new-pass)
-
Click **Next**.
Your credentials are reset and the **Success **page appears.
-
Click **Re-Login** to log in to ZIdentity Admin Portal and navigate to the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#6success)
[]To reset the password by requesting another administrator, see [Configuring Security Settings for Users](/zidentity/configuring-security-settings-users).
[]
To reset the MFA option, contact your ZIdentity administrator. An administrator might delete the configured MFA option from the **Security Settings** tab for users. The user is then prompted to reconfigure MFA the next time they log in to the ZIdentity Admin Portal.
Administrators can also delete the Email OTP option for users who have opted it as their MFA option.
[See image.](#3Security-settings)
[]
![ZIdentity Admin Portal Welcome page with blurred Login ID.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/1welcome-page.png)
[]
![ZIdentity Admin Portal Welcome page with blurred login ID and highlighted "Having Trouble Logging In" option.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/2having-trouble.png)
[]![Having Trouble Logging In page with blurred Login ID.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/3reset-pass.png)
[]
![Second Factor Authentication page displaying TOTP Authenticator for verification.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/4second-factor-auth.png)
[]![Reset Password page with blurred Login ID.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/5new-pass.png)
[]![Account Creation Success page with blurred login ID and option to Re-Login.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-resetting-login-credentials-or-mfa-doc-57297/6success.png)
[]
![Security Settings tab displaying configured MFA Authenticators for users.](/downloads/zidentity/getting-started/setting-your-zscaler-account/3SecuritySettings.png)