# Configuring Custom Dashboards
Source: https://help.zscaler.com/uvm/configuring-custom-dashboards
PDF: https://help.zscaler.com/pdf/com/en/1527896.pdf

Custom dashboards allow you to organize and display relevant data in a way that is meaningful to your organization. While the platform comes equipped with built-in dashboards that provide powerful and ready-to-use insights, custom dashboards give you the flexibility to tailor your view, selecting specific measurements and dimensions that matter most to you. This article provides step-by-step instructions on how to create and configure custom dashboards. . For details on how to manage existing dashboards, see [Managing Custom Dashboards](/uvm/managing-custom-dashbords).
Creating a Custom Dashboard
You can create a custom dashboard from scratch or start with a preconfigured template.
To use a template, go to **Explore** > **Dashboards** > **Template Gallery**, where you can browse and select from a variety of dashboard templates.
To create a custom dashboard:
-
Go to **Explore** > **Dashboards**.
A list of the private and public dashboards that you have access to appears.
[See image.](#explore-dashboards)
-
Click **New**.
The **Create New Dashboard** window appears.
-
In the **Create New Dashboard** window:
- **Name**: Enter a unique name for the dashboard.
- **Description**: (Optional) Enter a short description of the dashboard’s purpose.
-
**Viewers**: Set the dashboard's viewer access.
- **Public**: Select this option to grant view access to all users in the account.
- **Selected Users**: Select users from the list to set them as viewers of the dashboard.
To set the dashboard as private and only visible to you, leave the **Viewers** drop-down menu blank.
-
**Editors**: Set the dashboard's editor access.
- **Public**: Select this option to grant edit access to all users in the account.
- **Selected Users:** Select users from the list to set them as editors of the dashboard. Users designated as editors override the **Viewers** setting.
To set the dashboard as private and editable only by you, leave the **Editors** drop-down menu blank.
- **Pin to Apps**: (Optional) Select the application to which you want to pin the dashboard. This allows you to easily find the dashboard under **My Dashboards** on the app.
[See image.](#create-new-dashboard-form)
-
Click **Create**.
The **Create New Widget** page appears, and you can start adding widgets to visualize your data.
[]![explore%20dashboards.png](/downloads/uvm/explore/dashboards/configuring-custom-dashboards/explore%20dashboards.png)
[]![mceclip2.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/mceclip2.png)
Adding Widgets to Dashboards
Each custom dashboard is made up of dynamic widgets that you can drag and drop into a layout that fits your needs. Widgets can be configured to display the measurements and dimensions most relevant to you. As you configure a widget, a live preview appears to the right of the settings panel, allowing you to track and review changes in real time.
To configure widgets in a dashboard:
- Click the **Edit **icon for an existing dashboard.
-
Click the **Edit Dashboard **icon at the top of the page, and then click **Widget**.
[See image.](#edit-dashboard-new-widget)
The **Create New Widget **window appears.
- . In the **Create New Widget **window:
-
Select a widget type in the left pane (e.g., **Bar**, **Line**, **Pie**).
The widget type affects the number of measurements and dimensions you can add to the widget.
- In the right pane, replace **Widget Title (Optional) **with a custom title.
-
On the **Filters** tab, select a **Timeframe** option:
- **Current**: Shows the current data. This is the default setting.
- **Historical**: Select to track over-time behavior in your organization. Specify the desired date range.
[See image.](#current-historical)
- Customize the widget's displayed data, filters, style, and interactivity.
- [Configure the data displayed in the widget.](#data-tab)
- [(Optional) Apply filters to the widget.](#filters-tab)
- [(Optional) Set the widget style.](#style-tab)
- [(Optional) Configure the widget drilldown.](#configuring-interactions)
- (Optional) Enable **Table View **to display the data in a table format.
- Click **Save** on the bottom right of the widget to save your widget.
- Click **Save** on the top right of the dashboard to add the widget to the dashboard.
You can repeat this process to add as many widgets as needed.
[]![edit dashboard new widget](/downloads/uvm/analytics/dashboards/configuring-custom-dashboards/edit%20dashboard%20new%20widget.png)
[]![mceclip1.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/mceclip1.png)
[]On the **Data** tab:
- Select the **Main Entity** type. Measurements and dimensions are dynamically displayed based on the selected entity type.
-
Add measurements and dimensions to the widget. To learn more, see [Understanding Measurements & Dimensions](/uvm/understanding-measurements-dimensions).
- Click the **Measurements **icon to view the list of available measurements.
- Click the **Dimensions **icon to view the list of available dimensions.
[See image.](#measurements-dimensions-lists)
The selected measurements and dimensions appear in the left pane, where you can rearrange them by dragging them to the desired position.
[See image.](#rearrange-dims-measures)
[]![measurements and dimensions lists icons](/downloads/uvm/analytics/dashboards/configuring-custom-dashboards/measurements%20dimensions%20lists.png)
[]![total%20tickets%20by%20ticket%20severity.png](/downloads/uvm/analytics/dashboards/configuring-custom-dashboards/total%20tickets%20by%20ticket%20severity.png)
[]On the **Filters** tab, customize and refine the data displayed and the way in which it's displayed, including date filtering, sorting and ordering, limiting the display to top results, and applying specific filter conditions.
- [Date](#filtering-date)
- [Sort & Top](#sort-and-top)
- [Conditions Filters](#conditions-filters)
[]When creating historical widgets, you can set date filters for the timeframe and granularity that your widget should display.
-
On the **Filters **tab, select **Historical** for the **Timeframe** setting.
Switching to the historical data type might remove some of the selected measurements or dimensions that are not supported in historical mode.
- In the **Date Range** drop-down menu, select the range of the data that the widget should display. You can choose either a fixed range (e.g., **Last 30 Days**) or a dynamic range that updates based on the current date. To learn more, see [Using Filters](/uvm/operational-views-filters).
-
(Optional) In the **Break down by **drop-down menu, select a time interval to set a time-based granularity (e.g., **Day**, **Week**, or **Month**). This selection adds a time dimension to your widget, which counts toward the total number of dimensions.
If you do not make a selection for **Break down by**, the widget will not include a time dimension.
[See image.](#date-filter)
[]![creating a widget with a time filter on a the right showing as a dimension on the left](/downloads/uvm/explore/dashboards/creating-custom-dashboard/breakdown%20by%20dimension%20time%20filter.png)
[]To configure the sorting and ordering of the data included in the widget, do the following:
- **Sort By**: Select the measurement or dimension for sorting the data in the widget. If the widget includes a measurement, the measurement is used as the default for sorting.
- **Order**: Set the data's display order to either descending (down arrow) or ascending (up arrow).
- **Show Top**: Select the maximum number of values that the widget should display. Select the **Group Others** checkbox to group the remaining results into one segment titled **Other**.
- **Exclude Zero Values**: Set whether empty values should be displayed or excluded from the widget display.
[]To apply condition filters:
- **Select Field**: Select the field you want to filter by from the drop-down menu.
- **Select Operator**: Select an operator that defines the relationship between the field and its value. The available operators vary depending on the selected field type. Repeated field filters include **All** and **Any** operators that you can use to evaluate multiple values within a single field. To learn more, see [Using Filters](/uvm/filtering-operational-views).
- **Type Value**: Enter the field value against which the filter is evaluated.
Use the **AND**/**OR** operators and repeat this process to add multiple condition filters to your widget. For example, you can add a condition to your widget, filtering to include only active tickets assigned to teams with either R&D or DEV in their name.
[See image.](#conditions-filter-example)
To remove a filter condition, click the **Delete** icon located to the right of the condition.
[]![6a536864-7ce6-4f5e-88d1-47c183ea5adb.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/6a536864-7ce6-4f5e-88d1-47c183ea5adb.png)
[]On the **Style** tab, you can determine how the data is displayed within the widget.
For example, you can configure the legend display for pie charts. The available options include:
-
**Table**: Displays the legend in a tabular format adjacent to the chart.
[See image.](#table-legend)
-
**Aside**: Displays the legend in lines extending from each chart segment.
[See image.](#aside-legend)
-
**Basic**: Displays dimension values above the chart and measurement values when hovering over a segment.
[See image.](#basic-legend)
- **Off**: Hides the legend entirely.
For the **Table** and **Aside** options, you can enable or disable **Show Values** and **Show Percentage** to control the display of corresponding measurements.
[See image.](#show-values-percentage)
Enable **Show Totals** to display aggregated totals, where applicable.
Apply formatting rules to set color-coded thresholds for your measurements, providing clear visual indicators in widgets. To learn more, see [Creating Formatting Rules](/uvm/creating-formatting-rules).
[]![c804ff8d-e39d-4279-a8ad-f99314fb0f60.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/c804ff8d-e39d-4279-a8ad-f99314fb0f60.png)
[]![aside%20legend%20total%20findings%20by%20source.png](/downloads/uvm/explore/dashboards/configuring-custom-dashboards/aside%20legend%20total%20findings%20by%20source.png)
[]![a0b2e671-99c2-4d1b-9aa3-870300d8e512.jpg](/downloads/uvm/explore/dashboards/creating-custom-dashboard/a0b2e671-99c2-4d1b-9aa3-870300d8e512.jpg)
[]![d5ac973d-954e-4994-bdde-beb6e725f1f2.jpg](/downloads/uvm/explore/dashboards/creating-custom-dashboard/d5ac973d-954e-4994-bdde-beb6e725f1f2.jpg)
[]On the **Interactions** tab, you can configure drilldown interactivity, which allows you to explore data at a more granular level by clicking elements in a widget to reveal additional dimensions.
Drilldown is available for **Bar**, **Pie**, and **Table** widgets that are configured with exactly one dimension.
To set up a drilldown hierarchy in your widget:
-
Click the **Interactions** tab.
[See image.](#interactions-tab)
-
Click **Add Level** to add the next dimension in the drilldown hierarchy.
You can add up to three drilldown levels.
After the drilldown hierarchy is configured, clicking a segment within the widget reveals the interactions menu, where you can either view items or drill down into the next level. To learn more, see [Viewing Items in a Widget Segment](https://help.zscaler.com/uvm/viewing-items-widget-segment).
When drilling down, the widget updates to display the data broken down by the next defined dimension. You can navigate back up the hierarchy using the breadcrumbs bar at the top of the widget.
[]![mceclip9.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/mceclip9.png)
After adding widgets, you can apply dashboard-wide filters using the filter bar in the top-left corner of the dashboard view.
Saved dashboards appear on the Dashboards page, where they can be accessed in View Dashboard mode with all applied configurations.
[See image.](#view-dashboard-mode)
To view existing filters for a widget, hover over the Filter icon. When editing a dashboard, you can click the Filter icon to open the widget configuration page, where you can edit the applied filters.
[]![9c8fa71b-0c82-4bd9-bf6a-ca429935f64f.png](/downloads/uvm/explore/dashboards/creating-custom-dashboard/9c8fa71b-0c82-4bd9-bf6a-ca429935f64f.png)