# Configuring OpenID for Single Sign-On Using Okta
Source: https://help.zscaler.com/deception/configuring-openid-single-sign-using-okta
PDF: https://help.zscaler.com/pdf/com/en/1531364.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on configuring OpenID for single sign-on (SSO) using Okta.
Before you configure OpenID for SSO, make sure to [configure OpenID on Okta](https://help.okta.com/en-us/Content/Topics/Apps/Apps_App_Integration_Wizard_OIDC.htm#) with the following settings:
-
Select Web Application as the application type.
[See image.](#deception-open-id-sso-app-type)
-
Use `https://``<Zscaler Deception Instance Name>``/oauth` as the sign-in redirect URI.
[See image.](#deception-open-id-sign-in-redirect)
To configure OpenID for SSO using Okta:
- [Step 1: Obtain the Client ID and Client Secret from Okta](#obtain-client-id-client-secret-okta-openid)
- [Step 2: Obtain the OpenID Endpoint Configuration for Okta](#obtain-endpoint-configuration-okta-openid)
- [Step 3: Configure OpenID for SSO on the Zscaler Deception Admin Portal](#config-openid-portal)
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the application that you created while configuring OpenID for Okta.
- Select **General**.
- Copy the **Client ID** and **Client Secrets**.
[See image.](#obtain-client-id-secret)
- []Enter the following URL in the browser:
`https://``<Okta Instance>``.okta.com/.well-known/openid-configuration`
- When the configuration file opens, copy the following information:
- `issuer`
- `authorization_endpoint`
- `token_endpoint`
- `jwks_uri`
[See image.](#obtain-endpoint-config)
[]After you obtain the client ID, client secret, and endpoint configuration details, you must [configure OpenID for SSO in the Deception Admin Portal](/deception/configuring-openid-single-sign).
[]![Select an app type](/downloads/deception/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-config-open-id-okta-app-type-web.png)
[]![Sign-in redirect URI details](/downloads/itdr/authentication/openid-configuration/configuring-openid-single-sign-using-okta/itdr-config-open-id-okta-sso-1.png)
[]![Obtain Client ID and Client Secret from Okta](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-okta/zscaler-deception-openid-copy-client-id-secret.png)
[]![Obtain OpenID Endpoint Configuration for Okta](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-okta/zscaler-deception-openid-endpoint-configuration-okta.png)