# Managing Workflows for Events
Source: https://help.zscaler.com/workflow-automation/managing-workflows-events
PDF: https://help.zscaler.com/pdf/com/en/1500306.pdf

Workflows enable you to automate user notifications and ticket creation to manage various events that occur in your organization without manual user intervention. An event is captured in Workflow Automation when the Business Insights Admin Portal logs a SaaS application license provisioned to a user who has not been active for a long period of time. After you create a workflow based on a workflow template, you can map it to one or more attributes available in an event. When an event is captured for your organization that contains those attributes, the workflow automatically triggers the actions specified in the workflow.
To learn more, see [Managing Workflow Templates for Events](/workflow-automation/managing-workflow-templates-events), [Managing Events](/workflow-automation/managing-events), and [Managing Workflow Mappings for Events](/workflow-automation/managing-workflow-mappings-events).
On the Workflows page, admins can:
- [View Workflows](#heading-view-workflows)
- [Add Workflows](#heading-add-workflows)
- [Edit Workflows](#heading-edit-workflows)
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [View Workflow Mappings](#heading-view-workflow-mappings)
[]You can also add a workflow from the [Workflow Templates](/workflow-automation/managing-workflow-templates-events) page.
To add a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, click **Add More**. The **Workflow Templates** page appears, listing all the available workflow templates.
- On the **Workflow Templates** page, in the **Action** column, click the **Add** icon next to the template. The **Workflow Settings** page appears, displaying the workflow definition for that template.
- On the **Workflow Settings** page, enter values in the workflow definition fields required for that particular type of workflow.
- [Entering Information for Notify Users and Create a Ticket Template Type](#enter-auto-notify)
- Click **Save**. The workflow is added.
[]To enter information for the Notify Users and Create a Ticket template type workflow:
- On the top-right side of the page:
- **Workflow Template**: Leave the default value of that template.
- **Workflow Name:** Enter a name for the workflow.
- **Description**: (Optional) Enter a description of the workflow.
- In the **Notify User** section:
- **Notification Channel**: Select the notification channel by which the user receives the user notification.
- **Language**: Select the language for the notification message displayed to the user. This field can only be edited after selecting the **Notification Channel** field.
- In the **Wait For User Response** section, in the **Time to wait for user response for hours **field**, enter** the maximum time limit in hours for the user to respond to the event notification.
- In the **Create Ticket** section:
- **Assignee Email**: Enter the email address for the user to assign the created ticket. The user must be added to the **Integration Users** page.
- **Ticketing System**: Select the ticketing integration application and its associated tenant ID, which creates the ticket. For example, **ServiceNow: snowtest**.
[See image.](#Workflow-Settings-Page-Add-Auto-Notify)
[]To view workflows:
Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows. For workflows, you can view:
- **Workflow Name**: The name of the workflow.
- **Template Name**: The template associated with the workflow.
[See image.](#Workflows-Page-View-All)
[]To edit a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, use the **Search** field to locate the workflow you want to edit.
- In the **Action** column, click the **Edit **icon next to a workflow. The **Workflow Settings** page appears, displaying the workflow.
-
On the **Workflow Settings** page, change any of the workflow detail fields that were previously added when creating the workflow, except for the **Workflow Template** field.
[See image.](#Workflow-Settings-Page-Edit-Workflow)
- Click **Save**.
The changes made apply to future events mapped to the workflow. Current workflow executions are not affected by the changes.
To delete a workflow, click the **Delete **icon next to a workflow in the **Action** column.
[]To add a workflow mapping:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
-
On the **Workflows** page, in the **Mapping** column next to a workflow, click the **Add **icon.
[See image.](#add-mappings-icon)
The **Workflow Mappings** page appears, displaying an expanded row for the workflow.
-
Add the workflow mapping for the workflow. To learn more, see [Managing Workflow Mappings for Events](/workflow-automation/managing-workflow-mappings-events).
[See image.](#Workflow-Settings-Page-Add-Workflow-Mapping)
Only admins with full access to Workflow Automation can map a workflow. Workflow mappings can be added to a workflow from the **Workflows** page and the [Workflow Mappings](/workflow-automation/managing-workflow-mappings-events) page.
[]To view workflow mappings:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
-
On the **Workflows** page, in the **Mapping** column next to a workflow, click the **View** icon.
[See image.](#Workflow-Settings-Page-View-Workflow-Mapping)
The **Workflow Mappings** page appears, displaying the mapping for the workflow.
![Viewing the Add Workflow Mappings icon on the Workflows page](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflows-PG-Add-Mapping-Icon.png)
[]
[]![Adding the Notify Users and Create a Ticket workflow on the Workflow Settings page](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflow-Settings-PG-Add-Workflow-Def.png)
[]![Viewing the list of workflows on the Workflows page. The Workflows are listed in a table that has columns for Workflow Name, Template Name, Mapping, and Action.](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflows-PG-Main-Page.png)
[]![Editing a workflow on the Workflow Settings page](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflow-Settings-PG-Adding-Workflow-Definition.png)
[]![Adding a workflow mapping on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflow-Mappings-PG.png)
[]![Viewing the View Workflow Mappings icons on the Workflows page](/downloads/workflow-automation/business-insights/workflows/managing-workflows-events/WA-BI-Workflows-PG-View-Mapping-Icon.png)