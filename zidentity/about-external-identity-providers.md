# About External Identity Providers
Source: https://help.zscaler.com/zidentity/about-external-identity-providers
PDF: https://help.zscaler.com/pdf/com/en/1499361.pdf

You can configure primary and secondary external identity providers (IdPs) in the ZIdentity Admin Portal based on your organization's requirements. ZIdentity redirects users to different IdPs based on the configured IdP criteria for authenticating users. ZIdentity supports both [OpenID Connect (OIDC)](/zidentity/adding-openid-providers) and [Security Assertion Markup Language (SAML)](/zidentity/adding-saml-identity-providers) configurations.
- ZIdentity allows you to configure a maximum of 64 IdPs per organization.
- Users and groups from the primary IdP are stored in ZIdentity even if the primary IdP is removed from ZIdentity. This is maintained to enable an easy migration of the primary IdP from one IdP partner to another.
- Users and groups from the secondary IdP are not retained in ZIdentity if the secondary IdP is removed.
External IdPs provide the following benefits and enable you to:
- Provide a quick and simple way for admins to assign multiple users to an IdP.
- Configure IdPs with different protocols, such as OIDC and SAML for authentication and SCIM for user provisioning.
- Configure multiple IdPs for different user domains.
Protocols Supported for External IdPs
Zscaler supports various third-party IdP solutions across OIDC and SAML protocols. ZIdentity can support any IdP as long as they follow a standard SAML, OIDC, or SCIM implementation.
The following table lists some external IdPs along with the supported protocol:
[](/zidentity/configuring-microsoft-entra-id-external-idp#oidc-entra-id)[](/zidentity/configuring-microsoft-entra-id-external-idp#saml-entra-id)[](/zidentity/configuring-okta-external-idp#oidc-okta-oin)[](/zidentity/configuring-okta-external-idp#oidc-okta-custom-app)[](/zidentity/configuring-okta-external-idp#saml-okta-custom-app)[](/zidentity/configuring-microsoft-ad-fs-external-idp#oidc-based-authentication-ad-fs)[](/zidentity/configuring-microsoft-ad-fs-external-idp#saml-based-authentication-ad-fs)[](/zidentity/configuring-pingone-external-idp)[](/zidentity/configuring-auth0-external-idp)[](/zidentity/configuring-onelogin-external-idp)[](/zidentity/configuring-pingfederate-external-idp#oidc-based-authentication)[](/zidentity/configuring-pingfederate-external-idp#saml-based-authentication)
| External IdP | OIDC (Recommended) | SAML |
| ------------ | ------------------ | ---- |
| Microsoft Entra ID | Supported (via Gallery App) | Supported |
| Okta | Supported (via OIN App and Custom App) | Supported |
| Microsoft AD FS | Supported | Supported |
| PingOne | Supported | Supported |
| Auth0 | Supported | Supported |
| OneLogin | Supported | Supported |
| PingFederate | Supported | Supported |
- If you want to leverage [step-up authentication](/zidentity/understanding-step-up-authentication), it is recommended to use OIDC-based integrations as most IdPs support step-up authentication only with the OIDC protocol. SAML-based integration is recommended if you do not have an option to use any OIDC-based integration.
- Zscaler recommends using SCIM-based provisioning over Just-in-Time (JIT)-based provisioning, because SCIM has the ability to proactively synchronize identities via APIs at scheduled or on-demand intervals. In contrast, JIT updates identities reactively, relying on attributes received during user login sessions.
Admin Management in Specific Scenarios
When an admin group from the external IdP is removed, ZIdentity handles the operation depending on whether the organization used ZIdentity for Admins or ZIdentity for Admins and Users. The following table describes how ZIdentity handles the removal of an admin group from an external IdP if the user is part of both admin group and user group, and the groups are assigned to ZIdentity in the external IdP:
-
-
-
-
-
-
-
-
-
-
-
| Scenario | Entitlements | ZIdentity for Admins | ZIdentity for Admins and Users |
| -------- | ------------ | -------------------- | ------------------------------ |
| External IdP sends a *deactivate* or *disable* request via SCIM to ZIdentity (e.g., in the case Entra ID and Okta). | ZIdentity for Admins: Administrative entitlements for both ZIA and ZPA are present.ZIdentity for Admins and Users: Administrative and service entitlements for ZIA and ZPA are present. | ZIdentity: Admin is deactivated.ZIA: Admin continues to be enabled in admin and user management.ZPA: Admin is disabled in admin management only and continues to be enabled in user management.The admin is not disabled from ZIA and ZPA user management to prevent unintentional restriction of access to the internet and private applications to those admins. | ZIdentity: Admin is deactivated.ZIA: Admin is disabled in both admin management and user management.ZPA: Admin is disabled in both admin management and user management. |
| External IdP sends a *delete *request via SCIM to ZIdentity (e.g., in the case of Ping Identity). | ZIdentity removes all administrative entitlements to all services (e.g, ZIA or ZPA) for the users part of the group. | ZIdentity: Admin is deleted.ZIA: Admin is deleted from admin management but continues to be enabled in user management.ZPA: Admin is deleted from admin management but continues to be enabled in user management.The admin entitlement is removed for users that are assigned services based in group entitlements. This results in the admin getting deleted from both ZIA and ZPA admin management. |
IdP-Initiated SSO for ZIdentity Tenants Enabled with Experience Center
During the IdP-initiated SSO for ZIdentity, tenants using OIDC or SAML protocols are redirected as follows:
- [OIDC Protocol](#OIDC-protocol-redirection)
- [SAML Protocol](#SAML-protocol-redirection)
To change the default redirection, contact [Zscaler Support](/contact-support).
[]
All admins authenticating with the SAML protocol for ZIdentity and IdP integrations are redirected to Experience Center. However, if the `zidServiceId` attribute is configured in the IdP within the ZIdentity tenant, then the admins are redirected to the ZIdentity Admin Portal instead of Experience Center.
[]
ZIdentity tenants that are enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the Experience Center.
ZIdentity tenants that are not enabled with Experience Center at the time of tenant creation and admins using OIDC protocol for ZIdentity and IdP integrations are redirected to the ZIdentity Admin Portal. They can click the Experience Center link and go to the Experience Center from the [ZIdentity Landing page](/zidentity/accessing-and-navigating-zidentity-landing-page). [See image.](#Zidentity_Landing_Page)
[]About the External Identities Page
On the External Identities page (Integration > External Identities), you can do the following:
-
View the configured primary IdP. For the primary IdP, you can see:
- **Name**: The IdP's name.
- **Type**: The type of authentication method used by the IdP.
- **Zscaler Admin MFA**: Whether multi-factor authentication (MFA) in ZIdentity is enabled or disabled for admins.
- **Status**: Displays the following information:
-
Whether the IdP is enabled or disabled.
-
Whether the enabled IdP certificates are about to expire or have already expired.
- **Caution **icon: Appears when the certificate is about to expire. This icon first appears when the certificate is about to expire within 90 days.
- **Red Exclamation Mark **icon: Appears when the certificate is expired.
The alert icons only appear for enabled SAML certificates.
If you haven't configured a primary IdP, click **Add Primary IdP** to proceed with the IdP configuration. [See image.](#zsl-addprimaryidp)
- View the configured secondary IdPs. For each secondary IdP, you can see:
- **Name**: The IdP's name.
- **Type**: The type of authentication method used by the IdP.
- **Domain**: The domains assigned to the IdP.
- **Zscaler Admin MFA**: Whether MFA in ZIdentity is enabled or disabled for admins.
- **Status**: Displays the following information:
-
Whether the IdP is enabled or disabled.
-
Whether the enabled IdP certificates are about to expire or have already expired.
- **Caution **icon: Appears when the certificate is about to expire. This icon first appears when the certificate is about to expire within 90 days.
- **Red Exclamation Mark **icon: Appears when the certificate is expired.
The alert icons only appear for enabled SAML certificates.
-
Add a secondary IdP.
You must configure a primary IdP before you configure secondary IdPs.
- [Edit or delete an IdP](/zidentity/editing-or-deleting-items).
- If any of the SAML certificates (IdP certificate, SAML Request Signing and Decryption Certificate) are about to expire within 90 days or have already expired, then the ZIdentity Admin Portal displays a banner. Click the **Click here** link to manage your external IdP certificates.
![External Identities page with configured Primary and Secondary Identity Providers.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-about-external-identity-providers-doc-55564/external-idp.png)
[]![Primary Identity Provider page when it is not added. ](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-about-external-identity-providers-doc-57297/Setup-primaryIdp.png)
[]
![ZIdentity Landing Page with highlighted banner at the top.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-configuring-okta-external-idp-doc-57200/zid-landing-page-1.png)