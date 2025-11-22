# About Location Groups
Source: https://help.zscaler.com/unified/about-location-groups
PDF: https://help.zscaler.com/pdf/com/en/1495556.pdf

If you have many locations and associated sub-locations within your organization, consider using location groups. You can create manual location groups or dynamic location groups:
- Manual Location Groups: When creating a manual location group, you can manually assign any number of locations or sub-locations to it.
- Dynamic Location Groups: When creating a dynamic location group, you select the location attributes that locations or sub-locations must match to be assigned to the group. A dynamic group automatically updates to include any matching locations or sub-locations.
A location or sub-location must match all of a dynamic group's location attributes, including when only some of a location's or sub-location's attributes match. For example, consider that you’ve created a dynamic location group with the following attributes: the location name starts with “NYC” and the **Enforce Bandwidth Control** setting is enabled. A location named “NYC Office 1” that has **Enforce Bandwidth Control** and **Enforce Firewall Control **enabled can be assigned this group.
The following conditions apply when configuring manual or dynamic location groups:
- A location can join a location group independently of its sub-locations, and a sub-location independently of its parent location.
- A location or sub-location can be a member of multiple manual and dynamic location groups.
- Location groups can be used to define the scope of a new or existing admin. You can also select location groups for use in policies and reporting (i.e., Insights, Dashboards, etc.).
About the Location Groups Page
[]On the Location Groups page (Infrastructure > Internet & SaaS > Traffic Forwarding > Location Management > Location Groups), you can do the following:
- [Add a manual location group](/unified/configuring-manual-location-groups).
- [Add a dynamic location group](/unified/configuring-dynamic-location-groups).
- Search for a location group by **Name**, **Description**, **Last Modified By**, **Group Type**, and **Locations**.
- View a list of all location groups that were configured for your organization. For location groups, you can see the following:
- **Name**: The name of the group. You can sort this column.
- **Type**: Shows if the group is a manual or dynamic location group.
- **Number of Locations and Sub-Locations**: The number of locations associated with the group. Clicking on the number displays the locations (and their sub-locations, if applicable) within the [Locations](/unified/about-locations) page. You can sort this column.
- **Last Modified By**: The last admin user to modify the group. You can sort this column.
- **Last Modified On**: The date and time the group was last modified.
- **Description**: The description of the group, if available.
- Edit a location group, including the ability to delete a group.
- [Modify the table and its columns](/unified/using-tables).
- Go to the [Locations](/unified/about-locations) page, to configure new locations and their sub-locations or manage existing locations.
- Go to the [Azure Virtual WAN Locations](/unified/configuring-azure-virtual-wan-locations) page, to view and manage your synced Microsoft Azure hub site locations. This tab is only displayed if you have a Microsoft Azure Virtual WAN integration with Zscaler. To learn more, see [About Partner Integrations](/unified/about-partner-integrations).
![Location Groups Page within the Admin Portal](/downloads/unified/networking/internet-saas/traffic-forwarding/location-management/about-location-groups/unified-location-groups-page.png)