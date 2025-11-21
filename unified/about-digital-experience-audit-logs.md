# About Digital Experience Audit Logs
Source: https://help.zscaler.com/unified/about-digital-experience-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1491696.pdf

Zscaler records the session information for each admin that signs in to the Admin Portal. The audit log displays information related to sign-in or sign-out attempts (e.g., timestamps, actions, IP addresses, etc.) and any configuration changes that were completed during their session such as updates or deletes.
Audit logs provide the following benefits and enable you to:
- Analyze administration sessions by reviewing in-depth information such as actions, categories, interface, or configuration changes (e.g., probe modifications, label alterations, etc.)
- Detect and investigate suspicious activity and track unauthorized access to the administrative user interface, demonstrating compliance with security policies.
- Customize filters to search for selected items and export them to a CSV file.
- Review configuration changes for comparison of the before-and-after administration sessions.
If an admin account makes five unsuccessful attempts to log in within one minute, the account is locked out for five minutes and the failed attempts are recorded in the audit log. Audit logs are stored for up to 6 months.
About the Digital Experience Audit Logs Page
On the Audit Logs page (Administration > Admin Management > Audit Logs > Digital Experience), you can do the following:
- View a list of actions that have occurred. For each action, you can see:
- **Timestamp**: The local time of the admin's last login or last logout.
- **Action**: The action performed by the admin in the Admin Portal.
- **Category**: A location in the Admin Portal where the action was performed.
- **Sub-Category**: A sublocation in the Admin Portal where the action was performed.
- **Resource**: The specific location within a subcategory.
- **Admin ID**: The admin's login ID.
- **Client IP**: The source IP address for the admin.
- **Interface**: Where the user performs their actions.
- **Result**: The outcome of an action in either Success or Failure.
- **Modification**: View configuration changes from an admin login.
-
Filter by Time Range, Action, Category, Sub-Category, Interface, or Result. You can also search for selected items on each filter.
The default Time Range is Current Day while the other filters are set to All.
- [List of potential Time Ranges](#Time-Ranges)
- [List of potential Actions](#Actions)
- [List of potential Categories](#Categories)
- [List of potential Sub-Categories](#Sub-Categories)
- [List of potential Interfaces](#Interfaces)
- [List of potential Results](#Results)
- Search for a specific Resource, Admin ID, or Client IP. Resource is the default.
- Download a CSV file of the displayed Audit Log. The times in the CSV file are in PDT.
- Modify the table and its columns.
- View configuration changes from an admin login.
[]
- Current Day
- Current Week
- Current Month
- Previous Day
- Previous Week
- Previous Month
- Custom
[]
- Activate
- Audit Operation
- All
- Create
- Delete
- Download
- Forced Activate
- Import
- Patch
- Report
- Sign In
- Sign Out
- Update
[]
- Activation
- Administration
- Administrator Management
- Alert
- All
- Cloud Service API Key
- Configuration
- Help
- ZDX Snapshot
- Software and Device Inventory
- Labels
- Login
- Organization Info
- Role Management
- Traffic Forwarding Resource
[]
- Activation
- Administrator
- Alert
- All
- Application
- Auditor
- Cloud Service API Key
- Deep Tracing
- EUSA Info
- Location
- Login
- ZDX Snapshot
- Password expiry
- Probe
- Remote Assistance
- Role Management
- SAML
- Self Service Settings
- Software and Device Inventory
- Labels
- Tenant
- Webhook
[]
- All
- ZDX UI
[]
- All
- Failure
- Success