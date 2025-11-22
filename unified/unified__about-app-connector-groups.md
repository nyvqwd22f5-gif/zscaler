# About App Connector Groups
Source: https://help.zscaler.com/unified/about-app-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1496056.pdf

Zscaler recommends deploying App Connectors in groups for high availability and horizontal scaling. You can create new App Connector groups whenever you [add a new App Connector](/unified/configuring-app-connectors) using a new provisioning key. Every App Connector belongs to a specific App Connector group, and every App Connector group should always be associated with at least one provisioning key and one Server group to serve any application. App Connector Groups must be associated with applications that the App Connector can access (i.e., only assign App Connectors to applications that the App Connector is capable of reaching). The closest App Connector is selected given the location of the user and the App Connector-to-application latency.
You do not need to create a new App Connector group every time you add an App Connector. If the App Connector group to which you want to add a new App Connector already exists, you can assign the App Connector to that group. To learn more, see [Configuring App Connectors](/unified/configuring-app-connectors).
App Connector groups provide the following benefits and enable you to:
- Deploy App Connectors in your tenant using provisioning keys.
- Group App Connectors per region or functional area; each App Connector must belong to a single group.
- Configure the automated update schedule to an off-hours maintenance window in a region.
- Configure the preferred local version profile for associated App Connectors and the App Connector’s location used in application path selection.
- Enable the necessary interface (IPv4, IPv6, or IPv4 and IPv6) using the DNS Resolution Option.
[]About the App Connector Groups Page
On the App Connector Groups page (Infrastructure > Private Access > Component > App Connector Groups), you can do the following:
- Select a Version Profile of the App Connector group. To learn more, see [Configuring a Version Profile](/unified/configuring-version-profile).
- View the App Connector groups as a table.
- View the App Connector groups in a map.
- Expand all of the rows in the table to see more information about each App Connector group.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all App Connector groups that are configured for your organization. For each App Connector group, you can see the following:
- **Name**: The name of the App Connector group.
- **Status**: Indicates whether the App Connector group is enabled or disabled.
- **Connectors**: List of deployed App Connectors that are included in the group.
- **Next Periodic Software Update**: The date and time of the next periodic software update for all of the App Connectors within the group.
If you accessed the App Connector Groups page from the [Log Receivers](/unified/about-log-streaming-service#AboutLogReceivers) page, then you only see groups with App Connectors that are set up for log streaming. The group also has a Log Streaming Service icon next to the name within the table.
[See image.](#image_logstream)
- See a graphical view for how the App Connector group connects to other configuration objects (e.g., Server groups, App Connectors, etc.).
You can edit any of the objects directly from the graphical view.
[See image.](#image_editobject)
- [Edit a configured App Connector group.](/unified/editing-app-connector-groups)
- Delete an App Connector group.
If an App Connector Group is configured using Zscaler Deception or is managed by Zscaler, then the edit and delete options are unavailable.
[See image.](#DeceptionAppConnectorGroup)
**![App Connector Groups page ](/downloads/unified/networking/private-applications/app-connector-management/app-connector-groups/about-app-connector-groups/about-app-connector-groups.png)
**
[]![App Connector Group with Log Streaming Service Icon](/downloads/zpa/documentation-knowledgebase/connectors/about-connectors-and-connector-groups/about-connectorgroups/ZPA-LSS-Icon.png)
[]![Edit object from Graphical View](/downloads/zpa/app-connector-management/app-connector-groups/about-connector-groups/zpa-segmentgroupspage-editingraphview.png)
[]![Deception App Connector Group](/downloads/zpa/app-connector-management/app-connector-groups/about-connector-groups/zpa-deception-integration-appConnectorGroups.png)