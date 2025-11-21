# Accessing and Navigating the Zscaler ITDR Admin Portal
Source: https://help.zscaler.com/itdr/accessing-and-navigating-zscaler-itdr-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1531712.pdf

This article covers the following topics:
- [Signing In to the Zscaler ITDR Admin Portal](#signing-in-to-zscaler-itdr-admin-portal)
- [Accepting the End User Subscription Agreement (EUSA)](#accepting-eusa)
- [Navigating within the ITDR Admin Portal](#navigating-within-zscaler-itdr-admin-portal)
[]After your organization is provisioned for Zscaler ITDR, you will receive an email with the following details:
- Link to your Zscaler ITDR instance
- Link to set your password
- Security code
To sign in to the ITDR Admin Portal:
- Click the password link in your email. You need to set your password when you sign in for the first time.
- When the **Reset Password** page appears, enter your new password and then confirm it.
- Enter the **Security Code **from your email.
- Click **Next**.
[See image.](#set-password)
- When a QR code appears, scan it using a two-factor authentication (2FA) app to complete the 2FA configuration.
-
Enter the **One-Time Password (OTP)**. This is the 6-digit code shown on the authenticator app.
[See image.](#deception-config-2fa)
- Click **Submit**.
- When the Sign In page appears, enter your **Email** and **Password**.
- Click **Sign in**.
[See image.](#sign-in-to-admin-portal)
-
When the **Two-factor authentication** page appears, enter the **2FA code** from the authentication app.
[See image.](#enter-configured-2fa-code)
- Click **Submit**.
For ZIdentity-Enabled Customers
There is no separate UI for ITDR in ZIdentity. The ITDR configuration is done through the Deception UI.
If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#itdr-zslogin-node)
- From the ZIdentity Landing Page, click the **Deception** tile to access the ITDR Admin Portal.
If ZIdentity is enabled, no other sign-in methods are allowed.
For Customers Using SSO
Zscaler recommends that you use the ZIdentity Admin Portal to configure primary and secondary external identity providers (IdPs). Contact Zscaler Support to subscribe to ZIdentity. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).
If your account is configured to use a single sign-on (SSO) with an IdP:
- On the Sign In page, click the sign-in button with the IdP name.
[See image.](#sign-in-using-idp)
- You are redirected to your IdP's login page. Log in with your credentials.
If you log in successfully, you are redirected back to the ITDR Admin Portal.
[]
Based on your organization's [authentication preference](/zidentity/configuring-authentication-methods), sign in to the ZIdentity Landing Page using one of the following methods:
- [Password](#password)
- [Email One-Time Password (OTP)](#email-otp)
- [Security Key or Biometric](#security-key-biometric)
-
[]Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
[See image.](#login-page)
- Click** Next**.
-
Enter your **Password **and click **Sign In**.
[See image.](#Password-auth)
-
Based on your organization's MFA policy, two-factor authentication (2FA) is required. Complete your 2FA to access the ZIdentity Landing Page.
If you forget your password or want to configure a different secondary authenticator, click **Having trouble signing in? **> **Reset Password **or** Reset Second Factor**, and a reset email is sent to your email ID. The reset link within the email expires after 15 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
If your account is configured with MFA, you can sign in using an email OTP as well:
- []Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
-
Click** Next** and then, click **Other Sign-in Options**.
[See image.](#email-otp1)
The **Sign-in Options** window appears.
-
In the **Sign-in Options** window, click **Email OTP**.
[See image.](#email-otp2)
-
Enter the OTP sent to your email address and click **Sign In**. The OTP expires after 15 minutes. If the OTP expires or you don't receive an OTP, click **Resend **to receive another OTP after 60 seconds.
[See image.](#email-otp3)
- []Enter your **Login ID**. If you want the service to remember your login ID the next time you log in, select **Remember Me**.
-
Select **Sign-in using Security Key or Biometric**.
[See image.](#security-key)
- Click** Next**.
-
Based on your configuration, enter your security key or complete the biometric to access the ZIdentity Landing Page.
If you want to configure with a different security key or biometric, click **Having trouble signing in? **> **Reset Security Key or Biometric**, and a reset email is sent to your email ID. The reset link within the email expires after 15 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
[]![ZIdentity Login screen with blurred Login ID and Remember Me option selected..](/downloads/zidentity/zid-login-pagenew.png)
[]![A screenshot with blurred login ID and displaying password field.](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/Zid-PasswordAuth.png)
[]![A screenshot with blurred login ID, displaying password field and highlighted Other Sign-in Options.](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-other-sign-in-option.png)
[]![Sign-in options screen with blurred login ID and highlighted email otp option. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-email-otp-sign-in.png)
[]![Login using Email Code window with blurred login ID and displaying placeholder to enter OTP. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-email-otp-MFA1.png)
[]![ZIdentity Login screen with blurred login ID and selected Remember Me  and Sign-in using Security Key or Biometric options. ](/downloads/tech-pubs-drafts/zslogin-draft-articles/draft-accessing-and-navigating-zidentity-landing-page-doc-56497/zid-securitykey-mfa.png)
[]When you log in for the first time, the ITDR Admin Portal displays an EUSA. Click **Accept** to accept the EUSA.
![Accept EUSA](/downloads/deception/getting-started/admin-portal/about-zscaler-deception-admin-portal/zscaler-deception-eusa.png)
You cannot activate your license without accepting the EUSA. You can read the full EUSA at any time.
[]The ITDR Admin Portal contains the following items in the left-side navigation:
![Navigate within the Zscaler Deception Admin Portal](/downloads/itdr/getting-started/admin-portal/accessing-and-navigating-zscaler-itdr-admin-portal/itdr-left-side-panel.png)
- [Investigate](#itdrinvestigate)
- [Orchestrate](#itdrorchestrate)
- [ITDR](#ITDR)
- [Settings](#itdrsettings)
- [Search](#itdr-search)
- [System Messages](#itdrsystem-messages)
- [Account Settings](#itdraccount-settings)
- [Help](#itdrhelp)
- [Logout](#itdrlogout)
[]The **Investigate** page is the landing page that displays all the logged forensics and attacker information in a graphical format. You can leverage this information to reduce the mean time to detect (MTTD) and improve security efficiency. The Investigate page allows you to monitor and analyze the event activities that adversaries conduct on the Active Directory (AD) domain and endpoints to understand their tactics, techniques, and procedures (TTPs).
[]Click **Orchestrate** to:
- Automate rules to take immediate actions when events with threats are detected.
- Integrate with the security information and event management (SIEM) solutions and other log aggregation repositories to forward events to the SIEM.
- Contain threats to isolate detected attackers.
- Enrich alerts with relevant contextual information to the security events that are generated in the ITDR Admin Portal
- Create API tokens for additional platform integration.
[]Click **Settings** to configure users and roles and provides information regarding license consumption and audit trails.
To learn more, see [About Settings](/itdr/about-settings).
[]Click the **System Messages** icon to view [audit logs](/itdr/about-logs-and-system-messages) and [system messages](/itdr/viewing-and-managing-system-messages)
[]Click the **Account Settings** icon to reset your two-factor authentication (2FA), edit your profile, change your time zone, and change your password.
To learn more, see [About Account Settings](/deception/about-account-settings).
[]Click the **Help **icon to access the Zscaler Support Portal and submit a ticket to Zscaler Support.
[]Click the **Logout** icon to log out of the ITDR Admin Portal.
If ZIdentity is enabled, you are logged out of the ITDR Admin Portal only. When you sign in again, you don't have to enter the user credentials.
[]Click **ITDR** to access the [Identity Posture](/itdr/about-itdr-posture-active-directory-dashboard), [Credential Exposure](/itdr/about-endpoint-credential-exposure-dashboard) and [Change Detection](/itdr/about-itdr-change-detection) dashboards. You can also configure an [Active Directory (AD) domain scan](/itdr/scanning-active-directory), [credential exposure scan](/itdr/about-endpoint-credential-exposure-scan) and [threat detection policies](/itdr/about-threat-detection).
[]Click the **Search** icon to search for ITDR modules or sub-modules across the ITDR Admin Portal.
[]![Set Admin Portal password](/downloads/deception/getting-started/admin-portal/about-zscaler-deception-admin-portal/zscaler-deception-sign-in-set-password.png?1647328275)
[]![Configure 2FA](/downloads/deception/getting-started/admin-portal/accessing-and-navigating-zscaler-deception-admin-portal/zscaler-deception-config-2fa-2.png)
[]![Sign in to the Zscaler Deception Admin Portal](/downloads/deception/getting-started/admin-portal/about-zscaler-deception-admin-portal/zscaler-deception-sign-in.png?1647328906)
[]![Enter two factor authentication](/downloads/deception/getting-started/admin-portal/about-zscaler-deception-admin-portal/zscaler-deception-enter-configured-2fa.png?1647329316)
[]![Sign in using an IdP](/downloads/deception/getting-started/admin-portal/about-zscaler-deception-admin-portal/zscaler-deception-idp.png?1647329558)