# Managing Event Group Mappings
Source: https://help.zscaler.com/workflow-automation/managing-event-group-mappings
PDF: https://help.zscaler.com/pdf/com/en/1500291.pdf

An event group mapping specifies the events that are associated with the event group. Event groups are mapped to one or more of the attributes available in an event transaction. These mappings can be basic or advanced to meet your requirements.
Prerequisites
Before you configure event group mappings in the Workflow Automation Admin Portal, ensure that you have configured appropriate event groups on the [Event Groups](/workflow-automation/managing-event-groups) page.
Managing Event Group Mappings
On the Event Group Mappings page, admins can:
- [Add Event Group Mappings](#add-event-group-mappings)
- [Edit Event Group Mappings](#heading-edit-eventgroup-mapping)
- [View Event Group Mappings](#heading-view-eventgroup-mapping)
- [Delete Event Group Mappings](#heading-delete-eventgroup-mapping)
- [Arrange Event Group Mapping Rules](#heading-arrange-eventgroup-mappings)
- [Specify the Default Event Group](#heading-specify-default-eventgroup)
[]To add an event group mapping:
- Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
-
On the **Event Group Mappings** page, click **Add Statement**. A new expanded row with the statement section appears after the last event group mapping.
[See image.](#Add-Statement)
You can also access the **Event Group Mappings** page from the** **[Event Groups](/workflow-automation/managing-event-groups) page by clicking the **Add** icon.
-
In the new row, from the drop-down menu, select the **Event Group** that you want to map.
[See image.](#add-event-group)
- As required, configure a basic or advanced property mapping for the event group.
- [Basic Event Mapping](#heading-basic-mapping)
- [Advanced Event Mapping](#heading-advanced-mapping)
[]To configure a basic event mapping:
- In the statement section, from the **Event Type **drop-down menu, select **Deprovision**.
-
[]Add a predicate for the first condition:
- **Property**: From the drop-down menu, select the property. All the attributes in an event transaction are available as properties. A property can be a number, a string, or a Boolean field (True or False).
- [Property List](#Property-List)
- **Operation**: Select the operation. The operations vary depending on the property you choose.
- [Operations Table](#Operations-Table)
- **Property value**: Enter or select the value of the property. Some of the properties and conditions you select automatically display values defined for your organization. For others, you must enter a value for the property.
- Select the function for the condition. If required, select **NOT**. You can only select **OR** or **AND** as the function when you add another predicate.
[See image.](#basic-mapping-1)
- [](Optional) Add another predicate:
-
Click **Add Predicate. **Another predicate row appears under the first predicate row, and the **AND** function is automatically selected for the condition.
[See image.](#basic-mapping-2)
- In the new predicate row, select the appropriate values for the **Property**, **Operation**, and **Property value** fields.
- Select the function for the condition. Functions are **NOT**, **OR**, and **AND**.
- (Optional) Add another condition to the statement:
-
Above the predicate statements that have been defined, click the **Add** icon. Another condition box appears.
[See image.](#basic-mapping-4)
- Enter the predicates for the condition. [Add a predicate for the first condition](#step1-predicate) and optionally [add another predicate](#step2-predicate).
- Click **Save**.
[]The following is a list of the event group mapping properties:
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
| **LIKE**It can be used for a String type property field. | This operation tests whether the property selected for the event type is like the value that you entered in the property value field. This operation does a partial comparison of the substring. For example, if you select **Event ID** as the property and enter `6e2e81e-fe8a-4d82-b368-3ee70a830146` for the property value, the **LIKE** operation matches the following event IDs:3ee70a830146-4d82-b368-66e2e81e-fe8a77hfcre81e-fe8a-5tr2-b368-3ee70a87614666e2e81e-fe8a-4d82-b09u-4rr70m436146 |
| **EXISTS**It can be used for all types of property fields. | This operation tests whether the property selected exists for the event type. For this type of operation, you do not enter a property value. |
[]To configure an advanced event mapping:
- In the statement section, from the drop-down menu, select the **Event Type**.
- Click **Advanced**. The statement section appears, displaying multiple nested conditions.
-
Configure the predicates as required for each condition in the statement. To add another predicate to a condition, click **Add Predicate**. To add another condition to a certain level in the statement section, click the **Add** icon at that level. To learn how to add a predicate and a condition to a statement, see [Basic Event Mapping](#heading-basic-mapping).
[See image.](#advanced-mapping)
- Click **Save**.
[]To edit an event group mapping:
- Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
- (Optional) On the **Event Group Mappings** page, use the **Search** field to locate the event group you want to edit the mappings for.
-
Next to the event group you want to edit, click the** Expand** icon. The row expands to display the mappings in the statement section for the event group.
[See image.](#Event-Group-Mappings-Page-Edit-Mapping)
- In the statement section, edit any of the existing predicates and conditions for the statement. You can edit the properties, operations for the properties, and property values within the existing predicates and the function for the condition.
- (Optional) Add additional predicates or conditions to the statement. To learn more, see [Adding Event Group Mappings](#add-incident-group-mappings).
- Click **Save**.
To delete a predicate or condition within a statement, click the **Delete** icon next to the predicate or condition.
[]To view event group mappings:
-
Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
[See image.](#view-all-event-group-mappings)
- On the **Event Group Mappings** page, next to an event group, click the **Expand** icon. The row expands to display the mappings in the statement section for that event group.
[]To delete an event group mapping:
- Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
- On the **Event Group Mappings** page, click the **Delete** icon next to an event group. A message appears asking whether you are sure you want to delete this statement.
[See image.](#delete-event-group-mapping)
- Click **OK**.
[]Rules equate to statements in Workflow Automation.
To arrange event group mapping rules:
- Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
- On the **Event Group Mappings** page, click the down arrow or up arrow next to an event group to arrange the order in which the rules are processed within the different event groups. Workflow Automation processes through all the rules for an event transaction. If a transaction matches a rule, the event group associated with the rule is assigned to the transaction. Depending on your rules, a transaction might be assigned to multiple event groups.
[See image.](#arrange-event-mapping-rules)
- Click **Save**.
[]To specify the default event group:
- Go to **Event Group** > **Event Group Mappings**. The **Event Group** **Mappings** page appears, listing the default event group and all the event groups that have been mapped.
- On the **Event Group Mappings** page, from the drop-down menu, select the **Default Event Group**. When Workflow Automation finds no other matches for any other event group mapping for an event, it uses the default event group for the event.
[See image.](#specify-default-event-group-mapping)
- Click **Save**.
[]![Click the Add Statement button on the Event Group Mappings page to add a mapping to an event group](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Add-Statement-But.png)
[]![Select an event group to map from the Event Group drop-down menu on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Select-Event-Group.png)
[]
![Adding a basic mapping for an event group on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Basic-Mapping.png)
[]![Adding another predicate to the basic mapping for an event group on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Basic-Mapping-2.png)
[]![Click the Add icon on the Event Group Mappings page to add another condition to the basic mapping for an event group](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Basic-Mapping-Add-Icon.png)
![Adding an advanced mapping for an event group on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Advanced-Mapping.png)
[]
[]![Editing a mapping on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Event-Group-Mappings.png)
[]![Viewing all the existing event group mappings on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-View-All-Mappings.png)
[]![Click the Delete icon next to an event group on the Event Group Mappings page to delete the mapping](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Delete-Icons.png)
![Click the up arrow or down arrow next to an event group on the Event Group Mappings page to arrange the order of the mapping rules](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Arrange-Order-Icons.png)
[]
![Specifying the default event group mapping on the Event Group Mappings page](/downloads/workflow-automation/business-insights/event-groups/managing-event-group-mappings/WA-BI-Event-Group-Mappings-PG-Specify-Default-Mapping.png)
[]