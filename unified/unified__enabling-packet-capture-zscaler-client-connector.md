# Enabling Packet Capture for Zscaler Client Connector
Source: https://help.zscaler.com/unified/enabling-packet-capture-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1496011.pdf

The packet capture feature allows users to capture traffic specific to the Zscaler Client Connector app. When enabled, users can run a packet capture to generate packet capture files that are stored with Zscaler Client Connector logs.
The packet capture feature captures packets at the adapter level and captures all packets on all network adapters.
If you use Zscaler Client Connector for Windows with the [Packet Filter-Based driver](/unified/configuring-forwarding-profiles-zscaler-client-connector#windows-driver-selection), the feature also captures packets that pass through the filter driver. With the Packet Filter-Based driver, the Zscaler service handles traffic on the system at a low level while traditional packet capture tools (e.g., Wireshark) might not see all traffic for troubleshooting purposes.
Enabling packet capture automatically installs Npcap if it is not already installed.
Enabling the Start Packet Capture Option
To enable packet capture for Zscaler Client Connector:
- In the** **Admin Portal, go to** Infrastructure > Connectors > Client > User Privacy**.
-
On the **User Privacy **tab, select **Enable Local Packet Capture in Zscaler Client Connector **if it's not already enabled.
[See image.](#enable-local-packet-capture)
After enabling access to local packet capture, it can take up to two hours for this feature to appear in Zscaler Client Connector. Click **Update Policy **from the **More** window to manually refresh your policies.
-
To confirm that the packet capture feature is enabled, click **More** in the app and verify that the **Start Packet Capture **option appears in the Troubleshoot section.
[See image.](#start-packet-capture)
If you use Zscaler Client Connector version 4.8 and later for Windows, you can configure access to local packet capture on the [app profile](/unified/configuring-zscaler-client-connector-app-profiles#notification). Packet capture access that is enabled on the app profile overrides this setting.
[]![Client Connector Support User Privacy tab](/downloads/zscaler-client-connector/zscaler-client-connector-support-settings/user-privacy/enabling-packet-capture-zscaler-client-connector/zclient-connector-enable-local-packet-capture.png)
[]![Start packet capture from More window](/downloads/zscaler-client-connector/zscaler-client-connector-support-settings/user-privacy/enabling-packet-capture-zscaler-client-connector/zclient-connector-start-packet-capture-app.png)
Using the Start Packet Capture Option
[]
When reproducing an issue that requires packet capture:
- In Zscaler Client Connector, click **More**.
- In the **Troubleshoot** section, click **Start Packet Capture **and modify the following settings:
- **Run Session For**: Select the time limit you want to run the packet captures for. The default setting is 5 mins.
- **Disk Space Limit**: Select the storage space for the PCAP file. Each PCAP file is stored at half the size of the selected disk space limit and the oldest PCAP file is deleted. For example, if a limit of 500 MB is chosen, two PCAP files are created in sequence, each with a size of 250 MB. If the packet capture space limit exceeds 500 MB, the first (oldest) file is deleted. The default setting is 200MB.
- **Frame Size Limit**: Select the packet payload length. The default setting is 1514.
- **Filters**: Enter [filter text](https://www.tcpdump.org/manpages/pcap-filter.7.html) to filter the packets. If left empty, all packets are captured. If invalid text is entered, an error message is displayed. The filter options are based on the OS:
- **Packet Capture Filter**: Filter all packets. Applies to Zscaler Client Connector for macOS, Linux, and version 4.7 and earlier for Windows.
- **Adapter Packet Capture Filter**: Filter the packets that go through the device adapter. Applies to Zscaler Client Connector version 4.8 and later for Windows.
- **LWF Packet Capture Filter**: Filter the packets that go through the Lightweight Filter (LWF) driver. Applies to Zscaler Client Connector version 4.8 and later for Windows.
- Click **Start** to run the packet capture.
[See image.](#start-packet-capture-options)
[]![Start packet capture options](/downloads/tech-pubs-drafts/client-connector-draft-articles/enabling-packet-capture-zscaler-client-connector-doc-48621/ZSclientconnector-start-packet-capture.png)
- Reproduce the issue.
- Click **Stop Packet Capture** after you resolve the issue.
If the user forgets to stop the packet capture, it automatically stops after the time limit set in **Run Session For** has expired.
Duplicate packets are created in a packet capture to use for troubleshooting. The duplicate packets are not sent to the destination.
Packet Capture Files
Packet capture files are stored with Zscaler Client Connector logs in the following locations:
- **Windows**: `%ProgramData%\Zscaler\log-``<random numbers>`
`%ProgramFiles(x86)%` and `%ProgramFiles%` are macros that represent the drive where the Windows program files are located. Typically, program files are located on the C drive. However, there are exceptions (e.g., on Amazon WorkSpaces, program files are on the D drive).
- **macOS**: `/Library/Application Support/com.zscaler.Zscaler`
For ARM processor-based macOS devices, the path is `/Library/Application Support/Zscaler`.
- **Linux**: /var/log/zscaler/.Zscaler/Logs
Packet capture files have the prefix `CaptureAdapters` (Windows can also have the prefix `CaptureLWF`), followed by a timestamp and the file extension `.pcap`.
You can export packet capture files to a secondary location by browsing to the desired location when you export logs.
Examples of packet capture files:
CaptureAdapters_2020-07-28-17-13-49.822349.pcap
CaptureLWF_2020-07-28-17-13-49.822349.pcap
You might need to select the option to display hidden files to view the packet capture file.
Packet capture files are exported to the archive that is generated when using the **Export Logs** option from Zscaler Client Connector.
However, these files are not exported to the archive that is generated when using the **Report an Issue** option from Zscaler Client Connector. You must send the files to Zscaler Support for assessment.