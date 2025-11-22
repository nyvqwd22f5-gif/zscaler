# Configuring Entity Unification
Source: https://help.zscaler.com/uvm/configuring-entity-unification
PDF: https://help.zscaler.com/pdf/com/en/1527966.pdf

Ingesting data from multiple sources often leads to duplicate records that represent the same real-world entity. As part of the broader data unification process, entity unification focuses on data normalization by identifying and merging these duplicates to establish a single, trusted source of truth. Admins can create entity unification rules that specify how records are recognized as duplicates and the conditions under which they are merged. This step is especially critical for asset deduplication and serves as a foundation for consistent and reliable data across systems. To learn more, see [What Is Data Unification?](/uvm/what-data-unification)
Configuring Entity Unification Rulesets
An entity’s unification ruleset is a collection of individual rules designed to cluster duplicate entity records into a single merged entity based on specific conditions according to your organization's business logic. Within an entity unification ruleset, you create the individual rules that define how the source data should be clustered into a single entity. For example, you can create a rule to merge all Windows assets that share the same asset hostname into a single asset.
For access to Entity Unification, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Model Management resource. To learn more, see [Creating Custom Roles](/uvm/creating-managing-role-permissions) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#field-unification-permissions)
To create a unification ruleset:
-
Go to **Configure **> **Data Unification **> **Entities**.
[See image.](#nav-unification-entities)
-
Locate the entity you want to create the unification ruleset for, and click **Merge **on the right.
[See image.](#asset-merge-button)
The <Entity> **Merge **page appears.
[]![e458e150-17b8-4f01-bdcb-6042fc8be752.png](/downloads/uvm/configure/data-unification/configuring-field-unification/e458e150-17b8-4f01-bdcb-6042fc8be752.png)
[]**![configure data unification entities](/downloads/uvm/administration/business-logic/unification/configuring-field-unification/configure%20unification%20entities.png)
**
[]**![mceclip2.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip2.png)
**
Configuring Entity Unification Rules
An entity unification ruleset consists of a series of individual rules, each composed of two key components:
- If condition: Defines a filter that determines which records the rule applies to.
- Then action: Specifies that entities should be merged if they have matching values in all selected fields.
To create an entity unification rule:
-
Click **New Rule**, or duplicate an existing rule in the ruleset.
The **Add Merge Rule** drawer appears.
A ruleset containing at least one conditional merging rule must also include a fallback rule, which provides a default merging method for records that don't match any conditions.
- In the **Add Merge Rule** drawer:
- **Name**: Enter a name for the rule.
-
**If**: Define the rule condition that determines which records the rule should apply to.
-
Select a field from the drop-down menu on which the condition should be based.
Available fields to filter by include the selected entity's fields and all fields with a relation to the entity. For example, when creating rules for the **Asset** entity, available fields include **Asset** fields (e.g., **Asset Name**, **Asset ID**), and fields with a relation to the **Asset** entity (e.g., **Application ID**, **Application Name**).
-
Select an operator from the drop-down menu.
The available operators vary depending on the field type, indicated to the left of the field name.
- Enter the value to which the rule should apply (e.g., `Windows`).
- (Optional) Use **AND**/**OR** logic to define compound rules:
- **AND** merges entities only if they meet all conditions in the rule.
- **OR** merges entities if they meet any of the conditions in the rule.
[See image.](#if-condition)
-
In the **Then **section, select at least one field according to which entities that meet your conditions should be merged. All entities with the same value are merged into a single entity.
Available fields to filter by include the selected entity's fields and all fields with a relation to the entity.
When merging entities based on multiple fields, the fields are evaluated using a logical **AND **relationship. This means that entities are merged only if the values in each of the specified fields match (e.g., the values in the **Asset ID** field must match, and the values in the **Asset Type** field must match for the record to merge).
[See image.](#then-action)
- (Recommended) Select the **Exclude Nulls from Merge** checkbox to avoid merging entities with null values in the defined fields.
- Click **Save** to save the rule.
Repeat the process to add as many rules as necessary for the entity. The rules' order of appearance doesn't affect the order of their application. Each data point is evaluated against all rules, even if one rule has already been satisfied.
After saving the rules to the ruleset, save the ruleset to complete the process in one of the following ways:
- Click **Save** to save the ruleset. Rules will apply the next time data is ingested into your account.
-
From the **Save** drop-down menu, click **Save & Run** to save the ruleset and immediately apply the rules to the data in your account.
[See image.](#save-drop-down-menu)
A ruleset that includes at least one conditional merging rule must also include a fallback rule, otherwise the ruleset cannot be saved. The fallback rule specifies a single field to use for merging entities without applying any conditions. It ensures a default merging method is always in place, preventing data loss or conflicts.
Your saved rulesets appear on the Entity Unification page, where you can view, edit, and manage them as needed. To learn more, see [Managing Entity Unification](/uvm/managing-entity-unification).
When Unification Rules Run
Unification rules run when data related to the entity is ingested, directly processed, or might be affected by a different processed entity. Unification rules are most commonly triggered in the following scenarios:
- Data Ingestion: Unification rules are triggered automatically when new data related to an entity is ingested. For example, the Asset entity unification rules run when asset data is ingested.
- Entity Processing: Unification rules run when an entity is directly processed, or indirectly impacted by changes to a related entity. For example, running the Asset Is Crown Jewel field's unification rule can trigger the Ticket Severity unification rule tied to that asset.
- Manual Processing: Unification rules run when you trigger manual processing when splitting or merging tickets, or when clicking Process or Process All on the Data Unification pages.
[]![mceclip5.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip5.png)
[]![then%20merge%20assets%20with%20matching%20values%20in%20the%20following%20fields.png](/downloads/uvm/account-management/account-settings/configuring-zscaler-gateway/then%20merge%20assets%20with%20matching%20values%20in%20the%20following%20fields.png)
[]![mceclip0.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip0.png)