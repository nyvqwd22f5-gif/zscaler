# Controlling Threat Events
Source: https://help.zscaler.com/itdr/controlling-threat-events
PDF: https://help.zscaler.com/pdf/com/en/1531838.pdf

When threat events are identified, you can respond immediately to contain the incident and mitigate the potential risk.
To contain a threat event:
-
On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#action-button)
-
Click the **Actions** drop-down menu and select the required mitigation action from the list.
- [Contain using a third-party solution.](#third-party-containment)
- [Mark an event or attacker as safe or unsafe.](#mark-as-safe)
- [Create a rule to blocklist the attacker's IP from accessing your decoy.](#block-an-event)
- [Delete attacker details.](#delete-an-event)
- In the confirmation window, click **OK**.
[]When you delete an attacker, all previously triggered events related to the attacker's activities are removed from the ITDR Admin Portal, and any associated ThreatParse data linked to the attacker is also permanently deleted.
You can also automate deletion using orchestration rules. To learn more, see [Creating an Orchestration Rule](/itdr/creating-orchestration-rule).
Tags associated with the attacker are retained.
[]You can mark an event as safe by selecting the **Mark as safe **option. This removes the attacker from the default view in the Zscaler ITDR Admin Portal. You can also automate this action using [orchestration rules.](https://help.zscaler.com/itdr/creating-orchestration-rule)
To revert the action and mark the event as unsafe:
-
Click the **Select Query** drop-down menu and enable **Show marked as safe**. This shows all events that are marked as safe.
[See image.](#show-attack-marked-safe)
- Click the attack icon for the event you want to reverse from safe to unsafe.
-
Click the **Actions** drop-down menu and select **Mark as unsafe**.
[See image.](#mark-as-unsafe)
- When an attacker is marked as safe, it can take up to an hour for the action to be reflected in the ITDR Admin Portal depending on the number of events associated with the attacker.
- If you mark an attacker's IP address as safe, all the past events from that attacker are marked as safe. However, any new events from that IP address are generated and displayed on the Zscaler ITDR dashboard.
[]When you select the blocklist option, you are redirected to the Blocklist page to create the rule.
[]Forward the attacker's details to the following security tools or services to remediate the issue:
- [CrowdStrike Falcon Insight](/itdr/containment-configuration-guide-crowdstrike)
- [Amazon GuardDuty](/itdr/containment-configuration-guide-amazon-guardduty)
- [Threat Protection with Okta AI](/itdr/containment-configuration-guide-identity-threat-protection-okta-ai)
- [Zscaler Internet Access (ZIA)](/itdr/containment-configuration-guide-zscaler-internet-access-zia)
- [Zscaler Private Access (ZPA)](/itdr/containment-configuration-guide-zscaler-private-access-zpa)
Before forwarding the attacker's details, make sure to enable the settings for these tools on the [Containment](https://help.zscaler.com/itdr/about-containment-integration) page. You can also automate containment using orchestration rules. To learn more, see [Creating an Orchestration Rule](/itdr/creating-orchestration-rule).
[See image.](#take-action)
[]![Showing attacks marked as safe](/downloads/itdr/investigate/controlling-threat-events/mark%20as%20safe.png)
[]![Actions menu to control and manage threat events](/downloads/itdr/investigate/controlling-threat-events/Actions.png)
[]![List of actions to control and manage threat events](/downloads/itdr/investigate/controlling-threat-events/Investigate_GIF.gif)
[]![Option to mark an event as unsafe](/downloads/itdr/investigate/taking-action-dashboard/deception-mark-as-unsafe.png)