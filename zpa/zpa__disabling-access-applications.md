# Disabling Access to Applications
Source: https://help.zscaler.com/zpa/disabling-access-applications
PDF: https://help.zscaler.com/pdf/com/en/1483531.pdf

To disable access to an application which was explicitly defined or dynamically discovered:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- In the table, locate the application segment to which the application belongs and click the **Edit icon**.
- In the **Edit Application Segment** window, for **Status**, select **Disabled**.
![Edit Application Segment window with Status setting](/downloads/zpa/documentation-knowledgebase/applications/application-segments/disabling-access-applications/zpa-editapplication-disable_0.png)
- Click **Save**.
Users will not be able to access the applications within the application segment until it is re-enabled.