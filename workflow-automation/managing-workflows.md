# Managing Workflows
Source: https://help.zscaler.com/workflow-automation/managing-workflows
PDF: https://help.zscaler.com/pdf/com/en/1455941.pdf

Workflows enable remediation actions to be performed against an incident that occurs in your organization without manual user intervention. You add a workflow in Workflow Automation. It is based on a workflow template that specifies one or more actions and the order in which those actions are to be performed against an incident. The workflow is then mapped to one or more of the attributes available on an incident transaction. Then, when an incident occurs in your organization that contains those attributes, the workflow automatically triggers those actions specified in the workflow.
To learn more, see [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation), [Managing Workflow Templates](/zia/managing-workflow-templates), [Managing Workflow Mappings](/zia/managing-workflow-mappings), [About Incidents](/zia/about-incidents), and [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
On the Workflows page in the Workflow Automation Admin Portal, admins can:
- [Add Workflows](#heading-add-workflows)
- [View Workflows](#heading-view-workflows)
- [Edit Workflows](#heading-edit-workflows)
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [View Workflow Mappings](#heading-view-workflow-mappings)
[]You can add workflows from the **Workflows** page or the **Workflow Templates** page. To learn more, see [Managing Workflow Templates](/zia/managing-workflow-templates).
To add a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, click **Add More**. The **Workflow Templates** page appears, listing all the available workflow templates.
- On the **Workflow Templates** page, in the **Action** column, click the **Add New Workflow Definition** icon next to the template on which you want to base the workflow. The **Workflow Settings** page appears, displaying the workflow definition for that template. The left side of the page displays a graphic representation of the workflow definition.
- On the **Workflow Settings** page, on the right side of the page, enter values in the workflow definition fields required for that particular type of workflow.
- [Entering Information for an Auto Close Data Protection Incident](#enter-auto-close-dp-incident-no-res)
- [Entering Information for an Auto Close Data Loss Protection Incident With Resolution Label Type Workflow](#enter-auto-close-dlp-incident)
- [Entering Information for an Auto Create Tickets Type Workflow](#enter-auto-create-tickets-workflow)
- [Entering Information for an Auto Escalate Template Type Workflow](#enter-auto-escalate)
- [Entering Information for an Auto Notify Template Type Workflow](#enter-auto-notify)
- [Entering Information for an Auto Notify User and Close Incident Template Type Workflow](#enter-auto-notify-user-close-incident)
- [Entering Information for an Auto Notify User and Concurrently Escalate Type Workflow](#enter-notify-owner-concurrently-escalate)
- [Entering Information for an Auto Notify User and Escalate Type Workflow](#enter-notify-owner-auto-escalate)
- [Entering Information for an Auto Notify User and Escalate to Manager Type Workflow](#enter-notify-owner-and-escalate-to-manager)
- Click **Save**. The workflow is added. The **Workflows** page appears, listing the workflow.
[]To enter information for an Auto Notify template type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Notify**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Notify User** section:
-
**Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the user notification. Notification channels are **Email**, **Slack**, and** Teams**.
The **Notification Channel** field is only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **field is not available for the workflow, the notification is by email.
- **Language**: From the drop-down menu, select the language in which the notification message is displayed to the user. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
[See image.](#Workflow-Settings-Page-Add-Auto-Notify)
[]To enter information for an Auto Notify User and Close Incident template type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Notify User and Close Incident**.
- **Workflow Name:** Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Notify User** section:
-
**Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the user notification. Notification channels are **Email**, **Slack**, and** Teams**.
The **Notification Channel** field is only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **field is not available for the workflow, the notification is by email.
- **Language**: From the drop-down menu, select the language in which the notification message is displayed to the user. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Wait For User Response** section, in the **Time to wait for user response in seconds** field, enter the number of seconds the workflow waits to receive a response from the user before it closes the incident.
- In the **Close Incident** section:
- **Notes**: Enter notes to associate with the incident when the workflow closes the incident.
- **Resolution Label Name**: From the drop-down menu, select a resolution label name to apply to the incident. After you select a resolution label name, if the label has configured values, the **Resolution** **Label Value **field becomes available. If the label does not have configured values, you cannot enter a label value.
- **Resolution Label Value**: From the drop-down menu, select a label value to apply to the incident. You can only associate one resolution label value with a resolution label name when closing an incident.
- **False Positive**: If the incident is a false positive, select this checkbox.
[See image.](#Workflow-Settings-Page-Auto-Notify-User-Close-Incident)
[]To enter information for an Auto Escalate template type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Escalate**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Escalate To Manager** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the manager receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the manager. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Escalate To Approver** section:
- **Approver Name**:** **From the drop-down menu, select the name of the approver. The approver must exist on the [Approvers](/workflow-automation/managing-approvers) page.
- **Notification Channel**: From the drop-down menu, select the notification channel by which the approver receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the approver. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
[See image.](#Workflow-Settings-Page-Add-Auto-Escalate)
The **Notification Channel** fields are only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **fields are not available for the workflow, the notifications are by email.
[]To enter information for an Auto Notify User and Escalate type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto** **Notify User and Escalate**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Notify User** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the user notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the notification message is displayed to the user. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Wait For User Response** section, in the **Time to wait for user response in seconds** field, enter the number of seconds the workflow waits to receive a response from the user before it escalates the incident to the manager and approver.
- In the **Escalate To Manager** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the manager receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the manager. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Escalate To Approver** section:
- **Approver Name**:** **From the drop-down menu, select the name of the approver. The approver must exist on the [Approvers](/workflow-automation/managing-approvers) page.
- **Notification Channel**: From the drop-down menu, select the notification channel by which the approver receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the approver. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
[See image.](#Workflow-Settings-Page-Add-Notify-User-and-Escalate)
The **Notification Channel** fields are only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **fields are not available for the workflow, the notifications are by email.
[]To enter information for an Auto Notify User and Concurrently Escalate type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto** **Notify User and Concurrently Escalate**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Notify User** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the user notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the notification message is displayed to the user. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Escalate To Manager** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the manager receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the manager. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Escalate To Approver** section:
- **Approver Name**:** **From the drop-down menu, select the name of the approver. The approver must exist on the [Approvers](/workflow-automation/managing-approvers) page.
- **Notification Channel**: From the drop-down menu, select the notification channel by which the approver receives the escalation notification. Notification channels are **Email**,** Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the approver. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
[See image.](#Workflow-Settings-Page-Add-Notify-User-Concurrently-Escalate)
The **Notification Channel** fields are only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **fields are not available for the workflow, the notifications are by email.
[]To enter information for an Auto Notify User and Escalate to Manager type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto** **Notify User and Escalate to Manager**.
- **Workflow Name:** Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Notify User** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the user notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the notification message is displayed to the user. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
- In the **Wait For User Response** section, in the **Time to wait for user response in seconds** field, enter the number of seconds the workflow waits to receive a response from the user before it escalates the incident to the manager.
- In the **Escalate To Manager** section:
- **Notification Channel**: From the drop-down menu, select the notification channel by which the manager receives the escalation notification. Notification channels are **Email**, **Slack**, and** Teams**.
- **Language**: From the drop-down menu, select the language in which the escalation message is displayed to the manager. The languages that appear in the drop-down menu depend on the mapped templates. If you select a language here that is not available in a mapped template set, then Workflow Automation defaults the notifications to English. You can edit this field only after selecting the **Notification Channel** field.
[See image.](#Workflow-Settings-Page-Add-Notify-Owner-and-Escalate-to-manager)
The **Notification Channel** fields are only available for the workflow if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel **fields are not available for the workflow, the notifications are by email.
[]To enter information for an Auto Close Data Protection Incident type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Close Data Protection Incident**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Close Incident** section:
- **Notes**:** **Enter notes to associate with the incident when the workflow closes the incident.
- **False Positive**:** **If the incident is a false positive, select this checkbox.
[See image.](#workflow-settings-page-auto-close-incident-no-label)
[]To enter information for an Auto Close Data Loss Protection Incident With Resolution Label type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Close Data Loss Protection Incident With Resolution Label**.
- **Workflow Name:** Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Close Incident** section:
- **Notes**: Enter notes to associate with the incident when the workflow closes the incident.
- **Resolution Label Name**: From the drop-down menu, select a resolution label name to apply to the incident. After you select a resolution label name, if the label has configured values, the **Resolution** **Label** **Value** field becomes available. If the label does not have configured values, you cannot enter a resolution label value.
- **Resolution Label Value**: From the drop-down menu, select a resolution label value to apply to the incident. You can only associate one resolution label value with a resolution label name when closing an incident.
- **False Positive**: If the incident is a false positive, select this checkbox.
[See image.](#Workflow-Settings-Page-Auto-Close-Data-Protection-Incident)
[]To enter information for an Auto Create Tickets type workflow:
- In the **Workflow** section:
- **Workflow Template**: Leave the default value of **Auto Create Tickets**.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Ticketing Configuration** section:
- **Ticketing Service**: From the drop-down menu, select the ticketing service that creates the ticket. Ticketing services are **JiraCloud** and **ServiceNow**. If you select JiraCloud as the service, the **Jira Project** field appears.
- **Default Ticketing System**: From the drop-down menu, select the tenant ID associated with the ticketing service.
- **Jira Project**: From the drop-down menu, select the Jira project for the ticket. Workflow Automation fetches all the projects from the Jira Software integration as part of the Jira Software application onboarding. To learn more, see [Managing Workflow Automation Integration with Jira Software](/workflow-automation/managing-workflow-automation-integration-jira-software).
- **Default Ticket Assignee Email**: From the drop-down menu, select the email address for the user who will be assigned to the ticket that the workflow creates. The user must be added to the [Integration Users](/workflow-automation/managing-integration-users).
[See image.](#Workflow-Settings-Page-Auto-Create-Tickets-Workflow)
[]To view workflows:
Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows. For workflows, you can view:
- **Workflow Name**: The name of the workflow.
- **Template Name**: The template associated with the workflow.
[See image.](#Workflows-Page-View-All)
[]To edit a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, use the **Search** field to locate the workflow you want to edit.
- Click the **Edit **icon in the **Action** column next to a workflow. The **Workflow Settings** page appears, displaying the workflow.
[See image.](#Workflow-Settings-Page-Edit-Workflow)
- On the **Workflow Settings** page, change any of the workflow detail fields except for the **Workflow Template** field.
- Click **Save**.
The changes apply to future incidents mapped to the workflow. Current workflow executions are not affected by the changes.
To delete a workflow, click the **Delete **icon in the **Action** column next to a workflow on the **Workflows** page.
[]To add a workflow mapping:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, click the **Add **icon in the **Mapping **column next to a workflow.
The **Workflow Mappings** page appears, displaying an expanded row for the workflow.
[See image.](#Workflow-Settings-Page-Add-Workflow-Mapping)
- Add the workflow mapping for the workflow. To learn more, see [Managing Workflow Mappings](/zia/managing-workflow-mappings#add-workflow-mappings).
Only admins with full access to Workflow Automation can map a workflow. You can add workflow mappings to a workflow from the **Workflows** page and the **Workflow Mappings** page.
[]To view workflow mappings:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, in the **Mapping **column, click the **View** icon next to a workflow.
[See image.](#Workflow-Settings-Page-View-Workflow-Mapping)
The **Workflow Mappings** page appears, displaying the mapping for the workflow.
[]![Workflow Settings Page - Add Auto Notify Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Notify-WF_0.png)
[][![Workflow Settings Page - Auto Notify User and Close Incident Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Notify-User-Close-WF_1.png)
](/downloads/zia/workflow-automation/workflows/managing-workflows/ZIA-WA-Workflow-Settings-Page-Add-AutoNotifyCloseIncident.png)
[]![Workflow Settings Page - Adding Auto Escalate Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Escalate-WF_0.png)
[]![Workflow Settings Page - Adding Auto Notify User and Escalate to Manager or Approver Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Notify-User-Escalate-Manager-Approver-WF_0.png)
[]![Workflow Settings Page - Adding Auto Notify User and Concurrently Escalate Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Notify-User-Concurrently-Escalate-Manager-Approver-WF.png)
[]![Workflow Settings Page - Adding Auto Notify User and Escalate to Manager Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Notify-User-Escalate-Manager-WF_0.png)
[][![Workflow Settings Page - Adding Auto Close Data Loss Protection Incident with Resolution Label Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Close-Resolution-Label-WF_0.png)
](/downloads/zia/workflow-automation/workflows/managing-workflows/ZIA-WA-Workflow-Settings-PG-AutoCloseIncidentResolutionLabel.png)
[]![Workflow Settings Page - Add Auto Close Data Protection Incident Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Close-NRL-WF_0.png)
[]![Workflow Settings Page - Adding Auto Create Tickets Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Add-Auto-Create-Tickets-WF_0.png)
[]![Workflows Page - Viewing a List of Workflows](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflows-PG-View-All.png)
[]![Workflow Settings Page - Editing a Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Edit-Workflow_0.png)
[]![Workflow Mappings Page - Adding a Mapping](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Mappings-PG-Add-Mapping_0.png)
[]![Workflows Page - Icons for Viewing Workflow Mapping](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflows-PG-View-Mapping-Icons.png)