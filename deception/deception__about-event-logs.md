# About Event Logs
Source: https://help.zscaler.com/deception/about-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531373.pdf

When an attacker interacts with a decoy, Zscaler Deception triggers an alert with the attacker's activity logged in event logs. The Event Logs page lists all the event logs.
Event Logs provide the following benefits and enable you to:
- Capture information about attacks attempted by bad actors who infiltrate your network and interact with the decoys configured and deployed using Deception.
- Investigate attacks using the log information and analyze the attacker's target and motives to devise enhanced threat response and containment strategies.
- Download the event logs in various formats for further analysis to contain future threats.
About the Event Logs Page
On the Event Logs page (accessed from the [extended details](/deception/viewing-extended-details) page), you can do the following:
- View the event logs. For each event, you can see:
- **Timestamp**: The time and date when the attack happened.
- **Attack type**: The attack type (e.g., network, web, etc.).
- **Attacker ID**: The attacker's IP address.
- **Decoy name**: The name of the decoy with which the attacker interacted.
- **Decoy port**: The port number of the decoy.
- **Decoy Connector**: The name of the Decoy Connector.
- **Kill chain phase**: The kill chain attack phase (e.g., lateral movement, exploitation, etc.).
-
Select an event to view the **Event Details** pane that provides the in-depth details of the event.
[See image.](#event-details-event-logs-page)
- [Add or remove fields from the Event Logs page](/deception/adding-removing-fields-event-logs).
-
Choose an option from the **Actions **drop-down menu:
- [Delete events](/deception/deleting-events).
- [Mark events as safe](/deception/marking-events-safe).
- [Test a rule with events](/deception/testing-rule-events).
[See image.](#actions-drop-down)
- [Export the event logs](/deception/exporting-event-logs).
![A screenshot showing the Event Logs page with annotations](/downloads/deception/investigate/accessing-extended-details/event-logs/about-event-logs/zscaler-deception-about-event-logs_1.jpg)
[]![Select an event to view the event details](/downloads/deception/investigate/accessing-extended-details/event-logs/about-event-logs/zscaler-deception-event-details.jpg)
[]
![A screenshot highlighting the options in the Actions drop-down menu](/downloads/deception/investigate/accessing-extended-details/event-logs/about-event-logs/zscaler-deception-action-event-logs.jpg)