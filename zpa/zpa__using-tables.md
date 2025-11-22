# Using Tables
Source: https://help.zscaler.com/zpa/using-tables
PDF: https://help.zscaler.com/pdf/com/en/1485821.pdf

In the ZPA Admin Portal, data is organized and displayed in tables. You can modify the default settings for each table. Every time you make a change, the settings are stored in your browser's local storage so that your changes are preserved the next time you log in.
If you clear your cache or use a different browser, your settings are lost.
You can do the following:
- [Expand data in the table](#expand)
- [Filter data in the table](#filterData)
- [Hide columns](#hideColumns)
- [Reorder columns](#reorderColumns)
- [Reset table to default settings](#resetTable)
- [Resize columns](#resizeColumns)
- [Sort the column data](#sortColumnData)
[]When you do not need to view all the columns at once, you can hide them so only the columns you want to view are visible.
To hide a column, click the **Table Settings** icon (![Settings Icon ](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-settings-icon.png)
) on the top right of the table and uncheck the column names you want to hide. After you click on the checkbox, the table refreshes and displays only the checked columns.
Two columns must be visible when all other columns are removed. These columns are grayed-out and cannot be hidden. The **Action** column must be visible at all times for the table on the **Backup and Restore** page.
![Table Settings in the ZPA Admin Portal](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-table-settings.png)
[]To reorder columns, click the **Table Settings **icon in the table. When you hover over a listed column name in the **Table Settings **window, a **Move** cursor appears. Adjust the column to the desired position. After you drop the column name, the table refreshes and displays the data in the new column order.
![Reordering columns in the Table Settings](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-table-settings-reorder_0.png)
[]When the data in a column takes up more space than the viewing area allows, it gets clipped.
To increase the column width, hover over the right border of the column. A **Resize** icon (![zpa-resize-column-icon.png](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-resize-column-icon.png)
) appears. Drag and drop to the desired column width.
![Resizing columns in the tables ](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-resizing-table-columns.png)
The first and last columns are fixed and cannot be resized when all other columns are hidden.
[]When you hover over different column headers, you will see that some columns have an **Sort** icon (![zpa-sort-icon.png](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-sort-icon.png)
) next to them. The **Sort** icon indicates that you can sort the data in those columns in ascending or descending order.
To sort a column, click on the **Sort **icon in the table column header.
[]To filter the data in the table, click on a filter (e.g., **Name**, **Created By**), select or enter a selection, and then click **Apply.**
![Filtering in data tables](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-filter.png)
You can also click **Clear** to clear your selections, click **Hide Filters** to hide your filters, click **Reset** to reset the applied filters after applying them, or save applied filters after applying them.
To save your filter preferences:
-
Click the **Menu** icon (![zpa-menu-icon.png](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-menu-icon.png)
), and then click **Save Applied Filter**.
The **Save Applied Filter **window appears.
-
In the **Save Applied Filter **window, enter a name for the applied filter, and then click **Save**.
![Save Applied Filter window](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-save-applied-filter-window.png)
After filters are saved to your preferences, you can toggle between the applied filters by clicking the name of the filter next to **Hide Filters**, or you can delete a saved filter by clicking the **Delete **icon (![zpa-delete-icon.png](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-delete-icon.png)
).
![Selecting predefined filters](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-selecting-predefined-filters.png)
For the applied filters that are saved to your preferences, you can apply additional filters. To save or discard the additional changes made to the applied filters, click the **Menu** icon, and then click **Discard Changes** or **Save Changes**.
![Saving or discarding changes to predefined filters](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-saving-discarding-changes-to-filters2.png)
After you make changes to an applied filter, an **Information **icon (![zpa-information-icon.png](/downloads/zpa/getting-started/admin-portal/using-tables/zpa-information-icon.png)
) appears next to the filter name to indicate unsaved changes. To save changes to the currently selected predefined filter, click the **Menu **icon and then click **Save Changes**.
[]When you make changes to the columns, you can revert back to the default settings. To revert back to the default settings, click the **Table Settings **icon, and then click **Reset**.
This does not reset your sort order.
[]Click the first column within a table to expand it. To expand all of the rows in the table, click **Expand All**. After a row is expanded, additional details are provided.
After a row is expanded, the following additional features are supported:
- [Search by an associated resource](#expandSearch)
- [View or edit a resource](#expandEdit)
The ability to expand rows within a table, in addition to the features found within individual rows, is not supported on every page within the ZPA Admin Portal.
[]Enter the name of the resource in the search bar to search for a specific resource. A minimum of three characters is required when entering text to search for a resource.
[]Click the name of the resource within the expanded row of the table to view or edit the resource. The **View **or **Edit **window appears.
You can only view a resource configured by Zscaler Deception.