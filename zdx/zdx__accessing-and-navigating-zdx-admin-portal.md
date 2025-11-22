# Accessing and Navigating the ZDX Admin Portal
Source: https://help.zscaler.com/zdx/accessing-and-navigating-zdx-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1355866.pdf

This article covers the following topics:
- [Signing In to the ZDX Admin Portal](#LoggingIn)
- [Accepting the End User Subscription Agreement (EUSA)](#AcceptEUSA)
- [Navigating within the ZDX Admin Portal](#NavigatingZDXAdminPortal)
[]After your organization is provisioned for ZDX, you can access the [ZDX Admin Portal](https://admin.zdxcloud.net).
When the Sign In page appears:
-
Enter your **Login ID **and your credentials as required.
If ZIdentity is enabled for ZDX, the login process changes to:
- Enter Login ID and then click **Next**.
- After a redirection to the ZIdentity Landing page, enter credentials as required.
- Click **Next**.
- If your organization has tenants provisioned on multiple Zscaler clouds, a drop-down menu displays the available clouds to choose from. Click the drop-down arrow for **Select Cloud App Tenant**, and select the cloud you want to probe.
- Click **Submit**.
[See image.](#select-cloud-app-tenant)
With ZIdentity
If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zslogin-landing)
-
Click the **Zscaler Digital Experience** tile to access the ZDX Admin Portal.
[See image.](#zslogin-selectZDX)
You are redirected to the ZDX Admin Portal.
[]![Select ZDX from the ZIdentity Admin Portal](/downloads/zdx/getting-started/admin-portal/about-zdx-admin-portal/zidentity-landing-page.png)
If your login attempt fails more than three times, your account is locked for 30 minutes. Any ZDX admin can reset your password during this time.
To simultaneously access the Zscaler Admin Portal of two different Zscaler services, you must either use a private browser or open each Zscaler service on different browsers. If you access the Admin Portals of multiple Zscaler services on different tabs of the same browser, the first accessed UI session is automatically redirected to the Admin Portal of the latest accessed service.
For example, if you log in to the ZDX Admin Portal on one tab of your browser and later log in to the ZIA Admin Portal on a different tab of the same browser, then the tab logged into the ZDX Admin Portal automatically redirects you to the most recently accessed ZIA Admin Portal.
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
[]
[![Select Cloud App Tenant](/downloads/zdx/getting-started/admin-portal/about-zdx-portal/ZDX_login_select-cloud-app-tenant_squircle_cropped.png)
]
[]When you log in for the first time, the ZDX Admin Portal displays a EUSA. Click **Accept** to accept the EUSA.
If you click **Cancel**, you have read-only access in the portal until one admin per organization accepts it. A reminder also appears at the top of the portal every time you log in until an admin accepts the EUSA.
![Accessing the EUSA in the ZDX Portal](/downloads/zdx/getting-started/admin-portal/accessing-and-navigating-zdx-admin-portal/zdx-accessingandnavigatingzdxadminportal-EUSA_0.jpg)
To access the EUSA if you did not accept it the first time, click the reminder notification. The EUSA appears and you can accept it. This notification disappears after the EUSA is accepted.
You can read the full EUSA at [https://www.zscaler.com/legal/end-user-subscription-agreement](https://www.zscaler.com/legal/end-user-subscription-agreement).
[]The ZDX Admin Portal has the following items in the left-side navigation:
![Navigation menu in the ZDX Admin Portal](/downloads/zdx/getting-started/admin-portal/accessing-and-navigating-zdx-admin-portal/zdx-accessingandnavigatingzdxadminportal-%20navigation-1.jpg)
- [Dashboard](#Dashboard)
- [Analytics](#Analytics)
- [Applications](#Applications)
- [Users](#Users)
- [Inventory](#Inventory)
- [Configuration](#Configuration)
- [Administration](#Administration)
- [Alerts](#Alerts)
- [Diagnostics](#Diagnostics)
- [Search](#Search)
- [Activation](#Activation)
- [Profile](#Profile)
- [Help](#help)
[]The **Dashboard** provides a list of dashboards, which is an overall summary of your organization's digital experience. To learn more about dashboards, see:
- [Monitoring the Performance](/zdx/monitoring-performance-dashboard)[ Dashboard](/zdx/monitoring-performance-dashboard)
- [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard)
- [Monitoring the Self Service Dashboard](/zdx/monitoring-self-service-dashboard)
[]Click **Applications** to view and filter the list of applications for your organization. To learn more, see [About Applications](/zdx/about-applications).
[]Click **Users** to view and filter data per user, such as device status and individual ZDX Scores. To learn more, see [Evaluating User Details](/zdx/evaluating-user-details).
[]Click **Diagnostics** to view the diagnostic sessions for your organization or configure a diagnostics session. To learn more, see [About Diagnostics](/zdx/about-diagnostics).
[]Click **Search** to find a user or device quickly. Enter the user name or device name. To learn more, see [Using Search in the ZDX Admin Portal](/zdx/using-search-zdx-admin-portal)[.]
[]Click **Administration** for access to **Administration Controls**, **Resources**, **Zscaler Portals**, **Integrations**, **Authentication**, and **Settings**.
- Administration Controls include:
- Administrator Management
- Role Management
- User Management
- Audit Logs
- Resources include:
- Location Management
- Labels
- Zscaler Portals include:
- Zscaler Client Connector Portal
-
Workflow Automation Admin Portal
If ZIdentity is enabled, the Portals do not appear under the Administration left-side navigation (Administration > Zscaler Portals). Instead, the Administration left-side navigation is replaced with ZIdentity. You can access the Zscaler Client Connector Portal or Workflow Automation Admin Portal from the ZIdentity Admin Portal. To learn more, see [Accessing and Navigating the ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page).
- Integrations for SaaS Applications tenants
- Authentication for API Key Management
- Settings include:
- Inventory
- Self Service
[See image.](#AdministrationMenu)
[]Click **Alerts** to create and manage alerts and rules. To learn more, see:
- [About Alerts](/zdx/about-alerts)
- [About Rules](/zdx/about-rules)
- [Configuring a Rule](/zdx/configuring-rule)
- [Editing a Rule](/zdx/editing-rule)
- [Configuring Webhooks](/zdx/configuring-webhooks)
- [Understanding the Alert Email](/zdx/understanding-alerts-email)
[]Click** Activation** (![Activate your changes](/downloads/zdx/getting-started/admin-portal/accessing-and-navigating-zdx-admin-portal/ZDX-Activation-small.png)
) to view the activation status and activate saved changes. To learn more, see [Saving and Activating Changes in the ZDX Admin Portal](/zdx/saving-and-activating-changes-admin-portal).
[]Click your **Profile** to view your account settings, such as **Username**, **Cloud**, and **Organization ID**. To learn more, see [Customizing Your Admin Account Settings](/zdx/customizing-your-admin-account-settings).
Click **Change Password** to change your ZDX Admin's password. If an update is made, this change applies to both the ZDX and ZIA Admin Portals.
Click **Log Out** to log out of the ZDX Admin Portal when you are done. If you are inactive for 15 minutes, you are automatically logged out.
[]Click **Help** to view the help settings menu. From this menu, you can **Submit a Ticket**. This redirects you to the Zscaler Support Portal where you can submit a help request ticket to Zscaler Support.
[]Click **Analytics** to view and analyze user, application, device, and ZDX Snapshots information. To learn more, see [Analytics](/zdx/analytics).
[]Click **Inventory** to view details about your organization's Software and Device Inventory information as well as processes that might be impacting the behavior of your users' devices. To learn more, see [Inventory](/zdx/analytics/inventory).
[]Click **Configuration** to create and manage applications and probes. To learn more, see the following articles:
- [Adding a Custom Application](/zdx/adding-custom-application)
- [Configuring a Predefined Application](/zdx/adding-predefined-application)
- [Editing an Application](/zdx/editing-application)
- [Configuring a Probe](/zdx/configuring-probe)
- [Editing a Probe](/zdx/editing-probe)
[]
![Administration Menu](/downloads/zdx/getting-started/admin-portal/accessing-and-navigating-zdx-admin-portal/ZDX-AdministrationMenu.png)
When you're ready to begin configuring ZDX, see the [Step-by-Step Configuration Guide for ZDX](/zdx/step-step-configuration-guide-zdx).