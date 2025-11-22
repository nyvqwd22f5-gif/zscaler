# Configuring Webhooks
Source: https://help.zscaler.com/risk360/configuring-webhooks
PDF: https://help.zscaler.com/pdf/com/en/1483191.pdf

You can configure and use webhooks in an alert rule and assign multiple alert rules to the same webhook from your third-party provider for alert delivery.
To configure a webhook:
-
Go to **Alerts **> **Webhooks** > **Add Webhook**.
The **Add New Webhook** drawer appears.
- In the **Add New Webhook** drawer:
- **Name**: Enter the name of the webhook.
- **Status**: Select **Enabled** or **Disabled **for the webhook.
- **URL**: Enter the URL of the webhook provider. Ensure the URL does not include any spaces.
-
[]**Authentication Type**: Select the authentication type for the webhook from **Basic **or **Token**. The webhook provider determines the authentication type used. Refer to your provider for details.
- [Basic](#Basic)
- [Token](#Bearer)
[See image.](#WebhookURL)
-
Click **Save** to save the webhook configuration.
If the webhook is configured successfully, the [Alert Status](/risk360/about-alerts) field on the Webhooks page displays **Active**. If not, the field displays **Error**. To resolve the error, check for issues in the **URL** or the **Authentication Type** fields.
[]
Enter a **Username **and** Password**. Password information is hidden by default. You can view it by clicking the **View** icon.
[]
Enter the bearer token. A bearer token is a unique alphanumeric string used for authentication. You can obtain the bearer token from your webhook provider.
[]![Add Webhook Drawer](/downloads/risk360/configuring-webhooks/Risk360-Add-Webhookpng.png)