# Accessing and Navigating the Workflow Automation Admin Portal for Events
Source: https://help.zscaler.com/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal-events
PDF: https://help.zscaler.com/pdf/com/en/1500336.pdf

If you are subscribed to Business Insights, Business Insights integration with Workflow Automation is automatically enabled. If you have subscriptions to integrated applications of Workflow Automation such as Data Loss Prevention (DLP) and Zscaler Digital Experience (ZDX), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. To configure and manage your organization's SaaS application events, select Business Insights.
This article covers the following topics:
- [Accessing the Workflow Automation Admin Portal for Events](#Access-ZWA)
- [Navigating within the Workflow Automation Admin Portal for Events](#Navigating-ZWA-Admin-Portal)
When you're ready to begin configuring Workflow Automation, see the [Step-by-Step Configuration Guide for Workflow Automation for Events](/workflow-automation/step-step-configuration-guide-workflow-automation-events).
[]You can log in to the Workflow Automation Admin Portal to access the Business Insights events through one of the following Zscaler Admin Portals:
- [Business Insights Admin Portal](#business-insights-login)
- [ZIdentity Admin Portal](#access-zidentity)
[]After the admins in your organization are provisioned for Workflow Automation in the Business Insights Admin Portal, they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal, in the Business Insights Admin Portal, go to **Administration** > **Workflow Automation**.
[See image.](#Login-Navigation)
[]If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zslogin-landing)
-
Click the** Zscaler Workflow Automation **tile to access the Workflow Automation Admin Portal.
[See image.](#zidentity-landing-page-image)
You are redirected to the Workflow Automation Admin Portal.
-
Select the appropriate product tile to proceed into the Workflow Automation Admin Portal.
[See image.](#image-workflow-automation-product-tiles)
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
[See image.](#currently-you-are-viewing-menu)
[]The Workflow Automation Admin Portal has the following items in the left-side navigation:
- [Events](#events)
- [Setup](#setup)
- [Event Group](#event-Group)
- [Workflows](#Workflows)
- [Profile](#Profile-Icon)
- [Log Out](#LogOut)
![Viewing the left-side menu navigation for the Workflow Automation Admin Portal for Business Insights integration. The menu contains tabs for Events, Setup, Event Group, and Workflows. Plus, the Profile icon and the Log Out icon.](/downloads/workflow-automation/business-insights/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-events/WA-BI-Navigating-Admin-Portal.png)
[]Click **Events** to view and manage the different Business Insights events for your organization. To learn more, see the following articles:
- [Managing Events](/workflow-automation/managing-events)
- [Managing Event Details](/workflow-automation/managing-event-details)
- [Responding to an End User Notification for Events](/workflow-automation/responding-end-user-notification-events)
[]Click **Setup** to access the pages where you can configure initial settings for Workflow Automation, such as application and user integrations. To learn more, see the following articles:
- [Managing Integration Users for Events](/workflow-automation/managing-integration-users-events)
- [Adding Integrations for Events](/workflow-automation/adding-integrations-events)
- [Managing ServiceNow Integration for Events](/workflow-automation/managing-servicenow-integration-events)
- [Managing Priorities for Events](/workflow-automation/managing-priorities-events)
- [Managing Notification Templates for Events](/workflow-automation/managing-notification-templates-events)
- [Managing Survey Templates for Events](/workflow-automation/managing-survey-templates-events)
- [Managing Template Mappings for Events](/workflow-automation/managing-template-mappings-events)
[]Click **Event Group** to add and map event groups for your organization. To learn more, see the following articles:
- [Managing Event Groups](/workflow-automation/managing-event-groups)
- [Managing Event Group Mappings](/workflow-automation/managing-event-group-mappings)
[]Click **Workflows** to view the predefined workflow templates and to add and map workflows for your organization. To learn more, see the following articles:
- [Managing Workflow Templates for Events](/workflow-automation/managing-workflow-templates-events)
- [Managing Workflows for Events](/workflow-automation/managing-workflows-events)
- [Managing Workflow Mappings for Events](/workflow-automation/managing-workflow-mappings-events)
[]Click the **Profile** icon to view your username.
[]When you are done, click the **Log Out** icon to log out of the Workflow Automation Admin Portal.
![Viewing the Currently you are viewing drop-down menu on the top of the Workflow Automation Admin Portal](/downloads/workflow-automation/business-insights/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-events/WA-BI-Navigating-Admin-Portal-Currently-You-Are-Viewing-Menu.png)
[]
[]![Navigation to Workflow Automation from Business Insights](/downloads/workflow-automation/business-insights/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-events/WA-BI-accessing-admin-portal.png)
![Navigating to Workflow Automation from the ZIdentity landing page. The ZIdentity landing page has tiles for Trust Portal, Zscaler Digital Experience, Business Insights, Zscaler Workflow Automation, ZIdentity Administration, and Zscaler Internet Access.](/downloads/workflow-automation/business-insights/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-events/WA-BI-ZIdentity-login-landing-page.png)
[]
[]![Viewing the Workflow Automation landing page with the product tiles displayed for accessing Data Protection, Digital Experience Monitoring (ZDX), and Business Insights.](/downloads/workflow-automation/business-insights/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal-events/WA-Workflow-Automation-Product-Tiles-BI.png)