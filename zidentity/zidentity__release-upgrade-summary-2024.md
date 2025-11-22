# Release Upgrade Summary (2024)
Source: https://help.zscaler.com/zidentity/release-upgrade-summary-2024

This article provides a summary of all new features and enhancements for ZIdentity.

**Clouds:** zslogin.net, zsloginbeta.net
The following service updates were deployed to zslogin.net on

## October 11, 2024
### Feature Available
#### MFA Grace Period Removed
All ZIdentity admins are required to enroll for multi-factor authentication (MFA). The option to skip MFA enrollment for a default grace period of 14 days is no longer available. While authenticating to the subscribed Zscaler service admin portal for the first time, admins need to enroll for MFA immediately before accessing the Zscaler service admin portal.
To learn more, see [Migrating Zscaler Service Admins to ZIdentity](/zidentity/migrating-zscaler-service-admins-zslogin) and [Configuring Authentication Methods](/zidentity/configuring-authentication-methods).

### Feature Available
#### Step-Up Authentication
ZIdentity supports step-up authentication over OpenID Connect protocol with external identity providers (IdP). You can define authentication levels and configure Zscaler policies to mandate user authentication at a particular level before allowing them to access sensitive resources.
Step-up authentication enhances security by mandating multi-factor authentication (MFA) when users attempt to access sensitive resources or when risk signals indicate potential threats. This feature allows organizations to configure hierarchical authentication levels, ensuring that access control is customized to resource sensitivity. By automatically adjusting authentication requirements based on user behavior or environmental changes, organizations can protect critical data and meet compliance requirements.
[See image.](#zidentity-step-up-authentication-levels)
Additionally, administrators can map authentication levels to ACR claims in external identity provider connections to request a particular authentication context. Based on the ACR, the IdP challenges the user with an appropriate authentication policy.
[See image.](#zidentity-step-up-authentication-mapping)
To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication) and [Configuring Authentication Levels](/zidentity/configuring-authentication-levels).
[]![Authentication Levels in ZIdenity](/sites/default/files/downloads/zidentity/release-notes/release-upgrade-summary-2024/zidentity-rn-step-up-authentication.png)
[]![Advanced Tab in IdP Configuration](/sites/default/files/downloads/zidentity/release-notes/release-upgrade-summary-2024/zidentity-rn-mapping-step-up.png)

### Feature Available
#### Support for Revoking Access Tokens
You can revoke access tokens assigned to API clients to access the Zscaler service API resources.
[See image.](#zid-revoketoken)
To learn more, see [About Access Tokens](/zidentity/about-access-tokens) and [Revoking Access Tokens](/zidentity/revoking-access-tokens).
[]
![Revoke the access token](/sites/default/files/downloads/zidentity/release-notes/release-upgrade-summary-2024/zid-activetokens.png)

## August 16, 2024
### Feature Available
#### Changes to Login ID Attribute Mapping
The Login ID user attribute is no longer part of the default user attributes and the option to map it for the Just-in-Time (JIT) provisioning as an optional configuration has been removed. All external identity providers (IdPs) added to the ZIdentity Admin Portal must mandatorily include mapping for the Login ID attribute with the corresponding SAML or OIDC attribute, depending on the protocol used for the IdP integration. By default, the new IdP integrations map the Login ID attribute with `sub` or `NameID` or value for OIDC or SAML-based configurations respectively. You can map other attributes with the Login ID attribute based on your requirements.
The option to map the Login ID attribute has been moved from the Provisioning tab to the Basic tab within the Add Primary Identity Provider window (or Add Secondary Identity Provider window) accessed from Integrations > External Identities.
[See image.](#login-id-mapping)
If you have enabled JIT provisioning for your external IdPs and mapped the Login ID attribute, the mapping is retained, but the option is moved to the Basic tab.
[See image.](#login-id-migrated)
To learn more, see [About Attributes](/zidentity/about-attributes), [About External Identity Providers](/zidentity/about-external-identity-providers), [Adding OpenID Providers](/zidentity/adding-openid-providers), and [Adding SAML Identity Providers](/zidentity/adding-saml-identity-providers).
[]![Login ID Attribute Mapping](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zidentity-login-id-mapping.png)
[]
![zidentity-login-id-mapping-new.png](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zidentity-login-id-mapping-new.png)

### Feature Available
#### ZIdentity Dashboard
The ZIdentity Admin Portal dashboard tracks user activity and provides a high-level overview of all users that are managed from ZIdentity. The dashboard displays the number of users, service entitlement assignments, and graphs for authentication and user management event counts.
[See image.](#zid-db)
To learn more, see [About the Dashboard](/zidentity/reskin/about-dashboard).
[]![zid-dboard.png](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zid-dboard.png)

### Feature Available
#### ZIdentity UI Enhancement
ZIdentity's administrative user interface (UI) is updated to Zscaler's modern UX design system. The menu layout is reorganized to make it easier to access common configurations.
To learn more, see [What is ZIdentity?](/zidentity/what-zslogin)

## July 18, 2024
### Feature Available
#### Control Multi-Factor Authentication
Admins can disable multi-factor authentication (MFA) for service enrollment for users when required. This option is available only for users that have single sign-on (SSO) enabled.
[See image.](#zsl-mfase)
Admins can allow users to skip two-factor authentication (2FA) for a short duration and use only their password to log in to the assigned Zscaler service admin portal.
[See image.](#zsl-skip-auth)
To learn more, see [Configuring Authentication Methods](/zidentity/configuring-authentication-methods).
[]![Disable the MFA for service enrollment](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zsl-authenticationmethods.png)
[]![zsl-users-skipmfa.png](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zsl-users-skipmfa.png)

### Feature Available
#### MFA Enrollment for Admins
After Zscaler-driven admin migration is completed, all ZIdentity admins are required to enroll for multi-factor authentication (MFA). While configuring the admin profile, admins can initially set the password and choose to enroll for MFA immediately or skip it for a default grace period of 14 days. After the default grace period is completed, admins should enroll for MFA before accessing the subscribed Zscaler service admin portals.
To learn more, see [Migrating Zscaler Service Admins to ZIdentity](/zidentity/migrating-zscaler-service-admins-zslogin) and [Configuring Authentication Methods](/zidentity/configuring-authentication-methods).

## June 28, 2024
### Feature Available
#### Support for Zscaler Client Connector Features
ZIdentity provides support for the following features on Zscaler Client Connector:
- Device groups and service entitlement
- Machine tunnel support
- Device token-based authentication for Zscaler Client Connector as an identity provider (IdP)
- Zscaler Client Connector dynamic service enrollments
To learn more, see [Managing Device Groups](/zidentity/managing-device-groups), [Managing Device Token Authentication](/zidentity/managing-device-token-authentication), and [About Zscaler Client Connector](/client-connector/what-is-zscaler-client-connector).

## June 12, 2024
### Feature Available
#### Additional Permission for Administrative Entitlement
While adding an admin role, you can now select the Restricted Full permission for administrative entitlements in the ZIdentity Admin Portal. ZIdentity checks an acting administrator's permissions in target services before allowing them to change the entitlement assignment for those services.
[See image.](#zsl-restful)
To learn more, see [Adding ZSLogin Admin Roles](/zidentity/adding-zslogin-admin-roles).
[]![zsl-restfull.png](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zsl-restfull.png)

### Feature Available
#### Predefined Dynamic Groups
Users are added to the following dynamic groups based on user data:
- Dynamic Group Registered Domains: Dynamic group of all users from registered domains.
- Dynamic Group Guest Domains: Dynamic group of all users from guest domains.
- Dynamic Group Administrators: Dynamic group of all users with administrative entitlements.
- Zscaler Global Administrators: Initial user group with global administrative entitlements.
- Zscaler Emergency Access: User group that has Zscaler Private Access (ZPA) emergency access entitlement.
To learn more, see [About Groups](/zidentity/about-user-groups).

### Feature Available
#### Support for Zscaler Identity Proxy for Cloud Apps via ZIdentity
Zscaler Identity Proxy for Cloud Apps is supported for ZIdentity-enabled Zscaler Internet Access (ZIA) tenants.
A new system-defined session attribute, `Is Device Managed`, mapped to the appropriate external IdP's claim is passed from the ZIdentity service to the Zscaler Identity Proxy to determine the device management status and apply access policies for the cloud apps.
[See image.](#managed-device-attribute)
To learn more, see [Adding Session Attributes](/zidentity/adding-session-attributes), [Adding SAML IdPs](/zidentity/adding-saml-identity-providers), [Adding OpenID Providers](/zidentity/adding-openid-providers), and [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps).
[]
![zslogin-rn-is-deviced-managed-attribute.jpg](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zslogin-rn-is-deviced-managed-attribute.jpg)

## June 05, 2024
### Feature Available
#### ZIdentity Admin Migration
ZIdentity admin migration is effective from June 2024. With ZIdentity migration, administrator data and their roles are migrated from various Zscaler services to ZIdentity, offering a unified identity management and authentication experience. Administrators can authenticate and access all Zscaler service admin portals with a single set of credentials, eliminating the need for multiple login credentials.
To learn more, see [Migrating Zscaler Service Admins to ZIdentity](/zidentity/migrating-zscaler-service-admins-zslogin).

## May 16, 2024
### Feature Available
#### Session Attributes for Users
ZIdentity provides support session attributes. ZIdentity records attributes related to the user’s session and makes them available to the Zscaler service, like Zscaler Private Access (ZPA). ZPA can define policies to enforce access based on session context. The ZIdentity admins can add and manage the session attributes.
[See image.](#zsl-sa)
To learn more, see [About Attributes](/zidentity/about-attributes) and [Adding Session Attributes](/zidentity/adding-session-attributes).
[]![Session attributes](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zsl-sessionattrib.png)

### Feature Available
#### Support for Customizing Logo and Emails
ZIdentity provides support for rebranding. You can replace the Zscaler logo with a different logo and add a different email address that is used by the Zscaler service to send emails to your users.
To learn more, see [Customizing Branding](/zidentity/customizing-branding%20).

### Feature Available
#### Support for Department Attribute
Department is available as a system-defined user attribute that can be viewed and edited in the ZIdentity Admin Portal. You can assign users to the required department.
[See image.](#zsl-dept)
To learn more, see [About Departments](/zidentity/about-departments) and [Adding Users](/zidentity/adding-users).
[]![Assign a department](/sites/default/files/downloads/zslogin/release-notes/release-upgrade-summary-2024/zsl-deptattribute.png)
