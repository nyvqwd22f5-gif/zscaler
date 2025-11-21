# Testing a Rule
Source: https://help.zscaler.com/itdr/testing-rule
PDF: https://help.zscaler.com/pdf/com/en/1531814.pdf

You can test an orchestration rule to validate if the rule conditions match a set of events. You can use a set of events from the exported [event logs](/itdr/exporting-event-logs) JSON file, or automatically add a sample event to test a rule.
To test a rule:
- Go to **Orchestrate** > **Rules**.
-
Locate a rule to test, and then click the **Edit **icon.
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
[]![Edit icon on the Rules page](/downloads/itdr/orchestrate/orchestration-rules/testing-rule/itdr-edit-rule-new_0.png)
[]![Clicking the here link to test a rule](/downloads/itdr/orchestrate/orchestration-rules/testing-rule/itdr-option-to-test-tule.png)
[]![Paste JSON events or click Add sample event ](/downloads/itdr/orchestrate/orchestration-rules/testing-rule/itdr-test-rule.png)
[]![Testing a rule](/downloads/itdr/orchestrate/orchestration-rules/testing-rule/itdr-test-pass.png)