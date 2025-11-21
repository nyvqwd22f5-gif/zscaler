# Configuring Server Groups
Source: https://help.zscaler.com/zpa/configuring-server-groups
PDF: https://help.zscaler.com/pdf/com/en/1483576.pdf

Within the ZPA Admin Portal, you can add up to 1,000 server groups. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
You can also add a new server group when [adding a new application segment](/zpa/about-application/onboard#tab3).
To configure server groups:
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **Server Groups**.
- Click the **Server Groups** tab.
- Click **Add Server Group**.
- In the **Add Server Group** window:
- **Name**:** **Enter a name for the server group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- **Status**:** **Make sure that the server group is enabled.
-
**Dynamic Server Discovery**: Choose one of the following options:
- Select **Off** to disable this option if you want to create a server group from servers you've [explicitly defined](/zpa/about-server/new).
- Select **On **to enable this option if you want ZPA to discover the appropriate servers for your applications as users request them.
If you disable **Dynamic Server Discovery**, choose the individual servers you want to add to the server group, and click **Done**. You can search for a specific server, or click **Clear Selection** to remove any selections.
When you configure server groups, only group servers that are capable of hosting the same applications.
- **Connector Type:** Choose one of the following options:
-
Select **App Connector **to use a ZPA App Connector to connect to applications that are accessible via App Connectors.
Choose the **App Connector Groups** that are applicable to the server group, and click **Done**. You can search for a specific group, or click **Clear Selection** to remove any selections.
[See image.](#addservergroup)
-
Select **Extranet** to use ZPA to connect to an application at a partner site via extranet application support. To learn more, see [About Extranet](/zia/about-extranet).
Make sure that you set extranet options at the tenant level as Microtenants aren't supported.
- **Extranet Resource**: Choose the applicable extranet resource that was [configured in ZIA](/zia/configuring-extranet). You can choose only one partner per server group.
-
**Extranet Location Groups**: Choose a location group that was configured in ZIA. By default, a location group is created for each extranet resource that includes all locations, but location groups can also be manually created with a subset of locations in ZIA. If you want to select an extranet by location instead of the location group, choose a location from the **Extranet Locations** drop-down menu instead.
You can expand the location group to view all locations associated with that group. If you want to include all those locations, you do not need to select an option for **Extranet Locations**. If you want to select a subset of those locations, you can select those in **Extranet Locations**.
- **Extranet Locations**: Choose the locations that can reach the application via an IPSec tunnel.
[See image.](#addextranetserver)
- Click **Save**.
[]![Adding a new server group with an App Connector to Zscaler Private Access (ZPA)](/downloads/zpa/documentation-knowledgebase/servers/server-groups/configuring-server-groups/zpa-addservergroup.png)
[]![Adding a new server group with an Extranet Connector Type in Zscaler Private Access (ZPA)](/downloads/zpa/documentation-knowledgebase/servers/server-groups/configuring-server-groups/zpa-addservergroup-extranet.png)