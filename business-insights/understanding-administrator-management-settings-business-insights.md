# Understanding Administrator Management Settings in Business Insights
Source: https://help.zscaler.com/business-insights/understanding-administrator-management-settings-business-insights
PDF: https://help.zscaler.com/pdf/com/en/1473136.pdf

On the Administrator Management page (Administration > Administrator Management > Administrator Management), you can configure password expiration, SAML authentication, and other settings for admins.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#zidentity-administration)
Password Management
If you're using the Zscaler-hosted admin database to authenticate admins, you can enable password expiration for all admins logging in to the Business Insights Admin Portal. To learn more, see [Configuring Password Expiration](/business-insights/configuring-password-expiration-business-insights).
SAML Authentication for Administrators
Admins can be authenticated via SAML using an external admin database rather than the admin database in the Business Insights Admin Portal. The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. You can integrate admin authentication with your existing two-factor authentication solution. The Zscaler service supports SAML 2.0 and later. To learn more, see [Configuring SAML for Admins](/business-insights/configuring-saml-admins-business-insights).
The Zscaler service doesn't enforce password expiration for external admin databases using SAML.
Advanced Configuration
You can choose the action to be taken on admins when their linked user accounts are deleted using the System for Cross-Domain Identity Management (SCIM) protocol. You can allow SCIM to delete the admin and its linked user account, or prevent SCIM from deleting it. To learn more, see [Configuring Advanced Configuration for Admins](/business-insights/configuring-advanced-configuration-admins).
![Administrator Management](/downloads/business-insights/authentication-administration/understanding-administrator-management-settings-business-insights/Business-Insights-Administrator-Management-page.png)
![Administrator Management page for ZSLogin-enabled tenants](/downloads/business-insights/authentication-administration/understanding-administrator-management-settings-business-insights/Business-Insights-ZIdentity-Administration.png)
[]