# Signing in to the Admin Portal
Source: https://help.zscaler.com/unified/signing-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1491881.pdf

This article covers the following topics:
- [Signing in to the Admin Portal](#Signing-in)
- [Navigating within the Admin Portal](#navigating-admin-portal)
- [Maintenance and Upgrades](#maint-and-upgrades)
[]After your organization is provisioned, you can access the Admin Portal at [https://console.zscaler.com](https://console.zscaler.com).
When the Sign In page appears:
- Enter your** Login ID** and select the **Remember my Login ID** checkbox if you want the service to remember your username the next time you log in.
- Click **Next**.
- If you have access to multiple Zscaler clouds or tenants, select the one you want to use and click **Proceed**. Your selection is saved for future logins. You can change the default cloud and tenant in[ Account Settings](/unified/customizing-your-account-settings).
-
Based on your organization's [authentication preference](/zslogin/configuring-authentication-methods), sign in to the ZIdentity Landing Page using one of the following methods:
- [Password](#password)
- [Multi-Factor Authentication (MFA)](#mfa)
- [Email One-Time Password (OTP)](#email-otp)
- [Security Key or Biometric](#security-key-biometric)
- []Enter your **Login ID and **select **Remember me **if you want the service to remember your login ID the next time you log in.
- Click** Next**.
- Enter your **Password **and click **Sign In**.
If you forget your password, click **Having trouble signing in? **> **Reset Password**, and a reset email is sent to your email ID. The password reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/unified/resetting-login-credentials-or-mfa).
- []Enter your **Login ID **and select **Remember me **if you want the service to remember your login ID the next time you log in.
- Click** Next**.
- Enter your **Password **and click **Sign In**.
- Based on your organization's MFA policy, two-factor authentication (2FA) is required. Complete your 2FA to access the ZIdentity Landing Page.
If you forget your password or want to configure a different secondary authenticator, click **Having trouble signing in? **> **Reset Password **or** Reset Second Factor**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/unified/resetting-login-credentials-or-mfa).
If your account is configured with MFA, you can sign in using an email OTP as well:
- []Enter your **Login ID **and select **Remember me **if you want the service to remember your login ID the next time you log in.
- Click** Next**, then click **Email OTP**.
- Enter the OTP sent to your email address and click **Sign In**. The OTP expires after two minutes. If the OTP expires or you don't receive an OTP, click **Resend **to receive another OTP after 60 seconds.
- []Enter your **Login ID **and select **Remember me **if you want the service to remember your login ID the next time you log in.
- Select **Sign-in using Security Key or Biometric**.
- Click** Next**.
- Based on your configuration, enter your security key or complete the biometric to access the ZIdentity Landing Page.
If you want to configure with a different security key or biometric, click **Having trouble signing in? **> **Reset Security Key or Biometric**, and a reset email is sent to your email ID. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Password or MFA](/unified/resetting-login-credentials-or-mfa).
To sign out, go to the **Account **menu in the upper-right corner and click **Sign Out**.
[See image.](#sign-out)
You are automatically logged out after a configurable number of inactive minutes. To learn more, see [Configuring the Authentication Session](/unified/configuring-authentication-session).
If you are an admin or user with access to Internet & SaaS features within the Admin Portal and you have 5 unsuccessful attempts to sign in within one minute, your account is locked out for 5 minutes. The failed attempts are recorded in the audit log. Audit logs are stored for up to 6 months.
If you are an admin or user with access to Private Applications features within the Admin Portal and you have three unsuccessful attempts to sign in, your account is locked out for 30 minutes. However, another admin with the same level of access or a full admin can reset your password.
[]The Admin Portal has the following items in the top navigation:
- [Analytics](#analytics)
- [Administration](#administration)
- [Policies](#policies)
- [Infrastructure](#infrastructure)
- [Logs](#logs)
- [Search](#search)
- [Help](#help)
- [Activation](#activation)
- [Account](#account)
[]Click the **Analytics** menu to view dashboards and reports that allow you to analyze your organization's traffic, application security, user experience, and more. By default, enhanced dashboards and reports that are unique to the Unified Experience are displayed. To display classic reports for Internet & SaaS, Private Applications, etc., select the **Switch to Existing Reports** toggle.
To learn more about Unified Experience and classic reports, see [Analytics](/unified/analytics).
[]Click the **Administration** menu to view and configure administration settings for various Zscaler services. To learn more, see [Administration](/unified/administration).
[]Click the **Policies **menu** **to view and configure policies for various Zscaler services. To learn more, see [Policies](/unified/policies).
[]Click the **Infrastructure **menu to configure networking settings for various Zscaler services. To learn more, see [Infrastructure](/unified/infrastructure).
[]Click the **Logs** menu to configure log streaming and other log-related settings. To learn more, see [Logs](/unified/logs).
[]Click the **Search** icon to search for menus in the Admin Portal. To learn more, see [Searching in the Admin Portal](/unified/searching-admin-portal).
[See image.](#search-icon)
[]Click the **Help** icon to access the Zscaler Help Portal, where you can find technical documentation that includes, but is not limited to, overview, configuration, and deployment information. You can also access Zscaler support, legal notices, and subscription agreements.
[See image.](#help-icon)
[]Click the **Activation** icon to activate configuration changes that impact Internet & SaaS features. To learn more, see [Saving and Activating Changes in the Admin Portal](/unified/saving-and-activating-changes-admin-portal).
[See image.](#activation-icon)
[]Click the **Account **icon to switch among Zscaler clouds and tenants (if applicable), view your user name and organization information, and view or change your password, display language, or time zone. To learn more, see [Customizing Your Account Settings](/unified/customizing-your-account-settings). If you want to sign out of your account, click **Sign Out**.
[See image.](#account-icon)
[]During the scheduled maintenance and regular upgrade periods, the Admin Portal is in read-only mode. You can view content and navigate through the Admin Portal to view various details.
You cannot configure or edit any parameters when the Admin Portal is in read-only mode. After the upgrade is complete, the Admin Portal automatically refreshes and enables editing.
If you need to onboard users, see [Setting up Secure Access](/unified/setting-up-secure-access).
[]![Account icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/signing-admin-portal/search-icon.png)
[]![Search icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/signing-admin-portal/help-icon.png)
[]![Help icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/signing-admin-portal/activation-icon.png)
[]![Activation icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/signing-admin-portal/account-icon.png)
[]![Activation icon](/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/signing-admin-portal/sign-out.png)