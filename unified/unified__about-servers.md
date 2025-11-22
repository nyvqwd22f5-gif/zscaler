# About Servers
Source: https://help.zscaler.com/unified/about-servers
PDF: https://help.zscaler.com/pdf/com/en/1492246.pdf

You must configure servers that host the applications you want to make available for Private Applications, whether the servers are in your enterprise data center or in a virtual public cloud (VPC).
Server configurations provide the following benefits and enable you to:
- Explicitly define servers and server groups where one or more applications are hosted (e.g., explicit server management, load balancers in front of multiple applications, and no-default-route/no-external-dns environments with a transparent proxy).
- Provide mapping of applications to specific servers and App Connector groups when paired with a server group.
- Dynamically discover applications through DNS when an empty server group is defined with Dynamic Server Discovery.
You have two main methods for server configuration:
- Explicitly define servers and server groups: You can explicitly define every server that hosts one or more applications. For each server, you provide a name as well as an IP address or fully qualified domain name (FQDN). Then, you can manually arrange those servers into server groups.
- Enable Dynamic Server Discovery: Instead of explicitly defining each server, you can enable dynamic server discovery so that Private Applications can discover the appropriate servers for your applications as users request them. For this method, you only need to create an empty server group that has dynamic server discovery enabled.
Choose the method that is best suited for our organization's needs. Both configuration methods can be completed within the Admin Portal, either in the Servers page or the Applications page.
- Configuring servers in the Servers page (Policies > Access Control > Private Applications > Servers):
- To learn more about explicitly defining your servers and creating server groups, see [Explicitly Defining Servers](/unified/explicitly-defining-servers) and [Configuring Server Groups](/unified/configuring-server-groups).
- To learn more about enabling dynamic server discovery, see [Enabling Dynamic Server Discovery](/unified/enabling-dynamic-server-discovery).
- Configuring servers when adding a new application segment and defining your applications:
- To learn more about configuring servers within an application segment, see [Configuring Application Segments](/unified/configuring-defined-application-segments).
After configuration, you can view a list of configured servers and server groups on the Servers and Server Groups page, respectively, and make any necessary changes.
About the Servers Page
On the Servers page (Policies > Access Control > Private Applications > Servers), you can do the following:
- [Add a new server** **](/unified/enabling-dynamic-server-discovery)[and explicitly define it](/unified/enabling-dynamic-server-discovery) to support one or more of your applications.
- View a list of all servers that were explicitly defined for your organization. For each server, you can see the following:
- **Name**: The server name
- **Status**: Indicates that the server is enabled or disabled
- **Domain or IP Address**: The fully qualified domain name (FQDN) or IP address of the server
If a server is missing required settings, the incomplete configuration icon appears next to the name within the table. Edit the server to resolve the configuration issues.
- Filter the information that appears in the table. By default, no filters are applied.
- [Edit an existing server](/unified/editing-servers).
- Delete a server.
- Expand all of the rows in the table to see more information about each server.
![Using the Servers page within the ZPA Admin Portal](/downloads/unified/policies/private-applications/application-management/servers-server-groups/servers/about-servers/servers-page.png)