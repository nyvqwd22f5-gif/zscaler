# Managing Workflow Mappings for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-workflow-mappings-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1478821.pdf

If you have subscriptions to multiple integrated applications of Workflow Automation such as Data Loss Prevention (DLP), you are prompted to select an application when you log in to the Workflow Automation Admin Portal. Select **Zscaler Digital Experience (ZDX)** to configure automated workflows for ZDX alerts.
A workflow mapping specifies the ZDX alerts that are associated with the workflow. Alerts are mapped to workflows based on one or more of the attributes associated with an alert. The mappings can be simple or more complex based on your requirements. Then, when an alert occurs in your organization that includes those attributes, the workflow automatically triggers and performs the actions specified in the workflow.
Only admins with full access to Workflow Automation can map the workflows.
The mapping statements are evaluated in the order in which you configure and position them in the Workflow Automation Admin Portal. Workflow Automation uses the first statement that matches with alert attributes. If no statements match an alert, then a workflow is not triggered.
On the Workflow Mappings page, you can:
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [View and Edit Workflow Mappings](#heading-edit-workflow-mapping)
- [Delete Workflow Mappings](#heading-delete-workflow-mapping)
- [Arrange Workflow Mapping Rules](#heading-arrange-workflow-mappings)
[]Prerequisites
In the Workflow Automation Admin Portal, ensure that the workflows are added to the [Workflows](/workflow-automation/managing-workflows-zdx-alerts) page.
[]Adding Workflow Mappings
To add a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears.
-
On the **Workflow Mappings** page, click **Add Statement**. A new expanded row appears after the last workflow mapping. The statement section appears within that row.
[See image.](#add-statement-option)
You can also access the **Workflow Mappings** page by clicking the **Add Workflow Mapping** icon in the **Mapping** column on the** Workflows** page.
[See image.](#add-mappings-workflows-page)
-
In the new row, from the **Workflow Name** drop-down menu, select the name of the workflow that you want to map.
[See image.](#add-name-workflow-mappings-new)
- Configure a basic or advanced alert property mapping for the workflow, as required.
- [Basic Workflow Mapping](#heading-basic-mapping)
- [Advanced Workflow Mapping](#heading-advanced-mapping)
[]To configure a basic workflow mapping:
-
[]Add a predicate for the first condition:
- **Property**: From the drop-down menu, select the property. All the attributes associated with an alert transaction are available as properties. A property can be a number or a string.
- [Property List](#property-list)
- **Operation**: From the drop-down menu, select the operation. The operations vary depending on the property you choose.
- [Operations Table](#Operations-Table)
- **Property value**: Enter the value of the property.
- Select the function for the condition. The default function is **NOT**. The functions **OR **and **AND** are only available when you add another predicate.
[See image.](#enter-field-values-new-statement)
-
[](Optional) Add another predicate:
- Click **Add Predicate**.** **A new predicate row appears under the first predicate row.
- In the new row, select the appropriate values for the **Property**, **Operation**, and **Property value** fields.
- If required, select the function for the condition. The default function for the new row is **AND**.
[See image.](#add-predicate-option)
-
(Optional) Add another condition to the statement:
- Above the predicates that have been defined, click the **Add** icon. Another condition box appears.
- Enter the predicates for the condition. [Add a predicate for the first condition](#step1-predicate) and optionally [add another predicate](#step2-predicate).
[See image.](#add-icon-basic-mapping)
- Click **Save**.
[]The following is a list of the properties available for workflow mapping:
- **Alert**
- **Type**
- **Department Count**
- **Geo Location Count**
- **Impacted Device Count**
- **Notification Labels**
- **Notification Label Description**
- **Notification Label Name**
- **OS Version Count**
- **Rule Name**
- **Severity**
- **Total Device Count**
- **Zscaler Location Count**
[]The following table lists the operations and their descriptions:
-
-
-
-
-
-
-
-
-
-
| Operation | Description |
| --------- | ----------- |
| **CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for these types of alerts contains the exact value that you entered in the **property value** field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., Notification Labels[*].Notification Label Name). |
| **NOT_CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for the event type does not contain the exact value that you entered in the property value field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., Notification Labels[*].Notification Label Name). |
| **EQUALS**It can be used for the following types of property fields:StringNumber | This operation tests whether the property selected for these types of alerts equals the value that you entered in the **property value** field. |
| **NOT_EQUALS**It can be used for the following types of property fields:StringNumber | This operation tests whether the property selected for these types of alerts does not equal the value that you entered in the **property value** field. |
| **LIKE**It can be used for a String type property field. | This operation tests whether the property selected for these types of alerts is like the value that you entered in the **property value** field. This operation partially compares the substrings. |
| **EXISTS**It can be used for all types of property fields. | This operation tests whether the property selected exists for these types of alerts. For this type of operation, you do not enter a property value. |
| **LESS_THAN**It can be used for a Number type property field. | This operation tests whether the property selected for these types of alerts is less than the value that you entered in the **property value** field. You can use this operation for numeric properties (e.g., Geo Location Count). |
| **GREATER_THAN**It can be used for a Number type property field. | This operation tests whether the property selected for these types of alerts is greater than the value that you entered in the **property value** field. You can use this operation for numeric properties (e.g., Geo Location Count). |
[]To configure an advanced workflow mapping:
-
Click **Advanced**. The statement section displays multiple nested conditions.
[See image.](#new-statement-advanced-mappings)
- Configure the predicates as required. To add another predicate to the condition, click **Add Predicate**. To learn how to add a predicate and a condition to a statement, see [Basic Workflow Mapping](#heading-basic-mapping).
- Click **Save**.
[]To view and edit a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings **page appears.
-
(Optional) On the **Workflow Mappings** page, use the **Search **field to locate the workflow for which you want to edit the mappings.
[See image.](#view-workflow-mappings)
-
At the end of the row next to the workflow you want to edit, click the **Expand** icon. The row expands to display the mappings in the statement section for the workflow.
[See image.](#expand-statement-icon)
- In the statement section, edit any of the existing predicates and conditions for the statement. You can edit the properties, operations for the properties, and property values within the existing predicates and the function for the condition.
- (Optional) Add additional predicates or conditions to the statement. To learn more, see [Adding Workflow Mappings](#add-workflow-mappings).
- Click **Save**.
To delete a predicate or condition within a statement, click the **Delete** icon next to the predicate or condition.
[]To delete a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears.
-
On the **Workflow Mappings** page, click the **Delete** icon next to a workflow. A message appears asking whether you are sure you want to delete this statement.
[See image.](#delete-icon)
- Click **OK**.
[]Rules equate to statements in Workflow Automation.
To arrange workflow mapping rules:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears.
-
On the **Workflow Mappings** page, click the down arrow or up arrow next to a workflow to arrange the order in which the rules are processed. Workflow Automation stops processing an alert after it finds its first rule match for the alert.
[See image.](#up-down-arrows)
- Click **Save**.
![Viewing the Workflow Mappings page with the Add Statement button highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Add-Statement-Button_0.png)
[]
![Viewing the Workflows page with the Add Workflow Mapping icons highlighted in the Mapping column](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflows-PG-Add-Mapping-Icon.png)
[]
![Viewing the Workflow Mappings page with the Workflow Name highlighted when adding a mapping](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Select-Workflow-Name.png)
[]
![Viewing the Workflow Mappings with a statement added.  When you add a statement to a workflow mapping you select the name of the property, the operator for the property, and the value of the property.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Add-New-Mapping.png)
[]
![Viewing the Workflow Mappings page with an additional predicate added to the statement. To add another predicate to the statement, click the Add Predicate button.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Add-Predicate.png)
[]
![Viewing the Workflow Mappings page with another condition added to the statement. To add another condition to the statement, click the Add icon.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Add-Condition.png)
[]
![Viewing the Workflow Mappings page with an Advanced statement mapping. To add an advanced statement, click the Advanced button.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Add-Advanced-Mapping.png)
[]
![Viewing all the workflows that have been mapped on the Workflow Mappings page.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Initial_0.png)
[]
![Viewing the Workflow Mappings page with the Delete icon highlighted along with the delete confirmation message. After you click the Delete icon, the Are you sure you want to delete this statement? confirmation message appears on the page with Cancel and OK buttons.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Delete-Icon.png)
[]
![Viewing the Workflow Mappings page with a workflow mapping expanded. To expand the workflow mapping, click the Expand Statement icon.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Expand-Statement.png)
[]
![Viewing the Workflow Mappings page with the Up and Down icons highlighted. Click the Up icon or Down icon to rearrange the order of the workflow mappings.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-workflow-mappings-zdx-alerts/WA-ZDX-Workflow-Mappings-PG-Arrange-Mappings-Up-Down-Arrows.png)
[]