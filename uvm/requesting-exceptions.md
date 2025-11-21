# Requesting Exceptions
Source: https://help.zscaler.com/uvm/requesting-exceptions
PDF: https://help.zscaler.com/pdf/com/en/1527636.pdf

When a ticket cannot be remediated within its designated service level agreement (SLA) due to technical limitations, an unavailable fix, or unacceptable business impact, you can submit an exception request to temporarily exempt the ticket from published security policies. When initiating the exception request, you'll need to provide justification and submit necessary supporting evidence for review. The request is then assessed by a reviewer, who either approves or denies it. To learn more, see [Understanding Exception Requests](/uvm/understanding-exception-requests).
If Exceptions is enabled in your account, you can submit exception requests.
Submitting Exception Requests
Before submitting an exception request, make sure the ticket contains only the findings you want the exception to cover. An exception applies to the entire ticket, not individual findings within it.
- To request an exception for a subset of a ticket's findings, split the relevant findings into a new, separate ticket. To learn more, see [Managing Manual Ticket Grouping](/uvm/managing-manual-ticket-grouping).
- To request an exception for findings across multiple tickets, merge the relevant tickets or findings into a single, consolidated ticket. To learn more, see [About Tickets](/uvm/about-tickets).
When your findings are grouped into a single ticket, you can request an exception.
To create an exception request:
- Go to **Vulnerabilities** > **Tickets**.
-
In the table, click the ticket for which you want to request an exception.
The **Ticket **drawer appears.
-
On the **Details** tab, click **Request Exception**.
[See image.](#request-exception-button)
The **Request Exception **dialog window appears.
- In the **Request Exception **dialog window:
- **Reason**: Select a reason for the exception from the drop-down menu.
-
**Requested SLA**: Select the date for the ticket's SLA extension.
Additional fields might appear depending on your organization's settings.
- (Optional) Click **Add Attachment **to upload documents that can support justification for the request.
- Click **Submit**.
After submitting, your request is routed for review. You can track your submission directly within the ticket it was created for, or from the Exceptions page. On the Exceptions page, filter by Requester Name to see all your requests and click Save As View to [create a saved view](/uvm/creating-managing-saved-views) for quick access to your requests. To manage a specific request, select the exception and add comments, upload attachments, or review the request's activity.
If no designated reviewers are assigned in your account, the Reviewer field remains empty by default. This typically means all users with reviewer permissions are responsible for reviewing exceptions.
By default, when submitting an exception request, the approved SLA field in the exception is auto-populated with the requested SLA. The ticket's SLA field updates with the Requested SLA if the request is approved.
Understanding Exception Statuses
The status of your request reflects the reviewer's decision and is shown in the top-right corner of the exception drawer.
- Approved: The request was accepted. The ticket's SLA date automatically updates to the approved date, and the ticket is locked to prevent new findings from being added.
- Denied: The request was rejected, and the ticket's original SLA date remains unchanged.
-
Cancelled: The request was automatically cancelled because the ticket's SLA was updated to a later date than the one you requested. This can happen if:
- The ticket's SLA date was manually changed to a later date.
- A new finding with lower severity was added to the ticket, consequently pushing the ticket's SLA date.
- Findings with critical or high severity were split from the ticket to a new ticket.
You cannot manually cancel a request. If it's no longer needed, add a comment notifying the reviewer.
Syncing Exceptions with External Systems
If your organization uses an outegration (e.g., ServiceNow IRM) to track exceptions, you can sync your request. To learn more, see [Creating Outegrations](/uvm/creating-outegrations).
To sync an exception request with an external system:
- Go to **Vulnerabilities **> **Exceptions**.
- In the table, click the exception request you want to sync.
- Click **Create **<Outegration> **Ticket**.
[]![b153472d-dc0e-4108-9126-96b88ab897a6.png](/downloads/uvm/vulnerability-management/remediate/requesting-exceptions/b153472d-dc0e-4108-9126-96b88ab897a6.png)