# Starting a New Diagnostics Session
Source: https://help.zscaler.com/zdx/starting-new-diagnostics-session
PDF: https://help.zscaler.com/pdf/com/en/1370101.pdf

To start a new Diagnostics session:
- Perform one of the following actions:
- In the ZDX Admin Portal, go to **Diagnostics** > **Start New Diagnostics Session**.
- On the **User Details** page, click the **Start New Diagnostics Session **button. This opens a new Start New Diagnostics Session window with the user name and device details prefilled.
- On the **User Overview** page, click the **Start New Diagnostics Session** button in the user's row. This opens a new Start New Diagnostics Session window with the user name prefilled.
-
On the **Diagnostics** page, copy an existing session using the **Copy** icon. This opens a new Start New Diagnostics Session window with all details of an existing session copied. All fields are editable. If the device has a session in progress or is no longer associated with the user, it is not copied.
The **Start New Diagnostics Session** window appears.
[See image.](#EmptyGeneralSettings)
- In the **Start New Diagnostics Session** window:
- **Name**: Enter a name for the session.
- **User**: Choose the user for this session from the drop-down menu.
-
**Device**: After selecting a user, choose the device for this session from the drop-down menu.
If the device has an ongoing troubleshooting session or there is a version incompatibility, the device appears grayed out in the menu. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
[See image.](#GeneralSettings)
-
**What would you like to run?** Choose among the selections:
Depending on which type of session you select, the minimum versions of Zscaler Client Connector and ZDX Module are required. To learn more, see [Supported Versions & Feature Compatibility](/zdx/supported-versions-feature-compatibility).
- Deep Tracing
- Bandwidth Testing
- Packet Capture Probing
- Hi-Fi Cloud Path
If there are no compatible devices for selection, then you cannot select Packet Capture Probing as an option.
You can select Packet Capture Probing as an add-on with Deep Tracing, Bandwidth Test, or Hi-Fi Cloud Path.
You cannot select Deep Tracing, Bandwidth Test, or Hi-Fi Cloud Path as an add-on to each other.
If you select Bandwidth Test, you cannot set a duration for the session. However, if you select both Packet Capture Probing and either Bandwidth Test, Deep Tracing, or Hi-Fi Cloud Path, you can set the duration to 5 minutes, 15 minutes, 30 minutes, or 60 minutes using the **Run Session For** option. Additionally, if you select only Packet Capture Probing, you can set the session duration to 5 minutes, 15 minutes, 30 minutes, 60 minutes, 24 hours, or 48 hours.
- Click **Next **to start configuring the session if you chose Deep Tracing, Packet Capture Probing, or Hi-Fi Cloud Path as an option. If you chose only Bandwidth Testing, proceed to the next step.
- [Deep Tracing](#DeepTracing)
- [Bandwidth Testing](#BandwidthTesting)
- [Packet Capture Probing](#PacketCaptureSettings)
- [Hi-Fi Cloud Path](#HiFiCloudPath)
- Click **Save** to create and start the session.
After you click **Save**, you see the session in the In Progress table on the Diagnostics page. As the session progresses, its status is updated and it eventually moves to the History table. You can view session results by clicking the **View** icon. To learn more, see [Viewing Diagnostics Session Results](/zdx/viewing-diagnostics-session-results).
[]You can start a Deep Tracing session to analyze issues that a user, device, or application is facing when connecting to the network.
You can configure the following:
- **Device Probing**: Enable or disable this option. When this option is enabled, device data is available. When this option is disabled, user device statistics are not collected and device data is unavailable.
-
**Application**: Choose the application for the session.
You can also choose **Add Special Application**. In this option, you can add a URL or a tenant URL to start a Deep Tracing session for an application without an existing probe.
The special application added here is not included as part of the sessions limit. To learn more, see [Ranges and Limitations](/zdx/ranges-limitations).
-
Depending on what application is chosen, you can see at least one of the following probes:
- **Web Probe**: Choose the configured Web probe for this application from the drop-down menu. Choose at least one probe: **Web **or **Cloud Path**.
-
**Cloud Path Probe**: Choose the configured Cloud Path probe for this application from the drop-down menu. When you add a Cloud Path probe, you can optionally enter thresholds for **Packet Loss** (in %) and **Latency** (in ms).
If you select a Cloud Path probe that has been configured to follow a Web probe, the Web probe is selected.
Network applications require only a single Cloud Path probe and do not require a Web probe. To learn more, see [About Applications](/zdx/about-applications) and [Monitoring the Applications Overview](/zdx/monitoring-applications-overview).
To learn more, see [About Probes](/zdx/about-probes).
[See image.](#DeviceProbeSettings)
[]You can start a bandwidth test to view network connectivity and latency, then proceed to the next step.
[See image.](#BandwidthTestSettings)
[]If you want to capture the Cloud Path network connectivity or latency details, you can start a Hi-Fi (High Fidelity) Cloud Path session where a Cloud Path run sends a high number of packets.
You can configure the following:
- **Packet Count**: Enter the number of probe packets to send per hop discovery that have the same TTL value between 20 and 300. The default is 300.
- **Protocol**: Select **ICMP**, **TCP**, or **UDP**. If you select **TCP** or **UDP**, enter your port number.
- **Interval (ms)**: Enter the time interval between probe packets with the same TTL. Probe packets of incremental TTL are paced evenly within this time interval. The number of iterations or cycles is defined by the configured Packet Count. The time interval must be within the range of 1000 to 3000.
- **Timeout (ms)**: Enter the time to wait for a response to a probe packet before considering loss. The timeout must be within the range of 1000 to 3000.
- **Destination**: Select **IP/FQDN** or **Zscaler Service Edge**.
- If you select **IP/FQDN**, enter the IP Address or FQDN.
- If you select **Zscaler Service Edge**, you can select **Force Reverse Cloud Path in Trusted Network**. This option allows you to force a reverse traceroute when a network device blocks the forward Cloud Path. Enable only if you cannot implement a different device configuration. Ideally, you should reconfigure the firewall or the device blocking the forward traceroute. If that isn't possible, this setting provides calculations for reverse latency from the Zscaler Internet Access (ZIA) Public Service Edge to the egress in the Cloud Path.
To learn more, see [Configuring a Probe](/zdx/configuring-probe)[.]
[See image.](#HiFiCloudPathSettings)
[]You can start a Packet Capture Probing to analyze and identify network performance issues that manage network traffic.
You can configure the following:
- **Packet Capture Filter**: Enter destination IP addresses and/or ports to filter Packet Captures (e.g., ip host 1.1.1 and port 80 or port 53).
- **Network Interface**: Choose a Network Interface. The default is All Interfaces.
- **Frame Size Limit:** Choose the frame size limit of the Packet Capture from 100 to 65,536 bytes. The default value is 1514 bytes.
- **Disk Space Limit: **(For ZDX version 4.5 and later) Select the storage space for the PCAP file from 100 MB, 200 MB, 500 MB, 1 GB, 2 GB, or 4 GB.
[See image.](#ConfigurePacketCaptureSettings)
[]
![Starting a Session](/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start%20New%20Diagnostics%20Session-4.png)
[]
![Fill in Required Information](/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start%20New%20Diagnostics%20Session-Configure-1.png)
[]
![Configure Device Probe Settings](/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start%20New%20Diagnostics%20Session-DeepTracing.png)
[]
![Bandwidth Test](/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start%20New%20Diagnostics%20Session-BandwidthTest-4.png)
[]
![Packet Capture](/downloads/tech-pubs-drafts/zdx-draft-articles/zdx-9467-doc-54040-starting-new-diagnostics-session/Start-New-Diagnostics.jpg)
[]
![Hi-Fi Cloud Path](/downloads/zdx/diagnostics/starting-new-diagnostics-session/ZDX-Start%20New%20Diagnostics%20Session-ConfigureHiFiCloudPath-1.png)