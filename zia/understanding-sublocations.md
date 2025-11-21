# Understanding Sublocations
Source: https://help.zscaler.com/zia/understanding-sublocations
PDF: https://help.zscaler.com/pdf/com/en/1399271.pdf

[]Sublocations enable an organization to create new locations that reference IP addresses that are encapsulated within a [GRE](/zia/configuring-gre-tunnels) or [IPSec](/zia/configuring-ipsec-vpn-tunnel) tunnel, or that are passed to the Zscaler service through X-Forwarded-For (XFF) headers.
For example, an organization can define one sublocation for its corporate network and another sublocation for its guest network, even if their traffic goes through the same GRE or IPSec tunnel. The organization can then use these sublocations to do the following:
- Implement different policies based on IP addresses.
- Enforce authentication on the internal corporate network, while disabling it for the guest network.
- Enforce bandwidth control for sublocations while ensuring that unused bandwidth remains available at the parent location.
- Provide reporting information for different internal networks or offices when they share the same egress IP address.
Key considerations while using sublocations:
- Sublocations cannot have overlapping IP addresses within a location.
- Sublocations can reference IP address ranges (e.g., 10.10.20.2-10.10.20.250).
-
After you add a sublocation, the Zscaler service automatically creates a sublocation named **other** on the Locations page. The **other** sublocation is created, by default, for IP addresses that are sent to the cloud from a location that is not already defined in the sublocation. You can rename the **other** sublocation if desired.
If the **Enable IPv6** option is enabled for your location, the Zscaler service automatically creates a sublocation named **other6** in addition to the **other** sublocation. You can rename the **other6** sublocation if desired.
[See image.](#other-other6-sublocations)
- After you add a sublocation to a location created in the Zscaler Cloud & Branch Connector Admin Portal, the **Workload traffic type** and **Workload Traffic Group** are applied as the default location type and the location group for the sublocation, respectively.
- When you add a sublocation to an **Extranet**-type location, the **Extranet** location type is applied automatically. The extranet sublocation uses the DNS server** **and traffic selector** **of the extranet location it was created for. To learn more, see [Configuring an Extranet](/zia/configuring-extranet).
- You can use a previously deleted sublocation name when you create a new sublocation, but you cannot use a deleted name when you edit an existing one. To learn more, see [Naming Locations & Sublocations](/zia/about-locations#naming-locations-sublocations).
- Although IP addresses within a location cannot overlap, the same IP address can exist in multiple locations.
To learn more, see [Viewing Sublocations](/zia/viewing-sublocations) and [Configuring Sublocations](/zia/configuring-sublocations).
[]
![Other and other6 sublocations added automatically to the Sublocations table on the Locations page](/downloads/zia/traffic-forwarding/location-management/understanding-sub-locations/ZIA-understanding-sublocations-other-other6-sublocations.png)