# Understanding Administrator Management Settings in Risk360
Source: https://help.zscaler.com/risk360/understanding-administrator-management-settings-risk360
PDF: https://help.zscaler.com/pdf/com/en/1456966.pdf

On the Administrator Management page (Administration > Administrator Management > Administrator Management), you can configure password expiration and SAML authentication for admins.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#ZIdentity-administration)
Password Management
If you're using the Zscaler-hosted admin database to authenticate admins, you can enable password expiration for all admins logging in to the Risk360 Admin Portal. To learn more, see [Configuring Password Expiration](/risk360/configuring-password-expiration-risk360).
SAML Authentication for Administrators
Admins can be authenticated via SAML using an external admin database rather than the admin database in the Risk360 Admin Portal. The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. You can integrate admin authentication with your existing two-factor authentication solution. The Zscaler service supports SAML 2.0 and later. To learn more, see [Configuring SAML for Admins](/risk360/configuring-saml-admins-risk360).
The Zscaler service doesn't enforce password expiration for external admin databases using SAML.
![Administrator Management Page](/downloads/risk360/authentication-administration/administration-role-management/understanding-administrator-management-settings-risk360/Risk360-Administrator%20management-page_0.png)
[]![Link to the ZIdentity Admin Portal on the Administrator Management Page](/downloads/risk360/administration-authentication/saml-admins/configuring-saml-admins-risk360/Risk360-ZIdentity-Administration.png)