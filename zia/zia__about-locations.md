# About Locations
Source: https://help.zscaler.com/zia/about-locations
PDF: https://help.zscaler.com/pdf/com/en/1399236.pdf

[]Locations identify the various networks from which your organization sends its internet traffic. When an organization forwards its traffic to the Zscaler service through a [GRE](/zia/configuring-gre-tunnels) or [IPSec](/zia/configuring-ipsec-vpn-tunnel) tunnel, Zscaler provisions your organization's IP addresses, which you then add as locations in the ZIA Admin Portal. You can either [add locations individually](/zia/configuring-locations) or [import a CSV file with your locations](/zia/configuring-multiple-locations-and-sublocations).
[]When the Zscaler service receives traffic, it checks whether the traffic is from a known location (a location that is configured on the ZIA Admin Portal), or from an unknown location (remote user traffic). If the traffic is from a known location, the service processes the traffic based on the location settings. For example, the service checks whether the location has authentication enabled and proceeds accordingly. It also applies any location policies that you configure and log Internet activity by location.
If your organization has thousands of locations or sublocations, then the loading time on the Locations page and in any policy that references locations when selected might incur noticeable loading time to retrieve and display the full location list.
Locations provide the following benefits and enable you to:
- Identify the locations from which your organization sends its traffic.
- Associate a VPN credential, Static IP address, and GRE tunnel with a location.
- Create sublocations for private networks.
- Associate Virtual Service Edges with a specific location.
- Establish upload and download bandwidth limits.
- Enable various features such as firewall control, AUP, Caution, authentication and reading the XFF header from forwarded traffic.
Naming Locations & Sublocations
You can use a previously deleted location or sublocation name when you create a new location or sublocation. However, you cannot use a previously deleted name when editing an existing location or sublocation. If you want to use a deleted name for an existing location or sublocation, you must complete the following steps:
- Take note of the existing location’s or sublocation’s attributes.
- [Delete the location or sublocation](/zia/editing-deleting-duplicating-items).
- Create a new [location](/zia/configuring-locations) or [sublocation](/zia/configuring-sublocations) with the deleted name and the proper attributes.
ZIA displays an error if you attempt to use a name that already belongs to an existing location or sublocation. It also displays this error if you attempt to change an existing location’s or sublocation’s name to a previously deleted name without completing the preceding steps.
[See image.](#error)
About the Locations Page
[]On the Locations page (Administration > Location Management), you can do the following:
- [Add a location](/zia/configuring-locations).
- [Import new locations and sublocations, or modify existing locations and sublocations, using a CSV file](/zia/importing-locations-using-a-csv).
- [Download a CSV file that lists your locations and sublocations](/zia/downloading-location-info-to-CSV).
- Download a **Sample Import CSV file** that shows the correct CSV format for adding or modifying locations and sublocations.
- [Filter the list of locations and sublocations](#locations-page-filters).
- Search for a location or sublocation.
-
View a list of all locations and sublocations that were configured for your organization. For each location, you can see the following:
- **Name**: The name of the location or sublocation.
- **Sublocations**: The number of sublocations for the location. If you click the number in this column, the **View Sublocation** window appears.
-
**IP Addresses**: The static IP addresses for your local gateway for the location.
The organization’s shared public IP addresses cannot be used for a specific tenant’s location.
- **Proxy Ports**: The [subscribed proxy ports](/zia/configuring-dedicated-proxy-ports) for the location, if applicable.
- **Use XFF from Client Request**: Indicates whether the [Use XFF from Client Request](/zia/configuring-locations#EnableXFFForwarding) feature is enabled for the location.
- **Authentication**: Indicates whether the [Enforce Authentication](/zia/configuring-locations#EnforceAuthentication) feature is enabled for the location. If you are also using the [Enable IP Surrogates](/zia/configuring-locations#EnableIPSurrogates) feature, this column displays the specified Idle Time to Disassociation.
- **Firewall Filtering**: Indicates whether the [Enforce Firewall Control](/zia/configuring-locations#EnforceFirewallControl) feature is enabled for the location.
- **Bandwidth**: If the [Enforce Bandwidth Control](/zia/configuring-locations#EnforceBandwidthControl) feature is enabled for the location, the download and upload bandwidth limits are displayed in Mbps.
- **Virtual Service Edges**: The [Virtual Service Edges](/zia/about-virtual-service-edge) and [Virtual Service Edge clusters](/zia/about-virtual-service-edge-clusters) for the location, if applicable.
- **IPS Control**: Indicates whether the [IPS control](/zia/about-ips-control) feature is enabled for the location.
-
**Group**: The location group associated with the location and its sublocations.
The Workload Traffic Group is automatically populated for locations with the location type Workload traffic type.
- **Managed By**: The name of the [SD-WAN partner](/zia/about-partner-integration-management) that manages the location.
-
**Location Type**: The primary type of traffic for the location.
The location type, Workload traffic type, automatically applies to a location created in the Zscaler Cloud & Branch Connector Admin Portal.
- **Description**: Additional notes or information about the location.
For location lists, you can view up to 100 locations on a page.
- [Modify the table and its columns](/zia/using-tables).
- [Add a sublocation](/zia/understanding-sublocations).
- [Edit a location or sublocation](/zia/editing-deleting-duplicating-items), including the ability to delete a location.
- Go to the [Location Groups](/zia/about-location-groups) page, to add a new location group or manage existing groups.
- Go to the [Azure Virtual WAN Locations](/zia/configuring-azure-vwan-locations) page, to view and manage your synced Microsoft Azure hub site locations. This tab is only displayed if you have a Microsoft Azure Virtual WAN integration with Zscaler. To learn more, see [About Partner Integrations](/zia/about-partner-integration-management).
![Viewing and managing locations and sublocations within the Zscaler Internet Access (ZIA) Admin Portal](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/about-locations/ZIA-Location-Management-Page.png)
[]To narrow down the list of locations and sublocations, click the **Apply Filter** icon (![Filter icon](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/about-locations/show-filter-icon.png)
). Click **Add Filter** and then select a location attribute from the drop-down menu. After you configure the attribute, the list automatically updates to show relevant locations and sublocations. You can add multiple attributes to narrow down the list even further. To remove a filter, click the **Remove icon** (![Remove icon](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/about-locations/remove-icon-test.png)
).
[]![The error that ZIA displays for location and sublocation names](/downloads/zia/traffic-forwarding/location-management/about-locations/ZIA-Locations-Error.png)