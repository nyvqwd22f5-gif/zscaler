# Integrating with Slack
Source: https://help.zscaler.com/dspm/integrating-slack
PDF: https://help.zscaler.com/pdf/com/en/1487526.pdf

You can integrate DSPM with Slack, a tool for centralized communication and collaboration. DSPM detects sensitive data or misconfigurations in the cloud resources and generates alerts. These alert notifications are sent to the configured Slack channels so you can investigate and address the issues on a common platform and streamline the mitigation directly into your developer tool.
Prerequisites
Before integrating DSPM with Slack, you must set up the webhook on Slack. Incoming webhooks are used to post messages from the DSPM app to Slack. The incoming webhook provides a unique URL to which you send a JSON payload with the message text. To learn more, refer to the [Slack documentation](https://api.slack.com/messaging/webhooks#:~:text=Incoming%20webhooks%20are%20a%20way,make%20the%20messages%20stand%20out.).
- Log in to [Slack](https://api.slack.com/apps).
-
Click **Create an App**, then select **From scratch**.
[See image.](#ds-slack-createapp)
-
In the **Name app & choose workspace** window:
- **App Name**: Enter a name for the app.
- **Pick a workspace to develop your app in**: Select the Slack workspace from the drop-down menu.
[See image.](#ds-slack-choosews)
- Click **Create App**.
-
On the **Basic Information** page, select **Incoming Webhooks**.
[See image.](#ds-slack-incomingwh)
-
On the **Incoming Webhooks** page:
- Enable** Activate Incoming Webhooks**.
- Click** Add New Webhook to Workspace**.
[See image.](#ds-slack-configurewh)
-
Select the Slack channel to which DSPM must send notifications, then click **Allow**.
[See image.](#ds-slack-permissions)
-
Copy the **Webhook URL**. You must specify this URL when [integrating DSPM with Slack](#integratingstep).
You can add only one Webhook per Slack channel.
[See image.](#ds-copywh)
Integrating with Slack
To integrate DSPM with Slack:
- Go to** Administration** > **Integrations**.
-
In the **ChatOps (Slack)** section, click **Add**.
[See image.](#ds-chat-addbutton)
-
[]On the **Integration Details** page:
- **Integration Name**: Enter a unique name for the integration.
- **Channel Name**: Enter the name of the Slack channel where you want to receive alert notifications.
- **Webhook URL**: Enter the webhook URL that you copied from the Slack portal. The URL allows DSPM to connect and communicate with the Slack channel.
-
**Add More**: Click to include additional channels where you want to receive alert notifications.
DSPM allows you to add 10 channels per integration. You can configure another integration to add more channels.
[See image.](#ds-slack-details)
- Click **Test Connection** to validate the Slack connection. A confirmation message appears that the Slack connection is verified. If not, then check the previous steps and try again.
-
Review the integration details on the **Summary** page.
[See image.](#ds-slack-review)
- Click **Finish**.
The Slack integration details are displayed on the **Integrations** page.
[]![Add a Slack integration](/downloads/zpc/third-party-integrations/chatops-tools/integrating-zpc-slack/ds-slack-addbutton.png)
[]![Configure the Slack integration](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-chatops-details.png)
[]
[]![Review the configuration](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-review.png)
[]![Create the DSPM app](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-createapp.png)
[]![Select a workspace](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-chooseworkspace.png)
[]![Select incoming webhooks option](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-incomingwebhooks.png)
[]![Configure webhooks](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-webhooks.png)
[]![Grant permissions to the app](/downloads/dspm/third-party-integrations/chatops-tools/integrating-slack/ds-slack-permission.png)
[]![Copy the webhook URL](/downloads/dspm/third-party-integrations/integrating-dspm-slack/ds-slack-copywh.png)