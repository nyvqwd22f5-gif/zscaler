# Supporting RDP Applications
Source: https://help.zscaler.com/zpa/supporting-rdp-applications
PDF: https://help.zscaler.com/pdf/com/en/1484306.pdf

To access applications via RDP in ZPA, Zscaler recommends that you use Zscaler Client Connector version 2.0.1 or later with the Windows Filter Driver enabled. To learn more, see [Using the Windows Filter Driver for the Zscaler Client Connector](/z-app/using-windows-filter-driver-zscaler-app).
To support RDP applications:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application** window, under **1. Define Applications**:
- For **Zscaler Client Connector Access**:
- **TCP Port Ranges**: Enter the TCP port ranges that can be used to access the defined applications.
- **UDP Port Ranges**: Leave this field empty.
Zscaler recommends that you only use TCP port ranges.
- Complete the configuration for the new application as detailed in [Configuring Application Segments](/zpa/koch/configuring-application-segments).
Zscaler recommends a dedicated App Connector Group for the File Server applications. These applications can be latency sensitive and may experience performance degradation if the associated App Connectors provide access to other applications as well.