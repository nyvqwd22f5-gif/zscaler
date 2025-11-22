# About Audit Logs
Source: https://help.zscaler.com/zdx/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1416976.pdf

Zscaler records the session information for each admin that signs in to the ZDX Admin Portal. The audit log displays information related to sign-in or sign-out attempts (e.g., timestamps, actions, IP addresses, etc.) and any configuration changes that were completed during their session such as updates or deletes.
Audit logs provide the following benefits and enable you to:
- Analyze administration sessions by reviewing in-depth information such as actions, categories, interface, or configuration changes.
- Customize filters to search for selected items and export them to a CSV file.
- Review configuration changes for comparison of the before-and-after administration sessions.
If an admin makes 5 consecutive unsuccessful attempts to sign in within 1 minute, the account is locked out for 5 minutes and the failed attempts are recorded.
Audit logs are stored for a period of 6 months.
About the Audits Log Page
On the Audit Logs page (Administration > Administration Controls > Audit Logs), you can do the following:
- View a list of Admin Logins. For each admin login, you see:
- **Timestamp**: The local time of the admin's last login or last logout.
- **Actions**: The action performed by the admin in the ZDX Admin Portal.
- **Category**: A location in the ZDX Admin Portal where the action was performed.
- **Sub-Category**: A sublocation in the ZDX Admin Portal where the action was performed.
- **Resource**: The specific location within a subcategory.
- **Admin ID**: The admin's login ID.
- **Client ID**: The source IP address for the admin.
- **Interface**: Where the user performs their actions.
- **Trace ID**: The trace ID is generated and logged for transactions associated with ZIA API requests made via [Zscaler OneAPI](/oneapi/understanding-oneapi). The trace ID helps admins correlate API transactions with the OneAPI platform and you can use the trace ID for debugging purposes.
- **Result**: The outcome of an action in either Success or Failure.
- **Modification**: View configuration changes from an admin login.
-
Filter by Time Range, Action, Category, Sub-Category, Interface, or Result. You can also search for selected items on each filter.
The default Time Range is Current Day while the defaults of the other filters are set to All.
- [List of potential Time Ranges](#Time-Ranges)
- [List of potential Actions](#Actions)
- [List of potential Categories](#Categories)
- [List of potential Sub-Categories](#Sub-Categories)
- [List of potential Interfaces](#Interfaces)
- [List of potential Results](#Results)
- Download a CSV file of the displayed Audit Log. The times in the CSV file are in PDT.
- Search for a specific Resource, Admin ID, or Client IP. Resource is the default.
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
- Inventory Management
- Login
- Organization Info
- Role Management
- Software and Device Inventory
- Tags
- Traffic Forwarding Resource
- ZDX Snapshots
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
- Password Expiry
- Probe
- Remote Assistance
- Role Management
- SAML
- Self Service Settings
- ZDX Snapshots
- Software and Device Inventory
- Tenant
- Webhook
[]
- All
- ZDX UI
[]
- All
- Failure
- Success
![Audit Logs Page](/downloads/zdx/administration/about-audit-logs/ZDX-AuditLog-2.png)