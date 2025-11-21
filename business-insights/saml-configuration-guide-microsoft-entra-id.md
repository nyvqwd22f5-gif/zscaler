# SAML Configuration Guide for Microsoft Entra ID
Source: https://help.zscaler.com/business-insights/saml-configuration-guide-microsoft-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1475156.pdf

The Business Insights service supports identity provider (IdP)-initiated SAML authentication for admins. Admins can log in to the Business Insights Admin Portal directly from a single sign-on (SSO) provider's portal by clicking the Business Insights application icon. This guide illustrates how to configure SAML SSO with Microsoft Entra ID for the Business Insights service.
Prerequisites
Ensure that you have the following before you start configuring Microsoft Entra ID:
- An Microsoft Entra ID account with admin privileges.
- Admins created for Business Insights service in Microsoft Entra ID.
Configuring SAML SSO with Microsoft Entra ID
To configure Microsoft Entra ID SAML SSO for Business Insights:
- [Step 1: Create Business Insights App (SAML Configuration) in Microsoft Entra ID](#create-app-integration)
- [Step 2: Assign Admins to Business Insights](#assign-admins)
- [Step 3: Download the SAML Signing Certificate from Microsoft Entra ID](#download-certificate)
- [Step 4: Configure SAML SSO in the Business Insights Admin Portal](/business-insights/configuring-saml-admins-business-insights)
After you complete the preceding steps, admins can access the Business Insights Admin Portal using their Microsoft Entra ID credentials or the Business Insights tile on their apps dashboard in the [My Apps](https://myapps.microsoft.com/) portal.
[See image.](#myapps-img)
[]To add the Business Insights application to Microsoft Entra ID:
- Log in to the [Microsoft Entra](https://entra.microsoft.com/) portal.
- From the left-side navigation, go to **Identity > Applications > Enterprise applications** .
[See image.](#enterprise-app)
- Click **New application**, then search for `Zscaler Internet Access Administrator`.
- Click the **Zscaler Internet Access Administrator** tile.
- Enter an application name for the Business Insights service in the **Name** field. For example, enter `Business Insights`.
-
Click **Create**.
[See image.](#create-your-app)
The Microsoft Entra ID service displays a notification that the application is added, and you are redirected to the application's **Overview** page.
-
From the left-side navigation, click **Single sign-on**, then click **SAML**.
[See image.](#single-sign-on)
The **Set up Single Sign-on with SAML** page appears.
-
In the **Basic SAML Configuration **section, click **Edit** and complete the following fields:
- **Identifier (Entity ID)**: Enter `https://admin.zscaleranalytics.net`.
- **Reply URL (Assertion Customer Service URL)**: Enter `https://admin.zscaleranalytics.net/idp-auth`.
-
**Relay State**: Enter your Business Insights cloud name. You can view the cloud from the Account page in the Business Insights Admin Portal. This field is mandatory.
[See image.](#my-profile)
- Click **Save** and exit the window.
[See image.](#basic-saml-cong)
- In the **Attributes & Claims **section, click **Edit**.
-
Click the **Unique User Identifier (Name ID)** claim.
[See image.](#name-id)
-
Ensure that the **Source attribute** value is set to **user.mail**.
[See image.](#source-attribute)
- Click **Save** and exit the window.
[]To assign admins to the Business Insights application:
- From the left-side navigation, go to **Identity > Applications > Enterprise applications**.
- Search for and open the Business Insights application.
- From the left-side navigation, click **Users and groups**, then click **Add user/group**.
[See image.](#add-user-group)
The **Users and groups** window appears.
- Search for the user or group you want to assign to the Business Insights service.
- Select the checkbox next to the user or group names you want to assign to the Business Insights service, then click **Select**.
[See image.](#adding-user)
- In the **Add Assignment** panel, click **Assign**.
[See image.](#assign-user)
You are redirected to the **Users and groups** page where you can see the users are successfully assigned to Business Insights.
[See image.](#assigned-users)
[]To download the SAML signing certificate:
- From the left-side navigation, go to **Identity > Applications > Enterprise applications**.
- Search for and open the Business Insights application.
-
From the left-side navigation, click **Single sign-on**, then click **SAML**.
[See image.](#single-sign-on-1)
The **Set up Single Sign-on with SAML** page appears.
- In the **SAML Certificates **section, click the download link next to the **Certificate (Base64) **field** **to obtain the Base64 certificate.
[See image.](#saml-certificate-img)
The certificate is downloaded to your system. Upload the certificate as part of Step 4 in the **IdP SAML Certificate **field.
![Create App Integration option in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Enterprise%20applications.png)
[]
![The SAML 2.0 option in OKta](/downloads/business-insights/authentication-administration/saml-admins/saml-configuration-guide-microsoft-entra-id/Business-Insights-SAML-Entra-ID.png)
[]
[]![Unique User Identifer claim in Attributes & Claims page](/downloads/business-insights/authentication-administration/saml-admins/saml-configuration-guide-microsoft-entra-id/Business-Insights-Attributes-Name-ID.png)
[]![Source Attribute field in Manage claim page](/downloads/business-insights/authentication-administration/saml-admins/saml-configuration-guide-microsoft-entra-id/Business-Insights-SAML-claim-attribute.png)
![The Configure SAML section in Okta](/downloads/business-insights/authentication-administration/saml-admins/saml-configuration-guide-microsoft-entra-id/Business-Insights-add-application.png)
[]
![The Feedback section in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Single%20sign-on%20(1).png)
[]
![Users and group](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Add-user-group%20(1).png)
[]
![SAML Signing Certificate section in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-users-assigned-in-azure-portal%20(1)%20(1).png)
[]
![The Assign to People option in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Assign-user-group%20(1).png)
[]
![The Assign option in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-adding-users%20(1).png)
[]
![The Assign option in Okta](/downloads/tech-pubs-drafts/business-insights-draft-articles/saml-configuration-guide-microsoft-entra-id/Business-Insights-Accounts-page.png)
[]
![The Feedback section in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Single%20sign-on%20(1)_0.png)
[]
![The Feedback section in Okta](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-Federation%20Metadata%20XML%20(1).png)
[]
![My Apps Homepage](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Business-Insights-myapps-homepage-BI-tile_0.png)
[]