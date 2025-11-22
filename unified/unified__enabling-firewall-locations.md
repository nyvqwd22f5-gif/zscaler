# Enabling the Firewall for Locations
Source: https://help.zscaler.com/unified/enabling-firewall-locations
PDF: https://help.zscaler.com/pdf/com/en/1494036.pdf

The firewall can be enabled on a per-location basis.
Before Enabling the Firewall
- Ensure you have configured the following policy resources:
- [Users](/unified/about-users), [Groups](/unified/about-groups), [Departments](/unified/about-departments), [Locations](/unified/about-locations), and [Sub-locations](/unified/understanding-sub-locations) for your firewall policies
- [Time Intervals](/unified/defining-time-intervals)
- Network Applications. You can create [network application groups](/unified/about-network-application-groups) as needed.
- Network Services. You can [modify network services](/unified/about-network-services) to edit services, add custom services, and create groups.
- [Source](/unified/configuring-source-ip-groups) and [Destination IPv4 Address Groups](/unified/configuring-destination-ip-groups)
- [IPv6 Configuration](/unified/understanding-ipv6-support)
- Ensure you have defined the necessary rules for each policy:
- [Firewall Filtering Policy](/unified/configuring-firewall-filtering-policy)
- [NAT Control Policy](/unified/configuring-nat-control-policy)
- [DNS Control Policy](/unified/configuring-dns-control-policy)
- [IPS Control Policy](/unified/configuring-ips-control-policy)
- If your organization uses non-standard ports for HTTP, HTTPS, DNS, FTP, RTSP, or PPTP traffic, ensure you have configured the service to use [custom ports](/unified/configuring-custom-ports) for these services.
Enabling the Firewall for a Location
To enable the firewall for a location:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management **>** Location**.
-
Click the **Edit** icon next to the location you want to enable.
[See image.](#edit-icon)
- Select** Enforce Firewall Control** to enable the service's [firewall controls](/unified/about-firewall-filtering).
-
Select **Enable IPS Control** to enable the service's [IPS controls](/unified/about-ips-control). (Available with the Advanced Firewall subscription).
[See image.](#gateway-options)
- Click **Save** and activate the change.
[]![Screenshot of Zscaler firewall location section highlighting edit icon](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/how-do-i-enable-firewall-locations/firewall_location_edit_screenshot.png)
[]![Enabling firewall and IPS control](/downloads/zia/policies/firewall/configuring-firewall-policies/gateway-options.png)