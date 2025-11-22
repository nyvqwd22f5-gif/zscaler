# Release Upgrade Summary (2023)
Source: https://help.zscaler.com/zidentity/release-upgrade-summary-2023

This article provides a summary of all new features and enhancements for ZIdentity.

**Clouds:** zslogin.net, zsloginbeta.net
The following service updates were deployed to zslogin.net on

## August 29, 2023
### Feature Available
#### Support for Multi-Factor Authentication
You can now enable and enforce multi-factor authentication for users that authenticate to ZSLogin. The users can choose to configure their [authentication preferences](/zidentity/configuring-authentication-preference) to access their ZSLogin account based on the [authentication methods](/zidentity/configuring-authentication-settings) (Administration > Authentication Methods) set by the ZSLogin admin.
[See image.](#auth-method-img)
As a ZSLogin admin, you can view and manage the authenticators for each user from their respective user window (Administration > Users > click the Edit icon for the user > Security Settings).
[See image.](#authenticators-img)
To learn more, see [Setting Up Your Zscaler Account](/zidentity/setting-your-zscaler-account), [Configuring Authentication Methods](/zidentity/configuring-authentication-settings), [Configuring Authentication Preference](/zidentity/configuring-authentication-preference), and [Viewing User Entitlements and Authenticators](/zidentity/viewing-user-entitlements-and-authenticators).
[]![Authenticator Information in the Security Settings tab](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-mfa-authenticators_0.png)
[]![Authentication Method page](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-authentication-methods.png)

### Feature Available
#### Support for OpenID Connect
ZSLogin service now supports the OpenID Connect (OIDC) protocol as a Relying Party (RP). OIDC is a single sign-on protocol much like SAML, which is used to authenticate users at your OpenID Provider (OP) and to assert their authenticated identities to ZSLogin.
[See image.](#oidc-config-img)
To learn more, see [Adding OpenID Provider](/zidentity/adding-openid-provider).
[]![OIDC provider configuration window](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-basic-tab-add-oidc_0.png)

### Feature Available
#### Support for User Enrollment to Zscaler Services
You can now use the ZSLogin service to enroll users to your subscribed Zscaler services, mitigating the effort of managing users for each service separately.
[See image.](#service-img)
To support this feature:
- The ZSLogin Admin Portal is introduced with a new Entitlements section inside the Administration menu (Administration > Administrative and Administration > Service) to manage service admins and service users separately.
[See image.](#menu-img)
- The existing Zscaler Services page (Administration > Zscaler Services) is no longer available.
[See image.](#services-menu-img)
- You can configure role-based administration for ZSLogin admins to implement granular permissions, such as controlling whether or not an admin can modify user records, assigning users to services, etc.
[See image.](#roles-img)
- You can view the service assignments for each user from their respective user window (Administration > Users > click the Edit icon for the user > Entitlements).
[See image.](#view-entitlements-img)
- Two new options, Authentication Session for service enrollment and Force Authentication for Private Access Reauthentication, are added to the Advanced Settings page (Administration > Advanced Settings).
[See image.](#advcd-settings-img)
To learn more, see U[nderstanding Entitlements](/zidentity/understanding-entitlements), [About ZSLogin Admin Roles](/zidentity/about-zslogin-admin-roles), [Configuring Advanced Settings](/zidentity/configuring-advanced-settings) and [Viewing User Entitlements and Authenticators](/zidentity/viewing-user-entitlements-and-authenticators).
[]![Image of the Advanced Settings page in the ZSLogin Admin Portal](/sites/default/files/downloads/tech-pubs-drafts/zia-draft-articles/about-shadow-it-report-doc-48651/ZSLogin-advanced-settings.png)
[]![Zscaler Services Page](/sites/default/files/downloads/ZSLogin-Zscaler-services-menu.png)
[]![Roles-page ](/sites/default/files/downloads/ZSLogin-Roles-page.png)
[]![ZSLogin menu ](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-entitlments-menu.png)
[]![Service Entitlements page](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-Service%20entitlments.png)
[]![View Entitlments for user in the Edit User window](/sites/default/files/downloads/zslogin/administration/adding-openid-provider/ZSLogin-entitlement-info.png)
