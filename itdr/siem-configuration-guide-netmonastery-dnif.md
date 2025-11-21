# SIEM Configuration Guide for Netmonastery DNIF
Source: https://help.zscaler.com/itdr/siem-configuration-guide-netmonastery-dnif
PDF: https://help.zscaler.com/pdf/com/en/1531740.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to a Netmonastery DNIF security information and event management (SIEM) solution.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the Netmonastery DNIF server on the port Netmonastery DNIF is listening to.
- Use TCP or UDP protocol depending on the Netmonastery DNIF SIEM configuration.
Configuring a Service Connector to Forward Events to Netmonastery DNIF
To configure a Service Connector to forward events or audit logs to a Netmonastery DNIF SIEM:
- In the Zscaler ITDR Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Netmonastery** **DNIF** from the drop-down menu.
[See image.](#itdr-netmonastery-siem-integration-option)
-
In the **Netmonastery DNIF Details** window:
- **Name**: Enter a name for the Netmonastery DNIF SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu. If you select a Service Connector that is configured in the ITDR Admin Portal, the portal sends logs to Netmonastery DNIF.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to Netmonastery DNIF.
- **Audit Logs**: Send audit logs to Netmonastery DNIF.
- **Include Safe Events**: Enable to forward the events that are marked as safe to Netmonastery DNIF.
-
**Filter**: Specify a query if you want to send filtered event logs to Netmonastery DNIF. If this field is blank, all event logs are sent to Netmonastery DNIF.
The **Filter** option is available only for event logs.
- **Host**: Enter the Netmonastery DNIF server IP address.
- **Port**: Enter the port number the Netmonastery DNIF server is listening to.
- **Transport**: Select **TCP** or **UDP**.
[See image.](#itdr-netmonastery-siem-details)
-
Click **Save**.
The Netmonastery DNIF SIEM integration is added.
To test the Netmonastery DNIF SIEM integration, generate events on the Investigate page. You can see the logs forwarded from the ITDR Admin Portal on the Netmonastery DNIF SIEM solution.
[]![Netmonastery DNIF SIEM Integration option](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-netmonastery-dnif/itdr-add-netmonastery-siem-integration-option.png)
[]![Configure Netmonastery SIEM integration details](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-netmonastery-dnif/itdr-config-netmonastery-siem-details.png)