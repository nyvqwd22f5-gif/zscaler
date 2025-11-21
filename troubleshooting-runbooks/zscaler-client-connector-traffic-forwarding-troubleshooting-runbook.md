# Zscaler Client Connector Traffic Forwarding Troubleshooting Runbook
Source: https://help.zscaler.com/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook
PDF: https://help.zscaler.com/pdf/com/en/1532445.pdf

The Zscaler Client Connector Traffic Forwarding Troubleshooting Runbook is designed to assist customers in identifying and resolving common Zscaler Client Connector issues and errors. It serves as a guide to troubleshoot problems, minimize downtime, and restore connectivity independently. It outlines:
- Common Zscaler Client Connector error scenarios.
- Methods to identify the issue using application logs and the Zscaler Client Connector.
- Suggested resolutions for each error.
Make sure to collect Zscaler Client Connector logs. To learn more, see [Troubleshooting Zscaler Client Connector](/zscaler-client-connector/troubleshooting-zscaler-client-connector).
Common Zscaler Client Connector Errors and Troubleshooting Steps
The following sections describe common Zscaler Client Connector errors and troubleshooting steps.
[Captive Portal Error](#captive-portal)
[]
Issue
Occurs when Zscaler Client Connector detects a captive portal network (e.g., Wi-Fi at airports, hotels, or cafes). Zscaler Client Connector bypasses traffic during captive portal detection but might transition into an error state if the user does not accept or agree to captive terms within the timeout period.
[See image.](#captive-portal-error)
Symptoms
- The browser displays errors such as `The page cannot be displayed.`
- The Internet Security window displays `Captive Portal Detected` or `Captive Portal Error`.
Identification
In Zscaler Client Connector logs and packet captures, look for HTTP requests to `http://gateway.``<cloud>``.net:443/generate_204`. If HTTP status code 204 is not returned, it indicates captive portal detection.
Zscaler Client Connector Logs
Packet Capture with HTTP_204 (No Captive Portal Detected) response:
[See image.](#packet-capture)
Possible Causes
- Captive portal login page not being prompted.
- Network components blocking access to required Zscaler URLs (e.g., gateway.<cloudname>.net).
Suggestions for Resolution
- Verify captive portal login: Ensure the captive portal login page is accessible from the default or another browser.
- Check network configuration:
- Confirm DNS is properly configured and is not blocking traffic to gateway.<cloudname>.net.
- Ensure firewall or network security devices do not block captive portal detection traffic.
- Bypass third-party VPN configurations: If using a third-party VPN, allow access to gateway.<cloudname>.net and pac.<cloudname>.net.
- Review timeout settings: Increase captive portal timeout in Zscaler Client Connector settings if login pages take longer to load.
- Update Zscaler Client Connector: Ensure Zscaler Client Connector is running on the latest version to avoid outdated captive portal handling issues.
[Connection Error](#conn-error)
[]
Issue
Zscaler Client Connector shows a connection error when it fails to establish a connection to Zscaler Internet Access (ZIA) or Zscaler Private Access (ZPA) services due to unreachable Zscaler data centers.
[See image.](#connection-error)
Symptoms
- The Internet Security window displays `Connection Error` or the logs show `Server Down Error`.
- Intermittent or no internet access.
Identification
- Review Zscaler Client Connector logs for proxy auto-configuration (PAC) file parsing and connection attempts to gateway.<cloudname>.net.
- Keywords to search: `getSmeProxyState`, `Tunnel Forwarding Status`.
Zscaler Client Connector Logs
The following sections show examples of Zscaler Client Connector logs.
Zscaler Client Connector Tunnel 1.0
Zscaler Client Connector parses the PAC file and lists the primary and secondary data centers:
`PAC Parsing - ZSATunnel Log
2022-10-26 09:16:15.381843(+0530)[21532:19740] DBG getProxyForUrl: Pac parse called for url: https://gateway.zscaler.net, pacRequestType: 1
2022-10-26 09:16:15.381843(+0530)[21532:19740] DBG getProxyForUrl: Before pacparser_find_proxy
2022-10-26 09:16:15.387850(+0530)[21532:11756] DBG initPacParserSession: Pac parse success!
2022-10-26 09:16:15.389402(+0530)[21532:19740] DBG getProxyForUrl: After pacparser_find_proxy
2022-10-26 09:16:15.389402(+0530)[21532:19740] INF Saving default proxy string as: PROXY 165.225.120.17:80; PROXY 165.225.122.17:80; DIRECT
2022-10-26 09:16:15.389402(+0530)[21532:19740] DBG getProxyForUrl: Proxy: PROXY 165.225.120.17:80; PROXY 165.225.122.17:80; DIRECT Url: https://gateway.zscaler.net
2022-10-26 09:16:15.389402(+0530)[21532:19740] DBG getProxyForUrl: First Proxy: 165.225.120.17:80
2022-10-26 09:16:15.389402(+0530)[21532:19740] DBG getProxyForUrl: Second Proxy: 165.225.122.17:80
2022-10-26 09:16:15.389402(+0530)[21532:19740] INF getProxyForUrl: Pac proxy array index: 0 value: 165.225.120.17
2022-10-26 09:16:15.389402(+0530)[21532:19740] INF getProxyForUrl: Pac proxy array index: 2 value: 165.225.122.17
2022-10-26 09:16:15.389402(+0530)[21532:19740] INF getProxyForUrl: Pac proxy array index: 3 value: 80`
- In the packet capture, you can see a CONNECT request initiated for proxy IP with hostname `www.zscaler.com:80`.
[See image.](#connect-request)
- Zscaler Client Connector performs monitoring for primary proxy IP every 30 seconds.
[See image.](#primary-proxy-ip-monitoring)
- If the keepalives fail with all the data centers returned from the PAC file, Zscaler Client Connector goes into connection error state. You can search for keyword `getSmeProxyState` in ZSATunnel logs to review the state of the connection over time.
- Here, you'll see four statuses: TUNNEL_FORWARDING, CONNECTING, SERVER_DOWN_ERROR, LOCAL_PROXY_FORWARDING.
`	2022-10-26 10:23:39.781222(+0530)[21532:12724] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:TUNNEL_FORWARDING
2022-10-26 10:23:41.285379(+0530)[21532:12724] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:TUNNEL_FORWARDING
2022-10-26 10:23:42.794816(+0530)[21532:12724] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:SERVER_DOWN_ERROR
2022-10-26 10:23:44.311423(+0530)[21532:12724] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:TUNNEL_FORWARDING`
Zscaler Client Connector Tunnel 2.0
Zscaler Tunnel (Z-Tunnel) has a tunneling architecture that uses DTLS or TLS to send packets to the Zscaler service.
You can find SVPN VIP in [https://config.zscaler.com/zscaler.net/cenr](https://config.zscaler.com/zscaler.net/cenr), which encrypts and decrypts the Tunnel 2.0 connection.
Zscaler Client Connector uses two channels to communicate with proxy: a control channel and a data channel. The control channel is always on TLS protocol, and the data channel is according to the Tunnel 2.0 mode set on the forwarding profile selection **Primary Transport Selection**.
You can monitor the Tunnel 2.0 connection status by searching `getSmeProxyState `in Zscaler Client Connector ZSATunnel logs:
`2022-10-10 07:29:12.337086(+0200)[11528:10960] DBG ZApp Status: getCurrentNetworkType:TRUSTED getSmeProxyState:TUNNEL_FORWARDING T2State: [Tx:31109 Rx:29942 IP:10.254.120.171 SME:165.225.202.56 Protocol: DTLS Status:UP]
2022-10-10 07:30:00.316743(+0200)[11528:10960] DBG ZApp Status: getCurrentNetworkType:TRUSTED getSmeProxyState:CONNECTING T2State: [Tx:32680 Rx:33136 IP:10.254.120.171 SME:165.225.202.56 Protocol: DTLS Status: ZSCCM:TUNNEL_FORWARDING ZSDDC:CONNECTING]
2022-10-10 07:30:06.306006(+0200)[11528:10960] DBG ZApp Status: getCurrentNetworkType:TRUSTED getSmeProxyState:TUNNEL_FORWARDING T2State: [Tx:7588 Rx:156 IP:10.254.120.171 SME:165.225.202.56 Protocol: TLS Status:UP]`
Tunnel 2.0 connection falling back to Tunnel 1.0 is highlighted in the following way:
`getSmeProxyState:TUNNEL_FORWARDING T2State: [Tx:192461 Rx:101858 IP:10.254.120.171 SME:165.225.202.56 Protocol: DTLS Status:UP]
2022-10-10 07:15:19.181506(+0200)[11528:10960] DBG ZApp Status: getCurrentNetworkType:TRUSTED getSmeProxyState:CONNECTING T2State: [Tx:195652 Rx:102133 IP:10.254.120.171 SME:165.225.202.56 Protocol: DTLS Status: ZSCCM:CONNECTING ZSDDC:TUNNEL_FORWARDING]
2022-10-10 07:15:37.285816(+0200)[11528:11776] INF ZSCCM::ACTIVE::startConnection: Failure#:0 Exception:Timeout: connect timed out: 147.161.179.24:443
2022-10-10 07:15:37.301796(+0200)[11528:13708] INF ZST2M::ACTIVE::updateZiaConfig: Updating ZIA Configuration
2022-10-10 07:15:37.301796(+0200)[11528:13708] INF ZST2M::ACTIVE::updateZiaConfig: SME List is empty. Fallback to ZTunnel 1.0`
If any device intercepts SSL connections, it is highlighted with the following logs:
`2025-08-27 05:59:36.586355(+0200)[11104:15584] INF ZST2M::ZT2A::initialize: Data Channel establishment Failed.
2025-08-27 05:59:36.602083(+0200)[11104:13696] INF Auth::Lib::certificateErroCallback: Invalid certificate`
Key Steps Zscaler Client Connector Follows
- Zscaler Client Connector retrieves primary and secondary data center addresses from the PAC file and attempts to connect sequentially using the fallback mechanism (ports 80, 443, etc.).
- Logs show connection attempts results such as TUNNEL_FORWARDING or SERVER_DOWN_ERROR.
Possible Causes
- Network firewall or endpoint device blocking Zscaler IP ranges or specific ports.
- SSL interception or network proxy interfering with Zscaler communication.
- Incorrect PAC file configuration.
Suggestions for Resolution
- Verify proxy settings:
- Check PAC file URL (e.g., `http://pac.``<cloud_name>``.net/``<cloud_name>``.net/proxy.pac`) for accuracy. Ensure there are no syntax errors.
- Confirm connectivity to dynamic proxy settings or custom ports, if configured.
- Bypass inspection devices:
- Firewall or SSL interception devices should bypass Zscaler IP ranges to prevent connection failures.
- Allow traffic to `gateway.``<cloud_name>``.net` on all standard ports (80, 443).
- Host-level security validation:
- Ensure endpoint protection (like antivirus) or host firewall aren't restricting access to Zscaler service IP ranges, and all required processes are allowed.
- Disable antivirus, endpoint firewalls, or security settings temporarily on one device to test if they are interfering.
- Monitor log traffic: Inspect logs to ensure `getSmeProxyState` displays `TUNNEL_FORWARDING`. Look for persistent connection drops or state changes to `SERVER_DOWN_ERROR`.
- Fallback mechanism check:
- For Z-Tunnel 2.0, make sure there is no restriction on UDP traffic as Z-Tunnel 2.0 uses UDP protocol for DTLS communication.
- Switch the tunnel protocol to TLS and test if that helps improve the situation.
- Perform connectivity tests: Use `ping `or `traceroute` commands to test reachability of Zscaler IP and data center ranges.
- Update Zscaler Client Connector version: Upgrade Zscaler Client Connector to the latest version in case of persistent errors.
[Endpoint Firewall or Antivirus Error](#enpoint-firewall)
[]
Issue
Zscaler Client Connector detects host-level interference from firewall or antivirus applications, which restrict inter-process communication within Zscaler Client Connector or block health check activities required for the Zscaler Client Connector services to function properly.
[See image.](#interference-firewall-antivirus-applications)
Symptoms
- The Internet Security window shows `Endpoint FW/AV Error` or `FIREWALL_BLOCK_ERROR`.
- Logs mention `Firewall detected retries expired` or [WFP]: `Bad health`.
- Connectivity issues or dropped packets related to reserved Zscaler IP range (100.64.0.0/24).
Zscaler Client Connector Logs
Some ISPs tend to throttle DTLS traffic, which leads to Zscaler Client Connector responding with `SERVER_DOWN_ERROR` and `FIREWALL_BLOCK_ERROR` errors and is captured in the ZSATunnel logs. In such cases, it is advised to switch to TLS.
`2024-08-21 09:09:17.339101(+0200)[15260:23464] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:CONNECTING getZpnProxyState:TUNNEL_FORWARDING getZpnAuthState:AUTHENTICATED broker:165.225.207.250 protocol:TLS type:User Tunnel
2024-08-21 09:09:18.857850(+0200)[15260:23464] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:SERVER_DOWN_ERROR getZpnProxyState:TUNNEL_FORWARDING getZpnAuthState:AUTHENTICATED broker:165.225.207.250 protocol:TLS type:User Tunnel
2024-08-21 09:10:19.381451(+0200)[15260:23464] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:SERVER_DOWN_ERROR getZpnProxyState:TUNNEL_FORWARDING getZpnAuthState:AUTHENTICATED broker:165.225.207.250 protocol:TLS type:User Tunnel
2024-08-21 09:10:20.895838(+0200)[15260:23464] DBG ZApp Status: getCurrentNetworkType:NON_TRUSTED getSmeProxyState:FIREWALL_BLOCK_ERROR getZpnProxyState:FIREWALL_BLOCK_ERROR getZpnAuthState:AUTHENTICATED broker:165.225.207.250 protocol:TLS type:User Tunnel`
Zscaler Client Connector `CaptureLWF``<timestamp>``.pcap` can confirm if the communication is failing:
[See image.](#capturelwf-pcap-confirmation)
Suggestions for Resolution
- Verify Zscaler Client Connector processes for allowlisting:
- Ensure critical processes (ZSATunnel.exe, ZSATray.exe, ZSAService.exe, ZDPService.exe) are excluded from firewall and antivirus scanning and policy restrictions.
- To learn more, see [Processes Allowlist](/zscaler-client-connector/zscaler-client-connector-processes-allowlist).
- Validate Z-Tunnel 2.0 Transport
- Test switching to TLS transport protocol. Create a profile to use Z-Tunnel 2.0 with TLS transport.
- Ensure Zscaler Client Connector health check traffic is excluded from any third-party VPN IP range to route 100.64.0.0 IP range via physical interface.
- Open Windows PowerShell and run the `Find-NetRoute -RemoteIPAddress 100.64.0.6` command to ensure the traffic is connected via Wi-Fi or ethernet (InterfaceAlias field) and not to the VPN adapter.
[See image.](#find-netroute-remote-ip-address)
- Check OS firewall rules:
- Confirm Zscaler App Rule exists and is enabled for all profiles (i.e., domain, private, public).
- Disable antivirus, endpoint firewalls, or security settings temporarily on one device to test if they are interfering.
-
Remove any conflicting block rules overriding ZSATunnel configuration. By default, Zscaler Client Connector adds a rule for ZSATunnel.exe for allowing all ports and protocols for domain, private, and public network, respectively. Windows firewall works in a way that if there is an ANY block rule which would catch the Zscaler Client Connector traffic (even if it is LESS specific than the Zscaler Client Connector rule), the block rule takes precedence. If there is a rule which is blocking inbound connectivity to local port 9000 or port 80, Zscaler recommends that you remove or disable that rule.
[See image.](#allowed-apps-features)
-
You can validate the Firewall rule from the Zscaler Client Connector log `AppInfo.xml`.
`<FirewallInfo>
Command: C:\WINDOWS\system32\netsh advfirewall firewall show rule name = all
ExitCode: 0
Error: (none)
Rule Name: Zscaler App Rule
----------------------------------------------------------------------
Enabled: Yes
Direction: In
Profiles: Domain,Private,Public
Grouping: ZSATunnel Rule Group
LocalIP: Any
RemoteIP: Any
Protocol: Any
Edge traversal: No
Action: Allow`
-
Verify by running the following CLI command:
`C:\Users\Username>netsh advfirewall firewall show rule name = "Zscaler App Rule"
Rule Name: Zscaler App Rule
----------------------------------------------------------------------
Enabled: Yes
Direction: In
Profiles: Domain,Private,Public
Grouping: ZSATunnel Rule Group
LocalIP: Any
RemoteIP: Any
Protocol: Any
Edge traversal: No
Action: Allow
Ok.`
- Investigate third-party software conflicts:
- Disable third-party VPN clients (e.g., Cisco AnyConnect) and endpoint security tools temporarily to identify traffic conflicts.
- Review logs for interactions between Zscaler Client Connector and firewall and antivirus services.
- Route health check traffic correctly: Add specific routing rules to exclude health check traffic (100.64.0.0/24) from VPN adapters.
- Analyze firewall logs using packet capture:
- Use tools like Wireshark to analyze traffic flow and identify instances of blocked Zscaler Client Connector packets.
- Adjust firewall rules based on packet capture findings.
- Update Zscaler Client Connector version:
- Upgrade Zscaler Client Connector to the latest version in case of persistent errors.
- If persistent, uninstall and reinstall Zscaler Client Connector to correct misconfigurations.
[Network Error](#net-error)
[]
Issue
This error appears when Zscaler Client Connector is unable to connect to the Zscaler cloud due to connectivity issues.
[See image.](#unable-connect-zscaler-cloud)
Symptoms
- The Internet Security window shows `Network Connection Failed. -8`.
- Logs indicate DNS resolution failures, connection resets, SSL interception, or unreachable hosts.
Identification
- Logs show Zscaler Client Connector queries to critical URLs (e.g., mobile.zscaler.net, login.<cloud_name>.net, mobile.<cloud_name>.net). Zscaler Client Connector uses these hostnames for control communication and needs uninterrupted access to these destinations.
- Failed responses include `Host not found`, `Connection reset by peer`, `No route to host`, or `Timeout`.
Zscaler Client Connector Logs
The following errors are logged in ZSTray logs.
DNS Failures
`2022-06-24 08:31:42.667324 #NORMAL #ERROR : Error checking updates: {"error":-8,"errorMessage":"Host not found. mobile.zscloud.net","response":"","success":"false"}`
Connection Interrupted
`2022-06-21 13:57:57.271950 #NORMAL #ERROR : Error checking updates: {"error":-8,"errorMessage":"Connection reset by peer. ","response":"1.4.3.1","success":"false"}`
Missing Route
`2022-07-03 01:19:54.568124 #NORMAL #ERROR : Error checking updates: {"error":-8,"errorMessage":"Net Exception. No route to host","response":"","success":"false"}`
Network Unreachable
`2022-06-27 06:38:30.554731 #NORMAL #INFO : Keep Alive Response: {"error":-8,"errorMessage":"Net Exception. Network is unreachable","success":"false"}`
SSL Connection Intercepted
`2022-06-22 07:04:57.044662 #NORMAL #INFO : Keep Alive Response: {"error":-8,"errorMessage":"Certificate validation error. Unacceptable certificate from mobile.zscloud.net: application verification failure","success":"false"}
2019-07-28 06:31:51.707162 #NORMAL #DEBUG : Get Domain Response: {"error":-8,"errorMessage":"SSL Exception. error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed","success":"false"}`
Suggestions for Resolution
- Verify connectivity to Zscaler service URLs:
- Test reachability to mobile.zscaler.net, login.<cloud_name>.net, and mobile.<cloud_name>.net using ping, nslookup, or traceroute.
- Ensure outbound connections to ports (80, 443) are allowed by firewalls.
- Check DNS resolution:
- Run `nslookup` or `dig` commands to ensure correct DNS resolution for Zscaler URLs.
- Test alternate DNS servers to ensure proper configuration (e.g., Google DNS: 8.8.8.8).
- Perform test for all of these domains:
- `mobile.zscaler.net`
- `login.``<cloud_name>``.net`
- `mobile.``<cloud_name>``.net`
Ping:
[See image.](#ping)
NSLookup
[See image.](#nslookup)
If the DNS resolution is showing IPv6 IP address, test by disabling IPv6 on the network adapter to rule out any conflict with IPv6.
[See image.](#network-connections)
If the DNS resolution result is not in Zscaler hub IP range (https://config.zscaler.com/<cloud_name>/hubs), verify if there is any custom entries in the Windows *hosts *file (e.g., file location: "C:\Windows\System32\drivers\etc\hosts"). Add a prefix "#" to disable (comment out) the custom entries if required.
[See image.](#windows-hosts-file)
If the DNS resolution fails on the configured DNS servers (either internal DNS or public DNS), test with a different DNS server (e.g., Google DNS Server IP - 8.8.8.8 / 8.8.4.4) to rule out any possible issue with the DNS server.
- Assess network adapter connectivity: Confirm the active network adapter is configured correctly and avoid tethering or virtual adapters.
- Validate proxy or PAC file configuration: Ensure accurate PAC file syntax and reachable proxy nodes.
- Address device and application conflicts:
- Temporarily disable VPN clients or endpoint security tools to rule out conflicts.
- Allowlist Zscaler Client Connector processes and IP ranges in security tools.
- Bypass inspection devices: Proxy or SSL interception devices bypass Zscaler IP ranges to prevent connection failures.
[Driver Error](#drive-error)
[]
Issue
[See image.](#driver-error)
Zscaler Client Connector displays `Driver Error` in the Service Status section of the Internet Security window or Private Access window, indicating that required network drivers, such as the Lightweight Filter (LWF) driver, are either not installed or malfunctioning.
Symptoms
- The Service Status section displays `Driver Error`.
- Logs contain the following error messages:
`	ERR LWF: Unable to load driver!
ERR lwf: Initial driver check FAILED! LightWeightFilter not loaded!`
Zscaler Client Connector Logs
The following sections show the Zscaler Client Connector logs.
ZSATray Logs
`2024-12-25 11:03:24.728897(+0530)[1808:2276] ERR LWF: Unable to load driver!
2024-12-25 11:03:24.728897(+0530)[1808:2276] ERR lwf: Initial driver check FAILED! LightWeightFilter not loaded! ZApp moves to DRIVER ERROR!`
Setup API logs (setupapi.dev.log)
`!!! idb: Failed to create driver package object 'zapprd.inf_amd64_474f234a17a9844c' in DRIVERS database node. Error = 0x00000002
!!! idb: Failed to register driver package 'C:\WINDOWS\System32\DriverStore\FileRepository\zapprd.inf_amd64_474f234a17a9844c\ZAPPRD.inf'. Error = 0x00000002
...
!!! sto: Failed to import driver package into Driver Store. Error = 0x00000002
...
!!! inf: Failed to import driver package into driver store
!!! inf: Error 2: The system cannot find the file specified.`
Common Causes
- Driver cache corruption: Cached drivers in C:\Windows\System32\DriverStore are incomplete or corrupted.
- Registry entry missing: Relevant registry keys for Zscaler Client Connector driver services are missing.
- Endpoint protection blockages: Antivirus tools or tampering protection settings prevent driver installation.
- Driver store corruption: Windows Driver Store shows errors preventing the addition of drivers.
Suggestions for Resolution
- Repair app function:
- In Zscaler Client Connector, go to **More **> **Troubleshoot **> **Repair App**.
- Restart the device and validate if the driver error resolves.
- Disable conflicting antivirus:
- Disable tools like Carbon Black or CrowdStrike temporarily.
- Retry the driver installation process.
- Reinstall Zscaler Client Connector: Uninstall and reinstall Zscaler Client Connector with force driver re-installation using cli flag --reinstallDriver 1. To learn more, see [Customizing Zscaler Client Connector with Install Options for EXE](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe).
Additional Resources
To learn more about Zscaler Client Connector errors and how to troubleshoot them, see the following articles:
- [Zscaler Client Connector: Connection Status Errors](/client-connector/zscaler-client-connector-connection-status-errors)
- [Zscaler Client Connector Errors](/client-connector/zscaler-client-connector-errors)
- [Troubleshooting Zscaler Client Connector](/zscaler-client-connector/troubleshooting-zscaler-client-connector)
[]![Captive Portal Error](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/captive-portal-error.png)
[]![Packet Capture](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/packet-capture.png)
[]![Connection Error](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/zscaler-client-connector-connection-error.png)
[]![Connect Request](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/connect-request.png)
[]![Primary Proxy IP Monitoring](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/primary-proxy-IP-monitoring.png)
[]![Interference from Firewall or Antivirus Applications](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/interference-firewall-antivirus-applications.png)
[]![CaptureLWF* PCAP Confirmation](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/zscaler-client-connector-captureLWF-PCAP.png)
[]![Find NetRoute Remote IP Address](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/find-netroute-remote-ip-address.png)
[]![Allowed Apps and Features](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/allowed-apps-features.png)
[]![Network Error](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/unable-connect-zscaler-cloud.png)
[]![Ping](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/ping.png)
[]![NSLookup](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/nslookup.png)
[]![Network Connections](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/network-connections.png)
[]![Windows Hosts File](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/windows-hosts-file.png)
[]![Driver Error](/downloads/troubleshooting-runbooks/zscaler-client-connector-traffic-forwarding-troubleshooting-runbook/driver-error.png)