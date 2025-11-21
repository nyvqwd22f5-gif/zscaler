# Managing Field Unification
Source: https://help.zscaler.com/uvm/managing-field-unification
PDF: https://help.zscaler.com/pdf/com/en/1528001.pdf

After configuring field unification, you can manage unification rulesets and the rules they contain.
For access to Field Unification, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Model Management resource. To learn more, see [Creating Custom Roles](/uvm/creating-managing-role-permissions) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#field-unification-permissions)
Managing Field Unification Rulesets
When managing field unification rulesets, you can perform the following actions:
- [Process Entity Rulesets](#process-entity-rulesets)
- [Edit Rulesets](#edit-ruleset)
- [Copy/Paste Rulesets](#copy-paste-rulesets)
- [Delete Rulesets](#delete-rulesets)
[]By default, newly configured unification rules apply to your data on the following data run. You can manually process all entities or specific entities.
To manually process unification rules:
- Go to **Configure **> **Data Unification **> **Fields**.
-
Choose one of the following options:
- **Process All**: Click to process all entities.
- **Process**: Click to process specific entities.
[See image.](#process-and-process-all)
Manually processing an entity without processing its related entities can cause data misalignment issues until the next full data run.
[]![field unification manual process](/downloads/uvm/administration/business-logic/unification/managing-field-unification/field%20unification%20manual%20process.png)
[]You can edit an existing ruleset to modify the rules it contains.
To edit a ruleset:
- Go to **Configure **> **Data Unification **> **Fields**.
-
Hover over the ruleset you want to edit, and click the** Edit** icon.
The **Field Rule Set page** appears.
- If prompted, click **Unlink & Override**.
- Make the necessary changes.
- Click **Save **to save the ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]You can copy all rules of a ruleset and paste them into a new ruleset.
To copy and paste a ruleset:
- Go to **Configure **> **Data Unification **> **Fields**.
- Hover over the ruleset you want to copy, and click the** Edit** icon.
- In the **Column Menu** located in the top-right corner of the ruleset, click **Copy All Rules**.
-
In the destination ruleset, click **Paste Rules**.
[See image.](#copy-paste-rule-buttons)
- Click **Save **to save the ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]![86b57e4d-3d41-4fb6-b2a7-97c3a11b4c67.png](/downloads/uvm/configure/data-unification/managing-field-unification/86b57e4d-3d41-4fb6-b2a7-97c3a11b4c67.png)
[]You can delete a ruleset that is outdated or no longer relevant due to changes in how data is sourced or structured.
To delete a ruleset:
- Go to **Configure **> **Data Unification **> **Fields**.
-
Hover over the ruleset you want to delete, and click the** Delete** icon.
The **Confirm Deletion** window appears.
[See image.](#confirm-deletion-window)
-
Click **Delete**.
The field's logic reverts to its default logic.
[]![d5c27f74-8198-4679-9115-465b057b695e.png](/downloads/uvm/configure/data-unification/managing-field-unification/d5c27f74-8198-4679-9115-465b057b695e.png)
Managing Field Unification Rules
You can clone, edit, or delete a rule in field unification rulesets.
When managing field unification rules, you can perform the following actions:
- [Clone a Rule](#clone-rule)
- [Edit a Rule](#edit-rule)
- [Delete a Rule](#delete-rule)
[]Cloning a field unification rule is useful when you need to create multiple rules with similar logic or structure. Instead of building each rule from scratch, you can clone an existing rule and modify only the parts that differ, such as conditions or field values.
To clone a rule:
- Go to **Configure **> **Data Unification **> **Fields**.
- Select the ruleset that you want to modify.
-
Hover over the rule in the ruleset that you want to clone, and click the **Clone **icon.
[See image.](#hover-clone-rule-icon)
- A copy of the rule is created with the same name as the original.
- Edit the cloned rule as needed, including the rule's name.
- Click **Save **to save the rule to the ruleset.
- Click **Save **to save the ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]**![cac66ff7-275d-46a8-b01a-6324061f6e8a.png](/downloads/uvm/configure/data-unification/managing-field-unification/cac66ff7-275d-46a8-b01a-6324061f6e8a.png)
**
[]If you need to modify an existing rule, you can edit it to make the necessary adjustments. To update an existing rule's logic, you can edit the rule directly rather than deleting and recreating it.
To edit a rule:
- Go to **Configure **> **Data Unification **> **Fields**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to edit, and click the** Edit** icon.
[See image.](#hover-edit-rule-icon)
- Make the necessary changes.
- Click **Save **to save the rule to the ruleset.
- Click **Save **to save the ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]![b5aa9e5f-763b-488f-997c-aa8c11714908.png](/downloads/uvm/configure/data-unification/managing-field-unification/b5aa9e5f-763b-488f-997c-aa8c11714908.png)
[]You can delete a rule if it's no longer applicable due to changes in how data is sourced or structured.
Deleting a rule doesn’t trigger a warning message and deletes the rule immediately.
To delete a rule:
- Go to **Configure **> **Data Unification **> **Fields**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to delete, and click the** Delete** icon.
[See image.](#hover-delete-rule-icon)
- Click **Save **to save the ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]![0edcd9f0-4612-4ba3-9acf-6fc90179ff3b.png](/downloads/uvm/configure/data-unification/managing-field-unification/0edcd9f0-4612-4ba3-9acf-6fc90179ff3b.png)
[]![e458e150-17b8-4f01-bdcb-6042fc8be752.png](/downloads/uvm/configure/data-unification/configuring-field-unification/e458e150-17b8-4f01-bdcb-6042fc8be752.png)