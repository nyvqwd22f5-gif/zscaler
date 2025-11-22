# Microsoft Teams Webhook Configuration Guide
Source: https://help.zscaler.com/zdx/microsoft-teams-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1440861.pdf

You must have a Microsoft Teams account to configure a webhook.
This guide provides information on configuring webhooks using Microsoft Teams for alerts in ZDX. The following instructions provide a sample configuration that you can use based on the user’s requirements.
- In Microsoft Teams:
- Select the team in which you want to add a channel for webhook notifications.
-
Click **More Actions** (**…**) > **Add channel**.
[See image.](#addChannel)
- []Enter the name of the channel and save your changes.
-
On the **Posts** tab, where you can see the conversation, go to **Channel** > **Connectors** > **Incoming Webhook** > **Configure**.
[See image.](#configureWebhook)
-
Enter the name of the webhook. Adding an image is optional. Click **Create**.
[See image.](#webhookName)
-
[]Copy the Zscaler Webhook Channel’s URL from the webhook configuration page.
[See image.](#copyURL)
- Click **Save**.
- [Create a webhook in the ZDX Admin Portal](/zdx/configuring-webhooks).
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
-
Enter the following information:
- **Name**: The name of the webhook for Microsoft Teams.
- **Status**: Select **Enabled**.
- **URL**: Paste the URL you copied from the Microsoft Teams webhook configuration page from the previous step.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: Microsoft Teams does not generate a bearer token. To meet webhook configuration requirements, enter any text for the bearer token (e.g., `1234`).
[See image.](#ZDXAdminAddNewWebhook)
-
(Optional) Click **Test Webhook** to confirm the webhook configuration works.
[See image.](#testWebhook)
- Click **Save**.
Managing Incoming Webhooks in Microsoft Teams
To manage your configured webhooks for Microsoft Teams to update the URL or generate a new URL, select the impacted channel and go to **Configured** > **Manage**.
[See image.](#manageTeamsWebhook)
[][![On Microsoft Teams, add a channel to generate a webhook.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-addchannel-0.jpg)
]
[][![Connector](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-connectors-1.jpg)
]
![Select Configure from the Incoming Webhook on Configured.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-incomingwebhooks.jpg)
[][![Enter name for the webhook.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-webhookname-0.jpg?1674074899)
]
[][![Copy URL](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-CopyURL-1.jpg)
]
[][![Add New Webhook in ZDX](/downloads/zdx/alerts/configuring-webhooks/ZDX-Add-New-Webhook-Example-Token.png)
]
[][![Test Webhook Result](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/ZDX-TestWebhookOnTeams-0.jpg)
]
[][![Manage the Microsoft Teams webhook as needed.](/downloads/zdx/alerts/webhook-configuration-microsoft-teams/zdx-webhookconfiguration-microsoftteams-managewebhook.jpg)
]