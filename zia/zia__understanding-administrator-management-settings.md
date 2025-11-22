# Understanding Administrator Management Settings
Source: https://help.zscaler.com/zia/understanding-administrator-management-settings
PDF: https://help.zscaler.com/pdf/com/en/1399691.pdf

[Watch a video about Administrator Management.](https://fast.wistia.net/embed/iframe/x3gbej6t7a)
On the Administrator Management page (Administration > Administrator Management > Administrator Management), you can configure restricted access, password expiration, SAML authentication, and the advanced configuration setting for admins.
[See image.](#Admin-settings)
The Administrator Management page shows a link to the ZIdentity Admin Portal if you are subscribed to ZIdentity. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
About Restricted Access
To enable this feature, contact your Zscaler Account team.
Zscaler allows admins with full permissions to enforce access restrictions for the admins logging in to the ZIA Admin Portal based on their source IP addresses. You need to specify or allowlist the source IP addresses of the admins for whom you want to provide access to the ZIA Admin Portal. You can also enable automatic access for the admins who log in via SAML authentication or through a known Zscaler Proxy. To learn more, see [Configuring Restricted Access for Admins](/zia/configuring-restricted-access-admins).
Enabling this feature does not restrict access to the admins who log in via SSO from another Zscaler product or via remote assistance from Zscaler Support.
About Password Management
If you're using the Zscaler-hosted [admin](/zia/about-administrators) database to authenticate admins, you can enable password expiration for all admins logging in to the ZIA and Zscaler Digital Experience (ZDX) Admin Portals. To learn more, see [Configuring Password Expiration](/zia/configuring-password-expiration).
Changing your password is managed from your user profile. To learn more, see [Customizing Your Account Settings](/zia/customizing-your-admin-account-settings).
About SAML Authentication for Administrators
Admins can be authenticated via SAML using an external admin database rather than the admin database in the ZIA Admin Portal. The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. You can integrate admin authentication with your existing two-factor authentication solution. The Zscaler service supports SAML 2.0 and later. To learn more, see [Configuring SAML for Admins](/zia/configuring-saml-admins).
The Zscaler service doesn't enforce password expiration for external admin databases using SAML.
About Advanced Configuration
Admins can choose the action to be taken against an admin account if the linked admin *user account *is deleted using the System for Cross-Domain Identity Management (SCIM) protocol. Admins can allow SCIM to delete the admin user and its linked user account, or they can prevent SCIM from deleting the admin user and its linked user account. To learn more, see [Configuring Advanced Configuration for Admins](/zia/configuring-advanced-configuration-admins).
[]![Image of Administrator Management Settings](/downloads/zia/authentication-administration/administrator-role-management/about-administrator-management/ZIA-6.2r-Admin-Management_Settings-6-30-23.png)