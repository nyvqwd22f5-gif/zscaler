# About Containment Integration
Source: https://help.zscaler.com/itdr/about-containment-integration
PDF: https://help.zscaler.com/pdf/com/en/1531810.pdf

Zscaler ITDR integrates seamlessly with third-party security solutions to isolate active attackers with automated containment.
Containment integration provides the following benefits and enables you to:
- Forward the attacker's identity to the integrated security solution, which then isolates the attacker's system from the network.
- Prevent advanced targeted attacks.
You can contain an attack from the Rules page (Orchestrate > Rules) by creating a response or containment rule, or manually contain the attack from the [Investigate dashboard](/deception/taking-action-from-the-dashboard).
About the Containment Page
On the Containment page (Orchestrate > Containment), you can do the following:
- View a list of all configured containment integrations. For each integration, you can see:
- **Enabled**: Indicates if the containment integration is enabled or not.
- **Settings**: The name of the third-party security solution.
-
**Blocked Identities**: The total number of blocked attackers.
You can click the number under **Blocked Identities** to [view the details of the contained attacker](/itdr/viewing-blocked-identities).
- Configure containment integrations on the following supported solutions:
- [CrowdStrike Falcon Insight](/itdr/containment-configuration-guide-crowdstrike)
- [Okta (SSF)](/itdr/containment-configuration-guide-identity-threat-protection-okta-ai)
- [Zscaler Internet Access (ZIA)](/itdr/containment-configuration-guide-zscaler-internet-access-zia)
- [Zscaler Private Access (ZPA)](/itdr/containment-configuration-guide-zscaler-private-access-zpa)
![About the Containment page](/downloads/itdr/orchestrate/containment-integrations/about-containment-integration/itdr-about-containment-page.png)