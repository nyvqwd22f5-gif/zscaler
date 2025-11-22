# Configuring Sub-Locations
Source: https://help.zscaler.com/unified/configuring-sub-locations
PDF: https://help.zscaler.com/pdf/com/en/1492871.pdf

This article describes how to add a single sub-location. You can add up to 2,000 sub-locations per location. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations#Locations). You can also use a CSV file to import multiple locations and sub-locations. To learn more, see [Configuring Multiple Locations and Sub-Locations](/unified/configuring-multiple-locations-and-sub-locations).
To add a sub-location:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
-
On the **Locations **page, locate the location you want to add a sub-location to, and click the **Edit **icon.
The **Edit Location** window appears.
-
In the **Edit Location** window, select the **Use XFF from Client Request** option if this location uses proxy chaining to forward traffic to the Zscaler service, and you want the service to discover the client RFC1918 IP address from the X-Forwarded-For (XFF) headers that your on-premises proxy server inserts in outbound HTTP requests. The XFF header identifies the client IP address, which can be leveraged by the service to identify the client’s sub-location.
Using the XFF headers, the service can apply the appropriate sub-location policy to the transaction, and if **Enable IP Surrogate** is turned on for the location or sub-location, the appropriate user policy is applied to the transaction. When the service forwards the traffic to its destination, it removes the original XFF header and replaces it with an XFF header that contains the IP address of the client gateway (the organization’s public IP address), ensuring that an organization's internal IP addresses are never exposed to externally.
-
Go back to the **Locations **page and click the **Add Sub-Location **icon for the location.
[See image.](#img2)
The **Add Sub-Location** window appears.
-
In the **Add Sub-Location** window, in the **Location** section:
- **Name**: Enter a name for the sub-location. To learn more, see [Naming Locations & Sub-Locations](/unified/about-locations#naming-locations-sub-locations).
- **Country**: Select the sub-location's country.
- **City/State/Province**: Enter the sub-location's state or province, if applicable.
- **Time Zone**: Select the sub-location's time zone.
-
**City Geolocation**: Enter the city name for geolocation on the map.
This field displays the values in the <City>, <State>, <Country> (<GeoID>) format. For example, Albany, Western Australia, Australia (2077963).
- **Manual Location Groups**: Search for and select the [manual location group](/unified/about-location-groups) names. The sub-location is added to the manual groups you selected. Otherwise, leave the selection as **None**.
-
**Dynamic Location Groups**: This field shows the [dynamic location groups](/unified/about-location-groups) that the sub-location belongs to.
A predefined dynamic location group corresponding to the location type selection is automatically populated, and this field is not editable.
- **Exclude from Manual Location Groups**: Enable or disable the switch. If enabled, the sub-location cannot be added to manual location groups. The sub-location is also removed from any manual groups it's already assigned to. If disabled, the location can be added to any manual groups.
-
**Exclude from Dynamic Location Groups**: Enable or disable the switch. If enabled, the sub-location is not automatically assigned to any matching dynamic location groups. The sub-location is also removed from any dynamic groups it's already assigned to. If disabled, the sub-location is automatically assigned to all matching dynamic groups.
Disabling this option does not impact the association of the location to the pre-defined location groups.
-
**Location Type**: Select a location type from the drop-down menu. You can also search for any one of the following location types:
- **Corporate user traffic**
- **Guest Wi-Fi traffic**
- **IoT traffic**
- **Server traffic**
Selecting a location type assigns the location automatically to a corresponding predefined location group.
When you update an existing location or add a new location, ensure to select a value for this field.
- **Description**: (Optional) Enter additional notes or information. The description cannot exceed 1,024 characters.
In the **Addressing** section:
- **Internal IP Addresses**:** **Add the internal IP addresses for the sub-location.
- Click **Add Items**.
In the **Gateway Options** section:
- []**Enforce Authentication**:** **Enable to require users from this location to authenticate to the service. To learn more, see [About Provisioning and Authenticating Users](/unified/about-provisioning-and-authenticating-users).
- **Enable Caution**: If you disabled **Enforce Authentication**, you can enable this feature and set the [Caution Interval](/unified/configuring-caution-notification#caution-interval) to be greater than one minute to display a caution notification to unauthenticated users. To learn more, see [Configuring End User Notifications](/unified/configuring-end-user-notifications). If you enable this feature, you must use one of the following methods to forward traffic to the service:
- A [GRE](/unified/configuring-gre-tunnels) or [IPSec](/unified/configuring-ipsec-vpn-tunnel) tunnel without NAT
- Forward [proxy chaining](/unified/configuring-proxy-chaining) with the **Use XFF from Client Request** option turned on for the parent location
-
[]**Enable AUP**: If you disabled **Enforce Authentication**, you can enable this feature to display an Acceptable Use Policy (AUP) for unauthenticated traffic and require users to accept it. If you enable this feature:
- In **Custom AUP Frequency (Days)** specify, in days, how frequently the AUP is displayed to users.
- A **First Time AUP Behavior** section appears, with the following settings:
- If **Block Internet Access** is enabled, the Zscaler service disables all access to the internet, including non-HTTP traffic, until the user accepts the AUP that is displayed to them.
- If **Force SSL Inspection **is enabled, to make [SSL Inspection](/unified/about-ssl-inspection) enforce an AUP for HTTPS traffic.
You can customize the AUP notification message on the End User Notifications page. To learn more, see [Configuring the Acceptable Use Policy](/unified/configuring-acceptable-use-policy).
- **Enable Digest Authentication**: If you enabled **Enforce Authentication**, select this option to enforce digest authentication on all web traffic explicitly forwarded from the location and its associated dedicated ports.
-
**Enable Basic Authentication**: If you enabled **Enforce Authentication**, select this option to enforce basic authentication on all web traffic explicitly forwarded from the sub-location and its associated dedicated ports.
The following caveats apply to Basic Authentication:
- The Internet & SaaS API Security feature must be enabled for your organization.
- The Hosted DB user repository type with the Form-Based authentication type is supported.
- The hosted users/passwords must be created or imported using a CSV file.
- The users must be enrolled for basic authentication using the following APIs:
- `https://admin.``<cloud>``.net/api/v1/authenticatedSession`
- `https://admin.``<cloud>``.net/api/v1/users/<userid>/enroll`
For the authenticatedSession API endpoint, admin user credentials and an API key are required. For the users API endpoint, you can get the user IDs using the browser developer tool on the User Management page.
After the user enrollment, their credentials are used for the basic proxy authentication.
Here is an example of basic proxy authentication:
curl -ivk -x gateway.<cloud>.net:<port> -A "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/109.0" -U "<username>@<domain.com>:<passwd>" example.com
The user credentials are transferred in clear text when using basic authentication. So, you must use an IPSec tunnel from a router or firewall or an encrypted tunnel from Cloud Connector or Branch Connector if you are forwarding the authenticated traffic over public internet.
-
**Enable IP Surrogate**: If you enabled **Enforce Authentication**, select this option if you want to map users to device IP addresses for a sub-location. To learn more, see [About Surrogate IP](/unified/about-surrogate-ip).
If you enable this feature on a sub-location:
- In **Idle Time to Disassociation**, specify how long after a completed transaction the service retains the IP address-to-user mapping.
-
If you want to use the existing IP address-to-user mapping (acquired from the surrogate IP) to authenticate users sending traffic from known browsers, enable **Enforce Surrogate IP for Known Browsers**.
With this feature enabled, the Zscaler service uses existing IP-to-user mapping for authentication even if users go to sites that support cookies. For example, this allows the service to authenticate without requiring the browser to complete HTTP redirects for every transaction, ensuring performance for users who connect over high-latency satellite links. If the feature is disabled, the service authenticates users on browsers with cookies or other configured authentication mechanisms.
-
If you enabled **Enforce Surrogate IP for Known Browsers**, in **Refresh Time for re-validation of Surrogacy**,** **specify the length of time that the Zscaler service can use IP address-to-user mapping for authenticating users sending traffic from known browsers. After the defined period of time elapses, the service refreshes and revalidates the existing IP-to-user mapping so that it can continue to use the mapping for authenticating users on browsers.
The refresh time for the revalidation of IP surrogacy must be shorter than the DHCP lease time, otherwise the wrong user policies might be applied. Also, Zscaler recommends setting the **Refresh Time for re-validation of Surrogacy** to a time period shorter than what you specified for **Idle Time to Disassociation**.
- If you enabled **Enforce Surrogate IP for Known Browsers**, in **Supported Authentication Methods**, select either **Cookie** or **Cookie and Proxy**. Selecting **Cookie and Proxy** prevents additional authentication challenges to traffic using both cookie and non-cookie-based authentication methods after the initial challenge. If **Cookie** is selected, all other methods are required to authenticate after each request.
- **Enable Kerberos Authentication**: If you enabled **Enforce Authentication**, you can enable this feature to enforce Kerberos authentication on all web traffic explicitly forwarded from the location and its associated dedicated ports.
- **Enforce Firewall Control**:** **Select to enable the service's [firewall controls](/unified/about-firewall-filtering).
- **Enable IPS Control**: If you enabled **Enforce Firewall Control**, select to enable the service's [IPS controls](/unified/about-ips-control).
-
**Enable IoT Discovery**: Enable to discover IoT/OT devices, servers, and unmanaged devices (e.g., personal user devices) at this location.
-
**Enforce IoT Policy Control**: Enable to enforce URL Filtering and Cloud App Control policy rules for unauthenticated traffic from IoT devices at this location. To learn more, see [About URL Filtering](/unified/about-url-filtering) and [About Cloud App Control](/unified/about-cloud-app-control).
The **Enforce IoT Policy Control** option appears when the **Enable IoT Discovery** option is enabled.
[See image.](#GatewayOptionsSection-IoT-Discovery)
The **Enable IoT Discovery** and **Enforce IoT Policy Control** options are available only if the IoT discovery and IoT policy control, respectively, are enabled for your organization.
[See image.](#AddSubLocation)
[]In the **Bandwidth Control** section, you can enforce [bandwidth controls](/unified/about-bandwidth-control) for the sub-location:
- If you have [bandwidth control disabled on the parent location](/unified/configuring-locations#EnforceBandwidthControl), you can still select **Enabled** for the sub-location and then specify the maximum bandwidth limits for **Download (Mbps)** and **Upload (Mbps)**.
- If you have [bandwidth control enabled on the parent location](/unified/configuring-locations#EnforceBandwidthControl), you can:
- Select **Use Location Bandwidth** to enable on the sub-location and use the download and upload maximum bandwidth limits as specified for the parent location.
- Select **Override **to enable on the sub-location and then specify the maximum bandwidth limits for **Download (Mbps)** and **Upload (Mbps)**. This bandwidth is dedicated to the sub-location and not shared with others.
- Select **Disable **to exempt the traffic from any Bandwidth Management policies. Sub-location with this option can only use up to a max of available **Shared Bandwidth** at any given time.
When **Use Location Bandwidth** or **Disable** is selected, any unused bandwidth returns to the parent location's bandwidth. You can also view the amount of **Shared Bandwidth** available. The shared bandwidth download/upload limit displayed is the parent location's bandwidth plus all sub-locations that have **Use Location Bandwidth** enabled.
[See image.](#EnableBWCOnSubLoc)
- Click **Save** and activate the change.
[]![Add Sub-Location window in Admin Portal](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-sub-locations/ZIA-Add-Sub-Locations-Window.png)
[]![Add Sub-Location window in Admin Portal](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-sub-locations/add-sub-location-bandwidth-control-section.png)
[]![Locations page with Add Sub-location icon](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-sub-locations/ZIA-Configuring-Sub-Locations-Add-Icon.png)
[]![Screenshot of ZIA Gateway Options in the Add Location Window ](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-locations/ZIA-Add-Location-Gateway-Options-IoT-Discovery.png)