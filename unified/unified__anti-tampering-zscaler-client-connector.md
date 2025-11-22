# Anti-Tampering for Zscaler Client Connector
Source: https://help.zscaler.com/unified/anti-tampering-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1494471.pdf

Anti-tampering protection prevents non-admin end-users from stopping, modifying, and deleting Zscaler products and services, including Zscaler files and new registry keys. Admins can enable or disable anti-tampering in [Zscaler Client Connector App Profiles](/unified/configuring-zscaler-client-connector-app-profiles). End users can disable anti-tampering in the Troubleshooting section of the More window in the Zscaler Client Connector app.
Anti-tampering is supported only on Windows desktop operating systems. Anti-tampering is not supported on Windows Server operating systems.
Zscaler Anti-Tampering does not run in safe mode by design. Zscaler recommends disabling safe mode for all end-users and allowing safe mode access only to the administrator.
ZEP Installer
The anti-tampering framework is part of the ZEP module and is installed by the ZEPInstaller.exe. The ZEPInstaller.exe is a 32-bit program on a 32-bit OS and a 64-bit program on a 64-bit OS that is embedded as a resource inside the Zscaler Client Connector installer. For example, Zscaler-windows-4.0.60.9-installer.exe.
The Zscaler Client Connector installer unpacks the ZEPInstaller.exe to the local hard drive based on the Zscaler Client Connector installer platform:
- If Zscaler Client Connector is a 32-bit version installed on a 64-bit OS, the ZEP package is unpacked to /program files (x86)/Zscaler.
- If Zscaler Client Connector is 64-bit version installed on a 64-bit OS, the ZEP package is unpacked to /program files/Zscaler.
- If Zscaler Client Connector is 32-bit version installed on a 32-bit OS, the ZEP package is unpacked to /program files/Zscaler.
To enable anti-tampering using an install option, see [Customizing Zscaler Client Connector with Install Options for EXE](/unified/customizing-zscaler-client-connector-install-options-exe).