# Creating & Managing Third-Party Tickets
Source: https://help.zscaler.com/uvm/creating-managing-third-party-tickets
PDF: https://help.zscaler.com/pdf/com/en/1528131.pdf

Third-party outegrations allow organizations to create third-party tickets in external work management systems directly from the Zscaler Security Operations (SecOps) applications' tickets (e.g., Tickets in UVM, Violation Tickets in AEM) to facilitate a streamlined workflow. After a work management outegration is created and configured, third-party tickets can be dispatched and managed directly from the SecOps application's tickets to external systems (e.g., [Jira](/uvm/configuring-jira-outegration), [ServiceNow](/uvm/configuring-servicenow-outegration), and other supported outegrations). To learn more, see [Creating Outegrations](/uvm/creating-outegrations).
Creating Third-Party Tickets
To create a third-party ticket:
- Go to the SecOps app's tickets page (e.g., [Tickets](/uvm/about-tickets-operational-view-uvm) in UVM, [Violation Tickets](/uvm/about-violation-tickets-operational-view-aem) in AEM).
-
Click the ticket you want to dispatch to the external system.
The ticket drawer appears.
-
In the ticket drawer, click **Create **<Vendor> **Ticket **in the bottom-right corner.
The SecOps ticket is dispatched to the external system, and is populated according to the mapping configuration you set up for the outegration.
To create multiple third-party tickets:
- Select the checkboxes of the tickets you want to dispatch from the tickets table.
-
Click **Create 3rd Party Issue**.
[See image.](#bulk-create-third-party-issue-button)
The SecOps tickets are dispatched to the external system, and are populated according to the mapping configuration you set up for the outegration.
When dispatching multiple tickets in bulk, a separate external ticket is created for each SecOps ticket. The external ticket is created and populated based on the field mappings defined during the outegration setup. To learn more, see [Creating Outegrations](/uvm/creating-outegrations).
SecOps tickets cannot be dispatched in bulk to different outegrations (e.g., Jira Bugs and Jira Tasks). Each ticket must be dispatched individually to ensure compatibility with their respective outegration configurations.
If two-way sync from the external system to the SecOps platform is configured, creating a third-party ticket triggers the sync and updates the SecOps ticket based on the outegration's settings set by your account admin.
Managing Third-Party Tickets
You can manage the connection between third-party tickets and SecOps tickets, including unlinking or manually linking tickets. To filter your tickets by whether they're linked to third-party tickets, you can add the Ticket External Issue Type field to the filters and select the desired integrations, or Empty to display tickets with no linked third-party tickets. To learn more, see [Using Filters](/uvm/using-filters).
Linking Existing Third-Party Tickets
To link an existing third-party ticket to a SecOps ticket:
-
Click the SecOps ticket you want to link.
The ticket drawer opens.
-
In the ticket drawer, click the **Create <**Outegration**> Ticket** drop-down menu, and select **Manually connect <**Outegration**>**.
[See image.](#create-outegration-dropdown-menu1)
-
Enter the third-party ticket ID.
Enter only the third-party ticket ID (e.g., `INC0012345` for a ServiceNow ticket ID), not the ticket's URL or link.
- Click **Apply**.
A third-party ticket can only be linked to one SecOps ticket.
If two-way sync from the external system to SecOps is configured, linking a third-party ticket triggers the sync and updates the SecOps ticket based on the outegration's settings set by your account admin. To learn more, see [Creating Outegrations](/uvm/creating-outegrations).
Unlinking Third-Party Tickets
To unlink a third-party ticket from the SecOps ticket:
-
Click the SecOps ticket you want to unlink.
The ticket drawer opens.
-
Click the **Create <**Outegration**> Ticket** drop-down menu, and select **Unlink <**Outegration**>**.
[See image.](#unlink-outegration-dropdown-menu)
After the tickets are unlinked, updates between the third-party ticket and the SecOps ticket no longer sync.
[]![bulk create third party ticket button](/downloads/uvm/vulnerability-management/remediate-uvm/creating-managing-third-party-tickets/bulk%20create%20third%20party%20issue.png)
[]![create outegration dropdown menu open](/downloads/uvm/getting-started/admin-portal/creating-managing-third-party-tickets/create%20outegration%20dropdown%20menu%20open.png)
[]![unlink outegration dropdown menu open](/downloads/uvm/getting-started/admin-portal/creating-managing-third-party-tickets/unlink%20outegration%20dropdown%20menu%20open.png)