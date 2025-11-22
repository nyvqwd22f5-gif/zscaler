# Understanding Measurements & Dimensions
Source: https://help.zscaler.com/uvm/understanding-measurements-dimensions
PDF: https://help.zscaler.com/pdf/com/en/1529098.pdf

The Zscaler SecOps platform's analytic capabilities enable you to view and [filter](/uvm/using-filters) data by measurements and dimensions.
- [Measurements](#measurements)
- [Dimensions](#dimensions)
[]A measurement is a quantitative field that represents a calculated value. Common calculation types include sums, averages, and maximums. Measurements are typically used to track or assess numerical aspects of the data. Measurements are calculated for the dataset currently in view and are updated dynamically based on the dimensions and filters applied.
Examples of measurements include:
- Total Undetected Findings: The number of findings in a ticket that have not been detected, and are thus considered remediated.
- Ticket Mean Time to Remediate: The average time it takes to remediate tickets.
[]A dimension is a categorical field used to group and segment data. When a dimension is added, the measurements are organized according to the unique values of that dimension. Examples of dimensions include Asset Type, Source, and Severity Level.
Using dimensions, you can explore how a measurement varies across its different categories. For example, viewing the Total Tickets measurement by Severity Level can help you understand how ticket volume is distributed across severity categories.
Adding multiple dimensions increases the granularity of the analysis. For example, adding Ticket Assignee as a dimension along with the % Active Findings measurement shows the percentage of active findings per assignee. Adding Ticket Severity as an additional dimension recalculates the same measurement for each unique combination of Ticket Assignee and Ticket Severity.
[See image.](#dimensions-breakdown)
Measurements and dimensions are entity specific and dynamically displayed based on the selected Main Entity type, which also determines which records are included in the results. For example, when Ticket is the main entity, only assets linked to tickets are displayed. In contrast, selecting Asset as the main entity shows all assets, including those without any associated tickets or findings (such as assets imported from a CMDB).
Additionally, when searching for measurements, the timeframe of the element you're configuring (i.e., current versus historical) can affect the available measurements. For example, the % Vulnerable Assets measurement is only available when viewing historical data.
Navigating Measurements and Dimensions
Measurements and dimensions are used across the SecOps platform to configure and adjust the displayed data (e.g., when applying [filters](/uvm/using-filters) in [reports](/uvm/creating-reports) and [custom dashboards](/uvm/configuring-custom-dashboards), or when [creating saved views](/uvm/creating-managing-saved-views)).
Dimensions are grouped by entity type (e.g., Ticket, Asset), and measurements appear at the bottom of the dimensions list.
In measurement and dimension lists, you can adjust the displayed fields:
- Click the **Measurements **icon to view the list of available measurements.
- Click the **Dimensions **icon to view the list of available dimensions.
- Click **In Use **to display the fields currently in use.
- Use the search bar to locate specific fields.
[See image.](#measurements-dimensions-filters)
[]![an example of adding a dimension](/downloads/uvm/explore/reports/creating-reports/df5c05ad-c126-4d17-849e-efa7ab3dda40.png)
[]![measurements and dimensions filters](/downloads/uvm/analytics/understanding-measurements-dimensions/measurements%20and%20dimensions%20filters.png)