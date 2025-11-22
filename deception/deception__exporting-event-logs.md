# Exporting Event Logs
Source: https://help.zscaler.com/deception/exporting-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1531367.pdf

When an attacker interacts with a decoy, Zscaler Deception triggers an event with all the activity logs of the attacker. You can download the attacker summary and event logs to analyze and orchestrate actions to contain the threat.
You can export:
- The attacker summary in JSON and CSV formats. The attacker’s summary includes the attacker's hostname and IP address, details of the decoys the attacker interacted with, first and last seen timestamps, etc.
- The event logs in JSON and CSV formats. By default, the event logs in the CSV format include event ID, timestamp, decoy details, etc. You can [add additional fields](/deception/adding-removing-fields-event-logs), if required. The event logs in the JSON format include all the fields.
- The event fields in JSON format. This format includes all the event fields.
- The event logs in STIX (Structured Threat Information eXpression) format.
- The snort rules for the event logs.
To export event logs:
- Open the [extended details](/deception/viewing-extended-details) page.
- Click **Event Logs.**
-
Click the **Export** drop-down menu and select an option (e.g., **Events as CSV**).
[See image.](#export_event_logs)
The event logs in the desired format are exported to your local system.
[See image.](#event_logs_exported_in_the_CSV_format)
[]![Export event logs ](/downloads/deception/investigate/accessing-extended-details/event-logs/exporting-event-logs/zscaler-deception-export-event-logs_1.png)
[]![Event logs exported in the CSV format](/downloads/deception/investigate/exporting-event-logs/zscaler-deception-event-logs-csv.png)