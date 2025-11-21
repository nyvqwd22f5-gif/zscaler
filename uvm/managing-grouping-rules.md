# Managing Grouping Rules
Source: https://help.zscaler.com/uvm/managing-grouping-rules
PDF: https://help.zscaler.com/pdf/com/en/1530814.pdf

After [creating grouping rules](/uvm/configuring-grouping-rules), you can manage the rulesets and the rules they contain to refine how findings are grouped into tickets. To apply changes to the grouping in your account, activate the updated ruleset.
Only one grouping ruleset can be active at any given time.
Managing Grouping Rulesets
When managing grouping rulesets, you can perform the following actions:
- [Activate a Grouping Ruleset](#activate-ruleset)
- [Clone a Grouping Ruleset](#clone-ruleset)
- [Edit a Grouping Ruleset](#edit-ruleset)
- [Delete a Grouping Ruleset](#delete-ruleset)
[]To manage and organize your rules effectively, you can create multiple grouping rulesets. This flexibility allows you to develop new rulesets without altering your existing ones, ensuring your current setup remains intact. However, keep in mind that only one ruleset can be active at a time. The active ruleset is clearly identified to help you track which configuration is currently in use.
[See image.](#active-ruleset)
To activate an inactive ruleset:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Click the **Column Menu **icon on the ruleset tile.
-
Click **Set as active**.
[See image.](#set-as-active-button)
The **Activate Rule Set **window appears.
-
In the **Activate Rule Set** window, enter the text displayed above the text box into the text box, then click **Continue**.
After manually activating a ruleset, the previously active ruleset becomes inactive.
To immediately apply changes to the grouping in your account, run the newly activated ruleset to reaggregate findings into tickets. To run the ruleset, click **Run **on the ruleset tile. This reprocesses all data in the account, and applies the new grouping logic to your findings.
[See image.](#run-ruleset-button)
[]![mceclip9.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip9.png)
[]![mceclip10.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip10.png)
[]![mceclip11.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip11.png)
[]You can clone an existing ruleset to create a new ruleset based on the structure of an existing one. This saves time and allows you to modify the cloned ruleset to fit your specific needs.
To clone a rule set:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Click the **Column Menu **icon on the ruleset tile.
-
Click **Clone**.
[See image.](#clone-ruleset-button)
A copy of the ruleset is created with the same name as the original, preceded by the word clone.
- Click the cloned ruleset to edit it.
- Enter a name for the ruleset and update the rules as needed.
- Save the ruleset in one of the following ways:
- Click **Save **to save the ruleset. This saves the rules to the ruleset but doesn't reaggregate into tickets based on the ruleset's rules. If the ruleset is left inactive, no changes will apply to the grouping of findings in the account until the ruleset is activated and runs.
- In the **Save **drop-down menu, click **Save & Activate **to save and set the ruleset as active. To apply changes immediately, run the activated ruleset to reaggregate findings into tickets; otherwise, changes will take effect during the next data ingestion.
[]![mceclip12.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip12.png)
[]You can edit a ruleset to update its name or adjust its logic as needed.
To edit a ruleset:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
-
Click the **Edit** icon on the ruleset.
[See image.](#edit-ruleset-button)
- Make the necessary changes.
- Save your changes.
- For the active ruleset: Click **Save **to apply the changes during the next data ingestion, or select **Save & Run **from the drop-down menu to immediately apply the changes to the grouping in your account.
- For inactive rulesets: Click **Save **to update the ruleset, or select **Save & Activate **from the drop-down menu to enable the ruleset and apply its grouping logic in your account. To apply changes immediately, make sure the ruleset is active and then run it.
[]![mceclip13.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip13.png)
[]If a ruleset is no longer needed, you can delete it to remove unnecessary configurations from your account. Deleting the active ruleset can impact data processing, so ensure another ruleset is activated before proceeding.
To delete a rule set:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Click the **Column Menu **icon on the ruleset tile.
-
Click **Delete rule set**.
[See image.](#delete-ruleset-button)
The **Confirm Deletion **dialog window appears.
- In the **Confirm Deletion **dialog window:
- For the active ruleset, enter the text displayed above the text box into the text box, then click **Delete**.
- For inactive rulesets, click **Delete**.
[]**![mceclip14.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip14.png)
**
Managing Grouping Rules
Manage grouping rules to control how findings are grouped into tickets within a ruleset. You can clone or edit rules to adjust their logic, or delete rules you no longer need. Each ruleset must include at least one rule in addition to the default fallback rule, which provides a standard grouping method for unmatched findings and cannot be removed.
When managing grouping rules, you can perform the following actions:
- [Clone Grouping Rules](#clone-rules)
- [Edit Grouping Rules](#edit-rules)
- [Delete Grouping Rules](#delete-rules)
[]Cloning a rule is useful when you need to create multiple rules with similar logic or structure. Instead of building each rule from scratch, you can copy an existing rule and modify only the parts that differ, such as field values, conditions, or grouping criteria.
To clone a grouping rule:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Select the ruleset that you want to modify.
- Hover over the rule you want to clone, and click the **Clone **icon (![clone icon](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/clone%20icon.png)
).
A copy of the rule is created with the same name as the original, followed by the word clone.
- Click the cloned rule to edit it.
- Enter a name for the rule and update the rule's logic as needed.
- (Optional) Click **Preview **to verify your rule's logic.
- Click **Save.**
[]To update an existing rule's grouping logic, you can edit the rule directly rather than deleting and recreating it.
To edit a rule:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Select the ruleset that you want to modify.
-
Hover over the rule you want to edit, and click the **Edit **icon (![edit icon](/downloads/uvm/vulnerability-management/settings-uvm/managing-grouping-rules/edit%20icon.png)
).
The **Edit Rule **drawer appears.
- Make the necessary changes.
- Click** Save**.
If your rule is part of the active ruleset, it will apply either when the ruleset is manually run or during the next data ingestion.
[]You can remove rules that are outdated or no longer relevant due to changes in data structure or grouping logic.
Deleting a rule doesn't trigger a warning message and deletes the rule immediately.
To delete a rule:
- Go to **Vulnerabilities** > **Settings** > **Grouping Rules**.
- Select the ruleset that you want to modify.
- Hover over the rule you want to delete, and click the **Delete **icon (![delete icon](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/delete%20icon.png)
).