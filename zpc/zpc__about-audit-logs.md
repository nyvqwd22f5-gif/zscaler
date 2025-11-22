# About Audit Logs
Source: https://help.zscaler.com/zpc/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1393856.pdf

Zscaler Posture Control (ZPC) can trace and monitor user activity as a security standard and best practice. ZPC records session information for every administrator who signs in to the ZPC Admin Portal. The audit logs provide a chronological list of activities performed by users in the tenants that are onboarded to ZPC. The logs are captured for several actions, including sign-in and sign-out attempts, adding or removing cloud accounts, configuring alerts, IaC integrations, vulnerability management, enabling or disabling policies, downloading reports, etc., including any configuration changes that users handled during a session. To see the list of actions that are recorded, see [Audit Log Events](/zpc/audit-log-events).
Administrators can view the audit logs for the past 60 days.
Audit logs provide the following benefits and enable you to:
- Monitor events and user activity for any anomalous behavior so that you can investigate and remediate the issue. This process is essential for both internal cybersecurity management and for external compliance auditors.
- Monitor data for any security breach or vulnerability.
- Gain insight into the usage and security of cloud resources.
- Reduce the likelihood of security risks by implementing security policies and best practices.
- Maintain compliance with standard regulations.
About the Audit Logs Page
On the Audit Logs (Administration > Audit Logs) page, you can do the following:
- View a list of events with the following details:
- **Event ID**: The unique identifier for the event.
- **Event Timestamp**: The date and time in Coordinated Universal Time (UTC), when the event occurred.
- **Tenant Name**: The name of the ZPC tenant.
- **User**: The email ID of the administrator who initiated the action.
- **Login Type**: The type of login (Local or SAML) that was initiated.
- **Interface**: The type of interface (browser, virtual machine, etc.) that is used to sign in to the ZPC Admin Portal.
- **Role Name**: The role assigned to the user.
- **IP**: The IP address of the interface where the administrator performs the action.
- **User Agent**: The browser application that was used to perform the action.
- **Action**: The action performed by the administrator. To learn more about the list of actions that are recorded, see [Audit Log Events](/zpc/audit-log-events).
- **Data Object Type**: The object (e.g., Alert Rule, Custom Policy, IaC Integration, etc.) within the module on which the action is being performed.
- **Data Object Name**: The name (e.g., the policy name that was disabled) of the object specified by the user.
- **Module**: The module (e.g., Administration, Alerts, Investigation, etc.) that was accessed in the ZPC Admin Portal.
- **Sub Module**: The sub-module (e.g., security policies, cloud alerts, etc.) that was accessed within the module in the ZPC Admin Portal.
- Click each filter to choose the required data that must be displayed in the column. For example, you can set the **Event Time** filter to view the logs that were recorded in the last 24 hours. You can add additional filters. To learn more, see [Using Filters](/zpc/using-filters).
- Select the previously saved filter.
- [Show or hide filters](/zpc/using-filters).
- Export the audit log data to a CSV file.
- Search the table for the required data.
- Sort the column data.
- [Modify the table and its columns](/zpc/using-tables).
- Click the **Configuration Changes** icon (![Configuration changes icon](/downloads/zpc/administration/audit-logs/about-audit-logs/zpc-auditlog-actionsicon.png)
)to view the configuration changes. [See image.](#configchanges)
![View the Audit Logs page](/downloads/zpc/administration/audit-logs/about-audit-logs/zpc-auditlog-page-new.jpg)
[![View the configuration changes](/downloads/zpc/administration/audit-logs/about-audit-logs/zpc-auditlog-configchanges.jpg)
]