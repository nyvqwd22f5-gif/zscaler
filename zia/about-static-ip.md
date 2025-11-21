# About Static IP
Source: https://help.zscaler.com/zia/about-static-ip
PDF: https://help.zscaler.com/pdf/com/en/1401916.pdf

[Watch a video about GRE Tunnels and Static IP.](https://fast.wistia.net/embed/iframe/4lx8k9aqum)
You must provision static IP addresses for your organization if you want to [create a GRE tunnel](/zia/self-provisioning-gre-tunnels) or [add a VPN credential](/zia/adding-vpn-credentials) (only for IP-based PSK). IP-based PSK is required for devices that don't support a fully qualified domain name (FQDN)-based PSK.
You can either [self-provision your static IP address](/zia/self-provisioning-static-ip-addresses) on the ZIA Admin Portal or request Zscaler Support to provision it for you.
Static IPs provide the following benefits and enable you to:
- Self-provision static IP addresses to configure GRE tunnels and VPN credentials for your organization.
- Auto-map static IP addresses to a location or manually map them by providing the coordinates of the location.
- Configure multiple static IP addresses using a CSV file, thereby simplifying the configuration effort for the administrator.
About the Static IP Page
On the Static IP page (Administration > Static IP & GRE Tunnels), you can do the following:
- [Add a static IP address](/zia/self-provisioning-static-ip-addresses).
- Import a CSV file.
- Download the CSV file.
- Download a sample CSV file to create your custom CSV file.
- Search for a configured static IP address.
- View a list of all static IP addresses configured for your organization. For each static IP address, you can see the following details:
- **Static IP**: The configured static IP address.
- **City**: The name of the city the static IP address belongs to.
- **Managed By**: Indicates if the static IP address is managed by self or a specific Zscaler partner.
- **Last Modified Time**: The time at which the static IP address was last modified.
- **Last Modified By**: The username of the admin who modified the IP address last.
- **Description**: Additional notes or information about the static IP address.
- [Edit a configured static IP address](/zia/editing-deleting-duplicating-items).
- [Modify the table and its columns](/zia/using-tables).
- Go to the [GRE Tunnels page](/zia/about-gre-tunnels).
![Screenshot of Static IP  page in the ZIA Admin Portal](/downloads/zia/traffic-forwarding/about-static-ip/ZIA-self-provision-static-ip.jpg)