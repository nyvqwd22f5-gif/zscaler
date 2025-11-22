# Configuring Manual Location Groups
Source: https://help.zscaler.com/unified/configuring-manual-location-groups
PDF: https://help.zscaler.com/pdf/com/en/1495561.pdf

This article describes how to create a [manual location group](/unified/about-location-groups) and how to add your locations and sub-locations to a manual group. You can add up to 256 groups, this is inclusive of manual and dynamic location groups. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations#Locations).
Adding a Manual Location Group
To add a manual location group:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding** > **Location Management**.
- Click the **Location Groups** tab.
- Click **Add Manual Group**.
The **Add Manual Group** window appears.
-
In the **Add Manual Group** window, for **1. Group Information**:
- **Name**: Enter a name for the location group.
- **Description**: (Optional) Enter a description for the location group.
- **Extranet Location Type**: Select this if you want to create a group of extranet locations. To learn more, see [About Extranet](/unified/about-extranet).
- **Extranet Resource**: Select the extranet that has the locations you want to add to the group. After you select an extranet, you can only add locations to the group that are assigned to the extranet you selected.
[See image.](#AddLocGroup)
- Click **Next**.
-
For **2. Select Locations**:
Select the checkboxes for the locations or sublocations you want to assign to the manual group. You can assign a location to the group independently of its sublocations and a sublocation independently of its parent location. You can add up to 32K locations and sublocations to a group. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations#Locations).
[See image.](#addlocgroup2)
To narrow down the list of locations and sublocations, click the **Apply Filter **icon (![The Apply Filter icon](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-location-groups/show-hide-filter-icon.png)
). Click **Add Filter **and then select a location attribute from the drop-down menu. When you configure the attribute, the list automatically updates to show relevant locations and sublocations. You can add multiple attributes to narrow down the list even further. To remove a filter, click the **Remove icon** (![The Remove icon](/downloads/zia/documentation-knowledgebase/traffic-forwarding/locations/configuring-location-groups/remove-icon.png)
).
[See image.](#filter)
You can also search for specific locations or sub-locations by entering the name, group name, IP address, proxy port, VPN credential name, Internet & SaaS Virtual Service Edge name, or cluster name.
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
Editing or Deleting a Manual Location Group
[]To edit or delete a manual location group:
- Go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding** > **Location Management**.
- Click the **Location Groups** tab.
-
Locate the location group in the table and click **Edit**.
The **Edit Manual Group** window appears.
-
In the **Edit Manual Group** window, for **1. Group Information**, modify the **Name,** **Description **or **Extranet Location Type**. To update the list of locations or sublocations assigned to the group, click **Next**. If you want to remove the group, click **Delete**.
[See image.](#EditLocGroup)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
[]![Image of the Add Manual Group window](/downloads/zia/traffic-forwarding/location-management/configuring-manual-location-groups/ZIA-add-manual-location-group.png)
[]![Image of the Select Locations step in the Add Manual Group window](/downloads/zia/traffic-forwarding/location-management/configuring-manual-location-groups/ZIA-select-manual-group-locations.png)
[]![Image of the filter in the Add Manual Group window](/downloads/zia/traffic-forwarding/location-management/configuring-manual-location-groups/ZIA-filter-locations.png)
[]![Image of the Edit Manual Group window](/downloads/zia/traffic-forwarding/location-management/configuring-manual-location-groups/ZIA-edit-manual-location-group.png)