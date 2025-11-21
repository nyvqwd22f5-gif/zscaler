# Enrichment Configuration Guide for Shadowserver
Source: https://help.zscaler.com/itdr/enrichment-configuration-guide-shadowserver
PDF: https://help.zscaler.com/pdf/com/en/1531820.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with Shadowserver to enhance security events generated in the Zscaler ITDR Admin Portal with additional context.
Shadowserver scans the internet, analyzes the collected threat data, and stores the detected malware in a repository. It sends daily remediation reports to address malicious activities and vulnerabilities.
Prerequisites
Ensure that there is network connectivity from the ITDR Admin Portal to the Shadowserver server.
Configuring Enrichment Integration with Shadowserver
To configure enrichment integration with Shadowserver:
- Go to **Orchestrate** > **Enrich**.
-
Locate **Shadowserver** in the table, and click the **Edit **icon under the **Actions **column.
[See image.](#deception-enrich-shadow-server-edit-icon)
-
In the **Shadowserver** window, select **Enabled**.
[See image.](#deception-enrich-shadow-server-config-details)
-
Click **Save**.
Enrichment integration with Shadowserver is enabled.
After enrichment integration is enabled, you can see the data from Shadowserver on the [Event Logs](/itdr/about-event-logs) page. The additional fields created in the event logs are prefixed with binary:
- binary.os_version
- binary.trusted_signature
- binary.os_name
- binary.sig_timestamp
- binary.description
- binary.fileversion
[]![Shadowserver enrichment integration Edit icon](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-shadowserver/itdr-edit-shadow-server_0.png)
[]![Configure Shadowserver enrichment integration](/downloads/itdr/orchestrate/enrichment-integrations/enrichment-configuration-guide-shadowserver/itdr-deception-enrichment-shadowserver-config-details_0.png)