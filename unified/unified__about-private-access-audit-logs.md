# About Private Access Audit Logs
Source: https://help.zscaler.com/unified/about-private-access-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1491611.pdf

[]Zscaler records the session information for each admin that signs in to the Admin Portal. The audit log displays information related to sign-in or sign-out attempts (e.g., timestamps, actions, IP addresses, etc.) and any configuration changes that were completed during their session, such as updates or deletes.
The Admin Portal no longer has the Health Check setting for [application segments](/unified/configuring-defined-application-segments), but healthCheckType can still appear in the audit logs.
Audit logs provide the following benefits and enable you to:
- Analyze administration sessions by reviewing in-depth information such as actions, categories, interface, or configuration changes (e.g., application segment modifications, posture profile alterations, etc.)
- Detect and investigate suspicious activity and track unauthorized access to the administrative user interface, demonstrating compliance with security policies.
- Customize filters to search for selected items and export them to a CSV file.
- Review configuration changes for comparison of the before-and-after administration sessions.
If an admin account makes five unsuccessful attempts to log in within one minute, the account is locked out for five minutes and the failed attempts are recorded in the audit log. Audit logs are stored for up to 6 months.
About the Private Access Audit Logs Page
On the Audit Logs page (Administration > Admin Management > Audit Logs > Private Access), you can do the following:
- Click the **Calendar **icon (![Calendar Icon](/downloads/zpa/administration/about-audit-logs/zpa-calendar-icon.png)
) to select a preset date range, or specify a custom start and end date. Admin audit log records are displayed in the table by the specified date range. By default, this is set to **6 Months**.
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filter).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Audit Logs page to reflect the most current information.
- Download the admin audit log records as a CSV file. Only admins with the Administrator role can download audit logs. The CSV file only includes audit log records for the time range and filters specified. Make sure that your filters are properly applied before clicking **Download**. In the **Save As** window that appears, navigate to the proper location and click **Save**.
The time displayed is based on the time you choose for your account setting in the Admin Portal, but the exported CSV file (`audit.csv`) always lists the timestamp in UTC. Also, the **Post-Configuration Change** **Value **column within the CSV file uses a dollar sign ($) to separate the content within a cell.
[See image.](#CSVTextSeparator)
- Filter the admin audit log records. To filter the table by this information, select the appropriate option from the drop-down menu (e.g., **Resource Type**) or enter the proper value in the field (e.g., **Resource Name**), and click **Apply**. If one or more values are selected for the **Admin ID** or **Client ID** filters, only the logs related to either **Admin ID** or **Client ID** are shown in the table. For example, if you are filtering by **Client ID**, only client IDs are shown in the table even if **All** is selected for **Admin ID**. To learn more, see [Using Tables](/unified/using-tables#filter).
For Managed Security Service Provider (MSSP) partners accessing the Admin Portal, if an admin views a child account for your organization, any configuration changes made appear in the Audit Logs page of the child account. However, the logs for the [Authentication resource type](/unified/about-audit-logs) are displayed within the Audit Logs page of the parent account. To learn more, [Signing in to the Admin Portal](/unified/signing-admin-portal).
- View a list of session information for every admin that signs into the Admin Portal. For each admin audit log record, you can see:
- **Timestamp**: The date and time of the admin's **Action**. The time displayed is based on the time you choose for [your account setting](/unified/signing-admin-portal) in the Admin Portal.
- **Admin ID**: The admin's sign-in ID (or username).
- **Client ID**: The API key's client ID that made changes via the API.
- **Action**: The action performed by the admin or via the API.
- [View a list of potential actions.](#action)
- [Learn more about the pre- and post-configuration changes for each action.](#config)
-
**Resource Type**: The location within the Admin Portal or via the API where the **Action** was performed.
- [View a list of all potential Resource Types.](#resourceType)
For **Time Range**, **Admin ID**, **Action**, and **Resource Type**, you can search for a specific text string or click **Clear Selection** to remove any selections within the drop-down menu.
-
**Transaction ID**: The unique identifier that binds multiple related API requests to assist in troubleshooting API request issues. Transaction IDs are created by the OneAPI framework. To learn more, see [OneAPI Authentication](/unified/administration/zidentity/authentication/oneapi-authentication) in ZIdentity.
The **Transaction ID **column is only visible if ZIdentity is enabled for your organization.
- **Resource Name**: The object name within a **Resource Type** (e.g., a policy name). Click the **Copy** icon to copy the name to your clipboard.
- **Request ID**: The ID associated with the configuration change related to the **Action** performed. Click the **Copy** icon to copy the ID to your clipboard.
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
![Viewing the Private Access Audit Logs page ](/downloads/unified/administration/audit-logs/about-private-access-audit-logs/about-private-access-audit-logs.png)
- []Create
- Update
- Delete
- Download
- Sign In
- Sign Out
- Sign In Failure
- Client Session Revoked
- Session Time Out
- Account Locked
- Account Unlocked
- EmergencyAccess User Invited
- EmergencyAccess User Created
- []Acceptable Usage Policy
- Admin Configurations
- Administrator
- Administrator to Notification Association
- App Connector
- App Connector Group
- App Connector Group Version Profile
- App Connector Group to App Connector Association
- App Connector Provisioning Key
- App Connector Version
- AppProtection Custom Control
- AppProtection Profile
- AppProtection Profile to AppProtection Control Association
- AppRecommendationReason
- Application Segment
- Application Segment to Server Group Association
- Audit
- Authentication
- Authentication Setting
- Backup
- Branch Connector
- Branch Connector Group
- Branch Connector Group to Branch Connector Association
- Branch Connector Provisioning
- Browser Access
- Browser Protection Profile
- Business Continuity Setting
- C2C IP Range
- C2C Registration
- CBI Banner
- CBI Certificate
- CORS/SameSite
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
- Credential To Rule Mapping
- Customer Custom Kubeflow Pipeline
- Customer Resiliency Setting
- Customer To UserDBMapping
- Customer To ZoneMapping Details
- Customer Version Profile
- DNS Search Domain
- Emergency Access
- Emergency Access User
- Enrollment Certificate
- Executive Insights Device
- Executive Insights User
- IdP Certificate
- IdP Configuration
- Ignore List
- Inspection Application
- Inspection Profile and ZSDefined Control Mapping
- Isolation Profile
- Kubeflow Pipeline Metadata
- Log Receiver
- Log Zone (Indicates the log store location for a region. This is only specified during organization account creation and is never modified.)
- Machine
- Machine Group
- Machine Group to Machine Association
- Machine Provisioning Key
- Microsegmentation Agent
- Microsegmentation Agent Group
- Microsegmentation App Zone
- Microsegmentation Provisioning Key
- Microtenant
- Notification
- Notifications
- Policy
- Policy Reorder
- Policy to Connector Group Association
- Policy to Server Group Association
- PolicyRule To ServiceEdgeGroup Mapping
- Portal Link
- Posture Profile
- Preferred SCIM Atrribute For Recommended Users
- Private Cloud
- Private Cloud Controller
- Private Cloud Controller Group
- Private Cloud Controller Group to Private Cloud Controller Mapping
- Private Service Edge
- Private Service Edge Group
- Private Service Edge Group Version Profile
- Private Service Edge Group to Private Service Edge Association
- Private Service Edge Group to Trusted Network Association
- Private Service Edge Provisioning Key
- Private Service Edge Version
- Privileged Approval
- Privileged Approval Association
- Privileged Capabilities
- Privileged Console
- Privileged Credentials
- Privileged Portal
- Privileged Portal to Privileged Console Association
- Privileged Remote Access
- Privileged Session
- Privileged Session Participant
- Probe Session
- Probe Session Entity
- Recommended Apps
- Restore Report
- Role
- SAML Attribute or Session Attribute
-
SCIM Attribute or User Attribute
If you are subscribed to ZIdentity for users, the **SAML Attributes **and **SCIM Attributes **resource types are replaced with **Session Attributes** and **User Attributes**. To learn more, see [Signing in to the Admin Portal](/unified/signing-admin-portal).
- Scheduled Backup Configuration
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
- ThreatLabz Control Bulk Deploy Job
- Trusted Network
- User Attribute
- User Portal
- User Portal to Portal Link Association
- User Risk Scores
- VersionProfile Visibility
- Workload Tag Group
- Private Applications to Isolation Association
- Znf
- Znf Group
- Znf Group to Znf Association
- Znf Provisioning Key
- ZPA to Isolation Association
- ZpnLocation
[]Within the **Action **column, click on the icon to view the differences between the pre-configuration and post-configuration changes related to an action. You can also click **Download** to save a JSON file (audit-config.json) that includes the pre- and post-configuration change values.
For policy configuration changes, if any criteria (e.g., SAML Attribute, Application Segments, Segment Groups, etc.) is set to "Any," the action is recorded but the configuration change details do not explicitly display "Any" for the changed criteria. For example, the following policy had its "SAML Attribute" setting set to "Any SAML Attribute" when it was created, then it was updated to include a segment group. However, the configuration details for "SAML Attribute" is not shown in either case:
[Show policy example](#AuditLogs_AllExample)
- View **Create**, **Update**, and **Delete **changes by clicking on the![zpa-auditlogs-updateicon.png](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-updateicon.png)
icon
Private Application logs the **Action** as well as any **Resource Type** associations made during that action. For example, when an admin creates a server and a server group within the Admin Portal, that server must be associated with a server group, and that server group must be associated with an App Connector group. So, both **Server Group to Server Association** and **Server Group to Connector Group Association** are displayed under **Resource Type**.
![Audit Logs page with association Resource Types displayed within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-transactionexample1.png)
Also, within the table, all associations for a particular **Action** are represented by color. In the example below, the Authentication is displayed as one transaction (in white), while the creation of a version profile and its associations are displayed as another transaction (in blue):
![Audit Logs page with two different Actions shown within the ZPA Admin Portal](/downloads/zpa/administration/about-audit-logs/zpa-about-audit-logs-colored-rows.png)
You can then view the pre- and post-configuration change details for each.
[Show Create server example](#CreateServerExample)
- View **Sign In** and **Sign Out** attempt details by clicking on the![zpa-auditlogs-signinicon.png](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-signinicon.png)
icon
[Show Sign In example](#signin)
[]
Pre- and post-configuration changes for a newly created policy with "SAML Attribute" set to "Any":
![Audit Logs page with Configuration Change window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-blanksamlatt-createpolicyexample1.png)
Pre- and post-configuration changes for the updated policy with "SAML Attribute" still set to "Any":
![Configuration Changes window for an updated policy with SAML Attribute set to All](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-blanksamlatt-updatepolicyexample1.png)
[]![Audit Logs page with Configuration Changes window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-createserverexample.png)
[]![Audit Logs page with Configuration Changes window within ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/company-and-administrators/about-audit-logs/zpa-auditlogs-signinactionexample.png)
[]![Post-Configuration Change Value with Dollar Sign Shown as Text Separator](/downloads/zpa/documentation-knowledgebase/company-and-administrators/audit-logs/about-audit-logs/zpa-auditlogs-csvdollarseparator.png)