# Locating Where Zscaler Client Connector is Installed on Your Device
Source: https://help.zscaler.com/zscaler-client-connector/locating-where-zscaler-client-connector-installed
PDF: https://help.zscaler.com/pdf/com/en/1363016.pdf

When Zscaler Client Connector is installed on users' devices, Zscaler creates specific folders on the devices based on the OS running on the system:
- [Windows](#locate-win)
- [macOS](#locate-macos)
- [Linux](#locate-linux)
[]When Zscaler Client Connector is installed on users' Windows devices, the following folders are installed.
- [Zscaler](#zscaler)
- [Zscaler-Network-Adapter](#z-network-adaptor)
The following Windows services also appear in **Computer Management (Local) **>** Services and Applications **>** Services**.
- ZSAService: This is a management service for Zscaler Client Connector.
- ZSATunnel: This is a packet handling service responsible for tunneling traffic to the Zscaler service.
- ZSAUpdater: This is the Zscaler Client Connector Update service.
[See image.](#z-windows-services)
[]![The Zscaler folder on a Windows device](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-windows/where-zscaler-app-installed-windows-devices/zscaler_folder_for_windows_screenshot.png)
[]![The Zscaler-Network-Adapter folder on the Windows device](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-windows/where-zscaler-app-installed-windows-devices/zscaler-network-adapter_folder_screenshot.png)
[]![The Windows services for the Zscaler Client Connector](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-windows/where-zscaler-app-installed-windows-devices/windows_services_screenshot.png)
[]When Zscaler Client Connector is installed on users' macOS devices, you can find the Zscaler folder in their list of applications.
![The Zscaler folder on a macOS device](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-app/zscaler-app-user-guide-macos/where-zscaler-app-installed-macos-devices/zscaler_folder_for_macos_screenshot.png)
[]When Zscaler Client Connector is installed on users' Linux devices, the /opt/zscaler directory is created.