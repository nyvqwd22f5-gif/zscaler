# OpsGenie Webhook Configuration Guide
Source: https://help.zscaler.com/unified/opsgenie-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1491926.pdf

This guide provides information on configuring webhooks using OpsGenie for alerts in Digital Experience Monitoring. The following instructions provide a sample configuration that can be used based on the user's requirements.
Setting Up Integration Keys on OpsGenie
- Log in to your OpsGenie account.
- Go to **Teams** > **Add Team** and enter the following information:
- **Name**: Enter a team name.
- **Description**: Enter a team description.
- **Add Members**: Search and select which members you want to view the alerts.
- Click **Add Team** to complete the team creation.
[See image.](#add-team)
- Go to the created Team page.
- From the left-side navigation, go to **Integrations** > **Add Integration** > **API**.
[See image.](#Select-API)
- []Click **Copy** or save your API Key. This is also called GenieKey.
[See image.](#API-Key)
- Select the following checkboxes:
- Read Access
- Create and Update Access
- Delete Access
- Enabled
[See image.](#DefaultConfiguration)
If these are already selected by default, you can skip to step 6.
- Click **Save**.
Setting Up Alert Webhooks on Digital Experience Monitoring
- Log in to your Admin account.
- Go to **Administration **> **Alerts**> **Webhooks.**
- Click **Add Webhook**.
- []Enter the following information:
- **Name**: Enter the name of the webhook for OpsGenie.
- **Status**: Select **Enabled**.
- **URL**: Enter your OpsGenie URL. It is normally `https://api.opsgenie.com/v2/alerts?isOpsGenie=true`.
The generic OpsGenie URL is `https://api.opsgenie.com/v2/alerts`.
For Digital Experience Monitoring Integration, `?isOpsGenie=true` must be appended to the URL. The final URL to enter the Digital Experience Monitoring UI is then `https://api.opsgenie.com/v2/alerts?isOpsGenie=true`.
The URL might be different when using an enterprise setup. If there is a specific URL for your organization, you still need to append `?isOpsGenie=true` at the end of your URL to integrate with Digital Experience Monitoring.
- **Authentication Type**: Select **Token**.
- **Bearer Token**: Enter your Bearer Token with the API Key from OpsGenie (also known as GenieKey) in the following format. The green text indicates the insertion of the GenieKey from the previous [Step 4](#CopySaveAPIKey).
GenieKey {GenieKey from the OpsGenie API Portal}
- Click **Save**.
[See image.](#ZDXWebhook)
- Go to **Alerts** > **Rules** > **Add Alert Rule**.
- Configure the Alert Rule settings as needed based on your organization's needs. To learn more, see [Configuring an Alert Rule](/unified/configuring-alert-rule).
- On the **Actions** tab and under the **Actions** section, the following fields are required to integrate with OpsGenie:
- **Muted**: Disable this setting.
- **Webhooks**: Select the Ops Webhook that you created from [Step 3](#AddWebhook).
[See image.](#ZDXAlertRule-Action)
- **Alert Delivery Method**: Select **Webhook**. Email is optional.
- Click **Next**.
- On the **Review** tab, click **Submit** to save the Alert Rule configuration.
- Click **Save** and activate the changes.
Viewing Alerts on OpsGenie
- Go to your OpsGenie home page.
- Go to the **Alerts** page to view a list of alerts, or select an individual alert for more details.
The Alert Title might not display all the characters if the character size exceeds 130 characters. If this happens, the fields are displayed within the description.
[See image.](#OpsGenieAlert)
[]![Add Team Window](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-AddTeam.jpg)
[]![Select API from the Integration list.](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-API.jpg)
[]![Copy or Save the API Key](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-API_Key.jpg)
[]![Default Configuration](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-Configuration.jpg)
[]![ZDX Webhook Configuration](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-ZDXWebhook-0.jpg)
[]![Alert List](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-AlertList.jpg)
![Individual Alert](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-Individual_Alert.jpg)
[]![ZDX Alert Rule Action](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-opsgenie/ZDX-OpsGenie-ZDXAlertRule-Action.jpg)