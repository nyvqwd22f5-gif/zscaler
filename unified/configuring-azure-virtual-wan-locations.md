# Configuring Azure Virtual WAN Locations
Source: https://help.zscaler.com/unified/configuring-azure-virtual-wan-locations
PDF: https://help.zscaler.com/pdf/com/en/1495571.pdf

To configure an Azure Virtual WAN (VWAN) location:
You must complete the procedure for [Integrating with Microsoft Azure Virtual WAN](/unified/integrating-microsoft-azure-virtual-wan) before you can sync and configure tunnels for your Azure hubs.
-
Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
If you clicked on the hub sites hyperlink within the **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Partner Integrations** > [Azure Virtual WAN](/unified/integrating-microsoft-azure-virtual-wan) tab, you are automatically redirected to this page.
-
Click the **Azure Virtual WAN Locations** tab.
All newly synced Azure hubs have their tunnel configuration listed as **Not Configured**.
[See image.](#VWAN_UnconfiguredLocations)
The date and time of the **Last Sync** and **Last Refresh** is always displayed in the upper-right corner next to the search field. If you are not seeing your synced hub locations, click **Sync** to manually re-sync the information or click **Refresh** to update the tunnel configuration information.
[See image.](#VWAN_SyncAndRefresh)
-
Within the table, find the Azure hub location you want to configure an IPSec tunnel for and click the **Edit** icon.
The **Edit Azure Hub** window appears.
-
In the **Edit Azure Hub** window, click **Start Configuration**. Zscaler will immediately begin to set up IPSec tunnel configuration objects for the selected Azure hub.
[See image.](#VWAN_StartConfiguration)
When you start the configuration the status changes to **In Progress**. During this time, the Zscaler service will:
- Check with Azure to obtain hub configuration information.
- Find the closest Zscaler data center (DC) and configure the hub to create an outbound tunnel to that DC.
- Fetch the IPSec pre-shared key for the VPN site from the hub.
- Provision the hub's IP address for the proper Zscaler cloud and organization.
- Create the VPN credentials using the IPSec pre-shared key associated to the VPN site and the hub's IP address.
- Create a new Zscaler location for the hub and associate the VPN credentials to it.
-
Click **Done**.
After the configuration completes, the **Tunnel Status** changes to **Configured** and the **IP Address** displays the relevant information for that IP. However, **VPN Connection** will remain unlisted, or is set as unknown, at this time.
-
Activate the change.
The **VPN Connection** column displays the primary tunnel status for the configured Azure hub locations.
You can view all Azure hub locations from this tab under the **Locations** tab. The [Locations](/unified/about-locations) page allows you apply Zscaler service features, such as enforcing [authentication](/unified/about-provisioning-and-authenticating-users), enabling [SSL Inspection](/unified/about-ssl-inspection), etc. to any locations associated to the hubs.
[]![Azure Virtual WAN Locations tab within the ZIA Admin Portal](/downloads/zia/traffic-forwarding/locations/configuring-azure-virtual-WAN-locations/zia-azurevwan-not-configured-locations.png)
[]![Azure Virtual WAN Locations tab within the ZIA Admin Portal](/downloads/zia/traffic-forwarding/locations/configuring-azure-virtual-WAN-locations/zia-azure-sync-refresh-locations.png)
[]![Edit Azure Hub window within the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-azure-vwan-locations/zia-azure-editlocation-startconfig_0.png)