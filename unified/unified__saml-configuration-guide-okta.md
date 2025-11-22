# SAML Configuration Guide for Okta
Source: https://help.zscaler.com/unified/saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1515246.pdf

Zscaler 3rd-Party App Governance supports identity provider (IdP)-initiated SAML to authenticate admins and users logging in to the 3rd-Party App Governance Admin Portal. This guide illustrates how to configure Okta SAML integration and Okta as the IdP in 3rd-Party App Governance. Refer to the Okta documentation for additional information about the steps in the guide.
You must contact Zscaler Support with the information listed in the prerequisites to complete the configuration process.
Prerequisites
Ensure you have the following before configuring Okta:
- Okta account
- **Sign In URL: **The URL where SAML authentication requests are sent. This is also called the single sign-on (SSO) endpoint.
- **X.509 Signing Certificate**: The public key certificate required by the service provider to validate the signature of the authentication assertions that have been digitally signed by the IdP. Auth0 accepts the .pem and .cer formats.
- **Sign Out URL:** The URL where SAML logout requests are sent. This is also called the single logout (SLO) endpoint. If logout is required, you must provide the sign out URL.
Configuring Okta SAML Integration
You can obtain the single sign-on URL and the X.509 certificate after configuring the Okta SAML integration. To configure the Okta SAML integration:
- Sign in to the [Okta Developer Console](https://login.okta.com/).
- Use the [App Integration Wizard](https://help.okta.com/en/prod/Content/Topics/Apps/Apps_App_Integration_Wizard.htm) to add an application for use with Auth0.
- Use the [SAML App Wizard](https://help.okta.com/en-us/content/topics/apps/apps_app_integration_wizard_saml.htm) to create your SAML integration. After completion, you are directed to the** **Sign On page for your newly created app.
- Click **View Setup Instructions** to complete the process.
- Note the IdP Single Sign-On URL, and download a copy of the X.509 certificate.
Configuring Okta as an IdP in 3rd-Party App Governance
To configure Okta as an IdP in 3rd-Party App Governance, contact Zscaler Support with the information listed in the prerequisites.