# Administrator Management Settings
Source: https://help.zscaler.com/cloud-branch-connector/administrator-management-settings
PDF: https://help.zscaler.com/pdf/com/en/1420591.pdf

You can configure password expiration for admins on the Administrator Management page (Administration > Administrator Management > Administrators Management).  Zscaler strongly recommends implementing routine password rotation as a fundamental best practice to safeguard your organization.  To learn more, see [Configuring Password Expiration.](/cloud-branch-connector/configuring-password-expiration)
If you are subscribed to ZIdentity, the **ZIdentity Administration** link redirects you to the ZIdentity Admin Portal where admins can be managed. To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
Accessing Password Management
If you're using the Zscaler-hosted [admin](/cloud-branch-connector/about-administrators) database to authenticate admins, you can enable password expiration for all admins logging in to the Zscaler Cloud & Branch Connector Admin Portal.
Accessing SAML Authentication for Administrators
You can authenticate admins via SAML using an external database rather than the admin database in the Cloud & Branch Connector Admin Portal. The Zscaler service supports identity provider authenticating admins using SAML initiated by the identity provider (IdP). You can integrate admin authentication with your existing two-factor authentication solution. The Zscaler service supports SAML 2.0 and later. To learn more, see [Configuring SAML for Admins](/cloud-branch-connector/configuring-saml-admins).
The Zscaler service doesn't enforce password expiration for external databases that use SAML.