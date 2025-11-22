# Splunk Webhook Configuration Guide
Source: https://help.zscaler.com/unified/splunk-webhook-configuration-guide
PDF: https://help.zscaler.com/pdf/com/en/1491976.pdf

This guide provides information on configuring webhooks using Splunk Enterprise for alerts in Digital Experience Monitoring. The instructions provide a sample configuration that can be enhanced, depending on user requirements.
Setting Up Webhooks in the Splunk Enterprise Instance
After your Splunk Enterprise instance has been installed and is running, follow this sequence to create webhooks:
- Log in to your instance. The home page is displayed.
- In the top-right corner of the page, click **Settings**.
[See image.](#home-settings)
- Within the Data section, select **Data inputs**.
[See image.](#data-inputs)
Configure HTTP Event Collector
Configure HTTP Event Collector (HEC) to receive data:
- Select **HTTP Event Collector **from the list of inputs.
[See image.](#hec-link)
- In the top-right corner of the page, click **Global Settings**.
[See image.](#global-settings-button)
- Configure the Global Settings as shown in the following example screen:
- Set All Tokens to **Enabled**.
- Set the Default Source Type to **json**.
- Leave the Default Index as **Default**.
- Leave the Default Output Group as **None**.
- Deselect the check boxes for Use Deployment Server and Enable SSL.
![Screen to Edit Global Settings](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-global-settings-edit.png)
To learn more about configuring HTTP Event Collector, refer to [Set up and use HTTP Event Collector in Splunk Web](https://docs.splunk.com/Documentation/SplunkCloud/8.1.2103/Data/UsetheHTTPEventCollector).
- Click **Save**.
[]Create a Token
Create a token to receive data:
- In the top-right corner of the page, click **New Token**.
- Enter a name for the token. Leave the remaining settings as shown on the following screen:
![Enter name of new token](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-new-token2.png)
- Click **Next**.
- Configure any additional input settings, then click **Review**.
Your settings are displayed for review.
[See image.](#review-settings)
- Click **Submit**. A confirmation screen displays the created token.
[See image.](#confirmation)
- Highlight and copy the Token Value. The string will be used for [Configuring Splunk Webhooks in Digital Experience Monitoring ](#webhooks-zdx).
[]Configuring Splunk Webhooks in Digital Experience Monitoring
To configure webhooks in Digital Experience Monitoring:
- Go to **Administration** > **Alerts **> **Webhooks**.
- Click **Add Webhook**.
- In the **Add Webhook** window:
- **Name**: Enter a webhook name for Splunk.
- **Status**: Select **Enabled **to enable the webhook.
- **URL**: Include the following parameter in your URL:
isSplunk=true
- **Authentication Type**: Select either **Basic **or **Token**.
- For Basic, enter any string as the username, and enter the configured HEC Token Value from [Create a Token](#create-token) as your password.
- For Token, enter the configured HEC Token Value from [Create a Token](#create-token) as the Bearer Token.
[See image.](#add-new-webhook)
- Click **Save**.
To learn more about configuring webhooks and testing your configuration, see [Configuring Webhooks](/unified/configuring-webhooks).
[]![Settings link in upper-right corner of home page](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-home-settings.png)
[]![Link to select data inputs](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-data-inputs.png)
[]![Select HTTP Event Collector](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-hec.png)
[]![Global Settings button](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-global-settings-button.png)
[]![Screen to review settings](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-review-settings.png)
[]![Screen confirms token has been created](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-confirmation.png)
[]![Screen to Add New Webhook](/downloads/zdx/alerts/webhook-configuration-guides-supported-platforms/webhook-configuration-guide-splunk/zdx-splunk-webhooks-add-new-webhook.png)