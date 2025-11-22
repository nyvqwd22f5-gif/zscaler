# SIEM Configuration Guide for Microsoft Sentinel
Source: https://help.zscaler.com/deception/siem-configuration-guide-microsoft-sentinel
PDF: https://help.zscaler.com/pdf/com/en/1531407.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to Microsoft Sentinel.
Prerequisites
Make sure the following prerequisites are met:
- Create a log analytics workspace on Sentinel. To learn more, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/sentinel/quickstart-onboard).
- Have network connectivity between the Service Connector and Sentinel API server on TCP port 443.
- Use the TCP protocol.
The Sentinel SIEM integration is proxy-aware if direct network connectivity is not available.
Configuring a Service Connector to Forward Events to Sentinel
Follow these steps to configure a Service Connector to forward events or audit logs to Microsoft Sentinel:
- [Step 1: Obtain the Log Analytics Workspace ID and Primary Key from the Microsoft Azure Portal](#obtain-ws-id-primary-key)
- [Step 2: Forward Logs to Sentinel](#forward-logs-to-azure-sentinel-siem-integration)
- []Log in to the [Microsoft Azure portal](http://portal.azure.com/) using your credentials.
- Go to **Azure services** > **Microsoft Sentinel**.
- Open the workspace that you created for the Sentinel SIEM integration.
- Go to **Settings** > **Agents management**.
- Click the **Windows servers** tab.
-
Copy the **Workspace ID** and **Primary key**.
[See image.](#azure-sentinel-copy-ws-id)
- []In the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Sentinel** from the drop-down menu.
[See image.](#azure-sentinel-siem-integration-option)
-
In the **Sentinel Details** window:
- **Name**: Enter a name for the Sentinel SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured in the Deception Admin Portal, the portal sends logs to Sentinel.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector sends logs to Sentinel.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to Sentinel.
- **Audit Logs**: Send audit logs to the Sentinel.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](/deception/taking-action-from-the-dashboard#mark-as-safe) to Sentinel.
-
**Filter**: Specify a query if you want to send filtered event logs to Sentinel. If this field is blank, all event logs are sent to Sentinel. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
The **Filter** option is available only for event logs.
- **Workspace ID**: Enter the [Workspace ID](#obtain-ws-id-primary-key) you copied from Sentinel.
- **Primary Key**: Enter the [Primary key ](#obtain-ws-id-primary-key)you copied from Sentinel.
- **Log Type**: Enter an identifier for the log type.
- **Use Proxy Settings**: Enable if the Service Connector requires a proxy to connect to the Sentinel server.
[See image.](#config-azure-sentinel-siem-integration-details)
-
Click **Save**.
The Sentinel SIEM integration is added.
To test Sentinel SIEM integration, access a decoy and generate alerts on the [Zscaler Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard). The Sentinel starts receiving the logs in 10 to 15 minutes.
[]![Copy the Workspace ID and Primary key from Azure Sentinel](/downloads/deception/orchestrate/siem-integrations/deception-and-microsoft-azure-sentinel-deployment-guide/zscaler-deception-azure-sentinel-siem-integration-ws-id.png?1666942833)
[]![Sentinel SIEM integration option](/downloads/deception/orchestrate/siem-integrations/siem-configuration-guide-microsoft-sentinel/zscaler-deception-sentinal-integration-option-1.png)
[]![Sentinel SIEM integration details](/downloads/deception/orchestrate/siem-integrations/siem-configuration-guide-microsoft-sentinel/zscaler-deception-sentinal-integration-details.png)