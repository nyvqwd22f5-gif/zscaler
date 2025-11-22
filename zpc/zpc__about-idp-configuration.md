# About IdP Configuration
Source: https://help.zscaler.com/zpc/about-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1402961.pdf

An identity provider (IdP) is a service that stores and manages user identity and authenticates users to access applications. IdPs work with single sign-on (SSO) providers to authenticate users. An SSO is a service that enables users to sign in once to access all their applications.
When [configuring SAML](/zpc/configuring-saml-sso) for users, you can configure only one identity provider (IdP) for your organization. The Zscaler service redirects users to the SAML URL based on the configured IdP criteria. You can configure just-in-time (JIT) provisioning and IdP-initiated SSO. To learn more, see [About SAML](/zpc/about-saml) and [Adding an IdP Configuration](/zpc/adding-idp-configuration).
You can add only one IdP configuration for a single tenant.
About the Identity Provider Page
On the Identity Provider page (Administration > Single Sign On), you can:
- [Add an IdP Configuration](/zpc/adding-idp-configuration).
- View the following details after you add an IdP:
- **Name**: The IdP name.
- **Status**: The status (Enabled or Disabled) of the IdP.
- **Identity Provider Issuer**: The URL of the IdP issuer.
After you add one IdP configuration, the **Add IdP Configuration** button is not visible. However, you can [edit an IdP configuration](/zpc/editing-or-deleting-idp-configuration) or [delete an IdP configuration](/zpc/editing-or-deleting-idp-configuration) as required.
![View the IdP page](/downloads/zpc/authentication/idp-configuration/about-idp-configuration/zpc-about-idp-page.png)