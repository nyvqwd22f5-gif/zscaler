# About the Data Discovery Report
Source: https://help.zscaler.com/zia/about-data-discovery-report
PDF: https://help.zscaler.com/pdf/com/en/1440806.pdf

The Data Discovery Report gives high-level visibility and insight into your organization's [Data Loss Prevention (DLP)](/zia/about-data-loss-prevention) content, allowing you to monitor and analyze DLP data in a single location. The report provides not only information based on your organization's DLP policies and dictionaries, but also on machine-learning data based on Zscaler analysis of the content in your organization.
The report contains a combination of static and interactive widgets. The latter allow you to click items on charts so you can instantly jump from a high-level chart to more granular information.
The Data Discovery Report provides the following benefits and allows you to:
- See a summary of different types of DLP data in a single location.
- Drill down as needed to see a more granular view of your data.
- Use machine learning from the Zscaler service to gain insight into your data.
About the Data Discovery Report Page
On the Data Discovery Report page (Analytics > Data Discovery Report), you can do the following:
- []Choose a different time frame from the menu. By default, the Data Discovery Report displays data for the last 7 days, but it also offers 1-day, 30-day, and 90-day time frames.
-
[]Set filters to determine the data shown, then click **Apply**:
- [Policy Actions](#filter-policy-actions)
- [Application Status](#filter-application-status)
- [Content Type](#filter-content-type)
- [Traffic Direction](#filter-traffic-direction)
If you don't want the filters to appear at the top of the report, click **Hide Filters**.
- View information about your DLP data on a series of widgets. When you click an item on an interactive chart or click **Analyze More** on a widget, the [Data Discovery Details page](/zia/viewing-data-discovery-details) opens to show a more granular view of the data for the item. The Data Discovery Report page contains the following widgets:
- [Files](#files-widget)
- [Users](#users-widget)
- [Applications](#applications-widget)
- [Files Trend](#files-trend-widget)
- [Files in Top 10 Categories](#top-10-categories-widget)
- [Top 10 Users](#top-10-users-widget)
- [Timeline for Files in Top 10 Categories](#timeline-widget)
- [Top 10 Applications](#top-10-apps-widget)
The widgets on the Data Discovery Report page are not editable and cannot be moved.
![Screenshot of the Data Discovery Report page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-data-discovery-dashboard/zia-data-discovery-report-page.png)
[]Select **All**, **Allow**, or **Block**. To learn more, see [About Policy Enforcement](/zia/about-policy-enforcement).
[]Select **All**, **Sanctioned**, or **Unsanctioned**. To learn more, see [About Cloud Application Status](/zia/about-cloud-application-status).
[]Select an option to filter by content type:
- **DLP Dictionaries: **Filter data based on the DLP dictionaries configured for your organization. To learn more, see [About DLP Dictionaries](/zia/about-policy-enforcement).
- **DLP Engines: **Filter data based on the DLP engines configured for your organization. To learn more, see [About DLP Engines](/zia/about-dlp-engines).
- **DLP Rules: **Filter data based on the DLP rules configured for your organization. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection) and [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection).
-
**ML Categories: **Filter data based on machine-learning analysis by the Zscaler service. The content is divided into Document Type categories. To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters/#download-document-type).
[]Select **All**, **Download**, or **Upload**. To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters).
[]The number of files used during the selected time period, along with the percentage change for the time period.
[]The number of active users during the selected time period, along with the percentage change for the time period.
[]The number of applications used during the selected time period, along with the percentage change for the time period.
[]A chronological line chart showing the number of files used in sanctioned and unsanctioned applications. Hover over a date on the line chart to see the number of files from that date for sanctioned and unsanctioned applications.
[]A Sankey chart based on the selection in the **Content Type** filter that shows information for up to 10 content categories at a time. Hover over a line in the chart to see the percentage that the files in the category represents as it relates to the total number of files.
[]A bar chart that shows up to 10 of the top users in the organization. Hover over the bars in the chart to see a breakdown of sanctioned vs. unsanctioned application files for each user. The widget also shows the total number of files from users not in the top 10.
[]A bubble chart that shows a day-by-day breakdown of the number of files used in up to 10 content categories at a time.
[]A bar chart that shows the number of applications in the organization during the selected time period. Hover over the bars to see the number and percentage of applications that are sanctioned and unsanctioned. The widget also shows the total number of applications not in the top 10.