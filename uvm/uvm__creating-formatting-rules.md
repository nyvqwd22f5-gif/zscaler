# Creating Formatting Rules
Source: https://help.zscaler.com/uvm/creating-formatting-rules
PDF: https://help.zscaler.com/pdf/com/en/1531110.pdf

Formatting rules apply color thresholds and visually distinguish measurements, making data interpretation more clear and intuitive. Use formatting rules to emphasize key measurements and trends across widget dashboards and asset compliance policies to help identify patterns, performance levels, or critical issues.
Creating Formatting Rules
To use formatting, you first have to create a rule. You can do this within the [policy configuration page](/uvm/configuring-asset-compliance-policies), or go to the formatting rules page from a widget in a [custom dashboard](/uvm/configuring-custom-dashboards).
To create a formatting rule:
- Go to **Configure **> **Formatting Rules**.
-
Click **New Rule**.
The **Create Formatting Rule **drawer appears.
-
In the **Create Formatting Rule** drawer:
- **Name**: Enter a name (e.g., `Policy Compliance Threshold`).
-
Define the conditions:
- Select an operator (e.g., **>**, **<**, **=**, **Between**). If you select **Between**, set both start and end values for the range.
- Enter a value for the condition.
-
Assign a color for the condition (e.g., red for <25%).
Green typically represents satisfactory rates, and red represents unsatisfactory rates.
The order of conditions determines the order that the rules are applied. When there is an overlap between conditions, the color of the top condition takes priority.
- **Fallback Formatting Rule Logic**: Assign a default color to display when no other condition applies to a value.
- Click **Save**.
[See image.](#formatting-rule-drawer)
[]![formatting rule drawer](/downloads/uvm/getting-started/admin-portal/creating-formatting-rules/generic%20formatting%20rule%20save.png)
Applying Formatting Rules
After saving the formatting rule, apply it to widgets or policies as needed.
To apply a formatting rule to a widget:
- Go to **Explore **> **Dashboards**.
- Click the dashboard you want to edit.
-
Click the **Edit Dashboard **icon.
[See image.](#edit-dashboard-icon)
- Hover over the widget that you want to edit, and click the **Edit **icon.
-
Click the **Style **icon, and select the formatting rule to apply to the widget.
[See image.](#style-tab-formatting-rule)
- Click **Save**.
- Save the dashboard to apply formatting rule to the widget.
To apply a formatting rule to an Asset Exposure Management (AEM) policy:
- Go to **Assets **> **Policies**.
-
Click the policy you want to edit.
The **Edit **<Policy Name> page appears.
- In the **Formatting Rule **section, select the relevant formatting rule.
- Click **Save** to apply the rule to the policy.
[]![edit dashboard icon](/downloads/uvm/getting-started/admin-portal/creating-formatting-rules/edit%20dashboard%20icon.png)
[]![style tab formatting rule](/downloads/uvm/getting-started/admin-portal/creating-formatting-rules/style%20tab%20formatting%20rule.png)