# Viewing & Managing Assets in UVM
Source: https://help.zscaler.com/uvm/viewing-managing-assets-uvm
PDF: https://help.zscaler.com/pdf/com/en/1531065.pdf

A Zscaler Unified Vulnerability Management (UVM) asset represents a single asset in your environment, unified (i.e., merged) and enriched with information from multiple sources. Selecting an asset on the Assets page opens its drawer, where you can view detailed information and perform multiple actions for the asset. To learn more, see [About Assets in UVM](/uvm/about-assets-operational-view-uvm).
The actions you can perform in the asset drawer depend on your user role in the UVM app. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
The asset drawer can be configured by admins and might look different in your account. The information provided in this article refers to the default asset drawer settings. To learn more, see [Configuring Entity Drawers in UVM](/uvm/configuring-ticket-ui-vulnerabilities-app).
To view the asset drawer:
-
Go to **Vulnerabilities **> **Assets**.
[See image.](#assets-operational-view)
-
Click the asset you want to view.
[See image.](#asset-drawer)
A drawer appears with the following details and tabs:
- [Top Panel](#asset-drawer-top-panel)
- [Details](#asset-drawer-details-tab)
- [Asset Merging](#asset-drawer-merging-tab)
- [Findings](#asset-drawer-findings-tab)
- [Tickets](#asset-drawer-tickets-tab)
- Click **Apply Changes** after making changes to the asset, or close the drawer.
[]In the top panel of the asset drawer, you can view:
- **Name**: The name of the asset.
- **First Seen**: The asset's first seen date.
Additionally, you can perform the following actions:
- Copy a shareable link to the asset you're viewing.
- View the asset ID.
- Expand the asset's drawer to full screen.
- Close the asset drawer.
- View the asset's severity level and severity score. By default, it reflects the highest severity score among the findings detected on the asset.
[]On the **Details **tab, you can view:
- **Asset Type**: The classification or category that the asset belongs to, such as server, workstation, or application.
- **Sources**: The sources that the findings on the asset were detected on.
- **Assignee**: The agent or team responsible for handling the asset.
- **Risk Mass**: The asset's cumulative risk exposure, calculated by summing the severity scores of active findings for each severity level (i.e., Critical, High, Medium, Low), and rounding the result. This indicator can be used to prioritize assets with similar risk profiles.
- **Has PII Data**: Indicates whether the asset contains Personally Identifiable Information (PII), highlighting its sensitivity and compliance requirements.
[]On the **Asset Merging **tab, you can view the original source records that the asset was merged from.
Additionally, you can perform the following actions:
- Apply filters to adjust the displayed assets by relevant attributes (e.g., filtering the original source records owner ID or first seen date).
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
- Click the **Export as CSV **icon to export the list of assets that the current asset was merged from as a CSV file.
[]On the **Findings **tab, you can explore the findings that were detected on the asset.
To view the finding's details (e.g., descriptions and [score calculation logic](/uvm/configuring-severity-score-formulas)), you can either expand the finding or drill down to the finding drawer.
Additionally, you can perform the following actions:
- Apply filters to adjust the displayed findings by relevant attributes and to explore the asset's risk portfolio (e.g., filtering the findings by a particular state, title, or severity score).
- To update key finding details, select the findings and click **Update**. The fields available to update include fields that were enabled for manual override in Configure > Data Model.
- Click the** Export as CSV **icon to export findings on the asset to a CSV file.
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
[]On the **Tickets **tab, you can view all tickets related to the asset and a summary of their details, sources, status, and remediation percentage.
Additionally, you can perform the following actions:
- Apply filters to adjust the displayed tickets by relevant attributes (e.g., filtering the tickets by type, title, or severity score).
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
Clicking a ticket opens its drawer. To return to the asset drawer, click the asset name in the top-left corner of the ticket drawer.
[]![vulnerabilities > assets table](/downloads/uvm/vulnerability-management/remediate-uvm/managing-tickets-uvm/assets%20table.png)
[]![asset drawer](/downloads/uvm/vulnerability-management/remediate-uvm/viewing-assets-uvm/asset%20drawer.png)