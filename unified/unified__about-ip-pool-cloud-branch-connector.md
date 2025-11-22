# About IP Pool for Cloud & Branch Connector
Source: https://help.zscaler.com/unified/about-ip-pool-cloud-branch-connector
PDF: https://help.zscaler.com/pdf/com/en/1516516.pdf

The IP Pool is only used in DNS control policies to forward traffic to Private Applications when the network traffic action under the DNS filtering rule is set as Resolved by ZPA. A default Private Applications IP Pool is automatically created. You can also configure different IP pools for each location based on your requirements. To learn more, see [Networking Deployed Private Service Edges](/unified/networking-deployed-private-service-edges) and [Networking Deployed App Connectors](/unified/networking-deployed-app-connectors).
IP Pool provides the following benefits and enables you to:
- Customize the IP Pool used to provide the synthetic IP address while resolving DNS requests from workloads to Private Applications applications.
- Configure separate IP pools to provide different synthetic IP addresses for resolving DNS requests from workloads to Private Applications applications. based on source location, Location Group, Cloud Connector Group, and Branch Connector Group.
About the IP Pool Page
IP pools allow users to control the IP address space that cloud workloads interact with by offering a customizable space where IP addresses do not overlap.
On the IP Pool page (**Policies**> **Access Control** > **Firewall **> **IP & FQDN Groups** > **IP Pool**), you can do the following:
- [Add an IP Pool](/unified/configuring-ip-pool).
- View a list of all the IP pools. For each IP pool, you can view:
- **Name** The name of the IP pool.
- **IP Addresses**: The range of IP addresses that are assigned to this pool.
- **Description**: Additional notes or information about the IP pool.
- View a specific IP Pool.
- Edit an IP Pool.
You cannot edit or delete the default IP pool.
- Delete an IP Pool.
- Modify the table and its columns.
- Go to the** **[Source IP Groups](/unified/about-source-ip-groups-cloud-branch-connector) page.
- Go to the** **[Destination IP Groups](/unified/about-destination-ip-groups-cloud-branch-connector) page.