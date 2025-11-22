# SIEM Configuration Guide for IBM QRadar
Source: https://help.zscaler.com/deception/siem-configuration-guide-ibm-qradar
PDF: https://help.zscaler.com/pdf/com/en/1531408.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to the IBM QRadar security information and event management (SIEM) solution.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the QRadar server on the port QRadar is listening to.
- Use either the TCP or UDP protocol depending on the QRadar server's configuration.
Configuring a Service Connector to Forward Events to IBM QRadar
Follow these steps to configure a Service Connector to forward events or audit logs to IBM QRadar:
- [Step 1: Forward Logs to QRadar](#qradar-siem-integration-forward-logs)
- [Step 2: Create a Log Source Type in QRadar](#qradar-siem-create-log-source)
- [Step 3: Create a Custom Log Source Extension in QRadar](#qradar-siem-log-source-extension)
- [Step 4: Add a Log Source to QRadar](#qradar-siem-integration-add-log-source)
- []In the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **IBM QRadar** from the drop-down menu.
[See image.](#qradar-siem-integration-option)
-
In the **QRadar Details** window:
- **Name**: Enter a name for the QRadar SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured on the Deception Admin Portal, the portal sends logs to QRadar.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector sends logs to QRadar.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to QRadar.
- **Audit Logs**: Send audit logs to QRadar.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](/deception/taking-action-from-the-dashboard#mark-as-safe) to QRadar.
- **Filter**: Specify a query if you want to send filtered event logs to QRadar. If this field is blank, all event logs are sent to QRadar. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
- **Host**: Enter the QRadar server IP address.
- **Port**: Enter the port number the QRadar server is listening to.
- **Transport**: Select **TCP** or **UDP**.
- **Facility**: Select a facility code (e.g., **User**) from the drop-down menu. Each event is labeled with a facility code, indicating the type of software generating the event logs.
- **Severity**: Select a severity level (e.g., **Debug**) from the drop-down menu. Each event is labeled with a severity, indicating the severity of the tool generating the event logs.
- **App Name**: Enter a log identifier (e.g., `Zscaler Deception`).
[See image.](#config-qradar-siem-integration-details)
-
Click **Save**.
The QRadar SIEM integration is added.
- []Open an IBM QRadar SIEM console.
- Go to **Admin** > **DSM Editor**.
- In the **Select Log Source Type** window, click **Create New**.
- Under **Log Source Type Name**, enter a name for the log source type.
- Click **Save**.
- Select the log source that you created and map the event fields with the help of raw logs. To learn more about event mapping, refer to the [IBM documentation](https://www.ibm.com/docs/en/qsip/7.5?topic=mapping-creating-event-map-categorization).
- []Go to **Admin** > **Log Source Extension**.
- Click **Add**.
- In the **Add Log Source Extension** window:
- Enter the name of the log source extension.
- Enter the description of the log source extension.
- Select the [log source type](#qradar-siem-create-log-source) that you created.
- Click **Save**.
- []Go to **Admin** > **Data Sources** > **Events**.
- Click **Log Sources** > **Add**.
- In the** Add a log source** window:
- **Log Source Name**: Enter a name for log source.
- **Log Source Description**: Enter a description for the log source.
- **Log Source Type**: Select the [log source type](#qradar-siem-create-log-source) you created from the drop-down menu.
- **Protocol Configuration**: Select **Syslog** from the drop-down menu.
- **Log Source Identifier**: Enter `service-connector`.
- **Enabled**: Select this checkbox to enable log source.
- Click **Save**.
- Go to the **Admin** page, and click **Deploy Changes** to activate the new log source.
To test the QRadar SIEM integration, access a decoy and generate alerts on the [Zscaler Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard). The QRadar console starts receiving logs.
[]![IBM QRadar SIEM integration option](/downloads/deception/orchestrate/siem-integrations/deception-and-ibm-qradar-deployment-guide/zscaler-deception-qradar-siem-integration-option.png)
[]![Configure IBM QRadar SIEM integration details](/downloads/deception/orchestrate/siem-integrations/deception-and-ibm-qradar-deployment-guide/zscaler-deception-qradar-siem-integration-details-2.png)