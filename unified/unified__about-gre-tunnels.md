# About GRE Tunnels
Source: https://help.zscaler.com/unified/about-gre-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1495326.pdf

The GRE Tunnels page allows you to self-provision the GRE tunnels for your organization via the Admin Portal. You can use the GRE tunnels to forward internet traffic from your corporate network to the Zscaler service.
The GRE Tunnels page provides the following benefits and enables you to:
- Self-provision GRE tunnels from your organization to the geographically nearest Zscaler data centers.
- Configure primary and secondary GRE tunnels from a single static IP address to support failover if one tunnel becomes unavailable.
- Configure multiple GRE tunnels using a CSV file, thereby simplifying the configuration effort for the administrator.
About the GRE Tunnels Page
On the GRE Tunnels page (Infrastructure > Internet & SaaS > Traffic Forwarding > Static IPs & GRE Tunnel > GRE Tunnels), you can do the following:
- [Add a GRE tunnel](/unified/self-provisioning-gre-tunnels).
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
- Edit a configured GRE tunnel.
- [Modify the table and its columns](/unified/using-tables).
- Go to the [Static IP](/unified/about-static-ip) page.
![Screenshot of the GRE Tunnels page](/downloads/zia/traffic-forwarding/about-gre-tunnels/ZIA-Self-Provision-GRE-Tunnel.png?1613739211)