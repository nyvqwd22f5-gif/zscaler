# Configuring Authentication Settings
Source: https://help.zscaler.com/unified/configuring-authentication-settings
PDF: https://help.zscaler.com/pdf/com/en/1491366.pdf

To configure authentication settings for Private Applications:
- Go to **Administration **> **Identity** > **Private Access **> **Settings**.
- On the **Settings** page:
- **Enforce SSO Login For Admins**: Enable to force admins to log into the Admin Portal using single sign-on (SSO) only. If you enable this setting, you must also [enable admin SSO](/unified/configuring-idp-single-sign) in an IdP configuration.
When enabled, admins can't log in locally. They need to select **Single Sign-On Using IdP** on the Admin Portal's Sign In page or log into their IdP directly to sign in.
If this setting is enabled, the default admin account that was initially created for your organization by Zscaler (i.e., privateapplicationsadmin@<your organization's domain>.com or admin@<your organization's domain>.com) can still log in locally. To learn more, see [About Administrators](/unified/about-administrators-0).
- **CORS Request:** Enable to allow CORS (cross-origin resource sharing) to request access to selected resources from a different origin, other than its own. The browser receives a response from the server and compares the Access-Control-Allow-Origin with the requesting website’s origin, permitting access to the response if they match. By default, this is set to **Disabled**.
- **SameSite Cookie Attribution**: Enable to set the SameSite cookie attribute for application domain cookies and authentication domain cookies to None for all Browser Access applications. By default, this is set to **Disabled**.
- **Admin Portal Session Timeout (In Minutes)**: This specifies how long admins can be inactive on the Admin Portal before they are logged out. The default value is 30 minutes, but you can enter any time interval from 5 to 600 minutes. A confirmation window appears 5 minutes before an admin is logged out, asking if they want to extend their session.
- **Primary Authentication Domain**: The primary domain your organization uses for authentication. This field can be updated by contacting Zscaler Support. During authentication, the domain suffix in the NameID must match this domain or the domains listed in **Secondary Authentication Domains**.
- **Secondary Authentication Domains**: These are other domains owned by your organization, but not configured as the primary authentication domain. This field can be updated by contacting Zscaler Support. During authentication, the domain suffix in the NameID must match the additional domains listed here or the **Primary Authentication Domain**.
The primary and secondary authentication domains have no relationship to application domains, but they can overlap.
- **Max Age for Authentication with Private Service Edge**: This specifies the duration that the user’s authentication is extended when the Private Service Edge for Private Applications cannot communicate to the cloud during a customer’s network outage. This allows users to connect to Private Service Edges for Private Applications and access applications for the specified duration since the last time you authenticated. The maximum allowed limit for the duration is 7 days. You can select the duration as **Minutes**, **Hours**, **Days**, or **Weeks **from the drop-down menu. By default, this is set to **0 Days**.
This feature and its procedures are in limited availability. To learn more, contact Zscaler Support.
![Accessing authentication settings](/downloads/unified/administration/private-applications/identity/idp-device-configuration/settings/configuring-authentication-settings/unified-auth-settings-page.png)
- Click **Save**.