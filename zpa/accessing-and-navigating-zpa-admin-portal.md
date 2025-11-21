# Accessing and Navigating the ZPA Admin Portal
Source: https://help.zscaler.com/zpa/accessing-and-navigating-zpa-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1483521.pdf

This article covers the following topics:
- [Signing In to the ZPA Admin Portal](#LoggingIn)
- [Accepting the End User Subscription Agreement (EUSA)](#ZPA_EUSA)
- [Navigating Within the ZPA Admin Portal](#NavigatingZPAAdminPortal)
When you are ready to begin configuring ZPA, see the [Step-by-Step Configuration Guide for ZPA](/zpa/step-step-configuration-guide-zpa).
[]After your organization is provisioned with a ZPA cloud, you are assigned to a [cloud name](/zpa/what-my-cloud-name-zpa). You can access the ZPA Admin Portal via your assigned ZPA cloud.
If your sign-in attempt fails more than three times, your account is locked out for 30 minutes. However, another ZPA admin can reset your password during this time.
If your account is configured without single sign-on (SSO):
- Enter your **Admin ID**.
If [Force Password Reset](/zpa/configuring-zpa-administrators) was enabled for your account, you must update your password before logging in.
- Click **Next**.
[See image.](#regularlogin)
- Select **Remember Me** if you want the ZPA Admin Portal to remember your username the next time you log in.
- (Optional) Click **Two Factor Authentication** and enter a passcode. To learn more, see [Configuring ZPA Administrators](/zpa/configuring-zpa-administrators).
- [](Optional) Select a language from the drop-down menu. The languages supported for ZPA are English, Spanish, French, German, Chinese, and Japanese. The default language selected is English.
Newer features might not be shown in other languages initially. The default language for all current features is English.
- Click **Sign In**.
[See image.](#additionallogin)
If your account is configured to use single sign-on (SSO):
- Enter your **Admin ID**.
- Click **Next**.
[See image.](#idplogin)
- You are redirected to your IdP's login page. Log in with your credentials.
If you logged in successfully, you are redirected back to the ZPA Admin Portal. To learn more, see [Configuring Authentication Settings](/zpa/configuring-authentication-settings) and [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
If your IdP is configured with the ZPA Admin Portal as a tile in the IdP-initiated SSO, log out of your ZPA Admin Portal. This will redirect you back to the ZPA login screen. Review the [previous step](#language) in the steps above to learn more about selecting a language for your ZPA Admin Portal.
Newer features might not be shown in other languages initially. The default language for all current features is English.
If you're subscribed to ZIdentity:
- Enter your **Admin ID**.
- Click **Next**.
[See image.](#zsloginlogin)
- You are redirected to [log in to the ZIdentity Landing Page.](#Node)
- After you log in, click the **Zscaler Private Access** tile to access the ZPA Admin Portal. If you have multiple tenants provisioned to the ZPA service, click on the service access tile of the tenant that you want to access.
[See image.](#zsloginlanding)
You are redirected to the ZPA Admin Portal.
[]When you log in for the first time, the ZPA Admin Portal displays a EUSA. Click **Accept** to accept the EUSA. If you click **Cancel**, the ZPA Admin Portal logs you out automatically.
The full EUSA can be read at [https://www.zscaler.com/legal/end-user-subscription-agreement](https://www.zscaler.com/legal/end-user-subscription-agreement?_ga=2.88734360.2019661774.1523980158-1285048483.1515448871).
[]The ZPA Admin Portal has the following items in the left-side navigation:
- [Search](#search)
- [Dashboard](#dashboard)
- [Insights](#insights)
- [Analytics](#Analytics)
- [Authentication](#Authentication)
- [Resource Management](#ResourceManagement)
- [Policy](#Policy)
- [Configuration & Control](#ConfigControl)
- [Zscaler Client Connector Portal](#ClientConnector)
- [Account](#Account)
- [Tools](#Tools)
- [VPN (for Legacy Apps)](#vpn)
- [What's New](#new)
- [Sign Out](#Logout)
![ZPA Admin Portal Login Page](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/Updated%20main%20page_0.png)
[]Click the **Search** icon to search for sections within the ZPA Admin Portal. To learn more, see [Searching in the ZPA Admin Portal](/zpa/searching-zpa-admin-portal).
[]Click **Dashboard** to view the different dashboards for the ZPA Admin Portal. To learn more about the dashboards, see the following articles:
- [Applications](/zpa/about-applications-dashboard)
- [Users](/zpa/about-users-dashboard)
- [Health](/zpa/about-health-dashboard)
- [App Connectors](/zpa/about-app-connector-dashboard)
- [Private Service Edges](/zpa/about-private-service-edge-dashboard)
- [AppProtection](/zpa/about-approtection-diagnostics)
[]Click **Insights** to view the insight options for the ZPA Admin Portal. To learn more about the deeper insights into ZPA, see the following articles:
- [Analyzing Risk with MITRE ATT&CK for AppProtection](/zpa/analyzing-risk-mitre-attck)
- [About Usage Insights](/zpa/about-usage-insights)
[]Click **Analytics** to view past and real-time data for users, applications, ZPA App Connector, ZPA Private Service Edges, events, and AppProtection for a specified date range. To learn more about diagnostics, see the following articles:
- [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics)
- [Viewing User Status Diagnostics](/zpa/viewing-user-status-diagnostics)
- [About App Connector Status Diagnostics](/zpa/about-connector-diagnostics)
- [About Private Service Edge Status Diagnostics](/zpa/about-zpa-service-edge-status-diagnostics)
- [About Events Diagnostics](/zpa/about-events-diagnostics)
- [About AppProtection Diagnostics](/zpa/about-approtection-diagnostics)
Click **Support Information** to create sessions that execute commands on App Connector and ZPA Private Service Edge. You can then filter and view the outputs of these sessions to assist in troubleshooting. To learn more, see [Accessing and Viewing Support Information](/zpa/accessing-and-viewing-support-information).
Click **Live Logs **to view real-time events and log data for user activity, user status, application activity, and App Connector status. To learn more, see [Accessing Live Logs](/zpa/accessing-live-logs).
[]To learn more about each component, see the following:
- User Authentication >
- [IdP Configuration](/zpa/documentation-knowledgebase/single-sign/idp-configuration)
- [Settings](/zpa/configuring-authentication-settings)
- [SAML Attributes](/zpa/documentation-knowledgebase/saml-attributes)
- [SCIM Attributes](/zpa/about-scim)
- [SCIM Users](/zpa/about-scim-users)
- [SCIM Groups](/zpa/about-scim-groups)
- [SCIM Sync Logs](/zpa/about-scim-sync-logs)
- Device Authentication >
- [Machine Groups](/zpa/about-machine-groups)
- [Machine Provisioning Keys](/zpa/about-machine-provisioning-keys)
[]To learn more about each component, see the following:
- Application Segment >
- [Application Segments](/zpa/documentation-knowledgebase/applications/application-segments)
- [Segment Groups](/zpa/documentation-knowledgebase/applications/segment-groups)
- [Browser Access](/zpa/documentation-knowledgebase/browser-access)
- [AppProtection](/zpa/about-appprotection-applications)
- [Privileged Remote Access](/zpa/about-privileged-remote-access-applications)
- User Portal >
- [User Portals](/zpa/about-user-portals)
- [Portal Links](/zpa/about-user-portal-links)
- [User Portal AUP](/zpa/about-user-portal-acceptable-use-policy)
- [Zscaler Client Connector Download Links](/zpa/about-zscaler-app-download-links)
- Privileged Remote Access >
- [Privileged Portals](/zpa/about-privileged-portals)
- [Privileged Consoles](/zpa/about-privileged-consoles)
- [Privileged Approvals](/zpa/about-privileged-approvals)
[]To learn more about each component, see the following:
- [Access Policy](/zpa/about-access-policy)
- [Timeout Policy](/zpa/about-timeout-policy)
- [Client Forwarding Policy](/zpa/about-client-forwarding-policy)
- [Isolation Policy](/zpa/about-isolation-policy)
- [AppProtection Policy](/zpa/about-appprotection-policy)
- [Privileged Policy](/zpa/about-privileged-policy)
[]To learn more about each component, see the following:
- Administration Control >
- [Administrators](/zpa/documentation-knowledgebase/company-and-administrators/administrators)
- [Roles](/zpa/about-roles)
- [Audit Logs](/zpa/about-audit-logs)
- [Company](/zpa/configuring-company-profile)
- [Disaster Recovery](/zpa/understanding-disaster-recovery)
- [Partner Information](/zpa/about-partner-information)
- [Client Sessions](/zpa/about-client-sessions)
- [Executive Insights App Access](/zpa/adding-executive-insights-app-user)
- Public API >
- [API Keys](/zpa/about-api-keys)
- Private Infrastructure >
- App Connector Management >
- [App Connectors](/zpa/documentation-knowledgebase/connectors-and-connector-groups/connectors)
- [App Connector Groups](/zpa/app-connector-management/app-connector-groups)
- [App Connector Provisioning Keys](/zpa/app-connector-management/app-connector-provisioning-keys)
- [Servers](/zpa/documentation-knowledgebase/servers/servers)
- [Server Groups](/zpa/documentation-knowledgebase/servers/server-groups)
- Private Service Edge Management >
- [Private Service Edges](/zpa/private-service-edge-management/private-service-edge)
- [Private Service Edge Groups](/zpa/private-service-edge-management/private-service-edge-groups)
- [Private Service Edge Provisioning Keys](/zpa/private-service-edge-management/private-service-edge-provisioning-keys)
- Log Streaming Service >
- [Log Receivers](/zpa/about-log-streaming-service)
- [App Connector Group](/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-groups)
- Cloud Connector Management >
- [Cloud Connectors](/zpa/about-cloud-connectors)
- [Cloud Connector Groups](/zpa/about-cloud-connector-groups)
- Certificate Management >
- [Enrollment Certificates](/zpa/documentation-knowledgebase/certificates/enrollment-certificates)
- [Certificates](/zpa/certificate-management/certificates)
- AppProtection >
- [AppProtection Controls](/zpa/about-appprotection-controls)
- [AppProtection Profiles](/zpa/about-appprotection-profiles)
- Notifications >
- [Notifications](/zpa/about-notifications)
[]Click the **Zscaler Client Connector Portal** icon to be redirected to the [Zscaler Client Connector Portal](/zscaler-client-connector/accessing-and-navigating-zscaler-client-connector-portal). In this portal, you can [configure settings](/zpa/step-step-configuration-guide-zpa) for the [Zscaler Client Connector](/zscaler-client-connector/what-is-zscaler-client-connector) as well as view information about users and devices that are enrolled with it.
For a ZPA tenant associated with multiple Zscaler Client Connector tenant accounts on separate clouds, you can select the Zscaler Client Connector cloud prior to connecting to the Zscaler Client Connector Portal.
[]From this menu, you can do the following:
- **Username**: View your user name for the ZPA Admin Portal account.
- **Customer ID**: View your customer ID for the ZPA Admin Portal account.
- **Language**: Set the language for your ZPA Admin Portal account. The language can also be set when you log in.
- **Time Zone**: Set the time zone for your ZPA Admin Portal account. The default time zone is your current one or the most recently saved one.
- **Password**: Set the password for your ZPA Admin Portal account.
![Account page in the ZPA Admin Portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/Updated2Account%20page%20in%20ZPA%20Admin%20portal_1.png)
[]From this menu, you can do the following:
- **Remote Assistance**: If you need Zscaler Support engineers to securely and remotely log in to your ZPA Admin Portal for troubleshooting purposes, you can update this setting. To learn more, see [About Remote Assistance](/zpa/about-remote-assistance).
- **Zscaler Help Portal**: This redirects you to the Help Portal where you can find documentation that provides background information as well as configuration guides about ZPA and other Zscaler products.
- **Submit a Ticket**: This redirects you to the Zscaler Support Portal where you can submit help request tickets to Zscaler Support.
[]To learn more about each component, see the following:
- [Dashboard](/zpa/viewing-network-connectors-dashboard)
- VPN Users >
- [User Enablement](/zpa/about-vpn-user-enablement)
- [VPN Connected Users](/zpa/about-vpn-connected-users)
- Network Connector Management >
- [Network Connectors](/zpa/about-network-connectors)
- [Network Connector Groups](/zpa/about-network-connector-groups)
- [Network Connector Provisioning Keys](/zpa/about-network-connector-provisioning-keys)
- [VPN Service Edges](/zpa/about-vpn-service-edges)
- [Network Segments](/zpa/about-network-segments)
[]Click **What's New **to request a free trial of features that can be added to your ZPA Admin Portal experience on the **Add-On Licenses** tab. You can also view newer features on the **Recently Released** tab. If you don't want to view these offers, click **Don't show me again**.
![What's New window shows features new products for the ZPA Admin Portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/Updated%20Try%20and%20Buy%20Screenshot.png)
[]Click the** Sign Out** icon to sign out of the ZPA Admin Portal when you are done. If you are inactive for 15 minutes, the portal automatically signs you out.
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
[]![Selecting the ZPA Admin Portal within the ZIdentity Landing Page](/downloads/zpa/documentation-knowledgebase/admin-settings/admins-and-roles/about-administrators/Zscaler%20OneIdentity%20ZPA%20login.png)
[]![First page logging into the ZPA portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/New%20Sign%20In%20page.png)
[]![First page logging into the ZPA portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/New%20Sign%20In%20page_2.png)
[]![First page logging into the ZPA portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/New%20Sign%20In%20page_3.png)
[]![ZPA Admin Portal Login Page](/downloads/zpa/getting-started/about-zpa/introduction-zpa-admin-portal/zpa-loginscreen.png)