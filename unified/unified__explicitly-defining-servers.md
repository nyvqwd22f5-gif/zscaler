# Explicitly Defining Servers
Source: https://help.zscaler.com/unified/explicitly-defining-servers
PDF: https://help.zscaler.com/pdf/com/en/1492256.pdf

The following information details how to explicitly define servers for your applications on the Servers page. However, you can also complete the steps below when defining a new application. To learn more, see [Configuring Application Segments](/unified/configuring-defined-application-segments).
Rather than explicitly define each server, you can [enable dynamic server discovery](/unified/enabling-dynamic-server-discovery) so that the appropriate servers for your applications can be discovered as users request them. To learn more, see [About Servers](/unified/about-servers).
You can add up to 10,000 servers. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
To explicitly define a server:
- Go to the **Servers** page (Policies > Access Control > Private Applications > Servers).
- Click **Add Server**.
The **Add Server** window appears.
- In the **Add Server** window:
- **Name**: Enter a name for the server. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Status**: Select whether to enable or disable the server.
- **Domain or IP Address**: Enter a fully qualified domain name (FQDN) or an IP address for the server.
- **Server Groups without DSD**: Select a server group(s). Only server groups that have Dynamic Server Discovery (DSD) turned off are displayed.
![Add Server page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/servers/servers/zpa-about-server-new/zpa-addserver.png)
- Click **Save**.
- After saving, you must add this server to a server group using one of the following options:
- Configure server groups on the Server Groups page. To learn more, see [Configuring Server Groups](/unified/configuring-server-groups).
- Configure server groups when defining a new application. To learn more, see [Configuring Application Segments](/unified/configuring-defined-application-segments).