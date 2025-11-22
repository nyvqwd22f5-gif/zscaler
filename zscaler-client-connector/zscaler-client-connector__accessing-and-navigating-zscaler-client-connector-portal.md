# Accessing and Navigating the Zscaler Client Connector Portal
Source: https://help.zscaler.com/zscaler-client-connector/accessing-and-navigating-zscaler-client-connector-portal
PDF: https://help.zscaler.com/pdf/com/en/1285481.pdf

This article covers the following topics:
- [Accessing the Zscaler Client Connector Portal](#accessing-the-portal)
- [Navigating within the Zscaler Client Connector Portal](#navigating-the-portal)
- [Maintenance and Upgrades](#maintenance-and-upgrades)
When you are ready to configure Zscaler Client Connector, see the [Step-by-Step Configuration Guide for Zscaler Client Connector](/zscaler-client-connector/step-step-configuration-guide-zscaler-client-connector).
[]You can access the Zscaler Client Connector Portal through one of the following Zscaler Admin Portals:
- [ZIA Admin Portal](#zia-admin-portal)
- [ZPA Admin Portal](#zpa-admin-portal)
- [ZDX Admin Portal](#zdx-admin-portal)
- [ZIdentity Landing Page](#SubscribedtoZIdentity)
Your Zscaler Client Connector Portal session expires after one hour and you are automatically redirected to the previous Zscaler Admin Portal, where you might need to authenticate.
[]In the** **ZIA Admin Portal, go to **Policy **>** Zscaler Client Connector Portal**.
![Zscaler Client Connector access through ZIA](/downloads/tech-pubs-drafts/client-connector-draft-articles/accessing-and-navigating-zscaler-client-connector-portal/ZIA-Admin-Portal_ZCC.png?1686761372)
If you're subscribed to ZIdentity, this link does not display in the ZIA Admin Portal and you must access the portal from the [ZIdentity Landing Page](#access-zidentity-landing).
[]In the ZPA Admin Portal, click the **Client Connector **icon from the left-side navigation.
![Accessing the Zscaler Client Connector Portal from the ZPA Admin Portal](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-zscaler-client-connector-portal-doc-47165/ZPA-Client-Connector-Portal_0.png)
If you're subscribed to ZIdentity, this link does not display in the ZPA Admin Portal and you must access the portal from the [ZIdentity Landing Page](#access-zidentity-landing).
[]In the ZDX Admin Portal, go to **Administration > Client Connector Portal**.
![Access to Client Connector from ZDX ](/downloads/tech-pubs-drafts/client-connector-draft-articles/accessing-and-navigating-zscaler-client-connector-portal/ZDX-ZCC.png?1686761477)
If you're subscribed to ZIdentity, this link does not display in the ZDX Admin Portal and you must access the portal from the [ZIdentity Landing Page](#access-zidentity-landing).
[]During the scheduled maintenance and regular upgrade periods, the Zscaler Client Connector Portal is in read-only mode. You can view the [Dashboard](/zscaler-client-connector/understanding-zscaler-client-connector-portal-dashboard) content and navigate through the Zscaler Client Connector Portal to view various details.
You cannot configure or edit any parameters when the Zscaler Admin Portal is in read-only mode. After the upgrade is complete, the Zscaler Admin Portal automatically refreshes and editing is enabled.
[]The Zscaler Client Connector Portal has the following items in the left-side navigation:
![Zscaler Client Connector Portal Navigation Bar](/downloads/tech-pubs-drafts/client-connector-draft-articles/about-zscaler-client-connector-portal-doc-47165/Zscaler-Client-Connector-Portal-reactUI.png)
- **Dashboard**: Click to view dashboard information about enrolled devices. To learn more, see [About the Zscaler Client Connector Portal Dashboard](/zscaler-client-connector/about-zscaler-app-portal-dashboard).
- **Enrolled Devices**: Click to view a list of enrolled devices and view device fingerprint information. To learn more, see [About Enrolled Devices](/zscaler-client-connector/about-enrolled-devices).
-
**App Profiles**: Click to configure Zscaler Client Connector profiles that control:
- Whether users must enter an admin-provided password in order to log out of, disable, or uninstall the app.
- The [forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-app) for Zscaler Internet Access (ZIA)) and Zscaler Private Access (ZPA).
To learn more about app profiles, see [About Zscaler Client Connector Profiles](/zscaler-client-connector/about-zscaler-app-profiles).
- **Administration**: Click to [configure the different administration settings for Zscaler Client Connector](/zscaler-client-connector/zscaler-app-step-step-configuration-guide#ConfigAdminSettings). To learn more, see the following:
- [Client Connector App Store](/zscaler-client-connector/about-zscaler-client-connector-app-store)
- [Client Connector Notification](/zscaler-client-connector/about-zscaler-client-connector-notifications)
- [Audit Logs](/zscaler-client-connector/about-audit-logs)
- [Forwarding Profile](/zscaler-client-connector/about-forwarding-profiles)
- [Trusted Networks](/zscaler-client-connector/about-trusted-networks)
- [Client Connector Support](/zscaler-client-connector/configuring-user-access-support-and-logging-zscaler-app)
- [Zscaler Service Entitlement](/zscaler-client-connector/about-zscaler-service-entitlement)
- [User Agent](/zscaler-client-connector/about-user-privacy)
- [Client Connector IdP](/zscaler-client-connector/about-zscaler-app-idp)
- [Device Posture](/zscaler-client-connector/about-device-posture-profiles)
- [ZIA Posture Profile](/zscaler-client-connector/adding-zia-posture-profiles)
- [Application Bypass](/zscaler-client-connector/about-application-bypass-info)
- [Dedicated Proxy Port](/zscaler-client-connector/configuring-dedicated-proxy-ports)
- [Public API](/zscaler-client-connector/adding-api-key)
- [Platform Settings](/zscaler-client-connector/about-platform-settings)
- [Administration Management](/zscaler-client-connector/about-administration-management)
- [Device Groups](/zscaler-client-connector/add-device-groups-zscaler-private-access-zpa)
- [ZPA Partner Logins](/zscaler-client-connector/enabling-zpa-partner-logins)
- **Profile**: Hover and select** Switch to Old UI** under **Choose a View **to return to the previous Zscaler Client Connector Portal view. To change the language, choose your desired language from the Language drop-down menu.
- **Logout**: Click to leave the Zscaler Client Connector Portal and return to the ZIA Admin Portal or ZPA Admin Portal.
- **Versions**: Select this option to display the required OS version next to the feature that is version-dependent.
- **Help**: Click to go to the Zscaler Help Browser, where you can find documentation that provides information and configuration guides about Zscaler Client Connector.
If you're subscribed to ZIdentity:
- [][Log in to the ZIdentity Landing Page](#access-zidentity-landing)
- Click the **Zscaler Client Connector **tile to access the Zscaler Client Connector Portal.
[See image.](#zidentity-landing-page)
You are redirected to the Zscaler Client Connector Portal.
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
[]![Zscaler Client Connector tile ](/downloads/z-app/getting-started/admin-portal/accessing-and-navigating-zscaler-client-connector-portal/zidentity-landing-page.png)