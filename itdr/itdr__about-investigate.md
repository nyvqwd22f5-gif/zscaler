# About Investigate
Source: https://help.zscaler.com/itdr/about-investigate
PDF: https://help.zscaler.com/pdf/com/en/1531835.pdf

The Investigate module in Zscaler ITDR allows you to track, analyze, and manage all generated events. The dashboard on the Investigate page provides a visualization of all events, along with a graphical representation of how these entities are connected to each other and to the Zscaler ITDR Admin Portal.
The Investigate module enhances user experience by providing:
- Visibility into attacker behavior through real-time alerts and detailed component views.
- Comprehensive forensic analysis with access to ThreatParse data, event logs, network telemetry, and evidence files.
- Accelerated response capabilities, enabling teams to take swift actions such as containment, blocking, or marking threats as safe.
- Improved threat detection accuracy by correlating attacker activities across multiple deception components.
- Reduced response time, helping teams act decisively before threats escalate.
- Strengthened overall security posture through integrated threat intelligence and streamlined workflows.
About the Investigate Page
On the Investigate page, you can do the following:
- View a graphical representation of all events and the components to which they are connected in the alerts area.
- Filter the events shown in the alerts area using queries and predefined time ranges. You can build complex queries using the purpose-built query language. To learn more, see [Understanding and Building Queries.](https://help.zscaler.com/itdr/understanding-and-building-queries)
- Customize the dashboard by filtering events based on level of details, threat level, etc.
- Manually filter the events that were generated over a specific time period. In addition, you can see how the events were generated sequentially.
![Investigate page shows alerts area, filter, customize dashboard option, and timeline](/downloads/itdr/investigate/understanding-investigate-module/Investigate%20dashboard.png)
Interacting with Components
The components shown in the alerts area are interactive. Click any of them to view details of the events and other components such as, attackers, ITDR Admin Portal, etc.
When you click an attacker icon in the details pane, the associated risk score and timestamps of the first and last events are displayed. You can use the Actions menu to contain, block, or delete threats, or mark an attack as safe, directly from the details pane. To learn more, see [Controlling Threat Events](https://help.zscaler.com/itdr/controlling-threat-events).
You can also automate these actions by [configuring orchestration rules.](https://help.zscaler.com/itdr/about-orchestration-rules)
[See image.](#Action_menu)
[]![Actions Menu to control and manage threat events](/downloads/itdr/investigate/about-investigate/Investigate_GIF.gif)
To further analyze an event or component, click **View Extended Details** in the details pane. The [extended details](https://help.zscaler.com/itdr/viewing-extended-details) window offers insights into:
- **ThreatParse**: Details of the MITRE ATT&CK  framework along with a risk score. To learn more, see [Viewing ThreatParse Details](/itdr/viewing-threatparse-details).
- **Chronology**: A temporal overview and heatmap of the attacker's activities. To learn more, see [Viewing Attack Chronology Details](/itdr/viewing-attack-chronology-details).
- **Event Logs**: Details of activities. To learn more, see [About Event Logs](/itdr/about-event-logs).
[See image](#Details_pane_gif)
[]![Details pane shows risk score, ThreatParse rules, triage incidents, Actions menu, and extended details ](/downloads/itdr/investigate/about-investigate/investigate_extended_details.gif)