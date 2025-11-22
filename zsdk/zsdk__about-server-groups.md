# About Server Groups
Source: https://help.zscaler.com/zsdk/about-server-groups
PDF: https://help.zscaler.com/pdf/com/en/1510111.pdf

Server groups identify servers hosting defined applications. They connect to defined applications via application segments and then connect to users via App Connector groups, thereby allowing you to create access policies to the defined applications.
Server groups provide the following benefits and enable you to:
- Provide mapping of applications via application segments to defined applications on hosted servers.
- Dynamically discover servers for applications through DNS when an empty server group is defined with Dynamic Server Discovery enabled.
- Manage server groups to organize access to defined servers.
About the Server Groups Page
On the Server Groups page (Configuration & Control > Private Infrastructure > Server Groups), you can do the following:
- Expand one or all of the rows in the table to view the server group's description, connector type, App Connector groups, and servers. You can also [edit the App Connector groups](/zsdk/managing-app-connector-groups).
- [Add a new server group.](/zsdk/managing-server-groups)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all server groups defined for your organization. For each server group, you can see:
- **Name**: The server group name.
- **Status**: Whether the server group is enabled or disabled.
- **Dynamic Server Discovery**: Whether the server group has Dynamic Server Discovery enabled or disabled. To learn more, see [Managing Server Groups](/zsdk/managing-server-groups).
- **App Connector Groups**: The App Connector groups that have access to the data center or virtual private cloud that contains the servers in this server group. To learn more, see [About App Connector Groups](/zsdk/about-app-connector-groups).
-
[View a configuration graph of connected objects.](/zsdk/viewing-configuration-graphs)
- [Edit an existing server group](/zsdk/managing-server-groups).
- [Delete a server group.](/zsdk/managing-server-groups)
- Go to the [Servers](/zsdk/about-servers) page, where you can explicitly define servers.
![View the Server Groups page](/downloads/zsdk/applications/about-server-groups/ZSDK-About-Server-Groups-Expand-Overview-1_0.png)