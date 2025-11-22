# Using Filters
Source: https://help.zscaler.com/uvm/using-filters
PDF: https://help.zscaler.com/pdf/com/en/1528106.pdf

You can use filters to adjust and refine the data displayed in views across the platform, from dashboards and reports to operational views (e.g., Tickets, Assets). By applying filters, you can focus on specific information relevant to your current task, such as reviewing vulnerabilities on a particular asset, addressing critical policy violations, or identifying high-priority tickets discovered in the last week. This helps security teams efficiently prioritize their workload and focus on the most critical risks in their environment.
Filters are applied using available fields, including measurements (e.g., counts, averages) and dimensions (e.g., Status or Severity categories). The specific fields available for filtering depend on where you are in the platform. For example, dashboards with data from multiple entities support filtering by dimensions but not measurements, while operational views typically allow filtering by both. To learn more, see [Understanding Measurements & Dimensions](/uvm/understanding-measurements-dimensions).
Adding Filters
Different fields have filtering options that vary according to the field type (e.g., Boolean, Text, Number, Date, IP) and whether it can contain multiple values (i.e., repeated fields).
To add a filter:
-
At the top of the page, click **Add Filters** (if no filters are active) or **More **(if filters are already applied) to open the list of available fields for filtering in the current page.
[See image.](#tickets-more-filters-dialog-open)
- Search for and select the field you want to filter by. Selecting a field adds it to the list of filters.
-
Select the checkbox for the field you want to filter by.
The field's filter dialog window appears.
- In the field's filter dialog window, set the values you want to filter the field by:
- [List](#filter-list)
- [Date Selector](#filter-date-picker)
- [Condition](#filter-conditions)
Applying filters adjusts the displayed data to what is included in the filter's scope. This resets when you leave the page. Your applied filters can be saved as a set view. To learn more, see [Creating & Managing Saved Views](/uvm/creating-managing-saved-views).
Filtering Repeated Fields
Repeated fields are fields that can store multiple values, such as the Asset or the Ticket Sources field. Filters applied to these fields allow you to focus on your data by including or excluding records based on one or more of the field's values.
Repeated Fields in List Filters
When filtering repeated fields from the list of the field's values, selecting one or more values returns records containing at least one of the selected values.
[See image.](#list-repeated-fields-asset-sources)
For example, to view assets retrieved from specific sources, such as Qualys Vulns and ServiceNow Assets, select these values from the field filter drop-down menu. This returns assets that include either of these as a source, and not necessarily both. To exclude assets retrieved exclusively from a specific source (e.g., ServiceNow Assets), select all other values except the one you want to exclude. This excludes assets that list ServiceNow Assets as their only source, and includes assets that contain at least one of the selected sources (e.g., Qualys Vulns).
Filtering repeated fields using the list of values functions similarly to the `Equals (Any)` operator in conditional filtering, checking the filter against any of the field's values.
Repeated Fields in Conditional Filters
For more granular filtering, you can configure conditional filters on repeated fields to define specific rules for their values. When configuring conditional filters for these fields, you can specify whether the filter should be checked against any or against all the field's values.
- [All Operator](#operator-all)
- [Any Operator](#operator-any)
The `Is Empty` and `Is Not Empty` operators are Boolean filters and do not have All or Any variations. These operators check whether a repeated field contains any values (i.e., `Is Not Empty`) or has no values at all (i.e., `Is Empty`). Unlike other conditional operators on repeated fields that evaluate individual values within the field, these operators apply to the field as a whole, making the distinction between All and Any unnecessary.
Managing Filters
Filters can be adjusted, cleared, or reset as needed. When managing filters, you can perform the following actions:
- To clear the values from an applied filter field without removing the field itself, click the field in the filters bar and click **Clear Selection**.
- To remove a field from the filters bar, open the **More **drop-down menu and deselect the field from the list of active filters.
- To reset the filters, click **Clear All Filters**. This removes all active filters and displays all available data.
[]For fields with a set list of values (e.g., **Status **or **Severity**, or Boolean fields), select one or more options in the filter dialog window. For example, select **Opened** or **In Progress **for the **Status **filter to focus on active tickets. Use the search bar to locate values in long lists.
[See image.](#filters-list-status-dialog)
Multiple selections apply a logical OR (e.g., selecting **Opened** and **In Progress **shows items matching either value). If no values are selected, the filter will show all data for that field.
[]![tickets more filters dialog open](/downloads/uvm/getting-started/admin-portal/using-filters/tickets%20more%20filters%20dialog%20open.png)
[]![filters list status field](/downloads/uvm/getting-started/admin-portal/using-filters/filters%20list%20status%20field.png)
[]You can define time ranges or conditions in the date selector window to filter data. For example, you can filter records to display only upcoming deadlines within the next month, or identify entries that lack assigned dates.
[See image.](#filters-date-picker-dialog)
Date filters can be configured using the following methods:
- **Date Range**: Choose a method to filter records based on specific timeframes.
- **Preconfigured**: Select a preset option on the left to filter records based on common timeframes (e.g., **Last 7 Days**, **Next 14 Days**).
- **Custom**: Define a range to include only records within specific timeframes.
- **Fixed Date Range**: Select a fixed start and end date using the calendar display, or manually enter dates in the date field at the bottom left of the filter dialog window.
- **Dynamic Date Range**: Define relative timeframes that automatically update based on the current date (e.g., **Last 7 Days** or **Next 1 Month**).
- Select a timeframe from the drop-down menu:
-
**Next**: Displays records from today forward (e.g., **Next 1 Month **includes today + 31 days; **Next 1 Day **includes today + 1 day). This timeframe is often used for SLA and due-date fields.
**Next **is not available for historical data.
- **Last**: Displays records from the start of the current time unit (calendar Month, Week, Day) to today (e.g., **Last 1 Month **includes the 1st of the current month to today, including today; **Last 1 Day **includes today).
- **Previous**: Displays records from the full previous time unit (calendar Month, Week, Day), not including the current time unit (e.g., **Previous 1 Month **in July includes the entire month of June; **Previous 1 Day **includes yesterday).
- **Before**: Displays all records up to and including the selected date (the default selected date is today).
- Enter a value for the time unit.
-
Select a time unit (i.e., **Day**, **Week**, **Months**) from the drop-down menu to define how the range is calculated.
Weekly filters follow a Monday-to-Sunday format.
- **Is Empty**: Display records with no date assigned (e.g., records missing SLA deadlines).
- **Is Not Empty**: Display records with a date assigned.
[]![filters date picker](/downloads/uvm/getting-started/admin-portal/using-filters/filters%20date%20picker.png)
[]Use conditional filters to apply rules that filter your data based on field values. Conditional filters are available depending on the field and the view you're filtering in, and are not available for Boolean and Date fields. You can combine multiple conditions using AND or OR to create compound filtering rules for more granular control.
[See image.](#filters-condition-dialog)
To apply conditional filters:
- In the filter dialog window of the field you are filtering by, select **Condition**.
- Configure the filter conditions:
- Select an operator (e.g., **Equals**, **>**). Available operators vary depending on the field type (i.e., Text, Number).
- Enter the value that the rule should apply to. Filter conditions are case sensitive.
- (Optional) Use **AND**/**OR **logic to define compound rules:
- **AND **includes records only if they meet all conditions in the rule.
- **OR **includes records if they meet any conditions in the rule.
- Click **Apply**.
The following examples show conditional filters:
- Ticket Severity Score: Filter tickets based on their severity score to focus on high-risk issues. For example, to view tickets with a severity score between 7 and 10, add the Ticket Severity Score field to the filters, and configure the conditional filter `>= 7`.
- Asset Type: Filter assets by type to focus on related data and streamline your analysis. For example, to exclude Container assets, add the Asset Type to the filters, and configure the conditional filter `Not Equals Container`. This helps you concentrate on non-containerized assets, such as virtual machines or databases, when assessing infrastructure-level risks or vulnerabilities.
[]![filters conditions](/downloads/uvm/getting-started/admin-portal/using-filters/filters%20conditions.png)
[]![filters list repeated fields asset sources](/downloads/uvm/getting-started/admin-portal/using-filters/filters%20list%20repeated%20field%20asset%20sources.png)
[]The All operator returns records only if all the values in the field meet the filter condition.
Examples:
- To include assets retrieved exclusively from the sources Qualys Assets and Wiz Assets, use the `Equals (All)` operator (i.e., `Asset Sources Equals (All) Qualys Assets AND Wiz Assets`). This displays assets where all listed sources are Qualys Assets and Wiz Assets, excluding any records with additional sources (e.g., ServiceNow Assets).
- To exclude all assets retrieved from the ServiceNow Assets source, even if they were retrieved by other sources, use the `Not Equals (All)` operator (i.e., `Asset Sources Not Equals (All) ServiceNow Assets`). This excludes all assets retrieved from ServiceNow Assets, even those retrieved by additional sources (e.g., an asset retrieved by ServiceNow Assets and Qualys Assets is excluded).
[]The Any operator returns records if at least one (i.e., any) value in the field meets the filter condition.
Examples:
- To view all assets retrieved from ServiceNow Assets, even if they were retrieved by additional sources, use the `Equals (Any)` operator (i.e., `Asset Sources Equals (Any) ServiceNow Assets`). Assets retrieved from ServiceNow Assets are retrieved, including those retrieved by other sources (e.g., an asset retrieved by ServiceNow Assets and Qualys Assets is included).
- To exclude records retrieved only from ServiceNow Assets (and no other sources), use the `Not Equals (Any)` operator (i.e., `Asset Sources Not Equals (Any) ServiceNow Assets`). Assets retrieved from ServiceNow Assets but also from other sources are not excluded (e.g., an asset retrieved by ServiceNow Assets and Qualys Assets is not excluded).