# About Tickets
Source: https://help.zscaler.com/uvm/about-tickets
PDF: https://help.zscaler.com/pdf/com/en/1527801.pdf

The Tickets page provides a centralized view of your organization's Zscaler Unified Vulnerability Management (UVM) tickets. Each ticket in the table aggregates related findings into a single work item that can be fixed as one task. On this page, you can explore ticket details and statuses, assign tickets to remediation owners, and initiate ticket remediation by dispatching tasks to external work management platforms (e.g., Jira, ServiceNow).
The Tickets page provides the following benefits and enables you to:
- Access and organize tickets using system-saved views, filters, grouping options, and customizable table columns to focus on specific scenarios or issues.
- Dive into detailed ticket information to prioritize actions, assign owners, and understand associated findings and assets.
- Dispatch tickets to external platforms (e.g., Jira, ServiceNow) to streamline workflows and remediation processes.
About the Tickets Page
On the Tickets page (Vulnerabilities > Tickets), you can do the following:
- Select from system-saved views or views [you previously saved](/uvm/creating-managing-saved-views).
- [List of System-Saved Views](#system-saved-views-list)
- Search for specific tickets by entering keywords in the search bar.
- [Save your view](/uvm/creating-managing-saved-views) for quick access after making adjustments to it (e.g., applying filters, adjusting columns, or grouping).
- [Filter](/uvm/using-filters) tickets by **Severity**, **Status**, **Assignee**, or **Source**.
- Apply actions to multiple tickets:
- **Update**: Update the details of a group of selected tickets.
- **Merge**: Merge multiple selected tickets into one ticket.
- **Comment**: Add comments to a group of selected tickets.
- **Create 3rd party Issue**: Dispatch a group of selected tickets to external work management systems.
- [Group tickets](/uvm/grouping-operational-views-group) by fields such as **Severity**, **Ticket Type**, or **Assignee**.
- Refresh the page to reflect the most current information.
- Export the list of tickets and their associated details as a CSV file.
- [Modify the columns displayed in the table.](/uvm/managing-table-columns)
- Select all policy violations on the page.
- Click a ticket to open individual [ticket drawers](/uvm/viewing-uvm-tickets). When the default **Active **saved view is selected, you can see the following details for each ticket:
- **ID**: The unique UVM ticket ID.
- **Severity Score**: The [severity score](/uvm/understanding-severity-scores) assigned to the ticket, calculated based on the severity scores of the findings within the ticket (e.g., using the highest score or the average score).
- **Risk Mass**: The sum of severity scores of findings in the ticket.
- **Title**: The ticket title, as configured in ticket [grouping rules](/uvm/configuring-grouping-rules).
- **First Seen**: The ticket's first seen date, which reflects the earliest detected finding included in the ticket.
- **SLA**: The SLA deadline for the ticket.
- **Assignee**: The remediation owner assigned to remediate the ticket.
- **Sources**: The sources that the findings in the ticket were ingested by.
- **Status**: The current status of the ticket.
- **Remediation**: The percentage of findings resolved within the ticket, based on those that are no longer detected by your sources.
![about tickets operational view](/downloads/uvm/vulnerability-management/remediate-uvm/about-tickets/about%20tickets%20operational%20view.png)
[]The Tickets page includes system views with predefined filter selections, providing quick access to common data scopes:
- **Active**: All active tickets (i.e., all tickets with at least one active finding). This is the default view.
- **Closed**: All tickets with a status tagged as closed in status settings (by default, this is the Confirmed status).
- **Missing Assignee**: All tickets with an unpopulated assignee field.
- **No External Ticket Created**: All tickets that are not linked to an external case management issue.
- **Over SLA**: All open tickets with expired service level agreements (SLA).
- **Pending Confirmation**: All tickets are automatically set as inactive when they no longer contain active findings, but have not yet been manually set as closed by the assignee.
- **Tickets With New Findings**: All tickets to which findings were added in the last week.