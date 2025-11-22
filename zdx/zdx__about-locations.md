# About Locations
Source: https://help.zscaler.com/zdx/about-locations
PDF: https://help.zscaler.com/pdf/com/en/1379346.pdf

[Watch a video about Locations in ZDX.](https://fast.wistia.net/embed/iframe/9zellefvwh)
Locations identify the various networks from which your organization sends its internet traffic. When an organization forwards its traffic to the Zscaler service through a GRE or IPSec tunnel, Zscaler provisions your organization's IP addresses, which are then displayed as locations in the ZDX Admin Portal. You can view sublocation information and perceive individual traffic information from a known or unknown location.
Locations provide the following benefits and enables you to:
- Identify locations from which your organization sends its traffic.
- Search for a location or sublocation.
- Sort and customize columns to export a list of locations into a CSV file.
About the Locations Page
On the Locations page (Administration > Location Management), you can do the following:
- Download a list of locations and sublocations in CSV format.
- Manage filters for the Locations list.
- Search by Name or IP address for a specific location or sublocation. Click the **X** icon in the Search bar to cancel and reset.
- View a list of all locations and sublocations that were configured for your organization. You can see:
- **Name**: The name of the location or sublocation.
- **Sublocations**: The number of sublocations assigned to the location.
- **IP Addresses**: The static IP addresses for your local gateway for the location.
- **Proxy Ports**: The [subscribed proxy ports](/zia/configuring-dedicated-proxy-ports) for the location, if applicable.
- **Use XFF from Client Request**: Indicates whether the [Use XFF from Client Request](/zia/how-do-i-add-location#EnableXFFForwarding) feature is enabled for the location.
- []**Authentication**: Indicates whether the [Enforce Authentication](/zia/how-do-i-add-location#EnforceAuthentication) feature is enabled for the location.
- **Firewall Filtering**: Indicates whether the [Enforce Firewall Control](/zia/how-do-i-add-location#EnforceFirewallControl) feature is enabled for the location.
- **Bandwidth**: If the [Enforce Bandwidth Control](/zia/how-do-i-add-location#EnforceBandwidthControl) feature is enabled for the location, the download and upload bandwidth limits are displayed in Mbps.
- **Group**: The location group associated with the location and its sublocations.
- **Location Type**: The type of location associated with the location and its sublocations.
- View the sublocations assigned to the location.
- View details about a location by clicking the **View** icon.
- Customize which columns to display.
![Location Management in ZDX Admin Portal](/downloads/zdx/administration/about-locations/ZDX-LocationManagement_0.jpg)