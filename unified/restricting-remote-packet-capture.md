# Restricting Remote Packet Capture
Source: https://help.zscaler.com/zscaler-client-connector/restricting-remote-packet-capture
PDF: https://help.zscaler.com/pdf/com/en/1452876.pdf

Zscaler Client Connector uses the Npcap library to perform [packet capture](/zscaler-client-connector/enabling-packet-capture-zscaler-client-connector) for troubleshooting.
EnablingZscaler Digital Experience (ZDX) installs Npcap.
When users run Zscaler Client Connector with Npcap functionality enabled, they can make packet capture tools available in the user space, allowing non-administrators to perform packet capture. This could elevate a user's access during a packet capture session and allow them unauthorized access. You can limit packet capture to administrators only by enabling **Restrict Remote Packet Capture**.
If Npcap is already installed, Zscaler Client Connector uses the registry setting to restrict remote packet capture to administrators only.
To limit packet capture to administrators only:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, select** Client Connector Support**.
- Click the **User Privacy** tab.
- Enable **Restrict Remote Packet Capture**.
- Click **Save**.
![Restrict Remote Access](/downloads/z-app/configuring-policy-and-administration-settings/zscaler-app-support-settings/user-privacy/restricting-remote-packet-capture/Restrict%20Remote%20Capture_1400.png)