# Zscaler Client Connector Processes to Allowlist
Source: https://help.zscaler.com/zscaler-client-connector/zscaler-client-connector-processes-allowlist
PDF: https://help.zscaler.com/pdf/com/en/1285511.pdf

Zscaler recommends that your users' devices have inbound rules that allow the Zscaler Client Connector binaries and processes.
For some endpoint protection products like anti-virus and personal firewalls, you might need to update additional allowlists for full Zscaler Client Connector functionality. This article covers processes and firewall rules that should be allowed.
Because Zscaler Client Connector modifies the networking component of the operating system, a Symantec Tamper Protection can trigger a false positive for the Zscaler service. While you can ignore this warning, you must update the allowlist for Symantec Tamper Protection.
Allowlist Processes
This section lists the file paths to allowlist for Zscaler Client Connector.
- [Windows](#windows-64-32-bit)
- [macOS](#macos-allowlist-rules)
- [Linux](#linux)
[]The location of files to allowlist depends on your version of Zscaler Client Connector.
If your organization uses [Group Policy Object (GPO)](/zscaler-client-connector/deploying-zscaler-client-connector-active-directory-windows#Create-Group-Policy) to push policies on both Windows 32-bit and Windows 64-bit systems, you must add the file paths of both versions to your GPO policy.
- [Zscaler Client Connector for Windows: 32-bit version](#windows32bit-allowlist-rules)
- [Zscaler Client Connector for Windows: 64-bit version](#windows64bit-allowlist-rules)
`%ProgramFiles(x86)%` and `%ProgramFiles%` are environmental variables that represent the drive where the Windows program files are located. Typically, program files are located on the C drive. However, there are exceptions. For example, on Amazon WorkSpaces, program files are on the D drive.
Allowlist the entire path of the following files:
These files reside in the `%ProgramFiles(x86)` folder even if you are running the 32-bit version of Zscaler Client Connector on a 64-bit system.
- []`%ProgramFiles(x86)%\Zscaler\ZSAHelper\ZSAHelper.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSATray\ZSATray.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSATrayManager\ZSATrayManager.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSATunnel\ZSATunnel.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSAService\ZSAService.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSAZDP`
- `%ProgramFiles(x86)%\Zscaler\ZSAUpdater\ZSAUpdater.exe`
- `%ProgramFiles(x86)%\Zscaler\ZSAUpm\ZSAUpm.exe`
- `%ProgramFiles(x86)%\Zscaler\Updater\zscalerappupdater.exe`
- `%ProgramFiles(x86)%\Zscaler\Updater\zscalerchecksumverifier.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\x86\Zscaler-Network-Adapter-1.0.1.0.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\x86\Zscaler-Network-Adapter-1.0.2.0.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\x86\Zscaler-Network-Adapter-Win10-1.0.2.0.exe`
- `%ProgramData%\Zscaler`
- `%WINDIR%\system32\`
- `%ProgramFiles%\Zscaler\ZDP\ZDPService.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPClassifier.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPApp.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPResources.exe`
If you are on a 64-bit device and install a 32-bit Zscaler Client Connector, the ZDPInstaller is installed in the 64-bit folder. If you are on a 32-bit device and install a 32-bit Zscaler Client Connector, the ZDPInstaller is not downloaded and installed.
- `%ProgramFiles%\Zscaler\ZDP`
- `%ProgramFiles%\Zscaler\ZEPInstaller`
- `%ProgramFiles(x86)%\Microsoft\EdgeWebView\Application\<``version number``>\msedgewebview2.exe`
[]Allowlist the entire path of the following files:
- `%ProgramFiles%\Zscaler\ZSAHelper\ZSAHelper.exe`
- `%ProgramFiles%\Zscaler\ZSATray\ZSATray.exe`
- `%ProgramFiles%\Zscaler\ZSATrayManager\ZSATrayManager.exe`
- `%ProgramFiles%\Zscaler\ZSATunnel\ZSATunnel.exe`
- `%ProgramFiles%\Zscaler\ZSAService\ZSAService.exe`
- `%ProgramFiles%\Zscaler\ZSAUpdater\ZSAUpdater.exe`
- `%ProgramFiles%\Zscaler\ZSAUpm\ZSAUpm.exe`
- `%ProgramFiles%\Zscaler\Updater\zscalerappupdater.exe`
- `%ProgramFiles%\Zscaler\Updater\zscalerchecksumverifier.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\TAPDriver\x64\Zscaler-Network-Adapter-1.0.1.0.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\TAPDriver\x64\Zscaler-Network-Adapter-1.0.2.0.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\TAPDriver\x64\Zscaler-Network-Adapter-Win10-1.0.2.0.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\ZSFFutil\x64\zsffutil.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\CertUtil\certutil.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\Filechecksum\fciv.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\Zscaler-Network-Adapter-1.0.1.0.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\Zscaler-Network-Adapter-1.0.2.0.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\TAPDriver\Zscaler-Network-Adapter-Win10-1.0.2.0.exe`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\ZSFFutil\zsffutil.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\WebView2\MicrosoftEdgeWebview2Setup.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\CertUtil\certutil.exe`
- `%ProgramFiles%\Zscaler\ThirdParty\Filechecksum\fciv.exe`
- `%ProgramData%\Zscaler`
- `%ProgramFiles%\Zscaler\ZDP`
- `%ProgramFiles%\Zscaler\ZDP\ZDPService.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPClassifier.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPApp.exe`
- `%ProgramFiles%\Zscaler\ZDP\ZDPResources.exe`
- `%ProgramFiles%\Zscaler\ZSAZDP`
- `%ProgramFiles%\Zscaler\ZEPInstaller`
- `%ProgramFiles(x86)%\Zscaler\ThirdParty\ZSFFutil\x86\zsffutil.exe`
- `%ProgramFiles(x86)%\Microsoft\EdgeWebView\Application\<``version number``>\msedgewebview2.exe`
Allowlist the entire path of the following files:
- []`/Applications/Zscaler/Zscaler.app/`
- `/Applications/Zscaler/.Updater/autoupdate-osx.app/Contents/MacOS/ZscalerUpdater`
This file is required only for Zscaler Client Connector version 3.7 and earlier for macOS.
- `/Library/Application Support/Zscaler/UPM/UPMServiceController`
- `com.zscaler.zscaler`
`com.zscaler.zscaler` is the Zscaler Client Connector identifier.
- `/Library/Application Support/Zscaler/ZDP`
[]Allowlist the entire path of the following files:
- `/opt/zscaler/bin/zsaservice`
- `/opt/zscaler/bin/zstunnel`
- `/opt/zscaler/bin/ZSTray`
- `/opt/zscaler/bin/zsupdater`
- `/opt/zscaler/ZSAUpm/bin/ZSAUpm`
Bypasses for Firewall
If you have a GPO-managed or AV-managed host firewall, you can configure firewall rules on your endpoint protection product for `ZSATunnel.exe` processes for all ports, protocols, network interfaces, and network addresses (e.g., 0.0.0.0/0).
Zscaler Client Connector also uses carrier-grade NAT range 100.64.0.0/16 as part of internal health checking and for the Zscaler Private Access (ZPA) service.
Zscaler can check IP addresses to avoid IP address conflict. For example, if you are using 100.64.0.0/16 and Zscaler sees a conflicting IP address, Zscaler changes it to 100.65.0.0/16. This change in the IP addresses can range from 100.64.0.0/16 to 100.83.0.0/16.
You can bypass the processes listed under the following platforms in your firewall rules:
- [Windows](#windows-bypasses-firewall)
- [macOS](#macos-bypasses-firewall)
- [Linux](#linux-bypasses-firewall)
- []`ZSATunnel.exe: Inbound`
- `ZSATunnel.exe: Outbound`
- `ZSATray.exe: Outbound`
- `ZSATrayManager.exe: Outbound`
- `ZSAUpdater.exe: Outbound`
- `ZSAService.exe: Outbound`
- `Zscalerappupdater.exe: Outbound`
- `ZDPService.exe: Outbound`
- `ZEPInstaller.exe: Outbound`
Zscaler Client Connector automatically adds required firewall rules to the Windows Defender Firewall. However, if the Local Policy Merge GPO setting is enabled, the rules are ignored and you must set up the firewall rules via the GPO. If you use Microsoft Defender Antivirus, you must configure any excluded paths and excluded processes from the allowlist as custom exclusions. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus).
- []`Zscaler: Inbound`
- `Zscaler: Outbound`
- `ZscalerService: Inbound`
- `ZscalerService: Outbound`
- `ZscalerTunnel: Inbound`
- `ZscalerTunnel: Outbound`
- `ZscalerUpdater: Outbound`
- `UPMServiceController: Inbound`
- `UPMServiceController: Outbound`
- `/Applications/Zscaler/.Updater/autoupdate-osx.app/Contents/MacOS/ZscalerUpdater: Inbound`
`/Applications/Zscaler/.Updater/autoupdate-osx.app/Contents/MacOS/ZscalerUpdater: Outbound`
- `/Library/Application Support/Zscaler/ZDP/bin/zdpd.app/Contents/MacOS/zdpd: Outbound`
If you are receiving a local FW/AV error after entering the rules, examine the `%windir%\system32\logfiles\firewall\pfirewall.log` to verify that there are no *drop* entries for 100.64 addresses. If you see *drop* entries, the Windows Firewall rules are not applied correctly to allow Zscaler to communicate. You must revise the rules based on the processes listed earlier.
[]Linux provides several firewall frameworks that operate primarily at the network level (IP, port, interface), each offering varying levels of abstraction and functionality. All these frameworks leverage the underlying Netfilter kernel infrastructure.
Here are the common firewall tools used across Linux distributions:
- **iptables**: A widely used tool for packet filtering and firewall management.
- **nftables**: A modern replacement for iptables, offering improved performance and flexibility.
- **firewalld**: A daemon that uses nftables or iptables as its backend, commonly used in RPM-based distributions.
- **ufw**: The Uncomplicated Firewall, a user-friendly tool commonly used in Ubuntu.
The Zscaler Client Connector for Linux relies on the iptables command-line tool to configure the necessary rules within Netfilter.
Firewall Hardening Guidelines for Linux Endpoints
The following example shows you how to harden your firewall for non-Zscaler traffic without affecting Zscaler Client Connector functionality. You must enter the commands in the terminal window in the specified order:
- Delete all rules: `sudo iptables -F`
Although optional, performing step 1 ensures the following steps work properly.
- Allow all outgoing connections: `sudo iptables -I OUTPUT -j ACCEPT`
- Allow loopback connections: `sudo iptables -A INPUT -i lo -j ACCEPT`
- Allow Zscaler Client Connector internal connections to the Zscaler Client Connector adapter: `sudo iptables -I INPUT -d 100.64.0.1 -j ACCEPT`
- Allow DHCP traffic:
- `sudo iptables -I INPUT -p udp --dport 68`
- `sudo iptables -I OUTPUT -p udp --dport 67`
- Allow SSH traffic (optional, comment out if not needed):
- `sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT`
- `sudo iptables -A OUTPUT -p tcp --sport ssh -j ACCEPT`
- Allow established and related incoming connections: `sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT`
- Deny everything else incoming: `sudo iptables -A INPUT -j DROP`
Processes Usage
The following list describes what each process is used for:
- **ZSAHelper**: An internal process used by other Zscaler Client Connector processes.
- **ZSATray**: The UI of the application.
- **ZSATrayManager**: Manages the tray process and checks signatures for communication between tray and system services.
- **ZSATunnel**: Handles traffic tunneling.
- **ZSAService**: The main service and the watchdog that looks after all other services.
- **ZSAUpdater**:** **The process that looks after automatic updates for the app.
- **ZSAUpm**: The Zscaler Digital Experience (ZDX) service.
- **zscalerappupdater**: The executable that initiates updates if found by the updater service.
- **zscalerchecksumverifier**: Ensures the update being launched is legitimate.
- **zsffutil**: Replaces certutil and file checksum used to validate crypto functions.
- **NetworkAdapter**: Various versions of the network adapter, used by Zscaler Client Connector when in Tunnel (Route-Based).
- **ProgramData\Zscaler**: Directory storing logs, PCAPs, and configuration for Zscaler Client Connector.
- **LogonUI**: Used for pre-Windows login in Zscaler Private Access (ZPA).
- **ZDPService.exe**: The data protection process that evaluates Data Loss Prevention (DLP) policy rules and determines the protection action to perform.
- **ZDPClassifier.exe**: The text extraction and classification process that identifies the true file type of a file and extracts the text from supported file types and then performs content classification.
- **ZDPApp.exe**: This process interacts with the end user to get user confirmation for specific activities.
- **ZEPInstaller.exe**: Prevents end users from stopping, modifying, and deleting Zscaler products and services.