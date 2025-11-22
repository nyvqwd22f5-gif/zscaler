# About GRE Tunnels
Source: https://help.zscaler.com/zia/about-gre-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1401921.pdf

[Watch a video about GRE Tunnels and Static IP.](https://fast.wistia.net/embed/iframe/4lx8k9aqum)
The GRE Tunnels page allows you to self-provision the GRE tunnels for your organization via the ZIA Admin Portal. You can use the GRE tunnels to forward internet traffic from your corporate network to the Zscaler service.
The GRE Tunnels page provides the following benefits and enables you to:
- Self-provision GRE tunnels from your organization to the geographically nearest Zscaler data centers.
- Configure primary and secondary GRE tunnels from a single static IP address to support failover if one tunnel becomes unavailable.
- Configure multiple GRE tunnels using a CSV file, thereby simplifying the configuration effort for the administrator.
About the GRE Tunnels Page
On the GRE Tunnels page (Administration > Static IP & GRE Tunnels), you can do the following:
- [Add a GRE tunnel](/zia/self-provisioning-gre-tunnels).
- Import a CSV file.
- Download the CSV file.
- Download a sample CSV file to create your custom CSV file.
- Search for a configured GRE tunnel.
- View a list of all GRE tunnels configured for your organization. For each GRE tunnel, you can see the following details:
- **Static IP**: The static IP address associated with the GRE tunnel.
- **Primary Data Center VIP**: The virtual IP address of the primary data center for the GRE tunnel.
- **Secondary Data Center VIP**: The virtual IP address of the secondary data center for the GRE tunnel.
- **Managed By**: Indicates if self or a specific Zscaler partner manages it.
- **Last Modified Time**: The time at which the GRE tunnel was last modified.
- **Last Modified By**: The username of the admin who modified the GRE tunnel last.
- **Description**: Additional notes or information about the GRE tunnel.
- [Edit a configured GRE tunnel](/zia/editing-deleting-duplicating-items).
- [Modify the table and its columns](/zia/using-tables).
- Go to the [Static IP page](/zia/about-static-ip).
![Screenshot of the GRE Tunnels page](/downloads/zia/traffic-forwarding/about-gre-tunnels/ZIA-Self-Provision-GRE-Tunnel.png?1613739211)