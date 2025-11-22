# Configuring Multi-Factor Authentication
Source: https://help.zscaler.com/zidentity/configuring-multi-factor-authentication
PDF: https://help.zscaler.com/pdf/com/en/1499196.pdf

ZIdentity supports multi-factor authentication (MFA) for enhanced security, and it is required by default for all admins. Zscaler strongly recommends keeping MFA enabled. You can authenticate users with a password and a second factor (i.e., SMS one-time passcode (OTP), email OTP, time-based OTP (TOTP), and Fast IDentity Online (FIDO) authentication). In addition, you can configure passwordless authentication by setting up FIDO2 as the primary authenticator.
Enabling MFA or FIDO2
To set up MFA or FIDO2:
- Go to **Administration** > **Authentication **> **Authentication Methods**.
-
On the **Authentication Methods** page:
- **Enable Multi-Factor Authentication (MFA) for Service Enrollment**: This option is shown only when the user single sign-on (SSO) feature is enabled for your tenant. You can choose to disable this option for your [users](/zidentity/about-users) when required.
-
**Allow FIDO2 as Primary Authenticator**: Enable this option to allow users to configure a passwordless authentication method for their ZIdentity account. When you enable this option, users can skip the password and configure any of the Fast IDentity Online 2 (FIDO2) methods available on their device in the subsequent log-in attempt.
The following scenarios occur when you disable FIDO2 authentication method as your primary authenticator:
- If MFA is enabled, users are required to log in using their MFA credentials. If not already configured, users can request the password reset option and set up MFA.
-
If MFA is disabled, users are required to log in using only their passwords. If a user has forgotten the password or has never configured a password-based authentication, they can click the **Password Reset** option and add a new password.
[See image.](#zsl-disablefido)
[See image.](#authentication-methods-page)
- Click **Save**.
Configuring MFA
After your organization configures a ZIdentity account for you with access to Zscaler services and the functional scope of your role, you receive an email from Zscaler Support to choose and set up MFA for accessing the ZIdentity account.
To configure MFA:
- [For ZIdentity Admins](#zid-admins)
- [For External IdP Admins](#external-idp)
[]
-
Open the email from Zscaler Support and click the setup link.
You are redirected to the sign-up page.
- On the sign-up page:
- **New Password**: Enter a password.
- **Confirm New Password**: Retype the password to confirm.
- Click **Next**.
-
On the **Multi-Factor Authentication **page, select one of the following authentication types, then click **Set Up**:
- [TOTP Authenticator](#google-auth)
- [Security Key or Biometric](#security-key-bio)
- [SMS OTP](#sms-otp)
- [Email OTP](#email)
[See image.](#zsl-secondaryauth)
Your account is successfully created. You can make a note of your login ID displayed on the screen and proceed to [log in to your ZIdentity account](/zidentity/accessing-and-navigating-zidentity-landing-page).
[]
-
On the ZIdentity **Log in** page, enter your **Login ID **and select **Remember me **if you want the service to remember your login ID the next time you log in.
[See image.](#1login-page)
- Click** Next**.
-
On the External IdP authentication page, enter the password and click **Sign in**.
[See image.](#2external-idp-auth)
After successful authentication at the external IdP, configure MFA in ZIdentity.
-
On the **Multi-factor Authentication **page, select one of the following authentication types, then click **Set Up**:
- [TOTP Authenticator](#external-idp-totp)
- [Security Key or Biometric](#external-idp-fido)
- [Email OTP](#external-idp-email)
[See image.](#3mfa)
Your account is successfully created. You can make a note of your login ID displayed on the screen and proceed to [log in to your ZIdentity account](/zidentity/accessing-and-navigating-zidentity-landing-page).
Skip Multi-factor Authentication
As an admin, you can skip the MFA for a grace period of 7 days. After the grace period is over, you need to configure MFA in ZIdentity.
Admins using MFA through their external IdP can disable **Enforce Zscaler Admin MFA** option to prevent additional authentication verification from ZIdentity. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers#about).
To skip MFA:
-
On the **Multi-factor Authentication **page, click **Skip **to temporarily skip MFA for 7 days.
[See image.](#4skip)
-
Click **Continue **to confirm.
[See image.](#5confirm-skip)
Your account is successfully created without MFA. You can make a note of your login ID displayed on the screen and proceed to [log in to your ZIdentity account](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#6skip-success)
[]
- Follow the steps shown on the screen and then click **Next**.
- In the **TOTP Authenticator Verification Code** field, enter the verification code that you see in the TOTP Authenticator and click **Verify **before the time-sensitive verification expires.
[]
A list of all Fast Identity Online 2 (FIDO2) supported methods available for your device is displayed. FIDO2 is a set of protocols developed by the FIDO Alliance to provide the most secure passwordless authentication methods. The services (such as Windows Hello, YubiKey, etc.) register and certify their security devices with FIDO2 for their customers.
To configure a security key or biometric:
- Click **Set Up**.
- Select one of the methods from the list to set up a security key or biometric authentication.
- Follow the instructions displayed on your screen to complete the setup.
[]
- **Country**: Select the country of your phone number.
- **Phone Number**: Enter the phone number on which you want to receive the OTP and click **Send OTP via SMS**.
- **Enter SMS OTP**: Enter the OTP received on your phone and click **Verify**. The OTP is only valid for two minutes, after which you can click ****Back****, then click ****Send OTP via SMS**** to receive another OTP.
[]After clicking **Set Up**, your secondary authenticator is configured as Email OTP. You don't have to verify your email address because it was verified at the beginning of the registration.
The Email OTP option is not enabled by default as it is not recommended for MFA as per [NIST guidelines](https://pages.nist.gov/800-63-FAQ/#q-b11). If you want to enable it, you can raise a [Zscaler Support](/contact-support) ticket.
[]
- Follow the steps shown on the screen and then click **Next**.
- In the **TOTP Authenticator Verification Code** field, enter the verification code that you see in the TOTP Authenticator and click **Verify **before the time-sensitive verification expires.
[]
A list of all Fast Identity Online 2 (FIDO2) supported methods available for your device is displayed. FIDO2 is a set of protocols developed by the FIDO Alliance to provide the most secure passwordless authentication methods. The services (such as Windows Hello, YubiKey, etc.) register and certify their security devices with FIDO2 for their customers.
To configure a security key or biometric:
- Click **Set Up**.
- Select one of the methods from the list to set up a security key or biometric authentication.
- Follow the instructions displayed on your screen to complete the setup.
[]
After clicking **Set Up**, your secondary authenticator is configured as Email OTP. You don't have to verify your email address because it was verified at the beginning of the registration.
The Email OTP option is not enabled by default as it is not recommended for MFA as per [NIST guidelines](https://pages.nist.gov/800-63-FAQ/#q-b11). If you want to enable it, you can raise a [Zscaler Support](/contact-support) ticket.
[]![The authentication methods MFA and FIDO2 in a list with their respective toggles.](/downloads/zidentity/authentication/configuring-authentication-methods/zid-authmethods.png)
[]![A message describing what happens when you disable FIDO2](/downloads/zslogin/authentication/configuring-authentication-methods/zidentity-disable-fido2_0.png)
[]![Select the MFA method](/downloads/zidentity/authentication/configuring-mfa/zid-mfaoptions.png)
[]![ZIdentity Login page with blurred Login ID and Remember ME checkbox checked.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/1Login-page.png)
[]![External IdP Authentication page with blurred Login ID.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/2external-idp-auth.png)
[]![Multi-factor Authentication page displaying authentication methods in ZIdentity for external IdP admins.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/3mfa.png)
[]![Multi-factor Authentication page displaying authentication methods in ZIdentity for external IdP admins.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/4skip.png)
[]![Multi-factor Authentication page when the MFA is skipped.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/5confirm-skip.png)
[]![Account Creation Success page without MFA configuration.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-mfa-doc-57297/6skip-success.png)