# Configuring Dynamic Location Groups
Source: https://help.zscaler.com/unified/configuring-dynamic-location-groups
PDF: https://help.zscaler.com/pdf/com/en/1495566.pdf

This article describes how to create a [dynamic location group](/unified/about-location-groups) and configure location attributes that locations or sub-location must match to be assigned to the dynamic group. You can add up to 256 groups. This is inclusive of dynamic and manual location groups. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
By default, the following predefined dynamic location groups are available in the Location Groups tab and are view only:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
One of these predefined dynamic location groups is automatically populated in the Dynamic Location Groups field of the [Add Location](/unified/configuring-locations) or [Add Sub-Location](/unified/configuring-sub-locations) window based on the location type selection.
Adding a Dynamic Location Group
To add a dynamic location group:
- Go to **Infrastructure **>** Internet & SaaS** >** Traffic Forwarding **>** Location Management**.
- Click the **Location Groups** tab.
- Click **Add Dynamic Group**.
The **Add Dynamic Group **window appears.
- In the **Add Dynamic Group** window, for **1. Group Information**:
[See image.](#image-1)
- For **General**:
- **Name**: Enter a name for the location group
- **Description**: (Optional) Enter a description for the location group
- For **Group Conditions**:
Select the location attributes that locations or sub-locations must match to be assigned to this group. To configure the group conditions:
- Click **Add New Condition**.
- From the drop-down menu, select and configure the attribute. You can add any of the following attributes:
- **City/State/Province**: Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Starts With**), and then enter at least three letters of the name for a specific city, state, or province. Locations or sub-locations for the specified city, state, or province will be assigned to the group.
- **Country**: From the drop-down menu, select the countries. Locations or sub-locations for the specified countries will be assigned to the group.
- **Enable AUP**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Enable AUP** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
- **Enable Caution**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Enable Caution** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
- **Enforce Authentication**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Enforce Authentication** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
- **Enforce Bandwidth Control**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Enforce Bandwidth Control** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
- **Enforce Firewall Control**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Enforce Firewall Control** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
- **Location Type**: Select a location type from the drop-down menu. You can also search for any one of the following location types:
- **Corporate user traffic**
- **Guest Wi-Fi traffic**
- **IoT traffic**
- **Server traffic**
- **Extranet**
- **Extranet Resource**: All locations assigned to the extranet you select are added unless they are excluded by another condition.
- **Managed By**: Search for and select the SD-WAN partner name from the drop-down menu. Locations or sub-locations managed by the partner will be assigned to the group.
- **Name**: Select a Boolean operator from the drop-down menu (e.g., **Contains**, **Ends With**, **Equals**, **Starts With**), and then enter the name. Locations or sub-locations that have the specified name will be assigned to the group.
- **Use XFF from Client Request**: Enable or disable the switch. If enabled, locations or sub-locations that have the **Use XFF from Client Request** setting turned on will be assigned to the group. If disabled, locations or sub-locations that have the setting turned off will be assigned to the group.
Repeat these steps to add more than one attribute.
- Click **Next**. For **2. Preview Locations**:
[See image.](#image-2)
View the list of locations and sub-locations that match all of the group’s configured attributes. You can search for specific locations or sub-locations by entering a name, group name, IP address, proxy port, VPN credential name, Virtual Service Edge name, and cluster name.
A location or sub-location can still be assigned to a dynamic group when only some of the location's or sub-location's attributes match all of the group's configured attributes. For example, consider that you’ve created a dynamic group with the following attributes: the location name starts with “NYC” and the **Enforce Bandwidth Control** setting is enabled. A location named “NYC Office 1” that has** Enforce Bandwidth Control** and **Enforce Firewall Control **enabled can be assigned this group.
- Click **Save** and activate the change.
Once saved, the dynamic group will continue to automatically update to include any new matching locations or sub-locations.
Editing or Deleting a Dynamic Location Group
To edit or delete a dynamic location group:
- Go to **Infrastructure **>** Internet & SaaS** >** Traffic Forwarding **>** Location Management**.
- Click the **Location Groups** tab.
- Locate the location group in the table and click **Edit**.
The **Edit Dynamic Group** window appears.
- In the **Edit Dynamic Group **window, modify the **Name**,** Description**, or **Group Conditions**. If you want to remove the group, click **Delete**.
[See image.](#image-3)
- Click **Save** and activate the change.
[]![Adding a Dynamic Location Group for Zscaler Internet Access (ZIA)](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-dynamic-location-groups/add-dynamic-location-group-1-group-info.png)
[]![Previewing the locations and sub-locations for the dynamic group](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-dynamic-location-groups/add-dynamic-location-group-2-preview-locations.png)
[]![Editing a Dynamic Location Group for Zscaler Internet Access (ZIA)](/downloads/zia/traffic-forwarding/location-management/configuring-dynamic-location-groups/edit-dynamic-location-group.png)