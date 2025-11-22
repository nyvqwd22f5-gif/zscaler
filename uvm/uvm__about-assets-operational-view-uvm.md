# About Assets in UVM
Source: https://help.zscaler.com/uvm/about-assets-operational-view-uvm
PDF: https://help.zscaler.com/pdf/com/en/1527976.pdf

The Assets page provides a centralized view of the assets in your organization's Zscaler Unified Vulnerability Management (UVM) app.** **Each asset represents a single asset in your environment, unified (i.e., merged) and enriched with information from multiple sources. On this page, you can explore asset details and statuses, view the sources and records from which it was merged, view the findings it contains, and view the tickets it's related to.
The Assets page provides the following benefits and enables you to:
- Access and organize assets using system-saved views, filters, grouping options, and customizable table columns to focus on specific scenarios.
- Explore detailed information about each asset, including associated tickets and findings, risk scores, ownership, and the sources that the assets were detected on.
- Understand how the asset was merged from multiple sources into a unified entity.
About the Assets Page
On the Assets page (Vulnerabilities > Assets), you can do the following:
- Select from system-saved views, or views [you previously saved](/uvm/creating-managing-saved-views).
- [List of System-Saved Views](#system-saved-views-list)
- Search for specific assets by entering keywords in the search bar.
- [Save your view](/uvm/creating-managing-saved-views) for quick access after making adjustments to it (e.g., applying filters, adjusting columns, or grouping).
- [Filter](/uvm/using-filters) assets by **Asset Is Crown Jewel, State**, **Owner ID**, or **Source**.
- Explore the **Overview **charts to gain high-level insights into the assets and their risk level in your environment. The charts are adjusted by the selected view and filters.
- **Number of Assets by Risk Score**: Displays the number of assets in the different risk score ranges (in increments of 0.5). The X-axis represents the max severity score of active findings related to the asset, and the colors represent the risk category. You can hover over the bars to view the number of assets and the exact score range.
- **Asset Count by Type**: Presents asset count categorized by asset type, displaying the 5 most frequently occurring types.
- **Asset Count by Operating System**: Displays the number of assets categorized by operating system, displaying the 5 most frequently occurring types.
- [Group assets](/uvm/grouping-operational-views-group) by fields such as **Asset State**, **Asset ID**, or **Asset Owner ID**.
- Refresh the page to reflect the most current information.
- Export the list of assets and their associated details as a CSV file.
- [Modify the columns displayed in the table.](/uvm/managing-table-columns)
- Select all assets on the page.
- Click an asset to open individual [asset drawers](/uvm/managing-assets-uvm). When the default **Active **saved view is selected, you can see the following details for each asset:
- **ID**: The asset's ID on the SecOps platform.
- **Type**: The asset type (e.g., **Windows Workstation**, **Web Application**, **Container Image**).
- **Name**: The asset's name.
- **Risk Score**: The risk level of findings associated with the asset. The risk score is initially set by the default [reconciliation function](/uvm/attribute-reconciliation-default-functions), and reflects the highest severity score among the findings. The default can be customized through [Data Unification](/uvm/what-data-unification).
- **Risk Mass**: The sum of all severity scores of the active findings associated with the asset.
- **Owner ID**: The unit in the organization assigned to handling the asset.
- **Sources**: The sources that the information on the asset is retrieved from.
- **Is Crown** **Jewel**: A boolean field with values of **TRUE **or **FALSE **indicating whether the asset is defined as a crown jewel asset (i.e., one of your organization's most valuable assets).
- **Site**: The site that the asset is located on.
- **First Seen**: The earliest date on which a finding on the asset was first detected.
- **Last Seen**: The latest date on which a finding on the asset was detected.
- **Total Findings**: The sum of the active findings per severity.
- **Tags**: Tags pulled from your sources that include information about the asset that can be [extracted](/uvm/configuring-field-unification) and used to enrich the asset data.
![about assets operational view](/downloads/uvm/vulnerability-management/remediate-uvm/about-assets-operational-view-uvm/about%20assets%20operational%20view_0.png)
[]The Assets page includes system views with predefined filter selections, providing quick access to common data scopes:
- **Active**: All active assets (i.e., all assets ingested into the account from your sources that have not been aged yet). This is the default view.
- **Vulnerable**: All active assets that have at least one active finding.