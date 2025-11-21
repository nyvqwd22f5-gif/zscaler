# Accessing and Navigating the Workflow Automation Admin Portal
Source: https://help.zscaler.com/workflow-automation/accessing-and-navigating-workflow-automation-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1417961.pdf

Data Protection integration with Workflow Automation is enabled when you subscribe to Data Loss Prevention (DLP). If you have subscriptions to integrated applications of Workflow Automation such as Business Insights and Zscaler Digital Experience (ZDX), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. To manage and configure automated workflows for DLP incidents, select **Data Protection**.
This article covers the following topics:
- [Accessing the Workflow Automation Admin Portal](#Access-ZWA)
- [Navigating within the Workflow Automation Admin Portal](#Navigating-ZWA-Admin-Portal)
When you're ready to begin configuring Workflow Automation, see the [Step-by-Step Configuration Guide for Workflow Automation](/zia/step-step-configuration-guide-workflow-automation).
[]Log in to the Workflow Automation Admin Portal to access the DLP incidents through one of the following Zscaler Admin Portals:
- [ZIA Admin Portal](#zia-admin-portal-access)
- [ZIdentity Admin Portal](#access-zidentity)
[]After the admins in your organization are provisioned for Workflow Automation in the ZIA Admin Portal, they can access the Workflow Automation Admin Portal. To access the Workflow Automation Admin Portal, in the ZIA Admin Portal, go to **Administration** > **Workflow Automation**. You are transferred to the Workflow Automation Admin Portal.
[See image.](#Login-Navigation)
[]If you're subscribed to ZIdentity:
- [Log in to the ZIdentity Landing Page.](#access-zidentity-landing)
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
[See image.](#currently-you-are-viewing-option)
[]The Workflow Automation Admin Portal has the following items in the left-side navigation:
- [Dashboard](#dashboard)
- [Incidents](#Incidents)
- [Setup](#setup)
- [Incident Group](#Incident-Group)
- [Workflows](#Workflows)
- [My Activity](#my-activity)
- [Notifications](#Notifications)
- [Profile](#Profile-Icon)
- [Log Out](#LogOut)
![Navigating the Workflow Automation Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal/WA-Accessing-Navigating-Menu.png)
[]Click **Dashboard** to access the Incident Analytics dashboard. The Incident Analytics dashboard gives high-level visibility and insight into your organization's Data Loss Prevention (DLP) incidents. To learn more, see [About Incident Analytics Dashboard](/workflow-automation/about-incident-analytics-dashboard).
[]Click **Incidents** to view and manage the different incidents for your organization. To learn more, see the following articles:
- [About Incidents](/zia/about-incidents)
- [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details)
- [Responding to an End User Notification](/zia/responding-end-user-notification)
- [Responding to an Escalation Notification](/zia/responding-escalation)
- [Responding to a User Digest Notification](/zia/responding-user-digest-notification)
- [Responding to a DLP Admin Digest Notification](/zia/responding-dlp-admin-digest-notification)
[]Click **Setup** to access the pages where you can configure initial settings for Workflow Automation, such as application and user integrations. To learn more, see the following articles:
- [Managing Admin Assignments](/workflow-automation/managing-admin-assignments)
- [Managing Roles and Permissions](/workflow-automation/managing-roles-and-permissions)
- [Managing Priorities](/zia/managing-priorities)
- [Managing Approvers](/zia/managing-approvers)
- [Configuring the DLP Application Integration Using Amazon Web Services](/zia/configuring-dlp-application-integration-using-amazon-web-services)
- [Configuring the DLP Application Integration Using Azure](/zia/configuring-dlp-application-integration-using-azure)
- [Managing DLP AWS Application Integrations in Workflow Automation](/zia/managing-dlp-application-integrations-workflow-automation)
- [Managing DLP Azure Application Integrations in Workflow Automation](/zia/managing-dlp-azure-application-integrations-workflow-automation)
- [Managing Workflow Automation Integration with Slack](/zia/managing-workflow-automation-integration-slack)
- [Managing Workflow Automation Integration with Microsoft Teams](/zia/managing-workflow-automation-integration-microsoft-teams)
- [Managing Workflow Automation Integration with ServiceNow](/zia/managing-workflow-automation-integration-servicenow)
- [Managing Workflow Automation Integration with Jira Software](/zia/managing-workflow-automation-integration-jira-software)
- [Managing Notification Templates](/zia/managing-notification-templates)
- [Managing Survey Templates](/zia/managing-survey-templates)
- [Managing Incident and Digest Template Mappings](/zia/managing-incident-and-digest-template-mappings)
- [Managing Account Settings](/zia/managing-account-settings)
- [Managing User Attributes](/workflow-automation/managing-user-attributes)
- [Managing Integration Users](/zia/managing-integration-users)
- [Managing Labels](/zia/managing-labels)
- [About API Keys](/zia/about-api-keys)
- [Managing Workflow Automation API Keys](/zia/managing-workflow-automation-api-keys)
- [Managing Custom Email Domains](/workflow-automation/managing-custom-email-domains)
- [About Audit Logs in Workflow Automation](/zia/about-audit-logs-in-workflow-automation)
[]Click **Incident Group** to add and map incident groups for your organization. To learn more, see the following articles:
- [Managing Incident Groups](/zia/managing-incident-groups)
- [Managing Incident Group Mappings](/zia/managing-incident-group-mappings)
[]Click **Workflows** to view the predefined workflow templates and to add and map workflows for your organization. To learn more, see the following articles:
- [Managing Workflow Templates](/zia/managing-workflow-templates)
- [Managing Workflows](/zia/managing-workflows)
- [Managing Workflow Mappings](/zia/managing-workflow-mappings)
[]Click the **Notifications** icon to view the alert notifications about problems that are affecting the operation of Workflow Automation. To learn more, see [Viewing Alert Notifications](/zia/viewing-notifications).
[]Click the **Profile** icon to view your username.
[]When you are done, click the **Log Out **icon to log out of the Workflow Automation Admin Portal.
[]Click **My Activity **to view the **Downloads** and **Bulk Actions** pages. These pages allow you to track the status of your incident file downloads and bulk actions performed on the [Incidents](/workflow-automation/about-incidents) page, respectively. To learn more, see the following articles:
- [Managing Downloads](/workflow-automation/managing-downloads)
- [Managing Bulk Actions](/workflow-automation/managing-bulk-actions)
![Screenshot of the Currently you are viewing drop-down menu in the Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal/WA-Currently-Viewing-Option.png)
[]
![Screenshot of the ZIdentity landing page with the Workflow Automation tile](/downloads/workflow-automation/getting-started/admin-portal/WA-ZIdentity-login-landing-page.png)
[]
[]![Viewing the Workflow Automation landing page with the product tiles displayed for accessing Data Protection, Digital Experience Monitoring (ZDX), and Business Insights.](/downloads/workflow-automation/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal/WA-Workflow-Automation-Product-Tiles.png)
[]![Navigation to Workflow Automation from the ZIA Admin Portal](/downloads/workflow-automation/getting-started/admin-portal/accessing-and-navigating-workflow-automation-admin-portal/WA-ZIA-Navigation-To-Workflow-Automation.png)