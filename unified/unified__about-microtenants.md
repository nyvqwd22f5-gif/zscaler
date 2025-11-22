# About Microtenants
Source: https://help.zscaler.com/unified/about-microtenants
PDF: https://help.zscaler.com/pdf/com/en/1491596.pdf

Contact Zscaler Support to enable this feature for your organization.
A Microtenant is a delegated administrator responsibility that is assigned to an admin by an admin with Microtenant administrator privileges. Microtenants are defined by an authentication domain and assigned to admins based on country, department, and company for role-based administration control.
Microtenants provide the following benefits and enable you to:
- Delegate the responsibilities of an admin.
- Manage the configuration of shared application segments, segment groups, servers, server groups, App Connectors, App Connector Groups, and policies exclusive to users within their country, department, and operating company.
- View the dashboard and logs exclusive to the users within their country, department, and operating company.
- Share application segments between different Microtenants.
A Microtenant is created within a tenant and is used when departments or subsidiaries within an organization want to manage their configurations independently. For example, an organization can delegate admin responsibilities to the admins of their subsidiaries, allowing them to independently manage their configurations. In the following diagram, the admin of an organization (Neoglobal Corp) has created two Microtenants for Subsidiary-1 and Subsidiary-2. End users of each subsidiary (i.e., Microtenants) can access resources (e.g., applications) from the default or global tenant, as well as those created within their respective subsidiaries. By default, end users of different subsidiaries cannot access resources configured in other Microtenants.
![Diagram showing how the Microtenants feature works](/downloads/zpa/administration/delegated-tenant-administration/about-microtenants/dia_zpa_mgmt-microtenants%20(current).png)
Zscaler recommends you consider the following before configuring a Microtenant:
- [App Profile Configuration in the Admin Portal](#appProfile)
[]Admins that want to map machine tunnels to their respective Microtenant must have a one-to-one mapping between an [app profile](/unified/about-zscaler-client-connector-app-profiles) and the individual Microtenant. For example, a tenant has the following app profiles in the Admin Portal:
| Rule Number | Policy Name | User Groups | Machine Token |
| ----------- | ----------- | ----------- | ------------- |
| 1 | Early_Adopters | Beta_Grp | None |
| 2 | China_Users | PRC_Grp | None |
| 3 | Default | All | Machine_Token_from_Default_Tenant |
The following Microtenants are configured:
| Microtenant Number | Name | Authentication Domain |
| ------------------ | ---- | --------------------- |
| 1 | Microtenant_for_US_Users | us.com |
| 2 | Microtenant_for_China_Users | prc.com |
| 3 | Default | All |
In this example, all machine tunnels enroll against the Default Microtenant. This allows all users to access the Default Microtenant resources over the machine tunnel.
- [Configurations That Can Only Be Managed or Configured by the Default Microtenant Admin](#DefaultMicrotenantConfiguration)
- [][IdP Configuration](/unified/about-idp-configuration)
- [Enrollment (CA) Certificates](/unified/about-enrollment-ca-certificates)
- [Log Streaming Service](/unified/about-log-streaming-service)
- Microtenants
- [SAML Attributes](/unified/about-saml-attributes)
Contact the Default Microtenant admin if you need help configuring or managing certain features and use cases.
- [Disaster Recovery Configuration](#drConfiguration)
[]The Microtenants feature is not supported when [disaster recovery is enabled](/unified/configuring-disaster-recovery). When Disaster Recovery Mode is activated, all users have access to all applications that are designated for disaster recovery. In the following diagram, user A and B are from USA and India and have access to separate applications when disaster recovery is disabled. After disaster recovery is enabled, both users have access to all applications that are designated for disaster recovery.
![Diagram showing the disaster recovery limitation](/downloads/tech-pubs-drafts/zpa-draft-articles/about-microtenants/zpa-disaster-recovery-microtenants-diagram3.png?1678210950)
When in Disaster Recovery Mode, Private Service Edges for Private Applications and App Connectors mapped within a default or custom Microtenant provide traffic to only applications designated for disaster recovery. To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery#drlimits).
- [Supported Features within a Microtenant](#SupportedFeatures)
-
[][Administration](/zpa/administration)
[Disaster Recovery settings](/unified/about-disaster-recovery-settings) configurations are read-only for custom Microtenant admins.
- [API Key Management](/unified/administration/private-applications/api-configuration)
-
[Application Management](/unified/policies/private-applications/access-control/application-segments)
[Browser Access](/unified/about-browser-access) with CORS and [Client Hostname Validation](/unified/validating-client-hostname) features are only supported for regular tenants. In addition, Source IP Anchor-enabled applications are only supported for regular tenants. To learn more, see [Configuring Application Segments](/unified/configuring-defined-application-segments#define-generalinfo).
- [App Connector Management](/unified/infrastructure/private-applications/infrastructure-components/app-connector-management)
-
Authentication
[IdP configuration](/unified/administration/private-applications/identity/idp-device-configuration/idp-configuration), [SAML attributes](/unified/administration/private-applications/identity/idp-device-configuration/saml-attributes), and [authentication settings](/unified/administration/private-applications/identity/idp-device-configuration/settings) configurations are read-only for custom Microtenant admins.
-
[Certificate Management](/unified/policies/private-applications/access-control/clientless/certificate-management)
[Enrollment (CA) certificates](/unified/infrastructure/private-applications/infrastructure-components/enrollment-certificates) are read-only for custom Microtenant admins.
- [Dashboard & Diagnostics](/unified/analytics/private-applications)
-
[Log Streaming Service (LSS)](/unified/logs/private-applications/log-streaming)
[Log receiver configurations](/unified/configuring-log-receiver) are read-only for custom Microtenant admins.
- [Notification Management](/unified/about-notifications)
-
[Policies](/unified/policies/private-applications/access-control)
[AppProtection policies](/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-policy) are only supported for regular tenants.
- [Private Service Edge Management](/unified/infrastructure/private-applications/infrastructure-components/private-service-edge-management)
-
[User Portal](/unified/policies/private-applications/access-control/clientless/user-portal)
[Zscaler Client Connector download links](/unified/viewing-and-managing-zscaler-client-connector-download-links) configurations are read-only for custom Microtenant admins.
There can be situations where users from one Microtenant need to access one or more application segments from another Microtenant. Applications that are present in a Microtenant can be shared with other Microtenants. If an application is not shared with any other Microtenant, it can be moved to the Default Microtenant. To learn more, see [Sharing Defined Application Segments](/unified/sharing-defined-application-segments) and [Moving Defined Application Segments](/unified/moving-resources-microtenant).
About the Microtenants Page
On the Microtenants page (Administration > Role Based Access Control > Microtenants), you can do the following:
- Expand all the rows in the table to see more information about each Microtenant.
- [Add a new Microtenant](/unified/configuring-microtenants).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all Microtenants. For each Microtenant, you can see:
- **Name**: The name of the Microtenant.
- **Description**: The description of the Microtenant.
- **Authentication Domain**: The authentication domain used to authenticate the admins to the Microtenant.
- **Status**: The status of the Microtenant.
-
**Privileged Approvals**: The privileged approval for the Microtenant. Enable to allow approval-based access even if no **Authentication Domain** is selected. The Emergency Access and Emergency Access Users pages are not visible for Microtenants with **Privileged Approvals** disabled. This field is **Disabled** by default.
The **Privileged Approvals** option is only supported for applications that have **Privileged Remote Access** enabled. To learn more, see [Configuring Defined Application Segments](/unified/configuring-defined-application-segments).
- [Edit the configuration of a Microtenant](/unified/editing-microtenants).
Users mapped to Microtenants that are using Private Service Edges reauthenticate when the Microtenant is disabled.
- Delete a Microtenant.
![Viewing the Microtenants page](/downloads/unified/administration/private-applications/admin-user-role-management/delegated-tenant-administration/about-private-app-microtenants/about-microtenants.png)