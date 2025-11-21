# SIEM Configuration Guide for Syslog
Source: https://help.zscaler.com/itdr/siem-configuration-guide-syslog
PDF: https://help.zscaler.com/pdf/com/en/1531742.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to a Syslog security information and event management (SIEM) server.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the Syslog server on the port Syslog is listening to.
-
Use TCP or UDP protocol depending on the Syslog server's configuration.
Zscaler recommends that you use the TCP protocol to avoid any issues with the UDP protocol's unreliability, frame limits, and fragmented packets.
Configuring a Service Connector to Forward Events to Syslog SIEM
To configure a Service Connector to forward events or audit logs to a Syslog SIEM server:
- In the Zscaler ITDR Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Syslog** from the drop-down menu.
[See image.](#itdr-syslog-add-siem-integration-option)
- In the **Syslog Details** window:
- **Name**: Enter a name for the Syslog SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu. If you select a Service Connector that is configured in the ITDR Admin Portal, the portal sends logs to Syslog.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to Syslog.
- **Audit Logs**: Send audit logs to Syslog.
- **Include Safe Events**: Enable to forward the events that are marked as safe to Syslog.
-
**Filter**: Specify a query if you want to send filtered event logs to Syslog. If this field is blank, all event logs are sent to Syslog.
The **Filter** option is available only for event logs.
- **Host**: Enter the Syslog server IP address.
- **Port**: Enter the port number the Syslog server is listening to.
- **Transport**: Select **TCP** or **UDP**.
- **Facility**: Select a facility code (e.g., **System**) from the drop-down menu. Each event is labeled with a facility code, indicating the type of software generating the event logs.
- **Severity**: Select a severity level (e.g., **Critical**). Each event is labeled with a severity, indicating the severity of the tool generating the event logs.
-
**App Name**: Enter a log identifier (e.g., `Zscaler ITDR`).
[See image.](#itdr-syslog-siem-integration-details)
-
Click **Save**.
The Syslog server integration is added.
To test the Syslog server integration, access a decoy and generate alerts on the Investigate page.
Run the following command on the syslog server:
tcpdump -n host <IP address of the Service Connector>
The Syslog server receives the event logs.
[]![Syslog SIEM integration option](/downloads/itdr/getting-started/step-step-configuration-guide-zscaler-itdr/itdr-add-siem-integration-syslog.png)
[]![Configure Syslog SIEM integration details](/downloads/itdr/getting-started/step-step-configuration-guide-zscaler-itdr/itdr-add-siem-integration-syslog-details.png)