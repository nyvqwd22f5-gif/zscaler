# Exporting Event Logs
Source: https://help.zscaler.com/itdr/exporting-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531823.pdf

Zscaler ITDR triggers an event with all the activity logs. You can download the summary and event logs to analyze and orchestrate actions to contain the threat.
You can export:
- The attacker summary in JSON and CSV formats.
- The event logs in JSON and CSV formats. By default, the event logs in the CSV format include event ID, timestamp, type, etc. You can [add additional fields](/itdr/adding-or-removing-fields-event-logs-page), if required. The event logs in the JSON format include all the fields.
- The event fields in JSON format. This format includes all the event fields.
- The event logs in STIX (Structured Threat Information eXpression) format.
- The snort rules for the event logs.
To export event logs:
- Open the [extended details](/itdr/viewing-extended-details) page.
- Click **Event Logs.**
-
Click the **Export** drop-down menu and select an option (e.g., **Events as CSV**).
[See image.](#export-logs)
The event logs in the desired format are exported to your local system.
[]![Export Event Logs](/downloads/itdr/investigate/extended-details/event-logs/exporting-event-logs/itdr-export-event-logs_0.png)