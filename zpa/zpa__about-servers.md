# About Servers
Source: https://help.zscaler.com/zpa/about-servers
PDF: https://help.zscaler.com/pdf/com/en/1483566.pdf

You must configure servers that host the applications you want to make available for ZPA, whether the servers are in your enterprise data center or in a virtual public cloud (VPC).
Server configurations provide the following benefits and enable you to:
- Explicitly define servers and server groups where one or more applications are hosted (e.g., explicit server management, load balancers in front of multiple applications, and no-default-route/no-external-dns environments with a transparent proxy).
- Provide mapping of applications to specific servers and App Connector groups when paired with a server group.
- Dynamically discover applications through DNS when an empty server group is defined with Dynamic Server Discovery.
There are two main methods for server configuration:
- Explicitly define servers and server groups: You can explicitly define every server that hosts one or more applications. For each server, you provide a name as well as an IP address or fully qualified domain name (FQDN). Then, you can manually arrange those servers into server groups.
- Enable Dynamic Server Discovery: Instead of explicitly defining each server, you can enable Dynamic Server Discovery so that ZPA can discover the appropriate servers for your applications as users request them. For this method, you only need to create an empty server group that has Dynamic Server Discovery enabled.
Choose the method that is best suited for your organization's needs. Both configuration methods can be completed within the ZPA Admin Portal, either on the Servers page or the Applications page.
- Configuring servers on the Servers page:
- To learn more about explicitly defining your servers and creating server groups, see [Explicitly Defining Servers](/zpa/explicitly-defining-servers) and [Configuring Server Groups](/zpa/configuring-server-groups).
- To learn more about enabling Dynamic Server Discovery, see [Enabling Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery).
- To learn more about configuring servers when adding a new application segment and defining your applications, see [Configuring Application Segments](/zpa/configuring-application-segments).
After configuration, you can view a list of configured servers and server groups on the Servers and Server Groups page, respectively, and make any necessary changes.
About the Servers Page
On the Servers page (Configuration & Control > Private Infrastructure > App Connector Management > Servers), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Servers page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new server** **and explicitly define it](/zpa/explicitly-defining-servers) to support one or more of your applications.
- [Expand all of the rows in the table](/zpa/using-tables#expand) to see more information about each server.
- View a list of all servers that were explicitly defined for your organization. For each server, you can see the following:
- **Name**: The server name.
- **Status**: Indicates that the server is enabled or disabled.
- **Domain or IP Address**: The fully qualified domain name (FQDN) or IP address of the server.
If a server is missing required settings, the yellow **Caution** icon (![Yellow Caution Icon ](/downloads/zpa/documentation-knowledgebase/servers/servers/about-servers/zpa-yellow-caution-icon.png)
) appears next to the name within the table. Edit the server to resolve the configuration issues.
- [Edit an existing server.](/zpa/editing-servers)
- Delete a server.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Server Groups](/zpa/about-server-groups) page to create server groups from servers you've defined previously, or to [enable Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) which allows ZPA to discover the appropriate servers for your applications as users request them as opposed to explicitly defining them.
![Viewing the Servers page ](/downloads/zpa/documentation-knowledgebase/servers/servers/about-servers/zpa-servers-page-2.png)