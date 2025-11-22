# Microsoft Teams Webhook Configuration Guide
Source: https://help.zscaler.com/unified/microsoft-teams-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1491911.pdf

You must have a Microsoft Teams account to configure a webhook.
This guide provides information on configuring webhooks using Microsoft Teams for alerts in ZDX. The following instructions provide a sample configuration that can be used based on the user’s requirements.
- Select the team in which you want to add a channel for webhook notifications.
- Click **More Actions** (**…**) > **Add channel**.
[See image.](#addChannel)
- Enter the name of the channel and save your changes.
For example purposes, the channel is called Zscaler Webhook Channel.
- On the **Posts** tab, where you can see the conversation, go to **Channel** > **Connectors** > **Incoming Webhook** > **Configure**.
[See image.](#configureWebhook)
- Enter the name of the webhook. Adding an image is optional. Click **Create**.
For example purposes, the webhook name is called Alerting Information.
[See image.](#webhookName)
- Copy the Zscaler Webhook Channel’s URL on the webhook configuration page.
[See image.](#copyURL)
- Click **Save**.
- Open and login to your ZDX Admin account.
- Go to **Administration** > **Alerts **> **Webhooks.**
- Click **Add Webhook**.
- Enter the following information:
- **Name**: The name of the webhook for Microsoft Teams.
- **Status**: Select **Enabled**.
- **URL**: The URL you copied from the Microsoft Teams webhook configuration page.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: Enter `1234`.
Due to the nature of the Microsoft Teams webhook, a bearer token will not be checked.
[See image.](#ZDXAdminAddNewWebhook)
- (Optional) Click **Test Webhook** to confirm the webhook configuration works. Verify within the Microsoft Teams Webhook Channel from step 3.
[See image.](#testWebhook)
- Click **Save**.
Managing Incoming Webhooks in Microsoft Teams
To manage your configured webhooks for Microsoft Teams to update the URL or generate a new URL, select the impacted channel and go to Configured > Manage.
[See image.](#manageTeamsWebhook)
[]![On Microsoft Teams, add a channel to generate a webhook.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-addchannel-0.jpg)
[]![Go to Connector to find webhook page](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-connectors.jpg)
[]![Select Configure from the Incoming Webhook on Configured.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-incomingwebhooks.jpg)
[]![Enter name for the webhook.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-webhookname-0.jpg?1674074899)
[]![Copy the webhook configuration URL](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-CopyURL.jpg)
[]![Add New Webhook in the ZDX Administration.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-administration-webhooks-addnewwebhook.jpg)
[]![Test Webhook Result](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/ZDX-TestWebhookOnTeams-0.jpg)
[]![Manage the Microsoft Teams webhook as needed.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-managewebhook.jpg)