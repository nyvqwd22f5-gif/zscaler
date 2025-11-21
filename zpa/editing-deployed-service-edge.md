# Editing a Deployed ZPA Private Service Edge
Source: https://help.zscaler.com/zpa/editing-deployed-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1484486.pdf

To edit a deployed ZPA Private Service Edge:
- Go to **Configuration & Control** > **Private Infrastructure** > **Private Service Edge** **Management **> **Private Service Edges**.
-
In the table, locate the ZPA Private Service Edge you want to modify and click the **Edit **icon.
ZPA Private Service Edges that are managed by Zscaler are read only and cannot be edited.
The **Edit Private Service Edge** window appears.
- In the **Edit Private Service Edge** window, you can only modify the following fields:
- **Name**: The name of the ZPA Private Service Edge. When [provisioning a new ZPA Private Service Edge](/zpa/editing-deployed-service-edge), the provisioning key's name is automatically assigned as a prefix for the name of each ZPA Private Service Edge enrolled with it. Meaning that all ZPA Private Service Edges in a given ZPA Private Service Edge group use the same prefix in its name. To help distinguish between the different ZPA Private Service Edges in a group, each ZPA Private Service Edge also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth ZPA Private Service Edge to be enrolled with the key.
If you edit the ZPA Private Service Edge name, be sure to keep the prefix followed by the number that indicates that this is the nth ZPA Private Service Edge to have been deployed with its key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: The description for the ZPA Private Service Edge.
- **Status**: Enable or disable the ZPA Private Service Edge.
- **Publish IPs or Domains**: The IP addresses and domains that clients and App Connectors can use to open a connection to the ZPA Private Service Edge. If this is not specified, then the clients and App Connectors try to connect using the Listen IPs. The primary use case is where you want to specify a ZPA Private Service Edge by name and use a Domain Name System (DNS) to find it. Another use case is where the IP address that clients and App Connectors use to connect to the ZPA Private Service Edge isn't actually a part of the ZPA Private Service Edge; it is a static external IP address that the ZPA Private Service Edge system (e.g., AWS) controls.
You can add or remove IP addresses and domains when editing a ZPA Private Service Edge.
- **Automatically Publish IPv6**: Enable to automatically publish both IPv4 and IPv6 IP addresses if a Publish IP address or domain isn't configured. When enabled, Zscaler Client Connector can receive both IPv4 and IPv6 addresses. Disable to only publish IPv4 IP addresses. By default, this field is disabled.
If you want to use IPv6, make sure your ZPA Private Service Edges are set up for IPv6. To learn more, see [ZPA Private Service Edge Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites#PlatformPrereqs) and [Understanding IPv4 and IPv6 Support](/zpa/understanding-ipv4-and-ipv6-support).
- **Listen IPs**: The interface addresses for the Private Service Edge system that the ZPA Private Service Edge listens to for connection requests from clients and App Connectors only at set addresses. If not configured, the ZPA Private Service Edge automatically listens to all interfaces. The common use case is to not specify any Listen IPs.
You can add or remove IP addresses when editing a ZPA Private Service Edge.
[See image.](#image_editse)
- Click **Save**.
If you want to completely replace a [deployed ZPA Private Service Edge](/zpa/about-deploying-service-edges), you must delete the configuration and then re-enroll it. However, you can apply the new ZPA Private Service Edge provisioning key to the virtual machine (VM) image you already deployed by [replacing the old key](/zpa/managing-deployed-zpa-private-service-edges#ReplaceProvisioningKey).
[]![Edit Private Service Edge window](/downloads/zpa/private-service-edge-management/private-service-edge/editing-deployed-service-edge/Edit%20Private%20Service%20Edge%20window_1.png)