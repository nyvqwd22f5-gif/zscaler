# Building Queries and Searching Logs
Source: https://help.zscaler.com/uvm/building-queries-searching-logs
PDF: https://help.zscaler.com/pdf/com/en/1527836.pdf

You can search logs to view data collected by the Zscaler Security Operations (SecOps) platform before it's processed and analyzed. This helps you to understand the raw data that's pulled from connected sources and subsequently pushed into the data model. You can search logs by building and using queries.
Building a Query
To create a query using the basic query builder:
-
In the SecOps platform, go to **Explore > Logs**.
![Build a basic query to search the logs](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-logs-1.png)
If you have not previously created a query, you can select from a list of prebuilt queries to get started. You can also select a saved query from the Queries Library.
[See image.](#ds-img)
- Click the **+** icon to add a new query.
A new query tab appears.
- Click the **Search Logs** box to open the query builder.
![Build a query](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-search-log.png)
- Select a field or enter a field name manually.
- Select an operator (e.g., **Equals**, **Contains**, **Starts With**, etc.).
- Enter or select the value you want to filter by.
- (Optional) Use **AND** or **OR** operators to add conditions to the query.
- (Optional) Click **Save **to save your query.
- Click **Search**.
Log data appears.
-
Use the time filter to filter results to a specific time frame. To learn more, see [Using Filters](/uvm/using-filters).
The selected time frame is not saved as part of the query, and must be configured for every result.
Click **Export as CSV** at the top right of the logs table to export the data as a CSV file.
[See image.](#uvm-csv)
[]
![Select a prebuilt query to search for the logs](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-pre-built-queries.png)
[]
![Export logs as CSV](/downloads/uvm/explore/logs/logs-search/mceclip8.png)
To create an advanced query, you can use QL syntax in the advanced query editor. Click **Advanced **and enter values as necessary.
![Build an advanced query](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-adavanced.png)
The basic query builder and the advanced query editor are completely independent, even when they are within the same query. If you make changes to one, the other remains unchanged.
Adding a Query to the Queries Library
You can save queries and add them to the Queries Library for quick access.
To add a query to the Queries Library:
-
Click **Save **at the top right of the page.
![Save the created query](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-save-query.png)
The **Edit Detail** page appears.
- Enter a name for the query.
- Click **Save**.
The query is saved to the library.
![View all the saved queries](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-queries-library.png)
Use the **Save As New** option to save a modified version of the current query to your library.
![Save a modified version of the query to the library](/downloads/uvm/explore/logs/logs-search/mceclip20.png)
Click **Library** to access your saved queries.
![Click Library to access saved queries](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-library.png)
Searching Logs
After you configure and run your query, a Logs table appears. Click a log in the table to open its drawer. You can search within the log using the search field, and copy the log using the Copy icon in the top-right corner of the drawer.
![Search for the logs](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-logs-table.png)
Hover over a field in the drawer to display the following icons:
- **Breakdown By Field**: Use the selected field as the breakdown by field in the pie chart pane.
- **Exclude**: Add a Not Equal filter to the query builder to return all logs for which the field's value is different from the value of the current log.
- **Add to Search**: Add a filter to the basic query builder to return all logs for which the field's value is equal to the value in the current log.
- **Add/Remove Column**: Add or remove a column in the log table.
- **Copy Value**: Copy the value of the field.
Analyzing the Data
You can filter and analyze the retrieved log data using the Time Series chart or a pie chart.
Time Series Chart
The Time Series chart shows the number of logs (on the y-axis) that match the query conditions, retrieved from your sources within the time frame selected in the time filter.
![Number of logs that match the query conditions on the Time Series chart](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-time-series.png)
You can click and drag the time filter to select a portion of the chart to define your desired time frame. This updates the table view as shown in the following image.
![Click and drag the time filter to view an updated view based on the desired time frame](/downloads/uvm/explore/logs/logs-search/mceclip25.png)
The selected time filter is not saved as part of the query, and must be configured each time.
Pie Chart
The pie chart displays all logs filtered by your query. Use the** Breakdown by** drop-down menu to select the field you want the logs to be grouped in, and the number of top values you want to be presented in the legend.
![Logs filtered by the query displayed on the Pie Chart](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-pie-chart.png)
Select any number of slices to filter by their value. This also adds your selection as a filter in the table of logs.
![Filter the pie chart by the selected value](/downloads/uvm/explore/logs/logs-search/mceclip27.png)
To remove a value from the filter created by the pie chart, deselect the slice on the chart itself or click the remove slicer** **icon under the chart.
![Deselect a slice using the Remove Slicer icon in the Pie Chart](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/doc-57696-searching-logs/uvm-slicer.png)