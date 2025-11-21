# Configuring Field Unification
Source: https://help.zscaler.com/uvm/configuring-field-unification
PDF: https://help.zscaler.com/pdf/com/en/1527981.pdf

Ingesting data from various sources often requires merging duplicate records for the same entity into a single unified record. Following deduplication through [entity unification](/uvm/configuring-entity-unification), the next step is reconciling attribute conflicts and subsequently cleansing and enriching the data. The platform's unique unification capabilities ultimately transform your data into a single, trusted source of truth.
On initial account setup, all deduplicated fields in your account are populated with [default values](/uvm/attribute-reconciliation-default-functions), implementing unification best practices. These default values can then be customized to increase workflow efficiency and reduce time to remediate, allowing your team to focus on resolving issues quickly and effectively.
The following are two common use cases for configuring field unification:
- Classifying assignment and ownership fields: Define unique asset ownership and ticket assignment rules that reflect your organization's business logic. Relevant fields to configure include Asset Owner ID and Ticket Assignee.
- Enriching field attributes (using tags): Automate the extraction of relevant attributes from tags, which are often manually entered, lack standardization, and are not easily accessible from all sources. Relevant fields to configure incdlue Asset Is Crown Jewel and Asset Business Criticality.
Configuring Field Unification Rulesets
A field's unification ruleset is a collection of individual rules designed to populate the field with customized values based on specific conditions according to your organization's business logic. Within a field unification ruleset, you create individual rules that define how the source values should be reconciled into a single value under different conditions. For example, you can create a rule to populate the Ticket Assignee field based on the Asset Type value of the assets in the ticket.
For access to Field Unification, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Model Management resource. To learn more, see [Creating Custom Roles](/uvm/creating-managing-role-permissions) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#field-unification-permissions)
[]![e458e150-17b8-4f01-bdcb-6042fc8be752.png](/downloads/uvm/configure/data-unification/configuring-field-unification/e458e150-17b8-4f01-bdcb-6042fc8be752.png)
To create a unification ruleset:
-
Go to **Configure** > **Data Unification** > **Fields**.
[See image.](#nav-unification-fields)
- Click **New Rule Set** located at the top right of the page.
-
Select the field for which you want to create a new ruleset.
[See image.](#new-rulset-fields)
- At the top left of the screen, select a **Rule Set Type**:
- **Conditions (Default)**: This ruleset type is the default, and it's available for fields of all entity types. Using conditions, you can define how to transform and enrich field values.
-
**Priority By Source**: This ruleset type is designed to allow attribute reconciliation to be prioritized by source in place of the default logic. Using this type, you can specify the order of source precedence, so that field values from higher priority sources take precedence over those from lower priority sources. For example, you can prioritize your Configuration Management Database (CMDB) as the highest priority source to populate the Asset Owner ID field.
This ruleset type is not available for Ticket fields.
[]**![configure data unification fields](/downloads/uvm/administration/business-logic/unification/configuring-entity-unification/configure%20unification%20field.png)
**
[]**![78d0828d-3836-4bfe-bd0f-98fa3e14deac.png](/downloads/uvm/configure/data-unification/configuring-field-unification/78d0828d-3836-4bfe-bd0f-98fa3e14deac.png)
**
Configuring Field Unification Rules
Every ruleset includes a rule that specifies a default fallback value with no conditional logic. This ensures that there is always a default method for populating the field, preventing potential data conflicts or loss. The fallback rule can be edited, but can't be removed or deleted.
To set the ticket Assignee field to No Assignee in the ticket drawer when no other assignment rules apply, set the default rule value to Empty.
[See image.](#ticket-no-assignee)
In addition to the default rule, unification rulesets consist of a series of individual conditional rules, each composed of two key components:
-
If condition: Defines a filter that determines which records the rule applies to. The IF condition can be configured as structured Conditions or as an Expression.
[See image.](#condition-expression)
- Set <field> as: Specifies the value to populate the field with, for fields that satisfy the rule's IF conditions. The field value can be set with a Value, Field, SmartText, Expression, or Empty.
To create a field unification rule:
-
In the ruleset you previously created, click **New Rule**, or clone an existing rule in the ruleset.
The **Create Unification Rule** drawer appears.
- In the **Create Unification Rule **drawer:
- **Name**: Enter a unique name for the rule.
- **IF**: Define the rule condition that determines which records the rule should apply to. For advanced filtering, use **Expressions**.
- Select a field that the condition should be based on. Available fields include entity fields and all fields with a relation to the entity.
- Select an operator (e.g., **Equals**, **Contains**). Available operators vary depending on the field type, indicated to the left of the field name.
- Enter the value that the rule should apply to. Field unification conditions are not case sensitive.
- (Optional) Use **AND**/**OR** logic to define compound rules.
- **AND** populates the field only if the field meets all conditions in the rule.
- **OR** populates the field if the field meets any of the conditions in the rule.
-
**Set <field> as**: Select one of the following methods to set the field's value. Available options vary depending on the field type.
- [Value](#set-value-as-value)
- [Field](#set-value-as-field)
- [SmartText](#set-value-as-smarttext)
- [Expression](#set-value-as-expression)
- [Empty](#set-value-as-empty)
The configured value populates the field when the rule's conditions are met.
-
Click **Preview** to test the rule. Use the filters and field selection to refine the previewed data and ensure the rule functions correctly.
[See image.](#preview-field-unification)
- Click **Add** to add the rule to the ruleset.
[]![e19af72c-601a-4fe5-abe4-5f10df94791b.png](/downloads/uvm/configure/data-unification/configuring-field-unification/e19af72c-601a-4fe5-abe4-5f10df94791b.png)
[]![50acdd79-1078-4ada-a4bc-0450d7fbf3ba.png](/downloads/uvm/configure/data-unification/configuring-field-unification/50acdd79-1078-4ada-a4bc-0450d7fbf3ba.png)
[]Set the field value to one of the options in the drop-down menu (i.e., **True**, **False**, or **Not defined**). For example, when configuring field unification for the Asset Is Crown Jewel field, in the **Set Asset Is Crown Jewel as **section, you can set the value to **True **if the Asset Owner ID includes Management or if its Tags include Crown Jewel, or you can set it to **False **if it doesn't.
[See image.](#set-value-as-value-radio)
The **Value **option is available for Boolean fields only.
[]![0af97ba2-fdc3-4bd1-8dbe-0839d6f1e49a.png](/downloads/uvm/configure/data-unification/configuring-field-unification/0af97ba2-fdc3-4bd1-8dbe-0839d6f1e49a.png)
[]Select a field from the drop-down menu to populate the value of the current field when the rule conditions are met. For example, you can populate the Ticket Assignee field with the value of Asset Owner ID if Application Name contains Adobe.
[See image.](#set-value-as-field-radio)
[]![c2261796-e647-4261-be29-528117dbdce2.png](/downloads/uvm/configure/data-unification/configuring-field-unification/c2261796-e647-4261-be29-528117dbdce2.png)
[]Use a combination of free text and field names as tokens to set the field's value. For example, when populating the Ticket Assignee field, you can dynamically enter the name of the team based on the business application associated with the ticket.
To add fields as tokens, enter the field name within double curly brackets. The field's display name automatically translates to the field's** **system name (e.g., Application Name appears as `application.name`).
[See image.](#set-value-as-smarttext-radio)
The **SmartText **option is available for Text fields only.
[]![4beffd59-e680-40f8-a2e6-be84c108fb05.png](/downloads/uvm/configure/data-unification/configuring-field-unification/4beffd59-e680-40f8-a2e6-be84c108fb05.png)
[]Set a field's value using an expression to apply custom value transformations and standardize formats. For example, extract asset tags to populate Asset Business Criticality and Asset Is Crown Jewel fields.
Supported functions, operators, and references, along with examples, are displayed when you click the Expression text box.
[See image.](#expression-dialog)
[]![unification expression functions](/downloads/uvm/administration/business-logic/unification/configuring-field-unification/unification%20expression%20functions.png)
[]Select this option to leave a field blank when the rule conditions are met.
The **Empty **option is commonly used for the Ticket Assignee field, to ensure that the field remains unpopulated if no rule conditions are satisfied. Empty Ticket Assignee values are automatically populated with the No Assignee value, which helps identify the need for manual assignment.
[]![f82a7105-67fe-4ece-bfcc-83936eae61f5.png](/downloads/uvm/configure/data-unification/configuring-field-unification/f82a7105-67fe-4ece-bfcc-83936eae61f5.png)
Save & Run Ruleset
After saving the rules to the ruleset, save the ruleset to complete the process in one of the following ways:
- Click **Save** to save the rule set. Rules will apply the next time data is ingested into your account.
-
From the **Save** drop-down menu, click **Save & Run** to save the ruleset and immediately rerun the rules for the current entity and all entities with a relation to the current entity. A full rerun of all entities occurs on the next data run.
[See image.](#save-drop-down-menu)
Alternatively, you can process entities manually. First, save the ruleset; this redirects you to the Data Unification - Fields page. On the Data Unification - Fields page, click **Process **next to individual entities, or click **Process All **in the top-right corner to process all entities.
When Unification Rules Run
Unification rules run when data related to the entity is ingested, directly processed, or might be affected by a different processed entity. Unification rules are most commonly triggered in the following scenarios:
- Data Ingestion: Unification rules are triggered automatically when new data related to an entity is ingested. For example, the Asset entity unification rules run when asset data is ingested.
- Entity Processing: Unification rules run when an entity is directly processed, or indirectly impacted by changes to a related entity. For example, running the Asset Is Crown Jewel field's unification rule can trigger the Ticket Severity unification rule tied to that asset.
- Manual Processing: Unification rules run when you trigger manual processing when splitting or merging tickets, or when clicking Process or Process All on the Data Unification pages.
[]![7f0ce54e-c950-49c4-ab6b-1a814668ab71.png](/downloads/uvm/configure/data-unification/configuring-field-unification/7f0ce54e-c950-49c4-ab6b-1a814668ab71.png)
Rule Order in Field Unification Ruleset
The rules within a field unification ruleset are run sequentially by their order of appearance. A field is unified according to the first rule that applies to it. If no rule applies to the field, it's unified by the default fallback rule. You can adjust the rule order by dragging them to your desired location. After rearranging the rule order, click **Save **to apply your changes.
[See image.](#reorder-rules)
[]![0a8d1c8b-1a05-4174-859e-28d9283359e0.png](/downloads/uvm/configure/data-unification/configuring-field-unification/0a8d1c8b-1a05-4174-859e-28d9283359e0.png)
Field Unification Examples
The following examples illustrate different types of field unification rules you can create to resolve attribute conflicts and support data cleansing and enrichment. Each example highlights a specific use case and demonstrates rule configurations to address it.
- [Asset Owner ID](#example-asset-owner-id)
- [Ticket Assignee](#example-ticket-assignee)
- [Asset Business Criticality](#example-asset-business-criticality)
[]Associate assets with their owners by configuring asset ownership rules. You can configure a ruleset for the Asset Owner ID field and use Priority By Source to set the order of source precedence for your asset sources, so the most trusted sources take priority.
[See image.](#example-priority-by-source)
For example, if your CMDB (e.g., ServiceNow) is the most reliable source for asset owner information, you can prioritize its data over other sources, ensuring that the owner values it reports are used.
[]![89d04b60-272f-4283-acda-d7b2eec9a2e4.png](/downloads/uvm/configure/data-unification/configuring-field-unification/89d04b60-272f-4283-acda-d7b2eec9a2e4.png)
[]Automate ticket assignment by routing tickets to the correct owner or team based on the assets they contain. You can create rules for the Ticket Assignee field that define your organization's assignment logic.
The following rules show examples for the Ticket Assignee field.
Rule 1: Network Assets
Create a rule to automatically assign tickets requiring expertise in Firewalls and Load Balancers to the Networking Team.
[See image.](#example-networking-team)
Rule Configuration: If the Assets in the ticket include Firewalls or Load Balancers (Conditions), then assign the ticket to the Networking Team (Action).
This translates to the rule logic:
- IF Asset Type = `Firewall` OR Asset Type = `Load Balancer`
- THEN Set Ticket Assignee as `Networking Team`
Rule 2: Cloud Owners
Create a rule to automatically assign tickets related to Cloud Assets to their respective individual service owners.
[See image.](#example-cloud-owners)
Rule Configuration: If the Asset is a Cloud Asset (Condition), then assign the ticket to the asset owner using the value in the Asset Owner ID field (Action).
This translates to the rule logic:
- IF Asset is Cloud Asset = `True` AND Asset Application Name Is Empty
- THEN Set Ticket Assignee as Asset Owner ID (dynamically retrieved from the Asset Owner ID field)
[]![f997495b-a525-47b5-9de6-f03b6459a530.png](/downloads/uvm/configure/data-unification/configuring-field-unification/f997495b-a525-47b5-9de6-f03b6459a530.png)
[]![d6d81764-6173-42f3-a04b-5af95c9137af.png](/downloads/uvm/configure/data-unification/configuring-field-unification/d6d81764-6173-42f3-a04b-5af95c9137af.png)
[]Isolate and extract the criticality level of your assets from asset tags to inform the risk level of each asset in your organization. You can create rules for the Asset Business Criticality field using an Expression to extract criticality information from Asset Tags.
[See image.](#example-expression-criticality-from-tags)
Rule Configuration: If the Asset Tags contain the criticality tag (Condition), then extract the criticality tag value to populate the Asset Business Criticality field (Action).
This translates to the rule logic:
- IF Asset Tags Contains (Any) criticality
-
THEN Set Asset Business Criticality as Expression:
`extract(extract(textJoin("@",{{asset.tags}}),"CRITICALITY: ", 1),"@",0)`
So if the Asset Tags field is populated by:
`[" CRITICALITY: CRITICAL","CROWN JEWEL: Yes"]`
The expression works by:
- `textJoin`: Joining all asset tags into a single string separated by the `@` delimiter.
- Inner `extract`: Finding the first occurrence of the criticality tag within that string.
- Outer `extract`: Extracting the value associated with the criticality tag, stopping at the first `@` delimiter (`0`).
[]![1b5c626b-edb8-4257-b56c-6b746a642102.png](/downloads/uvm/configure/data-unification/configuring-field-unification/1b5c626b-edb8-4257-b56c-6b746a642102.png)