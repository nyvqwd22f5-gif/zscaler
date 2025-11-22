# Using Zscaler Diagnostics
Source: https://help.zscaler.com/zscaler-client-connector/using-zscaler-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1374426.pdf

This article details how to access Zscaler Diagnostics features that are available for use after IdP authentication. This is the same information as provided in [Troubleshooting Zscaler Client Connector](/zscaler-client-connector/troubleshooting-zscaler-client-connector), except users can access this information without being logged in to Zscaler Client Connector on a Windows or macOS device.
- [Windows](#windows)
- [macOS](#macOS)
[]This feature is available with Zscaler Client Connector version 3.2 or later for Windows.
The Windows Policy setting for **ZPA Machine Authentication** must be enabled so users can authenticate and start the machine tunnel.
To authenticate and start the machine tunnel from the Windows login screen:
- In the bottom-left corner of the screen, click **Zscaler Diagnostics**.
-
Click **Zscaler Options**.
[See image.](#windows-login)
- Based on your organization’s authentication mechanism, you are prompted to complete one of the following steps:
-
Enter the IdP credentials for Username and Password.
[See image.](#idp-credentials)
-
On a separate device (e.g., a mobile phone), enter the link that displays in a browser and then enter the passcode. You can scan the QR code to automatically go to the verification site.
[See image.](#oauth2.0-credentials)
After successful authentication, the **Tunnel Status** window displays current information about the machine tunnel, including the number of packets sent or received, and whether the tunnel is running on a trusted network. Users have the option to stop the machine tunnel by clicking **Turn Off**.
[See image.](#tunnel-status)
The following options are available in the **Diagnostics **menu:
- **Start Packet Capture**: If your organization's admin enabled packet captures, you can use this feature when reproducing an issue. To learn more, see [Using the Start Packet Capture Option](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture).
- **Restart Service**: You can restart the [machine tunnel](/zscaler-client-connector/about-machine-tunnels). Restarting does not impact security enforcement.
- **Report an Issue**: If your organization's admin enabled support access, you can use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support (your support admin also receives a copy of this ticket). To learn more, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector).
- **Include Packet Captures**: Select this option to include [packet capture](/zscaler-client-connector/enabling-packet-capture-zscaler-app#using-start-packet-capture) files when using the Report an Issue feature.
- **Clear Logs**: You can clear stored logs.
- **Update Policy**: You can manually refresh the [machine tunnel](/zscaler-client-connector/about-machine-tunnels) policy.
[See image.](#tunnel-diagnostics)
[]![Windows login screen](/downloads/z-app/end-user-guide/using-zscaler-diagnostics-windows/client-connector-windows-login.PNG)
[]![IdP authentication screen](/downloads/z-app/end-user-guide/using-zscaler-diagnostics-windows/client-connector-idp-auth2.png)
[]![OAuth 2.0 authentication screen](/downloads/zscaler-diagnostics-oauth2.0.png)
[]![Tunnel Status screen](/downloads/z-app/end-user-guide/using-zscaler-diagnostics-windows/client-connector-tunnel-status2.PNG)
[][]![Diagnostics options screen](/downloads/z-app/end-user-guide/using-zscaler-diagnostics-windows/client-connector-diagnostics-options2.PNG)
[]To start the machine tunnel from the macOS login screen, in the bottom-left corner of the screen, click the Zscaler icon. This machine tunnel icon is only visible when a device logs out or reboots. The icon is not visible when a user locks the screen.
[See image.](#macOS-login)
[]![zscaler icon](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-diagnostics-doc-55298/zscaler-machine-tunnel-macOS-zscaler-icon.png)
The **Tunnel Status** window displays current information about the machine tunnel, including the number of packets sent or received, and whether the tunnel is running on a trusted network.
[See image.](#macOS-tunnel-status)
[]![Tunnel status](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-diagnostics-doc-55298/zscaler-machine-tunnel-macOS-tunnel-status.png)
The following options are available in the **Diagnostics **menu:
- **Restart Service**: You can restart the [machine tunnel](/zscaler-client-connector/about-machine-tunnels). Restarting does not impact security enforcement.
- **Report an Issue**: If your organization's admin enabled support access, you can use this feature to report an issue. When you submit the form, depending on your organization's setup, Zscaler Client Connector can send an email to your organization's support admin or submit a ticket directly to Zscaler Support (your support admin also receives a copy of this ticket). To learn more, see [Reporting an Issue with Zscaler Client Connector](/zscaler-client-connector/reporting-issue-zscaler-client-connector).
- **Clear Logs**: You can clear stored logs.
- **Update Policy**: You can manually refresh the [machine tunnel](/zscaler-client-connector/about-machine-tunnels) policy.
[See image.](#macOS-diagnostics)
[]![Diagnostics](/downloads/tech-pubs-drafts/client-connector-draft-articles/using-zscaler-diagnostics-doc-55298/macOS-zscaler-machine-tunnel-diagnostics.png)