# Reviewing Exception Requests
Source: https://help.zscaler.com/uvm/reviewing-exception-requests
PDF: https://help.zscaler.com/pdf/com/en/1527631.pdf

If a ticket cannot be remediated by its service level agreement (SLA) date, remediation owners can submit an exception request for an extension. Following submission, a reviewer assesses the request and either approves or denies it based on organizational policies. To learn more, see [Understanding Exception Requests](/uvm/understanding-exception-requests).
For access to review exceptions, your assigned role must include the Read, Create, Edit, Delete, and Audit permissions under the Vulnerabilities App > Exception Operational View resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#review-exceptions-permissions)
To review requests, go to Vulnerabilities > Exceptions. The Exceptions page is your central hub for managing all submitted requests, featuring charts for high-level insights and a detailed exceptions table for managing individual submissions. To view the requests assigned to you, filter by Reviewer Name. You can also add or remove columns, sort data, and apply additional filters to adjust the view to your needs. To learn more, see [Filtering Operational Views](/uvm/filtering-operational-views) and [Creating & Managing Saved Views](/uvm/creating-managing-saved-views).
The Exceptions page features charts that represent key exception insights, helping you to identify trends and patterns and optimize the exception review process.
- [Exceptions by Ticket Severity](#exceptions-by-ticket-severity)
- [Active Tickets by Exception Status Buckets](#active-tickets-by-exception-status-buckets)
- [Exceptions by Requester](#exceptions-by-requester)
The exceptions table, located below the charts, lists all exception requests for your account. Use this table to track and manage submissions throughout the review process. By default, the table displays key information about each request, including its ID, Status, Reason, and Requested SLA. It also shows details from the original ticket, such as Ticket SLA (the ticket's original SLA), Ticket Severity, Ticket Title, and Ticket ID.
If reviewer assignment rules are configured in your account, the assigned reviewers are displayed in the Reviewer column. You can filter this column to display the requests assigned to you.
Auditing Exception Requests
To view the request submission's details, click an exception request. The exception drawer appears, displaying a comprehensive view of the request details.
[See image.](#exception-details-tab)
In the top right of the exception drawer, you can view and modify the status of the request so the requester can keep track of where the request is in the review process.
To audit an exception request:
- Go to **Vulnerabilities **> **Exceptions**.
-
Click the exception request you want to audit.
You can also drill down to the exception request from the **Exception Requests **section on the **Details **tab of the ticket the request was created for.
- Review the request details:
- **Requested SLA**: The SLA date that the requester is asking for.
- **Approved SLA**: This field defaults to the requested SLA but you can modify it to grant a different SLA extension date.
- **Reason and Attachments**: The justification provided by the requester.
- **Original SLA**: The first SLA date assigned to the ticket for which the request was submitted.
- **Current SLA**: The SLA date currently assigned to the ticket, which can be different from the original due to new findings that were added to the ticket or to previously approved exception requests for the ticket.
- Choose an audit decision:
- **Approve**: If the request is valid, click **Approve**. The request status updates to **Approved**, the ticket's SLA is automatically extended, and the ticket is locked to prevent new findings from being added to it.
-
**Approve with a Modified Date**: If you agree with the request but want to grant a different extension date, first change the **Approved SLA **field value, click **Apply Changes**, and then click **Approve**. The exception request is automatically cancelled if the ticket's SLA is extended to a date later than the requested SLA.
[See image.](#apply-changes-button)
- **Deny**: If the request is unjustified, click **Deny**. The status updates to **Denied**, and the ticket's original SLA remains in effect.
Syncing Exceptions with External Systems
If your organization uses an integration (e.g., ServiceNow IRM) to track exceptions, you can sync your request.
To sync an exception request with an external system:
- Go to **Vulnerabilities **> **Exceptions**.
- In the table, click the exception request you want to sync.
- Click **Create **<Outegration> **Ticket**.
[]This chart displays the distribution of exceptions by ticket severity, enabling you to visualize the severity landscape and focus on high-priority exceptions that require immediate attention.
[See image.](#exceptions-by-ticket-severity-chart)
[]![a89659a2-7aae-4b87-ba15-4bb1af45f6c9.png](/downloads/uvm/vulnerability-management/remediate/reviewing-exception-requests/a89659a2-7aae-4b87-ba15-4bb1af45f6c9.png)
[]This chart categorizes active tickets by their exception status. The exception statuses reflect the progression of the review process, giving you a high-level understanding of the overall status of exceptions within your organization.
[See image.](#active-tickets-by-exception-status-buckets-chart)
The displayed statuses vary depending on the configured exception statuses in your account. The default exception statuses include:
- Requested: Exceptions that have been submitted for approval but are pending acknowledgment, indicating that the review process has not yet begun.
- Under Review: Exceptions that have been acknowledged and are actively being evaluated for exception approval.
- Denied: Exceptions that have been rejected, resulting in no change to the original SLA of the associated ticket.
- Cancelled: Exceptions that were automatically cancelled as a result of the ticket's SLA date updating to a later date than the requested extension, effectively ending the exception request process.
- Approved: Exceptions that have been approved, granting an extended SLA for the associated ticket.
[]![2b9531dc-c2b9-48b9-a56f-6bd64b4231b2.png](/downloads/uvm/vulnerability-management/remediate/reviewing-exception-requests/2b9531dc-c2b9-48b9-a56f-6bd64b4231b2.png)
[]This chart displays the distribution of exception requests by individual requester, providing insight into the frequency and volume of requests submitted by each user.
[See image.](#exceptions-by-requester-chart)
[]![exceptions by requester overview chart](/downloads/uvm/vulnerability-management/remediate-uvm/reviewing-exception-requests/exceptions%20by%20requster%20overview%20chart.png)
[]![exception request drawer details tab](/downloads/uvm/vulnerability-management/remediate-uvm/reviewing-exception-requests/exception%20request%20drawer%20details%20tab.png)
[]![161413b4-47ae-423c-af36-4bddd513aa9f.png](/downloads/uvm/vulnerability-management/remediate/reviewing-exception-requests/161413b4-47ae-423c-af36-4bddd513aa9f.png)
[]![a62f20de-8c36-4ea5-96d7-0d4ada27643c.png](/downloads/uvm/vulnerability-management/remediate/reviewing-exception-requests/a62f20de-8c36-4ea5-96d7-0d4ada27643c.png)