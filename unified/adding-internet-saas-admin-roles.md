# Adding Internet & SaaS Admin Roles
Source: https://help.zscaler.com/unified/adding-internet-saas-admin-roles
PDF: https://help.zscaler.com/pdf/com/en/1491291.pdf

Configuring an admin role is one of the tasks that you must complete when [configuring role-based administration](/unified/configuring-role-based-administration). You can edit or delete admin roles at any time. You can add up to 64 admin roles. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
For ZIdentity-enabled tenants (that are linked to ZIdentity), admin roles must be assigned from [ZIdentity](/zidentity/what-zidentity). To learn more, see [About Administrative Entitlements](/zidentity/about-administrative-entitlements).
Prerequisites
To configure admin roles:
- You must have the proper permissions to configure roles.
- You must have access to create, edit, or delete roles with a lower [rank](/unified/about-admin-rank).
- You must be assigned organizational [admin scope](/unified/about-admin-scope).
Admin rank and scope don't apply to SD-WAN partner API clients. To learn more, see [Adding SD-WAN Partner API Clients](/unified/adding-sd-wan-partner-api-clients).
Adding Admin Roles
To add and configure admin roles:
- Go to **Administration** > **Admin Management **> **Role Based Access Control** > **Internet & SaaS**.
-
On the **Role Management **page, click **Add Administrator Role**.
The **Add Administrator Role** window appears.
-
In the **Add Administrator Role** window:
- **Name**: Enter a name** **for the admin role.
- **Enable Permissions for Executive Insights App**: Enable to give the admin assigned this role the permissions and scope required to access the Executive Insights App. This setting is disabled by default. If you enable this setting, the Zscaler service enables the following scopes regardless of your configuration: **Data Loss Prevention**, **Security**, and **Firewall, DNAT, DNS & IPS**. Enabling this setting also enables the **Policy and Resource Management** option for **Access Control (Web and Mobile)**.
-
**Permissions**: Permissions allow you to control an admin's access to the major features of the Admin Portal. For each admin, you must select permissions in the following categories:
- [Admin Rank](#adminrank)
- [Logs Limit (Days)](#logs-limit-days)
- [Dashboard Access](#dashboard-access)
- [Reporting Access](#reporting-access)
- [Insights Access](#insights-access)
- [Alerts Access](#alerts-access)
- [User Names](#user-names)
- [Device Information](#device-info)
[See image.](#permissions-section-image)
-
**Scope**: Assign appropriate permissions for the admins to access major Internet & SaaS features. Assigning permissions allows admins to access certain features with more granularity. For each admin role, you can configure the following permissions to access various features:
- **Full**: This permission provides admins with full (i.e., edit) access to the feature.
- **View Only**: This permission only allows admins to view the feature. Admins cannot edit any data within the feature.
- **None**: This permission does not allow admins to access the feature.
Optionally, you can select **Custom**, which allows you to assign feature-wise permissions (Full, View Only, and None) for the Internet & SaaS modules, providing further granular access to those features.
[See image.](#different-permissions-options-policies)
When a role doesn't have any access (i.e., if **None** is selected) to a feature, that feature does not show up in the Admin Portal for that admin role.
You can configure permissions for the following scopes:
- [Policy & Components](#policy-comp)
- [Cloud Configuration & Integration](#cloud-config)
- [Traffic Forwarding](#traffic-forward)
- [Administration Controls](#administration)
- [Reporting Data](#reporting)
[See image.](#add-administration-role-window-image)
- Click **Save **and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]Select an admin rank** **for the role if this feature is enabled in [Advanced Settings](/unified/configuring-advanced-settings#admin-ranking). Admin rank enables you to create a hierarchy between admins and ensures that policies and settings configured by admins with a higher rank cannot be overridden by admins with a lower rank. To learn more, see [About Admin Rank](/unified/about-admin-rank).
[]Enter the number of days an admin in this role can view logs. Admins can view real-time logs of every transaction performed by your users, regardless of where they are in the world. To learn more, see [About Insights Logs](/unified/about-insights-logs-internet-saas).
By specifying a limit in **Logs Limit (Days)**, you can control the number of days admins are allowed to view logs. By default, admins can view logs for an unrestricted amount of time. If you need temporary access to the logs to verify compliance, admins can only view logs for the specified number of days. For example, if you select a limit of 30** **days, then admins can only view logs for 30 days.
[]In **Dashboards**, admins can view predefined dashboards that enable real-time visibility of your organization's internet traffic. Admins can customize the dashboards if they have **Full** access permission.
Choose one of the following permissions for an admin's dashboard access:
- **Full**:** **Allows admins to view, edit, and delete dashboards
- **View** **Only**: Allows admins to only view all dashboards
[]Admins can access a wide range of standard reports and can also create custom reports**. **By specifying permissions in **Reporting Access**, you can control the admin's access to these features.
Choose one of the following permissions for an admin's reporting access:
- **Full**: Allows admins access to all features in **Interactive Reports** and **Scheduled Reports**. Admins must have full permission here to obtain detailed transaction logs from the **View Logs** field in Insights. In addition, only admins with the super admin role can schedule executive reports and delete any custom reports; otherwise, admins can delete their own custom reports only.
- **View Only**:
- **Interactive Reports**: Allows admins to view standard reports and custom reports created by other admins.
- **Scheduled Reports**: Allows admins full access to features.
- **None**: Doesn't allow admins access to **Reporting** and **Insights**. The **Analytics** menu disappears from the Admin Portal. The **Insights Access** permission option also disappears.
If you select** Enable Permissions for Executive Insights App** with the **Reporting Access** selection as **None**, then the **Reporting Access** selection defaults to **View Only** after saving.
[]Admins can interactively mine logs for data on specific transactions. By specifying permissions in **Insights Access**,** **you can control the access that admins have to this feature.
Choose one of the following permissions for an admin's insights access:
- **View Only**: Allows admins full access to **Insights**. However, the role must be given **Full **permission** **to **Reporting Access** to obtain detailed transaction logs. Admins cannot view these detailed transaction logs if they have **View Only** permission to **Reporting Access**.
- **None**: Doesn't allow admins access to **Insights**. The **Insights** page disappears from the **Analytics **menu.
This category appears only if the role has been given **Full** or **View Only **permissions for **Reporting Access**.
[]In **Alerts**, you can control admins' access to the **Alerts** dashboard, **Alerts Rules**, and **Webhooks**. For the features that are disabled for your role, the **Alerts** page displays a **View Restricted** message. To learn more, see [About Security & UEBA Alerts](/unified/about-security-ueba-alerts-internet-saas).
Choose one of the following permissions for an admin's alerts access:
- **Full**: Admins can both view and edit.
- **View Only**: Admins can only view and cannot edit.
- **None**: Admins have no access to alerts.
[]Choose whether real usernames are visible to admins when they view dashboards, reports, or insights:
- **Visible**: Usernames are visible.
- **Obfuscated**: Usernames are obfuscated.
If an admin is assigned a role with username obfuscation, but requires access to real usernames, an auditor's permission is required. To learn more, see [About Auditors](/unified/about-auditors).
[]Choose whether device information (i.e., device name, device hostname, and device owner) is visible to admins when they view dashboards, reports, or insights:
- **Visible**: Device information is visible.
- **Obfuscated**: Device information is obfuscated.
If an admin is assigned a role with device information obfuscation, but requires access to device information, an auditor's permission is required. To learn more, see [About Auditors](/unified/about-auditors).
[]The **Policy & Components** scope includes the following categories:
- [Security](#security)
- [Access Control](#access-control)
- [Data Protection](#data-loss-prevention)
- [Decryption](#decryption)
- [URL Categories](#pc-url-cat)
- [Shared Policy Components](#pc-shared-config)
[]The **Cloud Configuration** scope includes the following categories:
- [Integrations](#cc-integration)
- [Cloud Configuration](#cc-cloud-config)
[]The **Traffic Forwarding** scope includes Traffic Forwarding, Traffic Forwarding Methods, and Traffic Forwarding Components.
You can assign **Full**, **View Only**,** None**, or **Custom **permissions to the admin to access the traffic-forwarding features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the following features:
Custom permission is available for traffic forwarding methods and traffic forwarding components. Select **Custom **to assign field-wise permissions to those features.
- Traffic Forwarding:
- Forwarding Control
- Traffic Forwarding Methods:
- Static IPs
- GRE Tunnels
- Locations
- VPN Credentials Management
- Hosted PAC Files
- Traffic Forwarding Components:
- Proxies & Gateways
-
Zscaler Client Connector
This field is not available if you are subscribed to ZIdentity. You can manage Zscaler Client Connector access for your admins from the [ZIdentity](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
- Subclouds & DC Exclusion
- Traffic Capture
[See image.](#tf-traffic-forwarding-image)
[]The **Administration Control** scope includes Administration Controls and Backup Controls.
You can assign **Full**, **View Only**,** None**, or **Custom** permissions to the admin to access the Administration Controls and Backup Controls features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Administration Controls:
- Advanced Settings
- Administrator Management
- Audit Logs
- User Management
- Remote Assistance Management
- Alerts
- Authentication Settings
- Identity Proxy Settings
- Role Management
- Backup Controls:
- Backup
- Restore
[See image.](#ac-administration-controls-image)
[]You can assign **View Only**,** None**,** **or** Custom** permissions to the admin to access the reporting features. If you select **View Only** or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the reporting features:
- Security
- Web Data
- DLP
- Firewall
- URL Categories
- IoT Discovery
[See image.](#reports-section-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the security features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Malware Protection
- Advanced Threat Protection
- Sandbox
- IPS Control
- Mobile Malware Protection
- Secure Browsing
[See image.](#pc-security-tab-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the URL category features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
-
Zscaler Defined URL Category Management
This option allows admins to edit predefined URL categories (e.g., Entertainment, Music, etc.), using **Custom URLs**, **URLs Retaining Parent Category**, **Keywords Retaining Parent Category**, and **Review Matches fields**. The **Custom URLs** and **Custom Keywords** fields have view-only access along with all fields in custom categories.
-
Custom URL Category Management
This option allows admins to create and edit custom categories using the **URLs Retaining Parent Category** and **Keywords Retaining Parent Category** fields. The **Custom URLs**, **Custom Keywords**, and all fields in predefined categories have view-only access.
-
Override Existing Categories
You can only assign** **access to the **Override Existing Categories** field if you have assigned **Full** access in the **Custom URL Category Management** field to an admin. This option allows admins full access to create and edit custom categories using the **Custom URLs**, **URLs Retaining Parent Category**, **Keywords Retaining Parent Category**, and **Custom Keywords **fields. Predefined categories have view-only access.
[See image.](#pc-url-categories-tab-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the shared-policy components features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- IP & FQDN Groups
-
Browser Isolation
Providing admins permissions access Isolation also includes access to Zscaler integrated [Votiro](https://votiro.com/resource-center/?fwp_resource_categories=guides) CDR services. Isolation customers can enable the Votiro functionality on Internet & SaaS isolation profiles to allow the file-sanitization capability. To learn more, see [About Partner Integrations](/unified/about-partner-integrations#Votiro-CDR).
- Device Management
- Time Intervals
[See image.](#pc-shared-policy-components-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the access control features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Policy Control:
- URL & Cloud App Control
- Firewall Control
- DNS Control
- NAT Control
- File Type Control
- Mobile App Store Control
- Bandwidth Control
- FTP Control
- Policy Components:
- Tenant Profiles
- Bandwidth Classes
[See image.](#pc-access-control-tab-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the data-protection features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Policy Control:
- Data Loss Prevention
- Endpoint DLP
- Data At Rest Scanning
- SaaS Security Posture Management
- Policy Components:
- DLP Dictionaries & Engines
- Notification Templates
- SaaS Application Tenants
- DLP Incident Receiver
[See image.](#pc-data-protection-tab-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the decryption features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Policy Control:
- SSL/TLS Inspection
- Policy Components:
- Intermediate CA Certificates
- Root Certificates
[See image.](#pc-decryption-tab-image)
[]This section provides the applications that are integrated with Intenet & SaaS for your organization. You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the integrated applications. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all applications. To assign custom permissions, select **Custom **and assign appropriate permissions for the following applications:
- Microsoft Cloud App Security
- SD-WAN
- Azure Virtual WAN
- CrowdStrike
- Microsoft Defender for Endpoint
- Workflow Automation
The applications appear only if your organization has access to or subscriptions to those applications.
[See image.](#cc-integrations-tab-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the cloud-configuration features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Nanolog Streaming Service
- Virtual ZENs
- API Key Management
[See image.](#cc-cloud-configurations-tab-image)
[]![The Add Administrator Role window on the Role Management page ](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-add-administrator-role.png)
[]![The Add Administrator Role window > Permissions section on the Role Management page ](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-add-role-management-permissions-section.png)
[]![The Add Administrator Role window displaying different permissions options (full, view only, none, custom) on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-permissions-options.png)
[]![The Security tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-security-tab.png)
[]![The Access Control tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-access-control.png)
[]![The Data Protection tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-data-protection-tab.png)
[]![The Decryption tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-decryption-tab.png)
[]![The URL Categories tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-url-categories.png)
[]![The Shared Policy Components tab in the Policy & Components section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-pc-shared-policy-configurations.png)
[]![The Integrations tab in the Cloud Configuration & Integration section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-cc-integrations.png)
[]![The Cloud Configuration tab in the Cloud Configuration & Integration section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-cc-cloud-configuration.png)
[]![The Traffic Forwarding section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-tf-traffic-forwarding-tab.png)
[]![The Administration Controls section > Administration Controls and Backup Controls in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-administration-controls-tab.png)
[]![The Reporting Data section in the Add Administrator Role window](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-admin-roles/6.2r%20folder/zia-configuring-admin-roles-reporting-data-tab.png)