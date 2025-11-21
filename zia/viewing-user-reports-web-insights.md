# Viewing User Reports in Web Insights
Source: https://help.zscaler.com/zia/viewing-user-reports-web-insights
PDF: https://help.zscaler.com/pdf/com/en/1401081.pdf

To get the most out of viewing user traffic in Web Insights, you can view the top users and can also see how much time users spend on the internet.
Top Users Reports
To view and export a list of top users:
- Go to **Analytics **>** Web Insights**.
- Select **User** as the data type to list the top users. You can also click **Export All Active Users** to export the list of active users to a CSV file.
[See image.](#export-users)
By default, user reports also include locations. You can [exclude locations](/zia/how-do-i-exclude-locations-user-related-reports) in user reports by creating new or editing existing widgets.
Time-Based Reports
You can check how much time users spend browsing the internet. Zscaler calculates the user's browsing time by adding the overall time spend on the internet across all tabs and devices within the filtered time period. For example, if a user logs in to www.facebook.com from mutiple tabs or devices, the total time spend by the user is calculated by adding all the sessions from each tab or device. Other factors such as traffic running via scripts, throttling by servers when pushing updates, etc. contributes to an inflated time spend data.
This report provides data for the last seven days only.
To create a time-based report:
- Go to **Analytics **>** Web Insights**.
- Select **User** as the data type.
- Expand **Add Filter** and choose **Received Bytes**.
[See image.](#insights-user-rb)
- Leave the Received Bytes values as is and click **Apply Filters**.
- Click **Time** to view the users who have spent the most time browsing.
[See image.](#time-unit)
- You can drill down and get more information about the user's internet activities and view the logs as well. To learn more about drilling down, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
[]![Screenshot of the Export All Active Users icon in the Web Insights Page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/zia6.2r-insights-export-users_0.png)
[]![Screenshot of the Web Insights data type User and the filter Received Bytes](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/zia-insights-user-received-bytes_0.png)
[]![Screenshot of the Web Insights data type User with the unit Time selected](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/zia-insights-time-unit_0.png)