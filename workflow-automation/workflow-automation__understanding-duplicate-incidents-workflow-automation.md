# Understanding Duplicate Incidents in Workflow Automation
Source: https://help.zscaler.com/workflow-automation/understanding-duplicate-incidents-workflow-automation
PDF: https://help.zscaler.com/pdf/com/en/1486281.pdf

Duplicate incidents can occur in Workflow Automation when a user violates the same Data Loss Prevention (DLP) rule during a two-hour time frame. Duplicate incidents are only applicable to Inline source DLP type incidents. Workflow Automation does not track duplicate incidents for SaaS Security, Email, or Endpoint source DLP type incidents.
To determine whether an incident is a duplicate of another incident, Workflow Automation looks at the following attributes. All of these attributes must be present in the incident:
- Host name from URL
- End user email
- MD5 hash of the content
- File name
It is possible that sites like Gmail can indefinitely send duplicate incidents until the page is refreshed, or the tab is closed. Since Workflow Automation cannot look back indefinitely in time, it only looks back two hours. In this case, Workflow Automation creates a duplicate incident every two hours.
On the Incidents page in the Workflow Automation Admin Portal, you can see the total count of duplicate incidents that have occurred for an incident, and you can also filter the incidents by duplicate incidents. On the Incident Details page, you can use the Duplicate Incidents dialog window to view all the duplicate incidents for a specific incident. To learn more, see [Managing Incidents](/workflow-automation/managing-incidents) and [Viewing & Managing Incident Details](/workflow-automation/viewing-managing-incident-details).