# About Audit Logs
Source: https://help.zscaler.com/zpa/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1484121.pdf

[]Zscaler records session information for every admin who signs in to the ZPA Admin Portal. The audit log displays an admin's sign-in and sign-out attempts, actions, request ID, etc., including any configuration changes they completed during their session. Audit logs are stored for up to 6 months.
Audit logs provide the following benefits and enable you to:
- View session information for every admin who signs in to the ZPA Admin Portal.
- View changes to the ZPA configuration.
The ZPA Admin Portal no longer has the Health Check setting for [application segments](/zpa/configuring-application-segments#tab1), but healthCheckType can still appear in the Audit logs.
About the Audit Logs Page
On the Audit Logs page (Configuration & Control > Administration Control > Audit Logs), you can do the following:
- Click the **Calendar **icon (![Calendar icon](/downloads/zpa/administration/about-audit-logs/zpa-calendar-icon.png)
) to select a preset date range, or specify a custom start and end date. Admin audit log records are displayed in the table by the specified date range. By default, this is set to **6 Months**.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Audit Logs page to reflect the most current information.
-
Download the admin audit log records as a CSV file. Only admins with the ZPA Administrator role can download audit logs. The CSV file only includes audit log records for the time range and filters specified. Make sure that your filters are properly applied before clicking **Download**. In the **Save As** window that appears, navigate to the proper location and click **Save**.
The time displayed is based on the time you choose for your account setting in the ZPA Admin Portal, but the exported CSV file (`audit.csv`) always lists the timestamp in UTC. Also, the **Post-Configuration Change** **Value **column within the CSV file uses a dollar sign ($) to separate the content within a cell.
[See image.](#CSVTextSeparator)
-
Filter the admin audit log records. To filter the table by this information, select the appropriate option from the drop-down menu (e.g., **Resource Type**) or enter the proper value in the field (e.g., **Resource Name**), and click **Apply**. If one or more values are selected for the **Admin ID** or **Client ID** filters, only the logs related to either **Admin ID** or **Client ID** are shown in the table. For example, if you are filtering by **Client ID**, only client IDs are shown in the table even if **All** is selected for **Admin ID**. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
For Managed Security Service Provider (MSSP) partners accessing the ZPA Admin Portal, if an admin views a child account for your organization, any configuration changes made appear in the Audit Logs page of the child account. However, the logs for the [Authentication resource type](/zpa/about-audit-logs#resourceType) are displayed within the Audit Logs page of the parent account. To learn more, see [About the ZPA Admin Portal](/zpa/getting-started/introduction-zpa-admin-portal#NavigatingZPAAdminPortal).
- View a list of session information for every admin that signs into the ZPA Admin Portal. For each admin audit log record, you can see:
- **Timestamp**: The date and time of the admin's **Action**. The time displayed is based on the time you choose for [your account setting](/zpa/about-zpa-admin-portal#username) in the ZPA Admin Portal.
- **Admin ID**: The admin's sign-in ID (or username).
- **Client ID**: The API key’s client ID that made changes via the API.
- **Action**: The action performed by the admin or via the API.
- [View a list of all potential actions.](#action)
- [Learn more about the pre- and post-configuration changes for each action.](#config)
-
**Resource Type**: The location within the ZPA Admin Portal or via the API where the **Action** was performed.
- [View a list of all potential Resource Types.](#resourceType)
For **Timestamp**, **Admin ID**, **Action**, and **Resource Type**, you can search for a specific text string or click **Clear Selection** to remove any selections within the drop-down menu.
-
**Transaction** **ID**: The unique identifier that binds multiple related API requests to assist in troubleshooting API request issues. Transaction IDs are created by the OneAPI framework. To learn more, see [OneAPI Authentication](/zidentity/integration/oneapi-authentication) in ZIdentity.
The **Transaction ID** column is only visible if ZIdentity is enabled for your organization.
- **Resource Name**: The object name within a **Resource Type** (e.g., a policy name). Click the **Copy** icon to copy the name to your clipboard.
- **Request ID**: The ID associated with the configuration change related to the **Action** performed. Click the **Copy** icon to copy the ID to your clipboard.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Depending on your ZPA Admin Portal subscriptions, you will see the following ZPA administration options:
- [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy)
- [Administrators](/zpa/about-administrators)
- [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment)
- [Client Sessions](/zpa/about-client-sessions)
- [Disaster Recovery](/zpa/understanding-disaster-recovery)
-
[Integrations](/zpa/about-integrations)
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
-
[Microtenants](/zpa/about-microtenants)
The Microtenants page is only visible for Default Microtenant admins.
- [Roles](/zpa/about-roles)
![Viewing the Audit Logs page](/downloads/tech-pubs-drafts/zpa-draft-articles/about-audit-logs-doc-54957/zpa-audit-logs-annotated.png)
- []Create
- Update
- Delete
- Download
- Nonce MaxUsage Increment
- Sign In
- Sign Out
- Sign In Failure
- Client Session Revoked
- []Acceptable Usage Policy
- Administrator
- Admin Configurations
- Administrator to Notification Association
- App Connector
- App Connector Group
- App Connector Group Version Profile
- App Connector Group to App Connector Association
- App Connector Provisioning Key
- App Connector Version
- AppProtection Custom Control
- AppProtection Profile
- AppProtection Profile and Zscaler-Defined Control Mapping
- AppProtection Profile to AppProtection Control Association
- Application Recommendation Reason
- Application Segment
- Application Segment to Server Group Association
- Audit
- Authentication
- Authentication Setting
- Backup
- Blocked Country
- Branch Connector
- Branch Connector Group
- Branch Connector Group to Branch Connector Association
- Browser Access
- Browser Protection Profile
- Business Continuity Setting
- Client-to-Client Connectivity IP Range
- Client-to-Client Connectivity Registration
- Certificate
- Certificate for Client Connector Enrollment
- Client Connector Download Link
- Client Credentials
- Client Session
- Cloud Connector
- Cloud Connector Group
- Cloud Connector Group to Cloud Connector Association
- Cloud Connector Provisioning Key
- Company Logo
- Constellation Association
- Credential to Rule Mapping
- CORS/SameSite
- Credential Pool
- Credential Pool Mapping
- Credential Pool to Rule Mapping
- Credential State
- Customer Custom Kubeflow Pipeline
- Customer Resiliency Setting
- Customer Support URL
- Customer to User Database Mapping
- Customer to Zone Mapping Details
- Customer Version Profile
- DNS Search Domain
- Emergency Access
- Emergency Access User
- Enrollment Certificate
- Executive Insights Device
- Executive Insights User
- Exempted Customers
- Exempted SNIs
- IdP Certificate
- IdP Configuration
- Ignore List
- Inspection Application
- Isolation Banner
- Isolation Certificate
- Isolation Profile
- Kubeflow Pipeline Metadata
- Location
- Log Receiver
- Log Zone (Indicates the log store location for a region. This is only specified during organization account creation and is never modified.)
- Network Connector
- Network Connector Group
- Network Connector Group to Network Connector Association
- Network Connector Provisioning Key
- Network Connector Version
- Network Segment
- Machine
- Machine Group
- Machine Group to Machine Association
- Machine Provisioning Key
- Microtenant
- Microsegmentation Admin Config
- Microsegmentation Agent
- Microsegmentation App Zone
- Microsegmentation Default Policy Rule
- Microsegmentation Managed Recommended Resource Group
- Microsegmentation Managed Resource Group
- Microsegementation Policy Rule
- Microsegmentation Provisioning Key
- Microsegmentation Unmanaged Recommended Resource Group
- Microsegmentation Unmanaged Resource Group
- Notification
- Notifications
- Policy
- Policy Reorder
- Policy to Connector Group Association
- Policy to Server Group Association
- Policy Rule to Private Service Edge Group Mapping
- Portal Link
- Posture Profile
- Preferred SCIM Attribute for Recommended Users
- Private Cloud
- Private Cloud Controller
- Private Cloud Controller Group
- Private Cloud Controller Group to Private Cloud Controller Mapping
- Private Cloud Controller Version
- Private Service Edge
- Private Service Edge Group
- Private Service Edge Group Version Profile
- Private Service Edge Group to Private Service Edge Association
- Private Service Edge Group to Trusted Network Association
- Private Service Edge Provisioning Key
- Private Service Edge Version
- Privileged Approval
- Privileged Approval Association
- Privileged Approval Request
- Privileged Capabilities
- Privileged Console
- Privileged Credential Pool
- Privileged Credential Pool Mapping
- Priivleged Credential Pool to Rule Mapping
- Privileged Credentials
- Privileged Files
- Privileged Portal
- Privileged Portal Capabilities
- Privileged Portal to Privileged Console Association
- Privileged Remote Access
- Privileged Session
- Privileged Session Participant
- Probe Session
- Probe Session Entity
- Recommended Apps
- Role
- SAML Attribute or Session Attribute
- Scheduled Backup Configuration
-
SCIM Attribute or User Attribute
If you are subscribed to ZIdentity for users, the **SAML Attributes **and **SCIM Attributes **resource types are replaced with **Session Attributes** and **User Attributes**. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- Segment Group
- Segment Group to Application Segment Association
- Segmentation Insights
- Server
- Server Group
- Server Group to App Connector Group Association
- Server Group to Server Association
- Server Validated Certificate Posture
- Supporting Files Upgrade Status
- Terminate All Sessions on Timeout
- ThreatLabZ Control Bulk Deploy Job
- Trusted Network
- User Portal
- User Portal to Portal Link Association
- User Risk Scores
- VPN Service Edge
- VersionProfile Visibility
- Workload Tag Group
- ZPA QBR Reports Download
- ZPA to Isolation Association
- ZpnLocation
- ZpnNanoLogAssociation
[]Within the **Action **column, click on the icon to view the differences between the pre-configuration and post-configuration changes related to an action. You can also click **Download** to save a JSON file (audit-config.json) that includes the pre- and post-configuration change values.
For policy configuration changes, if any criteria (e.g., SAML Attribute, Application Segments, Segment Groups, etc.) is set to "Any," ZPA records the action but the configuration change details do not explicitly display "Any" for the changed criteria. For example, the following policy had its "SAML Attribute" setting set to "Any SAML Attribute" when it was created, then it was updated to include a segment group. However, the configuration details for "SAML Attribute" is not shown in either case. [Show policy example.](#AuditLogs_AllExample)
- View **Create**, **Update**, and **Delete **changes by clicking the![zpa-auditlogs-updateicon.png](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-updateicon.png)
icon.
ZPA logs the **Action** as well as any **Resource Type** associations made during that action. For example, when an admin creates a server and a server group within the ZPA Admin Portal, that server must be associated with a server group, and that server group must be associated with an App Connector group. So, both **Server Group to Server Association** and **Server Group to App Connector Group Association** are displayed under **Resource Type**.
![Audit Logs page with association Resource Types displayed within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/admin-settings/about-audit-logs/zpa-create-delete-server-server-group-app-connector-association.png)
You can then view the pre- and post-configuration change details for each.
[Show Create Server example.](#CreateServerExample)
- View **Sign In** and **Sign Out** attempt details by clicking the![zpa-auditlogs-signinicon.png](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-signinicon.png)
icon.
[Show Sign In example.](#signin)
[]
Pre- and post-configuration changes for a newly created policy with "SAML Attribute" set to "Any":
![Audit Logs page with Configuration Change window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-blanksamlatt-createpolicyexample1.png)
Pre- and post-configuration changes for the updated policy with "SAML Attribute" still set to "Any":
![Configuration Changes window for an updated policy with SAML Attribute set to All](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-blanksamlatt-updatepolicyexample1.png)
[]![Audit Logs page with Configuration Changes window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-createserverexample.png)
[]![Audit Logs page with Configuration Changes window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-signinactionexample.png)
[]![Post-Configuration Change Value with Dollar Sign Shown as Text Separator](/downloads/zpa/documentation-knowledgebase/company-and-administrators/audit-logs/about-audit-logs/zpa-auditlogs-csvdollarseparator.png)