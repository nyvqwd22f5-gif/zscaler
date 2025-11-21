# SIEM Configuration Guide for Syslog
Source: https://help.zscaler.com/deception/siem-configuration-guide-syslog-server
PDF: https://help.zscaler.com/pdf/com/en/1531402.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to a Syslog security information and event management (SIEM) server.
Prerequisites
Before configuring a Service Connector to forward logs to Syslog, ensure that you:
- Have network connectivity between the Service Connector and the Syslog server on the port Syslog is listening to.
-
Use TCP or UDP protocol depending on the Syslog server's configuration.
Zscaler recommends that you use the TCP protocol to avoid any issues with the UDP protocol's unreliability, frame limits, and fragmented packets.
Configuring a Service Connector to Forward Events to Syslog SIEM
To configure a Service Connector to forward events or audit logs to a Syslog SIEM server:
- []In the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Syslog** from the drop-down menu.
[See image.](#syslog-add-siem-integration-option)
- In the **Syslog Details** window:
- **Name**: Enter a name for the Syslog SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured in the Deception Admin Portal, the admin portal sends logs to Syslog.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector sends logs to Syslog.
- **Type of logs**: Select an option from the drop-down menu:
- **Events**: Send events to Syslog.
- **Audit Logs**: Send audit logs to Syslog.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](https://help.zscaler.com/deception/controlling-threat-events) to Syslog.
-
**Filter**: Specify a query if you want to send filtered event logs to Syslog. If this field is blank, all event logs are sent to Syslog. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
The **Filter** option is available only for event logs.
- **Host**: Enter the Syslog server IP address.
- **Port**: Enter the port number the Syslog server is listening to.
- **Transport**: Select **TCP** or **UDP**.
- **Facility**: Select a facility code (e.g., **System**) from the drop-down menu. Each event is labeled with a facility code, indicating the type of software generating the event logs.
- **Severity**: Select a severity level (e.g., **Critical**). Each event is labeled with a severity, indicating the severity of the tool generating the event logs.
-
**App Name**: Enter a log identifier (e.g., `Zscaler Deception`).
[See image.](#syslog-siem-integration-details)
-
Click **Save**.
The Syslog server integration is added.
To test the Syslog server integration, access a decoy and generate alerts on the [Zscaler Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).
Run the following command on the syslog server:
tcpdump -n host <IP address of the Service Connector>
The Syslog server receives the event logs.
[]![Add Syslog SIEM Integration option](/downloads/deception/orchestrate/siem-integrations/deception-and-syslog-server-deployment-guide/zscaler-deception-add-siem-integration-syslog.png)
[]![Configure Syslog server SIEM integration details ](/downloads/deception/orchestrate/siem-integrations/deception-and-syslog-server-deployment-guide/zscaler-deception-add-siem-integration-syslog-details-2.png)