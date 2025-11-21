# Configuring Firewall Policies
Source: https://help.zscaler.com/zia/configuring-firewall-policies
PDF: https://help.zscaler.com/pdf/com/en/1399871.pdf

[Watch a video about Firewall Policies](https://fast.wistia.net/embed/iframe/67lc77bxsf)
Configuring firewall policies requires configuring the following policies as applicable: Firewall Filtering, NAT Control, DNS Control, and IPS Control policies. For FTP Control settings within Firewall, see [About FTP Control](/zia/about-ftp-control).
To configure firewall policies:
- Configure the resources that the policies reference:
- Users, Groups, Departments, Locations, and Sublocations for your firewall policies.
- Time Intervals.
- Network Applications. You can create network application groups as needed.
- Network Services. You can modify network services to edit services, add custom services, and create groups.
- Source and Destination IPv4 Groups.
- [IPv6 Configuration](/zia/understanding-ipv6-support)
- Define the rules for each policy:
- [Firewall Filtering Policy](/zia/configuring-firewall-filtering-policy)
- [NAT Control Policy](/zia/configuring-nat-control-policy)
- [DNS Control Policy](/zia/configuring-dns-control-policy)
- [IPS Control Policy](/zia/configuring-ips-control-policy)
-
By default, the Zscaler service *listens to* the following ports:
- Port 80 for HTTP traffic
- Port 443 for HTTPS traffic
- Port 53 for DNS traffic
- Port 21 for FTP traffic
- Port 554 for RTSP traffic
- Port 1723 for PPTP traffic
If your organization uses other or additional ports for these types of traffic, you can configure the service to use [custom ports](/zia/configuring-custom-ports) for these services.
- [Enable the firewall per location.](/zia/enabling-firewall-locations)
Advanced Firewall is required to configure and apply policies based on users, groups, departments, or network applications.