# Viewing Violation Tickets in AEM
Source: https://help.zscaler.com/uvm/viewing-violation-tickets-aem
PDF: https://help.zscaler.com/pdf/com/en/1531118.pdf

Zscaler Asset Exposure Management (AEM) violation tickets aggregate related policy violations into a single work item that can be fixed as one task. Selecting a violation ticket from the Violation Tickets page opens the violation ticket's drawer, where you can view detailed information and perform multiple actions for the violation ticket. To learn more, see [About Violation Tickets](/uvm/about-violation-tickets-operational-view-aem).
The actions you can perform in the violation ticket drawer depend on your user role in AEM. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
To view the violation ticket drawer:
- Go to the AEM app.
-
In the left-side navigation, click **Violation Tickets**.
[See image.](#violation-tickets-operational-view)
-
Click the violation ticket you want to view.
[See image.](#violation-ticket-drawer)
A drawer appears with the following details:
- [Top Panel](#violation-ticket-drawer-top-panel)
- [Details](#violation-ticket-details-tab)
- [Policy Violations](#violation-ticket-policy-violations-tab)
- [Assets](#violation-ticket-assets-tab)
- Click **Apply Changes** after making updates to the violation ticket.
[]![Violation Tickets table in UVM](/downloads/uvm/asset-exposure-management-aem/remediate-aem/managing-violation-tickets-aem/violation%20tickets%20table.png)
[]![violation ticket drawer](/downloads/uvm/asset-exposure-management-aem/remediate-aem/viewing-violation-tickets-aem/violation%20ticket%20drawer.png)
[]In the top panel of the violation ticket drawer, you can view:
- **Title:** The violation ticket's title set by your account's grouping rules.
- **First Seen:** The earliest detected policy violation included in the violation ticket.
- **Severity Score:** The violation ticket's severity score.
- **Status:** The current workflow status of the violation ticket (e.g., **New**, **Open**, **In Progress**, or **Closed**).
Additionally, you can perform the following actions:
- Copy a shareable link to the violation ticket.
- View the violation ticket's ID.
- Expand the violation ticket drawer to full screen.
- Close the violation ticket drawer.
[]On the **Details **tab, you can view:
- **SLA:** The service-level agreement (SLA) date that the violation ticket must be remediated by.
- **Assignee:** The user or team assigned to handle the violation ticket.
- **Policy Violations Count:** The total number of policy violations aggregated into the violation ticket.
[]On the **Policy Violations **tab, you can view all the policy violations aggregated into the violation ticket. You can:
- Apply filters to adjust the displayed policy violations by relevant attributes (e.g., **Severity**, **Policy Name**).
- Drill down into individual policy violations to view additional details in the policy violation drawer.
- Click the **Export as CSV **icon to export policy violations in the violation ticket to a CSV file.
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
[]On the **Assets **tab, you can view the list of assets affected by the policy violations contained in the violation ticket. You can perform the following actions:
- Apply filters to adjust the displayed assets by relevant attributes (e.g., **Asset Type**, **Last Seen**).
- Drill down into individual assets to view additional details in the asset drawer.
- Select an asset and click **Update **to update the asset's details. The fields available to update include fields that have been enabled for manual override in Configure > Data Model.
- Click the **Export as CSV **icon to export assets in the violation ticket to a CSV file.
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).