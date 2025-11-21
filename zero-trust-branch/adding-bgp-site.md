# Adding a Border Gateway Protocol to a Site
Source: https://help.zscaler.com/zero-trust-branch/adding-bgp-site
PDF: https://help.zscaler.com/pdf/com/en/1525631.pdf

A border gateway protocol (BGP) governs routing among devices within a site.
To add a BGP configuration:
- Go to **Deployment > Sites**.
-
In the** Site Name** column, click the name of the site to which you want to add a BGP configuration.
[See image.](#view-site)
-
On the site details page, click the **Settings **tab, then click **BGP **in the left-side navigation. Click **Add** in the upper-right corner to add a new BGP configuration.
[See image.](#site-bgp)
In the **Add Peer **panel:
- **Name**: Enter a name for this BGP configuration.
- **Neighbor IP**: Enter the IP address of the peer router for this configuration.
- **Neighbor AS**: Enter the autonomous system (AS) number that identifies this peer router's network.
- **Local IP**: Enter the IP address of the local network.
- **Local AS**: Enter the AS number that identifies the local network.
- **Password**: Enter the password shared between the two networks.
- **Graceful Restart Time**: Enter a time in milliseconds to allow the peer router to restart before timing out.
[See image.](#add-bgp)
- Click **Save** to save the configuration.
[]![Accessing details for a site on the Sites page](/downloads/device-segmentation/administration/resources/adding-border-gateway-protocol-site/view-sites.png)
[]![Adding a BGP configuration on the Settings tab for a Site](/downloads/device-segmentation/administration/resources/adding-border-gateway-protocol-site/add-bgp.png)
[]![Add Peer panel](/downloads/device-segmentation/administration/resources/adding-border-gateway-protocol-site/add-bgp-peer.png)