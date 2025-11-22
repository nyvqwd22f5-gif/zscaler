# Adding Roles
Source: https://help.zscaler.com/unified/adding-roles
PDF: https://help.zscaler.com/pdf/com/en/1490871.pdf

With Role Management, you can manage access to Admin Portal settings.
Admin roles must be assigned in ZIdentity. To learn more, see [Assigning Admins to Zscaler Service](/zidentity/assigning-entitlements-users#admin-entitlements).
The following three permissions are available when you add a role. You can also create a custom access level based on these permissions:
- **Full**: View and configure settings.
- **View Only**: View settings.
- **None**: Setting is hidden.
To add a role:
- Go to **Administration** > **Admin Management > Role Based Access Control > Client Connector**.
- On the **Role Management** tab, click **Add Role**.
[See Image.](#RM)
- In the **Edit Admin Role** window, provide information for the following fields:
[See Image.](#RM_Full)
- [Role Info](#roleinfo)
- [Permissions](#permissions)
![Role Management in Zscaler Client Connector](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-role-management-page.png)
[]
[]**Name**: Enter a name for the role. The name you enter cannot contain special characters, except periods (.), hyphens (-), and underscores ( _ ).
[]Permissions allow you to control an admin’s access to Admin Portal administration settings. You can choose one of the following permissions: **Full**, **View Only**, **None**, or **Customize**.
For some settings, only **View Only** or **None **is available.
Expand each section to display the settings under that section and choose the permission for the role you’re creating. When you choose **Full**, **View Only**, or **None**, that permission applies to the setting's entire section. When you choose **Customize**, you can select a mix of permissions for each setting.
[See Image.](#ARE)
- [Dashboard](#dashboard)
- [Enrolled Devices](#enrolled)
- [App Profiles](#app_profiles)
- [Administration](#Admin)
- [Sensitive Data](#sensitive-data)
[]On the [Dashboard](/unified/understanding-zscaler-client-connector-dashboard), admins can view data for all or specific users, all or specific device states, and all or specific operating systems. **View Only** is the default permission for the Dashboard and cannot be changed.
[]
The Enrolled Devices menu includes the following settings:
- [**Device Overview**](/unified/about-enrolled-devices): View, sort, filter, and export data for enrolled devices and removed devices.
- [**Machine Tunnel**](/unified/about-machine-tunnels):** **View a list of machine tunnels, details about each machine tunnel, and remove machine tunnels.
- [**Partner Devices**](/unified/about-partner-devices): View, sort, filter, and export data for Partner Devices.
Choose one of the following permissions:
- **Full**: Allows access to all settings on the Device Overview page and the Machine Tunnel page. Admins must have full access to remove devices and machine tunnels.
- **View Only**: Allows access to view, filter, sort, export, and search data on the Device Overview page and the Machine Tunnel page.
- **None**: Does not allow access to the Device Overview page and the Machine Tunnel page.
- **Customize**: Allows you to choose a permission level for each setting.
[]Admins can view [app profile](/unified/about-zscaler-client-connector-app-profiles) rules for a specific platform, a list of all configured app rules, the policy token for an app profile rule, and the default policy. Admins can also configure, edit, or delete an app profile rule.
For each platform listed, choose one of the following permissions:
- **Full**: Allows access to all settings for all platforms on the **App Profiles** page. Admins must have full access to configure, edit, and delete app profile rules, except the default policy.
- **View Only**: Allows access to only view data on the **App Profiles** page.
- **None**: Does not allow access to the **App Profiles** page.
- **Customize**: Allows you to choose a permission level for each platform.
[]
The Administration menu includes the following settings:
- [Client Connector App Store](/unified/about-zscaler-client-connector-app-store)
- [Client Connector Notifications](/unified/about-zscaler-client-connector-notifications)
- [Audit Logs](/unified/about-audit-logs-0)
- [Forwarding Profile](/unified/about-forwarding-profiles)
- [Trusted Networks](/unified/about-trusted-networks)
- [Client Connector Support](/unified/about-zscaler-client-connector-support)
- [Zscaler Service Entitlement](/unified/about-zscaler-service-entitlement)
- [User Agent](/unified/customizing-zscaler-client-connector-user-agent)
- [Client Connector IdP](/unified/using-zscaler-client-connector-identity-provider)
- [Device Posture](/unified/about-device-posture-profiles)
- [Business Continuity](/unified/about-business-continuity)
- [Application Bypass Info](/unified/about-application-bypass)
- [Dedicated Proxy Port](/unified/configuring-dedicated-proxy-ports-0)
- [Public API](/unified/about-api-key-management)
- [Platform Settings](/unified/about-platform-settings) (formerly Authentication Settings)
- [Device Groups](/unified/about-device-groups)
- [ZPA Partner Logins](/unified/enabling-private-applications-partner-logins)
- [Location-Based Policies](/unified/about-location-based-policies)
- [Administration Management](/unified/about-administration-management)
For each setting, select one of the following permissions:
- **Full**: Allows access to all settings in the Administration menu. Admins must have full access to configure settings.
- **View Only**: Allows access to only view settings on the Administration page.
- **None**: Does not allow access to the Administration page.
- **Customize**: Allows you to choose a permission level for each Administration setting.
[]
The Sensitive Data section includes the option to obfuscate passwords and tokens in the Admin Portal.
**Obfuscate Passwords and Tokens**: When enabled, all passwords, OTP, Policy Tokens, Device Tokens, and Machine Tokens in the Admin Portal are obfuscated. This feature is applicable to admins who have read-only access.
![Add Admin Role window](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-add-admin-role-window-collapsed.png)
[]
![Add Admin Role permissions](/downloads/zscaler-client-connector/administration/adding-roles/zclient-connector-add-admin-role-window.png)
[]