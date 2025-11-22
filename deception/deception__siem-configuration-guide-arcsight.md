# SIEM Configuration Guide for ArcSight Enterprise Security Manager
Source: https://help.zscaler.com/deception/siem-configuration-guide-arcsight
PDF: https://help.zscaler.com/pdf/com/en/1531403.pdf

This article provides information on prerequisites and how to configure a Service Connector to forward events or audit logs to the ArcSight Enterprise Security Manager (ESM) security information and event management (SIEM) solution.
Prerequisites
Make sure the following prerequisites are met:
- Have network connectivity between the Service Connector and the ArcSight server on the port ArcSight is listening to.
- Use TCP or UDP protocol depending on the ArcSight SIEM configuration.
Configuring a Service Connector to Forward Events to ArcSight
To configure a Service Connector to forward events or audit logs to the ArcSight SIEM solution:
- []In the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **ArcSight** from the drop-down menu.
[See image.](#add-siem-integration-option)
-
In the **ArcSight Details** window:
- **Name**: Enter a name for the ArcSight SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured on the Deception Admin Portal, the portal sends logs to ArcSight.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector sends logs to ArcSight.
- **Type of logs**: Select an option from the drop-down menu.
- **Events**: Send events to ArcSight.
- **Audit Logs**: Send audit logs to ArcSight.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](/deception/taking-action-from-the-dashboard#mark-as-safe) to ArcSight.
- **Filter**: Specify a query if you want to send filtered event logs to ArcSight. If this field is blank, all event logs are sent to ArcSight. The **Filter **option is available only for event logs. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
- **Host**: Enter the ArcSight server IP address.
- **Port**: Enter the port number the ArcSight server is listening to.
- **Transport**: Select **TCP** or **UDP**.
[See image.](#config-arcsight-siem-integration-details)
-
Click **Save**.
The ArcSight SIEM integration is configured.
To test the ArcSight SIEM integration, access a decoy and generate alerts on the [Zscaler Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard). You can see the logs forwarded from the Deception Admin Portal on the ArcSight SIEM solution.
[]![Add ArcSight SIEM integration option](/downloads/deception/orchestrate/siem-integrations/deception-and-arcsight-deployment-guide/zscaler-deception-siem-integration-arcsight-option.png)
[]![Configure ArcSight SIEM integration details](/downloads/deception/orchestrate/siem-integrations/deception-and-arcsight-deployment-guide/zscaler-deception-siem-arcsight-details-2.png?1670217301)