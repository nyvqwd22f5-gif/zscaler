# About Server Groups
Source: https://help.zscaler.com/zpa/about-server-groups
PDF: https://help.zscaler.com/pdf/com/en/1483581.pdf

When configuring an application segment within ZPA, you must identify the server group that contains the servers hosting the defined applications.
There are two types of server groups you can configure:
- You can create a server group and manually add servers you've explicitly defined.
- You can create a server group with Dynamic Server Discovery enabled so that ZPA discovers the appropriate servers for your applications as users request them. If you use this method, you do not need to manually define each server in the server group.
When you configure server groups, only group servers that are capable of hosting the same applications. To learn more, see [Configuring Server Groups](/zpa/configuring-server-groups).
You also have the option to configure server groups when [configuring a new application segment](/zpa/configuring-application-segments#tab3).
About the Server Groups Page
On the Server Groups page (Configuration & Control > Private Infrastructure > App Connector Management > Server Groups), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Server Groups page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new server group](/zpa/configuring-server-groups), then add servers you've [explicitly defined](/zpa/explicitly-defining-servers), or [enable Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) so that ZPA discovers the appropriate servers for your applications as users request them.
- [Expand all of the rows in the table](/zpa/using-tables#expand) to see more information about each server group.
-
View a list of all server groups that were defined for your organization. For each server group, you can see:
- **Name**: The server group name.
- **Status**: Indicates that the server group is enabled or disabled.
- **Dynamic Server Discovery**: Indicates that the server group has Dynamic Server Discovery enabled or disabled.
- **App Connector Groups**: The App Connector groups that have access to the data center or virtual private cloud (VPC) that contains the servers in this server group. Expand a server group in the table to see the names of the App Connector groups that are linked to the server group. To learn more, see [About App Connector Groups](/zpa/about-connector-groups).
If a server group is missing the required settings, then the yellow **Caution** icon (![Yellow Caution Icon ](/downloads/zpa/documentation-knowledgebase/servers/server-groups/about-server-groups/zpa-yellow-caution-icon.png)
) appears next to the name within the table. Edit the server group to resolve the configuration issues.
-
[View a configuration graph of connected objects.](/zpa/pselabel/viewing-configuration-graphs)
- [Edit an existing server group.](/zpa/editing-server-groups)
-
Delete a server group.
If a server group is configured using Zscaler Deception, then the edit and delete options are unavailable.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Servers](/zpa/about-servers) page to [explicitly define servers](/zpa/explicitly-defining-servers).
![Viewing the Server Groups page ](/downloads/zpa/documentation-knowledgebase/servers/server-groups/about-server-groups/zpa-server-groups-page4.png)