# Viewing Application Segments Usage
Source: https://help.zscaler.com/zpa/viewing-application-segments-usage
PDF: https://help.zscaler.com/pdf/com/en/1531128.pdf

Application Segments Usage insights provide visibility into which application segments are being actively used or not. These insights can help you assess and determine unused application segments for improvement consideration. The Application Segments Usage insights provide:
- A distribution of users and their associated application segments.
- Most used application segments.
- Least used application segments.
[See image.](#appSegmentUsageGif)
[]![Application Segments Usage page](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-segments-usage-doc-59370/zpa-application-segments-usage-insights-page-gif.gif)
Application Segments Usage Report
The Application Segments Usage Report contains the following information:
-
The number of application segments applied to a percentage distribution of users. This includes:
- **Most Used Application Segments**: Displays the number of most used application segments.
- **Unused Application Segments**: Displays the number of unused application segments.
The distribution of users is calculated based on the number of unique users (must be more than zero users) against each application segment. Then the distribution categorizes the users into 1 of 10 percentage bars based on their usage of the application segment. Each bar indicates a tenth percentage of application segments based on usage. You can click a bar to view application segment usage data based on that user group. The percentage is rounded to the nearest whole number.
-
**Current Report Information**: Displays the current report information based on when it was last updated.
[See image.](#currentReportInfo)
- **Launch Tour**: Launches a series of guided steps on how to interact with the Application Segments Usage page.
-
**Run Report**: Generates the report to include data from the selected time range. In the time range drop-down menu, you can select a preset range (e.g., **14 Days** or **30 Days**). By default, the time range of the report is set to **14 Days**. The report automatically expires after 90 days. You cannot run the report if there is no more data to add when the report was recently updated.
Run Report is disabled for 72 hours before and after 12:00 AM on the first Saturday of every month due to scheduled automatic reports. You cannot manually generate a report during this time. Additionally, customers with the Segmentation Add-On feature can generate one report per day, and customers without the feature can generate one report every 90 days.
[See image.](#runReportInfo)
[]![Viewing the Current Report Information in the Application Segment Usage Insights page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-segments-usage-insights/application-segment-usage-insights-current-report.png)
[See image.](#applicationSegmentUsageReportInfo)
[]![Run a report on the Application Segments Usage insights page ](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-segments-usage-doc-59370/zpa-app-segment-usage-run-report.png)
[]![Application Segment Usage report information](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-segments-usage/zpa-app-segments-usage-reports.png)
Application Segments Usage Chart and Table
The Application Segments Usage page consists of two charts:
- [Usage](#usage)
- [Discovered Host Count](#discoveredHostCount)
[]The Application Segments Usage chart and table provide the following information:
- **Application Segment Usage Bar Chart**: Displays the distribution of application segment usage from access policy rules. Click a bar to specify the application segments displayed in the table. The default is set to **Unused Application Segments**.
- [See image.](#applicationSegmentUsageBarChartInfo)
-
**Application Segment Filter**: Select specific application segments to display in the chart and table.
[See image.](#applicationSegmentUsageTableFilter)
- **View Application Segments**: Allows you to access the [Defined Application Segments](/zpa/about-applications) page to manage the defined application segments.
- **Application Segment Table**: Displays the following information for each application segment:
- **Application Segment**: The name of the application segment.
- **Segment Group**: The name of the segment group.
- **Applications**: The number of applications accessed. If the same application is accessed through different ports and/or protocols (e.g., TCP, UDP), then each application is counted separately.
- **Access Policy Rules**: The number of access policy rules that allowed access to the application segment.
- **Unique Users**: The number of unique users impacted by the application segment.
- **Transactions**: The number of ZPA transactions going through the application segment.
- **Actions**: The available actions for the application segment. This includes:
- **Edit**: Edit the application segment in the Edit Application Segment window. To learn more, see [Editing Defined Application Segments](/zpa/editing-application-segments).
- **Application Segments and User Details**: View the application segment's usage details. To learn more, see [Viewing Application Segment Usage Details](/zpa/viewing-application-segment-usage-details).
[]![Bar Chart Selection within the Application Segment Usage Insights page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-segments-usage/zpa-app-segments-usage-bar-chart.png)
[]![Application Segment Filter within the Application Segment Usage Insights Table](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-segments-usage-insights/application-segment-usage-insights-table-filter.png)
[See image.](#applicationSegmentUsageDetails)
[]![Application Segment Usage Page within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-segments-usage/zpa-app-segment-usage-full-page.png)
[]The Discovered Host Count chart and table provide the following information:
-
**Discovered Host Count Bar Chart**: Displays the top 10 application segments by discovered host count.
[See image.](#discoveredHostCountBarChart)
- **Application Segment Filter**: Select specific application segments to display in the chart and table.
- **Application Segment Table**: Displays the following information for each application segment:
- **Application Segment**: The name of the application segment.
- **Segment Group**: The name of the segment group.
- **Discovered Host Count**: The number of discovered hosts.
[See image.](#discoveredHostCountPage)
[]![Discovered Host Count Bar Chart](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-segments-usage-doc-59370/zpa-app-segment-usage-insights-discovered-host-count-bar-chart1.png)
[]![Viewing the Discovered Host Count Chart and Table](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-segments-usage-doc-59370/zpa-app-segment-usage-insights-discovered-host-count-full-page1.png)