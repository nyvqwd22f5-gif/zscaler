# Configuring the Authentication Session
Source: https://help.zscaler.com/unified/configuring-authentication-session
PDF: https://help.zscaler.com/pdf/com/en/1505596.pdf

ZIdentity uses session-based authentication to keep track of the authenticated users or enrolled services.
To configure the authentication session:
- Go to **Administration** > **Identity **>** ZIdentity** > **Authentication Session**.
-
On the **Settings **page:
- **Administrator Inactivity Timeout Duration (in Minutes)**: Enter the timeout period after which the user is logged out from a ZIdentity session. You can set the timeout period from 5 to 600 minutes (10 hours).
- **Authentication Session for Service Entitlement**: Enable this option if you want ZIdentity's authenticated session to apply to Zscaler services for enrolling users. This option is disabled by default, as the ZIdentity service sends users to the organization's identity provider (IdP) for authentication. This option is shown only when the User Single Sign-On (SSO) feature is enabled for your tenant.
- **Service Entitlement Session Timeout (in Minutes)**: Enter the timeout period after which the user is logged out from a Zscaler service session. You can set the timeout period from 5 to 600 minutes (10 hours).
-
**Force Authentication for Private Access Reauthentication**: This option is disabled by default. The ZIdentity service does not send this parameter to the IdP and allows the IdP's settings to determine whether or not to prompt the user for authentication. Enable this option for your configured IdPs or hosted users when the Private Applications service requests reauthentication. When enabled, ZIdentity sends a parameter to the IdP and informs the IdP to ignore ZIdentity's authentication session for the user and prompt the user for authentication whenever the Private Applications service requests reauthentication. This option is shown only when user Single Sign-On (SSO) is enabled for your tenant.
By default, only the Hosted option is shown for all tenants. The options for third-party IdPs are also listed, depending on the [external IdPs configured](/unified/about-external-identity-providers) for the tenant.
[See image.](#zsl-authsession)
-
Click **Save**.
[]![Configure the authentication session](/downloads/unified/administration/zidentity/authentication/configuring-authentication-session/ec-authsettingspage.png)