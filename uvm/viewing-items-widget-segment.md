# Viewing Items in a Widget Segment
Source: https://help.zscaler.com/uvm/viewing-items-widget-segment
PDF: https://help.zscaler.com/pdf/com/en/1529159.pdf

You can view detailed data associated with a specific segment in a widget (e.g., a slice of a pie chart, or a bar in a bar chart) by clicking the segment. Viewing a segment's items opens a table view that displays the data for the selected segment.
Viewing items is distinct from widget drilldown, which enables users to explore additional dimensions set in the widget configuration. Viewing items displays the underlying data for a specific segment of a widget, while drilling down displays additional dimensions that are configured in the drilldown hierarchy. For example, a drilldown on open tickets can further break down the data by severity or ticket status.
Clicking a segment of a widget displays the items that make up that segment. For example, in a pie chart showing open tickets by asset type, clicking the Linux segment opens a table listing all tickets assigned to Linux.
[See image.](#linux-segment)
If you configure drilldown in the widget when [adding widgets to the dashboard](/uvm/configuring-custom-dashboards#adding-widgets-to-dashboards), an Interactions menu appears, allowing you to either click through to a table detailing the individual items that make up the measurement's value or to drill down into additional dimensions.
Customizing the View Items Table
When you click a segment to view its items, the columns displayed in the table that appears are those defined in the entity's default saved view in the relevant app (e.g., [Tickets](/uvm/about-tickets) in UVM, [Violation Tickets](/uvm/about-violation-tickets) in AEM).
To temporarily modify the displayed columns, click the Settings icon in the top-right corner of the table. You can add or remove columns for the current session. These changes are not saved to the widget and only apply while viewing the table.
By default, the table displays data based on the account's default saved view for the relevant entity (e.g., Ticket or Asset). The default view is indicated by the Set as Account Default View icon in the saved view's drop-down menu on the entity's page. If you need to permanently adjust the displayed columns, you can update the default saved view for the relevant entity. To learn more, see [Creating & Managing Saved Views](/uvm/creating-managing-saved-views).
[See image.](#displayed-segment-fields)
[]![mceclip5.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/mceclip5.png)
[]![set%20as%20account%20default%20view%20icon.png](/downloads/uvm/analytics/dashboards/viewing-items-widget-segment/set%20as%20account%20default%20view%20icon.png)
Exporting the Table
To export the data shown in the table as a CSV file, click the Export as CSV icon located in the top-right corner of the table.
[See image.](#export-as-csv-icon)
The data is exported based on the currently displayed columns.
[]![mceclip8.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/mceclip8.png)