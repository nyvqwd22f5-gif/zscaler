# Understanding Exception Requests
Source: https://help.zscaler.com/uvm/understanding-exception-requests
PDF: https://help.zscaler.com/pdf/com/en/1527696.pdf

Exception requests are a critical component of vulnerability management. They provide a structured process for organizations to temporarily exempt vulnerabilities or remediation tasks from published security policies, standards, or guidelines when remediation cannot be completed within designated timeframes.
Common Use Cases for Requesting Exceptions
Common use cases for extending vulnerability remediation timelines include:
- Technical or Operational Limitations: The vulnerability resides in legacy systems, custom applications, or critical infrastructure where applying a fix would introduce significant instability, is technically unfeasible without substantial re-engineering, or requires extensive testing cycles that exceed standard remediation windows.
- Unavailable Fix: A patch, fix, or viable workaround is currently unavailable from the vendor or internal development teams.
- Unacceptable Business Impact: Remediation efforts (e.g., system downtime, major reconfigurations, extensive testing) would severely disrupt critical business operations, impact revenue, or compromise essential services beyond an acceptable level.
Key Roles in the Exception Request Process
The following primary personas are involved in the exception request process in vulnerability management:
- Exceptions Manager: Configures exceptions settings, defines user permissions for requesting exceptions, and sets rules to assign exception reviewers. To learn more, see [Managing Exception Settings](/uvm/managing-exception-settings).
- Requester: Typically a remediation owner who is assigned remediation tasks that might require a timeline extension. They are responsible for initiating the exception request, providing justification, and submitting necessary supporting evidence for review. To learn more, see [Requesting Exceptions](/uvm/requesting-exceptions).
- Reviewer: Designated reviewers who assess exception requests. They evaluate the associated risks, verify the justification and evidence, and make a decision to approve or deny the request based on organizational policies and risk acceptance criteria. To learn more, see [Reviewing Exception Requests](/uvm/reviewing-exception-requests).
Exception Request Lifecycle
The Zscaler Unified Vulnerability Management (UVM) exception lifecycle starts with the submission of an exception request, which is routed for review using the configured review process in the account's exception settings. The review process results in either approval or denial. Approved exceptions are managed and monitored on the Exceptions page.
Requesting an Exception
The exception lifecycle begins when a remediation owner determines they cannot meet the deadline for an assigned remediation ticket. They submit an exception request through the Exception Request form in the ticket that requires an extension, providing a detailed justification, supporting evidence, and a proposed new remediation date.
A new exception is created in the Exceptions View with the Requested status. This exception is automatically linked to the source remediation ticket that is awaiting assessment.
Reviewing an Exception Request
The system routes the requested exception to the appropriate reviewer based on configured assignment rules. The reviewer assesses the request against organizational policies and risk acceptance criteria, evaluating the business justification, technical feasibility, and potential risk exposure before making a final decision to approve or deny the request. The decision immediately updates the exception's status and dictates the next steps:
- If Approved: The exception's status changes to Approved, and the due date on the associated remediation ticket is automatically deferred to the new date.
- If Denied: The exception's status changes to Denied. The request is rejected, and the original remediation timeline for the ticket remains in effect.
Tracking an Exception Request
The status of the exception request can be tracked in two locations to ensure ongoing visibility for all parties:
- Exceptions View: A centralized dashboard to view and manage all exception requests across the organization.
- Ticket's Details Tab: All exception requests linked to the ticket appear on the ticket's Details tab, displaying the exception status and the relevant exception updates.