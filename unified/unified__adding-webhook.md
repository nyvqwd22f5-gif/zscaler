# Adding a Webhook
Source: https://help.zscaler.com/unified/adding-webhook
PDF: https://help.zscaler.com/pdf/com/en/1530728.pdf

Webhook configuration in the Admin Portal allows you to deliver alerts for the configured events in the alert rule to third-party applications (e.g., ServiceNow, Splunk, etc.) for incident management. The feature comprises two parts:
- Creating a webhook
- Associating the webhook with the alert rules
To add a webhook:
- Go to **Administration** > **Alerts **>** Security & UEBA Alerts** > **Webhooks**.
-
Click **Add Webhook**.
The **Add Webhook** window appears.
- In the **Add Webhook **window:
- **Name**: Enter a name for the webhook.
- **Status**: Choose **Disabled** to disable the webhook. By default, the field is **Enabled**.
- **URL**: Enter the URL of the webhook provider
- **Authentication Type**: Choose either **Basic** or **Token** for authentication. The webhook provider determines the authentication type used. Refer to your provider for details.
- For **Basic**, enter the **Username **and** Password**.
- For **Token**, enter the **Bearer Token**. A bearer token is a unique alphanumeric string used for authentication. You can obtain the bearer token from your webhook provider.
-
Click **Test Webhook** to check the configuration.
If the test is successful, a message indicating success appears.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).