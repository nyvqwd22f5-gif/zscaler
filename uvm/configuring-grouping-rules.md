# Configuring Grouping Rules
Source: https://help.zscaler.com/uvm/configuring-grouping-rules
PDF: https://help.zscaler.com/pdf/com/en/1527901.pdf

Ticket grouping rules are customizable rules that aggregate findings with similar attributes into tickets to facilitate a more focused and productive work process. On initial account setup, grouping rules include a default active ruleset that implements grouping best practices. You can adjust the default grouping and align it to your organization's business logic.
You can create rulesets in the following ways:
- Create a new ruleset. After adding rules to your ruleset, activate and run the ruleset to reaggregate findings into tickets using your new ruleset. Activating your new ruleset deactivates the currently active ruleset. To learn more, see [Managing Grouping Rules](/uvm/managing-grouping-rules).
- Clone and edit the default ruleset to refine it according to your organization's needs. When complete, run the edited ruleset to reaggregate findings into tickets based on the newly configured grouping logic. To learn more, see [Managing Grouping Rules](/uvm/managing-grouping-rules).
Configuring a Grouping Ruleset
A grouping ruleset is a collection of individual rules designed to group findings into tickets based on specific conditions.
You can have multiple rulesets in the account, but only one ruleset can be active.
To create a grouping ruleset:
- In the **Vulnerabilities** app, go to **Settings** > **Grouping Rules**.
-
Click **New Rule Set**.
The **Create Rule Set** page appears.
- Enter a name for the ruleset.
-
Add at least one grouping rule in addition to the default fallback rule.
Every ruleset includes a default fallback rule, which provides a default aggregation method for findings that don't match any conditions. The fallback rule can be edited, but can't be removed or deleted.
To aggregate findings into tickets based on your new logic, activate and run the new ruleset. If you only activate but don't run your new ruleset, it will run on the next data ingestion in your account. To learn more, see [Managing Grouping Rules](/uvm/managing-grouping-rules).
Configuring Grouping Rules
Within a grouping ruleset, you can create individual rules that define how findings should be aggregated into tickets. For example, you can create a rule to group findings reported on the same vulnerable component (e.g., Adobe Acrobat) to facilitate fixing all findings in a single ticket. Every new ruleset must include at least one rule in addition to the default fallback rule.
A grouping rule consists of three key components:
- If condition: Defines a filter that determines which findings the rule applies to.
- Then action: Specifies that findings should be aggregated into a single ticket if they have matching values in all selected fields.
- Define Ticket Title By: Defines the title format for tickets that are created based on the rule.
To create a grouping rule:
-
In the relevant ruleset, click **New Rule**.
The **Create Rule** drawer appears.
[See image.](#create-grouping-rule-drawer)
- In the **Create Rule **drawer:
- **Name**: Enter a name for the rule.
- **If**: Define the rule condition that determines which findings the rule should aggregate into a single ticket.
- Select a field on which the condition should be based.
-
Select an operator (e.g., **Is Not Empty**, **Is Empty**, **Equals**).
The available operators vary depending on the field type, indicated to the left of the field name.
- Enter the value to which the rule should apply.
- (Optional) Use **AND**/**OR **logic to define compound rules.
- **AND **aggregates findings only if they meet all conditions in the rule.
- **OR **aggregates findings if they meet any of the conditions in the rule.
- **Then**: Select at least one field from the **Group By **drop-down menu according to which the findings that meet your conditions should be aggregated. All findings with the same value are merged into a single ticket. For example, if you group findings by the Asset Type field and there are two findings on Server assets and three findings on Workstation assets, then two tickets are created, one for each asset type. Adding the Asset OS field can lead to the creation of additional tickets, as a ticket is created for each unique combination of Asset Type and Asset OS values.
- **Define Ticket Title By**: Select a method to set the ticket title.
- **Smart Text**: Use a combination of free text and field names as tokens to set the ticket title. For example, you can enter the name of the team based on the business application associated with the ticket. To add fields as tokens, enter the field name within double curly brackets. The field's display name automatically translates to the field's system name (e.g., Application Name → `application.name`).
- **Expression**: Set a ticket title using an expression to apply custom value transformations and standardize formats. Supported functions, operators, and references, along with examples, are displayed when clicking the Expression text box.
-
Click **Preview **to validate your rule's logic. The preview displays findings that match the rule and their relevant fields according to the fields specified in the rule. This can indicate whether the rule's filters apply to the findings you intend to group into tickets.
[See image.](#preview-grouping-rule)
If **No findings match filter condition** is displayed in the preview, you might need to adjust the rule's configured filters. Alternatively, a previous rule might be applicable to the relevant findings, as grouping is dependent on rule order.
- Click **Save** to add the rule to the ruleset.
Repeat the process to add as many grouping rules as necessary to the ruleset.
After adding all the necessary rules to the ruleset, save the ruleset to complete the process:
- Click **Save **to save the ruleset. This saves the rules to the ruleset but doesn't reaggregate into tickets based on the ruleset's rules.
- If the ruleset is active, the new ruleset will take effect either when you click Run or the next time data is processed in the account (e.g., when a data source runs).
- If the ruleset is inactive, no changes will apply to the grouping of findings in the account until the ruleset is activated and runs.
- In the **Save **drop-down menu, click **Save & Activate **to save the ruleset and immediately apply the rules to the data in your account.
Order of Rules in a Grouping Ruleset
The rules within a grouping ruleset are executed sequentially by their order of appearance. A finding is aggregated into a ticket according to the first rule that applies to it. If no rule applies to the finding, it's aggregated by the default fallback rule. You can adjust the order of rules by dragging the rules to your desired order. After rearranging the rule order, click Save to apply your changes.
[See image.](#rearrange-grouping-rules)
[]![create grouping rule drawer](/downloads/uvm/administration/business-logic/unification/configuring-field-unification/create%20grouping%20rule%20drawer.png)
[]![mceclip7.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip7.png)
[]![mceclip8.png](/downloads/uvm/vulnerability-management/settings/configuring-grouping-rules/mceclip8.png)