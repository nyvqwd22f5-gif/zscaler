# Accessing and Navigating the ZIA Admin Portal
Source: https://help.zscaler.com/zia/accessing-and-navigating-zia-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1402301.pdf

This article covers the following topics:
- [Signing in to the ZIA Admin Portal](#Signing-into-zia)
- [Accepting the End User Subscription Agreement (EUSA)](#zia-eusa)
- [Navigating within the ZIA Admin Portal](#navigating-zia-admin-portal)
- [Maintenance and Upgrades](#AdminPortal-ReadOnlyMode)
[]After your organization is provisioned for ZIA, you are assigned to a [cloud name](/zia/what-my-cloud-name-zia). You can access the ZIA Admin Portal via your assigned cloud.
When the Sign In page appears:
-
Enter your** Login ID** and select the **Remember my Login ID** checkbox if you want the service to remember your username the next time you log in.
[See image.](#imagesignin)
- Click **Next**.
- Based on whether the ZIdentity service is enabled for the account or not, one of the following authentication flows appears:
- [For ZIdentity-enabled account](#zidentity-enabled)
- [For account without ZIdentity](#without-zidentity)
[]![Screenshot of ZIA Admin Portal Sign In page](/downloads/zia/getting-started/admin-portal/about-zia-admin-portal/ZIA-6.2r-Sign-In-Page_0.png)
If an admin account makes 5 unsuccessful attempts to log in within one minute, the account is locked out for 5 minutes and the failed attempts are recorded in the audit log. The audit logs are stored for up to 6 months.
To access the Admin Portals of two different Zscaler services simultaneously, you must either use a private browser or open them on different browsers. If you access the Admin Portals of multiple Zscaler services on different tabs of the same browser, the first accessed UI session is automatically redirected to the Admin Portal of the latest accessed service.
For example, if you log in to the ZIA Admin Portal on one tab of your browser and later log in to the ZDX Admin Portal on a different tab of the same browser, then the tab logged into the ZIA Admin Portal automatically redirects you to the most recently accessed ZDX Admin Portal.
With ZIdentity
If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zidentity-landing)
- Click the **Zscaler Internet Access** tile to access the ZIA Admin Portal. If you have multiple tenants provisioned to the ZIA service, click on the ZIA service access tile for the tenant that you want to access.
[See image.](#zidentity-landing-page)
You are redirected to the ZIA Admin Portal.
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
[]![Image of the ZIA Admin Portal tile in ZIdentity](/downloads/zia/getting-started/admin-portal/about-zia-admin-portal/ZIA-ZIdentity-landing-page-zia.png)
[]The Zscaler service redirects you to the ZIdentity authentication page.
Based on your organization's authentication preference, sign in to the ZIdentity service using one of the following methods:
- [Password](#password1)
- [Multi-Factor Authentication (MFA)](#mfa1)
- [Email One-Time Password (OTP)](#email-otp1)
- [Security Key or Biometric](#security-key-biometric1)
After a successful authentication by the ZIdentity service, you're redirected to the ZIdentity Admin Portal.
[]Enter your **Password **and click **Sign In**. If you forget your password, click **Having trouble signing in? **> **Reset Password**, and a reset email is sent to your email ID. The password reset link within the email expires after 5 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
- []Enter your **Password **and click **Sign In**.
- Based on your organization's MFA policy, two-factor authentication (2FA) is required. Complete your 2FA to access the ZIdentity Landing Page.
If you forget your password or want to configure a different secondary authenticator, click **Having trouble signing in? **> **Reset Password **or** Reset Second Factor**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
If your account is configured with MFA, you can sign in using a email OTP as well:
- []Click **Email OTP**.
- Enter the OTP received to your email address and click **Sign In**. The OTP expires after two minutes. If the OTP expires or you don't receive an OTP, click **Resend **to receive another OTP after 60 seconds.
- []Select **Sign-in using Security Key or Biometric**.
- Click** Next**.
- Based on your configuration, enter your security key or complete the biometric to access the ZIdentity Landing Page.
If you want to configure with a different security key or biometric, click **Having trouble signing in? **> **Reset Security Key or Biometric**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
[]The Password page appears.
- In the **Password For** field, enter your ZIA Admin Portal password.
-
Click **Sign In**.
Click **Back **if you want to go back to the Sign In page.
After a successful authentication by the ZIA service, you're logged into the ZIA Admin Portal.
[]When you log in for the first time, the ZIA Admin Portal displays EUSA. To learn more, see [Accepting the End User Subscription Agreement (EUSA)](/zia/accepting-end-user-subscription-agreement-eusa).
[]The ZIA Admin Portal has the following items in the left-side navigation:
- [Dashboard](#dashboard)
- [Analytics](#analytics)
- [Policy](#policy)
- [Administration](#administration)
- [Activation](#activation)
- [Search](#search)
- [Alerts](#alerts)
- [Notification](#notification)
- [Profile](#profile)
- [Help](#help)
- [Log Out](#logout)
![ZIA Admin home screen](/downloads/zia/getting-started/admin-portal/about-zia-admin-portal/ZIA-navigation-bar.png)
[]Click **Dashboard** to view the different dashboards for the ZIA Admin Portal. To learn more, see [About Dashboards](/zia/about-dashboards).
[]Click **Analytics** to view and analyze **Insights**, **Insights Logs**, and** Reports** for your organization's traffic.
To learn more about Analytics, see:
- [About Insights](/zia/about-insights)
- [About Insights Logs](/zia/about-insights-logs)
[]Click the **Policy **menu** **to apply various security access policy controls on the **Web**, **SaaS Security API**, **Mobile **and **Firewall Filtering**. To learn more, see [ZIA Policies](/zia/policies).
[]Click the **Administration** menu to apply the various administration controls such as **Settings**, **Authentication**, and **Resources.** To learn more, see [Administrator & Role Management](/zia/authentication-administration/administrator-role-management).
[]Hover over the **Profile** to view your Username, Organization ID and to select a color theme for your ZIA Admin Portal. Click the **Profile** to customize your account settings on the **My Profile** page. To learn more, see [Customizing your Admin Account Settings](/zia/customizing-your-admin-account-settings).
[]Click** Activation** to activate saved changes and to view the activation status. To learn more, see [Saving and Activating Changes in the ZIA Admin Portal](/zia/saving-and-activating-changes-admin-portal).
[]Click **Alerts** to view all the ongoing alerts within your organization. To learn more, see [About Security Alerts.](/zia/about-security-alerts)
[]Click the **Help** icon to view the menu. From this menu, you can do the following:
- **Remote Assistance**: If you need Zscaler Support engineers to securely and remotely log in to your ZIA Admin Portal for troubleshooting purposes, you can update this setting. To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).
- **Zscaler Help Portal**: This will redirect you to the Help Portal, where you can find documentation that provides background information, as well as configuration guides about ZIA and other Zscaler products.
- **Submit a Ticket**: This redirects you to the ZIA Support Portal where you can submit help request tickets to Zscaler Support.
- **Cloud Configuration Requirements**: This redirects you to the Zscaler cloud configuration requirements page for your account.
- **Threat Library**: This redirects you to the [Zscaler Threat library](https://threatlibrary.zscaler.com) page, where you can browse the Zscaler ThreatlabZ listing of threats to find more information about specific threats.
- **Zulu**: This redirects you to [Zscaler Zulu URL Risk Analyzer,](https://zulu.zscaler.com/) which is a dynamic risk scoring engine for web account content.
- **ThreatLabz (Security Research)**: This redirects you to the [Security Research](https://www.zscaler.com/blogs/security-research) page in the Zscaler company blog.
- **Proxy Test**: This redirects you to [https://ip.zscaler.com](https://ip.zscaler.com) where you can check if your traffic is going to the Zscaler service. You can also see information about the Zscaler cloud to which the device is sending its traffic.
- **URL Lookup**: View how Zscaler classifies a site according to its URL or IP address. To learn more, see [Looking Up URLs in the ZIA Admin Portal](/zia/lookup-urls-admin-portal).
- **Denylist IP Check**: Check if the Zscaler service is placing service access from an IP address on the denylist, due to suspicious traffic activity. To learn more, see [Checking for IP Addresses on the Denylist](/zia/checking-ip-addresses-on-denylist).
- **Zscaler Analyzer**: Use the Zscaler Analyzer app to perform an MTR (My Traceroute), and send the results to Zscaler Support. To learn more, see [About Zscaler Analyzer](/zia/about-zscaler-analyzer).
[]Click the **Notification **menu** **to view notifications. To learn more, see [About Notification](/zia/about-notification).
[]Click the **Log Out** icon to log out of the ZIA Admin Portal when you are done. If you are inactive for 15 minutes, the Admin Portal automatically logs you out.
[]Click the **Search** icon to search for sections within the ZIA Admin Portal. To learn more, see [Searching in the ZIA Admin Portal](/zia/searching-admin-portal).
[]During the scheduled maintenance and regular upgrade periods, the ZIA Admin Portal is in read-only mode. You can view the [Dashboard ](/zia/about-zia-admin-portal#dashboard)content and navigate through the [ZIA Admin Portal](/zia/about-zia-admin-portal#navigating-zia-admin-portal) to view various details.
You cannot configure or edit any parameters when the Admin Portal is in read-only mode. After the upgrade is complete, the Admin Portal automatically refreshes and enables editing.
When you are ready to begin configuring ZIA, see the [Step-by-Step Configuration Guide for ZIA](/zia/step-step-configuration-guide-zia).