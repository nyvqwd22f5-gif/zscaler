# Processing Rules
Source: https://help.zscaler.com/deception/stop-rule-processing
PDF: https://help.zscaler.com/pdf/com/en/1531431.pdf

Orchestration rules are processed in the order they appear on the Orchestrate page. For example, a rule with priority 1 is processed first and then the rule with priority 2, etc. You can determine when to stop processing rules in the orchestration rule pipeline. For example, assume that you have configured the following rules:
- Rule A (priority 1): Delete an event if the attacker's IP address is 192.0.2.3.
- Rule B (priority 2): Send an email notification with the event details to specific users.
If you don’t want to send this event in an email to the users, you can stop processing any subsequent rules after processing Rule A.
To stop processing more rules:
- Go to **Orchestrate** > **Rules**.
-
Locate the rule that you want to modify and click the **Edit** icon under the **Actions **column.
[See image.](#deception-stop-process-more-rule-edit-icon)
-
In the **Rules Details** window, under **General**, enable **Don't process further rules**.
[See image.](#deception-stop-processing-more-rules-option)
-
Click **Save**.
In this example, after Rule A is processed, subsequent rules are ignored.
[]![Edit icon on the Rules page](/downloads/deception/orchestrate/orchestration-rules/stopping-rule-processing/zscaler-deception-orchestrate-edit-rule.png?1666338152)
[]![Stop processing more rules option](/downloads/deception/orchestrate/orchestration-rules/stop-rule-processing/zscaler-deception-processing-rules-toggle_0.jpg)