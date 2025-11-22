# Testing a Rule
Source: https://help.zscaler.com/deception/testing-rule
PDF: https://help.zscaler.com/pdf/com/en/1531432.pdf

You can test an orchestration rule to validate if the rule conditions match a set of events. You can use a set of events from the exported [event logs](/deception/exporting-event-logs) JSON file, or automatically add a sample event to test a rule.
To test a rule:
- Go to **Orchestrate** > **Rules**.
-
Select a rule to test, and then click the **Edit **icon.
[See image.](#deception-test-rule-edit-icon)
-
In the **Rule Details** window, under **General**, click the** here** link.
[See image.](#deception-click-here-test-rule)
-
In the **Test Rules** window, in the **Events **field, copy and paste the events in the JSON format, or click **Add sample event** to automatically add an event.
[See image.](#deception-paste-json-event-test-rule)
The** All events passed** message appears if the rule conditions match with the events.
[See image.](#deception-test-rule)
- Click **Cancel** to close the window.
[]![Edit icon on the Rules page](/downloads/deception/orchestrate/orchestration-rules/testing-rule/zscaler-deception-orchestrate-edit-rule.png)
[]![Click the here link to test a rule](/downloads/deception/orchestrate/orchestration-rules/testing-rule/zscaler-deception-test-a-rule-click-here.png?1667555712)
[]![Paste JSON events or click Add sample event ](/downloads/deception/orchestrate/orchestration-rules/testing-rule/zscaler-deception-test-rule-paste-json-1.png)
[]![Test a rule](/downloads/deception/orchestrate/orchestration-rules/testing-rule/zscaler-deception-test-a-rule-passed.png)