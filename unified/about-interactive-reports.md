# About Interactive Reports
Source: https://help.zscaler.com/zia/about-interactive-reports
PDF: https://help.zscaler.com/pdf/com/en/1399526.pdf

[Watch a video about Interactive Reports.](https://fast.wistia.net/embed/iframe/dj64tv044u)
The Interactive Reports page presents a wide range of standard reports, based on your organization's subscription, and provides the ability to create up to 500 custom reports as well. It supports real-time interactive analysis. You can seamlessly drill down from any report to the logs, where you can view details such as the specific URLs that users requested, risk score of each URL, and more.
Interactive reports support UTF-8 characters enabling the display of special characters.
An administrator's [role](/zia/how-do-i-add-admin-roles) and [scope](/zia/about-admin-scope) define which reports the administrator can view.
About the Interactive Reports Page
On the Interactive Reports page, you can do the following:
- Search for a specific report or for any [scheduled reports](/zia/scheduling-reports).
- Create a custom report from scratch, copy from an existing report, or import a report. To learn more, see [Creating or Copying a Report](/zia/how-do-i-create-new-report) and [Exporting and Importing Reports](/zia/how-do-i-export-and-import-reports).
The widgets for the report Top Threat Names cannot be used in custom reports.
[See image.](#top-section)
Standard Reports
In the Standard Reports tab, the reports are grouped into sections that can be expanded or collapsed. When you expand all sections, you’ll see a tile view of each report.
Standard reports are available based on your organization's subscriptions. For example, you can view mobile security reports only if your organization has a Mobile Security subscription.
Standard reports cannot be deleted.
[See image.](#standard-reports)
Custom Reports
In the Custom Reports tab, the reports are grouped into sections, each of which shows a tile view of each report.
You can delete a custom report by selecting the report's check box, and then clicking the Delete button. You can also select or deselect all reports for deletion. Admins can only delete custom reports. Admins with the default super admin role can delete any report; all other admins can only delete their own reports. If the report was in the Favorites tab, it is deleted from there as well. Additionally, if it was a scheduled report, its schedule is deleted as well.
Deleted reports cannot be restored.
You can also export a custom report. To learn more, see [Exporting and Importing Reports](/zia/how-do-i-export-and-import-reports).
[See image.](#custom-reports)
My Favorites
In the My Favorites tab, you can view all the reports you have starred as your favorites. Each admin can favorite up to 50 reports. In this tab, you’ll see a tile view of each report. You can remove a report from this tab by clicking on the blue star on the upper right-hand corner of the report’s tile.
[See image.](#my-favorites)
Scheduled Reports
In the Scheduled Reports tab, you can schedule a standard or custom report for regular distribution to specified recipients. To learn more, see [Scheduling Reports](/zia/scheduling-reports).
Viewing a Report
To view a standard, custom, or favorite report in full, click the **View** button on the report you’d like to see. In the report:
- Add a report description. When you edit a custom report or create a new report, you can add a description for your report.
- Choose a time frame. You can choose a predefined time frame or select **Custom** to set the start date and time. When you set a custom time frame:
- The start date cannot be earlier than January 1, 2012.
- The maximum time range is 90 days.
- Selecting multiple days will result in seeing the sum of bytes/transactions per day in charts.
- View the widgets that the report contains. To learn more, see [About Widgets](/zia/about-widgets).
- Hover over a chart’s data, and click on it to obtain more information.
- Click the **View Logs** option to view the chart’s logs in the [Insights Logs](/zia/about-insights-logs) page. If you want to go back to the report, click **Back to Original**. This option is not available for charts that display secure browsing class, data or status, because they only use samples as their data units.
- Click the **Analyze Chart** option to view the chart in an [Insights](/zia/about-insights) page. If you want to go back to the report, click **Back to Original**. To learn more, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
- A widget displays the top five items and groups everything else under Other. Click **Show Details** to see the items that were grouped under Other.
- Edit or delete a note. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/adding-notes-dashboard-interactive-reports).
- Hide or show all notes. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/adding-notes-dashboard-interactive-reports).
- Add a note to the report. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/adding-notes-dashboard-interactive-reports).
- Add or remove a selected report to the **Favorites** tab. Each admin can favorite up to 50 reports.
- Edit a custom report. Admins can only edit custom reports. Standard reports cannot be edited. Admins with the default super admin role can edit any custom report; all other admins can only edit their own reports. To edit a standard report, you can copy it, and then edit it.
- Copy a report. Copying a standard report allows you to create a new custom report.
- Schedule a standard or custom report for regular distribution to specified recipients. To learn more, see [Scheduling Reports](/zia/scheduling-reports).
- Print a report. To learn more, see [Printing Reports](/zia/printing-reports).
- View the Weblog time, which appears at the bottom of every window. The Nanolog servers collect the logs of all users worldwide, and then consolidates and correlates them. The Weblog time displays the date and time of the logs that are being processed by the Nanolog servers.
![A sample of a custom interactive report with its different sections highlighted](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-interactive-reports/ZIA-6.1-Interactive-Reports-Report-Sections.png)
[]![The Search bar and New Report button at the top of the Interactive Reports page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-interactive-reports/ZIA-6.1-Interactive-Reports-Top-Section.png)
[]![The Standard Reports tab in Expand All view. The thumbnail of each report is shown.](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-interactive-reports/ZIA-6.1-Interactive-Reports-Standard.png)
[]![The Custom Reports tab with the thumbnail of each report. Each thumbnail has a checkbox on the top-left corner.](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-interactive-reports/ZIA-6.1-Interactive-Reports-Custom.png)
[]![The My Favorites tab with the thumbnail of each favorited report. Each thumbnail has a blue star on the top-right corner.](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-interactive-reports/ZIA-6.1-Interactive-Reports-Favorites.png)