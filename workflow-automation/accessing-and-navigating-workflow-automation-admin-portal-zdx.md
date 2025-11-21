# Accessing and Navigating the Workflow Automation Admin Portal for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-zdx
PDF: https://help.zscaler.com/pdf/com/en/1487441.pdf

If you are subscribed to ZDX Advanced Plus, Zscaler Digital Experience (ZDX) integration with Workflow Automation is automatically enabled. To learn more, contact Zscaler Support. If you have subscriptions to integrated applications of Workflow Automation such as Data Loss Prevention (DLP), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. To configure automated workflows for the ZDX alerts, select Zscaler Digital Experience (ZDX).
This article covers the following topics:
- [Accessing the Workflow Automation Admin Portal](#accessing-admin-portal)
- [Navigating within the Workflow Automation Admin Portal](#navigation)
When you're ready to begin configuring Workflow Automation, see the [Step-by-Step Configuration Guide for Workflow Automation](/workflow-automation/step-step-configuration-guide-workflow-automation-zdx).
[]You can log in to the Workflow Automation Admin Portal to configure workflows for ZDX alerts through one of the following Zscaler Admin Portals:
- [ZDX Admin Portal](#access-zdx)
- [ZIdentity Admin Portal](#access-zidentity)
[]After the admins are provisioned for Workflow Automation in the ZDX Admin Portal, they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal, in the ZDX Admin Portal, go to **Administration** > **Workflow Automation**. You are redirected to the Workflow Automation Admin Portal.
[See image.](#zdx-wa-navigation)
[]If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zslogin-landing)
-
Click the** Zscaler Workflow Automation **tile to access the Workflow Automation Admin Portal.
[See image.](#zidentity-landing-page-image)
You are redirected to the Workflow Automation Admin Portal.
-
Select the appropriate product tile to proceed into the Workflow Automation Admin Portal.
[See image.](#workflow-automation-product-selection-tiles)
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
If you have subscriptions to multiple integrated applications of Workflow Automation, the current application you are using is shown at the top of the Workflow Automation Admin Portal. You can use the **Currently you are viewing** drop-down menu to view another integrated application.
[See image.](#currently-you-are-viewing-drop-down)
[]The Workflow Automation Admin Portal has the following items in the left-side navigation:
- [Setup](#setup)
- [Workflows](#Workflows)
- [Profile](#Profile-Icon)
- [Log Out](#LogOut)
![The Workflow Automation Admin Portal displaying the left-side navigation and menu items. Menu items are Setup tab, Workflows tab, Profile icon, and Log Out icon.](/downloads/workflow-automation/zscaler-digital-experience/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-zdx/WA-ZDX-Accessing-Navigating-Admin-Portal-Menu.png)
[]Click **Setup** to access the pages where you can configure initial settings for Workflow Automation, such as application and user integrations. To learn more, see the following articles:
- [Managing Workflow Automation Integration with ServiceNow](/workflow-automation/managing-servicenow-integration-zdx-alerts)
- [Managing Integration Users](/workflow-automation/draft-managing-integration-users-zdx-alerts)
[]Click **Workflows** to view the predefined workflow templates and to add and map workflows for your organization. To learn more, see the following articles:
- [Managing Workflow Templates for ZDX Alerts](/workflow-automation/managing-workflow-templates-zdx-alerts)
- [Managing Workflows for ZDX Alerts](/workflow-automation/managing-workflows-zdx-alerts)
- [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts)
- [Managing Shared Configuration for ZDX Alerts](/workflow-automation/managing-shared-configuration-zdx)
[]Click the **Profile** icon to view your username.
[]Click the **Log Out **icon to log out of the Workflow Automation Admin Portal when you are done.
![Navigating to the Workflow Automation Admin Portal from the ZDX Admin Portal](/downloads/zia/workflow-automation/getting-started/Accessing%20and%20Navigating%20the%20Workflow%20Automation%20Admin%20Portal/WA-navigation-ZDX.png)
[]
![Screenshot of the ZIdentity landing page with Workflow Automation tile](/downloads/workflow-automation/zscaler-digital-experience/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-zdx/WA-zdx-ZIdentity-login-landing-page.png)
[]
[]![Viewing the Workflow Automation landing page with the product tiles displayed for accessing Data Protection, Digital Experience Monitoring (ZDX), and Business Insights.](/downloads/workflow-automation/zscaler-digital-experience/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-zdx/WA-Workflow-Automation-Product-Tiles-ZDX.png)
![The Workflow Automation Admin Portal displaying the Currently you are viewing drop-down menu](/downloads/workflow-automation/zscaler-digital-experience/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-zdx/WA-ZDX-Currently-You-Are-Viewing-Menu.png)
[]