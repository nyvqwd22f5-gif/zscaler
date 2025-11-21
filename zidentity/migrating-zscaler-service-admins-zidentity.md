# Migrating Zscaler Service Admins to ZIdentity
Source: https://help.zscaler.com/zidentity/migrating-zscaler-service-admins-zidentity
PDF: https://help.zscaler.com/pdf/com/en/1499436.pdf

[Watch a video on ZIdentity Migration.](https://fast.wistia.net/embed/iframe/hmlnvqvvvo)
ZIdentity is the common identity service for all Zscaler products. ZIdentity provides a centralized platform for managing admin roles and entitlements across all Zscaler services. ZIdentity is being provisioned for all new customers since January 2024. Existing customers began upgrading to ZIdentity in June 2024. At this time, the majority of Zscaler customers are upgraded to ZIdentity.
Prior to ZIdentity, customers provisioned and managed administrators and end users directly in individual Zscaler services (e.g., Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), etc.). The external identity provider (IdP) integrations were also configured directly to individual Zscaler services.
With ZIdentity migration, administrator data and their role assignments are transferred from various Zscaler services and synced to ZIdentity. It also offers a unified authentication experience. Administrators can authenticate and access all Zscaler service admin portals with a single set of credentials, eliminating the need for multiple login credentials.
Migration and Upgrade Processes
ZIdentity migration includes customer-driven migration:
Customers that authenticate their Zscaler administrators with an external IdP, request for ZIdentity migration.
[Watch a video on customer-driven migration.](https://fast.wistia.net/embed/iframe/dm0oz6o33t)
[Migration Process](#zsl-customerdriven)
Enrolling for MFA
All administrators must use multi-factor authentication (MFA). You can either use Zscaler's MFA or enforce MFA with your external IdP, or both. Administrators hosted in ZIdentity are required to use Zscaler's MFA, as they are not using single sign-on (SSO) with an external IdP.
Accessing Zscaler Services After Migration
The authentication process changes after the admins are migrated to ZIdentity. After the migration, the credential validation for admins of all Zscaler services is handled by ZIdentity.
To improve security, all admins with credentials hosted at Zscaler must use MFA for admin login. The MFA options supported include security key or biometric, Google Authenticator, email OTP, and SMS OTP. To learn more, see [Accessing and Navigating the ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page).
Admins can authenticate in any of the following ways:
Zscaler recommends using a vanity domain (e.g., https://acme.zslogin.net) for simplicity and directly accessing the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page) via SSO URL.
- [Use the Two-Step Login Process](#two-step)
- [Access ZIdentity through Your Organization's External IdP](#externalidp)
- [Use the ZIdentity Vanity Domain](#vanitydomain)
- [Use of ZIA Admin API and Zscaler Cloud & Branch Connectors](#zia-api-connectors)
Password Management and User Sync Behavior with External IdPs
If admins were originally synced from ZIA or Cloud Connector and an admin API authentication attempt was performed using their old passwords to ZIA Admin Portal or Cloud & Branch Connector Admin Portal, then ZIdentity requests the ZIA or Cloud Connector services to look for the local password and copies it to ZIdentity to validate the current and subsequent API authentication calls. In such cases, ZIdentity enables the option to change passwords for admins even if their login ID domain is mapped to an external IdP. The options to change passwords in such cases are described as follows:
-
Admins synced to ZIdentity through external IdPs can change their passwords directly from the My Profile page in ZIdentity launched from the ZIdentity Landing Page or the ZIdentity Admin Portal.
[See image.](#password-change-users)
-
Admins with the [Users and Groups](/zidentity/admin-roles-and-permissions) permission in [ZIdentity roles](/zidentity/about-zidentity-admin-roles) can change passwords for users and admins synced from an external IdP by editing the corresponding user entry in the directory.
[See image.](#password-change-others)
- If ZIdentity does not maintain a local password for admins based on the API authentication event, then this option to change local passwords is not supported.
- The password management functions for users and admins synced to ZIdentity via external IdPs only work when the identities are synced to ZIdentity from downstream services (e.g., Cloud Connector). For identities provisioned from external IdPs via SCIM or JIT provisioning, the password management functions are not supported.
For existing customers, identities might not get synced if they are removed from ZIdentity during the migration process. A support ticket must be raised to force sync the users from the downstream service. This synchronization issue occurs in the following scenario:
- ZIdentity is in the provisioned state.
- An IdP is configured for ZIdentity.
- A user is deleted from ZIdentity Admin Portal manually.
- Admin migration is completed with Zscaler services.
- []Customers must contact their Zscaler Account team to provision a ZIdentity tenant and have it linked to all their Zscaler tenants.
- Zscaler sends an email to the customer to specify the Zscaler service tenants that must be linked to the ZIdentity tenant and the new ZIdentity super admin’s name and email ID.
-
Zscaler provisions the ZIdentity tenant and links the customer’s Zscaler service tenants (ZIA, ZPA, ZDX, etc.).
Next, as the ZIdentity super admin, you need to complete the following:
- When you receive the email about the new ZIdentity tenant registration, follow the instructions provided in the email and complete the registration.
- Connect your organization's external IdP to ZIdentity and provision your admins (users) to ZIdentity.
-
Inform the other admins to test ZIdentity by clicking the tile at their IdP to confirm they see the ZIdentity SSO portal ([ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page)) and the assigned Zscaler service tiles.
- The service tiles are disabled until you complete the migration.
- If the admins don't see the assigned tiles, the super admin can review the entitlements assigned to the admins on the [Entitlements tab](/zidentity/viewing-entitlements-assigned-users) in the ZIdentity Admin Portal. They can also make adjustments to the entitlements on the[ Administrative Entitlements page](/zidentity/about-administrative-entitlements).
-
When all the admins confirm they can access the ZIdentity Landing Page and see the Zscaler service tiles, go to the ZIdentity Admin Portal and click the link in the banner to proceed with the admin migration.
[See image.](#zsl-banner)
-
Read the message and click **Confirm**.
[See image.](#zsl-msg)
The ZIdentity admin migration is completed.
- []Access a Zscaler admin portal (ZIA, ZDX, ZPA, Branch Connector, Cloud Connector, or Deception).
-
Enter the login ID that you have been using.
After the migration, the credential validation for ZIA and ZPA admins is handled by ZIdentity. When ZIA or ZPA admins log in for the first time post migration, their password stored in the respective admin-portal is synced with the ZIdentity Admin Portal, and the validation is handled by ZIdentity.
- Click **Next**.
- Enter your existing password for the respective Zscaler service, then click **Next**.
-
[]When you are prompted to set up the MFA, select the required authentication method, then click **Set Up**.
[See image.](#zsl-selectauthtype)
A message appears indicating that a link is sent to your email address for completing MFA enrollment.
[See image.](#zsl-email)
- Click **Continue** and you are logged in to the respective admin portal.
- []Go to your organization's external IdP (e.g., Okta).
-
Click the Zscaler tile.
The ZIdentity page appears.
- Enter the password that you have been using.
-
After successful validation, you are logged in to the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page) that displays the assigned Zscaler service tiles.
The first admin who logs in is presented with the ZIdentity End User Service Agreement (EUSA) and they accept it. Admins can access ZIdentity only if someone from that service tenant accepts the EUSA.
-
[]Access the Zscaler assigned vanity domain (e.g., https://acme.zslogin.net).
The ZIdentity page appears.
- Enter the login ID and password that you have been using.
-
[You are prompted to set up the MFA](#zsl-setup-mfa).
After successful validation, you are logged in to the [ZIdentity Landing Page](/zidentity/accessing-and-navigating-zidentity-landing-page) that displays the assigned Zscaler service tiles.
The first admin who logs in is presented with the ZIdentity End User Service Agreement (EUSA) and they accept it. Admins can access ZIdentity only if someone from that service tenant accepts the EUSA.
[]When Cloud Connector attempts to authenticate to ZIA's admin API and ZIA is linked to ZIdentity, ZIA receives the request and then attempts to validate the credentials with ZIdentity. If ZIdentity has a hosted user with that username and password, it validates the credentials and provides a successful response to ZIA. Then, ZIA responds to Cloud Connector with a success message, completing authentication to the ZIA Admin API.
User accounts with login ID domains that are associated with an external IdP can still be used for the Cloud Connector use case in some scenarios.
ZIdentity does not support users with both IdP mapping and passwords. However, to provide a seamless migration experience, passwords from ZIA are still synced to ZIdentity even if the user's domain is mapped to an IdP, retaining some password-managed functions. Additionally, Zscaler recommends that customers migrate away from such configurations where users with both password and IdP mapping are present. Customers must make necessary changes to use user identities under a vanity domain (e.g., `<your_domain>``.zslogin.net`) that cannot be mapped against an IdP.
[]![Banner indicating the admin migration status](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zid-banner.png)
[]![Read the message before proceeding with admin migration](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zid-confirmmigration.png)
[]![Selecting the authentication type](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zid-mfaoptions1_0.png)
[]![Link sent to email ID](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zsl-enrolllink_0%20(1).png)
[]![Options to change password for users and admins in the ZIdentity Landing Page and the ZIdentity Admin Portal](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zidentity-self-change-password.png)
[]![The Edit User drawer showing the Security Settings tab where you can change passwords for users and admins](/downloads/zidentity/getting-started/migrating-zscaler-service-admins-zidentity/zidentity-change-password-for-others.png)