# About Widgets
Source: https://help.zscaler.com/unified/about-widgets
PDF: https://help.zscaler.com/pdf/com/en/1497411.pdf

[Dashboards](/unified/about-dashboards) and [reports](/unified/about-interactive-reports) contain widgets that present data in interactive charts.
In widgets, roll over a chart to obtain more information about an item, click it, and select one of the following:
-
Click** View Logs** to see its associated logs. To learn more, see [About Insights Logs](/unified/about-insights-logs).
The **View Logs** option isn't available for charts that display secure browsing class, data or status, because they only use samples as their data units.
- Click **Analyze Chart** to view the chart in an Insights** **page, and then drill down to the logs. To learn more, see [Analyzing Traffic Using Insights](/unified/analyzing-traffic-using-insights).
![The View Logs and Analyze Chart options for a Zscaler widget](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Widgets-View-Logs-Analyze-Chart.png)
A widget displays the top five items and groups everything else under Other. You can then click **Show Details** to see the items that were grouped under Other.
![An Other slice from a Zscaler widget pie chart](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Widgets-Other-Slice.png)
Using Charts in Widgets
When you edit a widget in a [dashboard](/unified/about-dashboards) or [report](/unified/about-interactive-reports), or [analyze a chart](/unified/analyzing-traffic-using-insights) in Web Insights, Mobile Insights, Firewall Insights, DNS Insights, or Tunnel Insights you can choose to display the following types of charts:
- Pie Chart
- Bar Chart
- Line Chart
- Value Chart
- Table Chart
![The Chart Types section in the Edit Widget window](/downloads/zia/dashboard-analytics/about-widgets/ZIA-6.2r-edit-widget.png)
Some guidelines on using charts are:
- Use line charts to view trends such as bandwidth usage trends.
- Pie and line charts display the top five results and Other, which is the cumulative total of the remaining results. You can click Other and Show Details to list the additional items grouped under Other.
- Bar charts and tables display the top 100 results and the remaining results are grouped under Other.
- On a dashboard or report, administrators can resize widgets that contain a table, a bar chart or a line chart. Widgets with pie charts can't be resized.
- Data in charts are aggregated based on the local time of the administrator, except for trend charts. For example, data for Current Day will be summarized from 12 AM to 11:59 PM local time for the administrator viewing the report.
- Bar charts and tables support the ability to view the top 5, 10, 25, 50 or 100 items. The menu that lists these options (Top 5, Top 10, Top 25, Top 50, and Top 100) appears when you view a bar chart or table in Logs > Insights > Web Insights.
Adding Widgets
To create a new widget:
- Do one of the following:
-
If you're adding a widget to a dashboard, click the **Add Widget** icon. A dashboard can contain up to 12 widgets.
![The Add Widget icon on Zscaler dashboards](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Dashboard-Add-Widget-Icon.png)
-
If you're adding a widget to a custom report, click the **Add Widget**. A report can display up to 20 widgets.
![The Add Widget button on custom Zscaler reports](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Report-Add-Widget-Button.png)
The **New Widget** window appears.
- In the **New Widget** window:
- If you're creating a dashboard widget, specify which type of data the widget displays. Click **Web**, **Mobile**,** Firewall**,** DNS**, or** EDLP** at the top of the window (the available options depend on your organization's subscriptions).
- **Title:** Enter a title, up to 50 characters, for the widget.
- **Data Type:** From the dropdown menu, choose the type of data that the widget displays. You can refine the data by applying filters. For more information on selecting data types and filters, see [Web Data Types and Filters](/unified/web-data-types-and-filters), [Mobile Data Types and Filters](/unified/mobile-data-types-and-filters), [Firewall Data Types and Filters](/unified/firewall-data-types-and-filters), [DNS Data Types and Filters](/unified/dns-data-types-and-filters), [Endpoint DLP Data Types and Filters](/unified/endpoint-dlp-data-types-and-filters), [Email DLP Data Types and Filters](/unified/email-dlp-data-types-and-filters), or [Extranet Data Types and Filters](/unified/extranet-data-types-and-filters). Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values.
- **Top N Results**: From the drop-down menu, choose the number of results that the widget displays. This field populates when you select **User** as the data type.
- **Units:** From the dropdown menu, choose **Transactions** or **Bytes** as the unit of data. The following data units will only appear with certain data types:
- **Samples** are used only with the Secure Browsing Class, Secure Browsing Status, and Secure Browsing Type data types.
- **bps** are used only with Bandwidth by Department, Bandwidth by Location, Bandwidth by Location Groups, Bandwidth by Rule, Bandwidth Class, and Bandwidth Consumption data types.
- If you're creating or editing a report widget and selected **Allow time to be set individually for each widget**, choose a time frame for the widget.
- Select a chart type. To learn more, see **Using Charts in Widgets **in the section above.
- Click** OK** to add your widget.
Editing or Removing Widgets
To edit or delete a widget, hover over the title of the widget and click the **Edit** icon that appears in the right-hand corner.
- To edit a widget, click **Edit Widget** and change its settings. After you complete your changes, click **OK** to apply your changes.
- To delete a widget, click **Remove**. You can't restore a widget after you delete it.
![The Edit Widget and Remove icons for Zscaler widgets](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Edit-Remove-Widget.png)
Moving or Resizing Widgets
To move a widget, click the title of the widget to drag it to its new location. The adjacent widgets automatically move, so the widgets don't overlap when you drag them to their new locations.
To resize a widget, click the icon on the lower right-hand corner of a widget and drag to resize the widget. You can resize widgets within a dashboard, which has a fixed resolution of 1024 x 768. You can resize widgets that contain a table, a bar chart or a line chart. Widgets with pie charts can't be resized. The size options of the widgets are fixed. If you enlarge a widget, the adjacent widget automatically moves to prevent overlapping.
![The Resize icon on a Zscaler widget](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboard-and-reporting-tools/about-widgets/ZIA-6.1-Resize-Widget-Icon.png)