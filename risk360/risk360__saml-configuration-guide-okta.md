# SAML Configuration Guide for Okta
Source: https://help.zscaler.com/risk360/saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1463891.pdf

The Risk360 service supports identity provider (IdP)-initiated SAML authentication for admins. The admin can log in to the [Risk360 Admin Portal](/risk360/accessing-and-navigating-risk-360-admin-portal) directly from a single sign-on (SSO) provider's portal by clicking the Risk360 application icon. This guide illustrates how to configure SAML SSO with Okta for the Risk360 service.
Prerequisites
Ensure that you have the following before you start configuring Okta:
- An Okta account with admin privileges.
- Admins created for the Risk360 service in the Okta directory.
Configuring SAML SSO with Okta
To configure Okta SAML SSO for Risk360:
- [1. Create Risk360 App integration in Okta.](#create-app-integration)
- [2. Assign admins to Risk360.](#assign-admins)
- [3. Download the SAML signing certificate from Okta.](#download-certificate)
- [4. Configure SAML SSO in the Risk360 Admin Portal.](/risk360/configuring-saml-admins-risk360)
After you complete the preceding steps, admins can access the Risk360 Admin Portal using their Okta credentials or the Risk360 tile on their Okta homepage.
[See image.](#okta-home-img)
[]To add the Risk360 application to Okta:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Click **Create App Integration**.
[See image.](#create-app-img)
- Select **SAML 2.0 **as the **Sign**-**in method**.
[See image.](#select-saml-img)
- Click **Next**.
- In the **General Settings** section, enter the display name for the service in the **App name** field (e.g., `Risk360`).
- Click **Next**.
- In the **Configure SAML** section:
- **Single sign-on URL**: Enter `https://admin.zscalerrisk.net/idp-auth`
- **Audience URI (SP Entity ID)**: Enter `https://admin.zscalerrisk.net/idp-auth`
- **Default RelayState**: Enter your Risk360 cloud name. You can view the cloud from the My Profile page in the Risk360 Admin Portal. [See image.](#my-profile)
[See image.](#saml-section-img)
- Click **Next**.
- In the **Feedback** section, select **I'm a software vendor. I'd like to integrate my app with Okta **and** **click **Finish**.
[See image.](#feedback-section-img)
The Risk360 integration is created in Okta. You can assign admins to the application.
[]To assign admins to the Risk360 application:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Select the Risk360 application from the list.
- Click **Assign **> **Assign to People**.
[See image.](#assign-peope-img)
- Click **Assign **next to the users that you want to assign the application.
[See image.](#assign-option-img)
- Click **Save and Go Back**, then click **Done**.
The admins are assigned to the Risk360 application.
[]To download the SAML signing certificate:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Select the Risk360 application from the list.
- In the** SAML Signing Certificates **section, download the SHA-2 type certificate by clicking **Actions** > **Download certificate**.
[See image.](#saml-certificate-img)
The certificate is downloaded to your system. Upload the certificate as part of Step 4 in the **IdP SAML Certificate **field.
[]![Screenshot of Create App Integration option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-create-integration-option.png)
[]![Screenshot of the SAML 2.0 option in OKta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-select-saml.png)
[]![My Profile page in the Risk360 Admin Portal](/downloads/risk360/administration-authentication/saml-configuration-guide-okta/Risk360-my-profile-page%20(1).png)
[]![Screenshot of the Configure SAML section in Okta](/downloads/risk360/administration-authentication/saml-configuration-guide-okta/Risk360-configure-saml-section%20(1).png)
[]![Screenshot of the Feedback section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-feedback.png)
[]![Screenshot of SAML Signing Certificate section in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-saml-sigining-certificate.png)
[]![Screenshot of the Assign to People option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-assiging-people.png)
[]![Screenshot of the Assign option in Okta](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-assign-option.png)
[]![Screenshot of Okta Homepage with RIsk360 tile](/downloads/risk360/authentication-administration/administration-role-management/saml-configuration-guide-okta/Risk360-Okta-homepage-risk360-tile_0.png)