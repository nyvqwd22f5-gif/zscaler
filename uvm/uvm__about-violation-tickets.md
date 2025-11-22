# About Violation Tickets
Source: https://help.zscaler.com/uvm/about-violation-tickets
PDF: https://help.zscaler.com/pdf/com/en/1531112.pdf

The Violation Tickets page provides a centralized overview of your organization's compliance-related tickets in AEM. Each violation ticket aggregates related policy violations into a single work item, helping you streamline actions needed to address compliance and operational risks. On this page, you can explore violation ticket details and statuses, assign tickets, and dispatch tasks to external platforms (e.g., Jira, ServiceNow).
The Violation Tickets page provides the following benefits and enables you to:
- Access and organize violation tickets using system-saved views, filters, grouping options, and customizable table columns to focus on specific scenarios.
- Dive into detailed violation ticket information to prioritize actions, assign owners, and understand associated policies and affected assets.
- Dispatch violation tickets to external platforms (e.g., Jira, ServiceNow) to streamline workflows and remediation processes.
About the Violation Tickets Page
On the Violation Tickets page (Assets > Violation Tickets), you can do the following:
-
Select from system-saved views, or views [you previously saved](/uvm/creating-managing-saved-views).
The Active view is the system default, which displays all violation tickets with at least one active policy violation.
- Search for specific tickets by entering keywords in the search bar.
- [Save your view](/uvm/creating-managing-saved-views) for quick access after making adjustments to it (e.g., applying filters, adjusting columns, or grouping).
- [Filter](/uvm/using-filters) violation tickets by **Severity**, **State**, **Assignee**, or **Policy Violation Count**.
- Apply actions to multiple violation tickets:
- **Update**: Update the details of a group of selected violation tickets.
- **Merge**: Merge multiple selected tickets into one violation ticket.
- **Create 3rd party Issue**: Dispatch a group of selected violation tickets to external work management systems.
- [Group violation tickets](/uvm/grouping-operational-views-group) by fields such as **Policy**, **Severity**, or **Assignee**.
- Refresh the page to reflect the most current information.
- Export the list of violation tickets and their associated details as a CSV file.
- [Modify the columns displayed in the table.](/uvm/managing-table-columns)
- Select multiple violations.
- Click a violation ticket to open individual [violation ticket drawers](/uvm/managing-violation-tickets-aem). When the default **Active **saved view is selected, you can see the following details for each violation ticket:
- **ID**: The unique AEM violation ticket ID.
- **Severity Score**: The severity score assigned to the violation ticket, calculated based on the severity scores of the policy violations within the violation ticket (e.g., using the highest score or the average score).
- **Title**: The violation ticket title.
- **SLA**: The service-level agreement (SLA) deadline for the violation ticket.
- **Assignee**: The remediation owner assigned to remediate the ticket.
- **Status**: The current status of the ticket.
- **Remediation**: The percentage of policy violations resolved within the violation ticket.
- **Policy Violation Count**: The total number of policy violations in the ticket.
- **Asset Count**: The number of affected assets linked to the ticket.
![about violation tickets operational view](/downloads/uvm/asset-exposure-management-aem/remediate-aem/about-violation-tickets/about%20aem%20violation%20tickets.png)