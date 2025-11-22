# Understanding Workflows for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/understanding-workflows-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1487451.pdf

Workflow Automation enables you to monitor and remediate Zscaler Digital Experience (ZDX) alerts that have occurred in your organization by configuring different Workflows for ZDX features. You can configure workflows that automatically trigger tickets for ZDX alerts and assign them to the configured assignee to remediate them.
Workflow Configuration
When configuring a workflow, you must select a workflow template to be the basis of the workflow and enter the details for the workflow steps within that workflow template. Depending on the workflow template, there might be one or more steps and different details required for each step, such as notification channel and time to wait for user response. Workflow Automation provides several workflow templates for ZDX alerts.
The following ZDX workflow templates are provided by Workflow Automation:
- ZDX Alert Auto Create Ticket: This template automatically creates tickets using the ticketing system for ZDX alerts.
- ZDX Alert Create and Update Tickets for Location: This template automatically creates and updates the status of the tickets for locations for a ZDX alert based on a shared configuration resource with the ticketing and assignee details for specific locations.
- ZDX Alert Create and Update Tickets for Location Groups: This template automatically creates and updates the status of the tickets for location groups for a ZDX alert based on a shared configuration resource with the ticketing and assignee details for specific location groups.
After the workflow is configured, you specify the alerts that use this workflow by mapping the workflow to one or more of the attributes available in an event transaction. When an alert event occurs in your organization that includes those attributes, the workflow automatically triggers and creates a ticket.
To learn more, see [Managing Workflow Templates for ZDX Alerts ](/workflow-automation/managing-workflow-templates-zdx-alerts), [Managing Workflows for ZDX Alerts](/workflow-automation/managing-workflows-zdx-alerts), and [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts).