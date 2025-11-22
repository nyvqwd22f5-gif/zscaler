# About App Connector Groups
Source: https://help.zscaler.com/zpa/about-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1483586.pdf

Zscaler recommends deploying App Connectors in groups for high availability and horizontal scaling. You can create new App Connector groups whenever you [add a new App Connector](/zpa/configuring-connectors) using a new provisioning key. Every App Connector belongs to a specific App Connector group, and every App Connector group should always be associated with at least one provisioning key and one Server group to serve any application. App Connector groups must be associated with applications that the App Connector can access (i.e., only assign App Connectors to applications that the App Connector is capable of reaching). ZPA selects the closest App Connector given the location of the user and the App Connector-to-application latency.
You do not need to create a new App Connector group every time you add an App Connector. If the App Connector group to which you want to add a new App Connector already exists, you can assign the App Connector to that group. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors).
App Connector groups provide the following benefits and enable you to:
- Deploy App Connectors in your tenant using provisioning keys.
- Group App Connectors per region or functional area; each App Connector must belong to a single group.
- Configure the automated update schedule to an off-hours maintenance window in a region.
- Configure the preferred local version profile for associated App Connectors and the App Connector’s location used in application path selection.
- Enable the necessary interface (IPv4, IPv6, or IPv4 and IPv6) using the DNS Resolution Option.
[]About the App Connector Groups Page
On the App Connector Groups page (Configuration & Control > Private Infrastructure > App Connector Management > App Connector Groups), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- View the App Connector groups as a table.
- View the App Connector groups in a map.
- Refresh the App Connector page to reflect the most current information.
- Select a Version Profile of the App Connector group. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- Expand all of the rows in the table to see more information about each App Connector group.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all App Connector groups that are configured for your organization. For each App Connector group, you can see:
- **Name**: The name of the App Connector group.
- **Status**: Indicates whether the App Connector group is enabled or disabled.
- **Version Profile**: The profile used to specify an App Connector build for the group.
- **Next Periodic Software Update**: The date and time of the next periodic software update for all of the App Connectors within the group.
If you accessed the App Connector Groups page from the [Log Receivers](/zpa/about-log-streaming#AboutLogReceivers) page, then you only see groups with App Connectors that are set up for log streaming. The group also has a Log Streaming Service icon next to the name within the table.
[See image.](#image_logstream)
- [Modify the columns displayed in the table.](/zpa/using-tables)
-
[View a configuration graph of connected objects.](/zpa/pselabel/viewing-configuration-graphs)
- [Edit a configured App Connector group.](/zpa/editing-connector-groups)
- Delete an App Connector group.
If an App Connector Group is configured using Zscaler Deception or is managed by Zscaler, then the edit and delete options are unavailable.
[See image.](#DeceptionAppConnectorGroup)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [App Connectors](/zpa/about-connectors) page to add new App Connectors or manage existing App Connectors.
- Go to the [App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys) page to manage your App Connector provisioning keys.
**![App Connector Groups page within the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connector-groups/about-connector-groups/zpa-about-app-connector-groups-page_1.png)
**
[]![App Connector Group with Log Streaming Service Icon](/downloads/zpa/documentation-knowledgebase/connectors/about-connectors-and-connector-groups/about-connectorgroups/ZPA-LSS-Icon.png)
[]![Deception App Connector Group](/downloads/zpa/app-connector-management/app-connector-groups/about-connector-groups/zpa-deception-integration-appConnectorGroups.png)