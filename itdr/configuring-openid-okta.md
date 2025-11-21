# Configuring OpenID for Okta
Source: https://help.zscaler.com/itdr/configuring-openid-okta
PDF: https://help.zscaler.com/pdf/com/en/1531733.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on configuring OpenID single sign-on (SSO) for Okta.
Prerequisites
Before you configure OpenID, make sure to [configure OpenID for Okta](https://help.okta.com/en-us/Content/Topics/Apps/Apps_App_Integration_Wizard_OIDC.htm#) with the following settings:
-
Select Web Application as the application type.
[See image.](#itdr-open-id-sso-app-type)
-
Use `https://``<Zscaler ITDR Instance Name>``/oauth` as the sign-in redirect URI.
[See image.](#itdr-open-id-sign-in-redirect)
Configuring OpenID
To configure OpenID for Okta:
- [Step 1: Obtain the Client ID and Client Secret from Okta](#itdr-obtain-client-id-client-secret-okta-openid)
- [Step 2: Obtain the OpenID Endpoint Configuration for Okta](#itdr-obtain-endpoint-configuration-okta-openid)
- [Step 3: Configure OpenID for SSO on the Zscaler ITDR Admin Portal](#itdr-config-openid-portal)
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
-
Select the application that you created while configuring OpenID for Okta.
[See image.](#itdr-openid-sso-select-app)
- Select **General**.
-
Copy the **Client ID** and **Client Secrets**.
[See image.](#itdr-obtain-client-id-secret)
-
[]Enter the following URL in the browser:
`https://``<Okta Instance>``.okta.com/.well-known/openid-configuration`
-
When the configuration file opens, copy the following information:
- `issuer`
- `authorization_endpoint`
- `token_endpoint`
- `jwks_uri`
[See image.](#itdr-obtain-endpoint-config)
[]After you obtain the client ID, client secret, and endpoint configuration details, you must [configure OpenID for SSO in the ITDR Admin Portal](/itdr/configuring-openid-single-sign).
[]![Select an app type](/downloads/deception/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-config-open-id-okta-app-type-web.png)
[]![Sign-in redirect URI details](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-config-open-id-okta-sso-1.png)
[]![Select the application](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-openid-select-application.png)
[]![Copy client credentials and client secret](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-openid-copy-client-id-secret.png)
[]![Obtain OpenID endpoint config details](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-openid-endpoint-config-details.png)