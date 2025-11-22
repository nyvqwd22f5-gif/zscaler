# Analyzing Traffic Using Insights
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-traffic-using-insights
PDF: https://help.zscaler.com/pdf/com/en/1420666.pdf

In the** Analytics **>** Insights** window, you can interactively drill down to specific transactions. To learn more about the Insights pages, see [About Insights](/cloud-branch-connector/about-insights).
Insights Walkthrough
The following Tunnel Insights instance is used to walk you through how to use the Insights pages. It shows a trend chart for the data type **Overall Traffic**. The chart shows you the overall traffic for the current day in terms of transactions.
![Cloud & Branch Connector Tunnel Insights page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/insights/analyzing-traffic-using-insights/Tunnel%20Insights%20page.jpg)
Using Insights
On the Insights pages, you can:
- [Define Settings](#defining)
- [Interactively Drill Down](#drilldown)
- [Start a New Analysis](#new)
- [Save Your Analysis](#save)
[]At any time, you can change the options to display your preferred metrics. For example, the timeframe and chart type are customizable. The following image shows a customized timeframe and the pie chart type has been selected. Even though these two options have been changed, you are still viewing **Overall Traffic **with custom dates selected.
![Cloud & Branch Tunnel Insights page pie chart in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/insights/analyzing-traffic-using-insights/Cloud%20%26%20Branch%20Connector%20Tunnel%20Insights%20Pie%20Chart.jpg)
Other data type options include **Location**, **Tunnel Destination IP**, and **Tunnel Source IP**. The chart changes to reflect the data type selected. As you edit the chart, your workflow is recorded in the history bar located under the chart.
[]There are several ways to interactively drill down and receive granular data. All data types have their own set of filters, located on the left-side navigation. Under **Select Filters**, select **Location** to filter accordingly.
![Zscaler Cloud & Branch Connector Tunnel Insights with Location data type in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/insights/analyzing-traffic-using-insights/Tunnel%20Insights%20Location%20Filtering.jpg)
You can also view the logs page for the selected data type. To view logs, apply filters from the left-side navigation. To learn more about the Logs pages, see [About Insights Logs](/cloud-branch-connector/about-insights-logs).
![Cloud & Branch Connector Tunnel Logs page with Location data type filter applied in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/insights/analyzing-traffic-using-insights/Tunnel%20Logs%20Filters.jpg)
[]To start a new analysis or change the focus of your investigation:
- Click **Start Over** to return to the default chart. The data type menu above the chart is set to **Overall Traffic**, filters are reset, and all charts, except the default, are deleted from the history bar.
- Choose a different data type from the **Overall Traffic** drop-down menu. This automatically resets the filters.
[]As you work with your data, the tool records the workflow in the history bar under the chart. Every time you make a change to the chart, such as add a filter or change the chart type, the Zscaler Cloud & Branch Connector Admin Portal adds the previous version to the history bar. You can then click any chart in the history bar to see it again. If you view an earlier version and change it, all subsequent versions are automatically deleted. This enables an administrator to review the various stages of the investigation and change direction for the analysis upon review, if necessary. The history bar can retain up to 50 versions of the chart. If there are more than 50 versions, the portal deletes the oldest versions as new ones are added. The chart icons are numbered, so you can track how many versions you have.
You can do the following:
- Delete charts from your workflow.
- Click **Print View** to print the entire sequence of charts in the history bar.