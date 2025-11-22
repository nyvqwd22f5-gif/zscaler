# About Identity Providers
Source: https://help.zscaler.com/dspm/about-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1474796.pdf

An identity provider (IdP) is a service that stores and manages user identity and authenticates users to access applications. IdPs work with single sign-on (SSO) providers to authenticate users. An SSO is a service that enables users to sign in once to access all their applications.
When configuring SAML for users, you can configure only one identity provider (IdP) for your organization. The Zscaler service redirects users to the SAML URL based on the configured IdP criteria. You can configure just-in-time (JIT) provisioning and IdP-initiated SSO.
You can add only one IdP configuration for a single tenant.
The identity providers provide the following benefits and enable you to:
- Provide a quick and simple way for admins to assign multiple users to an IdP.
- Leverage single authentication using the configured IdPs to allow users to sign in to the DSPM Admin Portal.
About the Single Sign-On Page
On the Single Sign-On page (Administration > Authentication & Authorization > Single Sign-On), you can do the following:
- [Add an IdP Configuration](/dspm/adding-identity-providers).
- View the following details after you add an IdP:
- **Name**: The IdP name.
- **Status**: The status (Enabled or Disabled) of the IdP.
- **Identity Provider Issuer**: The URL of the IdP issuer.
After you add one IdP configuration, the **Add IdP Configuration** button is not visible. However, you can [edit or delete](/dspm/editing-or-deleting-idp) the configured IdP as required. [See image.](#editdeleteidp)
![View the IdP page](/downloads/dspm/authentication/idp-configuration/about-identity-providers/dspm-sso-page.png)
[]![Edit or delete the configured IdP](/downloads/dspm/authentication/idp-configuration/about-identity-providers/dspm-sso-configured.png)