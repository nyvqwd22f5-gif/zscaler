# SIEM Configuration Guide for Splunk Enterprise and Cloud Platform
Source: https://help.zscaler.com/deception/siem-configuration-guide-splunk
PDF: https://help.zscaler.com/pdf/com/en/1531401.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to the Splunk security information and event management (SIEM) solution.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the Splunk server on TCP port. The default port is 8088.
- Use HTTP or HTTPS protocol depending on the Splunk SIEM configuration.
Configuring a Service Connector to Forward Events to Splunk Enterprise and Cloud Platform
Follow these steps to forward events to Splunk Enterprise and Cloud Platform:
- [Step 1: Generate a Token ID in Splunk](#splunk-siem-generate-api-token)
- [Step 2: Forward Logs to Splunk](#forward-logs-splunk-siem)
- []Log in to a Splunk instance.
- Go to **Settings** > **Data Inputs** > **HTTP Event Collector**.
-
Click **Global Settings**.
[See image.](#config-splunk-siem-global-settings)
-
In the **Edit Global Settings** window:
- **All Tokens**: Select **Enabled**.
- **Default Source Type**: Select **_ json** from the drop-down menu.
- Select the **Enable SSL **checkbox.
[See image.](#splunk-siem-edit-global-settings)
- Click **Save**.
-
On the **HTTP Event Collector** page, click **New Token**.
[See image.](#splunk-siem-new-token-button)
- In the **Add Data** wizard:
- On the **Select Source** page:
-
Enter a **Name** for the new token.
[See image.](#splunk-siem-token-name)
- Click **Next**.
- On the **Input Settings** page:
-
Select **_ json** from the **Select Source Type** drop-down menu.
[See image.](#splunk-siem-input-data-source)
- Click **Review**.
-
On the **Review** page, verify the configuration and click **Submit**.
[See image.](#splunk-siem-review-submit-token-id)
The API token ID is generated.
[See image.](#splunk-siem-token-id-generated)
- Copy the token ID.
- []In the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Splunk **from the drop-down menu.
[See image.](#splunk-siem-add-integration-splunk)
- In the **Splunk Details** window:
- **Name**: Enter a name for the Splunk SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured in the Deception Admin Portal, the portal forwards the logs to Splunk.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector forwards the logs to Splunk.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Forward events to Splunk.
- **Audit logs**: Forward audit logs to Splunk.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](https://help.zscaler.com/deception/controlling-threat-events) to Splunk.
-
**Filter**: Enter queries if you want to filter the logs before forwarding them to Splunk. If this field is blank, all logs are forwarded to Splunk. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
The **Filter** option is available only for event logs.
-
**Host**: Enter the IP address or FQDN of the Splunk server or cloud platform URL.
For the Splunk cloud platform, add `http-input-` to the beginning of the URL. For example, if the URL is `<Splunk instance>``.splunkcloud.com`, enter `http-input-``<Splunk instance>``.splunkcloud.com`.
- **Port**: Enter `8088`.
- **Data Source**: Enter a log identifier. You can use this identifier to filter logs in Splunk.
- **Key**: Enter the [token ID](#splunk-siem-generate-api-token) that you generated.
- **Strict SSL**: If enabled, the SSL certificate on the Splunk server is validated by a list of public certificate authorities. If disabled, then the SSL certificate verification is disabled.
-
**Use Proxy Settings (if available)**: Enable if you want to use proxy settings on the Service Connector, if available. This can be useful for Splunk cloud instances.
[See image.](#config-splunk-details)
-
Click **Save**.
The Splunk SIEM integration entry is added.
To test the Splunk SIEM integration, access a decoy and generate alerts on the [Zscaler Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard). You can see the forwarded logs on the Splunk instance.
[See image.](#logs-forwarded-to-splunk)
[]![Global Settings button in the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-global-settings.png)
[]![Edit Global Settings in the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-edit-global-settings.png)
[]![New Token button in the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/deception-splunk-deployment-guide/zscaler-deception-siem-integration-new-token-option-1.png)
[]![Enter a name for the new token in the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-add-data-select-source.png?1662548094)
[]![Select incoming data source format](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-add-data-input-settings.png?1662548395)
[]![Review and submit new token ID configuration ](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-add-data-review-submit.png)
[]![The new token ID is generated in the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-add-token-generated.png)
[]![Navigate to Splunk SIEM integration option](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-select-splunk.png)
[]![Configure Splunk SIEM integration details](/downloads/deception/orchestrate/siem-integrations/deception-splunk-deployment-guide/zscaler-deception-siem-integration-config-splunk-details-3.png)
[]![Logs forwarded to the Splunk SIEM](/downloads/deception/orchestrate/siem-integrations/forwarding-logs-splunk/zscaler-deception-siem-integration-events-triggered-splunk.png)