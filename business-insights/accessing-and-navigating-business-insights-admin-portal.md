# Accessing and Navigating the Business Insights Admin Portal
Source: https://help.zscaler.com/business-insights/accessing-and-navigating-business-insights-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1473091.pdf

This article covers the following topics:
- [Accessing the Business Insights Admin Portal](#accessanagementportal)
- [Accepting the End User Subscription Agreement (EUSA)](#accept-eusa)
- [Navigating within the Business Insights Admin Portal](#navigating-portal)
[]Zscaler Support configures a super admin role, which has access to all the functions in the Business Insights Admin Portal, and emails you requesting the password to be set for that role. After you set the password, take note of your login ID used for accessing the [Business Insights Admin Portal](https://admin.zscaleranalytics.net/).
When the Sign In page appears:
-
Enter your** Login ID** and select the **Remember my Login ID** checkbox if you want the service to remember your username the next time you log in.
[See image.](#business-insights-sign-in)
- Click **Next**.
- Select the Zscaler cloud from the **Select Cloud App Tenant** drop-down menu.
- Based on whether the ZIdentity service is enabled for the account or not, one of the following authentication flows appears:
- [For ZIdentity-Enabled Account](#zidentity-enabled)
- [For Account Without ZIdentity](#without-zidentity)
With ZIdentity
If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zidentity-landing)
- Click the **Business Insights** tile to access the Business Insights Admin Portal. If you have multiple tenants provisioned to the Business Insights service, click on the Business Insights service access tile for the tenant that you want to access.
[See image.](#business-insights-tile)
You are redirected to the Business Insights Admin Portal.
[]When you log in for the first time, the Business Insights Admin Portal displays a EUSA. Click **Accept** to accept the EUSA.
If you don't accept EUSA, the service logs you out of the Business Insights Admin Portal.
![EUSA for Business Insights Admin Portal](/downloads/tech-pubs-drafts/business-insights-draft-articles/accessing-and-navigating-business-insights-admin-portal-doc-55713/Business-Inisghts-EUSA.png)
You can read the full EUSA at [https://www.zscaler.com/legal/end-user-subscription-agreement](https://www.zscaler.com/legal/end-user-subscription-agreement).
[]The Business Insights Admin Portal has the following items in the left-side navigation:
- [Search](#search)
- [Applications](#application)
- [Workspace](#workspace)
- [Reports](#reports)
- [Administration](#admin)
- [Notifications](#notification)
- [Account](#accounts)
- [Help](#help)
- [Log Out](#logout)
Use the arrow at the bottom to show or hide the left-side navigation.
![Business Insights Left-Side Navigation](/downloads/business-insights/getting-started/admin-portal/accessing-and-navigating-business-insights-admin-portal/Business-Insights-left-navigation%20(1).png)
[]Search for an item in the left-side navigation.
[]Click **Application **to view application insights for discovered, connected, and overlapping apps, as well as their cost-saving opportunities. To learn more, see:
- [About Application Insights](/business-insights/about-application-inventory)
- [About All Applications](/business-insights/about-all-applications)
- [About Application Configuration](/business-insights/about-application-configuration)
[]Click **Workplace** to view insights and monitor your workplace. To learn more, see:
- [Analyzing Workplace Insights](/business-insights/analyzing-workplace-insights)
- [About Offices and Locations](/business-insights/about-offices-and-locations)
- [About Department Mapping](/business-insights/about-department-mapping)
- [About Configured Offices](/business-insights/about-configured-offices)
[]Click **Reports **to download your Business Insights analysis report or schedule a report. To learn more, see:
- [Downloading Business Insights Reports](/business-insights/downloading-business-insights-reports).
- [About Scheduled Reports](/business-insights/about-scheduled-reports)
[]Click **Administration **to manage your admins, their roles, view user accounts, and audit logs. To learn more, see:
- [Understanding Administrator Management Settings](/business-insights/understanding-administrator-management-settings-business-insights)
- [About Role Management](/business-insights/about-role-management-business-insights)
- [About Audit Logs](/business-insights/about-audit-logs-business-insights)
- [Integrating a SaaS Application for Workflow Automation](/business-insights/integrating-saas-application-workflow-automation)
[]Click **Notifications** to view any new notifications within the Business Insights Admin Portal.
[]Click **Account** to view your username, cloud name, and organization ID. You can also change your password on this page. To learn more, see [Managing Your Admin Account](/business-insights/managing-your-admin-account).
[]Click **Help** to enable remote assistance for your Business Insights Admin Portal. To learn more, see [Enabling Remote Assistance](/business-insights/enabling-remote-assistance-business-insights).
[]Click **Logout** to log out of the Business Insights Admin Portal when you are done.
[]The Zscaler service redirects you to the ZIdentity authentication page.
Based on your organization's authentication preference, sign in to the ZIdentity service using one of the following methods:
- [Password](#password1)
- [Multi-Factor Authentication (MFA)](#mfa1)
- [Email One-Time Password (OTP)](#email-otp1)
- [Security Key or Biometric](#security-key-biometric1)
After a successful authentication by the ZIdentity service, you're redirected to the Business Insights Admin Portal.
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
[]The Password page appears.
- In the **Password **field, enter your Business Insights Admin Portal password.
-
Click **Sign In**.
Click **Back **if you want to go back to the Sign In page.
After a successful authentication by the Business Insights service, you're logged in to the Business Insights Admin Portal.
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
[]![Business Insights Sign In Page](/downloads/business-insights/getting-started/admin-portal/accessing-and-navigating-business-insights-admin-portal/Business-Insights-Sign-In-Page.png)
[]![Business Insights Tile in ZIdentity Landing Page](/downloads/business-insights/getting-started/admin-portal/accessing-and-navigating-business-insights-admin-portal/ZIdentityLanding-Page-Business-Insights-Tile.png)