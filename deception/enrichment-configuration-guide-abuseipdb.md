# Enrichment Configuration Guide for AbuseIPDB
Source: https://help.zscaler.com/deception/enrichment-configuration-guide-abuseipdb
PDF: https://help.zscaler.com/pdf/com/en/1531438.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with AbuseIPDB to enhance events that are generated in the Zscaler Deception Admin Portal with additional context.
AbuseIPDB maintains a database of IP addresses that are reported performing activities such as spamming, scanning, web app attacks, etc. You can report an IP address associated with malicious activity, or verify if an IP address has been reported. Deception integration with AbuseIPDB helps you to enrich events from internet-facing decoys.
Prerequisites
Before you configure the enrichment integration, ensure that you have:
- Network connectivity from the Deception Admin Portal to the AbuseIPDB API server.
- An active [AbuseIPDB account](https://www.abuseipdb.com/account/api).
-
Created an AbuseIPDB API key. To learn more, refer to the [AbuseIPDB documentation](https://www.abuseipdb.com/api.html).
[See image.](#deception-enrich-abuseipdb-create-api-key)
Configuring the Enrichment Integration with AbuseIPDB
To configure the enrichment integration with AbuseIPDB:
- Go to **Orchestrate** > **Enrich**.
-
Locate **AbuseIPDB **in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-enrich-abuseipdb-edit-icon)
-
In the **AbuseIPDB** window:
- Select **Enabled**.
- Enter the AbuseIPDB API key.
[See image.](#deception-enrich-abuseipdb-config-details)
-
Click **Save**.
The enrichment integration with AbuseIPDB is enabled.
After the enrichment integration is enabled, you can see the data from AbuseIPDB on the [Event Logs](/deception/about-event-logs) page. The additional fields created in the event logs are prefixed with abuseip:
- abuseip.abuseConfidenceScore
- abuseip.countryCode
- abuseip.countryName
- abuseip.ipAddress
- abuseip.ipVersion
- abuseip.isPublic
- abuseip.isWhitelisted
- abuseip.lastReportedAt
- abuseip.totalReports
[]![Create an API key in AbuseIPDB](/downloads/deception/orchestrate/enrichment-integrations/deception-and-abuseipdb-deployment-guide/zscaler-deception-enrich-abuseipdb-create-api-key.png)
[]![AbuseIPDB enrichment integration Edit icon](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-abuseipdb/zscaler-deception-enrich-abuseipdb-edit-icon.png)
[]![Configure AbuseIPDB enrichment integration](/downloads/deception/orchestrate/enrichment-integrations/enrichment-configuration-guide-abuseipdb/zscaler-deception-enrich-abuseipdb-config-details.png)