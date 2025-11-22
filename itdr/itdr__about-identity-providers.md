# About Identity Providers
Source: https://help.zscaler.com/itdr/about-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1531737.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
You can configure identity providers (IdPs) to support single sign-on (SSO) for users. The SSO page allows you to:
- [Configure SAML for SSO](/itdr/configuring-saml-single-sign-on).
- [Configure SAML for Okta](/itdr/configuring-saml-okta-single-sign-on).
- [Configure SAML for Microsoft Entra ID](/itdr/configuring-saml-microsoft-entra-id-single-sign-on).
- [Configure SAML for Active Directory Federation Services](/itdr/configuring-saml-active-directory-federation-services).
- [Configure OpenID for SSO](/itdr/configuring-openid-single-sign).
- [Configure OpenID for Okta](/itdr/configuring-openid-single-sign-using-okta).
- [Configure OpenID for Google](/itdr/configuring-openid-single-sign-using-google).
IdPs provide the following benefits and enable you to:
- Configure third-party IdPs using OpenID or SAML.
- Leverage single authentication using the configured IdPs to allow users to sign in to the Zscaler ITDR Admin Portal.
About the IdP Providers Page
On the IdP Providers page (Settings > Users & Roles > IdP Providers), you can do the following:
- Add and configure [SAML](/itdr/configuring-saml-single-sign-on) or [OpenID](/itdr/configuring-openid-single-sign) IdPs to support SSO.
- View a list of configured IdPs. For each IdP, you can view:
- **Name**: The name of the IdP configuration.
- **Type**: The type of IdP.
- **Issuer**: The URL of the IdP issuer.
- **Enabled**: The status of the IdP configuration. The checkmark icon indicates that the IdP is enabled, and the **X** icon indicates that the IdP is disabled.
- Edit or delete an [SAML](/itdr/editing-or-deleting-saml-idp-configuration) or [OpenID](/itdr/editing-or-deleting-openid-idp-configuration) IdP configuration.
![About the IdP Providers page](/downloads/itdr/authentication/about-identity-provider/zscaler-deception-about-idp-1.png)
If ZIdentity is enabled, you can't configure SSO using third-party IdPs in the ITDR Admin Portal. You must configure IdPs in the ZIdentity Admin Portal.
The existing SSO third-party IdPs are disabled.
To configure IdPs, click the ZIdentity** **link. You are redirected to the ZIdentity Admin Portal. To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).
[See image.](#itdr-zidentity-config-idp-redirect-link)
[]![Configure SSO when ZIdentity is enabled](/downloads/itdr/authentication/about-identity-provider/itdr-about-idp-sso-zidentity-enabled-3.png)