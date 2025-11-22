# Enabling Private Applications Partner Logins
Source: https://help.zscaler.com/unified/enabling-private-applications-partner-logins
PDF: https://help.zscaler.com/pdf/com/en/1491416.pdf

A partner is a separate entity or company that owns a Private Applications tenant. You can give partner organizations access to your organization's tenant. You can also allow your users to access a partner organization's tenant. A partner organization must have these same settings configured for their own tenant as well to ensure users from your organization and their organization can access each other's tenants.
To enable partner logins for Private Applications:
- In the Admin Portal, go to **Administration > Identity > Private Access > Partner Login**.
- Under **Allow Partner Login to This Tenant**:
- **No Access**: Select this option to disallow access to your tenant to any partner organizations.
-
**Specific Tenants**: Select this option to allow access to your tenant by specific tenants:
- **Allow Following Primary Tenants to Connect to this Tenant**: Enter a fully qualified domain name (FQDN) for the partner tenant and, optionally, a cloudname. If no cloudname is entered, a user on the partner domain on any cloudname can access your tenant.
-
**Restrict Old Zscaler Client Connector Versions to Select to this Tenant**: Enable to allow only partner tenant devices using Zscaler Client Connector version 4.7 and later for Windows to log in to this tenant.
If you enable this option, any existing partner tenants using Zscaler Client Connector for macOS or version 4.6 and earlier for Windows are unenrolled.
The **Specific Tenants** option applies only to Zscaler Client Connector 4.7 and later for Windows.
- **All Tenants**: Select this option to give access to your tenant to all partner organizations.
-
Enable **Allow Users of This Tenant to Login to Other Tenants** to let your users access a partner's tenant. By default, this setting is disabled.
If you use Zscaler Client Connector version 4.6 and later for Windows, you can configure access to a partner’s tenant on the [app profile](/unified/configuring-zscaler-client-connector-app-profiles). Partner login settings that are enabled on the app profile override these settings.
[See image.](#Enable-partner-login)
- Click **Save**.
[]![Enable partner login options](/downloads/zscaler-client-connector/platform-and-authentication-management/zpa-partner-login/enabling-zpa-partner-logins/zclient-connector-zpa-partner%20logins_0.png)