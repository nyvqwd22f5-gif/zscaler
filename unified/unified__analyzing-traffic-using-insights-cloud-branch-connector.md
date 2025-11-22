# Analyzing Traffic Using Insights for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/analyzing-traffic-using-insights-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1516856.pdf

In the** Logs** > **Insights** > **Branch & Cloud Connectors** window, you can interactively drill down to specific transactions. To learn more about the Insights pages, see [About Insights](/unified/about-insights-0).
Insights Walkthrough
The following Tunnel Insights instance is used to walk you through how to use the Insights pages. It shows a trend chart for the data type **Overall Traffic**. The chart shows you the overall traffic for the current day in terms of transactions.
Using Insights
On the Insights pages, you can:
- [Define Settings](#defining)
- [Interactively Drill Down](#drilldown)
- [Start a New Analysis](#new)
- [Save Your Analysis](#save)
[]At any time, you can change the options to display your preferred metrics. For example, the timeframe and chart type are customizable. The following image shows a customized timeframe and the pie chart type has been selected. Even though these two options have been changed, you are still viewing **Overall Traffic **with custom dates selected.
Other data type options include **Location**, **Tunnel Destination IP**, and **Tunnel Source IP**. The chart changes to reflect the data type selected. As you edit the chart, your workflow is recorded in the history bar located under the chart.
[]There are several ways to interactively drill down and receive granular data. All data types have their own set of filters, located on the left-side navigation. Under **Select Filters**, select **Location** to filter accordingly.
You can also view the logs page for the selected data type. To view logs, apply filters from the left-side navigation. To learn more about the Logs pages, see [About Insights Logs](/unified/about-insights-logs-0).
[]To start a new analysis or change the focus of your investigation:
- Click **Start Over** to return to the default chart. The data type menu above the chart is set to **Overall Traffic**, filters are reset, and all charts, except the default, are deleted from the history bar.
- Choose a different data type from the **Overall Traffic** drop-down menu. This automatically resets the filters.
[]As you work with your data, the tool records the workflow in the history bar under the chart. Every time you make a change to the chart, such as add a filter or change the chart type, the Zscaler Cloud & Branch Connector Admin Portal adds the previous version to the history bar. You can then click any chart in the history bar to see it again. If you view an earlier version and change it, all subsequent versions are automatically deleted. This enables an administrator to review the various stages of the investigation and change direction for the analysis upon review, if necessary. The history bar can retain up to 50 versions of the chart. If there are more than 50 versions, the portal deletes the oldest versions as new ones are added. The chart icons are numbered, so you can track how many versions you have.
You can do the following:
- Delete charts from your workflow.
- Click **Print View** to print the entire sequence of charts in the history bar.