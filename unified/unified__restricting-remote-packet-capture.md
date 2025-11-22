# Restricting Remote Packet Capture
Source: https://help.zscaler.com/unified/restricting-remote-packet-capture
PDF: https://help.zscaler.com/pdf/com/en/1496111.pdf

Zscaler Client Connector uses the Npcap library to perform [packet capture](/unified/enabling-packet-capture-zscaler-client-connector) for troubleshooting.
Enabling Digital Experience Monitoring installs Npcap.
When users run Zscaler Client Connector with Npcap functionality enabled, they can make packet capture tools available in the user space, allowing non-administrators to perform packet capture. This could elevate a user's access during a packet capture session and allow them unauthorized access. You can limit packet capture to administrators only by enabling **Restrict Remote Packet Capture**.
If Npcap is already installed, Zscaler Client Connector uses the registry setting to restrict remote packet capture to administrators only.
To limit packet capture to administrators only:
- In the Admin Portal, go to **Infrastructure > Connectors > Client > User Privacy**.
- On the **User Privacy** tab, enable **Restrict Remote Packet Capture**.
- Click **Save**.
![Restrict Remote Access](/downloads/client-connector-restrict-remote-pkg-capture.png)