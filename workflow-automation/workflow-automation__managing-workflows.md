# Managing Workflows
Source: https://help.zscaler.com/workflow-automation/managing-workflows
PDF: https://help.zscaler.com/pdf/com/en/1455941.pdf

Workflows enable remediation actions to be performed against an incident that occurs in your organization without manual user intervention. You can add a predefined workflow in Workflow Automation based on a workflow template that specifies one or more actions and the order in which those actions are to be performed against an incident, or you can add a custom workflow where you choose and configure the different steps and actions required for the workflow without using a template. In either case, you must then map the workflow to one or more of the attributes available on an incident transaction. Then, when an incident occurs in your organization that contains those attributes, the workflow automatically triggers those actions specified in the workflow.
To learn more, see [Understanding Workflows in Workflow Automation](/zia/understanding-workflows-workflow-automation), [Managing Workflow Templates](/zia/managing-workflow-templates), [Managing Workflow Mappings](/zia/managing-workflow-mappings), [About Incidents](/zia/about-incidents), and [Viewing & Managing Incident Details](/zia/viewing-managing-incident-details).
On the Workflows page in the Workflow Automation Admin Portal, admins can:
- [Add Workflows](#Adding-Workflows)
- [View Workflows](#heading-viewing-workflows)
- [Edit Workflows](#Editing-Workflows)
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [View Workflow Mappings](#heading-view-workflow-mappings)
[]You can add predefined workflows based on a template, or you can add custom workflows that are not based on a template.
- [Adding Predefined Workflows](#heading-add-workflows)
- [Adding Custom Workflows](#heading-adding-custom-workflows)
[]You can add predefined workflows from the **Workflows** page or the **Workflow Templates** page. To learn more, see [Managing Workflow Templates](/zia/managing-workflow-templates).
To add a predefined workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- On the **Workflows** page, click **Add Pre-defined Workflows**. The **Workflow Templates** page appears, listing all the available workflow templates.
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
[][]The custom workflow functionality in Workflow Automation is currently a preliminary version, as indicated by the Beta label on the Add Custom Workflow button. This functionality has been tested, but you might still encounter some issues or errors when using this functionality.
To add a custom workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
-
On the **Workflows** page, click **Add Custom Workflow**. The custom workflow builder page appears, displaying the following:
- The custom workflow name field at the top left of the page. Use this field to name the custom workflow.
- The **Description** button at the top right of the page. Click this button to add a description for the custom workflow.
- The **Tile** pane, which contains the **Notify** tile and the **Close Incident** tile. Use these to configure the custom workflow. A custom workflow can be simple or more complex depending on the requirements for the workflow.
- The custom workflow design area, which is blank except for the **Start** tile. Use this area to create and configure the custom workflow.
[See image.](#custom-workflow-builder-page-initial)
- Click in the custom workflow name field and enter a name for the custom workflow.
- (Optional) Enter a description for the custom workflow. To enter a description:
- Click **Description**. The **Description** dialog window appears.
- Enter a description in the text box.
- Click **OK**.
-
In the custom workflow design area, configure the custom workflow using one or more of the tiles. You can add as many tiles as required for the custom workflow.
A custom workflow must start with the **Start** tile, and then you can add one or more notify tiles and close incident tiles as required. In a custom workflow configuration, you cannot connect a close incident tile immediately to another close incident tile, have two close incident tiles in the same branch of the workflow, or have an escalation to manager notify tile after a close incident tile.
- [Adding Notify Tiles for a User Notification](#heading-adding-notify-tiles-user-notification)
- [Adding Notify Tiles for an Escalation Notification to a Manager](#heading-adding-notify-tiles-escalation-notification-manager)
- [Adding Notify Tiles for an Escalation Notification to an Approver](#heading-adding-notify-tiles-escalation-notification-approver)
- [Adding Notify Tiles for an Escalation Notification to Someone Other than a Manager or an Approver.](#heading-adding-notify-tiles-escalation-notification-other)
- [Adding Close Incident Tiles](#heading-adding-close-incident-tiles)
- [Duplicating Tiles](#duplicating-tiles)
- [Deleting Tiles and Edge Connectors](#heading-deleting-tiles-and-edge-connectors)
-
(Optional) Click **Validate **to have the system** **validate the overall structure and configuration details of the workflow. If there are any validation errors in the workflow, the tiles where there are errors are highlighted in red. Click the Information icon on a tile to get an explanation of the error.
[See image.](#tiles-validation-errors)
- (Optional) Click **Draft**. You can come back later and continue to work on the custom workflow configuration. The status of the custom workflow is **Draft**.
- Click **Publish**. The custom workflow is published, and its status is **Published**. Workflow Automation only uses published custom workflows for incident remediation.
[]To add a notify tile for a user notification:
- In the **Tile** pane, click the **Notify** tile, then drag and drop it in the custom workflow design area. The **Notify** Rich Text Editor appears on the right side of the page.
- In the **Notify** Rich Text Editor, configure the notify tile:
- **Action**: From the drop-down menu, select **Notify**.
- **Actor**: From the drop-down menu, select** User**. This is the person who receives the user notification for the incident.
- **Notification Channel**: From the drop-down menu, select the notification channel by which the user receives the notification. Notification channels are **Email**, **Slack**, and **Teams**.
- **Wait time for response (in minutes)**: (Optional) Enter the number of minutes the workflow waits to receive a response from the user. If you don't enter a wait time, the workflow immediately performs the action without waiting.
- **Notification Template**: (Optional) From the drop-down menu, select the notification template for the user notification. After you select the notification template, the **Survey Template** field and the **Language** field appear.
- **Survey Template**: (Optional) From the drop-down menu, select the survey template for the user notification. If you don't require a user response, do not select a survey template. Even if you do not select a survey template, the user notification still contains the content for the default survey template. If the user wants, they can provide a justification for the incident, but the workflow doesn't depend on it.
- **Language**: From the drop-down menu, select the language in which the user receives the user notification.
- Click **OK**.
- In the custom workflow design area, depending on the workflow, add one or more edge connectors (i.e., connection lines) between this tile and the other existing tiles in the custom workflow design area. The edge connectors link the tiles in the appropriate order for the workflow. To add an edge connector:
- Hover over the small circles on the tile to reveal the connection pointer.
- Drag the connection pointer between the points on two tiles. Depending on the tiles you are connecting and how they were configured, either a connection line appears immediately between the two tiles or a **Justification Condition** dialog window appears that you must configure before the connection line appears.
- If required, enter a justification condition for when the connecting tile action is executed in the workflow. To enter a justification condition, in the **Justification Condition** dialog window, from the **Justification Conditions** drop-down menu, select one of the justification types, or select **Any Response** or **No Response**. The justification types that appear in this field are based on the survey template that you selected when configuring the tile you are connecting from.
- Click **OK**. The connection line appears with the justification condition you selected displayed in a black box on the line.
[See image.](#notify-tile-user-notification)
[]To add a notify tile for an escalation notification to a manager:
- In the **Tile** pane, click the **Notify** tile, then drag and drop it in the custom workflow design area. The **Notify** Rich Text Editor appears on the right side of the page.
- In the **Notify** Rich Text Editor, configure the notify tile:
- **Action**: From the drop-down menu, select **Escalate**.
- **Actor**: From the drop-down menu, select **Manager** as the person to receive the escalation notification. The **If manager doesn't exist** checkbox appears at the bottom of the Rich Text Editor.
- **Notification Channel**: From the drop-down menu, select the notification channel by which the manager receives the notification. Notification channels are **Email**, **Slack**, and **Teams**.
- **Wait time for response (in minutes)**: Enter the number of minutes the workflow waits to receive a response from the user before it sends the escalation notification to the manager.
- **Notification Template**: (Optional) From the drop-down menu, select the notification template for the escalation notification. After you select the notification template, the **Survey Template** field and the **Language** field appear.
- **Survey Template**: (Optional) From the drop-down menu, select the survey template that the manager receives to respond to the escalation notification.
- **Language**: From the drop-down menu, select the language in which the manager receives the escalation notification.
- **If manager doesn't exist**: (Optional) Select this checkbox if you want to specify another approver's email address for the escalation notification if the manager's email address cannot be found. After you select this checkbox, the **Approver Email** field appears immediately below the checkbox.
- **Approver Email**: From the drop-down menu, select the approver's email address. The approver must exist on the [Approvers](/workflow-automation/managing-approvers) page.
- Click **OK**.
- In the custom workflow design area, depending on the workflow, add one or more edge connectors (i.e., connection lines) between this tile and the other existing tiles in the custom workflow design area. The edge connectors link the tiles in the appropriate order for the workflow. To add an edge connector:
- Hover over the small circles on the tile to reveal the connection pointer.
- Drag the connection pointer between the points on two tiles. Depending on the tiles you are connecting and how they were configured, either a connection line appears immediately between the two tiles or a **Justification Condition** dialog window appears that you must configure before the connection line appears.
- If required, enter a justification condition for when the connecting tile action is executed in the workflow. To enter a justification condition, in the **Justification Condition** dialog window, from the **Justification Conditions** drop-down menu, select either one of the justification types, or select **Any Response** or **No Response**. The justification types that appear in this field are based on the survey template that you selected when configuring the tile you are connecting from. If no templates were selected in the from tile, then the **Justification Conditions** dialog window does not appear.
- Click **OK**. The connection line appears with the justification condition you selected displayed in a black box on the line.
[See image.](#notify-tile-escalation-manager)
[]To add a notify tile for an escalation notification to an approver:
- In the **Tile** pane, click the **Notify** tile, then drag and drop it in the custom workflow design area. The **Notify** Rich Text Editor appears on the right side of the page.
- In the **Notify** Rich Text Editor, configure the notify tile:
- **Action**: From the drop-down menu, select **Escalate**.
- **Actor**: From the drop-down menu, select **Approver** as the person to receive the escalation notification. The **Approver Email **field appears below the **Actor** field in the Rich Text Editor.
- **Approver Email**: From the drop-down menu, select the email address of the person to receive the escalation notification. The approver must exist on the [Approvers](/workflow-automation/managing-approvers) page.
- **Notification Channel**: From the drop-down menu, select the notification channel by which this person receives the notification. Notification channels are **Email**, **Slack**, and **Teams**.
- **Wait time for response (in minutes)**: Enter the number of minutes the workflow waits to receive a response from the user before it sends an escalation to this person.
- **Notification Template**: (Optional) From the drop-down menu, select the notification template for the escalation notification. After you select the notification template, the **Survey Template** field and the **Language** field appear.
- **Survey Template**: (Optional) From the drop-down menu, select the survey template that the approver receives to respond to the escalation notification.
- **Language**: From the drop-down menu, select the language in which this person receives the escalation notification.
- Click **OK**.
- In the custom workflow design area, depending on the workflow, add one or more edge connectors (i.e., connection lines) between this tile and the other existing tiles in the custom workflow design area. The edge connectors link the tiles in the appropriate order for the workflow. To add an edge connector:
- Hover over the small circles on the tile to reveal the connection pointer.
- Drag the connection pointer between the points on two tiles. Depending on the tiles you are connecting and how they were configured, either a connection line appears immediately between the two tiles or a **Justification Condition** dialog window appears that you must configure before the connection line appears.
- If required, enter a justification condition for when the connecting tile action is executed in the workflow. To enter a justification condition, in the **Justification Condition** dialog window, from the **Justification Conditions** drop-down menu, select either one of the justification types, or select **Any Response** or **No Response**. The justification types that appear in this field are based on the survey template that you selected when configuring the tile you are connecting from. If no templates were selected in the from tile, then the **Justification Conditions** dialog window does not appear.
- Click **OK**. The connection line appears with the justification condition you selected displayed in a black box on the line.
[See image.](#notify-tile-escalation-approver)
[]To add a notify tile for an escalation notification to someone other than a manager or approver:
- In the **Tile** pane, click the **Notify** tile, then drag and drop it in the custom workflow design area. The **Notify** Rich Text Editor appears on the right side of the page.
- In the **Notify** Rich Text Editor, configure the notify tile:
- **Action**: From the drop-down menu, select **Escalate**.
- **Actor**: From the drop-down menu, select **Other** as the person to receive the escalation notification. The **Email Address **field appears below the **Actor** field in the Rich Text Editor.
- **Email Address**: Enter the email address of the person to receive the escalation notification.
- **Notification Channel**: From the drop-down menu, select the notification channel by which this person receives the notification. Notification channels are **Email**, **Slack**, and **Teams**.
- **Wait time for response (in minutes)**: Enter the number of minutes the workflow waits to receive a response from the user before it sends an escalation to this person.
- **Notification Template**: (Optional) From the drop-down menu, select the notification template for the escalation notification. After you select the notification template, the **Survey Template** field and the **Language** field appear.
- **Survey Template**: (Optional) From the drop-down menu, select the survey template that the person receives to respond to the escalation notification.
- **Language**: From the drop-down menu, select the language in which this person receives the escalation notification.
- Click **OK**.
- In the custom workflow design area, depending on the workflow, add one or more edge connectors (i.e., connection lines) between this tile and the other existing tiles in the custom workflow design area. The edge connectors link the tiles in the appropriate order for the workflow. To add an edge connector:
- Hover over the small circles on the tile to reveal the connection pointer.
- Drag the connection pointer between the points on two tiles. Depending on the tiles you are connecting and how they were configured, either a connection line appears immediately between the two tiles or a **Justification Condition** dialog window appears that you must configure before the connection line appears.
- If required, enter a justification condition for when the connecting tile action is executed in the workflow. To enter a justification condition, in the **Justification Condition** dialog window, from the **Justification Conditions** drop-down menu, select either one of the justification types, or select **Any Response** or **No Response**. The justification types that appear in this field are based on the survey template that you selected when configuring the tile you are connecting from. If no templates were selected in the from tile, then the **Justification Conditions** dialog window does not appear.
- Click **OK**. The connection line appears with the justification condition you selected displayed in a black box on the line.
[See image.](#notify-tile-other-approver)
[]To add a close incident tile:
- In the **Tile** pane, click the **Close Incident** tile, then drag and drop it in the custom workflow design area. The **Close Incident** Rich Text Editor appears on the right side of the page.
- In the **Close Incident** Rich Text Editor, configure the close incident tile:
- **Notes**: Enter notes to associate with the incident when the workflow closes the incident.
- **Resolution Label Name**: From the drop-down menu, select a resolution label name to apply to the incident.
- **Resolution Label Value**: From the drop-down menu, select a resolution label value to apply to the incident. You can only associate one resolution label value with a resolution label name when closing an incident.
- **False Positive**: Select this checkbox to indicate that the incident is a false positive.
- Click **OK**.
- In the custom workflow design area, depending on the workflow, add one or more edge connectors (i.e., connection lines) between this tile and the other existing tiles in the custom workflow design area. The edge connectors link the tiles in the appropriate order for the workflow. To add an edge connector:
- Hover over the small circles on the tile to reveal the connection pointer.
- Drag the connection pointer between the points on two tiles. Depending on the tiles you are connecting and how they were configured, either a connection line appears immediately between the two tiles or a **Justification Condition** dialog window appears that you must configure before the connection line appears.
- If required, enter a justification condition for when the connecting tile action is executed in the workflow. To enter a justification condition, in the **Justification Condition** dialog window, from the **Justification Conditions** drop-down menu, select either one of the justification types, or select **Any Response** or **No Response**. The justification types that appear in this field are based on the survey template that you selected when configuring the tile you are connecting from.
- Click **OK**. The connection line appears with the justification condition you selected displayed in a black box on the line.
[See image.](#close-incident-tile)
[]You can duplicate any tile in the custom workflow design area, except for the start tile.
To duplicate a tile:
-
In the custom workflow design area, hover over a tile that you want to duplicate, and right-click. The **Duplicate** and **Delete** options appear.
[See image.](#duplicate-tiles-image)
- Select **Duplicate**. A duplicate tile appears in the custom workflow design area. The new tile is an exact duplicate of the tile it was duplicated from.
[]You can delete tiles and edge connectors in the custom workflow design area.
- [Deleting Tiles](#deleting-tiles)
- [Deleting Edge Connectors](#delete-edge-connector)
[]To delete a tile:
-
In the custom workflow design area, hover over a tile that you want to delete, and right-click. The **Duplicate** and **Delete** options appear.
[See image.](#delete-tiles-image)
- Select **Delete**. The tile is deleted from the custom workflow design area.
You can also delete a tile by clicking on the tile and then pressing `Backspace`.
[]To delete an edge connector, click the edge connector (i.e., connection line) in the custom workflow design area that you want to delete, and press `Backspace`.
[]Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows. For each workflow, you can view:
- **Workflow Name**: The name of the workflow.
- **Template Name**: The template associated with the workflow. For custom workflows, **Custom Workflow** appears in this field.
- **Status**: The status of the workflow. Statuses are **Draft** and **Published**. Only custom workflows can have a draft status.
[See image.](#Workflows-Page-View-All)
[]You can edit a predefined workflow that was configured using a template, and you can edit a custom workflow that was created without using a template.
- [Editing a Predefined Workflow](#heading-edit-workflows)
- [Editing a Draft Custom Workflow](#heading-edit-draft-custom-workflow)
- [Editing a Published Custom Workflow](#heading-edit-published-custom-workflow)
[]To edit a predefined workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, apply filters** **to locate the workflow you want to edit. To apply filters:
- Click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
- Select a filter and then select the filter values on the right side of the window. As you select the filter values, the number of values selected appears next to the filter. You can select multiple filters and their values. You can include or exclude all the filter values by selecting the **Select All** checkbox. To remove all the selected filters, click **Reset**.
- Click **Apply**.
- (Optional) On the **Workflows** page, use the **Search** field to locate the workflow you want to edit.
-
Click the **Edit **icon in the **Action** column next to a workflow. The **Workflow Settings** page appears, displaying the workflow.
[See image.](#Workflow-Settings-Page-Edit-Workflow)
- On the **Workflow Settings** page, change any of the workflow detail fields except the **Workflow Template** field.
- Click **Save**.
The changes apply to future incidents mapped to the workflow. Current workflow executions are not affected by the changes.
To delete a workflow, click the **Delete **icon in the **Action** column next to a workflow on the **Workflows** page.
[]To edit a draft custom workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, apply filters** **to locate the workflow you want to edit. To apply filters:
- Click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
- Select a filter and then select the filter values on the right side of the window. As you select the filter values, the number of values selected appears next to the filter. You can select multiple filters and their values. You can include or exclude all the filter values by selecting the **Select All** checkbox. To remove all the selected filters, click **Reset**.
- Click **Apply**.
- (Optional) On the **Workflows** page, use the **Search** field to locate the workflow you want to edit.
-
Click the **Edit **icon in the **Action** column next to a draft custom workflow. The custom workflow builder page appears, displaying the custom workflow.
[See image.](#custom-workflow-builder-page-edit-draft-workflow)
-
On the custom workflow page, you can change the workflow description and any of the workflow detail fields in the existing tiles or configure additional tiles for the workflow. You can also change the justification condition on an edge connector. You cannot change the name of the custom workflow. To change the justification condition on an edge connector:
-
Click an edge connector. The **Update Justification Condition** Rich Text Editor appears on the right side of the page.
[See image.](#edit-justification-condition-draft-workflow)
- In the **Justification Conditions** field, delete the existing justification condition and then select another condition from the drop-down menu.
- Click **Ok**.
To learn more, see [Adding Custom Workflows](#add-custom-workflows).
- (Optional) Click **Validate **to have the system** **validate the overall structure and configuration details of the workflow. If there are any validation errors in the workflow, the tiles where there are errors are highlighted in red. Click the Information icon on a tile to get an explanation of the error.
- (Optional) Click **Draft**. You can come back later and continue to work on the workflow configuration. The status of the workflow is **Draft**.
- Click **Publish**. The workflow is published, and its status is **Published**.
To delete a draft custom workflow, click the **Delete **icon in the **Action** column next to a draft custom workflow on the **Workflows** page.
[]To edit a published custom workflow:
- Go to **Workflows** > **Workflows**. The **Workflows** page appears, listing all the workflows.
- (Optional) On the **Workflows** page, apply filters** **to locate the workflow you want to edit. To apply filters:
- Click **Filters**. The **Filters** window appears, displaying all the available filters on the left side of the window.
- Select a filter and then select the filter values on the right side of the window. As you select the filter values, the number of values selected appears next to the filter. You can select multiple filters and their values. You can include or exclude all the filter values by selecting the **Select All** checkbox. To remove all the selected filters, click **Reset**.
- Click **Apply**.
- (Optional) On the **Workflows** page, use the **Search** field to locate the workflow you want to edit.
-
Click the **Edit **icon in the **Action** column next to a published custom workflow. The custom workflow page appears, displaying the custom workflow.
[See image.](#custom-workflow-builder-page-edit-published-workflow)
- On the custom workflow page, you can change the workflow description and any of the workflow detail fields in the existing tiles or configure additional tiles for the workflow. You can also change the justification condition on an edge connector. You cannot change the name of the custom workflow. To change the justification condition on an edge connector:
-
Click an edge connector. The **Update Justification Condition** Rich Text Editor appears on the right side of the page.
[See image.](#edit-justification-condition-published-workflow)
- In the **Justification Conditions** field, delete the existing justification condition and then select another condition from the drop-down menu.
- Click **Ok**.
- (Optional) Click **Validate **to have the system** **validate the overall structure and configuration details of the workflow. If there are any validation errors in the workflow, the tiles where there are errors are highlighted in red.
- Click **Update**. The workflow is updated, and its status remains **Published**.
The changes apply to future incidents mapped to the custom workflow. The changes do not affect current custom workflow executions.
To delete a published custom workflow, click the **Delete **icon in the **Action** column next to a published custom workflow on the **Workflows** page.
[]After you add a predefined workflow or a custom workflow, you must then map the workflow.
A custom workflow must be in a Published state before you can map it.
To add a workflow mapping:
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
[]![Viewing the custom workflow builder page. The page is highlighted to indicate the different areas of the page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-PG-Initial.png)
[]![Video showing how to add a notify tile for a user notification on the custom workflow builder page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Video-Configure-Notify-Tile-User-Notification.gif)
[]![Video showing how to add a notify tile for an escalation notification to a manager on the custom workflow builder page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Video-Configure-Notify-Tile-Escalation-Notification-Manager.gif)
[]![Video showing how to add a notify tile for an escalation notification to an approver on the custom workflow builder page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Video-Configure-Notify-Tile-Escalation-Notification-Approver_1.gif)
[]![Video showing how to add a notify tile for an escalation notification to another person besides a manager or approver on the custom workflow builder page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Video-Configure-Notify-Tile-Escalation-Notification-Other.gif)
[]![Video showing how to add a close incident tile on the custom workflow builder page.](/downloads/workflow-automation/workflows/managing-workflows/WA-Video-Configure-Close-Incident-Tile.gif)
[]![Viewing a custom workflow where the tiles have errors on the custom workflow builder page. The page shows a Close Incident tile connected to an Escalate to Manager notify tile, and then that tile is connected to an Escalate to Approver notify tile.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Validation-Errors.png)
[]![Viewing the available tile options (Duplicate and Delete) for a tile in the custom workflow design area.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Duplicate-Tile.png)
[]![Viewing the available tile options (Duplicate and Delete) for a tile in the custom workflow design area.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Delete-Tile.png)
[]![Viewing the custom workflow builder page when editing a draft custom workflow.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Edit-Draft-Custom-Workflow.png)
[]![Viewing the custom workflow builder page when updating the justification condition for an edge connector between two tiles in a draft custom workflow. One of the edge connectors is highlighted in the workflow and the Update Justification Condition Real Text Editor is displayed.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Update-Justification-Condition-RTE-Draft.png)
[]![Viewing the custom workflow builder page when editing a published custom workflow. ](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Edit-Published-Custom-Workflow.png)
[]![Viewing the custom workflow builder page when updating the justification condition for an edge connector between two tiles in a published custom workflow. One of the edge connectors is highlighted in the workflow and the Update Justification Condition Real Text Editor is displayed.](/downloads/workflow-automation/workflows/managing-workflows/WA-Custom-Workflow-Builder-Page-Update-Justification-Condition-RTE-Published.png)
[]![Workflows Page - Viewing a List of Workflows](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflows-PG-View-All_0.png)
[]![Workflow Settings Page - Editing a Workflow](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Settings-PG-Edit-Workflow_0.png)
[]![Workflow Mappings Page - Adding a Mapping](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflow-Mappings-PG-Add-Mapping_0.png)
[]![Workflows Page - Icons for Viewing Workflow Mapping](/downloads/workflow-automation/workflows/managing-workflows/WA-Workflows-PG-View-Mapping-Icons_0.png)