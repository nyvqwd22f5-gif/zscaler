# Configuring a High Availability Site with Virtual Router Redundancy Protocol
Source: https://help.zscaler.com/zero-trust-branch/configuring-ha-site-vrrp
PDF: https://help.zscaler.com/pdf/com/en/1529555.pdf

To ensure that mission-critical systems in a network remain resilient to failures, you can configure Zero Trust Branch with a dedicated high availability (HA) link that makes use of Virtual Router Redundancy Protocol (VRRP). VRRP allows multiple Zero Trust Branch appliances to share a virtual IP address, minimizing downtime and enhancing overall reliability and security.
Prior to release 7.8, Zero Trust Branch used a WAN link to run VRRP, which is less reliable due to the potential for latency, jitter, packet loss, and unpredictable failover behavior due to WAN performance.
Beginning with release 7.8, Zero Trust Branch introduced a dedicated HA link. This ensures that VRRP is independent of WAN issues, leading to faster and more reliable failovers, and also ensures that state synchronization and failover signaling occur within a controlled, secure environment, reducing attack surfaces.
To configure an HA site:
- Go to **Deployment > Sites**.
-
In the** Site Name** column, click the name of the site that you want to enable for HA.
[See image.](#view-site)
-
On the site details page, click the **Settings **tab, then click **VRRP **in the left-side navigation.
In the **VRRP **panel:
- **VRRP Group ID**: A unique numerical identifier (between 1 and 255) that groups routers together for redundancy purposes. Zero Trust Branch automatically fills in this value.
- **VRRP interface for ****<gateway 1>**: Select the interface to use for VRRP for the primary gateway.
- **VRRP interface for ****<gateway 2>**: Select the interface to use for VRRP for the secondary gateway.
- **Track Interface for <****gateway 1>**: Select the interface to be tracked for the primary gateway. If this interface goes down, the secondary gateway becomes the primary.
- **Track Interface for ****<gateway 2>**: Select the interface to be tracked for the secondary gateway.
- **Password**: (Optional) Enter a password to encrypt this VRRP configuration (maximum of 8 alphabetic characters).
- **Advertisement Interval**: The interval, in seconds, for the primary gateway to send VRRP advertisements to the secondary gateway. The default value is `1`. If the secondary gateway misses three advertisements from the primary, it becomes the new primary.
- **Priority**: Enter the rank (between 1 and 255) for this Zero Trust Branch to determine which is the primary in the VRRP group. The Zero Trust Branch with the highest number (e.g., 255 is higher than 254) has priority.
[See image.](#vrrp)
- Click **Save** to save the VRRP configuration for this site.
[]![Accessing details for a site on the Sites page](/downloads/device-segmentation/administration/resources/adding-border-gateway-protocol-site/view-sites.png)
[]![VRRP configuration panel for a Site](/downloads/zero-trust-branch/administration/deployment-configuration/adding-bgp-site/vrrp.png)