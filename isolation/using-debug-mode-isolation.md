# Using Debug Mode for Isolation
Source: https://help.zscaler.com/isolation/using-debug-mode-isolation
PDF: https://help.zscaler.com/pdf/com/en/1479256.pdf

Enabling Debug Mode for Users
Debug mode is a feature that admins can enable for users in their isolation profiles. To learn more, see [Creating Isolation Profiles for ZIA](/isolation/creating-zia-isolation-profile-isolation) and [Creating Isolation Profiles for ZPA](/isolation/creating-isolation-profiles-zpa).
When an issue occurs during an isolated session, users can start debug mode to troubleshoot the issue. This allows users to decipher whether the issue occurring is related to the isolated session itself, or something else with their web browsing. Native browsers allow you to troubleshoot in a few ways, usually with developer tools. An end user of Isolation, however, should never be able to see these details that are typically available in the native browser. Debug mode allows users to troubleshoot the issue without revealing confidential information.
Starting Debug Mode
- Enter an isolation session on your browser.
- From the **Isolation Menu**, select **Start debug mode**.
[See image.](#Start-session-debug-mode)
- A message appears asking you to confirm starting debug mode. Click **Start**.
[See image.](#Confirmation-message-start-debug)
- The web page reloads with the same URL and restarts the isolation session with debug mode activated. The **Debug Mode** icon appears in the lower right of your web page, next to the **Show Isolation Bar** icon. If you have multiple tabs open for one isolation session, only the selected tab enters debug mode. The other tabs in the existing session close automatically, and any information on those tabs is lost when the session restarts. If you open new tabs while in the restarted isolated session, the new tabs are automatically in debug mode.
[See image.](#Stop-Debug-Red-Icon)
- To stop debug mode, click the **Debug Mode** icon. You can also click **Stop debug mode** from the Isolation Menu.
[See image.](#Stop-debug-mode-Iso-menu)
- A message appears asking you to confirm ending debug mode. Click **Stop**. If you do not manually stop debug mode, it will deactivate after a timeout period of 10 minutes. If you end your isolation session while using debug mode, all data from the debugging is still captured. If you stop debug mode when there are multiple tabs open, the data from all tabs is captured.
[See image.](#Confirmation-message-Stop-debug-mode)
- After debug mode stops, a message appears confirming it has concluded. To return to the original isolated session without debug mode activated, click **Restore session**.
[See image.](#Restore-session)
- When debug mode ends, a ZIP file is automatically generated and downloaded to your device. The ZIP file is named in the format "debug_DDMMYY: TimeinUTC" and is encrypted by a password set by the admin. It includes data for:
- Console Logs: Information from the website(s) accessed by isolation.
- HTTP Archive format (HAR) Data: Information about the isolated session.
- Netlog Data: Information from the web browser used.
- Network Latency: Information from the Isolation network diagnostics tab. To learn more, see [Accessing Network Diagnostics in Isolation](/isolation/accessing-network-diagnostics-isolation).
- General Information: Information that pertains to Zscaler, such as:
- User ID
- Isolation profile name and ID
- Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA) tenant ID (including the cloud name)
- Isolation tenant ID
- Name space ID
- Isolation region and cluster information
- Expected cooperative transmission count (ECTX) received from ZIA
- Isolation browser egress IP address
- ZIA PAC file
- Modified PAC file (if applicable)
- Flow details (ZIA Flow/IdP Proxy Flow/ZPA Flow)
- Correlation IDs (endpoint session ID, pod ID, etc.)
[]![Start-session-debug-mode-button.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Start-session-debug-mode-button.png)
[]![Confirmation-message-start-debug.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Confirmation-message-start-debug.png)
[]![Stop-Debug-Red-Icon.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Stop-Debug-Red-Icon.png)
[]![Confirmation-message-Stop-debug-mode.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Confirmation-message-Stop-debug-mode.png)
[]![Restore-session.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Restore-session.png)
![Stop-Debug-Mode_Iso-Menu.png](/downloads/isolation/end-user-isolation-experience/using-session-debug-mode-isolation/Stop-Debug-Mode_Iso-Menu.png)
[]