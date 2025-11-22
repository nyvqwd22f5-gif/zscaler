# Configuring Segment Groups
Source: https://help.zscaler.com/unified/configuring-segment-groups
PDF: https://help.zscaler.com/pdf/com/en/1492236.pdf

Within the Admin Portal, you can add up to 100 segment groups. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations).
You can also add a new segment group when adding a new application segment. To learn more, see [Configuring Application Segments](/unified/configuring-defined-application-segments).
To configure a segment group:
- Go to the **Segment Groups **page (Policies > Access Control > Private Applications > Segment Groups).
- Click **Add Segment Group**.
The **Add Segment Group** window appears.
- In the **Add Segment Group** window:
- **Name**:** **Enter a name for the segment group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the segment group.
- **Status**:** **Make sure that the segment group is enabled.
- **Application Segments**:** **Choose one or more application segments you want to add to this group and click **Save**. You can search for a specific application segment, click **Select All Displayed** to apply all application segments, or click **Clear All** to remove all selections. An application segment can only belong to one group.
![Add Segment Group window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/segment-groups/configuring-segment-groups/AddAppSeg.png)
- Click **Save**.
After you can create a segment group, you can create access policies associated to them and the applications defined within them. To learn more, see [About Policies](/unified/about-policies) and [Configuring Access Policies](/unified/configuring-access-policies).