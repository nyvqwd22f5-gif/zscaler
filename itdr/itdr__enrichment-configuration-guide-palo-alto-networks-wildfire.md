# Enrichment Configuration Guide for Palo Alto Networks WildFire
Source: https://help.zscaler.com/itdr/enrichment-configuration-guide-palo-alto-networks-wildfire
PDF: https://help.zscaler.com/pdf/com/en/1531819.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with Palo Alto Networks WildFire.
Prerequisites
Before you configure enrichment integration, ensure that you have:
- An active Palo Alto Networks WildFire account.
- The Palo Alto Networks WildFire console [URL](https://sso.paloaltonetworks.com/).
-
Obtained the Palo Alto Networks WildFire API key. In the Palo Alto Networks WildFire console, go to **My Account** and copy the API key.
[See image.](#deception-enrich-palo-alto-wildfire-api-key)
Configuring Enrichment Integration with Palo Alto Networks WildFire
To configure enrichment integration with Palo Alto Networks WildFire:
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
Enrichment integration with Palo Alto Networks WildFire is enabled.
[]![Copy Palo Alto Networks WildFire API key](/downloads/deception/orchestrate/enrichment-integrations/deception-and-palo-alto-networks-wildfire-deployment-guide/zscaler-deception-enrich-palo-alto-copy-api-key.png)
[]![Palo Alto Networks WildFire enrichment integration Edit icon](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-palo-alto-networks-wildfire/itdr-edit-pan_0.png)
[]![Configuring Palo Alto Networks WildFire enrichment integration](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-palo-alto-networks-wildfire/itdr-palo-alto-config-details.png)