# Configuring Webhooks
Source: https://help.zscaler.com/unified/configuring-webhooks
PDF: https://help.zscaler.com/pdf/com/en/1491786.pdf

You can configure webhooks to deliver alerts about your application, device, or network performance. You can also use webhooks in an alert rule and configure multiple alert rules to the same webhook from your third-party provider. To learn more, see [Configuring an Alert Rule](/unified/configuring-alert-rule).
To configure a new webhook in the Admin Portal:
- Go to **Administration **> **Alerts** > **Webhooks**.
-
Click **Add Webhook**.
[See image.](#WebhookURL)
- In the **Add Webhook** window:
- **Name**: Enter the name of the webhook.
- **Status**: Choose either **Enabled** or **Disabled**.
-
**URL**: Enter the URL of the webhook provider.
Ensure your URL does not include any space.
-
**Authentication Type**: Choose either **Basic**, **Token**, or **OAuth** for authentication. The webhook provider determines the authentication type used. Refer to your provider for details.
You can configure OAuth 2.0 for ServiceNow when configuring a webhook. To learn more, see [ServiceNow Webhook Configuration Guide](/unified/servicenow-webhook-configuration-guide).
- [Basic](#Basic)
- [Token](#Bearer)
- [OAuth](#OAuth)
- Click **Test Webhook** to check the configuration.
-
If the test is successful, a message indicating success appears.
Click **Save** to save the webhook configuration and activate the changes.
Test Webhook for OAuth does not post a test message. Instead, it acquires the OAuth token.
- If the test is unsuccessful, an error message appears.
- To resolve the error, check for issues in the **URL** or the **Authentication Type** fields.
- If the error persists, click **Cancel** so that the webhook configuration containing errors is not saved.
After the webhook is configured on your webhook provider site, you can view alert information such as:
- Alert start and end time
- Devices impacted
- Severity
- Rule name
- Alert criteria
[]
Enter a **Username **and** Password**. Password information is hidden by default, but you can view it by clicking the **View** icon.
[See image.](#BasicTab)
[]
Enter the bearer token. A bearer token is a unique alphanumeric string used for authentication. You can obtain the bearer token from your webhook provider.
[See image.](#TokenTab)
[]
Enter the following:
- **Applications**: Select an application.
- **Client ID**: Enter your Client ID.
- **Client Secret**: Enter your Client Secret.
- **Refresh Token Expiration**: Select the date your token expires. The default is the current date.
Click **Authenticate Tenant** to authorize access to your application as a tenant.
[See image.](#OAuthTab)
[]
![Add Webhook URL](/downloads/zdx/alerts/configuring-webhooks/ZDX-ConfiguringWebhook-Add-Window.png)
[]
![Add Bearer Token](/downloads/zdx/alerts/configuring-webhooks/ZDX-ConfiguringWebhook-Add-Authentication-Token.png)
[]
![Add Basic Authentication](/downloads/zdx/alerts/configuring-webhooks/ZDX-ConfiguringWebhook-Add-Authentication-Basic.png)
[]
![Add OAuth Details](/downloads/zdx/alerts/configuring-webhooks/ZDX-ConfiguringWebhook-Add-Authentication-OAuth.png)