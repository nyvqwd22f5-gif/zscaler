# Managing Workflow Mappings
Source: https://help.zscaler.com/workflow-automation/managing-workflow-mappings
PDF: https://help.zscaler.com/pdf/com/en/1455966.pdf

A workflow mapping specifies the incidents that are associated with the workflow. Only admins with full access to Workflow Automation can map the workflows. Incidents are mapped to workflows, which are based on one or more of the attributes available in an incident transaction. These mappings can be simple or more complex to meet your requirements. Then, when an incident occurs in your organization that contains those attributes, the workflow automatically triggers and performs the actions that the workflow specifies.
The mapping statements are evaluated in the order in which you configure them. Workflow Automation uses the first statement that matches with an incident. If no statements match an incident, then a workflow is not automatically triggered for the incident.
On the Workflow Mappings page in the Workflow Automation Admin Portal, admins can:
- [Add Workflow Mappings](#heading-add-workflow-mappings)
- [Edit Workflow Mappings](#heading-edit-workflow-mapping)
- [View Workflow Mappings](#heading-view-workflow-mapping)
- [Delete Workflow Mappings](#heading-delete-workflow-mapping)
- [Arrange Workflow Mapping Rules](#heading-arrange-workflow-mappings)
[]Prerequisites
In the Workflow Automation Admin Portal, ensure that workflows have been added on the Workflows page. To learn more, see [Managing Workflows](/workflow-automation/managing-workflows).
[]Adding Workflow Mappings
To add a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, at the top left of the page, click **Add Statement**. A new expanded row appears after the last workflow mapping. The statement section appears within that row.
[See image.](#Workflow-Mapping-Page-Add-Statement)
You can also access the **Workflow Mappings** page from the **Workflows** page. In the table, click the **Add Workflows Mapping** icon in the Mapping column for the workflow you want to map.
[See image.](#access-mapping-from-workflows-page)
-
In the new row, from the **Workflow Name **drop-down menu, select the name of the workflow that you want to map.
[See image.](#Workflow-Mapping-Page-add-workflow-name)
- Configure a basic or advanced incident property mapping for the workflow, as required.
- [Basic Workflow Mapping](#heading-basic-mapping)
- [Advanced Workflow Mapping](#heading-advanced-mapping)
[]To configure a basic workflow mapping:
- In the statement section, from the drop-down menu, select the **Source** **DLP Type**. Source DLP types are **Any**, **Email**, **Endpoint**, **Inline**,** **and **SaaS Security**. **Any **appears by default.
-
[]Add a predicate for the first condition:
-
**Property**: From the drop-down menu, select the property. All the attributes in an incident transaction are available as properties. The properties available for selection vary depending on the DLP type you select. A property can be a number, a string, a date, or a Boolean field (True or False).
If you choose user attributes for obfuscation, you cannot map a workflow to these obfuscated attributes (properties). In addition, if a user with permissions to workflow mappings has obfuscation enabled and a workflow was previously mapped using an obfuscation field, then the user cannot edit those existing workflow mappings. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- [Property List](#Property-List)
- **Operation**: From the drop-down menu, select the operation. The operations vary depending on the property you choose.
- [Operations Table](#Operations-Table)
- **Property value**: Enter or select the value for the property. Some of the properties display values for your organization filtered by the source DLP type that you can select (e.g., Severity, Source Actions, and Matching Policies.Rules[*].name). For others, you must enter a value for the property.
- Select the function for the condition. If required, select **NOT**. You can only select **OR** or **AND** as the function when you add another predicate.
[See image.](#add-basic-mapping-1)
- [](Optional) Add another predicate:
-
Click **Add Predicate**.** **Another predicate row appears under the first predicate row, and the **AND** function is automatically selected for the condition.
[See image.](#add-basic-mapping-2)
- In the new predicate row:
- **Property**: From the drop-down menu, select the property.
- **Operation**: From the drop-down menu, select the operation.
- **Property value**: Enter or select the property value for the property.
-
If required, select the function for the condition. Functions are **NOT**, **OR**, and **AND**.
[See image.](#add-basic-mapping-3)
- (Optional) Add another condition to the statement:
-
Above the predicates that have been defined, click the **Add** icon. Another condition box appears.
[See image.](#basic-mapping-4)
- Enter the predicates for the condition. [Add a predicate for the first condition](#step1-predicate) and optionally [add another predicate](#step2-predicate).
- Click **Save**.
[]The following is a list of the workflow mapping properties:
-
**Application Info**
The Application Info properties are available only for Source DLP types of Inline, SaaS Security, and Email.
- [Inline Source DLP Type](#Application-Info-Inline)
- [SaaS Security Source DLP Type](#Application-Info-SaaS-Security)
- [Email Source DLP Type](#Application-Info-Email)
- **Content Info**
- [Inline and Any Source DLP Types](#INLINE-contentInfo)
- [SaaS Security Source DLP Type](#SaaS-Security-API-contentInfo)
- [Endpoint Source DLP Type](#Endpoint-contentInfo)
- [Email Source DLP Type](#Email-contentInfo)
-
**Endpoint Info**
The Endpoint Info properties are available only for Source DLP type Endpoint.
- **Activity Type**
- **Confirm Action**
- **Confirm Justification**
- **Integration Type**
- **Matching Policies**
- [Inline Source DLP Type](#inline-matching-policies)
- [SaaS Security Source DLP Type](#INLINE-SaaS-Security-API-Matching-Policies)
- [Endpoint Source DLP Type](#Endpoint-Matching-Policies)
- [Email Source DLP Type](#Email-Matching-Policies)
- [Any Source DLP Type](#Any-Matching-Policies)
- **Severity** (not available for Source DLP type Email)
- **Source Actions**
- **Source ID**
- **Source SubType**
- **Source Type**
- **User Info**
- **Addresses**
- **Home**
- **Country**
- **PostCode**
- **Region**
- **Other**
- **Country**
- **PostCode**
- **Region**
- **Work**
- **Country**
- **PostCode**
- **Region**
- **Client IP **(only available for Source DLP type Inline)
- **Cost Center**
- **Department**
- **Device Name **(only available for Source DLP type Endpoint)
- **Device OS **(only available for Source DLP type Endpoint)
- **Device Trust Level** (only available for Source DLP type Endpoint)
- **Division**
- **Email**
- **Employ Number**
- **First Name**
- **Groups**
- **Home Country **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Job Title **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Last Name**
- **Location **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Manager**
- **Department**
- **Email**
- **Groups**
- **ID**
- **Name**
- **Organization**
- **Name**
- **Organization**
- **Organization Hierarchy **(only available if you select **CSV **as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Phone Number **(only available if you select **CSV **as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Project IDs **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
-
**Skip Level Managers**
The Skip Level Managers properties are only available if you select **CSV** as your primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page.
- **Department**
- **Email**
- **ID**
- **Name**
- **Status**
- **Termination Date **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **User ID**
- **User Role **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- **Worker Type **(only available if you select **CSV** as the primary user data source on the [Account Settings](/workflow-automation/managing-account-settings) page)
- []**Category**
- **Hostname Or Application**
- **Name**
- **Referrer URL**
- **Url**
- []**Additional Info**
- **SaaS Tenant Name**
- **Category**
- **Current Tag Name**
- **Hostname Or Application**
- **Is Copilot Accessible**
- **Name**
- **Url**
- []**Additional Info**
- **Tenant**
- **Category**
- **Hostname Or Application**
- **Name**
- **Url**
- []**Additional Info**
- **DLP MD5**
- **File Name**
- **File Type**
- []**Additional Info**
- **Attachment Name**
- **Bucket Name**
- **Bucket Owner**
- **Channel Name**
- **Code Repository**
- **Collaboration Scope**
- **Values**
- **DLP MD5**
- **Email Sender**
- **External Collaborators**
- **External Collaborators Groups**
- **External Email Recipients**
- **File ID**
- **File Owner**
- **Internal Collaborators**
- **Internal Collaborators Groups**
- **Internal Email Recipients**
- **Message ID**
- **Object ID**
- **Object Name**
- **Attachments**
- **Document Sub Type**
- **File Category**
- **File Name**
- **File Size**
- **File Type**
- **File**** MD5**
- **Content Location**
- **File Category**
- **File Link Expiry**
- **File Modified By**
- **File Name**
- **File Shared At**
- **File Shared By**
- **File Size**
- **File Type**
- []**Additional Info**
- **Additional Info**
- **Channel**
- **Destination Type**
- **File**** DLP MD5**
- **Expected Action**
- **File Destination Location**
- **File Size**
- **File Source Location**
- **Item Destination Name**
- **Item Source Name**
- **Item Type**
- **Source Type**
- **ZDP Mode**
- **Evidence Url**
- **File Name**
- **File Type**
- []**Additional Info**
- **Message ID**
- **Other Email Recipients**
- **Subject**
- []**Dictionaries**
- **Match Count**
- **Name**
- **Name Match Count**
- **Engines**
- **Name**
- **Rule**
- **Other Rules**
- **Other Rules**
- **Rule Name**
- **Total Other Rules**
- **Rules**
- **Name**
- []**Dictionaries**
- **Match Count**
- **Name**
- **Name Match Count**
- **Engines**
- **Name**
- **Rule**
- **Rules**
- **Name**
- []**Dictionaries**
- **Assigned To Hit Rule**
- **Match Count**
- **Name**
- **Name Match Count**
- **Engines**
- **Assigned To Hit Rule**
- **Name**
- **Rule Expr**
- **Other Rules**
- **Other Rules**
- **Rule ID**
- **Rule Name**
- **Total Other Rules**
- **Rules**
- **Name**
- []**Dictionaries**
- **Assigned To Hit Rule**
- **Match Count**
- **Name**
- **Name Match Count**
- **Engines**
- **Assigned To Hit Rule**
- **Name**
- **Rule**
- **Rules**
- **Action**
- **Files Info**
- **Content Location**
- **File Category**
- **File Name**
- **File Size**
- **File Type**
- **MD5**
- **Name**
- **Other Matched Rules**
- **Recipient**
- **Severity**
- []**Dictionaries**
- **Match Count**
- **Name**
- **Name Match Count**
- **Engines**
- **Name**
- **Rules**
- **Name**
[]The following table lists the operations and their descriptions:
-
-
-
-
-
-
-
[](#operations-example-2)
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
| **AFTER**It can be used for a Date type property field. | This operation tests whether the property selected for these types of incidents is after the value that you entered in the property value field (e.g., userInfo.Termination Date). |
| **BEFORE**It can be used for a Date type property field. | This operation tests whether the property selected for these types of incidents is before the value that you entered in the property value field (e.g., userInfo.Termination Date). |
| **CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for these types of incidents contains the exact value that you entered in the property value field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., matchingPolicies.rules[*].name, matchingPolicies.engines[*].name, and matchingPolicies.dictionaries[*].name).For example, let's say you want to map incidents that have violated a specific Data Loss Prevention (DLP) rule (Block-HIPAA-SSN) to a workflow (Social Security Numbers). But incidents are occurring in your organization that violate multiple DLP rules (Block-HIPAA-MIN, Block-PCI-CC, and Block-HIPAA-SSN) at the same time. Using the CONTAINS operation, you can ensure that those incidents with multiple rule violations that include the Block-HIPAA-SSN rule are mapped to the Social Security Numbers workflow.In the future, to ensure that this type of incident maps to the Social Security Numbers workflow, create the following workflow mapping predicate:Workflow Name = Social Security NumbersProperty = matchingPolicies.rules[*].nameOperation = CONTAINS_EXACTProperty Value = Block-HIPAA-SSN (must contain the full name of the DLP rule)See image. |
| **NOT_CONTAINS_EXACT**It can be used for the following types of property fields:Array of stringsNumberBoolean | This operation tests whether the property selected for these types of incidents does not contain the exact value that you entered in the property value field. You must enter the full value for the property because no partial comparisons are performed. The property field value is not case sensitive. You can use this operation for properties that might include multiple values (e.g., matchingPolicies.rules[*].name, matchingPolicies.engines[*].name, and matchingPolicies.dictionaries[*].name). |
| **EQUALS**It can be used for the following types of property fields:StringNumberDate | This operation tests whether the property selected for these types of incidents equals the value that you entered in the property value field. The property field value is not case sensitive. |
| **NOT_EQUALS**It can be used for the following types of property fields:StringNumberDate | This operation tests whether the property selected for these types of incidents does not equal the value that you entered in the property value field. The property field value is not case sensitive. |
| **IN_IPv4_SUBNET**It can be used for an IP Address type property field. | This operation tests whether the property selected for these types of incidents is in the IPv4 subnet value that you entered in the property value field. You can use this operation for IP address properties. |
| **IN_IPv6_SUBNET**It can be used for an IP Address type property field. | This operation tests whether the property selected for these types of incidents is in the IPv6 subnet value that you entered in the property value field. You can use this operation for IP address properties. |
| **LIKE**It can be used for a String type property field. | This operation tests whether the property selected for these types of incidents is like the value that you entered in the property value field. This operation does a partial comparison of the substring. For example, if you select **userInfo.name** as the property and enter `John` for the property value, the **LIKE** operation matches the following user names:John BrownDavid John SmithSusan JohnJohn |
| **EXISTS**It can be used for all types of property fields. | This operation tests whether the property selected exists for these types of incidents. For this type of operation, you do not enter a property value. |
| **LESS_THAN**It can be used for a Number type property field. | This operation tests whether the property selected for these types of incidents is less than the value that you entered in the property value field. You can use this operation for numeric properties (e.g., userInfo.userId). |
| **GREATER_THAN**It can be used for a Number type property field. | This operation tests whether the property selected for these types of incidents is greater than the value that you entered in the property value field. You can use this operation for numeric properties (e.g., userInfo.userId). |
[]To configure an advanced workflow mapping:
- In the statement section, from the drop-down menu, select the **Source** **DLP Type**. Source DLP types are **Any**, **Email**, **Endpoint**, **Inline**,** **and **SaaS Security**. **Any **appears by default.
-
Click **Advanced**. The statement section reappears, displaying multiple nested conditions.
[See image.](#adding-advanced-mapping)
- Configure the predicates as required for each condition in the statement. To add another predicate to a condition, click **Add Predicate**. To add another condition to a level in the statement section, click the **Add** icon at that level. To learn how to add a predicate and a condition to a statement, see [Basic Workflow Mapping](#heading-basic-mapping).
- Click **Save**.
[]To edit a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
- (Optional) On the **Workflow Mappings** page, use the **Search** field to locate the workflow you want to edit the mappings for.
-
At the end of the row next to the workflow you want to edit, click the **Expand** icon. The row expands to display the mappings in the statement section for the workflow.
[See image.](#edit-workflow-mapping)
- In the statement section, edit any of the existing predicates and conditions for the statement. You can edit the properties, operations for the properties, and property values within the existing predicates and the function for the condition.
- (Optional) Add additional predicates or conditions to the statement. To learn more, see [Adding Workflow Mappings](#add-workflow-mappings).
- Click **Save**.
To delete a predicate or condition within a statement, click the **Delete** icon next to the predicate or condition.
[]To view workflow mappings:
-
Go to **Workflows** > **Workflow Mappings**. The** Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
[See image.](#Workflow-Mapping-Page-View-All-Mappings)
-
On the **Workflow Mappings** page, at the end of the row next to a workflow, click the **Expand** icon. The row expands to display the mappings in the statement section for that workflow.
[See image.](#view-individual-workflow-mapping)
[]To delete a workflow mapping:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, click the **Delete** icon next to a workflow. A message appears asking whether you are sure that you want to delete this statement.
[See image.](#delete-workflow-mapping)
- Click **OK**.
[]Rules equate to statements in Workflow Automation.
To arrange workflow mapping rules:
- Go to **Workflows** > **Workflow Mappings**. The **Workflow** **Mappings** page appears, listing all the workflows that have been mapped.
-
On the **Workflow Mappings** page, click the down arrow or up arrow next to a workflow to arrange the order in which the rules are processed. Workflow Automation stops processing an incident after it finds its first rule match for the incident.
[See image.](#arrange-workflow-mapping-rules)
- Click **Save**.
[]![Viewing the Workflow Mappings Page with the Add Statement Button Highlighted](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-After-Add-Statement_0.png)
[]![Viewing the Workflows Page with the Add Workflows Mapping Icons highlighted on the Table](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflows-PG-Add-Mapping-Icon_0.png)
[]![Viewing the Workflow Mappings Page with the Workflow Name Selected in the Statement Row](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Select-Workflow-Name_0.png)
[]![Example of a Workflow Mapping with a Contains_Exact Operation on the Workflow Mappings Page](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Contains-Exact-Example_0.png)
[]![Viewing the Workflow Mappings Page with a Basic Mapping Added](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Add-Basic-MP_0.png)
[]![Adding Another Predicate to a Basic Mapping on the Workflow Mappings Page. When You Click the Add Predicate Button, a New Row Appears in the Statement Section Under the First Row.](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Add-Basic-MP2_0.png)
[]![Adding Another Predicate to a Basic Mapping on the Workflow Mappings Page](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Add-Basic-MP3_0.png)
[]![Adding Another Condition to a Basic Mapping on the Workflow Mappings Page. The New Condition Row is Highlighted.](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Add-Basic-MP4_0.png)
[]![Adding an Advanced Mapping on the Workflow Mappings Page.](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Add-Adv-Mapping_0.png)
[]![Editing a Mapping on the Workflow Mappings Page](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Edit-Mapping_0.png)
[]![Viewing All Workflow Mappings on the Workflow Mappings Page](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-View-All_0.png)
[]![Viewing the Details for a Specific Workflow Mapping on the Workflow Mappings Page](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-View-One-Mapping_0.png)
[]![Deleting a Workflow Mapping on the Workflow Mappings Page. The Delete Icons are Highlighted Next to Each Mapping.](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Delete-Mappings_0.png)
[]![Arranging Workflow Mapping Rules on the Workflow Mappings Page. The Up and Down Arrow Icons are Highlighted Next to Each Mapping.](/downloads/workflow-automation/workflows/managing-workflow-mappings/WA-Workflow-Mappings-PG-Arrange-Mapping-Rules_0.png)