# Splunk Webhook Configuration Guide
Source: https://help.zscaler.com/zdx/splunk-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1390521.pdf

This guide provides information on configuring webhooks using Splunk Enterprise for alerts in ZDX. The instructions provide a sample configuration that you can configure based on user requirements.
Setting Up Webhooks in the Splunk Enterprise Instance
After your Splunk Enterprise instance has been installed and is running, follow this sequence to create webhooks:
- Log in to your instance. The home page is displayed.
-
In the top-right corner of the page, click **Settings**.
[See image.](#home-settings)
-
Go to **Data** > **Data inputs**.
[See image.](#data-inputs)
Configure HTTP Event Collector
Configure HTTP Event Collector (HEC) to receive data:
-
Select **HTTP Event Collector **from the list of inputs.
[See image.](#hec-link)
-
In the top-right corner of the page, click **Global Settings**.
[See image.](#global-settings-button)
-
Configure the following Global Settings:
- **All Tokens**: Select **Enabled**.
- **Default Source Type**: Select **_json**.
- **Default Index**: Select **Default**.
- **Default Output Group**: Select **None**.
- Deselect the **Use Deployment Server** checkbox.
- Deselect the **Enable SSL** checkbox.
- **HTTP Port Number**: Enter your HTTP Port Number.
Click **Save**.
[See image.](#EditGlobalSettings)
To learn more about configuring HTTP Event Collector, refer to [Splunk Documentation](https://docs.splunk.com/Documentation/SplunkCloud/latest/Data/UsetheHTTPEventCollector).
[]Create a Token
Create a token to receive data:
- In the top-right corner of the page, click **New Token**.
-
Enter a name for the token. Leave the remaining settings as shown in the following screen:
[See image.](#CreateToken)
- Click **Next**.
-
Configure any additional input settings, then click **Review**.
Your settings are displayed for review.
[See image.](#review-settings)
-
Click **Submit**. A confirmation screen displays the created token.
[See image.](#confirmation)
- Highlight and copy the Token Value.
[]Configuring Splunk Webhooks in ZDX
[To configure a webhook in the ZDX Admin Portal](/zdx/configuring-webhooks):
-
Go to **Administration** > **Integrations** > **Webhooks** > **Add New Webhook**.
-
In the **Add New Webhook** window:
- **Name**: Enter a webhook name for Splunk.
- **Status**: Select **Enabled **to enable the webhook.
- **URL**: Include the following parameter in your URL:
- **Authentication Type**: Select **Basic **or **Token**.
- For Basic, enter any string as the username, and enter the configured HEC Token Value from the previous step.
- For Token, enter the configured HEC Token Value from the previous step as the Bearer Token.
[See image.](#add-new-webhook)
- Click **Save **and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
[]
![Screen to Edit Global Settings](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-global-settings-edit.png)
[]
![Enter name of new token](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-new-token2.png)
[]
![Settings link in upper-right corner of home page](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-home-settings.png)
[]
![Link to select data inputs](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-data-inputs.png)
[]
![Select HTTP Event Collector](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-hec.png)
[]
![Global Settings button](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-global-settings-button.png)
[]
![Screen to review settings](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-review-settings.png)
[]
![Screen confirms token has been created](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-confirmation.png)
[]
![Screen to Add New Webhook](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-add-new-webhook.png)