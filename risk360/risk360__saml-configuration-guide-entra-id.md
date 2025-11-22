# SAML Configuration Guide for Microsoft Entra ID
Source: https://help.zscaler.com/risk360/saml-configuration-guide-entra-id
PDF: https://help.zscaler.com/pdf/com/en/1470391.pdf

The Risk360 service supports identity provider (IdP)-initiated SAML authentication for admins. The admin can log in to the [Risk360 Admin Portal](/risk360/accessing-and-navigating-risk-360-admin-portal) directly from a single sign-on (SSO) provider's portal by clicking the Risk360 application icon. This guide illustrates how to configure SAML SSO with Microsoft Entra ID for the Risk360 service.
Prerequisites
Ensure that you have the following before you start configuring Microsoft Entra ID:
- An Microsoft Entra ID account with admin privileges.
- Admins created for Risk360 service in Microsoft Entra ID.
Configuring SAML SSO with Microsoft Entra ID
To configure Microsoft Entra ID SAML SSO for Risk360:
- [1. Create Risk360 App integration in Microsoft Entra ID.](#create-app-integration)
- [2. Assign admins to Risk360.](#assign-admins)
- [3. Download the SAML signing certificate from Microsoft Entra ID.](#download-certificate)
- [4. Configure SAML SSO in the Risk360 Admin Portal.](/risk360/configuring-saml-admins-risk360)
After you complete the preceding steps, admins can access the Risk360 Admin Portal using their Microsoft Entra ID credentials or the Risk360 tile on their apps dashboard in the [My Apps](https://myapps.microsoft.com/) portal..
[See image.](#myapps-img)
[]To add the Risk360 application to Microsoft Entra ID:
- Log in to the [Microsoft Entra portal](https://entra.microsoft.com/) portal.
- Go to **Identity > Applications > Enterprise applications** from the left-side navigation.
[See image.](#enterprise-app)
-
Click **New application**, then click **Create your own application**.
The **Create your own application** window appears.
-
In the **Create your own application** window:
- Enter an application name for the Risk360 service in the **What's the name of your app?** field. For example, enter `Risk360`.
- Select the **Integrate any other application you don't find in the gallery (Non-gallery)** option.
- Click **Create**.
[See image.](#create-your-app)
The Microsoft Entra ID service displays a notification that the application is added, and you are redirected to the application's **Overview** page.
-
From the left-side navigation, click **Single sign-on**, then click **SAML**.
[See image.](#single-sign-on)
The **Set up Single Sign-on with SAML** page appears.
- In the **Basic SAML Configuration **section, click **Edit** and complete the following fields:
-
**Identifier (Entity ID)**: Enter the entity ID. You can find this information by downloading the XML metadata file from the **Download XML Metadata **field on the Administrator Management page (**Administration **> **Administrator Management**) in the Risk360 Admin Portal. This ID is specific to your IdP.
[See image.](#sp-entity-id-download)
-
**Reply URL (Assertion Customer Service URL)**: Enter the Reply URL. You can find this information by downloading the XML metadata file from the **Download XML Metadata **field on the Administrator Management page (**Administration **> **Administrator Management**) in the Risk360 Admin Portal.
[See image.](#acs-url)
-
**Relay State**: Enter your Risk360 cloud name. You can view the cloud from the My Profile page in the Risk360 Admin Portal.
[See image.](#my-profile)
- Click **Save** and exit the window.
[See image.](#basic-saml-cong)
[]To assign admins to the Risk360 application:
- From the left-side navigation, go to **Identity > Applications > Enterprise applications**.
- Search for and open the Risk360 application.
- From the left-side navigation, click **Users and groups**, then **Add user/group**.
[See image.](#add-user-group)
The **Users and groups** window appears.
- Search for the user or group you want to assign to the Risk360 service.
- Select the checkbox next to the user or group names you want to assign to the Risk360 service, then click **Select**.
[See image.](#adding-user)
- In the **Add Assignment** panel, click **Assign**.
[See image.](#assign-user)
You are redirected to the **Users and groups** page where you can see the users are successfully assigned to Risk360.
[See image.](#assigned-users)
[]To download the SAML signing certificate:
- From the left-side navigation, go to **Identity > Applications > Enterprise applications**.
- Search for and open the Risk360 application.
-
From the left-side navigation, click **Single sign-on**, then **SAML**.
[See image.](#single-sign-on-1)
The **Set up Single Sign-on with SAML** page appears.
- In the **SAML Certificates **section, click the download link next to the **Certificate (Base64) **field** **to obtain the Base64 certificate.
[See image.](#saml-certificate-img)
The certificate is downloaded to your system. Upload the certificate as part of Step 4 in the **IdP SAML Certificate **field.
![Screenshot of Create App Integration option in Okta](/downloads/ZSLogin-Enterprise%20applications%20(1)%20(1).png)
[]
![Screenshot of the SAML 2.0 option in OKta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-SAML.png)
[]
![Screenshot of the Configure SAML section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Create%20your%20own%20application.png)
[]
![Screenshot of the Feedback section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Single%20sign-on.png)
[]
![Users and group](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Add-user-group.png)
[]
![Screenshot of SAML Signing Certificate section in Okta](/downloads/Risk360-users-assigned-in-azure-portal%20(1).png)
[]
![Screenshot of the Assign to People option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Assign-user-group.png)
[]
![Screenshot of the Assign option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-adding-users.png)
[]
![Screenshot of the Assign option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Federation%20Metadata%20XML-entity-it_0.png)
[]
![ACS URL](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Federation%20Metadata%20XML-ACS1.png)
[]
![Screenshot of the Assign option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-my-profile-page.png)
[]
![Screenshot of the Feedback section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Single%20sign-on.png)
[]
![Screenshot of the Feedback section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-azure-ad/Risk360-Federation%20Metadata%20XML.png)
[]
![My Apps Portal](/downloads/business-insights/authentication-administration/saml-configuration-guide-microsoft-entra-id/Risk360-myapps-homepage-BI-tile_0.png)
[]