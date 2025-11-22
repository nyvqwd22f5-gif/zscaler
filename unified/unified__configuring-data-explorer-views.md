# Configuring Data Explorer Views
Source: https://help.zscaler.com/unified/configuring-data-explorer-views
PDF: https://help.zscaler.com/pdf/com/en/1492671.pdf

Data Explorer provides the flexibility to build and organize your own customized views of applications and metrics to analyze data. To learn more about monitoring Data Explorer views, see [Monitoring Data Explorer Views](/unified/monitoring-data-explorer-views).
Prerequisites
Before configuring a view in Data Explorer, make sure your Digital Experience Monitoring subscription level supports Data Explorer. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
Creating a View
You have the option to create a view from either End User or Hosted Monitoring data. To learn more about Hosted Monitoring, see [Understanding Zscaler Hosted Monitoring](/unified/understanding-zscaler-hosted-monitoring).
To begin creating your view:
- Go to **Analytics **> **Digital Experience Management** > **Reporting **> **Data Explorer**.
-
Click **Create New View.**
[See image.](#create-new-view)
Create a View for End User Monitoring
To create a view for End User Monitoring:
- On the **Untitled View** page, select **End User Monitoring** from the **Data Source** drop-down menu.
- Use the time range filter to narrow the results of your view. Some filters are unavailable if your selected time range is greater than 48 hours. Your time range also determines the granularity of the data displayed in your views:
- If 24 Hours** **or less, data is displayed in 5-minute intervals.
- If greater than 24 Hours but less than (or equal to) 14 Days, data is displayed in 1-hour intervals.
- Structure your view:
- [a. Applications](#view-apps)
- [b. Metrics](#view-metrics)
- [c. Group By](#view-groupby)
- [d. Aggregation Type](#view-aggtype)
- [e. View Type](#view-charttype)
- Apply filters such as **User Groups** to analyze interactions tied to a specific group or **Geolocations **to focus on data based on user locations.
- Click **Run Query** to display your view.
-
The chart format displays individual charts for your selected applications and metrics. For details about the interaction and format of Data Explorer charts, see [Viewing System-Generated Reports](/unified/viewing-system-generated-reports).
[See image.](#chart-format)
-
The tabular format provides the flexibility to filter your selected applications and metrics for an instant view of the data. To capture your configured table information in a CSV file, click **Export**, then click the **Download **icon.
[See image.](#tabular-format)
- Click **Save **to keep your view for future access. To learn more, see [Monitoring Data Explorer Views](/unified/monitoring-data-explorer-views).
- Enter a name for your view in the dialog window, and click **Save **to save your configuration.
The total number of views you can save depends on your Digital Experience Monitoring subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
Create a View for Hosted Monitoring
To create a view for Hosted Monitoring:
- On the **Untitled View** page, select **Hosted Monitoring** from the **Data Source** drop-down menu.
- Use the time range filter to narrow the results of your view. The default time range is 24 hours. Your time range also determines the granularity of the data displayed in your views.
- Use the **Zscaler Hosted Locations** filter to select the Zscaler data centers to run your probes.
- Structure your view:
- [a. Probes](#view-probes)
- [b. Metrics](#hosted-view-metrics)
- [c. Group By](#hosted-view-groupby)
- [d. Aggregation Type](#hosted-view-aggtype)
- [e. View Type](#hosted-view-charttype)
- [f. Overlays](#hosted-overlays-setup)
- Click **Run Query** to display your customized view:
-
The chart format displays individual charts for your selected applications and metrics. For details about the interaction and format of Data Explorer charts, see [Viewing System-Generated Reports](/unified/viewing-system-generated-reports).
[See image.](#hosted-chart-format)
-
The tabular format provides the flexibility to filter your selected applications and metrics for an instant view of the data. Only the top 1,000 rows are displayed. To capture your configured table information in a CSV file, click **Export**, then click the **Download **icon.
[See image.](#hosted-tabular-format)
-
The scatter format displays your selected applications and metrics as dispersed data points.
[See image.](#hosted-scattered-format)
-
The range format displays your selected applications and metrics as dispersed data points across a continuous range of values, helping you analyze distribution patterns.
This format is unavailable when multiple probes or metrics are selected.
[See image.](#hosted-range-format)
-
The multipath visualization format displays Cloud Path visualization data corresponding to the selected timestamp in the chart view. Located under the chart, this format helps you analyze how data traverses different cloud paths for the selected applications and metrics. Use it to gain deeper insight into routing behaviors and path performance at specific moments in time.
- This view is unavailable if you select multiple probes.
- You can select a time range only between 2 hours and 7 days.
- This view is unavailable if you select multiple probes.
- You cannot choose an option from the **Group By** drop-down menu; Zscaler Hosted Locations is set by default.
- You cannot change the selection under **Metrics**; latency metrics are selected by default.
- By default, the Cloud Path visualization shows data from the last 24 hours.
[See image.](#hosted-multipath-format)
- Click **Save **to keep your view for future access. To learn more, see [Monitoring Data Explorer Views](/unified/monitoring-data-explorer-views).
- Enter a name for your view in the dialog window, and click **Save **to save your configuration.
The total number of views you can save depends on your Digital Experience Monitoring subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations).
Editing a View
Only the Digital Experience Monitoring Super Admin or the admin who created the view can edit a configured Data Explorer view.
To edit a Data Explorer view:
- Go to **Analytics **> **Digital Experience Management** > **Reporting **> **Data Explorer**.
- Search for the view you want to edit in the Data Explorer table.
- Click the **Edit **icon for the view.
- After you've finished editing, click **Run Query** to display your edited view.
- Click **Update**.
- Activate your changes.
Deleting a View
Only the Digital Experience Monitoring Super Admin or the admin who created the view can delete a configured Data Explorer view.
To delete a Data Explorer view:
- Go to **Analytics **> **Digital Experience Management** > **Reporting **> **Data Explorer**.
- Search for the view you want to delete in the Data Explorer table.
- Click the **Delete **icon for the view.
- In the dialog window, confirm you want to delete the view.
- Activate your change.
[]![Button to Create New View](/downloads/zdx/configuration/configuring-data-explorer-views/zdx-de-create-new-view3.png)
[]![Chart view](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-chart-format.png)
[]![Scatter View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-scatter_0.png)
[]![Chart View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-chart_0.png)
[]![Range View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-range_0.png)
[]![Multipath View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-multipath_0.png)
[]Click **Add **to specify the applications for your view:
- If you select a United Communications as a Service (UCaaS) application, you can add other UCaaS applications for your view.
- If you select a non-UCaaS application, you can add other non-UCaaS applications for your view.
The applications you select determine the particular metrics that are available. The number of applications you can add depends on your Digital Experience Monitoring subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
![Add applications to your view](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-add-applications.png)
[]Click **Add **to specify the probes for your view. You can add up to 10 probes for Hosted Monitoring.
![Add probes to your view](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-probe-selection_0.png)
[]Click **Add **to specify the metrics for your view. The number of metrics you can add depends on your Digital Experience Monitoring subscription level. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#analytics).
After selecting your metrics, you can apply Metric-Based filters to refine the dataset being displayed in your view. These filters allow you to specify conditions or thresholds based on the metrics you've chosen.
![Adding Metrics to your view](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-add-metrics-updated.png)
[]Click **Add **to specify the metrics for your view. You can add up to 10 metrics for Hosted Monitoring.
If a Web probe is configured with a Cloud Path probe as a companion probe, **Page Fetch Time** and **End-to-End Latency** metrics are automatically selected by default.
![Adding metrics to your hosted monitoring view ](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-metrics-addfunctionality_0.png)
[]Select an option to group data by **Zscaler Locations**, **Geolocations**, **Departments**, **Applications, Last Mile ISPs, or Zscaler Data Center**. If you group by Applications, views are rendered for each metric. If you group by other options in the drop-down menu, views are rendered for each application and metric.
If you've selected more than one application for your view, your **Group By** option is limited to **Applications**.
![Select how to group data](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-group-by3.png)
[]Select the option to group data by** Probes **or **Zscaler Hosted Locations**.
If you've selected more than one metric for your view in chart format, your **Group By** option is limited to **Probes**.
![Select how to group data](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-groupby-probes_0.png)
[]Select the **Average**, **Minimum**, or **Maximum **method for data aggregation across all users. The default setting is Average.
![Select Aggregation Type](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-agg-type3.png)
[]Select the **Average**, **Minimum**, or **Maximum **method for data aggregation across all users. The default setting is Average.
![Select Aggregation Type](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-aggregationtype-selectionmenu_0.png)
[]Select a **View Type** icon to display views in a chart format or tabular format.
![Select View Type options](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-viewtypes-chart.png)
[]Select the **View Type** icon to display your view in a chart, tabular, scatter, range, or multipath visualization format.
![Hosted View Chart View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-selection-UI_0.png)
[]![Hosted View Tabular View](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-viewtype-tabular_101025.png)
[]![Tabular view](/downloads/zdx/configuration/configuring-data-explorer-views/endusermonitoring-tabular-format.png)
[]Select a **Percentile Threshold**, such as the 99th (P99) or 95th (P95) percentile, to display statistical measures that highlight worst-case and typical performance scenarios. The** Show Errors** toggle, enabled by default, displays red markers on charts to indicate probe errors. You can click these markers within the chart to view detailed information about the error, including the timestamp, error type, and relevant metrics.
![Data Explorer view showing the Overlays section configured with the P99 percentile threshold and 'Show Errors' enabled, alongside a line chart displaying average end-to-end latency for selected probes.](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-monitoring-overlays-ui-p99_0.png)
![Line chart showing average page fetch time with HTTP error markers displayed in red for specific timestamps. Includes a tooltip with percentile metrics and error details.](/downloads/zdx/configuration/configuring-data-explorer-views/hosted-overlays-ErrorOverlayWithInformationDisplay_0.png)