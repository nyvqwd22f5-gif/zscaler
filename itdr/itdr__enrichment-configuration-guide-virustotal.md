# Enrichment Configuration Guide for VirusTotal
Source: https://help.zscaler.com/itdr/enrichment-configuration-guide-virustotal
PDF: https://help.zscaler.com/pdf/com/en/1531821.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with VirusTotal to enhance events generated in the Zscaler ITDR Admin Portal with additional context.
VirusTotal aggregates various antivirus products and online scan engines to analyze suspicious files, URLs, and IP addresses to detect threats. VirusTotal runs the forwarded file or hash through multiple antivirus engines and rulesets to generate enriched reports with detailed results.
Prerequisites
Before you configure enrichment integration, ensure that you have:
- Network connectivity from the ITDR Admin Portal to the VirusTotal API server.
- An active [VirusTotal account](https://www.virustotal.com/gui/sign-in).
-
Obtained the VirusTotal API key.
[See image.](#deception-enrich-virustotal-copy-api-key)
Configuring Enrichment Integration with VirusTotal
To configure enrichment integration with VirusTotal:
- Go to **Orchestrate** > **Enrich**.
-
Locate **VirusTotal** in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-virustotal-enrich-edit-icon)
-
In the **VirusTotal** window:
- Select **Enabled**.
- Enter the VirusTotal API key.
[See image.](#deception-virustotal-enrich-config-details-window)
-
Click **Save**.
Enrichment integration with VirusTotal is enabled.
After enrichment integration is enabled, you can see the data from VirusTotal on the [Event Logs](/itdr/about-event-logs) page. The additional fields created in the event logs are prefixed with vt:
- vt.positives
- vt.total
- vt.names
- vt.error
- vt.permalink
[]![Copy API key from VirusTotal](/downloads/deception/orchestrate/enrichment-integrations/deception-and-virustotal-deployment-guide/zscaler-deception-enrich-virustotal-api-key.png)
[]![VirusTotal enrichment integration Edit icon](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-virustotal/itdr-edit-virustotal_0.png)
[]![Configure VirusTotal enrichment integration](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-virustotal/zscaler-itdr-enrich-virustotal-config-details.png)