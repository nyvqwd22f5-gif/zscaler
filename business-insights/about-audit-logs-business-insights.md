# About Audit Logs in Business Insights
Source: https://help.zscaler.com/business-insights/about-audit-logs-business-insights
PDF: https://help.zscaler.com/pdf/com/en/1473131.pdf

Zscaler records the login name and IP address of every user who logs in to the Business Insights Admin Portal and changes configuration settings. Audit logs display the user's login and logout record (timestamps, actions, client IP, etc.) and any configuration change they perform.
Audit Logs provide the following benefits and enable you to:
- View logs for every admin that logs in to the Business Insights Admin Portal.
- Monitor the changes made by the admins to policies or configurations.
About the Audit Logs Page
On the Audit Logs (Administration > Audit Logs) page, you can do the following:
- Filter by Time Range, Action, Category, Sub-Category, or Result.
- Download a CSV file. The timestamps in the CSV file are in PDT.
- Search for logs by Resource, Admin ID, or Client IP.
- View a list of user logins. For each user login, you can see:
- **Timestamp**: The date and time of the user's action.
- **Action**:** **The action performed by the user in the Business Insights Admin Portal.
- **Category**: A location within the Business Insights Admin Portal where the action is performed.
- **Sub-category**: The subject under the selected category.
- **Resource**: The item within the selected sub-category.
- **Admin ID**: The user's login ID.
- **Client IP**: The IP address for the user.
- **Interface**: Where the user performed their actions. Currently, the interface is BI UI for all logs, which means Business Insights UI.
- **Result**: The outcome of an action performed.
-
View the change in settings performed by the user for certain logs. The red section shows the previous values and the green section shows the updated values.
[See image.](#change-state)
![Audit Logs Page in the Risk360 Admin Portal](/downloads/zia/dashboard-analytics/about-audit-logs-0/Bussiness-Insights-Audit-Logs%20(1).png)
[]![View Change State](/downloads/zia/dashboard-analytics/about-audit-logs-0/Bussiness-Insights-Audit-Logs-change-state.png)