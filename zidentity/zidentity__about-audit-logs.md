# About Audit Logs
Source: https://help.zscaler.com/zidentity/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1499166.pdf

Audit logs are records of activities performed by users in the ZIdentity Admin Portal. These logs enable administrators to track configuration changes, user management (e.g., creating, updating, and deleting users), tenant management, authentication settings changes, service assignments, and authentication events.
ZIdentity audit logs track key authentication events, including:
- Password-based logins by users or admins.
- Authentication via external IdPs (e.g., SAML, OIDC).
- Completion of multi-factor authentication (MFA).
- MFA performed by IdP-managed users within ZIdentity.
Administrators can also monitor authentication events triggered by users logging in through the Zscaler Client Connector or browser from the Audit Logs page.
Audit logs provide the following benefits and enable you to:
- View details on all the changes made by an administrator during a login session.
- Monitor the changes made by an administrator to policies or configurations via the ZIdentity Admin Portal or APIs.
About the Audit Logs Page
On the Audit Logs (Administration > System > Audit Logs) page, you can do the following:
- View logs. For each user, you can see:
- **Timestamp**: The date and time when the user performed the activity.
-
**Action**:** **The action performed by the user in the ZIdentity Admin Portal.
- [List of actions](#action)
-
**Category**: A UI page in the ZIdentity Admin Portal where the action is performed.
- [List of categories](#category)
- **Sub-Category**: The entity under the selected category. For example, user and group under the User Management category.
- **Resource**: The entity within the sub-category.
- **Admin ID**: The user's login ID.
- **Client IP**: The IP address for the user.
- **Interface**: The means by which the user performed their actions. The interface is either UI, Zscaler Client Connector, or API-based.
- **Result**: The outcome of an action (Success, Failure, or Partially Failed)
- Filter the data by time range, action, category, sub-category, interface, or result.
- Refresh audit logs to sync new data.
- Search for the logs by resource, admin ID, or client IP.
- Download a CSV file. The times in the CSV file are in PDT.
- [Modify the table and its columns](/zidentity/using-tables).
- [See configuration changes.](#configuration-step)
![Audit Logs page](/downloads/zidentity/audit-logs/about-audit-logs/zid-audit-logs-page.png)
- []Create
- Update
- Delete
- Password Change
- Reset Password
- Import
- Link
- Unlink
- Admin or User Login
- Admin or User Logout
- []User Management
- Guest Domains
- Tenants
- Authentication Settings
- Authentication
[]Click on the configuration changes you want to view. You are able to view visual differences between the pre- and post-configuration changes.
There are two types of changes you can view:
![Audit Logs Icons](/downloads/zslogin/audit-logs/about-audit-logs/zid-audit-logs-icons.png)
- View updates. The following is an example of the modification:
[See image.](#update)
- View additions or deletions. The following is an example of an addition:
[See image.](#add-or-delete-changes)
[]![Viewing addition changes in audit logs page](/downloads/zslogin/audit-logs/about-audit-logs/zid-add-or-delete.png)
[]![Viewing update changes in audit logs page](/downloads/zslogin/audit-logs/about-audit-logs/zid-updates.png)