# Configuring SAML for Cloud & Branch Connector Admins
Source: https://help.zscaler.com/unified/configuring-saml-admins-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1516741.pdf

You configure and manage SAML for your admins from [ZIdentity](/zslogin/what-zslogin). To learn more, see [About Attributes](/zslogin/about-attributes).
The Zscaler service supports identity provider (IdP)-initiated SAML to authenticate admins. The admin can log in to the Admin Portal directly from a Single Sign-On (SSO) provider's portal by clicking the Zscaler application icon. This feature also enables you to integrate admin authentication with your existing two-factor authentication solution.
Admins are not added through auto-provisioning. Rather, an admin must be added in the Admin Portal and can then use SAML authentication to log into it. The Zscaler service does provide a password authentication option for admins, but the Zscaler service recommends that admins use SAML authentication to log in to the Admin Portal. However, the service also recommends that you have at least one super admin with password authentication enabled to ensure an admin can still access the Admin Portal if SAML servers external to the Zscaler service become unreachable. The Zscaler service supports SAML 2.0 and later.
IdP Configuration Guides
Following are guides for configuring admin SAML SSO with specific IdPs.
- [Admin SAML Configuration Guide for AD FS 3.0](/unified/admin-saml-configuration-guide-ad-fs-3-0-1)
- [Admin SAML Configuration Guide for Okta](/unified/admin-saml-configuration-guide-okta-1)
- [Admin SAML Configuration Guide for Azure Active Directory](/unified/admin-saml-configuration-guide-azure-active-directory-0)
When configuring other IdPs, the following information might be required:
-
The ACS URL:
https://admin.<Zscaler Cloud>.net/adminsso.do
Replace <Zscaler Cloud> with the name of the cloud on which your organization is provisioned.
- The SAML SSL certificate downloaded from the IdP must be in Base-64 encoded PEM format.
-
The Entity ID:
admin.<Zscaler Cloud>.net
Replace <Zscaler Cloud> with the name of the cloud on which your organization is provisioned.