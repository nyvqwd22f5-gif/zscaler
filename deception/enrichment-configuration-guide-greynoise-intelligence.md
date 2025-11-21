# Enrichment Configuration Guide for GreyNoise Intelligence
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-greynoise-intelligence
PDF: https://help.zscaler.com/pdf/com/en/1531435.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with GreyNoise Intelligence to enhance events that are generated in the Zscaler Deception Admin Portal with additional context.
GreyNoise Intelligence collects, labels, and analyzes internet-wide scan and attack data. It categorizes and tags IP addresses based on activity, threat actor, and tools.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- Network connectivity from the Deception Admin Portal to the GreyNoise Intelligence API server.
- An active [GreyNoise Intelligence account](https://viz.greynoise.io/account).
-
Obtained the GreyNoise Intelligence API key. To learn more, refer to the [GreyNoise Intelligence documentation](https://developer.greynoise.io/docs/getting-started).
[See image.](#deception-enrich-greynoise-copy-api-key)
Configuring the Enrichment Integration with GreyNoise Intelligence
To configure the enrichment integrationwith GreyNoise Intelligence:
- Go to **Orchestrate** > **Enrich**.
-
Locate **GreyNoise Intelligence** in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-greynoise-enrich-edit-icon)
-
In the **GreyNoise Intelligence** window:
- Select **Enabled**.
- Enter the GreyNoise Intelligence API key.
[See image.](#deception-enrich-greynoise-config-details)
-
Click **Save**.
The enrichment integration with GreyNoise Intelligence is enabled.
After the enrichment integration is enabled, you can see the data from GreyNoise Intelligence on the [Event Logs](/deception/about-event-logs) page. The additional fields created in the event logs are prefixed with greynoise:
- greynoise.categories
- greynoise.category.activity
- greynoise.category.actor
- greynoise.category.hosting
- greynoise.category.scanner
- greynoise.category.search_engine
- greynoise.category.tool
- greynoise.category.worm
- greynoise.returned_count
- greynoise.status
[]![Copy the API key from GreyNoise](/downloads/deception/orchestrate/enrichment-integrations/deception-and-greynoise-intelligence-deployment-guide/zscaler-deception-enrich-greynoise-api-key.png)
[]![GreyNoise Intelligence enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-greynoise-intelligence/zscaler-deception-enrich-greynoise-edit-icon.png)
[]![Configure GreyNoise Intelligence enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-greynoise-intelligence/zscaler-deception-enrich-greynoise-config-details.png)