# Configuring OpenID for Google
Source: https://help.zscaler.com/itdr/configuring-openid-google
PDF: https://help.zscaler.com/pdf/com/en/1531735.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on configuring OpenID single sign-on (SSO) for Google.
Prerequisites
Before you configure OpenID for Google, make sure to [configure Google OAuth 2.0](https://developers.google.com/identity/openid-connect/openid-connect).
Configuring OpenID
To configure OpenID for Google:
- [Step 1: Obtain Client ID and Client Secret from Google](#itdr-obtain-client-id-client-secret-google)
- [Step 2: Obtain OpenID Endpoint Configuration for Google](#itdr-obtain-endpoint-config-google-openid)
- [Step 3: Configure OpenID for SSO on the Zscaler ITDR Admin Portal](#itdr-config-openid-portal-google)
- []Log in to the [Google Cloud Platform Console](https://console.cloud.google.com/).
- Under **Quick Access**, click **API and Services**.
- In the left-side navigation, click **Credentials**.
-
Select the application that you created while configuring OpenID for Google, and click the **Edit** icon.
[See image.](#itdr-openid-google-edit-app)
-
On the **Client ID for Web application** page, copy the **Client ID** and **Client secret**.
[See image.](#itdr-openid-google-client-id-secret)
-
[]Enter the following URL in the browser:
`https://accounts.google.com/.well-known/openid-configuration`
-
When the configuration file opens, copy the following information:
- `issuer`
- `authorization_endpoint`
- `token_endpoint`
- `jwks_uri`
[See image.](#itdr-openid-google-endpoint-config-file)
[]After you obtain the client ID, client secret, and endpoint configuration details, you must [configure OpenID for SSO in the ITDR Admin Portal](/itdr/configuring-openid-single-sign).
[]![Edit the OAuth 2.0 app](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-google/itdr-openid-google-auth-app.png)
[]![Obtain client ID and client secret details](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-google/itdr-google-outh-obtain-client-id-secret.png)
[]![OpenID endpoint configuration details](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-google/itdr-google-openid-endpoint-config.png)