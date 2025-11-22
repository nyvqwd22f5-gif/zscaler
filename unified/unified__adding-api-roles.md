# Adding API Roles
Source: https://help.zscaler.com/unified/adding-api-roles
PDF: https://help.zscaler.com/pdf/com/en/1491316.pdf

An API role defines a client application's permission and access to the different API categories in the Internet & SaaS API. An API role is not assigned to an admin. Instead, it is used during the configuration of an external OAuth 2.0 authentication server for API authentication. You can add up to 16 API roles. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
Configuring an API role is one of the tasks you must complete when configuring an external OAuth 2.0 authentication server for API authentication. To learn more, see [Securing Internet & SaaS APIs with OAuth 2.0](/unified/securing-internet-saas-apis-oauth-2-0).
You can edit or delete API roles at any time.
Prerequisites
To configure API roles, the admin must be assigned to a role that has full permission to Administrators Access in the Admin Portal. To learn more, see [Adding Admin Roles](/unified/adding-admin-roles).
Admin rank doesn't apply to API roles.
Adding API Roles
To configure API roles:
- Go to **Administration **> **Admin Management** > **Role Based Access Control** > **Internet & SaaS**.
-
On the **Role Management** page, click **Add API Role**.
The **Add API Role** window appears.
-
In the **Add API Role** window:
- **Name**: Enter a name** **for the API role.
-
**Scope**: Assign appropriate permissions for the API categories that the client application can access. Assigning permissions allows you to control a client application's access to the major API categories of the Internet & SaaS with more granularity. For each API role, you can configure the following permissions to access various API categories:
- **Full**: This permission provides the client application full (i.e., edit) access to the API categories.
- **View Only**: This permission provides the client application view-only access to the API categories.
- **None**: This permission provides the client application with no access to the API categories.
- **Custom**: This permission allows you to assign field-wise permissions (Full, View Only, and None) to the API categories, providing further granular access to them.
You can configure permissions for the following scopes:
- [Policy & Components](#policy-comp)
- [Cloud Configuration & Integration](#cloud-config)
- [Traffic Forwarding](#traffic-forward)
- [Administration Controls](#administration)
[See image.](#add-api-role-window-image)
- Click **Save **and [activate the change](/unified/saving-and-activating-changes-admin-portal).
The API role is created, and an internal API user is automatically created for the role in the format of `oauth-<rolename>$@<orgid>.<cloud_domain>`. For example, `oauth-apirole1$@64444.zscaler.net` is used as the User context in any API operation. It is also displayed in the audit log for any API operation that is authenticated by an external OAuth 2.0 authentication server. However, this internal user is not displayed on the Administrator Management or User Management pages in the Admin Portal.
After the API role is created, define that role as a Scope on the authorization server. You must configure the Scope value in the `<Zscaler Cloud Name>::<Org ID>::<API Role>` format, where:
- Zscaler Cloud Name represents the cloud on which your organization is provisioned.
- Org ID represents your organization ID obtained from the Admin Portal.
- API Role represents an API role configured in the **Add API Role** window in the Admin Portal.
[]The **Policy & Components** scope includes the following categories:
- [Security](#security)
- [Access Control](#access-control)
- [Data Protection](#data-loss-prevention)
- [Decryption](#decryption)
- [URL Categories](#pc-url-cat)
- [Shared Policy Components](#pc-shared-config)
[]The **Cloud Configuration & Integration** scope includes the following categories:
- [Integrations](#cc-integration)
- [Cloud Configuration](#cc-cloud-config)
[]The **Traffic Forwarding** scope includes Traffic Forwarding, Traffic Forwarding Methods, and Traffic Forwarding Components.
You can assign **Full**, **View Only**, or** None** permissions to the client application to access the traffic-forwarding API category within the Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the following categories:
Custom permission is available for Traffic Forwarding Methods and Traffic Forwarding Components. Select **Custom **to assign field-wise permissions to those categories.
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
- Subclouds & DC Exclusion
- Traffic Capture
[See image.](#tf-traffic-forwarding-image)
[]The **Administration** **Controls** scope includes Administration Controls and Backup Controls.
You can assign **Full**, **View Only**,** None**, or **Custom** permissions to the client application to access the Administration Controls and Backup Controls API category within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
- Administration Controls:
- Advanced Settings
- Administrator Management
- Audit Logs
- Remote Assistance Management
- Authentication Settings
- Identity Proxy Settings
- Role Management
- Backup Controls
- Backup
- Restore
[See image.](#ac-administration-controls-image)
[]You can assign **Full**, **View Only**,** None**, or** Custom** permissions to the client application to access the security policies API category within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
- Malware Protection
- Advanced Threat Protection
- Sandbox
- IPS Control
- Mobile Malware Protection
- Secure Browsing
[See image.](#pc-security-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the client application to access the URL categories API category and its subcategories within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
- Zscaler Defined URL Category Management
- Custom URL Category Management
-
Override Existing Categories
You can assign **Full** access to the **Override Existing Categories** field only if you have been assigned **Full** access to the **Custom URL Category Management** field.
[See image.](#pc-url-categories-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the client application to access the shared-policy components API category within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
- IP & FQDN Groups
-
Browser Isolation
Allowing client applications to access Isolation also includes permission to access the Zscaler integrated [Votiro](https://votiro.com/resource-center/?fwp_resource_categories=guides) CDR services. Isolation customers can enable the Votiro functionality on Internet & SaaS isolation profiles to allow the file-sanitization capability. To learn more, see [About Partner Integrations](/unified/about-partner-integrations#Votiro-CDR).
- Device Management
- Time Intervals
[See image.](#pc-shared-policy-components-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the client application to access the access-control API category within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
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
- Bandwidth Classes
[See image.](#pc-access-control-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the client application to access the data-protection API category and its subcategories within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
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
[See image.](#pc-data-protection-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the client application to access the decryption API category within the Zscaler Internet & SaaS API. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the categories. To assign custom permissions, select **Custom **and assign appropriate permissions for the following categories:
- Policy Control:
- SSL/TLS Inspection
- Policy Components:
- Intermediate CA Certificates
- Root Certificates
[See image.](#pc-decryption-image)
[]This section provides the applications that are integrated with Internet & SaaS for your organization. You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the integrated applications. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all applications. To assign custom permissions, select **Custom **and assign appropriate permissions for the following applications:
- Microsoft Cloud App Security
- SD-WAN
- Azure Virtual WAN
- CrowdStrike
- Microsoft Defender for Endpoint
- Workflow Automation
The applications appear only if your organization has access to or subscriptions to those applications.
[See image.](#cc-integrations-image)
[]You can assign **Full**, **View Only**,** None**,** **or** Custom** permissions to the admin to access the cloud-configuration features. If you select **Full**, **View Only**, or** None **permissions, the selected permission applies to all the features. To assign custom permissions, select **Custom **and assign appropriate permissions for the following features:
- Nanolog Streaming Service
- Virtual ZENs
[See image.](#cc-cloud-config-image)
[]![The Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding%20api-roles-add-api-role-window.png)
[]![The Security tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding-api-roles-pc-security-tab.png)
[]![The Access Control tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-addig-api-roles-pc-access-control-tab.png)
[]![The Data Protection tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding-api-roles-pc-data-protection-tab.png)
[]![The Decryption tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding-api-roles-pc-decryption.png)
[]![The URL Categories tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-addig-api-roles-pc-url-categories-tab.png)
[]![The Shared Policy Components tab in the Policy & Components section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-addig-api-roles-pc-shared-policy-components-tab.png)
[]![The Integrations tab in the Cloud Configuration & Integration section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding%20api-roles-cc-integrations-tab.png)
[]![The Cloud Configuration tab in the Cloud Configuration & Integration section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding%20api-roles-cc-cloud-config-tab.png)
[]![The Traffic Forwarding section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding-api-roles-tc-traffic-forwarding-tab.png)
[]![The Administration Controls section in the Add API Role window on the Role Management page](/downloads/zia/authentication-administration/administrator-role-management/role-management/adding-api-roles/zia-adding-api-roles-ac-administration-controls-tab.png)