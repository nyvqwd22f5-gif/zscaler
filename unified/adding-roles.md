# Adding Roles
Source: https://help.zscaler.com/zscaler-client-connector/adding-roles
PDF: https://help.zscaler.com/pdf/com/en/1413006.pdf

With Role Management, you can manage access to Zscaler Client Connector Portal settings.
For ZIdentity-enabled tenants (that are linked to ZIdentity), admin roles must be assigned in the ZIdentity Admin Portal. To learn more, see [About Administrative Entitlements](/zidentity/about-administrative-entitlements).
The following three permissions are available when you add a role. You can also create a custom access level based on these permissions:
- **Full**: View and configure settings.
- **View Only**: View settings.
- **None**: Setting is hidden.
To add a role:
- In the Zscaler Client Connector Portal, go to **Administration** > **Administration Management**.
- Click the **Role Management **tab.
- Click **Add Role**.
[See image.](#RM)
-
In the **Add Admin Role** window, provide information for the following fields:
[See image.](#RM_Full)
- [Role Info](#roleinfo)
- [Permissions](#permissions)
![Role Management in Zscaler Client Connector](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-role-management-page.png)
[]
[]**Name**: Enter a name for the role. The name you enter cannot contain special characters, except periods (.), hyphens (-), and underscores ( _ ).
[]Permissions allow you to control an admin’s access to Zscaler Client Connector Portal administration settings. You can choose one of the following permissions: **Full**, **View Only**, **None**, or **Customize**.
For some settings, only **View Only** or **None **is available.
Expand each section to display the settings under that section and choose the permission for the role you’re creating. When you choose **Full**, **View Only**, or **None**, that permission applies to the setting's entire section. When you choose **Customize**, you can select a mix of permissions for each setting.
[See image.](#ARE)
- [Dashboard](#dashboard)
- [Enrolled Devices](#enrolled)
- [App Profiles](#app_profiles)
- [Administration](#Admin)
- [Sensitive Data](#sensitive-data)
[]On the [Dashboard](/zscaler-client-connector/about-zscaler-client-connector-portal-dashboard), admins can view data for all or specific users, all or specific device states, and all or specific operating systems. **View Only** is the default permission for the Dashboard and cannot be changed.
[]
The Enrolled Devices menu includes the following settings:
- [**Device Overview**](/zscaler-client-connector/about-enrolled-devices): View, sort, filter, and export data for enrolled devices and removed devices.
- [**Machine Tunnel**](/zscaler-client-connector/about-machine-tunnels):** **View a list of machine tunnels, details about each machine tunnel, and remove machine tunnels.
- [**Partner Devices**](/zscaler-client-connector/about-partner-devices): View, sort, filter, and export data for Partner Devices.
Choose one of the following permissions:
- **Full**: Allows access to all settings on the Device Overview page and the Machine Tunnel page. Admins must have full access to remove devices and machine tunnels.
- **View Only**: Allows access to view, filter, sort, export, and search data on the Device Overview page and the Machine Tunnel page.
- **None**: Does not allow access to the Device Overview page and the Machine Tunnel page.
- **Customize**: Allows you to choose a permission level for each setting.
[]Admins can view [app profile](/zscaler-client-connector/about-zscaler-app-profiles) rules for a specific platform, a list of all configured app rules, the policy token for an app profile rule, and the default policy. Admins can also configure, edit, or delete an app profile rule.
For each platform listed, choose one of the following permissions:
- **Full**: Allows access to all settings for all platforms on the App Profiles page. Admins must have full access to configure, edit, and delete app profile rules, except the default policy.
- **View Only**: Allows access to only view data on the App Profiles page.
- **None**: Does not allow access to the App Profiles page.
- **Customize**: Allows you to choose a permission level for each platform.
[]
The Administration menu includes the following settings:
- [Client Connector App Store](/zscaler-client-connector/about-zscaler-client-connector-store)
- [Client Connector Notifications](/zscaler-client-connector/about-zscaler-client-connector-notifications)
- [Audit Logs](/zscaler-client-connector/about-audit-logs)
- [Forwarding Profile](/zscaler-client-connector/about-forwarding-profiles)
- [Trusted Networks](/zscaler-client-connector/about-trusted-networks)
- [Client Connector Support](/zscaler-client-connector/about-zscaler-app-support)
- [Zscaler Service Entitlement](/zscaler-client-connector/about-zscaler-service-entitlement)
- [User Agent](/zscaler-client-connector/customizing-zscaler-app-user-agent)
- [Client Connector IdP](/zscaler-client-connector/about-zscaler-app-idp)
- [Device Posture](/zscaler-client-connector/about-device-posture)
- [Business Continuity](/zscaler-client-connector/about-business-continuity)
- [Application Bypass Info](/zscaler-client-connector/about-application-bypass-info)
- [Dedicated Proxy Port](/zscaler-client-connector/about-dedicated-proxy-ports)
- [Public API](/zscaler-client-connector/about-api-key-management)
- [Platform Settings](/zscaler-client-connector/about-authentication-settings) (formerly Authentication Settings)
- [Device Groups](/zscaler-client-connector/about-device-groups-0)
- [ZPA Partner Logins](/zscaler-client-connector/enabling-zpa-partner-logins)
- [Location-Based Policies](/zscaler-client-connector/about-location-based-policies)
- [Administration Management](/zscaler-client-connector/about-role-management-zscaler-client-connector)
For each setting, select one of the following permissions:
- **Full**: Allows access to all settings in the Administration menu. Admins must have full access to configure settings.
- **View Only**: Allows access to only view settings on the Administration page.
- **None**: Does not allow access to the Administration page.
- **Customize**: Allows you to choose a permission level for each Administration setting.
[]
The Sensitive Data section includes the option to obfuscate passwords and tokens in the Zscaler Client Connector Portal.
**Obfuscate Passwords and Tokens**: When enabled, all passwords, OTP, Policy Tokens, Device Tokens, and Machine Tokens in the Zscaler Client Connector Portal are obfuscated. This feature is applicable to admins who have read-only access.
![Add Admin Role window](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-add-admin-role-window-collapsed.png)
[]
![Add Admin Role permissions](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-add-admin-role-window.png)
[]