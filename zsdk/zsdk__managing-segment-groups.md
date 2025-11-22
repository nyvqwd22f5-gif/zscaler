# Managing Segment Groups
Source: https://help.zscaler.com/zsdk/managing-segment-groups
PDF: https://help.zscaler.com/pdf/com/en/1508926.pdf

You can add or modify a segment group while [configuring an application segment](/zsdk/defining-and-managing-application-segments), or you can create one on the Segment Groups page.
To manage segment groups on the **Segment Groups** page (Resource Management > Application Management > Segment Groups), you can:
- [Add a segment group.](#add)
- [Edit a segment group.](#edit)
- [Delete a segment group.](#delete)
After you create segment groups, you can create or assign existing access policies to them and the applications defined within them. To learn more, see [About Access Policy](/zsdk/about-access-policy) and [Managing Access Policies](/zsdk/managing-access-policies).
Limitations & Considerations
When configuring a segment group:
- If you have more than 500 application segments attached to a segment group, the Clear All button is hidden. If you have 500 or fewer application segments, the Clear All button is visible.
- You can add up to 100 segment groups. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations).
- If there are required fields missing, the **Incomplete Configuration** icon (![ZSDK-SegmentGroup-incompleteicon.png](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-SegmentGroup-incompleteicon.png)
) appears next to the missing item.
[]
-
Click **Add Segment Group**.
The **Add Segment Group** window appears.
-
In the **Add Segment Group** window:
- **Name**:** **Enter a name for the segment group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the segment group.
- **Status**:** **Set to **Enabled**. When the segment group is **Enabled**, it can be used for configuration.
- **Application Segments**:** **Choose one or more application segments that you want to add to this group. You can search for a specific application segment, click **Select All Displayed** to apply all application segments, or click **Clear All** to remove all selections. An application segment can only belong to one group.
[See image.](#IMG_add)
- Click **Save**.
[]
-
Locate the segment group that you want to revise by clicking the **Edit **icon.
The **Edit Segment Group** window appears.
-
In the **Edit Segment Group** window:
- **Name**:** **Edit the name for the segment group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Edit the description for the segment group.
- **Status**:** **Set to **Enabled**. When the segment group is **Enabled**, it can be used for configuration.
- **Application Segments**:** **Choose one or more application segments that you want to add to this group. You can search for a specific application segment, click **Select All Displayed** to apply all application segments, or click **Clear All** to remove all selections. An application segment can only belong to one group.
[See image.](#IMG_edit)
- Click **Save**.
[]
-
Locate the segment group that you want to delete by clicking the **Delete** icon.
The **Confirm: Delete Action **window appears.
-
Click **Delete** to confirm the deletion of the selected segment group.
[See image.](#IMG_delete)
[]
![Add Segment Group](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-AddSegmentGroup.png)
[]
![Edit Segment Group](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-EditSegmentGroup.png)
[]
![Confirm Deletion](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-DeleteSegmentGroup.png)