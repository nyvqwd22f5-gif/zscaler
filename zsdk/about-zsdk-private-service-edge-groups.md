# About ZSDK Private Service Edge Groups
Source: https://help.zscaler.com/zsdk/about-zsdk-private-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1524981.pdf

Deploying ZSDK Private Service Edges in groups allows for high availability and horizontal scaling. Create new Private Service Edge groups whenever you [add a new Private Service Edge](/zsdk/managing-zsdk-private-service-edges#add) by using a new provisioning key. Each Private Service Edge belongs to a specific Private Service Edge group.
Private Service Edge groups provide the following benefits and enable you to:
- Deploy Private Service Edges on your tenant using provisioning keys.
- Group Private Service Edges based on region or functional area.
- Set the location for the Private Service Edges in the group.
- Configure and enable disaster recovery.
- Set an automatic update schedule to an off-hours maintenance window for a region.
- Configure the preferred local version profile for associated Private Service Edges.
About the Private Service Edge Groups Page
On the Private Service Edge Groups page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Groups), you can do the following:
- Filter the information that appears in the table. By default, no filters are applied. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
Switch between the table and map view. The map view displays where Private Service Edge groups are located. By default, the table view is selected.
[See image.](#map)
- Refresh the page to reflect the most current information.
- Expand one row or all rows in the table to see details about each group.
- [View Private Service Edge group details.](#details)
- View a list of all Private Service Edge groups. For each group, you see:
- **Name**: The name of the Private Service Edge group.
- **Status**: Whether the Private Service Edge group is enabled or disabled.
- **Version Profile**: The version profile of the Private Service Edge group.
- **Next Periodic Software Update**: The date and time of the next periodic software update for all the Private Service Edges within the group.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- [Edit the Private Service Edge group.](/zsdk/managing-zsdk-private-service-edge-groups#edit)
- [Delete the Private Service Edge group.](/zsdk/managing-zsdk-private-service-edge-groups#delete)
- Configure the number of rows for the table.
- Move between pages of Private Service Edge groups.
- Go to one of the following pages:
- [Private Service Edges](/zsdk/about-zsdk-private-service-edges): Add new Private Service Edges or manage existing ones.
- [Private Service Edge Provisioning Keys](/zsdk/about-zsdk-private-service-edge-provisioning-keys): Manage Private Service Edge provisioning keys.
![View the Private Service Edge Groups page](/downloads/zsdk/private-service-edge/about-zsdk-private-service-edge-groups/zsdk-private-service-edge-groups-page-overview-1.png)
[]
- **Persist Local Version Profile**: Indicates whether a Private Service Edge group is enabled or disabled to persist the local version profile.
- **Location:** The location where the Private Service Edge group, which the Private Service Edge belongs to, is set up.
- **Location Coordinates:** The latitude and longitude of the Private Service Edge group location.
- **Publicly Accessible:** Indicates whether the Private Service Edge group with specific [trusted networks](/zscaler-client-connector/about-trusted-networks) mapping is also available publicly for all users outside these trusted networks. It is important to ensure the Private Service Edge is reachable over a public IP address if you need remote users to be able to connect to it.
- **Client Connector Trusted Networks:** Your organization's [trusted networks](/zscaler-client-connector/about-trusted-networks) that are mapped to the Private Service Edge group. Use this option to prioritize Private Service Edges matching the given trusted network when users connect from those trusted networks.
- **Private Service Edge Provisioning Keys:** The key used to identify the Private Service Edge group to which a Private Service Edge must deploy. You can click the **Copy** icon to copy the provisioning key.
- **Private Service Edges:** A list of deployed Private Service Edges that are included in the group. You can click a Private Service Edge to edit it.
- **Description:** The description of the Private Service Edge group.
- **Disaster Recovery**: Whether the Private Service Edge group is [enabled for disaster recovery](/zsdk/viewing-disaster-recovery).
[]
![Switch to the map view to see where your ZSDK Private Service Edge groups are](/downloads/zsdk/private-service-edge/about-zsdk-private-service-edge-groups/zsdk-private-service-edge-groups-map-view.png)