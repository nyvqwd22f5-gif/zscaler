# Editing Defined Application Segments
Source: https://help.zscaler.com/zpa/editing-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1483561.pdf

To edit an application segment:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- In the table, locate the application segment you want to modify and click the **Edit **icon.
- [](Optional) If you selected the **Show Recommendation Before Editing** checkbox on the [Defined Application Segments](/zpa/about-applications) page, then you will have the following additional steps. If you did not select this option, go to [Step 4](#Step4).
[See image.](#SRBEoption)
In the **Merge Recommended Application Segment with Defined Application Segment** window:
- [Step 1: Recommended Application Segment](#Step1)
- [Step 2: Selected Segment](#Step2)
- On the **Applications and Port Configuration** tab, modify fields as necessary. To learn more about each field, see [Configuring Application Segments](/zpa/configuring-application-segments).[]
![Incomplete configuration warning when editing an Application Segment](/downloads/zpa/documentation-knowledgebase/applications/application-segments/editing-application-segments/editappseg.png)
- Click **Next** to view the **General Information** tab, and modify any fields as necessary.
If you select multiple server groups when editing, only one server group should be saved. This is because multiple server groups mapped to the same application segment can cause the console to disconnect.
To learn more about each field, see [Configuring Application Segments](/zpa/configuring-application-segments).
If there are required fields missing, the incomplete configuration icon appears next to the missing item.
![Incomplete configuration warning when editing an Application Segment](/downloads/zpa/documentation-knowledgebase/applications/application-segments/editing-application-segments/zpa_EditApplicationSegment_ICWsgmntgrp.png)
- Click **Save**.
[]On the **Recommended Application Segment** tab, select the necessary application groups:
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all application groups that were configured for your organization. Click **Next** or **Previous** at the bottom of the table to view additional application groups. For each application group, you can see:
- **Name**: The name of the application segment.
- **Applications**: A list of up to three defined applications within the application segment.
- **Grouping Reason**: Describes why the applications within that application group were placed together.
- **Descriptions**: Details of why the applications within that grouping reason were placed together.
- **Confidence**: The measurement of accuracy that a recommended application matched the set requirements. The range is from 0–100, with higher numbers meaning a more accurate match, given the configured filters set in the [Application Segments Settings](/zpa/about-application-segments-settings) page.
[See image.](#Recappsegtab1)
[]![Edit Recommended Application Segment with Defined Application Segment window.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/editing-application-segments/edit-merge-defined-app-segment-with-recommended-app-segment-01.png)
- Select an application segment and click **Next**.
[]On the **Selected Segment** tab, select the necessary applications from the designated application group:
**Applications**
The following are listed for the application group that you selected in the previous step:
- **Name**: The name of the application segment.
- **Attack Surface Reduction**: The percentage reduction in the attack surface (i.e., percentage difference between potential users and recommended users).
[See image.](#attacksurface)
- **Potential Users**: The number of potential users for this application group due to the current open policies. Users who are not currently accessing this application group show as potential users if they are included in a policy set with that application group.
- **Recommended Users**: The suggested users for this recommended application segment.
- **Number of Transactions**: The total number of transactions.
- **Number of Defined Application Segments**: The total number of defined application segments linked to this recommended application group. Click the **Expand **icon to see the list of defined application segments. You can click each defined application segment in the list to view its details in the **Application Segment** window.
- **TCP Port Ranges**: The TCP port ranges being used to access applications.
- **UDP Port Ranges**: The UDP port ranges being used to access applications.
- **Grouping Reasons**: Describes why the applications within that application group were placed together.
- **Descriptions**: Details of why the applications within that grouping reason were placed together.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all applications assigned to the selected application group. Click **Next** or **Previous** at the bottom of the table to view additional applications. For each application, you can see:
- **Application**: The name of the application.
- **Defined Application Segment**: The defined application segment linked to that specific application.
- **Port and Protocol**: The protocol and the web server port used by the application.
- **Server_IP**: The web server IP address (e.g., 192.0.2.0).
- **Confidence**: The measurement of accuracy that a recommended application segment matched the set requirements. The range is from 0-100, with higher numbers meaning a more accurate match, given the configured filters set in the [Application Segments Settings](/zpa/about-application-segments-settings) page.
[See image.](#Recappsegtab2)
- Select Applications and click **Next**.
[]![Merge Defined Application Segment with Recommended Application Segment window.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/editing-application-segments/edit-merge-defined-app-segment-with-recommended-app-segment-03.png)
[![Show Recommendation Before Editing option](/downloads/zscaler-tech-pubs-style-guide/draft-articles/editing-defined-application-segments-draft/Editing%20Application%20Segments_1.png)
]
![Attack surface percentage reduction.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/editing-application-segments/attach-surface-reduction-graphic_02.png)
[]