# Administrator Management Settings
Source: https://help.zscaler.com/zdx/administrator-management-settings
PDF: https://help.zscaler.com/pdf/com/en/1456556.pdf

On the Administrator Management page (Administration > Administrator Management > Administrator Management), you can configure restricted access for admins, password expiration, and SAML authentication for admins.
The Administrator Management page shows a link to the ZIdentity Admin Portal if you are subscribed to ZIdentity. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What is ZIdentity?](/zidentity/what-zidentity).
Password Management
If you're using the Zscaler-hosted [admin](/zdx/about-administrators) database to authenticate admins, you can enable password expiration for all admins logging in to the Zscaler Internet Access (ZIA) and Zscaler Digital Experience (ZDX) Admin Portal. To learn more, see [Configuring Password Expiration](/zdx/configuring-password-expiration).
SAML Authentication for Administrators
Admins can be authenticated via SAML using an external admin database rather than the admin database in the ZDX Admin Portal. The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. You can integrate admin authentication with your existing two-factor authentication solution. The Zscaler service supports SAML 2.0 and later. To learn more, see [Configuring SAML for Admins](/zdx/configuring-saml-zdx-admins).
The Zscaler service doesn't enforce password expiration for external admin databases using SAML.
Advanced Configuration
Admins can configure an action when SCIM deletes a linked user account.
- **Do Nothing**: When SCIM deletes a linked user account, the ZDX admin account is not deleted.
- **Delete Account**: When SCIM deletes a linked user account, the ZDX admin account is also deleted.
[See image.](#administrator-management)
[]![Administrator Management Page](/downloads/tech-pubs-drafts/zdx-draft-articles/about-administration-management-draft/ZDX-AdministratorManagement.png)