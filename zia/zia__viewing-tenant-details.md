# Viewing Tenant Details
Source: https://help.zscaler.com/zia/viewing-tenant-details
PDF: https://help.zscaler.com/pdf/com/en/1402016.pdf

The Tenant Details page shows the account and configuration details of a tenant. This information is view-only and cannot be modified within the Zscaler Management Portal for Partners. If you want to make changes to your configurations, contact Zscaler Support.
To view each tenant's account and configuration details:
- Go to **Tenants**.
-
From the **Tenant Name** column, click the tenant name for which you want to open the **Tenant Details** page.
[See image.](#tenant-details-image)
-
On the **Tenant Details** page, you can view the following information about your tenant's account:
- [General Account Information](#Generalinfo)
- [List of Subscriptions](#Subscription)
- [Technical Information](#techinfo)
- [Special Settings](#specialsettings)
- [Activation Details](#activation)
- [Contact Information](#contact)
- [Executive Insights](#executive-insights)
[]
![Tenant details page](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/view-tenant-details.png)
- []The name of the tenant account.
- **Organization ID:** The tenant organization ID.
- The status of the tenant account.
- **View On**: Hover over to access the ZIA Admin Portal of the tenant account. You can also access other admin portals (i.e., Zscaler Digital Experience (ZDX), Zscaler Cloud Connector, etc.) if the tenant is provisioned on them.
- **Primary Account Owner**: The owner of the tenant account.
- **Geographical Region**: The geographical region of the tenant.
- **Number of Employees**: The number of employees in the tenant organization.
- **Industry Vertical**: The industry vertical of the tenant organization.
- **HQ Location**: The HQ location of the tenant organization.
- **Account Type**: The type of tenant account.
- **Clouds**: The clouds on which the tenant is provisioned.
- **Account Creation Date**: The tenant account creation date.
- **Last Modified**: The date on which the tenant account was last modified.
- **Tenant Since**: The date since the organization has been Zscaler's tenant.
- **Domains**: The domains of the tenant organization.
- **Internal Domain**: The internal domain. This domain is generated when the tenant account is created with Zscaler.
- **Policy Template**: The policy template applied to the tenant.
- **CMC Hostname**: The CMC Hostname associated with the tenant.
- **Show Partner Logo**: This is a white labeling feature that indicates if the partner logo is enabled or disabled in the admin portals the tenant has access to.
[See image.](#tenant-details-gen-info-img)
[]
![Tenant's general information](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-general-info.png)
- []**Subscription Name**: The subscription package for the tenant. You can expand the subscription name to view the list of services offered in the subscription and any additional services, if configured.
- **Bundle/Edition Name**: The name of the bundle or edition.
- **Service Name**: The name of the service in the package. The **ADD-ON** tag beside the service name indicates the additional service included in the package.
- **SKU**: The ID of the service.
- **Status**: Whether the subscription package is on trial, expired, not subscribed, subscribed, or temporarily extended.
- **Start Date**: The start date of the subscription.
- **End Date**: The end date of the subscription.
- **Number of Licenses**: The number of licenses the tenant owns.
[See image.](#tenant-details-subs-img)
[]
![Tenant's subscriptions](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-subscriptions.png)
- []**Dedicated Proxy Ports**: The Proxy Ports that are dedicated solely to the tenant.
- **Preferred Nanolog Cluster**: The cluster where the tenant logs are recorded.
- **Sandbox Cluster**: The cluster where files are quarantined and scanned for malicious activities.
- **SMTP Cluster**: The SMTP cluster configured for the tenant.
- **SMCDSS DLP Cluster**: The cluster where the ADP client uploads or downloads the Data Loss Prevention (DLP) Schema files for Exact Data Match (EDM).
- **SMAA Servers**: The configured SMAA servers for the tenant account.
- **Source IP-based Load Distribution**: If enabled, indicates that the load distribution is based on source IP rather than source and destination.
- **For allowed Social Media transactions, apply URL Policy**: Indicates whether the URL policy is applied for the allowed social media transactions.
- **Block outbound suspected spam messages**: Indicates whether blocking outbound suspected spam messages is enabled or disabled.
- **Apply location mapping to Global Auth Bypass Traffic**: If enabled, indicates that the Zscaler service marks traffic destined to Global Auth Bypass destinations as the Location.
- **Disable Default Sandbox Rule**: If enabled, indicates that the default Sandbox rules are disabled.
- **Enable Internal IP Features (Sublocations and Surrogate IP)**: If enabled, allows for additional internal IP features in the admin portals.
- **Sandbox Unique Files Analyzed Daily Limit**: The daily file limit for sandbox analysis.
- **Sandbox API File Submission Daily Limit**: The daily API file limit for sandbox analysis.
- **Self-service GRE and IP Provisioning**: If enabled, allows the tenant to provision GRE or IP addresses in the ZIA Admin Portal.
- **Self-provisioned IP Limit**: Indicates the self-provisioning IP limit in the ZIA Admin Portal. The limit is 100, 1,000, 10K, or 100K.
- **Custom URL Category Limit**: Indicates the number of URL categories that can be configured in the ZIA Admin Portal. It can be either 56 or 256.
- **Mobile Admin Service**: Indicates the mobile admin URL for a specific cloud, if configured.
- **DC Exclusion**: If enabled, restricts customer data forwarding to all data centers (DCs) within the country.
- **DC Exclusion for Traffic Forwarding**: When enabled, it shows the Traffic Forwarding Method option for DC Exclusion in the ZIA Admin Portal (Administration > Resources > DC Exclusion > Traffic Forwarding Method).
- **ZPA Tenant**: Indicates if the Zscaler Private Access (ZPA) tenant ID is mapped to the ZIA tenant ID.
- **Custom File Type Limit**: Indicates the number of custom file types that can be created for file type policies in the ZIA Admin Portal. It can either be 512, 1,024, or 2,048. The default value is blank.
- **IPSec Certificate Common Name (CN)**: Click **View **to see all the IPSec certificate CNs and their descriptions.
- **Static IP Addresses**: Click **View **to see the static IP addresses of the tenant.
If GRE is enabled and configured for the tenant, you can see the following information:
- Customer IP Address
- Tunnel Name
- Tunnel IP
- Primary Gateway IP
- Secondary Gateway IP
- Managed By
[See image.](#tenant-details-tech-info-img)
[]
![Tenant's technical information](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-tech-info-updated.png)
- []**Bypass Authentication for special user agent**: Indicates bypass of authentication for special users who have configured policies for unauthenticated traffic from the ZIA Admin Portal.
- **Bypass Safe Browser Control**: Indicates bypass of Browser Control policies for the tenant.
- **Nanolog cluster to forward logs from Virtual Service Edge**: This field shows where the tenant's Virtual Service Edge (Virtual ZEN (VZEN)) logs are directed and saved.
- **NSS Subscriptions Multiplier**: This field shows the number of NSS for a tenant. For example, if set to 8, the customer can configure 8 different NSS of each type.
- **Limited RBA**: Indicates whether the number Role-Based Access is limited.
- **EDM Primary Key Max Duplicates across Schemas**: When enabled, indicates the number of supported duplicate primary keys for a schema file. The maximum can be 512.
- **Schedule QBR**: Indicates whether the Quarterly Business Report (QBR) is generated every quarter.
- **API Key Status**: Indicates access to use the public ZIA APIs.
- **API Key**: This field shows the API key used for accessing the public ZIA APIs, if generated.
- **Kerberos password for Virtual Service Edge node(s)**: Indicates whether the password for allowing Kerberos on Virtual Service Edge nodes is enabled or disabled.
- **Extended Bucket Limit in SaaS Security**: Indicates whether an extended bucket limit in SaaS Security scan configuration is enabled or disabled.
- **Large PAC Files (up to 2MB)**: Indicates whether 2MB PAC files are supported or not. The normal limit is up to 256 KB.
- **PAC Files up to 1K**: When enabled, the maximum limit of PAC files per organization is increased to 1,000 (i.e., 1,024 PAC files). When disabled, the maximum number of PAC files allowed per organization is 256.
- **Sandbox API Key Status**: Indicates the access for using the Sandbox APIs.
- **Sandbox API Key**:** **This field shows the API key used for accessing the Sandbox APIs, if generated.
- **EC API Key Status**: Indicates access to use the public EC API keys.
- **EC API Key**: This field shows the EC API key used for accessing the public EC APIs, if generated.
- **High Group Limit**: Indicates whether the user can belong to more than 100 groups. If enabled, the limit is up to 128.
- **Scheduled Backup**: Indicates whether the user can automate configuration backups from the ZIA Admin Portal.
- **DLP Engine Expansion**: Indicates whether the DLP Engine Expansion is enabled or disabled.
- **DLP Dictionary Expansion**: Indicates whether the DLP Dictionary Expansion is enabled or disabled.
- **Evaluate all DLP Rules**: When enabled, it shows the **Evaluate All Rules** option in the ZIA Admin Portal (Administration > DLP Advanced Settings > Rule Evaluation).
- **Custom EUN for DLP and Cloud App**: When enabled, it shows the End User Notification and Notification Template in the ZIA Admin Portal (Policy > Data Loss Prevention > Add DLP Rule > End User Notification > Notification Template), which allows the customer to link the Zscaler Client Connector notification template to the DLP rules.
- **Enable Digest Authentication**: Indicates whether using a hash instead of a username or password for authenticating is enabled or disabled.
- **Onboarding Public IaaS Apps (AWS, Azure & GCP)**: Indicates if the onboarding of public IaaS applications in the ZIA Admin Portal is enabled or disabled.
- **Anomaly Report**: Indicates whether the tenant can generate the anomaly report.
- **Custom IP Range**: Indicates if the support for IP ranges in custom URL categories is enabled or disabled.
- **Cloud App Instances**: Indicates the number of cloud application instances a customer can create. A customer can create up to 512 cloud application instances.
- **Keyword Type Identifier in Cloud App Instance Profile**: Indicates if the support for keyword type identifiers in the cloud application instance profile is enabled or disabled. A maximum of 1,024 keyword type identifiers per cloud application instance is allowed. The length of the identifier should not exceed 128 characters.
- **IPv6**: If enabled, this allows seamless connectivity, efficient communication, and large address space to accommodate the increasing number of devices.
- **Microsoft Information Protection (MIP) Labels**: When enabled, it retrieves Microsoft Information Protection (MIP) Labels from the MIP account.
- **Custom Cloud App Support**: When enabled, it allows customers to configure their own applications in the ZIA Admin Portal. This cannot be disabled if any custom cloud applications have been added to a tenant.
- **Custom Filehash**: When enabled, it allows customers to configure their own custom file blocklists based on MD5 hashes in the ZIA Admin Portal. Customers can block up to a maximum of 10K MD5 hashes.
- **Zoom Tenancy Support: **When enabled, it shows the Zoom app option under **Tenant profile** in the ZIA Admin Portal.
- **Adaptive access for User and Entity Behavior Analytics (UEBA)**: When enabled, this triggers Multi-Factor Authentication in the ZIA Admin Portal (Alerts > Alert Rules > Add Alert Rules).
- **Real-Time Risk Score Updates: **When enabled, this shows the **Enable Real-Time Risk Score Updates** option in the ZIA Admin Portal (Administration > Advanced Settings).
- **Remove HTTP Range Header: **When enabled, it provides support for custom categories for the Remove Range Headers feature under Administration > Cloud Configuration > Advanced Settings in the ZIA Admin Portal.
- **SaaS Security Collaborator Count**: When enabled, this knob specifies the number of users who can access certain files in a SaaS application.
- **ZSLogin Admin: **When enabled, it allows admin access to the ZSLogin Admin Portal. By default, this option is disabled. ZSLogin is a unified identity service for Zscaler that centralizes and simplifies identity management, user authentication, and entitlement assignment for users to Zscaler services, such as Zscaler Internet Access (ZIA), Zscaler Private Access (ZPA), etc. To learn more, see [Zscaler ZSLogin Help](/zslogin).
- **ZSLogin User: **When enabled, it allows users to access the ZSLogin Admin Portal. By default, this option is disabled.
- **Allow Admin ZSLogin:** When enabled, it allows admin access to the ZSLogin Admin Portal. By default, this option is disabled. ZSLogin is a unified identity service for Zscaler that centralizes and simplifies identity management, user authentication, and entitlement assignment for users to Zscaler services, such as ZIA, Zscaler Private Access (ZPA), etc. To learn more, see [Zscaler ZSLogin Help](/zslogin).
- **Allow User ZSLogin**: When enabled, it allows users to access to the ZSLogin Admin Portal. By default, this option is disabled.
- **AND Functionality for URL Filtering Categories**: When enabled, it provides the support for the logical operation AND between the URL categories in a URL filtering rule in the ZIA Admin Portal. By default, this option is disabled. To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
- **Schedule QBR**: This option generates the Quarterly Business Report (QBR) every quarter, if configured.
- **Attack Surface Report**: Indicates whether the tenant can generate the attack surface report.
- **ZIA Access Restrictions Feature**: Indicates whether the ZIA access restrictions feature is enabled or disabled for the tenant.
- **JWT Auth for Workload**: When enabled, it provides support for JWT authentication for workload locations under Administration > Location Management in the ZIA Admin Portal. By default, this option is disabled.
[See image.](#tenant-details-special-info-img)
[]
![Tenant's Special Settings information](/downloads/zia/zscaler-management-portal-partners/tenant-management/viewing-tenant-details/tenant-details-special-settings-updated.png)
[]The tenant account activation and password reset information:
- **Send Activation Email**: Indicates whether sending the activation email is enabled or disabled.
- **Send ZIA Password Reset Email**: Indicates whether sending the ZIA password reset email is enabled or disabled.
- **Send ZDX Password Reset Email**: Indicates whether sending the Zscaler Digital Experience (ZDX) password reset email is enabled or disabled.
- **Send Zscaler Cloud Connector Password Reset Email**: Indicates whether sending the Zscaler Cloud Connector password reset email is enabled or disabled.
- **Send ZCSPM Admin Password Reset Email**: Indicates whether sending the Zscaler Cloud Security Posture Management (ZCSPM) password reset email is enabled or disabled.
- **Send BI Password Reset Email**: Indicates whether sending the password reset link email notification to the Zscaler Business Intelligence (BI) contact is enabled or disabled.
- **Send Risk Analytics Password Reset Emai**l: Indicates whether sending the password reset link email notification to the Zscaler Risk Analytics contact is enabled or disabled.
- **Activation Email Recipient**: The email ID of the recipient to receive the activation or password reset email for enabled preceding fields.
- **Send notification to the following emails**: The email ID of the recipient to receive a notification from Zscaler about their account creation.
[See image.](#tenant-details-act-info-img)
[]
![Tenant's email activation details](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-activation.png)
[]The primary and secondary contact details for Billing, Technical, or Business divisions, and if provisioned, you can view the contact information for ZDX, Zscaler Cloud Connector, Zscaler Deception, Zscaler Risk Analytics, Zscaler Business Intelligence (BI), and Zscaler Cloud Security Posture Management (ZCSPM).
For each contact, you can see:
- **Name**: The name of the contact person.
- **Title**: The job title of the contact person.
- **Email**: The email address of the contact person.
- **Phone**: The phone number contact person.
- **Alternate Phone**: The alternate phone number of the contact person, if any.
[See image.](#tenant-details-alt-info-img)
[]
![Tenant's contact details](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-contacts.png)
[]The Executive Insights must be enabled for the tenant account in order to receive the Insights reports. In the **Recipient Lists for Executive Insights** section, you can see:
- **Executive Insights Report (Display & Sending)**: Indicates whether displaying and sending the Executive Insights Report to the tenant is enabled or disabled.
- **Send at report generation**: The email addresses that receive the Executive Insights Report when it's generated.
- **Send after 7 days**: The email addresses that receive the Executive Insights Report 7 days from the date of the report generation.
- **Allowed external email domains**: Displays the external email domains allowed to receive the Executive Insights Report.
[See image.](#tenant-details-exec-info-img)
[]
![Tenant's Executive Insights recipients](/downloads/zia/zscaler-management-portal-partners/end-user-management/viewing-tenant-details/tenant-details-recipient.png)