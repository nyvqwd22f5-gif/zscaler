# Step-by-Step Configuration Guide for ZIdentity
Source: https://help.zscaler.com/zidentity/step-step-configuration-guide-zidentity
PDF: https://help.zscaler.com/pdf/com/en/1499171.pdf

This article provides the recommended configuration steps to begin using ZIdentity for your organization.
Before you begin configuring ZIdentity, Zscaler recommends reading the following articles:
- [What Is ZIdentity?](/zidentity/what-zidentity)
- [Accessing and Navigating the ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page)
- [Accessing and Navigating the ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal)
ZIdentity supports only the following versions of Zscaler Client Connector:
- Zscaler Client Connector for Windows 4.4 and later
- Zscaler Client Connector for macOS 4.2 and later
- Zscaler Client Connector for Android 3.9 and later
Configuring ZIdentity
To configure ZIdentity:
- [Step 1: Set Up Your ZIdentity Account](#setup-zslogin)
- [Step 2: Add Users to ZIdentity](#step2-add-users)
- [Step 3: Configure Authentication Session Controls (Optional)](#step3-configure-auth-sessions)
- [Step 4: Update Password Policies (Optional)](#step4-password-policy)
- [Step 5: Configure Admin Sign-On Policies (Optional)](#step5-sign-on-policy)
- [Step 6: Create Custom Roles (Optional)](#step6-custom-roles)
- [Step 7: Sync Domains](#step7-sync-domains)
- [Step 8: Assign Entitlements to Users and User Groups](#step8-entitlements)
- [Step 9: Configure Step-Up Authentication (Optional)](#step9-stepUp)
[]To set up your ZIdentity account, see [Setting Up Your Zscaler Account](/zidentity/setting-your-zscaler-account).
[]You can add users using one of the following methods:
- Integrate ZIdentity with an [External IdP](/zidentity/integration/external-idp-configuration).
- [Add users](/zidentity/adding-users) to the ZIdentity Admin Portal as hosted users.
- (Optional) To allow administrators to use FIDO as the primary authenticator without the password requirement, enable the **Allow FIDO2 as Primary Authenticator** option from the [Authentication Methods](/zidentity/configuring-authentication-methods) page.
-
(Optional) To prompt users for MFA enrollment during authentication, enable the **Multi-Factor Authentication (MFA) for Service Enrollment** option from the [Authentication Methods](/zidentity/configuring-authentication-methods) page.
All admins, including the super admin (admin@xxxxx.net), must enroll an MFA authenticator after initially setting up their password.
[]To enable more controls, such as the administrator’s **Idle Session Timeout**, **Authentication Session for Service Enrollment**, and **Force Authentication for Private Access Reauthentication**, see [Configuring the Authentication Session](/zidentity/configuring-authentication-session).
[]To modify the password policy configuration to comply with your organization’s requirements, see [Configuring the Password Policy](/zidentity/configuring-password-policy).
[]To create rules to allow or deny access from a specific location, see [Configuring Admin Sign-On Policy](/zidentity/configuring-sign-on-policy). The Admin Sign-On policies are created using [IP locations](/zidentity/adding-ip-locations) or [IP location groups](/zidentity/adding-ip-location-groups).
[]To create custom roles in ZIdentity for role-based access control for ZIdentity administrators, see [Adding ZIdentity Admin Roles](/zidentity/adding-zidentity-admin-roles).
Roles for services (e.g., Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX)) are assigned in the ZIdentity Admin Portal, while custom roles are created in the respective service Admin Portals.
[]Ensure that all the required domains are available on the **Domains **page (**Administration **> **Environment **> **Domains**).
[See image.](#domains)
Domains are automatically synced from the Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) Admin Portals every 24 hours.
[]
- To assign [administrative entitlement](/zidentity/about-administrative-entitlements) to make the user an admin to ZIdentity or other services such as Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX), etc., see [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups#service-entitlements).
- To assign [service entitlement](/zidentity/about-service-entitlements) to allow users to enroll to Zscaler services such as Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX), etc., see [Assigning Entitlements to Users and User Groups](/zidentity/assigning-entitlements-users-and-user-groups#service-entitlements).
[]To provide resource-specific, risk-based access to users, you can configure step-up authentication with external IdPs. Ensure that you have configured the necessary [authentication levels in ZIdentity](/zidentity/configuring-authentication-levels) and [access policies in supported Zscaler services](/zidentity/understanding-step-up-authentication#access-policies-mapping). Users must have ZIdentity access to configure step-up authentication. To learn more, see [Understanding Step-Up Authentication](/zidentity/understanding-step-up-authentication) and [Configuring Authentication Levels](/zidentity/configuring-authentication-levels).
ZIdentity with User Single Sign-On (SSO) is required to enable step-up authentication for the tenant. For further assistance, contact Zscaler Support.
[]![Domains Page](/downloads/tech-pubs-drafts/zslogin-draft-articles/step-step-configuration-guide-zidentity-doc-54852/domains.png)