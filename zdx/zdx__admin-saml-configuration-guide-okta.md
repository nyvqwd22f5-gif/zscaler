# Admin SAML Configuration Guide for Okta
Source: https://help.zscaler.com/zdx/admin-saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1413011.pdf

This guide illustrates how to configure Okta as the identity provider for the Zscaler service and use [SAML single sign-on (SSO) for admins](/zdx/configuring-saml-zdx-admins). Refer to the [Okta documentation](https://developer.okta.com/docs/guides/build-sso-integration/saml2/main/#create-your-integration) for additional information about the steps in the guide.
Prerequisites
Ensure you have the following before configuring Okta:
- [Okta account with admin privileges](https://developer.okta.com/docs/guides/build-sso-integration/saml2/main/)
- [ZDX Admin accounts](/zdx/adding-zdx-admins) created for your organization's admins
- [ZDX cloud URL](#zdx-cloudurls)
Configuring Admin SAML SSO in Okta
To configure Okta as the IdP for the Zscaler service and use SAML SSO for admins:
- Go **Applications** > **Create App Integration**.
- Enter `ZDX` in the **Search** field to select **ZDX SAML**.
-
Select **SAML 2.0** as the sign-in method and click **Next**.
[See image.](#Sign-In-Method)
-
In the **Create SAML Integration** wizard, for **General Settings**, enter the **App Name** for the Zscaler service's display name and then click **Next.**
[See image.](#GeneralSettings)
-
For **Configure SAML**, enter your Access (ACS) URL to **Single sign on URL**, **Recipient URL**, **Destination URL**, and **Audience URI (SP Entity ID)**.
Click **Next**.
[See image.](#ConfigureSAML)
If **Use this for Recipient URL and Destination URL** is selected, then your **Single sign on URL** is copied into the **Single sign on URL** and **Audience URI (SP Entity ID)** fields.
If you have a domain defined on multiple ZIA clouds, then enter the ZIA cloud name that is associated with ZDX in the **Default RelayState** field (e.g., zscaler.net).
[See image.](#RelayState)
-
For **Feedback**, choose **I'm a software vendor. I'd like to integrate my app with Okta** and then click **Finish** to complete the SAML integration.
[See image.](#Feedback)
-
In the **Assign ZDX SAML SSO to People**, enter the admin's name or email address (Username) to search, and click **Assign**.
[See image.](#AssignAdmin)
-
Confirm the selected admin by their user name and click **Save and go back**.
[See image.](#ConfirmUserName)
-
Review the assigned admin in the SAML Service Provider and exit from the window.
[See image.](#ConfirmAssignmentToAdmin)
The admin can now access the ZDX Admin Portal through Okta by clicking the configured Zscaler application for Admin SAML.
[See image.](#MyApps-ZDXSAMLSSO)
[]![General Settings Tab for Add SAML Service Provider.](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-App-Name.png?1662676931)
[]![Feedback selection](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-Select-Customer-Partner.png)
[]![Select Admin to assign SAML provider.](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-Select-Assign-Admins.png?1662677400)
[]![Save and go back to confirm assignment to admin.](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-Confirm-Assignment-Admin.png?1662677345)
[]![Exit upon confirmation of assignment](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-Confirmed-Assignment-Admins.png?1662677271)
[]![Screenshot of the Okta app with the admin SAML app now available](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-SAML-Admin-SSO.png?1662678645)
[]![Choose SAML 2.0.](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-Okta-Select-SAML-2.0.png?1662677691)
[]![Configure SAML with Access URLs](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-CreateSAMLIntegration-ConfigureSAML.png)
[]![Add Relay State URL](/downloads/zdx/administration/admin-saml-configuration-guide-okta/ZDX-CreateSAMLIntegration-ConfigureSAML-RelayState.png)
[]
[]When configuring IdPs, the following information might be required for ZDX.
- ACS URL:
For ZDX Cloud:
https://admin.zdxcloud.net/zdx/idp-auth
For ZDX Beta Cloud:
https://admin.zdxbeta.net/zdx/idp-auth
- Download the SAML SSL certificate from the IdP. It must be in Base64-encoded PEM format.
- Entity ID:
For ZDX Cloud:
https://admin.zdxcloud.net
For ZDX Beta Cloud:
https://admin.zdxbeta.net
If you have a domain defined on multiple ZIA clouds, enter the ZIA cloud name that is associated with ZDX in the **Relay State** field (for example, `zscalertwo.net`) for each application.
You must also create admin accounts for your organization's admins. To learn more, see [Adding ZDX Admins](/zdx/adding-zdx-admins).
To learn more, see [Configuring SAML for ZDX Admins](/zdx/configuring-saml-zdx-admins).