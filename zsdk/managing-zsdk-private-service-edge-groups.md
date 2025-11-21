# Managing ZSDK Private Service Edge Groups
Source: https://help.zscaler.com/zsdk/managing-zsdk-private-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1525706.pdf

When Private Service Edges are created, you can add them to an existing ZSDK Private Service Edge group or create a new one. Private Service Edge groups allow you to organize Private Service Edges for high availability and horizontal scaling.
To manage your Private Service Edge groups, you can:
- [Create a new Private Service Edge group by adding a Private Service Edge.](/zsdk/managing-zsdk-private-service-edges#PrivateServiceEdgeGroup-Add)
- [Edit a Private Service Edge group.](#edit)
- [Delete a Private Service Edge group.](#delete)
Considerations & Limitations
When using Private Service Edge groups:
- You can have up to 100 Private Service Edge groups. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations#privateserviceedge).
- Private Service Edge groups require disaster recovery to be enabled to ensure business continuity.
- You do not need to create a new Private Service Edge group every time you add a Private Service Edge. Instead, you can [assign the Private Service Edge to an existing Private Service Edge group](/zsdk/managing-zsdk-private-service-edges#PrivateServiceEdgeGroup-Select).
- When Publicly Accessible is disabled without a trusted network, the IP address of the Private Service Edge is returned to the client for both on-premises and roaming users who are located closest to the Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this Private Service Edge, ensure that it is reachable over a public IP address.
[]
On the **Private Service Edge Groups** page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Groups):
-
Click the **Edit** icon on the Private Service Edge that you want to modify.
The **Edit Private Service Edge Group** window appears.
[See image.](#img_edit)
- You can modify the following fields:
- **Name**: Enter a name for the group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description of the group.
- **Status**: Select **Enabled** or **Disabled **to determine whether the Private Service Edge group can be associated with Private Service Edges.
- **Publicly Accessible**: Determines whether the Private Service Edge group's specific trusted network mapping is also available publicly for all users outside these trusted networks.
- **Enabled**: Zscaler recommends setting to **Enabled** to ensure the Private Service Edge is reachable over a public IP address if you need remote users to be able to connect to it.
-
**Disabled**: Zscaler recommends setting to **Disabled **if the Private Service Edge has a public IP address or a published IP address set to a public IP address of a Source Network Address Translation (SNAT) such as a firewall.
When you disable **Publicly Accessible** without a trusted network, the IP address of the Private Service Edge is returned to the client for both on-premises and roaming users who are located closest to the Private Service Edge. To mitigate connectivity issues for remote users who want to connect to this Private Service Edge, ensure that the Private Service Edge is reachable over a public IP address.
- **Client Connector Trusted Networks**: Your organization's [trusted networks](/zscaler-client-connector/about-trusted-networks) that are mapped to the Private Service Edge group. Use this option to prioritize Private Service Edges when users connect from those trusted networks.
- **Disaster Recovery**: Enable to designate the Private Service Edge for [disaster recovery](/zsdk/viewing-disaster-recovery). Private Service Edge groups that are designated for disaster recovery bypass the ZSDK cloud to ensure business continuity in the event of a disaster scenario.
- **Persist Local Version Profile**: Enable if the Private Service Edge group should persist the local version profile.
- **Version Profile**: Displays the current [version profile](/zpa/configuring-version-profile).
- **Private Service Edge Location**: Enter the location where the Private Service Edges in the group are set up. The map displays the location you've entered. After the location marker appears on the map, the **Latitude**, **Longitude**, and **Location Address** fields are then automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
- Click **Save**.
[]
![Edit the Private Service Edge Group](/downloads/zsdk/private-service-edge/maintaining-zsdk-private-service-edge-groups/zsdk-private-service-edge-groups-edit.png)
[]
On the **Private Service Edge Groups** page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Groups):
- Click the **Delete** icon.
- Select the checkbox.
- Click **Delete**.
![Delete the Private Service Edge group](/downloads/zsdk/private-service-edge/about-zsdk-private-service-edge-groups/zsdk-private-service-edge-groups-delete.png)