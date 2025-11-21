# IdP Configuration Best Practices
Source: https://help.zscaler.com/zpa/idp-configuration-best-practices
PDF: https://help.zscaler.com/pdf/com/en/1484256.pdf

Regardless of the identity provider (IdP) you [configure for single sign-on](/zpa/configuring-idp-single-sign) (SSO), the following best practices apply.
Best Practices for User SSO
Zscaler recommends you are aware of the following best practices for user SSO:
- If you also use Zscaler Client Connector for Zscaler Internet Access (ZIA), authentication into Zscaler Client Connector for internet access should also use SAML and ideally the same IdP as ZPA to avoid having the user log in twice.
- It is not possible to associate a ZPA account to a Zscaler Client Connector account on different clouds.
- If ZIA and ZPA are using the same IdP, then users can access applications through ZPA using Zscaler Client Connector or Browser Access.
- If the IdPs in ZPA are not being used by ZIA, authentication domains must be configured in ZPA. Zscaler Client Connector does not require these domains. As a result, users can access applications through ZPA using Browser Access only.
- If the authentication domain associated with the IdP configured in ZPA is not associated with the IdP configured in ZIA, users will see an error when using that domain for authentication in ZIA.
Best Practices for Admin SSO
If you are configuring your IdP for admin SSO, make sure that a ZPA admin account exists and that NameID in the SAML assertion matches the admin account.
Best Practices for Configuring Multiple IdPs
Zscaler recommends configuring multiple IdPs for:
- Users that are authenticating via Browser Access and do not require Zscaler Client Connector.
- Organizations who are using Zscaler Client Connector only for ZPA.
To learn more, see [About IdP Configuration](/zpa/about-idps).
Best Practices for IdP Migration
Zscaler recommends editing the existing IdP to migrate to a new IdP. Adding a new IdP for migration can duplicate groups and departments, and your existing policies might no longer apply.
To learn more, see [Migrating to a New IdP Configuration](/zpa/migrating-new-idp-configuration).