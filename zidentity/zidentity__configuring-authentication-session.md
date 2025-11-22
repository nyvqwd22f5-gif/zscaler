# Configuring the Authentication Session
Source: https://help.zscaler.com/zidentity/configuring-authentication-session
PDF: https://help.zscaler.com/pdf/com/en/1499401.pdf

ZIdentity uses session-based authentication to keep track of the authenticated users or enrolled services.
To configure the authentication session:
- Go to **Administration** > **Authentication **> **Authentication Session**.
-
In the **Authentication Session **window:
- **Administrator Inactivity Timeout Duration (in Minutes)**: Enter the timeout period after which the user is logged out from a ZIdentity session. You can set the timeout period from 5 to 600 minutes (10 hours).
-
**Authentication Session for Service Entitlement**: Enable this option if you want ZIdentity's authenticated session to apply to Zscaler services during user enrollment. This option is disabled by default, as the ZIdentity service sends users to the organization's identity provider (IdP) for authentication. If enabled, ZIdentity can locally verify active sessions based on the **Service Enrollment Session Timeout** value, instead of always redirecting users to the IdP.
For example:
- **Zscaler Private Access (ZPA) reauthentication through Zscaler Client Connector**: During reauthentication, if the existing session is still valid, ZIdentity authenticates the user locally. If the session is expired, the user is redirected to the external IdP.
- **Browser-based access through Zscaler Internet Access (ZIA) or ZPA**: During user's access to Zscaler service through a browser, if the existing session is still valid, ZIdentity authenticates the user locally. If the session is expired, the user is redirected to the external IdP.
- **Service Enrollment Session Timeout (in Minutes)**: Enter the timeout period after which the user's service session expires, and the user is required to reauthenticate. You can set the timeout period from 5 to 600 minutes (10 hours).
-
**Force Authentication for Private Access Reauthentication**: This option determines whether to prompt the users to reauthenticate when ZPA requests reauthentication. When this option is disabled, the IdP decides if reauthentication is required for a user. When enabled, ZIdentity instructs the IdP to ignore existing user sessions and force reauthentication each time ZPA requests it by sending a parameter (for SAML protocol: `forceauth=true` and for OIDC protocol: `prompt=login`). This option is shown only when User Single Sign-On (SSO) is enabled for your tenant.
By default, only the **Hosted **option is shown for all tenants. The options for third-party IdPs are also listed, depending on the [external IdPs configured](/zidentity/about-external-identity-providers) for the tenant.
[See image.](#zsl-authsession)
- Click **Save**.
[]![Authentication Session page displaying the configured values for session.](/downloads/Zid-auth-session.png)