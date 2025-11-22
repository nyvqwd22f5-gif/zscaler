# Defining and Managing Servers
Source: https://help.zscaler.com/zsdk/defining-and-managing-servers
PDF: https://help.zscaler.com/pdf/com/en/1509991.pdf

Defining servers for your applications is required to map your applications to a server. After defining the server, you can associate the server with a server group. You can also view a list of configured servers and server groups on the Servers and Server Groups pages, respectively, and make any necessary changes.
There are two main methods of associating a server with a server group:
- Explicitly define servers and server groups: You can explicitly define every server that hosts one or more applications. For each server, you provide a name as well as an IP address or FQDN. Then, you can manually arrange those servers into server groups.
- Enable [Dynamic Server Discovery](/zsdk/managing-server-groups) on a server group: Instead of explicitly defining each server, you can enable Dynamic Server Discovery so that ZSDK can discover the appropriate servers for your applications as users request them. For this method, you must create an empty server group that has Dynamic Server Discovery enabled. To learn more, see [About Application Discovery](/zpa/about-application-discovery).
Choose the method that is best suited for your organization's needs.
To manage servers on the Servers page (Configuration & Control > Private Infrastructure > App Connector Management > Servers), you can:
- [Add a server.](#add)
- [Edit a server.](#edit)
- [Delete a server.](#delete)
Limitations & Considerations
When defining servers:
- You can define up to 10K servers. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations).
- If a server is missing any required settings, the **Incomplete Configuration** icon (![ZSDK-incompleteicon.png](/downloads/zsdk/application-management/managing-servers/ZSDK-incompleteicon.png)
) appears next to the name on the table. Edit the server to resolve the configuration issues.
[]You can add a server on the Servers page or when you [define an application segment](/zsdk/defining-and-managing-application-segments).
To add a server:
-
Click **Add Server**.
The **Add Server **window appears.
-
In the **Add Server** window:
- **Name**: Enter a name for the server. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Status**: Select whether to enable or disable the server. If you disable a server, it cannot be found.
- **Domain or IP Address**: Enter an FQDN or an IP address for the server.
- **Server Groups without DSD**: Select server groups that have Dynamic Server Discovery turned off. To learn more, see [Managing Server Groups](/zsdk/managing-server-groups).
[See image.](#img_add)
- Click **Save**.
[]
-
Click the **Edit** icon on a defined server.
The **Edit Server **window appears.
-
In the **Edit Server** window:
- **Name**: Enter a name for the server. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Status**: Select whether to enable or disable the server. If you disable a server, it cannot be found.
- **Domain or IP Address**: Enter an FQDN or an IP address for the server.
- **Server Groups without DSD**: Select server groups that have Dynamic Server Discovery turned off. To learn more, see [Managing Server Groups](/zsdk/managing-server-groups).
[See image.](#img_edit)
- Click **Save**.
[]
-
Click the **Delete** icon on a defined server.
The **Confirm: Delete Action **window appears.
-
In the **Confirm: Delete Action** window, click **Delete** to confirm the deletion of the server.
[See image.](#img_delete)
[]
![Add Server](/downloads/zsdk/application-management/managing-servers/ZSDK-AddServer.png)
[]
![Edit Server](/downloads/zsdk/application-management/managing-servers/ZSDK-EditServer.png)
[]
![Confirm Deletion](/downloads/zsdk/application-management/managing-servers/ZSDK-DeleteServer.png)