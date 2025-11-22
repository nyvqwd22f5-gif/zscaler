# Skipping Two-Factor Authentication
Source: https://help.zscaler.com/unified/skipping-two-factor-authentication
PDF: https://help.zscaler.com/pdf/com/en/1520326.pdf

ZIdentity allows administrators to permit users to skip two-factor authentication (2FA) for a short duration and use only their password to log in to the Admin Portal. For example, if a user does not have the device on which they receive the one-time passcode (OTP) for authentication, they can be allowed to skip 2FA temporarily.
2FA can be disabled only for user profiles that have single sign-on (SSO) enabled.
To allow users to skip 2FA:
- Go to **Administration **>** Identity** > **ZIdentity** > **Users**.
-
On the **Users** page, click the **Edit** icon for the required user.
[See image.](#edit-icon-users-page)
- In the** Edit User** window, select the **Security Settings** tab.
-
Enable **Skip Second Factor Authentication**.
[See image.](#skipping-2fa-option)
-
The **Skip Until** field appears, displaying the current date and time until when the user is allowed to skip the second factor authentication. By default, the skip duration is 8 hours. Click to select a different date and time. The maximum limit is 5 days.
[See image.](#skip-2fa-calendar)
- Click **Update**.
[]![A screenshot highlighting the option to edit a user record](/downloads/zidentity/authentication/skipping-two-factor-authentication/zidentity-edit-auser_0.png)
[]![A screenshot highlighting the option to skip 2FA](/downloads/zidentity/authentication/skipping-two-factor-authentication/zidenity-skip-authentication_0.png)
[]![A screenshot showing the Calendar option for skipping 2FA](/downloads/zidentity/authentication/skipping-two-factor-authentication/zidentity-skip-2fa-time_0.png)