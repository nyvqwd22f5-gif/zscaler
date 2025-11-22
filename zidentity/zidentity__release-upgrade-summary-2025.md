# Release Upgrade Summary (2025)
Source: https://help.zscaler.com/zidentity/release-upgrade-summary-2025

This article provides a summary of all new features and enhancements for ZIdentity.

**Clouds:** zslogin.net, zsloginbeta.net
The following service updates were deployed to zslogin.net on

## October 31, 2025
### Feature Available
#### Common Domain for Multiple ZIdentity Tenants
ZIdentity provides support for using the same domain for multiple tenants within a single ZIdentity cloud environment. If two or more tenants share a common domain, users might be prompted to select their tenant from a drop-down menu during login. This experience is applicable to the following services using [OpenID Connect (OIDC)](/zidentity/adding-openid-providers) flow to redirect users to ZIdentity:
- Experience Center
- Zscaler Breach Predictor
- External Attack Surface Management (EASM)
- Data Security Posture Management (DSPM)
[See image.](#common-domain)
[]
![ZIdentity Login page displaying the dropdown to select the tenant when there are multiple tenants in one domain.](/sites/default/files/downloads/common-domain1.png)

## October 10, 2025
### Feature Available
#### Enhancements to External Identities Certificate Management
The External Identities Certificate Management feature is updated with the following enhancements:
Notification for SAML Certificate Expiration
If any of the SAML certificates (IdP Certificate or SAML Request Signing and Decryption Certificate) are about to expire within 90 days or have already expired, a banner appears on all the pages in the ZIdentity Admin Portal, and a visual indicator is displayed on the External Identities page. During the last 90 days before certificate expiration, the administrator receives weekly email reminders until the certificate is updated. After the certificate expires, the administrator receives two more reminder emails to take the necessary action.
[See image.](#notification)
To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).
Upload Multiple IdP Certificates
ZIdentity provides support for uploading multiple IdP certificates, enabling seamless transition with IdP certificate rotations.
[See image.](#multiple-idps)
To learn more, see [Adding SAML ZIdentity Providers](/zidentity/adding-saml-identity-providers).
Update SAML Request Signing and Decryption Certificate
You can add a new SAML Request Signing and Decryption Certificate when the existing one is about to expire or as needed. Administrators can select a new certificate before the old certificate expires to prevent authentication issues with the IdP.
[See image.](#SAML-request-signing-and-decryption-certificate)
To learn more, see [Adding SAML ZIdentity Providers](/zidentity/adding-saml-identity-providers).
[]
![The External Identities page displaying the notifications for request signing and decryption certificates that is about to expire or already expired.](/sites/default/files/downloads/RN-external-idp-banner1.png)
[]![Enter Manually tab on Edit Secondary Identity Provider page that displays the capability of adding multiple  IdP certificates.](/sites/default/files/downloads/zidentity/authentication/using-zidentity-identity-provider/Enter-manually-tab.png)
[]![Advanced tab on Edit Secondary Identity Provider page displaying the option to update SAML request signing and decryption certificate.](/sites/default/files/downloads/zidentity/authentication/using-zidentity-identity-provider/Advanced-tab.png)

## September 08, 2025
### Feature Available
#### Token Validators
You can create and use token validators in the ZIdentity Admin Portal to validate the JSON Web Token (JWT) that is used for authorization to access Zscaler services, like Zscaler Internet Access (ZIA).
[See image.](#tokenvalidator)
To learn more, see [About Token Validators](/zidentity/about-token-validators), [Adding a Token Validator](/zidentity/adding-token-validator), and [Testing an Access Token](/zidentity/testing-access-token).
[]![The Token Validators page with Add Token Validator and Test token options and displaying the configured token validators. ](/sites/default/files/downloads/tech-pubs-drafts/zidentity-draft-articles/admin-roles-and-permissions-doc-57090/Token%20Validators-RN.png)

## September 03, 2025
### Feature Available
#### API Client Access Policy
You can now define API client access policy rules to manage the API client's access to specific resources within a set time frame. Administrators can define the policy rules and assign them to the required API clients. This allows you to control and manage authorization.
[See image.](#api-client-access-policy)
To learn more, see [About the API Client Access Policy](/zidentity/about-api-client-access-policy) and [Adding API Client Access Policy Rule](/zidentity/adding-api-client-access-policy-rule).
[]
![API client access policy page displaying the configured rules with status. ](/sites/default/files/downloads/zidentity/integration/oneapi-authentication/about-api-client-access-policy/api-client-access-policy.png)

## August 29, 2025
### Feature Available
#### Updates to MFA
The SMS OTP authentication steps are updated and simplified. After entering the login ID and password, admins are no longer prompted to re-enter the country and phone number but can directly enter the SMS OTP for authentication.
To learn more, see [Setting Up Your Zscaler Account](/zidentity/setting-your-zscaler-account) and [Configuring MFA](/zidentity/configuring-mfa).

## August 08, 2025
### Feature Available
#### Authentication Events in Audit Logs
Administrators can view authentication login and logout events on the Audit Logs page. This provides visibility into the user authentication activities within your tenant.
[See image.](#Audit-logs)
To learn more, see [About Audit Logs](/zidentity/about-audit-logs).
[]
![Audit Logs page displaying authentication logs with blurred Resource and Client IP.](/sites/default/files/downloads/zidentity/release-notes/release-upgrade-summary-2025/zidentity-rn-audit-logs.png)

## July 15, 2025
### Feature Available
#### APIs for Identity and Lifecycle Management
ZIdentity supports APIs that give you programmatic access for managing identity and authentication-related features. The APIs allow you to integrate with ZIdentity for seamless identity lifecycle management and API client management.
To access and use the APIs, you must [add an API client](/zidentity/adding-api-client). Only admins with full access to the [API Clients & Resource role](/zidentity/adding-zidentity-admin-roles#API-Clients-and-resources) can add API clients.
[See image.](#zid-rn-add-api-client-image)
To learn more, see [Understanding ZIdentity APIs](/zidentity/understanding-zidentity-apis) and [Working with ZIdentity APIs](/zidentity/api-clients).
[]![Add an API client in the ZIdentity Admin Portal](/sites/default/files/downloads/zidentity/release-notes/release-upgrade-summary-2025/zid-rn-api-client-key.png)

## July 10, 2025
### Feature Available
#### MFA for Admins Using External IdP
In ZIdentity, MFA is enabled for all new and existing identity providers (IdPs) by default. Admins authenticating through external IdPs have a 7-day grace period option to temporarily skip MFA. After the grace period, they are required to configure second-factor authentication in ZIdentity if the Enforce Zscaler Admin MFA option is enabled on either the Add Primary or Secondary Identity Provider page.
Admins using MFA through their external IdP can disable the Enforce Zscaler Admin MFA option to prevent additional authentication verification from ZIdentity. This allows admins to decide whether MFA is managed by ZIdentity, their external IdP, or both.
[See image.](#2mfa-for-idp)
To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers#about) and [Adding OpenID Providers](/zidentity/adding-openid-providers).
[]
![Secondary IdP page highlighting new option "Enforce Zscaler Admin MFA". ](/sites/default/files/downloads/zidentity/getting-started/setting-your-zscaler-account/2EnforceZSAdminMFA.png)

## May 13, 2025
### Feature Available
#### IdP-Initiated SSO Redirect
For new ZIdentity tenants enabled with Experience Center, the IdP-initiated SSO redirects users to Experience Center by default.
To learn more, see [About External Identity Providers](/zidentity/about-external-identity-providers).

## January 17, 2025
### Feature Available
#### Regenerate Registration Link
You can regenerate the one-time registration link if it becomes invalid after 72 hours. An email with a new registration link is sent to the registered email address, and this link remains valid for 24 hours. You can regenerate the registration link up to three times. After three attempts, contact [Zscaler Support](/contact-support) to request a new registration link.
[See image.](#new-OTL)
[]![New One-Time Link](/sites/default/files/downloads/unified/getting-started-zscaler/admin-portal-access-navigation/resetting-login-credentials-or-mfa/OTL1.png)
To learn more, see [Setting Up Your Zscaler Account](/zidentity/setting-your-zscaler-account).
