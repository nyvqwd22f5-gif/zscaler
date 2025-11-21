# What Is ZIdentity?
Source: https://help.zscaler.com/zidentity/what-zidentity
PDF: https://help.zscaler.com/pdf/com/en/1499041.pdf

ZIdentity is a unified identity service for Zscaler that centralizes and simplifies identity management, user authentication, and entitlement assignment for users to Zscaler services, such as Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), Zscaler Digital Experience (ZDX), etc. The services are managed through individual Zscaler admin portals (e.g., ZIA Admin Portal). If you have subscribed to more than one Zscaler service or just one service for multiple organizations, you must access these portals using different login credentials.
With ZIdentity, a single authentication into Zscaler allows users to seamlessly access Zscaler services used by their organization, without worrying about remembering or managing multiple passwords.
ZIdentity supports multi-factor authentication (MFA) for enhanced security, and it is required by default. Zscaler strongly recommends enabling MFA. You can authenticate users with a password, password and a second factor such as SMS one-time password (OTP), email OTP, Google Authenticator (TOTP), and fast identity online (FIDO) authentication.
You can use the ZIdentity service to enroll users to your subscribed Zscaler services using the ZIdentity user database. This mitigates the effort of creating a separate user database in each service's portal for provisioning users.
Key Features and Benefits
ZIdentity has the following key features and benefits:
- Seamlessly access all the subscribed Zscaler services with a single set of credentials.
- Use multi-factor authentication (MFA) to securely authenticate users.
- Control and manage admin roles and access to Zscaler services.
- Create and manage user accounts in the ZIdentity Admin Portal.
- Automatically synchronize users with identity providers through SAML just-in-time (JIT) provisioning or SCIM provisioning.
- Limit administrator access based on source IP address to ensure that admins access the system from authorized locations.
- Access audit reports to evaluate configuration changes in ZIdentity.
Accessing Zscaler Services
With ZIdentity, there are two ways to access the Zscaler portals:
ZIdentity-Initiated Access
In a ZIdentity-initiated access, users can access the portals by clicking the respective Zscaler service tile on the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page).
[See image.](#zsl-tiles)
Target Service-Initiated Access
The following flow takes place when users access a specific Zscaler service:
-
The user opens a browser and tries to access a portal (e.g., ZIA Admin Portal).
[See image.](#zsl-loginid)
- The Zscaler service checks if ZIdentity is enabled for the account. If yes, it redirects the user to ZIdentity for authentication.
-
The user authenticates themselves to the ZIdentity service with their ZIdentity credentials.
[See image.](#zsl-pwd)
- After the ZIdentity service successfully verifies the user, it logs in the user and redirects the user's browser to the service admin portal.
[]![ZSLogin Portal](/downloads/zslogin/getting-started/what-zslogin/1%20zid-landing-page.png)
[]![The Zscaler service login page](/downloads/zslogin/getting-started/what-zslogin/zsl-login.png)
[]![Entering the password](/downloads/zslogin/getting-started/what-zslogin/3%20zid-password.png)