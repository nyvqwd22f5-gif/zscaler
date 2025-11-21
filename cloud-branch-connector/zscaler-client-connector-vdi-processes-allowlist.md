# Zscaler Client Connector for VDI Processes to Allowlist
Source: https://help.zscaler.com/cloud-branch-connector/zscaler-client-connector-vdi-processes-allowlist
PDF: https://help.zscaler.com/pdf/com/en/1516321.pdf

Zscaler recommends that you allowlist Zscaler Client Connector for VDI processes that permit Virtual Desktop Infrastructure (VDI) binaries and processes. You can only allowlist in Windows. To learn more about Zscaler Client Connector for VDI, see [What Is Zscaler Client Connector for VDI?](/cloud-branch-connector/what-zscaler-client-connector-vdi)
Allowlist Processes
The file paths to allowlist for Zscaler Client Connector for VDI are:
- `%ProgramFiles%\ZCCVDI\ZCCVDIHelper.exe`
- `%ProgramFiles%\ZCCVDI\ZCCVDIService.exe`
- `%ProgramFiles%\ZCCVDI\ZCCVDIUI\ZCCVDIUI.exe`
- `%ProgramFiles%\ZCCVDI\ThirdParty\WebView2\MicrosoftEdgeWebview2Setup.exe`
- `%ProgramData%\ZCCVDI`
Bypasses for Firewall
If you have a firewall managed by group policy object (GPO), you can configure firewall rules on your endpoint protection product for `ZCCVDI.exe` processes for all ports, protocols, network interfaces, and network addresses (e.g., `0.0.0.0/0`).
- `ZCCVDIUI.exe: Outbound`
- `ZCCVDIService.exe: Outbound`
Processes Usage
The following list describes what each process is used for:
- **ZCCVDIHelper**: An internal process used by other Zscaler Client Connector for VDI processes.
- **ZCCVDIUI**: The user interface of the application.
- **ZCCVDIService**: The main service that manages all other internal services.
- **ProgramData\ZCCVDI**: The directory that stores logs and configuration for Zscaler Client Connector for VDI.