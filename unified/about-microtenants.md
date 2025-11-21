# About Microtenants
Source: https://help.zscaler.com/zpa/about-microtenants
PDF: https://help.zscaler.com/pdf/com/en/1485681.pdf

Contact Zscaler Support to enable this feature for your organization.
A Microtenant is a delegated administrator responsibility that is assigned to an admin by an admin with Microtenant administrator privileges. Microtenants are defined by an authentication domain and assigned to admins based on country, department, and company for role-based administration control.
Microtenants provide the following benefits and enable you to:
- Delegate the responsibilities of an admin.
- Manage the configuration of shared application segments, segment groups, servers, server groups, App Connectors, App Connector groups, and policies exclusive to users within their country, department, and operating company.
- View the dashboard and logs exclusive to the users within their country, department, and operating company.
- Share application segments between different Microtenants.
A Microtenant is created within a tenant and is used when departments or subsidiaries within an organization want to manage their configurations independently. For example, an organization can delegate admin responsibilities to the admins of their subsidiaries, allowing them to independently manage their configurations. In the following diagram, the admin of an organization (Neoglobal Corp) has created two Microtenants for Subsidiary-1 and Subsidiary-2. End users of each subsidiary (i.e., Microtenants) can access resources (e.g., applications) from the default or global tenant, as well as those created within their respective subsidiaries. By default, end users of different subsidiaries cannot access resources configured in other Microtenants.
![Diagram showing how the Microtenants feature works](/downloads/zpa/administration/delegated-tenant-administration/about-microtenants/dia_zpa_mgmt-microtenants%20(current).png)
Zscaler recommends you consider the following before configuring a Microtenant:
- [App Profile Configuration in the Zscaler Client Connector Portal](#appProfile)
[]Admins that want to map machine tunnels to their respective Microtenant must have a one-to-one mapping between an [app profile](/z-app/about-zscaler-app-profiles) and the individual Microtenant. For example, a tenant has the following app profiles in the Zscaler Client Connector Portal:
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
- [][IdP Configuration](/zpa/about-idp-configuration)
- [Enrollment (CA) Certificates](/zpa/about-enrollment-ca-certificates)
- [Log Streaming Service](/zpa/about-log-streaming-service)
- Microtenants
- [SAML Attributes](/zpa/about-saml-attributes)
- [Zscaler Client Connector Portal Links](/z-app/about-zscaler-app-portal#zpa-admin-portal)
Contact the Default Microtenant admin if you need help configuring or managing certain features and use cases.
- [Disaster Recovery Configuration](#drConfiguration)
[]The Microtenants feature is not supported when [disaster recovery is enabled](/zpa/configuring-disaster-recovery). When Disaster Recovery Mode is activated, all users have access to all applications that are designated for disaster recovery. In the following diagram, user A and B are from USA and India and have access to separate applications when disaster recovery is disabled. After disaster recovery is enabled, both users have access to all applications that are designated for disaster recovery.
![Diagram showing the disaster recovery limitation](/downloads/tech-pubs-drafts/zpa-draft-articles/about-microtenants/zpa-disaster-recovery-microtenants-diagram3.png?1678210950)
When in Disaster Recovery Mode, ZPA Private Service Edges and App Connectors mapped within a default or custom Microtenant provide traffic to only applications designated for disaster recovery. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery#drlimits).
- [Supported Features within a Microtenant](#SupportedFeatures)
-
[][Administration](/zpa/administration)
[Disaster Recovery settings](/zpa/about-disaster-recovery-settings) configurations are read-only for custom Microtenant admins.
- [API Key Management](/zpa/api-key-management)
-
[Application Management](/zpa/application-management)
[Browser Access](/zpa/about-browser-access) with CORS and [Client Hostname Validation](/zpa/validating-client-hostname) features are only supported for regular tenants. In addition, Inspect Traffic with ZIA- or Source IP Anchor-enabled applications are only supported for regular tenants. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments#define-generalinfo).
- [App Connector Management](/zpa/app-connector-management)
-
[Authentication](/zpa/authentication)
[IdP configuration](/zpa/about-idp-configuration), [SAML attributes](/zpa/about-saml-attributes), and [authentication settings](/zpa/configuring-authentication-settings) configurations are read-only for custom Microtenant admins.
-
[Certificate Management](/zpa/certificate-management)
[Enrollment (CA) certificates](/zpa/about-enrollment-ca-certificates) are read-only for custom Microtenant admins.
- [Dashboard & Diagnostics](/zpa/dashboard-diagnostics)
-
[Log Streaming Service (LSS)](/zpa/log-streaming-service)
[Log receiver](/zpa/configuring-log-receiver) configurations are read-only for custom Microtenant admins.
- [Notification Management](/zpa/notification-management)
-
[Policies](/zpa/policies)
[AppProtection policies](/zpa/policies/appprotection-private-application-traffic-policy-formerly-inspection/appprotection-policy) are only supported for regular tenants.
- [Privileged Remote Access (PRA)](/zpa/privileged-remote-access-management)
- [Private Service Edge Management](/zpa/private-service-edge-management)
-
[User Portal](/zpa/user-portal)
[Zscaler Client Connector download links](/zpa/viewing-and-managing-zscaler-client-connector-download-links) configurations are read-only for custom Microtenant admins.
There can be situations where users from one Microtenant need to access one or more application segments from another Microtenant. Applications that are present in a Microtenant can be shared with other Microtenants. If an application is not shared with any other Microtenant, it can be moved to the Default Microtenant. To learn more, see [Sharing Defined Application Segments](/zpa/sharing-defined-application-segments) and [Moving Defined Application Segments](/zpa/moving-defined-application-segments).
About the Microtenants Page
On the Microtenants page (Configuration & Control > Administration Control > Microtenants), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Microtenants page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new Microtenant](/zpa/configuring-microtenants).
- Expand all the rows in the table to see more information about each Microtenant.
- View a list of all Microtenants. For each Microtenant, you can see:
- **Name**: The name of the Microtenant.
- **Description**: The description of the Microtenant.
- **Authentication Domain**: The authentication domain used to authenticate the admins to the Microtenant.
- **Status**: The status of the Microtenant.
-
**Privileged Approvals**: The privileged approval for the Microtenant. Enable to allow approval-based access even if no **Authentication Domain** is selected. The Emergency Access and Emergency Access Users pages are not visible for Microtenants with **Privileged Approvals** disabled. This field is **Disabled** by default.
The **Privileged Approvals** option is only supported for applications that have **Privileged Remote Access** enabled. To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
- [Edit the configuration of a Microtenant](/zpa/editing-microtenants).
Users mapped to Microtenants that are using ZPA Private Service Edges reauthenticate when the Microtenant is disabled.
- Delete a Microtenant.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Administrators](/zpa/about-administrators) page to add new admins or manage existing admins.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your [user portals](/zpa/user-portal).
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
- Go to the [Disaster Recovery](/zpa/understanding-disaster-recovery) page to view critical application segments, ZPA Private Service Edge groups, or App Connector groups that are designated for disaster recovery. You can also configure the [Disaster Recovery settings](/zpa/about-disaster-recovery-settings).
When [Disaster Recovery](/zpa/configuring-disaster-recovery) is enabled and Disaster Recovery Mode is activated, all users have access to all applications that are designated for disaster recovery.
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for Microtenant admins.
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
![Viewing the Microtenants page](/downloads/zpa/administration/delegated-tenant-administration/about-microtenants/zpa-microtenants-page_0.png)