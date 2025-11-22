# Supporting FTP Applications
Source: https://help.zscaler.com/zpa/supporting-ftp-applications
PDF: https://help.zscaler.com/pdf/com/en/1483986.pdf

ZPA does not support active FTP mode; only passive mode is supported. Active FTP requires a TCP connection initiated from the server to the client, while passive FTP requires client-initiated TCP connections only. If an FTP client attempts active mode FTP, or sends an active mode request in parallel to the passive request, the attempt fails.
To support FTP applications in passive mode:
- Go to **Resource Management **> **Application Management** > **Application Segments** > **Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application** window, under **1. Define Applications**:
- For **Applications**:
- Enter an IP address. ZPA only supports IP-based passive FTP applications.
- For **Zscaler Client Connector Access**:
- **TCP Port Ranges**: Add all TCP ports (i.e., 1-65535).
- **Bypass**: Select **Use Client Forwarding Policy**. You need to [create a client forwarding policy](/zpa/configuring-application-segments#define-clientconnector) with the rule **Forward to ZPA**.
- For **Common Configuration**:
- **Health Reporting**: Select **None**. App Connector health reporting must be set to **None** because each FTP data channel is pseudo-random and opened on a per client basis.
[See image.](#BypassPassiveFTPApp)
[]![Add Application Segment window with Domain or IP address, Port Ranges, and Bypass When settings](/downloads/zpa/documentation-knowledgebase/application-management/enterprise-application-configurations/supporting-ftp-applications/Omission%20of%20Health%20Check.png)
- Complete the configuration for the new application as detailed in [Configuring Application Segments](/zpa/about-application/onboard).
Zscaler recommends that your users access a proper FTP client (i.e., FireFTP, FileZilla, CuteFTP, etc.). Command line FTP on Windows and macOS does not implement passive FTP correctly.