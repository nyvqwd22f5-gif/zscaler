# Managing Workflows for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-workflows-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1478816.pdf

If you have subscriptions to various integrated applications of Workflow Automation such as Data Loss Prevention (DLP), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select Zscaler Digital Experience (ZDX) to configure automated workflows for ZDX alerts.
Workflows enable you to monitor and notify admins about various alert events that occur in your organization without manual user intervention. An alert is triggered and captured in Workflow Automation when certain events violate the alert rules configured in the ZDX Admin Portal. A workflow is based on a workflow template that creates tickets and assigns them to the desired teams automatically to remediate the issues. You can then map the workflow to one or more attributes available on an alert transaction. Then, when an alert occurs in your organization that contains those attributes, the workflow automatically triggers the actions specified in the workflow.
To learn more, see [Understanding Workflows for ZDX Alerts](/workflow-automation/understanding-workflows-zdx-alerts), [Managing Shared Configuration for ZDX Alerts](/workflow-automation/managing-shared-configuration-zdx-alerts), [Managing Workflow Templates for ZDX Alerts](/workflow-automation/managing-workflow-templates-zdx-alerts), and [Managing Workflow Mappings for ZDX Alerts](/workflow-automation/managing-workflow-mappings-zdx-alerts).
Prerequisites
Ensure that you set Workflow Automation as the **Alert Delivery Method **while configuring** **[ZDX Alert Rules](/zdx/configuring-alert-rule) to manage the alerts through the Workflow Automation Admin Portal.
On the Workflows page, admins can:
- [Add Workflows](#heading-add-workflows)
- [View Workflows](#heading-view-workflows)
- [Edit Workflows](#heading-edit-workflows)
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [View Workflow Mappings](#heading-view-workflow-mappings)
[]You can add workflows from the Workflow Templates page. To learn more, see [Managing Workflow Templates for ZDX Alerts](/workflow-automation/managing-workflow-templates-zdx-alerts).
To add a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, click **Add More**. The **Workflow Templates** page appears, listing all the available workflow templates.
- On the **Workflow Templates** page, next to the template on which you want to base the workflow, click the **Add New Workflow Definition** icon. The **Workflow Settings** page appears, displaying the workflow definition for that template and a graphic representation of the workflow.
- On the **Workflow Settings** page, enter appropriate values in the workflow definition fields.
- [Entering Information for ZDX Alert Auto Create Ticket Template](#enter-zdx-auto-create-template)
- [Entering Information for ZDX Alert Create and Update Tickets for Location](#zdx-alert-create-update-location)
- [Entering Information for ZDX Alert Create and Update Tickets for Location Groups](#zdx-alert-create-update-location-group)
- Click **Save**. The workflow is added.
[]Enter the following information:
- **Workflow Template**: Leave the default value that appears.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Create Ticket **section:
- **Ticketing System**: From the drop-down menu, select the ticketing integration application and its associated tenant ID, which creates the ticket—for example, ServiceNow: snowtest.
- **Assignee**: From the drop-down menu, select the email address for the user to be assigned to the created ticket. The user must be added to the [Integration Users](/workflow-automation/managing-integration-users).
[See image.](#enter-fields-auto-alert)
[]Enter the following information:
- **Workflow Template**: Leave the default value** **that appears.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Ticketing Configuration** section:
- **Default Ticketing System**: From the drop-down menu, select the ticketing integration application and its associated tenant ID, which creates the ticket—for example, ServiceNow:snowtest.
- **Default Ticket Assignee Email**: From the drop-down menu, select the email address for the user to be assigned to the created ticket. The user must be added to the [Integration Users](/workflow-automation/draft-managing-integration-users-zdx).
- **Shared Configuration Resource for Locations**: From the drop-down menu, select a location-ticketing configuration.
[See image.](#zdx-alerts-create-update-location)
[]Enter the following information:
- **Workflow Template**: Leave the default value** **that appears.
- **Workflow Name**: Enter a name for the workflow.
- **Description**: (Optional) Enter a description for the workflow.
- In the **Ticketing Configuration** section:
- **Default Ticketing System**: From the drop-down menu, select the ticketing integration application and its associated tenant ID, which creates the ticket—for example, ServiceNow:snowtest.
- **Default Ticket Assignee Email**: From the drop-down menu, select the email address for the user to be assigned to the created ticket. The user must be added to the [Integration Users](/workflow-automation/draft-managing-integration-users-zdx).
- **Shared Configuration Resource for Location Groups**: From the drop-down menu, select a location group-ticketing configuration.
[See image.](#create-update-location-groups-template-image)
[]To view workflows:
Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows. For workflows, you can view:
- **Workflow Name**: The name of the workflow.
- **Template Name**: The template associated with the workflow.
- **Mapping**: Provides the option to view existing workflow mappings or add new workflow mappings.
[See image.](#view-workflows-page)
[]To edit a workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, use the **Search **field to locate the workflow you want to edit.
- In the **Action** column next to a workflow, click the **Edit** icon. The **Workflow Settings** page appears, displaying the workflow.
[See image.](#edit-workflows-fields)
- On the **Workflow Settings** page, change any of the workflow detail fields except for the **Workflow Template** field.
- Click **Save**.
The changes apply to future alerts mapped to the workflow. They will not affect current workflow executions.
To delete a workflow, on the Workflows page, in the Action column next to a workflow, click the **Delete** icon.
[]To add a workflow mapping:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, in the **Mapping** column next to a workflow, click the **Add Workflows Mapping** icon.
The **Workflow Mappings** page appears, displaying an expanded row for the workflow.
[See image.](#mapping-workflows)
- Add the [workflow mappings](/workflow-automation/managing-workflow-mappings-zdx-alerts) for the workflow. Only admins with full access to Workflow Automation can map a workflow.
[]To view workflow mappings:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, in the **Mapping** column next to a workflow, click the **View** icon.
[See image.](#view-workflow-mappings)
The **Workflow Mappings** page appears, displaying the mapping for the workflow.
![Viewing the configured workflows on the Workflows page. The workflows are listed in table that has columns for Workflow Name, Template Name, Mapping, and Action.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflows-Page-View-All.png)
[]
![Editing the workflow configuration on the Workflow Settings page. On the left side of the page, a graphical representation of the workflow is displayed. On the right side of the page, the fields that define the workflow are displayed.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflow-Settings-PG-View-Workflow-Settings-PG.png)
[]
![Viewing the ZDX Alert Create and Update Tickets for Location workflow definition on the Workflow Settings page](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflow-Settings-PG-Create-Update-Ticket-Location.png)
[]
![Viewing the ZDX Alert Create and Update Tickets for Location Groups workflow definition on the Workflow Settings page](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflow-Settings-PG-Create-Update-Ticket-Location-Groups.png)
[]
![Mapping a workflow on the Workflow Mappings page. A row is expanded on the Workflow Mappings page where you can add the mapping.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflows-Page-Add-Mapping.png)
[]
![Viewing the View icons in the Mapping column on the Workflows page](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflows-Page-View-Mapping.png)
[]
![Viewing the ZDX Alert Auto Create Ticket workflow definition on the Workflow Settings page](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflows-zdx-alerts/WA-ZDX-Workflow-Settings-PG-Auto-Create-Ticket.png)
[]