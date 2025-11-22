# About Containment Integration
Source: https://help.zscaler.com/deception/about-containment-integration
PDF: https://help.zscaler.com/pdf/com/en/1531409.pdf

Zscaler Deception integrates seamlessly with third-party security solutions to isolate active attackers with automated containment.
Containment integration provides the following benefits and enables you to:
- Forward the attacker's identity to the integrated security solution, which then isolates the attacker's system from the network.
- Prevent advanced targeted attacks.
You can contain an attack from the Rules page (Orchestrate > Rules) by creating a response or containment rule, or manually contain the attack from the [Investigate Dashboard](/deception/taking-action-from-the-dashboard).
About the Containment Page
On the Containment page (Orchestrate > Containment), you can do the following:
- View a list of all configured containment integrations. For each integration, you can see:
- **Enabled**: Indicates if the containment integration is enabled or not.
- **Settings**: The name of the third-party security solution.
-
**Blocked IPs/Hostnames**: Total number of blocked attackers.
You can click the number (IP count) to [view the details of the contained attacker](/deception/viewing-contained-attacker-ip-address-details).
- Configure containment integrations on the following supported solutions:
- [Check Point Firewall](/deception/containment-configuration-guide-check-point-firewall)
- [CrowdStrike Falcon Insight](/deception/containment-configuration-guide-crowdstrike)
- [Fortinet](/deception/containment-configuration-guide-fortinet)
- [Microsoft Defender](/deception/containment-configuration-guide-microsoft-defender)
- [Palo Alto Networks](/deception/containment-configuration-guide-palo-alto-networks)
- [VMware Carbon Black EDR](/deception/containment-configuration-guide-vmware-carbon-black-edr)
- [VMware Carbon Black Endpoint Standard](/deception/containment-configuration-guide-vmware-carbon-black-endpoint-standard)
- [Zscaler Internet Access (ZIA)](/deception/containment-configuration-guide-zscaler-internet-access-zia)
- [Zscaler Private Access (ZPA)](/deception/containment-configuration-guide-zscaler-private-access-zpa)
![About the Containment page](/downloads/deception/orchestrate/containment-integrations/about-containment-integration/zscaler-deception-containment-page-new.png)