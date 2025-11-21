# Understanding Sub-Locations
Source: https://help.zscaler.com/unified/understanding-sub-locations
PDF: https://help.zscaler.com/pdf/com/en/1495521.pdf

[]Sub-locations enable an organization to create new locations that reference IP addresses that are encapsulated within a [GRE](/unified/configuring-gre-tunnels) or [IPSec](/unified/configuring-ipsec-vpn-tunnel) tunnel, or that are passed to the Zscaler service through X-Forwarded-For (XFF) headers.
For example, an organization can define a sub-location for its corporate network, and another sub-location for its guest network, even if their traffic goes through the same GRE or IPSec tunnel. The organization can then use these sub-locations to do the following:
- Implement different policies based on IP addresses
- Enforce authentication on the internal corporate network, while disabling it for the guest network
- Enforce bandwidth control for sub-locations while ensuring that unused bandwidth remains available to the parent location
- Provide reporting information for different internal networks/offices when they share the same egress IP address
A few things to keep in mind regarding sub-locations:
- Sub-locations cannot have overlapping IP addresses within a location.
- Sub-locations can reference IP address ranges (e.g., 10.10.20.2-10.10.20.250).
- When you add a sub-location, the service automatically creates the other sub-location for all other IP addresses that are sent to the cloud from the location that is not already defined in the sub-location. You can rename the other sub-location if desired.
If the Enable IPv6 option is enabled for the [location](/unified/configuring-locations), the service automatically creates the other6 sub-location in addition to the other sub-location. You can rename the other6 sub-location if desired.
- You can use a previously deleted sub-location name when you create a new sub-location, but you cannot use a deleted name when you edit an existing one. To learn more, see [Naming Locations & Sub-Locations](/unified/about-locations#naming-locations-sub-locations).
- While IP addresses within a location cannot overlap, the same IP address can exist in multiple locations.
You can [add sub-locations](/unified/configuring-sub-locations) individually or [import multiple locations and sub-locations using a CSV file](/unified/configuring-multiple-locations-and-sub-locations).
On the [Locations](/unified/about-locations) page, when you click the sublocations number within the table, the sub-locations for the location appear. For sub-location lists, you can view up to 100 sub-locations on a page.