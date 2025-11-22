# About Segment Groups
Source: https://help.zscaler.com/unified/about-segment-groups
PDF: https://help.zscaler.com/pdf/com/en/1492231.pdf

You must place each application segment you configure into a segment group. This allows you to configure user access policies based on segment groups. For example, if you have a set of defined applications that you want only users from the "Sales" department to access, you can create a segment group called "Sales Applications" and apply to it all sales-related applications. You can then create an access policy using that segment group.
However, you cannot assign an application segment to multiple segment groups. For example, if you place Salesforce in the "Sales Applications Group," you cannot add Salesforce to another group.
Segment groups provide the following benefits and enable you to:
- Logically group application segments together for easier management.
- Provide a layer of abstraction to simplify access policy configuration.
You can add or modify a segment group while [configuring an application segment](/unified/configuring-defined-application-segments#tab2) or you can do so [manually](/unified/configuring-defined-application-segments) at any time.
About the Segment Groups Page
On the Segment Groups page (Policies > Access Control > Private Applications > Segment Groups), you can:
- [View and add DNS search domains](/unified/adding-dns-search-domains).
- Expand all rows in the table to see more information about each segment group.
- [Add a new segment group](/unified/configuring-segment-groups).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all segment groups that were configured for your organization. For each segment group, you can see:
- **Name**: The segment group name.
- **Status**: Indicates that the segment group is enabled or disabled.
If a segment group is missing required settings, the incomplete configuration icon appears next to the name within the table. Edit the segment group to resolve the configuration issues.
- See a graphical view for how the segment group connects to other configuration objects (e.g., Application Segments, Server groups, etc.)
You can edit any of the objects directly from the graphical view.
[See image.](#image_editobject)
- [Edit an existing segment group](/unified/editing-segment-groups).
- Delete a segment group.
If a segment group is configured using Zscaler Deception, then the edit and delete options are unavailable.
[See image.](#DeceptionSegmentGroup)
- Migrate or delete an existing segment group policy.
![Using the Segment Groups page within the ZPA Admin Portal](/downloads/unified/policies/private-applications/access-control/segment-groups/about-segment-groups/about-segment-groups-page.png)
[]![Edit Segment Group from Graphical View](/downloads/zpa/documentation-knowledgebase/applications/segment-groups/about-segment-groups/zpa-segmentgroupspage-editingraphview.png)
[]![Deception segment group](/downloads/zpa/documentation-knowledgebase/applications/segment-groups/about-segment-groups/zpa-deception-integration-segmentGroups1.png)