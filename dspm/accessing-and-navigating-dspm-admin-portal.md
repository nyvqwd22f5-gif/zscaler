# Accessing and Navigating the DSPM Admin Portal
Source: https://help.zscaler.com/dspm/accessing-and-navigating-dspm-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1474191.pdf

This article covers the following topics:
- [Accessing the DSPM Admin Portal](#dspm-signon)
- [Accepting the End User Subscription Agreement (EUSA)](#dspm-eusa)
- [Navigating within the DSPM Admin Portal](#dspm-portalnav)
When you are ready to begin configuring DSPM, see the [Step-by-Step Configuration Guide for DSPM](/dspm/step-step-configuration-guide-dspm).
[]DSPM is enabled with ZIdentity as the identity and authentication service. After your organization is provisioned for DSPM, you receive an email to complete your account registration. To set up the account:
- Open the email that you received from Zscaler Support and click **Setup**. This link is valid for 72 hours.
- On the **Create a Password** page, set up a new password:
- **New Password**: Enter a password.
- **Confirm New Password**: Retype the password to confirm.
- Click **Next**.
- On the **Multi-Factor Authentication** page, select one of the following authentication types and click **Set Up**.
- [Security Key or Biometric](#securitykey)
- [Phone OTP](#phoneotp)
- [TOTP Authenticator](#totpauthenticator)
Logging in to the DSPM Admin Portal
You can log in to the DSPM Admin Portal using one of the following options:
- [ZIdentity](#zidentitylandingpage)
- [ZIA Admin Portal](#ziaadminportal)
- [IdP](#Idp)
- [Service Provider (SP)-Initiated Flow](#sp-initiatedlogin)
[]
- [][Log in to the ZIdentity Landing Page.](#access-zslogin-landing)
-
Click the **Data Security Posture Management** tile.
[See image.](#zid-dspm-tile)
You are redirected to the DSPM Admin Portal.
[]You can access the DSPM Admin Portal from the Zscaler Internet Access (ZIA) admin portal using SSO.
In the ZIA Admin Portal, go to **Dashboard** > **Zscaler DSPM Portal**, or **Policy** > **Zscaler DSPM Portal**. You are directed to the DSPM Admin Portal. On the [Data Sensitivity Settings page](/dspm/about-data-sensitivity-settings), you can see the link to navigate back to the ZIA Admin Portal and modify the DLP engine configuration. This link is only visible if you access the DSPM Admin Portal from the ZIA Admin Portal and not vice versa. To learn more, see [Accessing the DSPM Admin Portal using SSO](/zia/accessing-zscaler-dspm-admin-portal-using-sso).
- []Log in to your IdP with your credentials. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).
-
On the IdP page, under **My Apps**, click the ZIdentity tile.
[See image.](#oktaidp)
You are redirected to the [ZIdentity landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
-
Click the **Data Security Posture Management** tile.
[See image.](#ziddspmtile)
-
[]Click the DSPM login URL.
You are directed to the ZIdentity login page.
- Enter your **Login ID **and select **Remember me **if you want the service to remember your login ID the next time you log in.
-
Click **Next**.
[See image.](#ssologinpage)
- Sign in to the [ZIdentity Landing Page](#zidentitylogin).
-
Click the **Data Security Posture Management** tile.
You are redirected to the DSPM Admin Portal.
[]When you log in for the first time, the DSPM Admin Portal displays the EUSA. Accept the EUSA. If you click **Cancel**, the DSPM Admin Portal logs you out automatically. You can read the [full EUSA](https://www.zscaler.com/legal/end-user-subscription-agreement?_gl=1*18c1oa5*_ga*MjEwNjUxNjQxNi4xNjUzOTY5NjU3*_ga_10SPJ4YJL9*MTY1NDE0MTg2MC4xMy4xLjE2NTQxNDIyMTQuNDM.&_ga=2.103808261.441828250.1708941132-1299510785.1708314652) any time.
When DSPM is first provisioned for your organization, you receive the admin account credentials. You are required to directly log in to the DSPM Admin Portal using your admin account credentials and accept the EUSA. Only after this initial login and EUSA acceptance, you can use SSO to access the DSPM Admin Portal from Zscaler Internet Access (ZIA).
[]The DSPM Admin Portal has the following items in the left-side navigation:
- [Dashboard](#ds-dboard)
- [Alerts](#ds-alerts)
- [Analytics](#ds-analytics)
- [Policy](#ds-policies)
- [Administration](#ds-admin)
- [Profile](#ds-profile)
- [Help](#helpicon)
- [Logout](#ds-logout)
![The DSPM dashboard with annotation around left-navigation menu.](/downloads/dspm/getting-started/accessing-and-navigating-dspm-admin-portal/dspm-left-side-navigation.png)
-
[]Select one of the methods from the list to set up a security key or biometric authentication.
[See image.](#select-biometric)
- Follow the instructions displayed on the screen to complete the setup.
- []**Country**: Select the country of your phone number.
- **Phone Number**: Enter the phone number on which you want to receive the OTP and click **Request Code**.
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
- []Follow the steps shown on the screen and then click **Next**.
- In the** Verification Code** field, enter the verification code that you see in the Authenticator and click **Verify **before the time-sensitive verification expires.
[]Click **Dashboard** to get a high level overview of the scan results for your cloud resources. To learn more, see [About the Dashboard](/dspm/about-dashboard).
[]Click **Alerts** to view and analyze the alerts, and configure and manage alert rules and alert filters. To learn more, see [About Alerts](/dspm/about-alerts).
[]Click **Analytics** to view the [data inventory](/dspm/about-data-inventory), [compliance dashboard](/dspm/about-compliance), [view and download reports](/dspm/about-reports), and to [investigate your cloud resources](/dspm/about-investigation).
[]Click **Policies** to apply various security policy controls. To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies).
[]Click **Administration** to [onboard cloud accounts](/dspm/about-cloud-accounts), [configure scan settings](/dspm/about-scan-settings), [view roles](/dspm/about-roles), or view or add [business units](/dspm/about-business-units).
[]Click the **Help **icon to access the Zscaler Help Portal, where you can find DSPM Help articles. You can also access legal notices, privacy policy, and the subscription agreement.
[See image.](#helpicn)
[]Click the **Profile** icon to view your account and tenant details. To learn more, see [Viewing the User Profile](/dspm/viewing-user-profile).
[]Click the **Log Out** icon to log out of the DSPM Admin Portal.
[]
![The Windows security window with the list of authentication options.](/downloads/tech-pubs-drafts/dspm-draft-articles/accessing-and-navigating-dspm-admin-portal-draft/set-up-biometric.png)
[]
![The Okta dashboard with the list of applications configured.](/downloads/dspm/getting-started/admin-portal/accessing-and-navigating-dspm-admin-portal/okta-zid-tile.png)
[]![The ZIdentity Landing Page with the list of entitlements assigned.](/downloads/dspm/getting-started/admin-portal/accessing-and-navigating-dspm-admin-portal/zidentity-dspm-tile.png)
[]![The ZIdentity Landing Page with the list of entitlements assigned.](/downloads/dspm/getting-started/admin-portal/accessing-and-navigating-dspm-admin-portal/zidentity-dspm-tile.png)
[]![The SSO login page to enter your login ID.](/downloads/dspm/getting-started/accessing-and-navigating-dspm-admin-portal/dspm-zidentity-ssopage.png)
[]![The icons on the left-side navigation with annotation around the help icon.](/downloads/dspm/getting-started/accessing-and-navigating-dspm-admin-portal/dspm-help-icon.png)