# Integrating ZPC with Slack
Source: https://help.zscaler.com/zpc/integrating-zpc-slack
PDF: https://help.zscaler.com/pdf/com/en/1456756.pdf

You can integrate Zscaler Posture Control (ZPC) with Slack, a tool for centralized communication and collaboration. ZPC detects various security issues in your public cloud infrastructure and misconfigurations in the CI/CD pipeline. These issues are sent as alert notifications on Slack, so you can investigate and address the issues on a common platform and streamline the mitigation directly into your developer tool.
Prerequisites
Before integrating ZPC with Slack, you must set up the Webhook on Slack:
- [Log in to Slack](https://api.slack.com/apps).
-
Click **Create an App**, then select **From scratch**.
[See image.](#createapp)
-
In the **Name app & choose workspace** window:
- **App Name**: Enter a name for the app.
- **Pick a workspace to develop your app in**: Select the Slack workspace from the drop-down menu.
[See image.](#nameworkspace)
- Click **Create App**.
-
On the **Basic Information** page, select **Incoming Webhooks**.
[See image.](#incomingwh)
-
On the **Incoming Webhooks** page:
- Enable** Activate Incoming Webhooks**.
- Click** Add New Webhook to Workspace**.
[See image.](#activatewh)
-
Select the Slack channel to which ZPC must send notifications, then click **Allow**.
[See image.](#channel)
-
Copy the **Webhook URL**. You must specify this URL when [integrating ZPC with Slack](#integratingstep).
You can add only one Webhook per Slack channel.
[See image.](#copywh)
Integrating with Slack
To integrate ZPC with Slack:
- Go to** Administration** > **Integrations**.
-
In the **ChatOps (Slack)** section,** **click **Add**.
[See image.](#add-integration)
- []On the **Integration Details** page:
- **Integration Name**: Enter a unique name for the integration.
- **Channel Name**: Enter the name of the Slack channel where you want to receive alert notifications.
- **Webhook URL**: Enter the webhook URL that you copied from the Slack portal. The URL allows ZPC to connect and communicate with the Slack channel.
-
**Add More**: Click to include additional channels where you want to receive alert notifications.
ZPC allows you to add 10 channels per integration. You can configure another integration to add more channels.
- [See image.](#integ-details)
- Click **Test Connection** to validate the Slack connection. A confirmation message appears that the Slack connection is verified. If not, then check the previous steps and try again.
-
Review the integration details on the **Summary** page.
[See image.](#summary)
- Click **Finish**.
The Slack integration details are displayed on the **Integrations** page.
[]![Create a new app](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-newapp.png)
[]![Incoming Webhook](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-incoming.png)
[]![Enter the name and workspace](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-appname.png)
[]
[![Select the Slack channel](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-channel.png)
]
[]
[![Copy the Webhook URL](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-copywh.png)
]
[![Add a Slack integration](/downloads/zpc/third-party-integrations/integrating-slack/zpc-add-slackintegration.png)
]
[![Add the integration details](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-integrationdetails.png)
]
[![Review the integration details](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-summary.png)
]
[]
[![Activate Webhook](/downloads/zpc/third-party-integrations/integrating-slack/zpc-slack-activatewebhook.png?1687937448)
]