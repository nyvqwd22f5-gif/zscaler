# Enrichment Configuration Guide for IPinfo
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-ipinfo
PDF: https://help.zscaler.com/pdf/com/en/1531439.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with IPinfo to enrich security events that are generated in the Zscaler Deception Admin Portal with additional context.
IPinfo consists of accurate IP address data for users around the globe. Deception integration with IPinfo enriches events with insights from the IP geolocation data.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- Network connectivity from the Deception Admin Portal to the IPinfo server.
- An active [IPinfo account](https://ipinfo.io/account/home).
-
Obtained the IPinfo API access token.
[See image.](#deception-enrich-ipinfo-access-token)
Configuring the Enrichment Integration with IPinfo
To configure the enrichment integration with IPinfo:
- Go to **Orchestrate** > **Enrich**.
-
Locate **IP Info **in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-enrich-ipinfo-edit-icon)
-
In the **IP Info** window:
- Select **Enabled**.
- Enter the IPinfo Access Token.
[See image.](#deception-enrich-ipinfo-config-details)
-
Click **Save**.
The enrichment integration with IPinfo is enabled.
After the enrichment is enabled, the enriched IP geolocation data from IPinfo is available in the attacker.country field on the [Event Logs](/deception/about-event-logs) page.
[]![Copy the access token from IPinfo](/downloads/deception/orchestrate/enrichment-integrations/deception-and-ipinfo-deployment-guide/zscaler-deception-enrich-ipinfo-access-token.png)
[]![IPinfo enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-ipinfo/zscaler-deception-enrich-ipinfo-edit-icon.png)
[]![Configure IPinfo enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-ipinfo/zscaler-deception-enrich-ipinfo-config-details.png)