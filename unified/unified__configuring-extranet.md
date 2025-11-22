# Configuring an Extranet
Source: https://help.zscaler.com/unified/configuring-extranet
PDF: https://help.zscaler.com/pdf/com/en/1518661.pdf

[Extranet resources](/unified/about-extranet) are created in the Admin Portal and assigned to locations in order to give organizations access to resources managed by partners that are not integrated with the Zscaler service. To learn more, see [Understanding Extranet Application Support](/unified/understanding-extranet-application-support).
To configure an extranet in the Admin Portal:
- [1. Create an extranet.](#step-1)
- [2. Configure VPN credentials.](#step-2)
- [3. Assign the extranet to a location.](#step-3)
Post Configuration
After you have configured extranet resources and locations in the Admin Portal, they become available to Private Applications when configuring [server groups](/unified/configuring-server-groups) and [application segments](/unified/configuring-defined-application-segments). You can configure [Private Applications access policies](/unified/configuring-access-policies) to manage extranet applications. When you finish extranet configuration for the Zscaler service, communicate with the partners who manage the extranet resources. They need the VPN credentials associated with the Extranet location to create the [IPSec tunnel](/unified/configuring-ipsec-vpn-tunnel) to the Zscaler service.
[]To add an extranet:
- Go to **Infrastructure **> **Locations** > **Extranet**.
- Click **Add Extranet**.
-
In the **Add Extranet **window:
- **Name**: Enter a name for the extranet.
- **Description**: (Optional) Enter a description for the extranet.
- Add a **Traffic Selector**.** **You can add more than one:
- **Default**: Enable this to designate a traffic selector as the default. You must select a default traffic selector.
- **Name**: Enter a name for the traffic selector.
- **IP Address Start**: Enter the starting address of the range for the traffic selector.
- **IP Address End**: Enter the ending address of the range for the traffic selector. The value should be greater than the starting address. The range of the traffic selector must include a minimum of 20 IP addresses.
- Add a **DNS Server**. You can add more than one:
- **Default**: Enable this to designate a DNS server as the default. You must select a default DNS server.
- **Name**: Enter a name for the DNS Server.
- **DNS Server 1**: Enter the IP address of the DNS server 1.
- **DNS Server 2**: Enter the IP address of the DNS server 2.
[See image.](#see-image-1)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]Extranet locations must have a VPN credential assigned to them. The VPN credentials must use the FQDN Authentication Type. If you do not already have FQDN type VPN credentials created, see [Adding VPN Credentials](/unified/adding-vpn-credentials).
[]To use extranet resources, the extranet must be assigned to a location.
To assign an extranet to a location:
- Go to the** **[Locations](/unified/about-locations)** **page.
- [Add a new location](/unified/configuring-locations) or edit an existing one.
-
For **Location Type**, select **Extranet **from the drop-down menu.
The **Extranet **section appears.
-
In the **Extranet **section, select the **Extranet Resource** that you would like to use for the location.
[See image.](#see-image-2)
- Select a **Traffic Selector **and **DNS Server **from the drop-down menu, or use the defaults.
-
In the **Addressing **section, select the appropriate **VPN Credentials **for the extranet you are using.
[See image.](#see-image-3)
-
Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
After a location is assigned to an extranet, it is automatically added to a dynamic location group for the assigned extranet resource. The Zscaler service creates one if a dynamic location group for the extranet does not already exist.
[]![Add Extranet Window](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-add-extranet.png)
[]![Extranet Section in the Add Location Window](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-location-extranet-section.png)
[]![VPN Credentials in the Add Location Window](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-location-extranet-vpn-credentials.png)