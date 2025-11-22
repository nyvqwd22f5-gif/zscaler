# Customizing Event Notification Templates
Source: https://help.zscaler.com/deception/customizing-event-notification-templates
PDF: https://help.zscaler.com/pdf/com/en/1531400.pdf

Zscaler Deception allows you to send event notifications when a threat is detected. Event notifications are sent as emails. You can enable notifications and customize the default email notification template.
Customizing the Email Notification Template
By default, the subject line for the email notification uses the text:
{kill_chain_phase} activity on {decoy.appliance.name}
You can modify this text using the built-in events.
You cannot change the template of the email body. However, you can include more event fields in the email body.
To customize the email notification template:
- Go to **Orchestrate** > **Event Templates**.
- Select **Enable Custom Templates**.
- Under **Email Subject**, enter the text and built-in events (within the curly braces).
- Under **Email Custom Fields**, enter the built-in events that you want to include in the email body. If **Email Custom Fields** is blank, the default list of events is sent in the email body.
[See image.](#customize-email-body-include-fields)
- Click **Save**.
[]![Customize email notification template](/downloads/deception/orchestrate/event-templates/customizing-event-notification-templates/zscaler-deception-customize-email-template.png)