# Configuring OpenID for Single Sign-On Using Google
Source: https://help.zscaler.com/deception/configuring-openid-single-sign-using-google
PDF: https://help.zscaler.com/pdf/com/en/1531365.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on configuring OpenID for single sign-on (SSO) using Google.
To configure OpenID for SSO using Google:
- [Step 1: Obtain Client ID and Client Secret from Google](#obtain-client-id-client-secret-google)
- [Step 2: Obtain OpenID Endpoint Configuration for Google](#obtain-endpoint-config-google-openid)
- [Step 3: Configure OpenID for SSO on the Zscaler Deception Admin Portal](#config-openid-portal-google)
- []Log in to the [Google Cloud Platform Console](https://console.cloud.google.com/).
- Under **Quick Access**, click **API and Services**.
- In the left-side navigation menu, click **Credentials**.
- Select the application that you created while configuring OpenID for Google, and click the **Edit** icon.
[See image.](#openid-google-edit-app)
- On the **Client ID for Web application** page, copy the **Client ID** and **Client secret**.
[See image.](#openid-google-client-id-secret)
- []Enter the following URL in the browser:
`https://accounts.google.com/.well-known/openid-configuration`
- When the configuration file opens, copy the following information:
- `issuer`
- `authorization_endpoint`
- `token_endpoint`
- `jwks_uri`
[See image.](#openid-google-endpoint-config-file)
[]After you obtain the client ID, client secret, and endpoint configuration details, you must [configure OpenID for SSO in the Deception Admin Portal](/deception/configuring-openid-single-sign).
[]![Edit the OpenID app on Google](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-google/zscaler-deception-openid-google-auth-app.png?1657777847)
[]![Obtain Client ID and Client Secret from Google](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-google/zscaler-deception-google-outh-obtain-client-id-secret.png)
[]![Obtain OpenID Endpoint Configuration for Google](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-google/zscaler-deception-google-openid-endpoint-config.png)