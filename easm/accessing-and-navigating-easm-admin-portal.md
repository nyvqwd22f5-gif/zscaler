# Accessing and Navigating the EASM Admin Portal
Source: https://help.zscaler.com/easm/accessing-and-navigating-easm-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1503626.pdf

This article covers the following topics:
- [Signing in to the EASM Admin Portal](#signing-in)
- [Accepting the End User Subscription Agreement (EUSA)](#accepting-eusa)
- [Navigating within the EASM Admin Portal](#navigating-admin-portal)
[]When an EASM tenant is provisioned for your organization, a user account with the super admin role is created. This account allows you to access all functionalities and features in the EASM Admin Portal. Zscaler sends you an email with details such as the URL to access the EASM Admin Portal along with your login ID. Use the details in the email to complete your account registration. The registration process involves accessing the EASM Admin Portal through the provided link and configuring the authentication credentials for your account. This authentication flow also applies to the other administrator users that are configured with access to the EASM Admin Portal.
You must complete the registration within the stipulated time mentioned in your email.
The following steps are required to sign in to the EASM Admin Portal for all administrators added to the portal.
To sign in to the EASM Admin Portal for the first time and complete your account registration:
-
Click the Setup link sent via the email.
This takes you to a password creation page served by ZIdentity, Zscaler's unified identity service that centralizes identity management, user authentication, and entitlement assignment for users to Zscaler services.
-
On the **Create a Password** page:
- **New Password**: Enter a password.
- **Confirm New Password**: Re-enter the password to confirm.
[See image.](#password-creation)
This password is configured for ZIdentity through which you can centrally access all the supported Zscaler services.
- Click **Next** to continue.
-
On the **Multi-Factor Authentication** page, select one of the following authentication methods as your second factor of authentication, then click **Set Up**:
- [Security Key or Biometric](#set-up-security-key-biometric)
- [Google Authenticator](#set-up-Google-authenticator)
- [Phone OTP](#set-up-phone-OTP)
- [Email OTP](#set-up-email-OTP)
[See image.](#MFA-setup)
Optionally, you can skip configuring MFA if your ZIdentity configuration allows it until a period of time and enroll later using the **Enroll Second Factor** button on the Welcome page. However, Zscaler recommends that all user accounts are enrolled for MFA for enhanced security.
Your account is created, and the account details are displayed as shown in the following image.
[See image.](#account-setup)
-
Click **Continue**.
The ZIdentity Landing Page appears.
-
On the ZIdentity Landing Page, click the **External Attack Surface Management** tile to access the EASM Admin Portal.
[See image.](#ZIdentity-landing-page)
To sign in to the EASM Admin Portal subsequently after the initial login:
- Go to the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page).
-
Enter your login ID. Select the **Remember me** checkbox if you want the service to autofill your login ID information in subsequent sessions from the same device.
[See image.](#sign-in-page)
- Click **Next**.
-
Enter your password and click **Sign In**.
[See image.](#signin-using-password)
- Depending on the second method of authentication configured, you are prompted to enter one of the following credentials to complete the sign-in process:
- [Security Key or Biometric](#security-key-biometric)
- [Google Authenticator](#Google-authenticator)
- [Phone OTP](#phone-OTP)
- [Email OTP](#email-OTP)
If you want to use a temporary alternative method to sign in without having to enter a password or the second factor authentication details, click **Other Sign-in Options** on the Password screen and select **Email OTP**. An OTP is sent to the email address configured for your account. Enter the OTP and click **Verify** to sign in your account. This option is supported only if you have configured MFA.
[See image.](#other-signin-options)
If you want to reset your password, click **Having trouble signing in?** > **Reset Password** to receive a password reset email. To configure a different method of authentication for MFA, click **Having trouble signing in?** > **Reset Second Factor** to receive an email with instructions to reset your second method of authentication a. The reset link within the email expires after 5 minutes. To learn more, see [Resetting the Login Credentials or MFA](/zidentity/resetting-login-credentials-or-mfa).
[See image.](#reset-account-credentials)
[]When administrators log in to the EASM Admin Portal for the first time, an EUSA is displayed. You need to accept the EUSA to start using the features in the EASM Admin Portal.
You can access the EUSA anytime on the [Zscaler website](https://www.zscaler.com/legal/end-user-subscription-agreement).
[]The EASM Admin Portal contains the following items in the left-side navigation:
- [Dashboard](#dashboard)
- [Insights](#insights)
- [Assets](#assets)
- [Administration](#administration)
- [Log Out](#logout)
[See image.](#portal-navigation)
[]To configure a security key or biometric:
- When you click **Set Up**, a list of all Fast Identity Online 2 (FIDO2) supported methods available for your devices is displayed. FIDO2 is a set of protocols developed by the FIDO Alliance to provide the most secure passwordless authentication methods. The services, such as Windows Hello, YubiKey, etc., register and certify their security devices with FIDO2 to cater to their customers.
- Select one of the methods from the list to set up a security key or biometric authentication.
- Follow the instructions displayed on your screen to complete the set up.
[]To set up Google Authenticator:
- Follow the steps shown on the screen and then click **Next**.
- In the **Google Authenticator Verification Code** field, enter the verification code that you see in the Google Authenticator and click **Verify**.
[]To set up SMS one-time password (OTP):
- **Country**: Select the country of your phone number.
- **Phone Number**: Enter the phone number on which you want to receive the OTP and click **Send OTP via SMS**.
- **Enter SMS OTP**: Enter the OTP received on your phone and click **Verify**. The OTP is valid for two minutes. If it expires, click **Back** and then **Send OTP via SMS** to request a new one.
You also have the option to go back and modify your number before verification. Currently, the SMS OTP option is only supported for phone numbers from India and the USA.
[]Your second-factor authentication is configured as **Email OTP** as soon as you click **Set Up**. An email OTP is sent to your official email address during your login attempts as part of your secondary authentication.
[See image.](#email-OTP-example)
[]Enter your security key or complete the biometric authentication.
[]Enter the one-time verification code generated and shown on your Google Authenticator.
[]Enter the **Country** and **Phone Number** and click **Request Code**. Enter the one-time password (OTP) received on your phone number and click **Verify**. The OTP expires after two minutes. If the OTP expires or if you don't receive an OTP, click **Resend** to receive another OTP after 60 seconds.
[]Enter the OTP received at your email address and click **Verify**. The OTP expires after two minutes. If the OTP expires or if you don't receive an OTP, click **Resend** to receive another OTP after 60 seconds.
[]Click the **Dashboard** drop-down menu to select between **Insights Overview** and **Assets Overview**. These dashboards provide a high-level summary of your organization's risk findings and asset inventory in graphical representations for a quick and easy interpretation of the data by adjusting the parameters as needed.
To learn more, see [Understanding Dashboards](/easm/understanding-dashboards).
[]Click the **Insights** drop-down menu to select between **Findings** and **Lookalike Domains**. The **Findings** page provides a cataloged list of risk findings associated with the assets attributed to your organization through EASM's discovery and inventory processes, along with critical information about the findings. The **Lookalike Domains** page provides a tabulated list of phishing domains detected for your legitimate domains. You can access detailed information about individual risk findings and lookalike domains from the repective pages.
To learn more, see [About Findings](/easm/about-findings) and [About Lookalike Domains](/easm/about-lookalike-domains).
[]Click **Assets** to view a tabulated list of all the internet-exposed assets linked to your organization along with critical information about each asset, such as the asset type, risk level, number of risk findings detected in the asset, when the asset was first and last seen, and more. You can access detailed information about each asset and its risk findings from this page.
To learn more, see [About Asset Inventory](/easm/about-asset-inventory).
[]Click the **Administration** drop-down menu to select from the following menu items displayed:
- **Organization**: Add your organization and set up a discovery profile to scan and inventory the internet-facing assets that are linked to your organization. To learn more, see [Creating & Managing Organizations](/easm/creating-managing-discovery-profiles).
- **Role Management**: Configure role-based access control to assign specific access permissions and privileges for users to organizations. To learn more, see [About Role Management](/easm/about-role-management).
[]Click **Log Out** to sign out of the EASM Admin Portal. Users are automatically logged out of the portal after 1 hour of inactivity.
[]![Setting up EASM account by creating a password](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-account-password-creation_0.png)
[]![Configure multi-factor authentication (MFA) for EASM account for enhanced security)](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-account-MFA-setup_0.png)
[]![EASM account details displayed after completing authentication setup ](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-account-setup-complete_0.png)
[]![EASM account sign-in page with login ID entered](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/zidentity-sign-in-page-easm_0.png)
[]![EASM account sign-in process using password](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-account-signin-using-password_0.png)
[]![EASM account sign-in using email OTP](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-account-email-OTP_0.png)
[]![EASM account additional sign-in options](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-other-signin-options_0.png)
[]![EASM account authentication credentials reset](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/easm-reset-account-credentials_0.png)
[]![EASM Admin Portal Left-Side Navigation](/downloads/easm/getting-started/admin-portal/accessing-and-navigating-easm-admin-portal/navigating-easm-admin-portal_0.png)
[]![ZIdentity landing page to access EASM](/downloads/easm/getting-started/admin-portal/accessing-navigating-easm-admin-portal/ZIdentity-landing-page_1.png)