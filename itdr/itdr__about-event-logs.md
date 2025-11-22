# About Event Logs
Source: https://help.zscaler.com/itdr/about-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531828.pdf

Zscaler ITDR triggers an alert with the attacker's activity logged in event logs. The Event Logs page lists all the event logs.
Event Logs provide the following benefits and enable you to:
- Capture information about attacks attempted by bad actors who infiltrate your network.
- Investigate attacks using the log information, analyze the attacker's target and motives, and then devise enhanced threat response and containment strategies.
- Download the event logs in various formats for further analysis to contain future threats.
About the Event Logs Page
On the Event Logs page (accessed from the [extended details](/itdr/viewing-extended-details) page), you can do the following:
- View the event logs. For each event, you can see:
- **Timestamp**: The time and date when the attack happened.
- **Type**: The attack type (e.g., itdr).
- **Sub Type**: The subtype of the attack.
- **Decoy Group**: The classification of the device (e.g., endpoint).
- **Attacker ID**: The attacker's IP address.
- **Decoy Name**: The actual endpoint name.
- **Decoy Port**: The port used on the endpoint.
- **Decoy Appliance Name**: The name for the ITDR Admin Portal.
- **Kill Chain Phase**: The kill chain attack phase (e.g., lateral movement, exploitation, etc.).
-
Select an event to view the **Event Details** pane that provides the in-depth details of the event.
[See image.](#event-details-event-logs-page)
- [Add or remove fields from the Event Logs page](/itdr/adding-or-removing-fields-event-logs-page).
-
Choose an option from the **Actions **drop-down menu:
- [Delete events](/itdr/deleting-events).
- [Mark events as safe](/itdr/marking-events-safe).
- [Test a rule with events](/itdr/testing-rule-events).
[See image.](#actions-drop-down)
- [Export the event logs](/itdr/exporting-event-logs).
![About Event Logs Page](/downloads/itdr/investigate/extended-details/event-logs/about-event-logs/itdr-about-event-logs.png)
[]![Select an event to view the event details](/downloads/itdr/investigate/extended-details/event-logs/about-event-logs/itdr-event-details-window.png)
[]
![Options in the Actions drop-down menu](/downloads/itdr/investigate/extended-details/event-logs/about-event-logs/itdr-event-logs-actions.png)