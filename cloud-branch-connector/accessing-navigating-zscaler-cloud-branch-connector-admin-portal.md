# Accessing and Navigating the Zscaler Cloud & Branch Connector Admin Portal
Source: https://help.zscaler.com/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1420406.pdf

The Zscaler Cloud & Branch Connector Admin Portal allows users to view and manage their Cloud and/or Branch Connectors.
- [Signing in to the Zscaler Cloud & Branch Connector Admin Portal](#LoggingIn)
- [Navigating within the Zscaler Cloud & Branch Connector Admin Portal](#NavigatingCCAdminPortal)
[]After your organization is provisioned for Cloud & Branch Connector and you know your [cloud name](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector), you can access the Cloud & Branch Connector Admin Portal.
- Go to the Cloud & Branch Connector login page.
- Enter your **Login ID**,** **select **Remember my Login ID** if you want the portal to remember your username the next time you log in, and then click **Next**.
- Enter your **Password** and click **Sign In**.
If you make 5 unsuccessful attempts to log in within one minute, the account is locked out for 5 minutes and the failed attempts are recorded.
To simultaneously access the Zscaler Admin Portal of two different Zscaler services, you must either use a private browser or open each Zscaler service on a different browser. If you access the admin portals of multiple Zscaler services on different tabs of the same browser, the UI session you access first is automatically redirected to the portal of the service you accessed most recently.
For example, if you log in to the Cloud & Branch Connector Admin Portal on one tab of your browser and later log in to the Zscaler Internet Access (ZIA) Admin Portal on a different tab of the same browser, then the tab logged in to the Cloud & Branch Connector Admin Portal automatically redirects you to the most recently accessed ZIA Admin Portal.
ZIdentity
ZIdentity is a unified identity platform that allows users to use single sign-on (SSO) to access multiple Zscaler admin portals. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
- [If you are subscribed to ZIdentity, perform the following steps:](#access-zidentity-landing)
- Click the **Zscaler Cloud and Branch Connector** tile to access the Cloud & Branch Connector Admin Portal. Perform the desired steps in the [left-side navigation](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal).
[See image.](#ZSLoginCBConnector)
You are redirected to the Cloud & Branch Connector Admin Portal.
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
[]![The Zscaler Cloud and Branch Connector option in the ZSLogin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/accessing-and-navigating-zscaler-cloud-branch-connector-admin-portal-draft-doc-46397/ZSLogin%20cbconnector.jpg)
[]The Cloud & Branch Connector Admin Portal has the following items on the left-side navigation:
- [Dashboard](#ZDXdashboard)
- [Analytics](#analytics)
- [Administration](#Administration)
- [Forwarding](#policy)
- [Search](#search)
- [Activation](#Activation)
- [Profile](#Profile)
- [Help](#help)
- [Log Out](#LogOut)
![Left-side Navigation in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/accessing-and-navigating-zscaler-cloud-branch-connector-admin-portal-draft-doc-48230/Accessing%20and%20Navigating%20GCP.png)
When you are ready to begin configuring Cloud Connector, see [Step-by-Step Configuration Guide for Zscaler Cloud Connector](/cloud-branch-connector/step-step-configuration-guide-zscaler-cloud-connector). When you are ready to begin configuring Branch Connector, see [Step-by-Step Configuration Guide for Zscaler Branch Connector](/cloud-branch-connector/step-step-configuration-guide-zscaler-branch-connector).
[]The Cloud & Branch Connector** Dashboard** has **Cloud & Branch Connector Monitoring** and **Traffic Monitoring** tabs. To learn more, see [Accessing Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) and [Analyzing Traffic Monitoring](/cloud-branch-connector/analyzing-traffic-monitoring).
[]Click **Analytics** for access to:
- Session Insights
- DNS Insights
- Tunnel Insights
To learn more, see [About Insights](/cloud-branch-connector/about-insights).
[]Click **Administration** for access to:
- API Key Management
- Cloud Connector Groups
- Branch Devices
- Locations
- Location Templates
- Provisioning & Configuration
- Gateways
- Administrator Management
- Role Management
- Audit Logs
- IP & FQDN Groups
- Network Services
- Deployment Templates
- Nanolog Streaming Service
- Advanced Settings
- Branch Connector Images
- ZT Devices
To learn more, see [Administration](/cloud-branch-connector/administration).
[]Click **Forwarding** for access to:
- Traffic Forwarding
- Log and Control Forwarding
- DNS Control
To learn more, see [Forwarding](/cloud-branch-connector/forwarding).
[]Click the **Search** icon to search for sections within the Cloud & Branch Connector Admin Portal. To learn more, see [Searching in the Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/searching-zscaler-cloud-branch-connector-admin-portal).
[]Click** Activation** to activate saved changes and view the activation status of those changes. To learn more, see [Saving and Activating Changes](/cloud-branch-connector/saving-and-activating-changes).
[]Click **Profile** for access to:
- User Display Name
- Password
- Language
- Time Zone
- Forwarding Information
[]Click **Help** for access to:
- [Zscaler Help Portal](/cloud-branch-connector)
- Remote Assistance
- Submit a Ticket
- [Cloud Configuration Requirements](https://config.zscaler.com/zscaler.net/fcr)
[]When you are done, click **Log Out** to log out of the Cloud & Branch Connector Admin Portal. If you are inactive for 15 minutes, you are automatically logged out.