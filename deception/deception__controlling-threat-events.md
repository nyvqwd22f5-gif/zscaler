# Controlling Threat Events
Source: https://help.zscaler.com/deception/controlling-threat-events
PDF: https://help.zscaler.com/pdf/com/en/1531377.pdf

When threat events are identified, you can respond immediately to contain the incident and mitigate the potential risk.
To contain a threat event:
-
On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#action)
- Click the **Actions** drop-down menu and select the required mitigation action from the list.
- [Contain using a third-party solution.](#third-party-containment)
- [Mark an event or attacker as safe or unsafe.](#mark-as-safe)
- [Create a rule to blocklist the attacker's IP from accessing your decoy.](#block-an-event)
- [Delete attacker details.](#delete-an-event)
- In the confirmation window, click **OK**.
[]When you delete an attacker, all previously triggered events related to the attacker's activities are removed from the Deception Admin Portal, and any associated ThreatParse data linked to the attacker is also permanently deleted.
You can also automate deletion using orchestration rules. To learn more, see [Creating an Orchestration Rule](/deception/creating-orchestration-rule).
Tags associated with the attacker are retained.
[]![Click an attacker icon to open the details pane](/downloads/deception/investigate/controlling-threat-events/action_decption.png)
[]You can mark an event as safe by selecting the **Mark as safe **option. This removes the attacker from the default view in the Zscaler Deception Admin Portal. You can also automate this action using [orchestration rules](/deception/creating-orchestration-rule).
To revert the action and mark the event as unsafe:
-
Click the **Select Query** drop-down menu and enable **Show marked as safe**. This shows all events that are marked as safe.
[See image.](#show-attack-marked-safe)
- Click the attack icon for the event that you want to reverse from safe to unsafe.
-
Click the **Actions **drop-down menu** **and select **Mark as unsafe**.
[See image.](#mark-as-unsafe)
- When an attacker is marked as safe, it can take up to an hour for the action to be reflected in the Deception Admin Portal depending on the number of events associated with the attacker.
- If you mark an attacker's IP address as safe, all the past events from that attacker are marked as safe. However, any new events from that IP address are generated and displayed on the Zscaler Deception dashboard.
[]When you select the blocklist option, you are redirected to the [Blocklist](https://help.zscaler.com/deception/creating-blocklist) page to create the rule.
[]Forward the attacker's details to the following security tools or services to remediate the issue:
- [Check Point Firewall](/deception/zscaler-deception-and-checkpoint-firewall-deployment-guide)
- [CrowdStrike Falcon Insight](/deception/zscaler-deception-and-crowdstrike-deployment-guide)
- [AWS GuardDuty](/deception/containment-configuration-guide-aws-guardduty)
- [Fortinet](/deception/zscaler-deception-fortinet-deployment-guide)
- [Microsoft Defender](/deception/zscaler-deception-and-microsoft-defender-deployment-guide)
- [Palo Alto Networks](/deception/zscaler-deception-and-palo-alto-networks-deployment-guide)
- [VMware Carbon Black EDR](/deception/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide)
- [VMware Carbon Black Endpoint Standard](/deception/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide)
- [Zscaler Internet Access (ZIA)](/deception/zscaler-deception-and-zscaler-internet-access-deployment-guide)
- [Zscaler Private Access (ZPA)](/deception/zscaler-deception-and-zscaler-private-access-deployment-guide)
Before forwarding the attacker's details, make sure to enable the settings for these tools on the [Containment](https://help.zscaler.com/deception/about-containment-integration) page. You can also automate containment using orchestration rules. To learn more, see [Creating an Orchestration Rule](/deception/creating-orchestration-rule).
[See image.](#take-action)
[]![Show attacks marked as safe](/downloads/deception/investigate/taking-actions-remediate-threats/zscaler-deception-show-marked-safe.png?1659433299)
[]![Click the Actions drop-down menu and choose a mitigation option](/downloads/deception/investigate/understanding-investigate-module/zscaler-deception-taking-action-gif.gif)
[]![Option to mark an event as unsafe](/downloads/deception/investigate/taking-action-from-the-dashboard/deception-mark-as-unsafe.png)