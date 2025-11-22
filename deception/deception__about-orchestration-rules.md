# About Orchestration Rules
Source: https://help.zscaler.com/deception/about-orchestration-rules
PDF: https://help.zscaler.com/pdf/com/en/1531430.pdf

Zscaler Deception allows you to create orchestration rules using queries and conditions to take immediate actions when events with threats are detected.
Orchestration rules provide the following benefits and enable you to:
- Automate tagging, deleting, or marking events as safe.
- Configure alert notifications about attackers to specific users via emails, phone calls with voice messages, and text messages.
- Automate containment of attacks in response to detections using integration with other third-party solutions.
Each event that is generated in the Zscaler Deception Admin Portal runs through the orchestration rule pipeline. When an event matches the conditions of the rule, the corresponding actions are taken.
Deception provides a few predefined or internal rules to detect attacks. By default, these rules are disabled. You can enable and configure actions based on your requirements. You cannot change the rule conditions or delete the internal rules.
About the Rules Page
On the Rules page (Orchestrate > Rules), you can do the following:
- View a list of rules. For each rule, you can view:
- **Priority**: The rule priority that determines the order in which the rules are run. Priority 1 has the highest priority and runs first. You can drag and drop the rules to change the order.
- **Name**: The name of the rule.
- **Condition**: The conditions configured to trigger an action. The conditions are created using the custom query language. To learn more about the custom query language, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
- **Tasks**: The actions taken when the rule is triggered.
- **Type**: Indicates if the rule is internal or not.
- Create an [orchestration rule](/deception/creating-orchestration-rule).
-
Pause or resume orchestration rules.
**Pause orchestration **indicates that the orchestration pipeline is running. **Resume orchestration** indicates that the orchestration pipeline is stopped.
- [Edit or delete a rule](/deception/editing-or-deleting-rule).
![About the Rules page](/downloads/deception/orchestrate/orchestration-rules/about-orchestration-rules/zscaler-deception-rules-page-about.png)