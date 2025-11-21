# Viewing Sublocations
Source: https://help.zscaler.com/zia/viewing-sublocations
PDF: https://help.zscaler.com/pdf/com/en/1531209.pdf

You can add sublocations to an existing parent location using your organization's internal IP address range. Organizations can leverage sublocations to implement various policies based on IP addresses, enforce authentication for selective networks, and enforce bandwidth control to ensure unused bandwidth is available for the parent location. To learn more, see [Understanding Sublocations](/zia/understanding-sublocations).
You can [add sublocations](/zia/configuring-sublocations) individually or import [multiple locations and sublocations](/zia/configuring-multiple-locations-and-sublocations) using a CSV file. You can view up to 100 sublocations per page.
To view the sublocations created for the location:
- Go to **Administration** > **Location Management** > **Locations**.
-
On the** Locations** page, click the sublocation number in the **Sublocations **column within the locations table.
The **View Sublocation** page appears, displaying all the sublocations created for the location.
- On the **View Sublocation** page, you can view the following for each sublocation:
- **Name**: The name of the sublocation.
- **IP Addresses**: The internal IP addresses for the sublocation.
- **Proxy Ports**: The [subscribed proxy ports](/zia/configuring-dedicated-proxy-ports) for the parent location, if applicable.
- **Use XFF from Client Request**: Whether the XFF header is enabled for the parent location.
- **Authentication**: Whether the **Authentication** feature is enabled for the sublocation. If you are also using the **Enable IP Surrogates** feature, this column displays the specified **Idle Time to Disassociation**.
- **Firewall Filtering**: Whether the **Firewall Control** feature is enabled for the location.
- **Bandwidth**: Bandwidth limitations for the sublocation. If the **Enforce Bandwidth Control **option is enabled for the sublocation, the download and upload bandwidth limits are displayed in Mbps.
- **IPS Control**: Whether the **IPS Control** feature is enabled for the sublocation.
- **Group**: The location group assigned to the sublocation.
- **Location Type**: The primary traffic type of the sublocation.
- **Scope Type**: The scope type of the sublocation. This field is only available for the** Workload traffic type **location type.
- **Description**: Additional notes or information about the location.
You can use the search bar to search for and select a specific sublocation.
[See image.](#Image)
[]![Locations page with sublocations displayed within table](/downloads/zia/traffic-forwarding/location-management/viewing-sublocations/ZIA-viewing-sublocations-view-sublocations-page.png)
![Image]()
![Image]()