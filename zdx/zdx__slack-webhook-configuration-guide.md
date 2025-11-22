# Slack Webhook Configuration Guide
Source: https://help.zscaler.com/zdx/slack-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1376321.pdf

This guide provides information on configuring webhooks using Slack for alerts in ZDX per user requirements. Incoming webhooks provide a simple way to post messages from ZDX to Slack. The incoming webhook provides a unique URL that sends a JSON payload with the message text.
Configuring a Webhook for a Paid Slack Subscription
A paid Slack subscription is required to use the Slack Workflow Builder.
To configure a workflow for your Slack application to send notifications to a selected Slack channel:
- In your Slack application:
-
Go to** Workspace **> **Tools **> **Workflow Builder**.
[See image.](#WorkflowBuilder)
-
In the **Workflow Builder**, click **Create**.
[See image.](#CreateWorkflow)
- Enter a name for the workflow.
-
Select **Webhook - Advanced**.
[See image.](#Webhook-Adv)
-
Add variables as needed for ZDX alerts. These variables dictate which fields from the webhook notification are displayed in the Slack notification.
[See image.](#SelectVariables)
- Click **Save**.
-
Select the action for this webhook. The action sends a message to the selected Slack channel.
You can adjust the message as preferred.
Click **Save**.
[See image.](#SelectAction)
- Click **Publish Changes**.
- In your desktop Slack app, go to **Workspace** > **Tools** > **Workflow Builder**.
-
[]Select your newly created workflow and go to **Edit** > **Webhook** > **Copy URL**.
[See image.](#CopyURL)
- [Create a webhook in the ZDX Admin Portal](/zdx/configuring-webhooks).
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
- In the **Add a New Webhook** window:
- **Name**: Enter a webhook name.
- **Status**: Select **Enable**.
- **URL**: Enter your copied URL from previous step.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: Enter any text as a bearer token is not required.
- Click **Test Webhook** and verify the test result appears on the assigned Slack channel.
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
Configuring a Webhook for a Free Slack Subscription
To configure a workflow for your free Slack application to send notifications to the selected Slack channel:
- On your desktop Slack application's workspace:
- Go to [Slack's Your Apps website](https://api.slack.com/apps).
-
Click **Create an App**.
[See image.](#slack_createapp)
-
Select **From scratch**.
[See image.](#slack_createapp_fromscratch)
-
In the **Name app & choose workspace** window:
- **App Name**: Enter a name for your application.
- **Pick a workspace to develop your app in**: Assign a workspace for your application.
Click **Create App**.
[See image.](#slack_createapp_nameappworkspace)
- After the redirection to the Slack settings page, go to **Features** > **Incoming Webhooks**.
- Enable **Activate Incoming Webhooks**.
- After the Slack settings page refreshes, click **Add New Webhook to Workspace**.
- Select an existing channel or create a new one to send the webhook messages to.
- []Click **Copy** for the webhook URL.
- [Create a webhook in the ZDX Admin Portal](/zdx/configuring-webhooks).
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
- In the **Add a New Webhook** window:
- **Name**: Enter a webhook name.
- **Status**: Select **Enable**.
- **URL**: Enter your copied URL from the previous step.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: Enter any text as Slack does not require a bearer token.
- Click **Test Webhook** and verify the test result appears on the assigned Slack channel.
- Click **Save **and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
[![Workflow Builder in Slack ](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_Slack_webhookbuilder.png)
]
[]
[![Create a Workflow in Slack ](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_CreateWorkflowbuilder.png)
]
[]
[![Choose Webhook in Slack ](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_WebhookAdvanced.png)
]
[]
[![Add Variables in Slack Workflow](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_Slack_variables.png)
]
[]
[![Add the Action in Slack ](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_Slack_Action.png)
]
[]
[![Copy Webhook URL ](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX_CopyWebhookURL.png)
]
[]
![Click Create an App](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX%20-%20Slack-%20Your%20App-%20Click%20Create%20an%20App.jpg?1688168660)
[]
![Select From Scratch](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX-%20Slack-%20Create%20an%20App%20selection.jpg?1688168715)
[]
![Enter Application Name and Select Workspace](/downloads/zdx/alerts/webhook-configuration-guide-slack/ZDX%20-%20Slack-%20Your%20App-%20Name_Workspace.jpg)