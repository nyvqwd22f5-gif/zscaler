# About the User Risk Report
Source: https://help.zscaler.com/zia/user-risk-report
PDF: https://help.zscaler.com/pdf/com/en/1403126.pdf

The User Risk Report allows you to monitor your organization's risk exposure from a user's perspective. The risk score is generated based on DLP violations, risky user behavior, unsanctioned cloud application usage, and other suspicious factors. If you want to view the report for a different user or date, use the appropriate drop-downs from the top of the page.
[See image.](#user-selection)
The User Risk Report provides the following benefits and enables you to:
- Configure stronger user-specific policies by monitoring user-level risk exposure.
- Study users' risk scores over time to determine the effectiveness of various user-specific policy configurations.
- Compare the user risk scores with your company and Zscaler cloud scores to identify risky users.
About the User Risk Report Page
On the Company User Risk Score Report page (Analytics > Company Risk Score > Top Risky Users), you can view the following sections:
- **Overview**: The section shows the following information about the user:
- **Email Address**: The email address of the user.
- **Department**: The [department](/zia/about-departments) that the user belongs to in your organization.
- **User Group**: The name of the [groups](/zia/about-groups) that the user belongs to in your organization.
- **Enrolled Devices**: The device names from which the user is enrolled.
- **Last Active**: The last time the user was active (day, date, and time).
- **Recent Risk Increases**: Any risk score increases since the last daily risk score computation. You can view the recent increases in the recent risk score only when **Real-Time Risk Score Updates **is enabled in the [Advanced Settings](/zia/configuring-advanced-settings).
- The semi-donut chart indicates the current risk category of the user, organization, and the cloud. The following risk categories are available in the chart:
- Low (0-25)
- Medium (26-50)
- High (51-75)
- Critical (76-100)
- **Risk Score Trend**: The graph shows the risk score trend for the user, company, and cloud. You can filter the graph for the last 7, 15, or 30 days. Click on a specific date in the graph to view the risk category for that date. You can also view the events that have contributed to the score by clicking **View** **Events Contributing To The Score**.
Click **View All Events** to view all the events that have contributed to the risk score. Click on an event, and you are redirected to the [Web Insights logs](/zia/about-insights-logs) page, where you can view the logs for that event.
- **DLP Violations by DLP Engine**: The donut chart indicates the percentage of DLP violations based on the DLP engines. The total number of DLP violations are displayed at the center of the donut. You can filter the data for the last 7, 15, or 30 days.
- **Top Unsanctioned Cloud Applications**: The chart shows all the unsanctioned cloud applications accessed by the user. The information can be viewed for the number of transactions or the total bytes used for each of the unsanctioned cloud applications. You can filter the data for the last 7, 15, or 30 days.
- **Top Risky URL Categories**: The tile shows the number of transactions made for each of the top risky URL categories. These top risky URL categories are identified by the Zscaler research team. The information can be viewed for the number of transactions or the total bytes used for each URL categories.
Select between **All**, **Allowed**, or **Blocked **tabs to see the URL categories for a specific status. You can filter the data for the last 7, 15, or 30 days.
![User Risk Report](/downloads/zia/dashboard-analytics/reports/user-risk-report/Real-time%20risk%20score%20deployement.png)
[]![User Risk Report - User Section](/downloads/zia/dashboard-analytics/reports/user-risk-report/user%20risk%20report.png)