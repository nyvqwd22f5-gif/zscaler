# About IP Pool
Source: https://help.zscaler.com/cloud-branch-connector/about-ip-pool
PDF: https://help.zscaler.us/pdf/com/en/1420391.pdf

The IP Pool is only used in DNS control policies to forward traffic to ZPA when the network traffic action under the DNS filtering rule is set as Resolved by ZPA. A default ZPA IP Pool is automatically created. You can also configure different IP pools for each location based on your requirements. To learn more, see [Networking Deployed ZPA Private Service Edges](/zpa/networking-deployed-service-edges) and [Networking Deployed App Connectors](/zpa/networking-deployed-connectors).
IP Pool provides the following benefits and enables you to:
- Customize the IP Pool used to provide the synthetic IP address while resolving DNS requests from workloads to ZPA applications.
- Configure separate IP pools to provide different synthetic IP addresses for resolving DNS requests from workloads to ZPA applications based on source location, Location Group, Cloud Connector Group, and Branch Connector Group.
About the IP Pool Page
IP pools allow users to control the IP address space that cloud workloads interact with by offering a customizable space where IP addresses do not overlap.
On the IP Pool page (Administration > IP & FQDN Groups > IP Pool), you can do the following:
- [Add an IP Pool](/cloud-branch-connector/configuring-ip-pool).
- View a list of all the IP pools. For each IP pool, you can view:
- **Name** The name of the IP pool.
- **IP Addresses**: The range of IP addresses that are assigned to this pool.
- **Description**: Additional notes or information about the IP pool.
- View a specific IP Pool.
- [Edit an IP Pool](/cloud-branch-connector/editing-deleting-or-duplicating-items).
You cannot edit or delete the default IP pool.
- [Delete an IP Pool](/cloud-branch-connector/editing-deleting-or-duplicating-items).
- Modify the table and its columns.
- Go to the** **[Source IP Groups](/cloud-branch-connector/about-source-ip-groups) page.
- Go to the** **[Destination IP Groups](/cloud-branch-connector/about-destination-ip-groups) page.
![IP Pool page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/administration/firewall-filtering/about-ip-pool/About%20IP%20Pool_0.jpg)