# About IP Pool
Source: https://help.zscaler.com/zia/about-ip-pool
PDF: https://help.zscaler.com/pdf/com/en/1401531.pdf

IP pools are used by the [Source IP Anchoring](/zia/about-source-ip-anchoring) feature for transparent traffic. When an incoming DNS request hits any of these rules that are preconfigured to forward the traffic to Zscaler Private Access (ZPA), Zscaler assigns an ephemeral IP address to the DNS request from the respective IP pool before forwarding it to ZPA.
IP pools provide the following benefits and enable you to:
- Resolve domain names of Source IP Anchoring-enabled ZPA applications to an ephemeral IP address selected from a preconfigured IP pool.
- Define custom IP address ranges for IP pools used for location traffic and remote user traffic.
- Extend Source IP Anchoring support to non-web traffic from locations and remote users by leveraging forwarding rules.
- Define fallback IP pools to ensure that the source IP-anchored traffic redirects to ZPA during ZIA control plane maintenance.
You can view or edit the predefined IP pools that are associated with the following preconfigured DNS rules:
- ZPA Resolver for Locations
- ZPA Resolver for Road Warrior
- Fallback ZPA Resolver for Locations
- Fallback ZPA Resolver for Road Warrior
You can edit the default name of the IP pools or even the IP pool range based on your needs. Any change in the IP pool is reflected in the Action column of the associated DNS rule when the rule is enabled.
Configuring the IP pool with public IP addresses is not recommended as it can lead to a conflict during normal DNS resolution if the domain names (other than those of applications with Source IP Anchoring enabled) resolve to a public IP address that matches the address configured in the IP pool.
About the IP Pool Page
- [Add an IP pool](/zia/adding-ip-pool).
- Search for an IP pool.
- View a list of all the IP pools. For each IP pool, you can view:
- **Name**: The name of the IP pool. You can sort this column.
- **IP Address**: The range of IP addresses assigned to this pool. You can configure a maximum of one IP address range for an IP pool.
- **Description**: Additional notes or information about the IP pool.
- **Type**: The type of IP pool. This field displays **Extranet **if the IP pool was created either manually or automatically for [Extranet Application Support](/zia/understanding-extranet-application-support). It is left blank for IP pools created automatically for ZPA.
- [Modify the table and its columns](/zia/how-do-i-use-tables-admin-portal).
- [Edit the IP pool](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal).
- View the **ZPA IP Pool for Extranet Location Traffic**.
- Go to the [Source IPv4 Groups](/zia/about-source-ip-groups#ipv4), [Source IPv6 Groups](/zia/about-source-ip-groups#ipv6), [Destination IPv4 Groups](/zia/about-destination-groups#ipv4), and [Destination IPv6 Groups](/zia/about-destination-groups#ipv6) pages.
![The IP Pool page showing the option to add an IP pool and view IP pools](/downloads/zia/policies/firewall/firewall-policy-resources/about-ip-pool/ZIA_IP-FQDN_about-ip-pool.png)