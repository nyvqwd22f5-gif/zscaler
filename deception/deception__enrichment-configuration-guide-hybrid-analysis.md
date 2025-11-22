# Enrichment Configuration Guide for Hybrid Analysis
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-hybrid-analysis
PDF: https://help.zscaler.com/pdf/com/en/1531442.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Hybrid Analysis to enhance the security events generated in the Zscaler Deception Admin Portal with additional context.
Hybrid Analysis detects and analyzes unknown threats using a file analysis approach. The analyzed data is processed and integrated into the malware analysis reports. You can send malware files to the Hybrid Analysis sandbox for testing and download reports for further analysis.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- Network connectivity from the Deception Admin Portal to the Hybrid Analysis server.
- An active [Hybrid Analysis account](https://www.hybrid-analysis.com/signup).
-
A valid Hybrid Analysis API key. To learn more, refer to the [Hybrid Analysis documentation](https://www.hybrid-analysis.com/docs/api/v2).
[See image.](#deception-enrich-hybrid-analysis-copy-api-key)
Configuring the Enrichment Integration with Hybrid Analysis
To configure the enrichment integration with Hybrid Analysis:
- Go to **Orchestrate** > **Enrich**.
- Locate **Hybrid Analysis **in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-enrich-hybrid-analysis-edit-icon)
-
In the **Hybrid Analysis** window:
- Select **Enabled**.
- Enter the API key.
[See image.](#deception-enrich-hybrid-analysis-config-details)
-
Click **Save**.
The enrichment integration with Hybrid Analysis is enabled.
To test the integration, run an application file on a network decoy with Windows service enabled. When an alert is generated on the [Investigate dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard), [send the evidence file](/deception/sending-evidence-file-sandbox) to the Hybrid Analysis sandbox. After you send the evidence file to the sandbox, you can [download the report](/deception/downloading-sandbox-report) for analysis.
[]![Copy the API key from Hybrid Analysis](/downloads/deception/orchestrate/enrichment-integrations/deception-and-shadowserver-deployment-guide/zscaler-deception-enrich-hybrid-analysis-api-key.png?1668590943)
[]![Hybrid Analysis enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-hybrid-analysis/zscaler-deception-enrich-hybrid-analysis-edit-icon.png)
[]![Configure Hybrid analysis enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-hybrid-analysis/zscaler-deception-enrich-hybrid-analysis-config-details.png)