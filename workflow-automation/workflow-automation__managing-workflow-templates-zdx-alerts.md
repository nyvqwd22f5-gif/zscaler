# Managing Workflow Templates for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-workflow-templates-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1478811.pdf

If you have subscriptions to various integrated applications of Workflow Automation such as Data Loss Prevention (DLP), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select Zscaler Digital Experience (ZDX) to configure automated workflows for ZDX alerts.
Workflow templates are used as the basis for the workflows you add in Workflow Automation. You have access to different predefined ZDX templates to address different alert events that occur in your organization. To add a workflow, you must use one of the predefined templates provided and map them with various criteria to monitor and remediate the alerts. To learn more, see [Understanding Workflows for ZDX Alerts](/workflow-automation/understanding-workflows-zdx-alerts).
The predefined ZDX workflow templates are as follows:
- ZDX Alert Auto Create Ticket
- ZDX Alert Create and Update Tickets for Location
- ZDX Alert Create and Update Tickets for Location Groups
On the Workflow Templates page, you can do the following:
- [View Workflow Templates](#heading-view-workflow-templates)
- [View Workflow Template Definitions](#heading-view-workflow-template-definitions)
- [Add Workflows](#add-workflow)
[]To view workflow templates:
- Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates provided.
- In the **Workflow Templates** page, you can view the following information for each workflow template:
- **Template Name**: The name of the template.
- **Template Description**: The description of the template.
- **Counts**: The number of workflow definitions that have been created using this workflow template.
You can also use the **Search in **field to locate a workflow template.
[See image.](#zdx-predefined-templates)
[]To view workflow template definitions:
- Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates provided by Workflow Automation.
- On the **Workflow Templates** page, click the **View** icon next to the template for which you want to view the definition. The **Workflow Settings** page appears, displaying the workflow definition. The left side of the page displays a graphic representation of the workflow definition. The right side of the page displays the required fields for this workflow definition.
[See image.](#workflow-settings-page)
- Click **Cancel** to return to the **Workflow Templates** page.
[]To add a workflow:
You can also add workflows from the [Workflows](/workflow-automation/managing-workflows-zdx-alerts) page.
- Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates.
- On the **Workflow Templates** page, click the **Add New Workflow Definition** icon next to the template on which you want to base the workflow. The **Workflow Settings** page appears, displaying the workflow definition for that template.
- On the **Workflow Settings** page, enter values in the workflow definition fields required for that particular type of workflow.
[See image.](#entering-field-values)
- Click **Save**. The workflow is added.
To learn more about adding workflows, see [Managing Workflows for ZDX Alerts](/workflow-automation/managing-workflows-zdx-alerts) and [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts).
![Viewing templates on the Workflow Templates page. The templates are listed in a table that has columns for Template Name, Template Description, Counts, and Action.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-templates-zdx-alerts/WA-ZDX-Workflow-Templates-PG-View-All.png)
[]
![Adding required field values for the workflow on the Workflow Settings page. The Workflow Settings page has fields for Workflow Template, Workflow Name, and Description. In addition, it also contains the Ticketing Configuration section.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-templates-zdx-alerts/WA-ZDX-Workflow-Settings-PG-Entering-Values.png)
[]
![Viewing a workflow template definition on the Workflow Settings page for a ZDX template](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-templates-zdx-alerts/WA-ZDX-Workflow-Settings-PG-ZDX-Alert-Auto-Create-Ticket.png)
[]