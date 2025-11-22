# Setting Up Your Zscaler Account
Source: https://help.zscaler.com/zidentity/setting-your-zscaler-account
PDF: https://help.zscaler.com/pdf/com/en/1499191.pdf

After you subscribe to ZIdentity, Zscaler Support creates a tenant for your organization and sends an email to complete the registration process and set up the authentication type. After completing the registration, you can start using the ZIdentity service.
During the registration process, you can cancel the process at any time, come back later, and choose to either continue the process from where you left it or restart the process from the beginning.
To complete your registration:
-
Open the email that you received from [Zscaler Support](/contact-support) and click the registration link. The registration link is valid for 72 hours.
You are redirected to the sign-up page.
[See image.](#support-email)
-
(Optional) If the link becomes invalid after 72 hours, click the expired link. A new registration link is sent to your email address that remains valid for 24 hours.
[See image.](#newOnboardinglink)
You can regenerate the registration link up to three times. After three attempts, contact [Zscaler Support](/contact-support) and request a new link.
-
On the sign-up page:
- **Organization Name**: Enter your organization's name.
- **First Name**: Enter your first name.
- **Last Name**: Enter your last name.
[See image.](#sign-up)
-
Click **Next**.
The **Email Address Verification** window appears.
-
Enter your email address and click **Verify**.
A one-time password (OTP) is sent to your email address. If you choose [multi-factor authentication (MFA)](/zidentity/resetting-login-credentials-or-mfa) for your account, the email address that you verify in this field is used for email-based authentication.
[See image.](#email-address)
-
Enter the OTP sent to your email address and click **Next**.
If you don't receive an OTP, click **Resend**, which is enabled after 60 seconds, to receive another OTP.
[See image.](#email-address-verify)
-
Enter a domain name for your organization and click **Next**.
This name is used to create a unique domain for your organization. After completing the setup, you can access the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page) by using the URL `<initial domain name>``.zslogin.net` (e.g., if `zidentitydep` is the domain name, then the login URL becomes `zidentitydep.zslogin.net`).
[See image.](#Initial-domain)
The End User Subscription Agreement (EUSA) appears.
- Read the EUSA and click **Accept**.
- On the **Create a Password** page, set up a new password.
- **New Password**: Enter a password.
-
**Confirm New Password**: Retype the password to confirm.
[See image.](#password-screen)
- Click **Next**.
-
On the **Multi-factor Authentication **page, select one of the following authentication types, then click **Set Up**:
- [TOTP Authenticator](#google-auth)
- [Security Key or Biometric](#security-key-bio)
- [SMS OTP](#sms-otp)
- [Email OTP](#email)
All users are required to set up MFA for improved security.
[See image.](#mfa-screen)
-
Your account is created after successful MFA enrollment. On the **Success **page, note your login ID and click **Re-Login **to log in to the ZIdentity Admin Portal.
[See image.](#success)
After successful login with configured credentials, the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page) appears.
[See image.](#zid-landing-page)
[]
A list of all Fast Identity Online 2 (FIDO2) supported methods available for your device is displayed. FIDO2 is a set of protocols developed by the FIDO Alliance to provide the most secure passwordless authentication methods. The services (such as Windows Hello, YubiKey, etc.) register and certify their security devices with FIDO2 for their customers.
To configure a security key or biometric:
- Select one of the methods from the list to set up a security key or biometric authentication.
- Follow the instructions displayed on your screen to complete the setup.
- []Follow the steps shown on the screen and then click **Next**.
- In the** Verification Code** field, enter the verification code that you see in the Authenticator and click **Verify **before the time-sensitive verification expires.
- []**Country**: Select the country of your phone number.
- **Phone Number**: Enter the phone number on which you want to receive the OTP and click **Send OTP via SMS**.
- **Enter SMS OTP**: Enter the OTP received on your phone and click **Verify**. The OTP is only valid for two minutes, after which you can click **Back**, then click **Send OTP via SMS** to receive another OTP. You can also choose to go back** **and modify your phone number before you verify.
[]After clicking **Set Up**, your secondary authenticator is configured as Email OTP. You don't have to verify your email address because it was verified at the beginning of the registration.
The Email OTP option is not enabled by default as it is not recommended for MFA as per [NIST guidelines](https://pages.nist.gov/800-63-FAQ/#q-b11). If you want to enable it, you can raise a [Zscaler Support](/contact-support) ticket.
[]![Sign-up page](/downloads/zidentity/getting-started/setting-your-zscaler-account/sign-up-page1.png)
[]![Entering Email Address](/downloads/zidentity/getting-started/setting-your-zscaler-account/one-timecode.png)
[]![Verifying Email Address](/downloads/zslogin/getting-started/setting-your-zscaler-account/zid-email-verify3.png)
[]![Entering Initial Domain](/downloads/zidentity/getting-started/setting-your-zscaler-account/sign-up-domain-page.png)
[]![Select the MFA method](/downloads/zidentity/getting-started/setting-your-zscaler-account/zid-mfaoptions.png)
[]![Create Password screen with blurred login ID.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-setting-your-zscaler-account-doc-57297/2createpassword.png)
[]![Account creation Success page with blurred login ID, name and email.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-setting-your-zscaler-account-doc-57297/4success.png)
[]![Registration Email](/downloads/zidentity/getting-started/setting-your-zscaler-account/Support-email1.png)
[]![ZIdentity Landing Page with different Zscaler services in tiles and annotation around the ZIdentity Administration tile. ](/downloads/zidentity/getting-started/admin-portal/accessing-and-navigating-zidentity-landing-page/Zid-landing%20page1.png)
[]![New Onboarding Link](/downloads/zidentity/getting-started/setting-your-zscaler-account/OTL1.png)