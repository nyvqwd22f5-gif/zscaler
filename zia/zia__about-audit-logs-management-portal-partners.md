# About Audit Logs in the Management Portal for Partners
Source: https://help.zscaler.com/zia/about-audit-logs-management-portal-partners
PDF: https://help.zscaler.com/pdf/com/en/1499791.pdf

Zscaler records the login name and IP address of every admin who logs in to the Management Portal and changes configuration settings. Audit logs display an admin's login and logout record (timestamps, actions, IP, etc.) and any configuration change they perform.
Audit logs provide the following benefits and enable you to:
- View changes made in the Management Portal, such as policy template modifications, alterations to the admins or tenant groups, etc.
- View details on all the actions that an admin performs during a login session.
- Detect and investigate suspicious activity, and track unauthorized access to the Management Portal.
**About the Audit Logs Page**
On the Audit Logs page, you can do the following:
- Filter the logs by time range, action, category, sub-category, or result.
- Search for the logs by resource, login ID, or client IP.
- Download a CSV file. The times in the CSV file are in PDT.
- View a list of actions performed in the Management Portal. For each action, you can see:
- **Timestamp**: The date and time of the admin's action.
- **Action**: The action performed by the admin in the Management Portal. It can be one of the following:
- Sign In
- Sign Out
- Create
- Update
- Delete
- **Category**: A location within the Management Portal where the action is performed. It can be one of the following:
- All
- Login
- Tenant Group
- Policy Template
- Admin Management
- Partner Settings
- **Sub-Category**: The subject under the selected category. It can be one of the following:
- Login
- Tenant Group
- Policy Template
- Partner Settings
- Roles
- Admin
- **Resource**: The item within the selected sub-category. It can be one of the following:
- Resource
- Login ID
- Client IP
- **Login ID**: The admin's login ID.
- **Client IP**: The source IP address for the admin.
- **Interface**: The interface through which the action is performed.
- **Result**: The outcome of an action, success or failure.
- **Cloud**: The cloud on which the action is performed.
![Audit Logs Page](/downloads/zia/zscaler-management-portal-partners/administration/about-audit-logs-management-portal-partners/Audit_Log_MPP1_0.png)