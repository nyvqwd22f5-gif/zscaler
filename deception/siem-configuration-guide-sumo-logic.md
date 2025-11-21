# SIEM Configuration Guide for Sumo Logic
Source: https://help.zscaler.com/itdr/siem-configuration-guide-sumo-logic
PDF: https://help.zscaler.com/pdf/com/en/1531743.pdf

This article provides information on how to configure a Service Connector to forward events or audit logs to the Sumo Logic Security Information and Event Management (SIEM) solution.
Follow these steps to configure a Service Connector to forward to Sumo Logic:
- [Step 1: Generate an HTTP Source Address URL in Sumo Logic](#itdr-siem-sumo-logic-gen-http-url)
- [Step 2: Forward Logs to Sumo Logic](#itdr-siem-sumo-logic-forward-logs)
- []Log in to Sumo Logic.
- Go to **Manage Data** > **Collection**.
-
Click **Add Collector**.
[See image.](#itdr-sumo-logic-add-collector)
-
In the **Select Collector Type** window, click **Hosted Collector**.
[See image.](#itdr-select-hosted-collector-type)
-
Enter the name of the collector, and click **Save**.
[See image.](#itdr-sumo-logic-config-hosted-collector)
-
Click **Add Source** for the collector.
[See image.](#itdr-sumo-logic-add-source)
-
Click **HTTP Logs & Metrics**.
[See image.](#itdr-sumo-logic-http-logs-metrics)
-
In the **HTTP Logs & Metrics** window:
- Enter a name.
- Expand the **Advanced Options for Logs (Optional)** menu, and under **Message Processing**, select the **Multiline Processing** checkbox.
[See image.](#itdr-sumo-logic-config-http-logs-metrics)
- Click **Save**.
-
[]The **HTTP Source Address** window appears with a URL.
[See image.](#itdr-sumo-logic-copy-http-source-address-url)
- Copy the URL. You need this URL when configuring the Zscaler ITDR and Sumo Logic SIEM integration.
- Click **OK**.
- []In the the Zscaler ITDR Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Sumo Logic** from the drop-down menu.
[See image.](#itdr-sumo-logic-add-integration)
- In the **Sumo Logic Details** window:
- **Name**: Enter a name for the Sumo Logic SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu. If you select a Service Connector that is configured in the ITDR Admin Portal, the portal forwards the logs to Sumo Logic.
- **Types of logs**: Select an option from the drop-down menu:
- **Event**: Forward events to Sumo Logic.
- **Audit logs**: Forward audit logs to Sumo Logic.
- **Include Safe Events**: Enable to forward the events that are marked as safe to Sumo Logic.
-
**Filter**: Enter queries if you want to filter the logs before forwarding them to Sumo Logic. If this field is blank, all logs are forwarded to Sumo Logic.
The **Filter** option is available only for event logs.
- **HTTP Collector Endpoint**: Enter the [HTTP Source Address URL](#itdr-sumo-logic-http-source-add-url) that you copied.
-
**Use Proxy Settings (if available)**: Enable if you want to use proxy settings on the Service Connector, if available. This can be useful for Sumo Logic cloud instances.
[See image.](#itdr-sumo-logic-config-details)
-
Click **Save**.
The Sumo Logic SIEM integration entry is added.
To test the Sumo Logic SIEM integration, generate events on the Investigate page. You can see the forwarded logs on the Sumo Logic instance.
[See image.](#itdr-siem-sumo-logic-events-forwarded)
[]![Add a collector in Sumo Logic](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-add-collector.png)
[]![Select a hosted collector type](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-collector-type-host-2.png)
[]![Configure hosted collector](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-config-collector-1.png)
[]![Add a source](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-add-source.png)
[]![Add HTTP Logs and Metrics source](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-add-source-http-metrics.png)
[]![Configure HTTP Logs and Metrics](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-http-logs-metrics.png)
[]![Copy HTTP source address URL](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-http-source-address.png)
[]![Sumo Logic SIEM integration option](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-option.png)
[]![Configure Sumo Logic SIEM integration](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-logic-config.png)
[]![ITDR events forwarded to Sumo Logic](/downloads/itdr/orchestrate/siem-integrations/siem-configuration-guide-sumo-logic/itdr-siem-sumo-events.png)