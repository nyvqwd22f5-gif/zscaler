# IdP Configuration Best Practices
Source: https://help.zscaler.com/unified/idp-configuration-best-practices
PDF: https://help.zscaler.com/pdf/com/en/1491096.pdf

Regardless of the identity provider (IdP) you [configure for single sign-on](/unified/configuring-idp-single-sign) (SSO), the following best practices apply.
Best Practices for User SSO
- If you also use Zscaler Client Connector for Internet & SaaS, authentication into Zscaler Client Connector for internet access should also use SAML and ideally the same IdP as Private Applications in order to avoid having the user log in twice.
- It is not possible to associate a Private Applications account to a Zscaler Client Connector account on different clouds.
- If Internet & Saas and Private Applications are using the same IdP, then users can access applications using Zscaler Client Connector or Browser Access.
- If the IdPs are not being used by Internet & SaaS, authentication domains must be configured. Zscaler Client Connector does not require these domains. As a result, users can access applications using Browser Access only.
- If you are changing IdPs for user SSO, be aware that:
- If the NameID of the user for the new IdP is different from the NameID for the old IdP, then the user will see an Authentication Error message, but they will not be prompted to reauthenticate. The user needs to sign out and then sign back in to properly authenticate against the new IdP.
- If the NameID of the user for the new IdP is the same as the NameID for the old IdP, then the user will see an Authentication Error message, but they will be prompted to reauthenticate.
- If you are updating IdP certificates, be aware that the user will see an Authentication Error message in Zscaler Client Connector and will need to reauthenticate.
Best Practices for Admin SSO
- If you are configuring your IdP for admin SSO, make sure that an admin account exists and that NameID in the SAML assertion matches the admin account.
Best Practices for Configuring Multiple IdPs
Zscaler recommends configuring multiple IdPs for:
- Users that are authenticating via Browser Access and do not require the Zscaler Client Connector.
- Organizations who are using Zscaler Client Connector only for Private Applications.
To learn more, see [About IdP Configuration](/unified/about-idp-configuration).