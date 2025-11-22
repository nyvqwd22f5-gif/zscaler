# Adding a Site
Source: https://help.zscaler.com/zero-trust-branch/adding-site
PDF: https://help.zscaler.com/pdf/com/en/1525146.pdf

Sites are where Zero Trust Branch appliances are deployed. You can create templates to add sites more quickly. To learn more about templates, see [Managing Templates](/zero-trust-branch/managing-templates).
If you are adding a high availability (HA) site, see [Creating a Zero Trust Branch High Availability Cluster](/zero-trust-branch/creating-zero-trust-branch-high-availability-cluster) for additional configuration steps.
Add a Site
The example shown in this procedure uses a custom standalone template, a new Zscaler Internet Access (ZIA) location, and DHCP for the WAN interface IP address.
To add a site:
- Go to **Deployments > Sites**.
-
Click **Add Site** in the upper-right corner.
[See image.](#sites)
-
In the **Add Site **panel:
- **Name**: Enter a name to identify the site.
- **Platform**: Select the hardware model or virtual machine for this site.
- **Template**: Select the template to use for this site. It can be a template that you cloned and customized or a default template.
- **Private DNS Servers**: Review the DNS servers used by Zero Trust Branch. The template populates this field, but you can override it for a site that uses a cloned and customized template.
- Select the ZIA location for this site and provide the requested information:
- **Existing Location**: Select an existing ZIA location for this site. To learn more, see [About Locations](/zia/about-locations).
- **New Location**: Enter a name for this location and select the country where it resides. Zero Trust Branch saves this location in your ZIA tenant and configures an Internet Protocol Security (IPSec) virtual private network (VPN) tunnel to that location.
- **None**: Select this option if the site does not have a physical location.
- **DHCP Service**: This field defines whether the Zero Trust Branch operates as a **DHCP Server** or a **DHCP Relay**. The template populates this field, but you can override it for a site that uses a cloned and customized template.
- **DHCP Server IP Address**: If the **DHCP Service** field displays **DHCP Relay**, enter the IP address of the DHCP server.
- **Gateway 1**: Enter the site-specific information for the primary gateway:
- **Name**: Enter a name to identify the primary gateway. By default, the name is appended with `-gw-01`, but you can enter any name to identify the primary gateway.
- **WAN Interface**: Select the WAN interface.
-
**Use DHCP for IP**: Enable to use DHCP to obtain the IP address.
If you do not enable DHCP, complete the following fields:
- **WAN IP Address**: Enter the WAN IP address.
- **WAN Prefix Length**: Enter the WAN prefix length (subnet mask).
- **Default Gateway IP Address**: Enter the gateway IP address.
- **Gateway 2**: If you are using an HA template, a **Gateway 2** section appears. Complete this section for the secondary gateway, as described previously for **Gateway 1**. By default, the gateway name is appended with `-gw-02`, but you can enter any name to identify the secondary gateway.
[See image.](#add-site)
- Click **Add **to add the site.
-
The **Add Site** panel displays the site URL and activation code opens. Copy both values and paste them somewhere safe. You need them when you activate the appliance.
[See image.](#site-url)
[]
![Sites page with Add Site button and list of existing sites](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/adding-site-draft-doc-60374/AddSite.png)
[]
![Add Site panel populated with values to add a site for a standalone ZT400 appliance using DHCP](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/adding-site-draft-doc-60374/AddSitePanel.png)
[]![Add Site panel showing the activation code and URL](/downloads/tech-pubs-drafts/zero-trust-branch-draft-articles/adding-site-draft-doc-60374/activation-add-site.png)