# Configuring an Extranet
Source: https://help.zscaler.com/zia/configuring-extranet
PDF: https://help.zscaler.com/pdf/com/en/1508701.pdf

[Extranet resources](/zia/about-extranet) are created in the ZIA Admin Portal and assigned to locations in order to give organizations and their partners access to each other's applications. To learn more, see [Understanding Extranet Application Support](/zia/understanding-extranet-application-support).
To configure an extranet in the ZIA Admin Portal:
- [1. Create an extranet.](#step-1)
- [2. Configure VPN credentials.](#step-2)
- [3. Assign the extranet to a location.](#step-3)
Post Configuration
After you have configured extranet resources and locations in the ZIA Admin Portal, they become available in the ZPA Admin Portal when configuring [server groups](/zpa/configuring-server-groups) and [application segments](/zpa/configuring-application-segments). You can configure [ZPA access policies](/zpa/configuring-access-policies) to manage extranet applications. When you finish extranet configuration for the Zscaler service, communicate with the partners who manage the extranet resources. They need the VPN credentials associated with the extranet location to create the [IPSec tunnel](/zia/configuring-ipsec-vpn-tunnel) to the Zscaler service.
[]To add an extranet:
- Go to **Administration** > **Extranet**.
- Click **Add Extranet**.
-
In the **Add Extranet **window:
- **Name**: Enter a name for the extranet.
- **Description**: (Optional) Enter a description for the extranet.
- Add a **Traffic Selector**.** **You can add more than one:
- **Default**: Enable this to designate a traffic selector as the default. You must select a default traffic selector.
- **Name**: Enter a name for the traffic selector.
- **IP Address Start**: Enter the starting address of the range for the traffic selector.
- **IP Address End**: Enter the ending address of the range for the traffic selector. The value must be greater than the starting address. The range of the traffic selector must include a minimum of 20 IP addresses.
- Add a **DNS Server**. You can add more than one:
- **Default**: Enable this to designate a DNS server as the default. You must select a default DNS server.
- **Name**: Enter a name for the DNS Server.
- **DNS Server 1**: Enter the IP address of the DNS server 1.
- **DNS Server 2**: Enter the IP address of the DNS server 2.
[See image.](#see-image-1)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]Extranet locations must have a VPN credential assigned to them. The VPN credentials must use the FQDN Authentication Type. If you do not already have FQDN type VPN credentials created, see [Adding VPN Credentials](/zia/adding-vpn-credentials).
[]To use extranet resources, the extranet must be assigned to a location.
To assign an extranet to a location:
- Go to **Administration **> **Location Management**.
- [Add a new location](/zia/configuring-locations) or edit an existing one.
-
For **Location Type**, select **Extranet **from the drop-down menu.
The **Extranet **section appears.
-
In the **Extranet **section, select the **Extranet Resource** that you would like to use for the location.
[See image.](#see-image-2)
- Select a **Traffic Selector **and **DNS Server **from the drop-down menu, or use the defaults.
-
In the **Addressing **section:
-
**Static IP Addresses and GRE Tunnels**: Choose the IP addresses of your local gateway. Do not choose a shared public IP address for a specific tenant’s location.
The static IP addresses that appear in the drop-down menu are provisioned for your organization. To learn more, see [Self-Provisioning of Static IP Addresses](/zia/self-provisioning-static-ip-addresses). If you want Zscaler to provision your static IP addresses, submit them to Zscaler Support to be properly added to the menu. If the Zscaler Client Connector traffic does not match any of the IP addresses listed here, the location is tagged as "Road Warrior" in the logs.
- **VPN Credentials**: Select the appropriate VPN credential** **for the extranet you are using.
[See image.](#see-image-3)
-
In the **Gateway Options **section:
- **Enforce Firewall Control**: [Firewall control](/zia/about-firewall-filtering) is automatically enabled for extranet locations and cannot be disabled.
- **Enable IPS Control**: Because firewall control is enabled, select to enable the service's [IPS Control](/zia/about-ips-control).
[See image.](#see-image-4)
-
Click **Save** and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
After a location is assigned to an extranet, it is automatically added to a dynamic location group for the assigned extranet resource. The Zscaler service creates one if a dynamic location group for the extranet does not already exist.
[]![The Add Extranet window showing the Traffic Selector and DNS Server sections](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-add-extranet.png)
[]![The Extranet section for an extranet location](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-location-extranet-section.png)
[]![The Addressing Section for an extranet location showing Static IP Addresses & GRE Tunnels and VPN Credentials](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-extranet-location-adressing-section.png)
[]![The Gateway Options section with Enforce Firewall Control and Enable IPS Control for an extranet location](/downloads/zia/traffic-forwarding/extranet/configuring-extranet/ZIA-extranet-location-gateway-options.png)