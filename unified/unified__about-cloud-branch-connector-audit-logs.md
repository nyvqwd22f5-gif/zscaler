# About Cloud & Branch Connector Audit Logs
Source: https://help.zscaler.com/unified/about-cloud-branch-connector-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1516661.pdf

Zscaler records the login name and IP address of every admin who logs in to the Admin Portal and changes policies or configuration settings. Audit logs display an admin's login and logout record (time stamps, actions, IP, etc.) and any configuration changes they completed. If an admin account makes 5 unsuccessful attempts to log in within one minute, the account is locked out for 5 minutes and the failed attempts are recorded.
Audit logs provide the following benefits and enable you to:
- Store audit logs for up to 6 months.
- Identify the login name and IP address of all users accessing the portal.
About the Audit Logs Page
On the Audit Logs page (Administration > Admin Management > Audit Logs > Branch and Cloud), you can do the following:
- View a list of admin logins:
- **Timestamp**: The local time of the admin's last login or last logout.
- **Actions**:** **The action performed by the admin in the Admin Portal or API.
- [List of all potential actions](#action)
- **Category**: A location in the portal where the action was performed.
- [List of all potential categories](#category)
- **Sub Categories**:
- [List of all potential sub-categories](#sub)
- **Resource**: The specific location within a sub-category.
- **Admin ID**: The admin's login ID.
- **Client IP**: The source IP address for the admin.
- **Interface**: The means by which the user performed their actions. The interface is either the Admin UI or an API.
- **Result**: The outcome of an action.
- If the action was a success, it is displayed as a green circle with a checkmark inside.
- If the action was a failure, it is displayed as a red circle with an X inside.
- [See configuration changes.](#config)
- Modify the table and its columns.
- Filter by time frame, actions, category, sub categories, interface, and/or result.
- Search for an audit log by resource, admin ID, or client IP.
- Download a CSV file. The times in the CSV file are in PDT.
![Audit Logs in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/administrator-role-management/about-audit-logs/About%20Audit%20Logs%20Brnch.jpg)
- []Sign In
- Sign Out
- Create
- Update
- Delete
- Patch
- Audit Operation
- Activate
- Force Activate
- Import
- Report
- Download
- []All
- Activation
- Advanced Settings
- Firewall Resource
- Location Management
- Traffic Forwarding Resource
- NSS
- Provisioning Management
- Forwarding Type
- Role Management
- API Key
- Administrator Management
- Firewall Access Control
- Audit Logs
- Login
- Cloud Management
- []Location
- Activation
- DNS
- Location Template
- Provisioning Template
- API Key
- Location Group
- Auditor
- Role Management
- Cloud & Branch Connector Group
- Login
- Gateways
- Cloud Management
- Administrator
- Network Service Group
- NSS Server
- Advanced Settings
- Network Service
- Password Expiry
- SAML
- Source IP Group
- Destination Group
- Firewall Forwarding
- NSS FEED
- Audit Logs
- Cloud & Branch Connector Location
[]Click the configuration changes you want to view. You'll be able to view visual differences between the pre-configuration and post-configuration changes.
There are two types of changes you can view:
![The two types of configuration changes you can view - additions/deletions and updates.](/downloads/cloud-connector/administration/administrator-role-management/about-audit-logs/cloudconnector-configchanges-2.png)