# About User Investigation
Source: https://help.zscaler.com/zia/about-user-investigation
PDF: https://help.zscaler.com/pdf/com/en/1479756.pdf

User Investigation provides scan results and data specific to all the endpoints connected to a user. You can view the user with the most number of activities, incidents, their department, risk profile, among other metrics. You can further drilldown the user to specific time, severity, and destinations for the user activities by clicking on a user. This helps you to configure necessary policy control for specific users to protect your organization's data.
User Investigation provides the following benefits and enables you to:
- Gain visibility into endpoint scan data for each user.
- Analyze Endpoint Data Loss Prevention (DLP) activities and incidents from various perspectives like departments, DLP engines, AI & ML categories, file type, etc. for each user.
- Prevent data leakage by configuring user-specific Endpoint DLP rules for risky users.
About the User Investigation Page
On the User Investigation page (Analytics > Endpoint Data Scan > User Investigation), you can do the following:
- Filter the data for a specific user risk profile, department, or last updated.
- Search the data for a specific user.
- View a list of users with endpoints. For each user, you can view:
- **User**: The email address of the user. Click a user to open a drawer that shows scan details for that user. To learn more, see [Analyzing Endpoint DLP Scan Details for a User](/zia/analyzing-endpoint-dlp-scan-details-user).
- **User Risk Profile**: The risk profile assigned to the user (Low, Medium, High, or Critical). Zscaler analyzes your organization's user behavior trends and builds a risk profile dynamically by assigning User Risk Score to each user. To learn more, see [Understanding User Risk Score](/zia/understanding-user-risk-score).
-
**Endpoint Name**: The name of the endpoints connected to the user's device. You can view the total number of endpoints connected to the user's device next to the device name. Click the number to open a window that shows the total number of files scanned and the number of sensitive files discovered from each endpoint.
[See image.](#list-of-endpoints)
- **Incidents**: The number of user activities that triggered Endpoint DLP rules over the last one month.
- **Activities**: The number of user actions that triggered DLP engines over the last one month.
- **Sensitive Files Discovered**: The total number of sensitive files discovered from all the user's endpoints. This data is updated every day.
- **Last Updated**: The date and time when the last update was received from the user's endpoints.
- **Department**: The name of the department that the user belongs to.
- [Modify the table and its columns](/zia/using-tables).
Use the arrows at the bottom of the page to go to view the next entries. You can also select the number of entries you want to view in the table (3, 5, or 15 rows).
![User Investigation Page](/downloads/zia/policies/endpoint-data-loss-prevention/about-user-investigation/ZIA-6.2r-User-Investigation-Page.png)
[]
[]![List of Endpoints for a User](/downloads/zia/policies/endpoint-data-loss-prevention/about-endpoint-data-scan/ZIA-6.2r-List-of-Endpoints-for-User.png)