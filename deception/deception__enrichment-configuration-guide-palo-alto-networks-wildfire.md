# Enrichment Configuration Guide for Palo Alto Networks WildFire
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-palo-alto-networks-wildfire
PDF: https://help.zscaler.com/pdf/com/en/1531440.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Palo Alto Networks WildFire. You can send the Deception evidence files to the Palo Alto Networks WildFire sandbox to enrich incident investigations and response.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- An active Palo Alto Networks WildFire account.
- The Palo Alto Networks WildFire console [URL](https://sso.paloaltonetworks.com/).
-
Obtained the Palo Alto Networks WildFire API key. In the Palo Alto Networks WildFire console, go to **My Account** and copy the API key.
[See image.](#deception-enrich-palo-alto-wildfire-api-key)
Configuring the Enrichment Integration with Palo Alto Networks WildFire
To configure the enrichment integration with Palo Alto Networks WildFire:
- Go to **Orchestrate** > **Enrich**.
-
Locate **Palo Alto Networks WildFire **in the table, and click the **Edit **icon under the **Actions** column.
[See image.](#deception-enrich-palo-alto-wildfire-edit-icon)
-
In the **Palo Alto Networks WildFire** window:
- Select **Enabled**.
- Enter the URL of the Palo Alto Networks WildFire console.
- Enter the API key.
[See image.](#deception-enrich-palo-alto-wildfire-config-details)
-
Click **Save**.
The enrichment integration with Palo Alto Networks WildFire is enabled.
To test the integration, run an application file on a network decoy with Windows service enabled. When an alert is generated on the [Investigate dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard), [send the evidence file](/deception/sending-evidence-file-sandbox) to the Palo Alto Networks WildFire sandbox. After you send the evidence file to the sandbox, you can [download the report](/deception/downloading-sandbox-report) for analysis.
[]![Copy Palo Alto Networks WildFire API key](/downloads/deception/orchestrate/enrichment-integrations/deception-and-palo-alto-networks-wildfire-deployment-guide/zscaler-deception-enrich-palo-alto-copy-api-key.png)
[]![Palo Alto Networks WildFire enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-palo-alto-networks-wildfire/zscaler-deception-enrich-palo-alto-edit-icon.png)
[]![Configure Palo Alto Networks WildFire enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-palo-alto-networks-wildfire/zscaler-deception-enrich-palo-alto-config-details.png)