# About Identity Providers
Source: https://help.zscaler.com/deception/about-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1531362.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
You can configure identity providers (IdPs) to support single sign-on (SSO) for users in Zscaler Deception. The IdP providers page allows you to:
- [Configure SAML for SSO.](/deception/configuring-saml-single-sign)
- [Configure SAML for SSO using Okta.](/deception/configuring-saml-okta-single-sign)
- [Configure SAML for Active Directory Federation Services](/deception/configuring-saml-active-directory-federation-services).
- [Configure SAML for Microsoft Azure Active Directory Single Sign-On](/deception/configuring-saml-azure-active-directory-single-sign).
- [Configure OpenID for SSO.](/deception/configuring-openid-single-sign)
- [Configure OpenID for SSO using Okta.](/deception/configuring-openid-single-sign-using-okta)
- [Configure OpenID for SSO using Google.](/deception/configuring-openid-single-sign-using-google)
IdPs provide the following benefits and enable you to:
- Configure third-party IdPs using OpenID or SAML.
- Leverage single authentication using the configured IdPs to allow users to sign in to the Zscaler Deception Admin Portal.
About the IdP Providers Page
On the IdP Providers page (Settings > Users & Roles > IdP Providers), you can do the following:
- Add and configure IdPs to support SSO.
- View a list of configured IdPs. For each IdP, you can view:
- **Name**: The name of the IdP configuration.
- **Type**: The type of IdP.
- **Issuer**: The URL of the IdP issuer.
- **Enabled**: The status of the IdP configuration. The checkmark icon indicates that the IdP is enabled, and the **X** icon indicates that the IdP is disabled.
- Edit or delete a [SAML](/deception/editing-or-deleting-saml-idp-configuration) or OpenID IdP.
![About the IdP page](/downloads/deception/authentication/about-identity-providers/zscaler-deception-about-idp-1.png)
If ZIdentity is enabled in Deception, you can't configure SSO using third-party IdPs in the Deception Admin Portal. You must configure IdPs in the ZIdentity Admin Portal.
The existing SSO third-party IdPs are disabled.
To configure IdPs, click the ZIdentity** **link. You are redirected to the ZIdentity Admin Portal. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).
[See image.](#deception-zidentity-config-idp-redirect-link)
[]![Configure IdP if ZIdentity is enabled](/downloads/deception/authentication/about-identity-providers/itdr-about-idp-sso-zidentity-enabled-3.png)