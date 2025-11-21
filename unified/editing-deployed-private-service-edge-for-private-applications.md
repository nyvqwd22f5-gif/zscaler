# Editing a Deployed Private Service Edge for Private Applications
Source: https://help.zscaler.com/unified/editing-deployed-private-service-edge-for-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496531.pdf

To edit a deployed Private Service Edge for Private Applications:
- Go to the **Private Service Edges **page (Infrastructure > Private Applications > Components > Private Service Edges).
-
In the table, locate the Private Service Edge you want to modify and click the **Edit **icon.
Private Service Edges that are managed by Zscaler are read only and cannot be edited.
The **Edit Private Service Edge** window appears.
- In the **Edit Private Service Edge** window, you can only modify the following fields:
- **Name**: The name of the Private Service Edge. When provisioning a new Private Service Edge, the provisioning key's name is automatically assigned as a prefix for the name of each Private Service Edge enrolled with it. Meaning that all Private Service Edges in a given Private Service Edge group use the same prefix in its name. To help distinguish between the different Private Service Edges in a group, each Private Service Edge also has a number automatically added to its name upon being enrolled. This number signifies that it is the nth Private Service Edge to be enrolled with the key.
If you edit the Private Service Edge name, be sure to keep the prefix followed by the number that indicates that this is the nth Private Service Edge to have been deployed with its key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: The description for the Private Service Edge.
- **Status**: Enable or disable the Private Service Edge.
- **Publish IPs or Domains**: The IP addresses and domains that clients and App Connectors can use to open a connection to the Private Service Edge. If this is not specified, then the clients and App Connectors try to connect using the Listen IPs. The primary use case is where you want to specify a Private Service Edge by name and use a Domain Name System (DNS) to find it. Another use case is where the IP address that clients and App Connectors use to connect to the Private Service Edge isn't actually a part of the Private Service Edge; it is a static external IP address that the Private Service Edge system (e.g., AWS) controls.
You can add or remove IP addresses and domains when editing a Private Service Edge.
- **Automatically Publish IPv6**: Enable to automatically publish both IPv4 and IPv6 IP addresses if a Publish IP address or domain isn't configured. When enabled, Zscaler Client Connector can receive both IPv4 and IPv6 addresses. Disable to only publish IPv4 IP addresses. By default, this field is disabled.
If you want to use IPv6, make sure your Private Service Edges are set up for IPv6. To learn more, see [Private Service Edge Deployment Prerequisites](/unified/private-service-edge-deployment-prerequisites).
- **Listen IPs**: The interface addresses for the Private Service Edge system that the Private Service Edge listens to for connection requests from clients and App Connectors only at set addresses. If not configured, the Private Service Edge automatically listens to all interfaces. The common use case is to not specify any Listen IPs.
You can add or remove IP addresses when editing a Private Service Edge.
[See image.](#image_editse)
- Click **Save**.
[]![Edit Private Service Edge window](/downloads/zpa/private-service-edge-management/private-service-edge/editing-deployed-service-edge/Edit%20Private%20Service%20Edge%20window_0.png)