# Testing a Rule with Events
Source: https://help.zscaler.com/deception/testing-rule-events
PDF: https://help.zscaler.com/pdf/com/en/1531580.pdf

On the [Events Logs](/deception/about-event-logs) page, you can see all the events associated with a particular entity, such as attackers, devices, Decoy Connectors, and other network components. You can use these listed events and test them if they match custom rules created using the purpose-built [query language](/deception/understanding-and-building-queries). You can combine multiple events and test custom rules on them. Typically, you can test rules on events to analyze why an existing [orchestration rule](/deception/about-orchestration-rules) did not trigger, or to create new rules that would match similar events.
To test a rule on events:
-
On the [extended details](/deception/viewing-extended-details) page of an entity from the dashboard, click **Event Logs**.
The **Event Logs** page appears.
- On the **Event Logs** page, select the events for which you want to test a custom rule. You can select a maximum of 10 events.
-
Click **Test Rule **from the **Actions **drop-down menu.
The **Test Rules **window appears.
-
In the **Test Rules **window, enter custom rules in the **Rule **field. You can create custom rules using the purpose-built query language. To learn more, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
[See image.](#test-rule)
The test results are displayed immediately, showing the number of events that passed the rule. The list of events that failed is shown separately.
[]
![zscaler-deception-test-a-rule.gif](/downloads/deception/investigate/accessing-extended-details/event-logs/testing-rule-event/zscaler-deception-test-a-rule.gif)