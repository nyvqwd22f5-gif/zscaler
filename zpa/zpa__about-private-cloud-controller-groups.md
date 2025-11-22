# About Private Cloud Controller Groups
Source: https://help.zscaler.com/zpa/about-private-cloud-controller-groups
PDF: https://help.zscaler.com/pdf/com/en/1507031.pdf

You can create new Private Cloud Controller groups whenever you add a new Private Cloud Controller using a new provisioning key. Every Private Cloud Controller belongs to a specific Private Cloud Controller group, and every Private Cloud Controller group must always be associated with at least one provisioning key to serve any application.
You do not need to create a new Private Cloud Controller group every time you add a Private Cloud Controller. If the Private Cloud Controller group to which you want to add a new Private Cloud Controller already exists, you can assign that Private Cloud Controller to that group. To learn more, see [Configuring Private Cloud Controllers](/zpa/configuring-private-cloud-controllers).
Private Cloud Controller groups provide the following benefits and enable you to:
- Deploy Private Cloud Controllers in your tenant using provisioning keys.
- Group Private Cloud Controllers per region or functional area; each Private Cloud Controller must belong to a single group.
- Configure the automated update schedule to an off-hours maintenance window in a region.
- Configure the preferred local version profile for associated Private Cloud Controllers and a Private Cloud Controller's location used in application path selection.
About the Private Cloud Controller Groups Page
On the Private Cloud Controller Groups page (Configuration & Control > Business Continuity > Business Continuity Management > Private Cloud Controller Groups), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters **to display the filters.
- View the Private Cloud Controller groups as a table.
- View the Private Cloud Controller groups on a map.
- Refresh the Private Cloud Controller Groups page to reflect the most current information.
- Select a [Version Profile](/zpa/configuring-version-profile) of the Private Cloud Controller group.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Expand all the rows in the table to see more information about each Private Cloud Controller group.
- View a list of all Private Cloud Controller groups that are configured for your organization. For each Private Cloud Controller group, you can see:
- **Name**: The name of the Private Cloud Controller group. Expand a Private Cloud Controller group in the table to see the following for that specific Private Cloud Controller group:
- **Persist Local Version Profile**: Indicates whether a Private Cloud Controller group is enabled or disabled to persist the local Version Profile.
- **Location**: The location where the Private Cloud Controller group, which the Private Cloud Controller belongs to, is set up.
- **Location Coordinates**: The latitude and longitude of the Private Cloud Controller group location.
- **Private Cloud Controllers**: The list of deployed Private Cloud Controllers that are included in the group.
- **Private Cloud Controller Provisioning Keys**: The key used to identify the Private Cloud Controller group to which a Private Cloud Controller must deploy.
- **Description**: The description of the Private Cloud Controller group.
- **Status**: Indicates whether the Private Cloud Controller group is enabled or disabled.
- **Version** **Profile**: The [Version Profile](/zpa/configuring-version-profile) of the Private Cloud Controller group (**Default**, **Previous Default**, **New Release**, **Custom**, **Zscaler Assigned**).
- **Next Periodic Software Update**: The date and time of the next periodic software update for all of the Private Cloud Controllers within the group.
- [Edit the configuration of the Private Cloud Controller group.](/zpa/editing-private-cloud-controller-groups)
-
Delete the Private Cloud Controller group.
Private Cloud Controller groups that are managed by Zscaler are read only and cannot be edited or deleted. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Private Cloud Controllers](/zpa/about-private-cloud-controllers) page to add new Private Cloud Controllers or manage existing Private Cloud Controllers.
- Go to the[ Private Cloud Controller Provisioning Keys](/zpa/about-private-cloud-controller-provisioning-keys) page to view and manage Private Cloud Controller provisioning keys.
- Go to the [Private Clouds](/zpa/about-private-clouds) page to add new Private Clouds or manage existing Private Clouds.
- Go to the [Settings](/zpa/configuring-business-continuity-settings) page to configure the Business Continuity settings.
![Viewing and Managing Private Cloud Controller Groups](/downloads/zpa/business-continuity-management/private-cloud-controller-groups/about-private-cloud-controller-groups/zpa-private-cloud-controller-groups.png)