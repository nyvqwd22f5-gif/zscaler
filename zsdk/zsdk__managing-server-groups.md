# Managing Server Groups
Source: https://help.zscaler.com/zsdk/managing-server-groups
PDF: https://help.zscaler.com/pdf/com/en/1510101.pdf

When configuring an application segment, you must identify the server group that contains the servers hosting the defined applications.
There are two types of server groups that you can configure:
- You can create a server group and manually add servers that you've explicitly defined.
- You can create a server group with Dynamic Server Discovery enabled so that ZSDK discovers the appropriate servers for your applications as users request them. If you use this method, you do not need to manually define each server in the server group.
To manage server groups on the Server Groups page (Configuration & Control > Private Infrastructure > App Connector Management > Server Groups), you can:
- [Add a server group.](#add)
- [Edit a server group.](#edit)
- [Delete a server group.](#delete)
Dynamic Server Discovery
When you enable Dynamic Server Discovery on a server group, ZSDK discovers the appropriate servers for your applications as users request them. When configuring an application segment, the Servers tab disappears when you select a server group with Dynamic Server Discovery enabled.
Limitations & Considerations
When you configure server groups:
- You can add up to 1,000 server groups. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zsdk/ranges-limitations).
- If a server group is missing required settings, the **incomplete configuration** icon (![ZSDK-incompleteicon.png](/downloads/zsdk/application-management/managing-server-groups/ZSDK-incompleteicon.png)
) appears next to the name within the table. Edit the server group to resolve the configuration issues.
- When you configure server groups, Zscaler recommends grouping servers that are capable of hosting the same applications.
- You also have the option to configure a server group when [configuring a new application segment](/zsdk/defining-and-managing-application-segments) or when editing a server group in its associated [configuration graph](/zsdk/viewing-configuration-graphs).
[]
-
Click **Add Server Group**.
The **Add Server Group** window appears.
-
In the **Add Server Group** window:
- **Name**:** **Enter a name for the server group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- **Status**:** **Select the status of the Server Group. Default is **Enabled** to allow the server group to be configurable with an application segment and server.
- **Dynamic Server Discovery**: Select the Dynamic Server Discovery method that best suits your server needs.
- **Off**: Disable this option if you want to create a server group from servers that you've [explicitly defined](/zsdk/defining-and-managing-servers).
- **On**: Enable this option if you want ZSDK to discover the appropriate servers for your applications as users request them.
- **Servers**: This option appears if you select **Off** for **Dynamic Server Discovery**.
-
**Servers**: Choose the defined servers that you want to add to this server group, and click **Done**. You can search for a specific server or click **Clear Selection** to remove any selections.
When you configure server groups, Zscaler recommends grouping servers that are capable of hosting the same applications.
- **App Connector Groups**:** **Choose the App Connector groups that have access to the data center or virtual private cloud (VPC) that contains the servers in this server group, and click **Done**. You can search for a specific group or click **Clear Selection** to remove any selections.
[See image.](#img_add)
- Click **Save**.
You can also add a new server group when [adding a new application segment](/zsdk/defining-and-managing-application-segments).
[]
-
Click the **Edit** icon for a server group.
The **Edit Server Group** window appears.
-
In the **Edit Server Group** window:
- **Name**:** **Enter a name for the server group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description.
- **Status**:** **Select the status of the server group. Default is **Enabled** to allow the server group to be configurable with an application segment and server.
- **Dynamic Server Discovery**: Select the Dynamic Server Discovery method that best suits your server needs.
- **Off**: Disable this option if you want to create a server group from servers that you've [explicitly defined](/zsdk/defining-and-managing-servers).
- **On**: Enable this option if you want ZSDK to discover the appropriate servers for your applications as users request them.
- **Servers**: This option appears if you select **Off** for **Dynamic Server Discovery**.
-
**Servers**: Choose the defined servers that you want to add to this server group, and click **Done**. You can search for a specific server or click **Clear Selection** to remove any selections.
When you configure server groups, Zscaler recommends grouping servers that are capable of hosting the same applications.
- **App Connector Groups**:** **Choose the App Connector groups that have access to the data center or VPC that contains the servers in this server group, and click **Done**. You can search for a specific group or click **Clear Selection** to remove any selections.
[See image.](#img_edit)
- Click **Save**.
You can also edit the server group when [viewing its associated configuration graph](/zsdk/viewing-configuration-graphs).
[]
- Click the **Delete** icon on a server group.
- The **Confirm: Delete Action **window appears.
-
In the **Confirm: Delete Action** window, click **Delete** to confirm the deletion of the server.
[See image.](#img_delete)
[]
![Add Server Group](/downloads/zsdk/application-management/managing-server-groups/ZSDK-AddServerGroup-Servers.png)
[]
![Edit Server Group](/downloads/zsdk/application-management/managing-server-groups/ZSDK-EditServerGroup.png)
[]
![Delete Server Group](/downloads/zsdk/application-management/managing-server-groups/ZSDK-DeleteServerGroup.png)