# Viewing & Managing Tickets in UVM
Source: https://help.zscaler.com/uvm/viewing-managing-tickets-uvm
PDF: https://help.zscaler.com/pdf/com/en/1531052.pdf

Zscaler Unified Vulnerability Management (UVM) tickets aggregate related findings into a single work item that can be fixed as one task. Selecting a ticket on the Tickets page opens its drawer, where you can view detailed information and perform multiple actions for the ticket. To learn more, see [About Tickets](/uvm/about-tickets-operational-view).
The actions you can perform in the ticket drawer depend on your user role in the UVM app. To learn more, see [Understanding System Roles](/uvm/understanding-system-roles) and [Creating Custom Roles](/uvm/creating-custom-roles).
The ticket drawer can be configured by admins and might look different in your account. The information provided in this article refers to the default ticket drawer settings. To learn more, see [Configuring Entity Drawers in UVM](/uvm/configuring-ticket-ui-vulnerabilities-app).
To view the ticket drawer:
-
Go to **Vulnerabilities **> **Tickets**.
[See image.](#tickets-operational-view)
-
Click the ticket you want to view.
[See image.](#ticket-drawer)
A drawer appears with the following details and tabs:
- [Top Panel](#ticket-drawer-top-panel)
- [Details](#ticket-drawer-details-tab)
- [Findings](#ticket-drawer-findings-tab)
- [Assets](#ticket-drawer-assets-tab)
- [Fixes](#ticket-drawer-fixes-tab)
- [Related Tickets](#ticket-drawer-related-tickets-tab)
- [Comments](#ticket-drawer-comments-tab)
- [Activity](#ticket-drawer-activity-tab)
- Dispatch the ticket to the external work management systems (e.g., Jira) configured in your account's outegrations. To learn more, see [Creating Outegrations](/uvm/creating-outegrations) and [Creating & Managing Third Party Tickets](/uvm/creating-managing-third-party-tickets).
- Click **Apply Changes** after making changes to the ticket.
[]![tickets operational view](/downloads/uvm/vulnerability-management/remediate-uvm/viewing-uvm-tickets/tickets%20table.png)
[]![ticket drawer](/downloads/uvm/vulnerability-management/remediate/ticket%20drawer.png)
[]In the top panel of the ticket drawer, you can view:
- **Title**: The ticket title is set by your account's grouping rules.
-
**First Seen**: The ticket's first seen date reflects the earliest detected finding included in the ticket.
The ticket creation date can differ from its first seen date due to ticket merges or changes to grouping rules.
Additionally, you can perform the following actions:
- Copy a shareable link to the ticket you're viewing.
- View the ticket ID.
- Expand the ticket's drawer to full screen.
- Close the ticket drawer.
- Check if the ticket is in Locked Scope, which means new findings cannot be added to it. Tickets are automatically locked when created through the findings split or ticket merge actions. A ticket might also be locked if it's linked to an external system or if an exception request was submitted for it. You can customize the conditions for locking tickets in the Ticket Lifecycle settings.
- View and manually update the ticket's severity level and severity score. The score on the right is the ticket's original severity score, while the score on the left is the UVM score, which is calculated based on the configurable score settings. To learn more, see [Configuring Severity Score Formulas](/uvm/configuring-severity-score-formulas).
-
View and manually update the ticket's status to track and manage its progress in the workflow.
When remediating tickets, consider the distinction between the ticket's status and state. Ticket status is either set manually by the ticket assignee or synced from an external work management system, indicating the ticket's current step in your workflow. Ticket state reflects whether the ticket contains active findings that were detected in a recent scan. The ticket state can remain active as long as it contains active findings, regardless of the ticket status.
[]On the **Details **tab, you can view:
- **Sources**: The sources that the findings in the ticket were detected on.
- **Assignee**: The agent or team responsible for handling the ticket.
- **SLA**: The service level agreement (SLA) date that the ticket needs to be remediated by.
- **Risk Mass**: The ticket's cumulative risk exposure, calculated by summing the severity scores of active findings for each severity level (i.e., Critical, High, Medium, Low), and rounding the result. This indicator can be used to prioritize tickets with similar risk profiles.
- **Grouping Details**: Specifies the grouping rule and the ruleset that grouped the findings into the ticket. This can be used when investigating whether your account's grouping logic needs to be adjusted. To learn more, see [Configuring Grouping Rules](/uvm/configuring-grouping-rules).
- **Exceptions**: The details of all exception requests to extend the ticket's SLA date that were submitted for the ticket. To learn more, see [Understanding Exception Requests](/uvm/understanding-exception-requests).
Additionally, you can perform the following actions:
- If the ticket isn't assigned, or if the ticket is incorrectly assigned, you can manually update the ticket assignee.
- To add attachments to your ticket, click the **Attachment **icon, and select the files you want to attach. Supported formats include CSV and XSLX.
- To request an exception for the ticket to extend its SLA date, click **Request Exception**. To learn more, see [Requesting Exceptions](/uvm/requesting-exceptions).
[]On the **Findings **tab, you can explore the findings that the ticket contains, aggregated based on the grouping rules configured in the account. For example, you can view and filter findings by the asset that they were discovered on. To learn more, see [Configuring Grouping Rules](/uvm/configuring-grouping-rules).
To view the finding's details (e.g., descriptions and [score calculation logic](/uvm/configuring-severity-score-formulas)), you can either expand the finding or drill down to the finding drawer.
Additionally, you can perform the following actions:
- Apply filters to adjust the displayed findings by relevant attributes (e.g., filtering the findings in the ticket by a particular asset).
-
Select the findings that you want to split into a new ticket, and click **Split into a New Ticket**.
Splitting findings from a ticket into a new ticket can be used when you need to focus on a specific subset of findings, such as launching a targeted remediation campaign, requesting an SLA extension, assigning findings to different teams, or resolving cases where automatic grouping has incorrectly combined unrelated findings. To learn more, see [Manually Splitting Findings into New Tickets](/uvm/manually-splitting-findings-new-ticket).
- To update key finding details, select the findings and click **Update**. The fields available to update include fields that were enabled for manual override in Configure > Data Model.
- To export the findings in the ticket as a CSV file, click the **Export as CSV **icon.
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
[]On the **Assets **tab, you can explore the list of assets on which the findings in the ticket were detected. For example, you can analyze the number of findings on each of the assets in the ticket and the percentage that are remediated.
To view the asset's details in the asset drawer, hover over the asset and click **Drill to Asset Page **on the right.
Additionally, you can perform the following actions:
- Apply filters to adjust the displayed assets to focus on those relevant to your current task.
- To update asset details, select the assets and click **Update**. The fields available to update include fields that were enabled for manual override in Configure > Data Model.
- To export the assets in the ticket as a CSV file, click the **Export as CSV **icon.
- Adjust the displayed columns and their sorting settings. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
[]On the **Fixes **tab, you can view the recommended fixes for the findings in the ticket. This tab is displayed depending on factors such as ticket type or available remediation insights in data sources.
The system extracts the following fix types from source data:
- KB: Microsoft KB fixes
- Version: Version updates
- Text: Fixes descriptions
You can group the fixes to optimize potential remediation strategies, to help you determine what fixes can be applied to resolve as many findings as possible.
To group fixes:
-
Click the **Settings **icon.
The **Select your preferred table view** dialog window appears.
- Select a **Group By **option (e.g., **Component**, **Fix**, **Asset**).
- Click **Apply**.
[]On the **Related Tickets **tab, you can view a list of tickets that are related to the ticket you're currently viewing.
Related tickets include:
- Tickets that were aggregated based on the same grouping rule as the locked ticket.
- Tickets that were split from the current ticket.
- Tickets that the current ticket were split from.
[]On the **Comments **tab, you can add, delete, or edit comments to collaborate, inquire, or share information with other users.
[]On the **Activity **tab, you can view the ticket's activity feed, which is the chronological record of actions performed on the ticket.
You can filter the feed by:
- **Manual**: Manual changes that were made to the ticket (e.g., manually assigning the ticket, or [splitting findings from the ticket](/uvm/manually-splitting-findings-new-ticket)).
- **Outegrations Actions**: Changes performed on the ticket as a result of a two-way sync with a third-party ticket (e.g., creating a Jira issue, updating the ticket's status based on a linked ServiceNow ticket).
- **System Actions**: Automatic actions performed by the system (e.g., newly discovered findings added to the ticket).