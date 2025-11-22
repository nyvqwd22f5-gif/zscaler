# Enrichment Configuration Guide for Joe Sandbox
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-joe-sandbox
PDF: https://help.zscaler.com/pdf/com/en/1531437.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Joe Sandbox to enhance events that are generated in the Zscaler Deception Admin Portal with additional context.
Joe Sandbox is a cloud-based malware sandbox that detects and analyzes malware samples. You can send malware files to Joe Sandbox for testing and download reports for further analysis.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- Network connectivity from the Deception Admin Portal to the Joe Sandbox API server.
- An active [Joe Sandbox account](https://www.joesandbox.com/register).
- Obtained the Joe Sandbox API key. In the Joe Sandbox console, go to **User Settings** > **API Key** to obtain the API key.
Configuring the Enrichment Integration with Joe Sandbox
To configure the enrichment integration with Joe Sandbox:
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
The enrichment integration with Joe Sandbox is enabled.
To test the integration, run an application file on a network decoy with Windows service enabled. When an alert is generated on the [Investigate dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard), [send the evidence file](/deception/sending-evidence-file-sandbox) to the Joe Sandbox. After you send the evidence file, you can [download the report](/deception/downloading-sandbox-report) for analysis.
[]![Joe Sandbox enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-joe-sandbox/zscaler-deception-enrich-joe-sandbox-edit-icon.png)
[]![Configure Joe Sandbox enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-joe-sandbox/zscaler-deception-enrich-joe-sandbox-configured-new.png)