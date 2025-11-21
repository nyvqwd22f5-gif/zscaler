# Enabling Dynamic Server Discovery
Source: https://help.zscaler.com/zpa/enabling-dynamic-server-discovery
PDF: https://help.zscaler.com/pdf/com/en/1483696.pdf

Instead of explicitly defining each server, you can allow ZPA to discover the appropriate servers for your applications as users request them. To learn more, see [About Application Discovery](/zpa/about-application-discovery). The procedure below covers how to complete this task in the Server Groups page, however, you also can complete this task when defining a new application. To learn more, see [Configuring Application Segments](/zpa/about-application/onboard).
To enable dynamic server discovery:
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **Server Groups**.
- Click on the **Server Groups** tab.
- Click **Add Server Group**.
The **Add Server Group** window appears.
- In the **Add Server Group** window:
- **Name**: Enter a name for the server group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- **Status**: Select whether to enable or disable the server group.
- **Dynamic Server Discovery**: Enable this option to allow ZPA to discover the appropriate servers for your applications as users request them. The **Servers** field disappears when you enable this option.
- **App Connector Groups**: Choose the App Connector groups that have access to the data center or virtual public cloud (VPC) that contains the servers in this server group, and click **Done**. You can search for a specific group or click **Clear Selection** to remove any selections.
![Add Server Group window with Dynamic Server Discovery enabled](/downloads/zpa/documentation-knowledgebase/servers/servers/how-do-i-enable-dynamic-server-discovery/zpa-newservergroup.png)
- Click **Save**.