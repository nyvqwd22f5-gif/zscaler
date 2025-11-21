# Accessing and Navigating the Risk360 Admin Portal
Source: https://help.zscaler.com/risk360/accessing-and-navigating-risk-360-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1452796.pdf

This article covers the following topics:
- [Accessing the Risk360 Admin Portal](#accessanagementportal)
- [Navigating within the Risk360 Admin Portal](#navigating-portal)
[]To access the Risk360 Admin Portal:
- Open the [Risk360 Admin Portal](https://admin.zscalerrisk.net/) in your browser.
-
Enter your** Login ID** and select the **Remember my Login ID** checkbox if you want the service to remember your username the next time you log in.
[See image.](#risk360-sign-in-page)
- Click **Next**.
- Based on whether the ZIdentity service is enabled for the account or not, one of the following authentication flows appears:
- [For ZIdentity-Enabled Account](#ZIdentity-enabled)
- [For Account Without ZIdentity](#without-ZIdentity)
With ZIdentity
If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-ZIdentity-landing)
- Click the **Risk360** tile to access the Risk360 Admin Portal. If you have multiple tenants provisioned to the Risk360 service, click on the Risk360 service access tile for the tenant that you want to access.
[See image.](#risk360-tile)
You are redirected to the Risk360 Admin Portal.
[]The Risk360 Admin Portal has the following items in the left-side navigation:
- [Search](#search-items)
- [Dashboard](#dashboard)
- [Factors](#factors)
- [Assets](#assets)
- [Insights](#insights)
- [Financial Risk](#financial-risk)
- [Frameworks](#framework)
- [Reports](#reports)
- [Administration](#administration)
- [Alerts](#alerts)
- [EASM](#easm)
- [My Profile](#my-profile)
- [Help](#help-risk)
- [Log Out](#log-out)
You can also search for an item using the Search field at the top.
![The Risk360 Admin Portal](/downloads/risk360/getting-started/admin-portal/accessing-and-navigating-risk-360-admin-portal/RIsk360-Left-Nav.png)
A few items are populated after clicking on any of the Administration pages. The left-side navigation is updated to show the following additional items:
- [Activation](#activation)
- [Search](#search)
- [Risk360 Home](#riskhome)
- [Notification](#notification)
- [Profile](#profile)
- [Help](#help)
![The Risk360 Admin Portal](/downloads/risk360/getting-started/admin-portal/accessing-and-navigating-risk-360-admin-portal/Risk360-tleft-navigation-admin.png)
[]Search for items within the left-side navigation.
[]Click **Dashboard** to view various risk scores and trends for your organization. To learn more, see [About Dashboard](/risk360/about-dashboard-risk360).
[]Click **Factors **to view the factors affecting your organization's risk score. To learn more, see [About Risk360 Factors](/risk360/about-factors).
[]Click **Assets **to view risk scores, trends, and more for your organization's assets. To learn more, see [About Asset-Level Risk](/risk360/about-asset-level-risk).
[]Click **Insights **to view the problems discovered within your organization that are impacting your risk score. To learn more, see [About Insights](/risk360/about-insights-risk360).
[]Click **Frameworks **to view various risk frameworks integrated with the Risk360 service. To learn more, see [Assessing Compliance](/risk360/assessing-compliance).
[]Click **Financial Risk **to view the metrics that are contributing to your organization's financial risk exposure. To learn more, see [About Financial Risk](/risk360/about-financial-risk).
[]Click **Administration **to manage your admins. To learn more, see:
- [Understanding Administrator Management Settings](/risk360/understanding-administrator-management-settings-risk360)
- [About Administrators](/risk360/about-administrators-risk360)
- &amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;!--td {border: 1px solid #cccccc;}br {mso-data-placement:same-cell;}--&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt;
[About Role Management](/risk360/about-role-management-risk360)
[]Click **Alerts **to configure alerts for various criteria. To learn more, see [About Alerts](/risk360/about-alerts).
[]Click **EASM** to access the EASM Admin Portal. To learn more, see [What is Zscaler EASM?](/easm/what-zscaler-easm)
[]Click **Reports **to download your Risk360 analysis report for the time period of your choice. To learn more, see [Downloading Risk360 Reports](/risk360/downloading-risk360-ciso-reports).
[]Click **Profile** to view your username, organization ID, cloud name, and current SKU. You can also change your password on the **My Profile** page. To learn more, see [Managing Your Admin Account](/risk360/managing-your-admin-account).
[]Click **Help** to view the help menu. From this menu, you can do the following:
- **Zscaler Help Portal**: This redirects you to the Help Portal, where you can find documentation that provides background information, as well as configuration guides about Risk360 and other Zscaler products.
- **Submit a Ticket**: This redirects you to the Risk360 Support Portal where you can submit help tickets to Zscaler Support.
- **Remote Assistance**: If you need Zscaler Support engineers to securely and remotely log in to your Risk360 Admin Portal for troubleshooting purposes, you can update this setting.
[]Click **Logout** to log out of the Risk360 Admin Portal when you are done.
[]Click the **Notification **icon** **to view notifications.
[]Hover over the **Profile** icon to view your username, organization ID, and to select a color theme for your Risk360 Admin Portal. Click the **Profile **icon to customize your account settings on the **My Profile** page. To learn more, see [Customizing Your Admin Account Settings](/risk360/customizing-your-admin-account-settings).
[]Click the **Help** icon to view the help menu. From this menu, you can do the following:
- **Remote Assistance**: If you need Zscaler Support engineers to securely and remotely log in to your Risk360 Admin Portal for troubleshooting purposes, you can update this setting.
- **Zscaler Help Portal**: This redirects you to the Help Portal, where you can find documentation that provides background information, as well as configuration guides about Risk360 and other Zscaler products.
- **Submit a Ticket**: This redirects you to the Risk360 Support Portal where you can submit help tickets to Zscaler Support.
[]Click** Activation** to activate saved changes and to view the activation status. To learn more, see [Saving and Activating Changes in the Portal](/risk360/accessing-and-navigating-risk-360-admin-portal).
[]Click the **Search** icon to search for sections within the Risk360 Admin Portal. To learn more, see [Searching in the Risk360 Admin Portal](/risk360/searching-risk360-admin-portal).
[]Click **Risk360 Home **to navigate back to Risk360 analytic pages (i.e., Dashboard, Factors, Insights, etc.).
[]The Zscaler service redirects you to the ZIdentity authentication page.
Based on your organization's authentication preference, sign in to the ZIdentity service using one of the following methods:
- [Password](#password1)
- [Multi-Factor Authentication (MFA)](#mfa1)
- [Email One-Time Password (OTP)](#email-otp1)
- [Security Key or Biometric](#security-key-biometric1)
After a successful authentication by the ZIdentity service, you're redirected to the ZIdentity Admin Portal.
[]Enter your **Password **and click **Sign In**. If you forget your password, click **Having trouble signing in? **> **Reset Password**, and a reset email is sent to your email ID. The password reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/zidentity/1.0/resetting-login-credentials-mfa).
- []Enter your **Password **and click **Sign In**.
- Based on your organization's MFA policy, two-factor authentication (2FA) is required. Complete your 2FA to access the ZIdentity Landing Page.
If you forget your password or want to configure a different secondary authenticator, click **Having trouble signing in? **> **Reset Password **or** Reset Second Factor**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/zidentity/1.0/resetting-login-credentials-mfa).
If your account is configured with MFA, you can sign in using a email OTP as well:
- []Click **Email OTP**.
- Enter the OTP received to your email address and click **Sign In**. The OTP expires after two minutes. If the OTP expires or you don't receive an OTP, click **Resend **to receive another OTP after 60 seconds.
- []Select **Sign-in using Security Key or Biometric**.
- Click** Next**.
- Based on your configuration, enter your security key or complete the biometric to access the ZIdentity Landing Page.
If you want to configure with a different security key or biometric, click **Having trouble signing in? **> **Reset Security Key or Biometric**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/zidentity/1.0/resetting-login-credentials-mfa).
[]The Pasword page appears.
- In the **Password for **field, enter your Risk360 Admin Portal password.
-
Click **Sign In**.
Click **Back **if you want to go back to the Sign In page.
After a successful authentication by the Risk360 service, you're logged in to the Risk360 Admin Portal.
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
[]![Risk360 Service Tile in ZSLogin Landing Page](/downloads/risk360/getting-started/admin-portal/accessing-and-navigating-risk-360-admin-portal/ZIdentityLanding-Page-Risk360-Tile.png)
[]![Risk360 Sign In Page](/downloads/risk360/getting-started/admin-portal/accessing-and-navigating-risk-360-admin-portal/Risk360-sign-in-page.png)