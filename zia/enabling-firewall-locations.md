# Enabling the Firewall for Locations
Source: https://help.zscaler.com/zia/enabling-firewall-locations
PDF: https://help.zscaler.com/pdf/com/en/1399931.pdf

The firewall can be enabled on a per-location basis.
Before Enabling the Firewall
- Ensure you have configured the following policy resources:
- [Users](/zia/about-users), [Groups](/zia/about-groups), [Departments](/zia/about-departments), [Locations](/zia/about-locations), and [Sublocations](/zia/understanding-sublocations) for your firewall policies
- [Time Intervals](/zia/how-do-i-define-time-intervals)
- Network Applications. You can create [network application groups](/zia/about-network-application-groups) as needed.
- Network Services. You can [modify network services](/zia/about-network-services) to edit services, add custom services, and create groups.
- [Source](/zia/configuring-source-ip-groups) and [Destination IPv4 Address Groups](/zia/configuring-destination-ip-groups)
- [IPv6 Configuration](/zia/understanding-ipv6-support)
- Ensure you have defined the necessary rules for each policy:
- [Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy)
- [NAT Control Policy](/zia/configuring-nat-control-policy)
- [DNS Control Policy](/zia/configuring-dns-control-policy)
- [IPS Control Policy](/zia/configuring-ips-control-policy)
- If your organization uses non-standard ports for HTTP, HTTPS, DNS, FTP, RTSP, or PPTP traffic, ensure you have configured the service to use [custom ports](/zia/configuring-custom-ports) for these services.
Enabling the Firewall for a Location
To enable the firewall for a location:
- Go to **Administration **>** Location**.
- Click the **Edit** icon next to the location you want to enable.
![The Zscaler firewall location section highlighting edit icon](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/firewall/firewall-policies/how-do-i-enable-firewall-locations/firewall_location_edit_screenshot.png)
- Select** Enforce Firewall Control** to enable the service's [firewall controls](/zia/about-firewall-control).
- Select **Enable IPS Control** to enable the service's [IPS controls](/zia/about-ips-control). (Available with the Advanced Firewall subscription)
![Enabling firewall and IPS control](/downloads/zia/policies/firewall/configuring-firewall-policies/gateway-options.png)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).