# Managing Workflow Mappings for Events
Source: https://help.zscaler.com/workflow-automation/managing-workflow-mappings-events
PDF: https://help.zscaler.com/pdf/com/en/1500311.pdf

A workflow mapping specifies the events that are associated with the workflow. Events are mapped to workflows based on one or more of the attributes associated with a Business Insights event. The mappings can be basic or advanced based on your requirements. When an event occurs in your organization that includes the mapped attributes, the workflow automatically triggers and performs the actions specified in the workflow.
The mapping statements are evaluated in the order in which you configure them. Workflow Automation uses the first mapping statement that matches with the event attributes. If no statements match an event, then a workflow is not triggered and that event must be evaluated manually.
Prerequisites
Before you configure workflow mappings in the Workflow Automation Admin Portal, ensure that you have configured appropriate workflows on the [Workflows](/workflow-automation/managing-workflows-events) page.
Managing Workflow Mappings
On the Workflow Mapping page, admins can:
- [Add Workflow Mappings](#add-workflow-mappings)
- [View and Edit Workflow Mappings](#heading-edit-workflow-mapping)
- [Delete Workflow Mappings](#heading-delete-workflow-mapping)
- [Arrange Workflow Mapping Rules](#heading-arrange-workflow-mappings)
[]To add a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, click **Add Statement**. A new expanded row with the statement section appears after the last workflow mapping.
[See image.](#Workflow-Mapping-Page-Add-Statement)
You can also access the **Workflow Mappings** page from the [Workflows](/workflow-automation/managing-workflows-events) page by clicking the **Add** icon.
[See image.](#access-mapping-from-workflows-page)
-
In the new row, from the **Workflow Name **drop-down menu, select the name of the workflow that you want to map.
[See image.](#Workflow-Mapping-Page-add-workflow-name)
- Configure a basic or advanced event property mapping for the workflow, as required.
- [Basic Workflow Mapping](#heading-basic-mapping)
- [Advanced Workflow Mapping](#heading-advanced-mapping)
[]To configure a basic workflow mapping:
- In the statement section, from the drop-down menu, select the **Event Type**.
-
[]Add a predicate for the first condition:
- **Property**: From the drop-down menu, select the property. All the attributes in an event transaction are available as properties. A property can be a number, a string, or a Boolean field (True or False).
- [Property List](#Property-List)
- **Operation**: From the drop-down menu, select the operation. The operations vary depending on the property you choose.
- [Operations Table](#Operations-Table)
- **Property value**: Enter or select the value of the property. Some of the properties display values already defined for your organization. For others, you must enter a value for the property.
- Select the function for the condition. If required, select **NOT**. You can only select **OR** or **AND** as the function when you add another predicate.
[See image.](#add-basic-mapping-2)
-
[](Optional) Add another predicate:
- Click **Add Predicate**.** **Another predicate row appears under the first predicate row, and the **AND** function is automatically selected for the condition.
- In the new predicate row, select the appropriate values for the **Property**, **Operation**, and **Property value** fields.
- If required, select the function for the condition. Functions are **NOT**, **OR**, and **AND**.
[See image.](#add-basic-mapping-3)
-
(Optional) Add another condition to the statement:
- Above the predicates that have been defined, click the **Add** icon. Another condition box appears.
- Enter the predicates for the condition. [Add a predicate for the first condition](#step1-predicate) and optionally [add another predicate](#step2-predicate).
- Click **Save**.
[See image.](#basic-mapping-4)
[]The following is a list of the event group mapping properties:
- **Event Group IDs**
- **Event Details**
- **Correlation ID**
- **SaaS Application**
- **Activity Source**
- **Application Name**
- **Plans**
- **Plan Name**
- **User List**
- **Email**
- **Last Active**
- **User ID**
- **User Name**
- **User count by plan name**
- **Plan Name**
- **User Count**
- **Timestamp**
- **Event Details Version**
- **Event Type**
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
-
-
-
| Operation | Description |
| --------- | ----------- |
| **CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for the event type contains the exact value that you entered in the property value field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., Event Details.SaaS Application.Plans [*] Plan Name). |
| **NOT_CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for the event type does not contain the exact value that you entered in the property value field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., Event Details.SaaS Application.Plans [*] Plan Name). |
| **EQUALS**It can be used for the following types of property fields:StringNumber | This operation tests whether the property selected for the event type equals the value that you entered in the property value field. The property field value is not case sensitive. |
| **NOT_EQUALS**It can be used for the following types of property fields:StringNumber | This operation tests whether the property selected for the event type does not equal the value that you entered in the property value field. The property field value is not case sensitive. |
| **LIKE**It can be used for a String type property field. | This operation tests whether the property selected for the event type is like the value that you entered in the property value field. This operation does a partial comparison of the substring. For example, if you select **Event ID** as the property and enter `66e2e81e-fe8a-4d82-b368-3ee70a830146` for the property value, the **LIKE** operation matches the following event IDs:3ee70a830146-4d82-b368-66e2e81e-fe8a77hfcre81e-fe8a-5tr2-b368-3ee70a87614666e2e81e-fe8a-4d82-b09u-4rr70m436146 |
| **EXISTS**It can be used for all types of property fields. | This operation tests whether the property selected exists for the event type. For this type of operation, you do not enter a property value. |
[]To configure an advanced workflow mapping:
- In the statement section, from the drop-down menu, select the **Event Type**.
- Click **Advanced**. The statement section appears, displaying multiple nested conditions.
-
Configure the predicates as required for each condition in the statement. To add another predicate to a condition, click **Add Predicate**. To add another condition to a level in the statement section, click the **Add** icon at that level. To learn how to add a predicate and a condition to a statement, see [Basic Event Mapping](#heading-basic-mapping).
[See image.](#adding-advanced-mapping)
- Click **Save**.
[]To view and edit a workflow mapping:
-
Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
[See image.](#Workflow-Mapping-Page-View-All-Mappings)
- (Optional) On the **Workflow Mappings** page, use the **Search** field to locate the workflow you want to edit the mappings for.
- Next to the workflow you want to edit, click the **Expand** icon. The row expands to display the mappings in the statement section for the workflow.
-
In the statement section, edit any of the existing predicates and conditions for the statement. You can edit the properties, operations for the properties, and property values within the existing predicates and the function for the condition.
[See image.](#edit-workflow-mapping)
- (Optional) Add additional predicates or conditions to the statement. To learn more, see [Adding Workflow Mappings](#add-workflow-mappings).
- Click **Save**.
To delete a predicate or condition within a statement, click the **Delete** icon next to the predicate or condition.
[]To delete a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, click the **Delete** icon next to a workflow. A message appears asking whether you are sure you want to delete this statement.
[See image.](#delete-workflow-mapping)
- Click **OK**.
[]Rules equate to statements in Workflow Automation.
To arrange workflow mapping rules:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, click the down arrow or up arrow next to a workflow to arrange the order in which the rules are processed. Workflow Automation stops processing an event after it finds its first rule match for the event.
[See image.](#arrange-workflow-mapping-rules)
- Click **Save**.
[]![Viewing the Add Statement button on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Add-Statement-Button_0.png)
[]![Viewing the Add Workflow Mapping icon on the Workflows page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflows-PG-Add-Workflow-Mapping-Icon.png)
[]![Selecting the workflow name to map on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Selecting-Workflow-Name.png)
[]![Adding a basic workflow mapping on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Add-Predicate-Button.png)
[]![Adding another predicate to a basic mapping on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Add-New-Predicate-Statement.png)
[]![Adding another condition to a basic mapping on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Add-New-Basic-Statement.png)
[]![Adding an advanced mapping on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Advanced-Statement-Mapping.png)
[]![Viewing the workflow mapping for a workflow on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Edit-Mapping.png)
[]![Viewing all existing mappings on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Initial-View.png)
[]![Viewing the Delete icons on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Delete-Mappings-Icon_0.png)
[]![Viewing the up and down arrows for arranging the workflow mapping rules on the Workflow Mappings page](/downloads/workflow-automation/business-insights/workflows/managing-workflow-mappings-events/WA-BI-Workflow-Mappings-PG-Arrange-Mappings-Updown-Icons_0.png)