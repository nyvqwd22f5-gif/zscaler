# Creating an Orchestration Rule
Source: https://help.zscaler.com/deception/creating-orchestration-rule
PDF: https://help.zscaler.com/pdf/com/en/1531574.pdf

An orchestration rule allows you to automate various actions performed in the Zscaler Deception Admin Portal based on custom conditions created using a purpose-built query language. Using the orchestration rule, you can automate actions that fall broadly under the following categories:
- Workflow: Automate actions performed on events within the [Investigate dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard), such as marking an event as safe, deleting an event, or adding a tag to the event.
- Notification: Automate sending alert notifications via emails.
- Response: Automate actions taken on an attacker or device using different Security Operation Center (SOC) tools [integrated with Zscaler Deception](/deception/about-containment-integration).
A single orchestration rule can include a combination of actions from these categories. For example, you can automate marking an event as safe and sending an email notification to IT administrators using a single orchestration rule. When you add multiple orchestration rules, Deception evaluates the rules for each event starting from the highest priority to find a matching condition and applies the rule action if the condition matches. If the rule condition does not match, the next rule is evaluated. This process continues until all rules are evaluated. When a rule with a matching condition is found, you can choose to evaluate and apply subsequent rules with matching conditions or stop further rule evaluation. To learn more, see [Processing Rules](/deception/stop-rule-processing).
To create an orchestration rule:
- Go to **Orchestrate **> **Rules**.
-
Click **Add Rule**.
[See image.](#deception-rule-add-rule-option)
The **Rule Details **window appears.
- In the **Rule Details **window:
-
Under the **General **section:
- **Name**: Enter a name for the rule.
- **Enabled**: Select to enable the rule.
- **Don't process further rules**:** **(Optional) Select to stop the evaluation of subsequent rules if this rule is applied.
- **Only ThreatParse Events:** (Optional) Select to apply this rule only for events that have a ThreatParse score.
-
Create a rule condition using queries. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
If no condition is configured, then the rule is applied to all events.
- **Time Zone**: Select a time zone that should be used to evaluate rules if you used date and time fields in the queries in the previous step.
[See image.](#deception-config-rule-general)
- Configure one or more categories of automation:
- [Workflow](#workflow-automation)
- [Notification](#notification-automation)
- [Response](#response-automation)
- Click **Save**.
[]You can create a rule to automatically perform workflow actions such as tagging, deleting, or marking [security events or alerts ](/deception/viewing-and-managing-zscaler-deception-dashboard)as safe.
To do this, under the **Workflow **section, configure one or more workflow actions:
- **Mark as safe**: Enable to mark the events that match the condition as safe.
- **Delete**: Enable to delete the events that match the condition.
- **Add Tags**: Enable and enter a tag name to tag the events that match the condition. For example, if the rule condition is `attacker.ip is "192.0.2.3"` and the tag name is `Team A`, then all events from the IP address 192.0.2.3 are tagged as Team A.
[See image.](#deception-config-workflow-rule-workflow)
[]You can create a rule to automatically send alert notifications about events to specific users via email. The rule generates a notification whenever an event matches the rule conditions.
To do this, under the **Notify **section, configure an email notification:
- Enable **Email**.
- Select the users you want to notify via email from the drop-down menu.
-
Select the email notification frequency from the drop-down menu.
[See image.](#deception-config-notification-rule-notify)
- The notifications use default templates and are sent to the email address [configured for the user](/deception/about-users-roles#deception-add-new-user-admin-portal). You can also customize the notification template. To learn more, see [Customizing Event Notification Templates](/deception/customizing-event-notification-templates)[.]
- The timestamps in the email notifications are generated according to the time zone configured for the users who are selected to receive the notification. To learn more, see [About Users & Roles](/deception/about-users-roles#deception-add-new-user-admin-portal) and [Editing the User Profile](/deception/editing-user-profile).
- Deception enforces a Fair Usage Policy (FUP) that limits the number of notifications triggered per day. A [system message](/deception/about-logs-and-system-messages) is also generated when this limit is reached for the first time in a day. To learn more, see [Ranges & Limitations](/deception/ranges-and-limitations#orchestrate-limitations).
[]You can create a response rule to automatically contain users or devices. Deception integrates seamlessly with various security solutions to isolate active attackers and devices. You can create a rule to forward the attacker's identity to the integrated solution, which then isolates the attacker's system from the network. To learn more, see [About Containment Integration](/deception/about-containment-integration).
To create a response action, under the **Respond **section, configure a containment action:
-
Enable one or more integrations that you want to use to contain identities.
[See image.](#deception-respond-block)
- Select additional options if you are configuring the following containment solutions:
-
**Palo Alto Networks - NGFW**: You can choose to contain attackers based on their hostnames or IP addresses per the External Dynamic List.
[See image.](#ngfw-image)
- **Fortinet**: You can choose to contain attackers based on their domains or IP addresses per the Threat Feeds.
[See image.](#fortinet-image)
- **CrowdStrike Falcon Insight**: You can contain endpoints based on the following parameters:
- [IOC Hash](#falcon-IOC-hash)
- [IOC IP](#falcon-IOC-ip)
- [IOA Process Tree](#falcon-IOA-process-tree)
-
**Okta (SSF)**: Select **Enabled** and configure the user risk level and risk change reason that you want to be pushed to Okta:
- **User Risk Level**: Select a risk score level (**Low**, **Medium**, or **High**) that you want to be pushed to Okta for a user when an event matching the configured rule condition occurs. This information is shared with Okta.
- **Risk Change Reason**: Enter the reason describing why the risk score is changed. This information is shared with Okta.
[See image.](#okta-rule-configuration)
- []**IOC Hash**: Enable to share file hashes that are considered indicators of compromise with CrowdStrike.
- **IOC Hash Action**: Choose the action that CrowdStrike should perform when IOC hashes are shared:
- **Detect Only**: Show the indicator as a detection and take no other action.
- **Block**: Add the indicator to the denylist and show it as a detection.
- **Block, Hide Detection**: Add the indicator to the denylist and do not detect it.
- **Allow**: Add the indicator to the allowlist and do not detect it.
- **No Action**: Save the indicator for future use and take no action.
- **IOC Hash Severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike. The available levels are **Informational**,** Low**, **Medium**,** High**,** **and **Critical**.
[See image.](#ioc-hash-image)
- []**IOC IP: **Enable to share IP addresses that are considered indicators of compromise with CrowdStrike.
- **IOC IP Action**: Choose the action that CrowdStrike should perform when IP addresses are shared:
- **Detect Only**: Show the indicator as a detection and take no other action.
- **No Action**: Save the indicator for future use and take no action.
- **IOC IP Severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike. The available levels are **Informational**,** Low**, **Medium**,** High**,** **and **Critical**.
[See image.](#ioc-ip-image)
- []**IOA Process Tree**: Enable to share process trees that are considered indicators of attack with CrowdStrike.
- **IOA Action**: Choose the action that CrowdStrike should perform when IOA process trees are shared:
- **Detect**: Show the indicator as a detection and take no other action.
- **Monitor**: Use the indicator for informational use only and take no action nor show it as a detection.
-
**Block Execution**: Kill the process and show the indicator as a detection.
Exercise caution when choosing the Block Execution action as CrowdStrike kills all processes that match with the process tree across all endpoints in your network. To avoid killing legitimate processes, make sure that you have configured IOA safe processes as described in the [Containment Configuration Guide for CrowdStrike](/deception/containment-configuration-guide-crowdstrike).
- **IOA severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike. The available levels are **Informational**,** Low**,** Medium**,** High**,** **and **Critical**.
[See image.](#ioa-image)
[]![Add Rule option on the Rules page](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-orchestration-add-rule.png)
[]![Configure a workflow rule](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-rule-general-window.jpg)
[]![Workflow Rule Configuration](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-workflow-rule-workflow.jpg)
[]![Configure notifcation settings](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-email-rule.png)
[]
[]![Respond block with Microsoft Defender toggle enabled](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-response.png)
[]
![A screenshot capturing the rule configuration for Palo Alto Networks NGFW](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-ngfw.jpg)
[]
![A screenshot capturing the rule configuration for Fortinet](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-fortinet-rule.jpg)
[]
![A screenshot capturing the IOA Process Tree configuration](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-ioa.png)
[]
![A screenshot capturing the IOC IP configuration](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-ioc-ip.png)
[]
![A screenshot capturing the IOC Hash configuration](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-ioc-hash.png)
[]
![A screenshot highlighting the Orchestration Rule for Okta](/downloads/deception/orchestrate/orchestration-rules/creating-orchestration-rule/zscaler-deception-okta-rule.jpg)