# Configuring OpenID for Single Sign-On
Source: https://help.zscaler.com/deception/configuring-openid-single-sign
PDF: https://help.zscaler.com/pdf/com/en/1531366.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
This article provides information on how to configure OpenID for single sign-on (SSO) in the Zscaler Deception Admin Portal.
Before you configure OpenID for SSO, obtain the following details for the identity provider (IdP):
- Client ID
- Client Secret
- Issuer
- Authorization Endpoint
- Token Endpoint
- JSON Web Key Set (JWKS)
To learn more, see [Configuring OpenID for Single Sign-On Using Okta](/deception/configuring-openid-single-sign-using-okta) and [Configuring OpenID for Single Sign-On Using Google](/deception/configuring-openid-single-sign-using-google).
To configure OpenID for SSO:
- Go to **Settings** > **Users & Roles** > **IdP Providers**.
- Click **Add Provider**, and select **OpenID** from the drop-down menu.
[See image.](#openid-add-provider)
- In the **OpenID Provider Details** window:
- **Name**: Enter a name for the OpenID integration.
- **Enabled**: Select to enable the OpenID SSO provider.
- **Use Proxy Settings**: Enable if the Deception Admin Portal requires a proxy to connect to the OpenID SSO servers. This toggle is optional if you are using a SaaS-hosted version of Zscaler Deception.
- **Client ID**: Enter the client ID you obtained from your IdP.
- **Client Secret**: Enter the client secret you obtained from your IdP.
- **Endpoints**: Enter the endpoint configuration details that you obtained from the file:
- **Issuer**: Enter the issuer URL obtained from your IdP.
- **Authorization Endpoint**: Enter the authorization endpoint URL obtained from your IdP.
- **Token Endpoint**: Enter the token endpoint URL obtained from your IdP.
- **JWKS URI**: Enter the JWKS URI obtained from your IdP.
[See image.](#config-openid-provider-details)
- Click **Save**.
After the configuration, sign in to the Deception Admin Portal. You will see the identity provider's login button. Sign in with the OpenID provider to verify if the integration is successful.
[See image.](#openid-okta-button)
[]![Select OpenID IdP](/downloads/deception/authentication/openid-configuration/configuring-openid-single-sign/deception-openid-sso-add-provider-1.png)
[]![Configure OpenID provider details](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-okta/zscaler-deception-openid-provider-details.png)
[]![Okta button on the Zscaler Deception Sign In page](/downloads/deception/authentication/openid-and-ldaps-configuration/configuring-openid-single-sign-using-okta/zscaler-deception-okta-button-sign-in-page.png)