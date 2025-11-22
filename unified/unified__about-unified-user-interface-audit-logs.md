# About Unified User Interface Audit Logs
Source: https://help.zscaler.com/unified/about-unified-user-interface-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1500641.pdf

Zscaler records the session information for each admin that signs in to the Admin Portal. The audit log displays information related to sign-in or sign-out attempts (e.g., timestamps, actions, IP addresses, etc.) and any configuration changes that were completed during their session such as updates or deletes.
Audit logs provide the following benefits and enable you to:
- Analyze administration sessions by reviewing in-depth information such as actions, categories, interface, or configuration changes (e.g., password modifications, linking or unlinking tenants, etc.)
- Detect and investigate suspicious activity and track unauthorized access to the administrative user interface, demonstrating compliance with security policies.
- Customize filters to search for selected items and export them to a CSV file.
- Review configuration changes for comparison of the before-and-after administration sessions.
If an admin account makes five unsuccessful attempts to log in within one minute, the account is locked out for five minutes and the failed attempts are recorded in the audit log. The audit logs are stored for up to 6 months.
About the Unified User Interface Audit Logs Page
On the Audit Logs page (Administration > Admin Management > Audit Logs > Unified User Interface), you can do the following:
- View a list of actions that have occurred. For each action, you can see:
- **Time stamp**: The date and local time the action occurred.
- **Action**:** **The action performed by the admin in the Admin Portal or the action performed by an API.
- [List of all potential actions](#action)
- **Resource**: The specific subject within a sub-category. For example, if an admin adds a new admin, then the resource is the name of the admin that was added.
- **Admin ID**: The admin's login ID or the internal API user (`oauth-<rolename>$@<orgid>.<cloud-domain>`) if an APIs action was authenticated by an external OAuth 2.0 authentication server.
- **Client IP**: The source IP address for the admin or the client application's IP address that executed the API.
- **Result**: The outcome of an action:
- **Success**
- **Failure**
- **Partially Failed**
- **Category**: A location in the Admin Portal where the action was performed by a user or an API.
- [List of all potential categories](#category)
- **Interface**: The means by which the action was performed:
- **UI**
- **API**
- **SCIM API**
- View configuration changes.
- [Viewing pre and post configuration changes for a log entry.](#config)
- [Modify the table and its columns.](/unified/using-tables)
- Filter by time range, action, category, sub-category, interface, and/or result.
- [List of all potential sub-categories](#sub)
- Search for an audit log by resource, admin ID, or client IP. The search only shows results starting with or completely matching the search string.
- Download a CSV file.
- []Create
- Update
- Delete
- Password Change
- Reset Password
- View Remote Assistance Details
- Import
- Link
- Unlink
- []Guest Domains
- Authentication Settings
- Tenants
- User Management
- []Guest Domains
- Password Policy Change
- Identity Providers
- Advance Settings
- Locations
- Location Group
- Sign-On Policy
- Remote Assistance
- Authenticaion Methods
- OAuth2 Client
- Tenats
- Service Assignment
- Device Group Assignment
- Service Runtime Assignment
- Services
- Roles
- Branding
- Tenant Migration
- User
- Custom Attribute
- Group
- Department
- User Authenticator
[]Click on the configuration changes you want to view. You'll be able to view visual differences between the pre-configuration and post-configuration changes.
There are two types of changes you can view:
![""](/downloads/zia/authentication-administration/administrator-role-management/about-audit-logs/ZIA-Audit-Logs-configuration-changes.png)
- View additions or deletions. The following is an example of an addition:
[See image.](#addition)
- View updates. The following is an example of modifications to a policy:
[See image.](#update)
[]![""](/downloads/zia/authentication-administration/administrator-role-management/about-audit-logs/ZIA-Audit-Logs-configuration-changes-add.png)
[]![""](/downloads/zia/authentication-administration/administrator-role-management/about-audit-logs/ZIA-Audit-Logs-configuration-changes-update.png)