# SIEM Configuration Guide for ArcSight Enterprise Security Manager
Source: https://help.zscaler.com/itdr/siem-configuration-guide-arcsight-enterprise-security-manager
PDF: https://help.zscaler.com/pdf/com/en/1531723.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to the ArcSight Enterprise Security Manager (ESM) security information and event management (SIEM) solution.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the ArcSight server on the port ArcSight is listening to.
- Use TCP or UDP protocol depending on the ArcSight SIEM configuration.
Configuring a Service Connector to Forward Events to ArcSight
To configure a Service Connector to forward events or audit logs to the Arcsigh SIEM solution:
- In the Zscaler ITDR Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **ArcSight** from the drop-down menu.
[See image.](#itdr-add-siem-integration-option)
-
In the **ArcSight Details** window:
- **Name**: Enter a name for the ArcSight SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu. If you select a Service Connector that is configured in the ITDR Admin Portal, the portal sends logs to ArcSight.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to ArcSight.
- **Audit Logs**: Send audit logs to ArcSight.
- **Include Safe Events**: Enable to forward the events that are marked as safe to ArcSight.
-
**Filter**: Specify a query if you want to send filtered event logs to ArcSight. If this field is blank, all event logs are sent to ArcSight.
The **Filter **option is available only for event logs.
- **Host**: Enter the ArcSight server IP address.
- **Port**: Enter the port number the ArcSight server is listening to.
- **Transport**: Select **TCP** or **UDP**.
[See image.](#itdr-config-arcsight-siem-integration-details)
-
Click **Save**.
The ArcSight SIEM integration is configured.
To test the ArcSight SIEM integration, generate events on the Investigate page. You can see the logs forwarded from the ITDR Admin Portal on the ArcSight SIEM solution.
[]![ITDR SIEM integration with Arcsight option](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-arcsight-enterprise-security-manager/itdr-add-siem-integrations-arcsight.png)
[]![Configure ArcSight SIEM integration](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-arcsight-enterprise-security-manager/itdr-configt-siem-integrations-arcsight-3.png)