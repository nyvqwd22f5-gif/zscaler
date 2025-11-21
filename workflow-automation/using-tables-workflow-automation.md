# Using Tables in Workflow Automation
Source: https://help.zscaler.com/workflow-automation/using-tables-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1467561.pdf

In the Workflow Automation Admin Portal, incidents are organized and displayed in a table on the Incidents page. You can modify the settings for the table.
You can do the following:
- [Reorder Columns](#reorder)
- [Resize Columns](#resize)
- [Hide Columns](#hide)
- [Sort the Column Data](#sort)
- [Configure the Number of Table Rows](#Configure-Number-of-Rows)
[]To reorder columns:
- Click the **Table Options** icon on the table. The **Table Options** dialog appears.
![Viewing the Table Options dialog on the Incidents page. The Table Options dialog contains tabs where you can select Columns or Rows for the table. The Columns tab displays a list of selected column names, such as Transaction ID, Last Change Date, Priority, and Severity.](/downloads/workflow-automation/getting-started/admin-portal/using-tables-workflow-automation/WA-Tables-Reorder-Table-Columns.png)
- In the **Table Options** dialog, select a listed column name, then drag and drop the column to the desired position. After you drop the column name, the table refreshes and displays the data in the new column order. In addition, these table settings are saved on the server, allowing them to persist across different devices and browsers.
[]When the data in a column takes up more space than the viewing area allows, only some of it is visible. You can increase the column width.
To resize the column width:
- Hover over the right border of the column on the table. A **Resize** icon appears.
- Drag and drop to the desired column width.
![Resizing a table column on the Incidents page](/downloads/workflow-automation/getting-started/admin-portal/using-tables-workflow-automation/WA-Tables-Resize-Table-Columns_0.png)
[]When you do not need to view all the columns simultaneously, you can hide them so only the columns you want to view are visible.
To hide columns:
- Click the **Table Options** icon on the table. The **Table Options** dialog appears.
- Deselect the column names you wish to hide. After you select each checkbox, the table refreshes and displays only the checked columns. In addition, these table settings are saved on the server, allowing them to persist across different devices and browsers.
![Table Options dialog displaying a few column checkboxes selected on the Columns tab](/downloads/workflow-automation/getting-started/admin-portal/using-tables-workflow-automation/WA-Tables-Hide-Table-Columns.png)
[]Some of the column headers have a **Sort** icon next to them. These icons indicate that you can sort the data in those columns. You can sort data in ascending or descending order. By default, the incidents are displayed in the table in descending order by incident date.
When the system sorts the data, the results are arranged based on standard alphabetical and numerical conventions. This ensures that sorting is predictable and follows established conventions for organizing data. For example, if you sort the File Name field in ascending order, numbers appear before letters, and words starting with uppercase letters (e.g., "Alert") come before those starting with lowercase letters (e.g., "incident"). In descending order, the reverse applies. Lowercase words appear before uppercase words, and letters come before numbers. For instance, sorting the values ["3", "Alert", "incident", "2"] in ascending order, displays ["2", "3", "Alert", "incident"]. While sorting in descending order, displays ["incident", "Alert", "3", "2"].
To sort a column's data for all the incidents in the table across all the pages, click the **Sort** icon in the table column header. You can only sort one column at a time. For example, if you sort by the DLP Admin column, all the pages are sorted by that column. If you next sort by the Source DLP Type column, the sorting for DLP Admin goes away and all the pages are sorted by the Source DLP Type.
These sort settings are saved in local storage, allowing them to persist within the same browser, but they won't carry over to different devices and browsers. They are saved for each user. If you have multiple users sharing the same browser, then each user's settings are stored separately. In addition, these sort settings stay with the users even if they refresh the page or if they log out of the Workflow Automation Admin Portal and log back in again.
![Sorting the table columns on the Incidents page. The Incidents page is displayed with the Sort icons highlighted in the heading for the Severity, DLP Admin, Source DLP Type, and DLP Type columns.](/downloads/workflow-automation/getting-started/admin-portal/using-tables-workflow-automation/WA-Tables-Sort-Table-Columns_0.png)
[]You can configure the number of rows that appear in the table.
To configure the number of table rows:
- Click the **Table Options** icon on the table. The **Table Options** dialog appears.
- Click the **Rows** tab.
![Table Options dialog displaying radio buttons for the different number of row selections (10 Rows, 20 Rows, 25 Rows, 50 Rows, and 100 rows) on the Rows tab](/downloads/workflow-automation/getting-started/admin-portal/using-tables-workflow-automation/WA-Tables-Configure-Rows.png)
- Select the number of rows to display on the page. Options are **10 rows**, **20 rows**, **25 rows**, **50 rows**, and **100 rows**. After you select the option, the page refreshes, displaying that number of rows. In addition, this table setting is saved on the server, allowing it to persist across different devices and browsers.