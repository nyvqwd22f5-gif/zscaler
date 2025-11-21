# Filtering & Customizing the Assets Page
Source: https://help.zscaler.com/easm/filtering-customizing-assets-page
PDF: https://help.zscaler.com/pdf/com/en/1503586.pdf

The [Assets page](/easm/about-asset-inventory) includes a set of filtering options that allows you to view a subset of data that matches specified criteria. You can set the criteria based on specific parameters of assets such as risk level, last seen, and type. These parameters can be applied individually or together to the Assets table to filter the data. After building a search query using the filters, you can optionally save the query as a custom filter to reuse it in the future for routine tasks. In addition, you can customize the table columns by choosing to show or hide specific columns from the table and by reordering and sorting the columns.
The following sections describe how to apply filters on assets and how to customize the Assets table columns.
The data on the Assets page corresponds to your organization selected on the top-right corner. Before you begin, ensure that the desired organization is selected.
Applying Filters
On the Assets page, you can select the required filters and select appropriate values to apply the filters. The mode of selection varies across the filters with some filters using a single select drop-down, while other filters support multiple select drop-downs from a predefined set of options. Some filters also support the use of logical operators to build more specific queries by manually entering the required values for match criteria.
The following filters are available:
- **Status**: Filters the assets based on their status. This filter allows you to select multiple values simultaneously by using the respective checkboxes. The following statuses are available for assets: Approved, Candidate, and Archived.
-
**Risk Level**: Filters the assets based on their criticality into Minimal, Low, Medium, High, and Critical risk levels, depending on the values chosen. This filter allows you to select multiple values simultaneously by using the respective checkboxes. The risk level assigned to an asset is based on the dynamic risk score generated for the asset.
[Mapping between Risk Level and Risk Score](#riskLevel-riskScore-mapping)
- **Last Seen**: Filters the assets based on when they were last detected in the EASM asset scan. This filter allows you to obtain the list of exposed assets that were observed in the most recent scans (within the last 7 days or 30 days) to a much greater range of timeline of 1 year. This filter supports single value selection using a drop-down menu and comes with the following options: Within 7 Days, Within 30 Days, Within 90 Days, and Within 1 Year.
-
**Type**: Filters the assets based on the type into which the asset is classified by EASM. The assets are classified into one or more of the following types:
- Domains
- Hosts
- Web Pages
- Certificates
- ASNs
- IP Addresses
- IP Blocks
This filter allows you to select multiple values simultaneously by using the respective checkboxes.
[See image.](#asset-filters-image)
Customizing Table Columns
You can customize the columns that appear within the Assets table by using the following options on the Assets page:
- Select the columns that must be shown within the table by clicking the **Settings** icon in the top-right corner. In the **Column Chooser** window that appears, you can select or deselect columns by clicking on them to add or remove them from the table respectively. The table refreshes and displays the new column set. The **Name** column is always shown and cannot be modified.
-
Sort the list by a specific column in an alphabetical or numerical order by using the **Sort** icon shown in the column header. The sorting option is available only for specific columns, indicated by the **Sort** icon displayed next to the column name.
To appropriately sort the columns, ensure that only one column is sorted at a time and deselect the Sort icon for other columns which use the functionality simultaneously.
[]
| Risk Level | Risk Score Range |
| ---------- | ---------------- |
| Minimal | 0 |
| Low | 1–39 |
| Medium | 40–69 |
| High | 70–89 |
| Critical | 90–100 |
[]![Asset filters in EASM to view a subset of the asset data](/downloads/easm/asset-inventory/filtering-customization-assets/asset-filters.png)