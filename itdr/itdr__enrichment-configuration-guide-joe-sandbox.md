# Enrichment Configuration Guide for Joe Sandbox
Source: https://help.zscaler.com/itdr/enrichment-configuration-guide-joe-sandbox
PDF: https://help.zscaler.com/pdf/com/en/1531817.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with Joe Sandbox to enhance events that are generated in the Zscaler ITDR Admin Portal with additional context.
Joe Sandbox is a cloud-based malware sandbox that detects and analyzes malware samples. You can send malware files to Joe Sandbox for testing and download reports for further analysis.
Prerequisites
Before you configure enrichment integration, ensure that you have:
- Network connectivity from the ITDR Admin Portal to the Joe Sandbox API server.
- An active [Joe Sandbox account](https://www.joesandbox.com/register).
- Obtained the Joe Sandbox API key. In the Joe Sandbox console, go to **User Settings** > **API Key** to obtain the API key.
Configuring Enrichment Integration with Joe Sandbox
To configure enrichment integration with Joe Sandbox:
- Go to **Orchestrate** > **Enrich**.
-
Locate **Joe Sandbox **in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-enrich-joe-sandbox-edit-icon)
-
In the **Joe Sandbox** window:
- Select **Enabled**.
- Enter the API key.
[See image.](#deception-enrich-joe-sandbox-config-details)
-
Click **Save**.
Enrichment integration with Joe Sandbox is enabled.
[]![Joe Sandbox enrichment integration Edit icon](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-joe-sandbox/itdr-edit-joe-sanbox_0.png)
[]![Configuring Joe Sandbox enrichment integration](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-joe-sandbox/itdr-joe-sandbox-config-details.png)