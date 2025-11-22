# About Audit Logs
Source: https://help.zscaler.com/risk360/about-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1463846.pdf

Zscaler records the login name and IP address of every user who logs in to the Risk360 Admin Portal and changes configuration settings. Audit logs display the user's login and logout record (timestamps, actions, client IP, etc.), the configuration changes they perform, and the risk score change logs across categories and factors.
Audit Logs provide the following benefits and enable you to:
- View logs for every admin that logs in to the Risk360 Admin Portal.
- Monitor the changes made by the admins to policies or configurations.
- Analyze the time and reason for the risk score change due to an event.
About the Audit Logs Page
The Audit Logs page (Administration > Audit Logs) contains the following two tabs:
- [Audit Logs](#audit)
- [Score Change Logs](#risk-logs)
[]On the Audit Logs page (Administration > Audit Logs > Audit Logs), you can you can do the following:
- Download a CSV file. The times mentioned in the CSV file are in PDT.
- Search for the logs by Resource, Admin ID, or Client IP.
- Filter logs by Time Range, Action, Category, Sub Category, Interface, or Result.
- View a list of user logins. For each user login, you can see:
- **Timestamp**: The date and time (in UTC) of the user's action.
- **Action**:** **The action performed by the user in the Risk360 Admin Portal.
- **Category**: A location within the Risk360 Admin Portal where the action is performed.
- **Sub-Category**: The subject under the selected category.
- **Resource**: The item within the selected sub-category.
- **Admin ID**: The user's login ID.
- **Client IP**: The IP address for the user.
- **Interface**: How the user performed their actions. The interface is either UI or API based.
- **Result**: The outcome of an action (Success, Failure, or Partially Failed).
![Audit Logs Page in the Risk360 Admin Portal](/downloads/tech-pubs-drafts/risk360-draft-articles/about-audit-logs-draft-0/Risk360-audit-logs_0.png)
[]On the Score Change Logs page (Administration > Audit Logs > Score Change Logs), you can you can do the following:
- Filter the logs by Change Event, Category, Factor Group, or Factor.
- Search for logs.
- Download a CSV file. The times mentioned in the CSV file are in PDT.
- View a list of risk score changes. For each score change, you can see:
- **Timestamp**: The date and time (in UTC) of the user's action.
- **Change Event**: The event that affected the risk score (override, weight, or score).
- **Category**: The Risk360 category where the change occurred (External Attack Surface, Compromise, Lateral Propagation, or Data Loss).
- **Factor Group**: The factor group that is affected.
- **Factor**: The factor that is affected.
- **Previous Value**: The score before the event.
- **Current Value**: The current score after the event.
![Risk Score Change Logs](/downloads/tech-pubs-drafts/risk360-draft-articles/about-audit-logs-draft-0/Risk360-score-logs.png)