# Managing Workflow Templates
Source: https://help.zscaler.com/workflow-automation/managing-workflow-templates
PDF: https://help.zscaler.com/pdf/com/en/1455806.pdf

Workflow templates are used as the basis for the workflows you add in Workflow Automation. Workflow Automation provides several different templates that address different scenarios. To add a workflow for your organization, you must select one of the templates provided. Admins use the workflows that are added and mapped to assist them with remediating the incidents that occur in your organization.
Workflow Automation provides the following workflow templates:
- Auto Close Data Protection Incident With Resolution Label
- Auto Close Data Protection Incident
- Auto Create Tickets
- Auto Escalate
- Auto Notify
- Auto Notify User and Close Incident
- Auto Notify User and Concurrently Escalate
- Auto Notify User and Escalate
- Auto Notify User and Escalate to Manager
To learn more, see [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation).
On the Workflow Templates page in the Workflow Automation Admin Portal, admins can:
- [View Workflow Templates](#heading-view-workflow-templates)
- [View Workflow Template Definitions](#heading-view-workflow-template-definitions)
- [Add Workflows](#add-workflow)
[]To view workflow templates:
Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates provided by Workflow Automation. For workflow templates, you can view:
- **Template Name**: The name of the template.
- **Template Description**: The description for the template.
- **Counts**: The number of workflow definitions that have been created using this workflow template.
[See image.](#Workflow-Templates-Page-Image)
[]To view workflow template definitions:
- Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates provided by Workflow Automation.
- On the **Workflow Templates** page, click the **View Workflow Template** icon in the **Action** column next to the template for which you want to view the definition. The **Workflow Settings** page appears, displaying the workflow definition. On the left side of the page, a graphic representation of the workflow definition is displayed. On the right side of the page, the workflow definition fields that are required for this workflow definition are displayed. The graphic and workflow definition fields vary depending on the workflow template that was selected. The **Notification Channel** fields are only available if you have integrated Workflow Automation with Slack or Microsoft Teams. If the **Notification Channel** fields are not available, the notifications are by email. The following image is an example of the Auto Notify User and Escalate template when Workflow Automation has been integrated with Slack or Microsoft Teams.
[See image.](#Workflow-Settings-Page-Image)
- Click **Cancel** to return to the **Workflow Templates** page.
[]To add a workflow:
Workflows can be added from the **Workflow Templates** page or the **Workflows** page.
- Go to **Workflows** > **Workflow Templates**. The **Workflow Templates** page appears, listing all the workflow templates provided by Workflow Automation.
- On the **Workflow Templates** page, click the **Add New Workflow Definition** icon in the **Action** column next to the template on which you want to base the workflow. The **Workflow Settings** page appears, displaying the workflow definition for that template. On the left side of the page, a graphic representation of the workflow definition is displayed.
- On the **Workflow Settings** page, on the right side of the page, enter values in the workflow definition fields required for that particular type of workflow.
- Click **Save**. The workflow is added. The **Workflows** page appears, listing the workflow.
To learn more about adding workflows, see [Managing Workflows](/zia/managing-workflows) and [Managing Workflow Mappings](/zia/managing-workflow-mappings).
[]![Workflow Templates Page](/downloads/workflow-automation/workflows/managing-workflow-templates/WA-Workflow-Templates-PG-View-All.png)
[]![Workflow Settings Page - Viewing workflow template definition](/downloads/workflow-automation/workflows/managing-workflow-templates/WA-Workflow-Templates-PG-View-Workflow-Template-Definition.png)