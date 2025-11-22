# Managing Entity Unification
Source: https://help.zscaler.com/uvm/managing-entity-unification
PDF: https://help.zscaler.com/pdf/com/en/1529702.pdf

After [creating entity unification rules](/uvm/configuring-entity-unification), you can manage the rules in the rulesets to refine how records are merged.
For access to Entity Unification, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Model Management resource. To learn more, see [Creating Custom Roles](/uvm/creating-managing-role-permissions) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#field-unification-permissions)
When managing entity unification rules, you can perform the following actions:
- [Duplicate an Entity Unification Rule](#duplicate-rule)
- [Edit an Entity Unification Rule](#edit-rule)
- [Delete an Entity Unification Rule](#delete-rule)
[]Duplicating a rule is useful when you need to create multiple rules with similar logic or structure. Instead of building each rule from scratch, you can copy an existing rule and modify only the parts that differ, such as field values, conditions, or merge criteria.
To duplicate a rule:
- Go to **Configure **> **Data Unification **> **Entities**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to duplicate, and click the **Duplicate** icon.
[See image.](#hover-duplicate-rule-icon)
- A copy of the rule is created with the same name as the original.
- Edit the duplicated rule as needed, including the rule's name.
- Click **Save** to save the rule.
- Click **Save **to save ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]**![mceclip8.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip8.png)
**
[]To update an existing rule's merge logic, you can edit the rule directly rather than deleting and recreating it. This is useful for updating an existing rule's merge logic to reflect changes in data structure, filtering requirements, or matching criteria.
To edit a rule:
- Go to **Configure **> **Data Unification **> **Entities**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to edit, and click the** Edit** icon.
[See image.](#hover-edit-icon)
The **Edit **<Entity> **Merge Rule **drawer appears.
- Make the necessary changes.
- Click **Save** to save the rule.
- Click **Save **to save ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]**![mceclip9.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip9.png)
**
[]You can remove rules that are outdated or no longer relevant due to changes in data structure or merge logic.
Deleting a rule doesn't trigger a warning message and deletes the rule immediately.
To delete a rule:
- Go to **Configure **> **Data Unification **> **Entities**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to delete, and click the **Delete** icon.
[See image.](#hover-delete-icon)
- Click **Save **to save ruleset and apply changes on the next data run, or click **Save & Run **to apply the changes immediately.
[]**![mceclip10.png](/downloads/uvm/configure/data-unification/configuring-entity-unification/mceclip10.png)
**
[]![e458e150-17b8-4f01-bdcb-6042fc8be752.png](/downloads/uvm/configure/data-unification/configuring-field-unification/e458e150-17b8-4f01-bdcb-6042fc8be752.png)