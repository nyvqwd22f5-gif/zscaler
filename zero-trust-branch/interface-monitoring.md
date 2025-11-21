# Interface Monitoring
Source: https://help.zscaler.com/zero-trust-branch/interface-monitoring
PDF: https://help.zscaler.com/pdf/com/en/1525246.pdf

Link failures can cause significant network disruptions. An intelligent switch, router, or firewall should identify failures and adjust routing decisions accordingly. Interface health monitoring sends continuous probes to a predefined target to monitor the liveliness of the interface link.
Zscaler routing policies are based on dynamic groups (e.g. device attributes, device score, etc.). These groups or objects are used to define segmentation policies. To learn more, see [Managing Objects](/zero-trust-branch/managing-objects).
Zero Trust Branch also supports link scoring on a scale of 0 to 30 based on jitter, latency, and packet loss. Since these measurements units are different, we normalize the result for a window of 30 iterations.
To enable monitoring on a site:
- Go to **Deployments > Sites**.
-
In the** Site Name** column, click the name of the site that you want to monitor.
[See image.](#view-site)
-
On the site details page, click the **Interfaces **tab. Then in the **Monitoring status** column, click **Disabled** in the interface for which you want to enable monitoring.
[See image.](#interfaces)
-
In the **Interface Health Monitor** panel:
- **Enable interface health monitoring**: Enable to start monitoring the health of this interface.
- **Probe target (IP address or FQDN)**: Enter the IP address or FQDN of the interface that you want to monitor.
- **Probe interval (seconds)**: Enter the probe interval in seconds.
- **Retry count (number of attempts)**: Enter the number of times to retry the probe before timing out.
[See image.](#monitoring)
- Click **Save**.
[]![Accessing details for a site on the Sites page](/downloads/device-segmentation/administration/site-configuration/interface-monitoring/view-sites.png)
[]![Viewing the Interfaces tab for a site](/downloads/device-segmentation/administration/site-configuration/interface-monitoring/interfaces-tab.png)
[]![Inteface Health Monitor panel](/downloads/device-segmentation/administration/site-configuration/interface-monitoring/interface-health-monitor-panel.png)