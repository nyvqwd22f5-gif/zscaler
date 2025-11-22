# SIEM Configuration Guide for Sumo Logic
Source: https://help.zscaler.com/deception/siem-configuration-guide-sumo-logic
PDF: https://help.zscaler.com/pdf/com/en/1531477.pdf

This article provides information on how to configure a Service Connector to forward events or audit logs to the Sumo Logic security information and event management (SIEM) solution.
- [Step 1: Generate an HTTP Source Address URL in Sumo Logic](#deception-siem-sumo-logic-gen-http-url)
- [Step 2: Forward Logs to Sumo Logic](#deception-siem-sumo-logic-forward-logs)
- []Log in to Sumo Logic.
- Go to **Manage Data** > **Collection**.
-
Click **Add Collector**.
[See image.](#deception-sumo-logic-add-collector)
-
In the **Select Collector Type** window, click **Hosted Collector**.
[See image.](#deception-sumo-logic-hosted-collector-type)
-
Enter the name of the collector, and click **Save**.
[See image.](#deception-sumo-logic-config-hosted-collector)
-
Click **Add Source** for the collector.
[See image.](#deception-sumo-logic-add-source)
-
Click **HTTP Logs & Metrics**.
[See image.](#deception-sumo-logic-http-logs-metrics)
-
In the **HTTP Logs & Metrics** window:
- Enter a name.
- Expand the **Advanced Options for Logs (Optional)** menu, and under **Message Processing**, select the **Multiline Processing** checkbox.
[See image.](#deception-sumo-logic-config-http-logs-metrics)
- Click **Save**.
-
[]The **HTTP Source Address** window appears with a URL.
[See image.](#deception-sumo-logic-copy-http-source-address-url)
- Copy the URL. You need this URL when configuring the Zscaler Deception and Sumo Logic SIEM integration.
- Click **OK**.
- []In the the Zscaler Deception Admin Portal, go to **Orchestrate** > **SIEM Integrations**.
-
Click **Add Integration**, and select **Sumo Logic** from the drop-down menu.
[See image.](#deception-sumo-logic-add-integration)
- In the **Sumo Logic Details** window:
- **Name**: Enter a name for the Sumo Logic SIEM integration.
- **Enabled**: Select to enable SIEM integration.
- **Service Connector**: Select a Service Connector from the drop-down menu:
- If you select a Service Connector that is configured in the Deception Admin Portal, the portal forwards the logs to Sumo Logic.
- If you select a Service Connector that is configured on a Decoy Connector, the selected Decoy Connector forwards the logs to Sumo Logic.
- **Types of logs**: Select an option from the drop-down menu:
- **Event**: Forward events to Sumo Logic.
- **Audit logs**: Forward audit logs to Sumo Logic.
- **Include Safe Events**: Enable to forward the events that are [marked as safe](/deception/taking-action-from-the-dashboard#mark-as-safe) to Sumo Logic.
-
**Filter**: Enter queries if you want to filter the logs before forwarding them to Sumo Logic. If this field is blank, all logs are forwarded to Sumo Logic. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
The **Filter** option is available only for event logs.
- **HTTP Collector Endpoint**: Enter the [HTTP Source Address URL](#deception-sumo-logic-http-source-address) that you copied.
-
**Use Proxy Settings (if available)**: Enable if you want to use proxy settings on the Service Connector, if available. This can be useful for Sumo Logic cloud instances.
[See image.](#deception-sumo-logic-config-details)
-
Click **Save**.
The Sumo Logic SIEM integration entry is added.
[See image.](#deception-siem-sumo-logic-integration-added)
To test the Sumo Logic SIEM integration, access a decoy and generate alerts on the Zscaler Deception dashboard. You can see the forwarded logs on the Sumo Logic instance.
[See image.](#deception-siem-sumo-logic-events-forwarded)
[]![Add a collector in Sumo Logic](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-add-collector.png)
[]![Select Hosted Collector type](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-collector-type-host.png)
[]![Configure hosted collector details](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-config-collector.png)
[]![Add a source for collector](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-add-source.png?1684133459)
[]![Add HTTP logs & Metrics source](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-add-source-http-metrics.png)
[]![Configure HTTP Logs & Metrics](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-http-metrics-multiline-processing.png)
[]![Copy the HTTP source address URL](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-logic-http-source-address.png)
[]![Add Sumo Logic SIEM integration](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-add-integration-sumo-logic.png)
[]![Configure Deception and Sumo Logic SIEM integration details](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-config-integration.png)
[]![Sumo Logic SIEM integration added](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-add-integration-added.png)
[]![Events forwarded to Sumo Logic](/downloads/deception/orchestrate/siem-integrations/deception-and-sumo-logic-deployment-guide/zscaler-deception-siem-sumo-events.png?1684731749)