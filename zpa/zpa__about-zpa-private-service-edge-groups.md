# About ZPA Private Service Edge Groups
Source: https://help.zscaler.com/zpa/about-zpa-private-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1484471.pdf

Zscaler recommends deploying ZPA Private Service Edges in groups for high availability and horizontal scaling. You can create new ZPA Private Service Edge groups whenever you [add a new ZPA Private Service Edge](/zpa/configuring-service-edges) using a new provisioning key. Every ZPA Private Service Edge belongs to a specific ZPA Private Service Edge group.
You do not need to create a new ZPA Private Service Edge group every time you add a ZPA Private Service Edge. Instead, you can assign the ZPA Private Service Edge to a ZPA Private Service Edge group that already exists. To learn more, see [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges).
ZPA Private Service Edge groups provide the following benefits and enable you to:
- Deploy ZPA Private Service Edges in your tenant using provisioning keys.
- Group ZPA Private Service Edges based on region or functional area (each ZPA Private Service Edge must belong to a single group).
- Set the location for the ZPA Private Service Edges in the group.
- Configure and enable disaster recovery.
- Set the automated update schedule to an off-hours maintenance window in a region.
- Configure the preferred local version profile for associated ZPA Private Service Edges.
[]About the Private Service Edge Groups Page
On the Private Service Edge Groups page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edge Groups), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- View a table of all the ZPA Private Service Edge groups.
- View a map of all the ZPA Private Service Edge groups.
- Refresh the Private Service Edge page to reflect the most current information.
- Select a Version Profile of the ZPA Private Service Edge group. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Expand all of the rows in the table to see more information about each ZPA Private Service Edge group.
- View a list of all ZPA Private Service Edge groups that are configured for your organization. For each ZPA Private Service Edge group, you can see:
- **Name**: The name of the ZPA Private Service Edge group. Expand a ZPA Private Service Edge group in the table to see the following for that specific ZPA Private Service Edge group:
- **Persist Local Version Profile**: Indicates whether a Private Service Edge Group is enabled or disabled to persist the local Version Profile.
- **Location:** The location where the ZPA Private Service Edge group, which the ZPA Private Service Edge belongs to, is set up.
- **Location Coordinates:** The latitude and longitude of the ZPA Private Service Edge group location.
- **Publicly Accessible:** Choose if the ZPA Private Service Edge group with specific [trusted networks](/zscaler-client-connector/about-trusted-networks) mapping is also available publicly for all users outside of these trusted networks. It is important to ensure the ZPA Private Service Edge is reachable over a public IP address if you need remote users to be able to connect to it.
- **Client Connector Trusted Networks:** Your organization's [trusted networks](/zscaler-client-connector/about-trusted-networks) that are mapped to the ZPA Private Service Edge group. This is used to prioritize ZPA Private Service Edges matching the given [trusted network](/zscaler-client-connector/about-trusted-networks) when users connect from those trusted networks. To learn more, see [About Trusted Networks](/zscaler-client-connector/about-trusted-networks).
- **Alternative Cloud Domain**: The alternative cloud domain that can override the default cloud domain for the ZPA Private Service Edge Group it is assigned to.
- **Private Service Edge Provisioning Keys:** The key used to identify the ZPA Private Service Edge group to which a ZPA Private Service Edge must deploy.
- **Private Service Edges:** List of deployed ZPA Private Service Edges that are included in the group.
- **Description:** The description of the ZPA Private Service Edge group if available.
- **Disaster Recovery**: Indicates the ZPA Private Service Edge group is [enabled for disaster recovery](/zpa/understanding-disaster-recovery).
- **Public Service Edge Proximity Override**: Indicates whether to allow this ZPA Private Service Edge group within a specified distance from the user to be prioritized over a closer ZPA Public Service Edge.
- **Status**: Indicates whether the ZPA Private Service Edge group is enabled or disabled.
- **Version Profile**: Indicates the Version Profile of the ZPA Private Service Edge group.
- **Next Periodic Software Update**: The date and time of the next periodic software update for all of the ZPA Private Service Edges within the group.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- [Edit a configured ZPA Private Service Edge group](/zpa/editing-service-edge-groups).
-
Delete a ZPA Private Service Edge group.
ZPA Private Service Edge groups that are managed by Zscaler are read only and cannot be edited or deleted.
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Private Service Edges](/zpa/about-zpa-service-edges) page to add new ZPA Private Service Edges or manage existing ZPA Private Service Edges.
- Go to the [Private Service Edge Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys) page to manage your ZPA Private Service Edge provisioning keys.
![Private Service Edge Groups page in the ZPA Admin Portal](/downloads/zpa/private-service-edge-management/private-service-edge-groups/about-zpa-private-service-edge-groups/zpa-about-pse-groups-page-w-steps_0.png)