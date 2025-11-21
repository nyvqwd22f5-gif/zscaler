# Firewall Insights Logs: Filters
Source: https://help.zscaler.com/zia/firewall-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1401001.pdf

Filters define the traffic information that you view in your Firewall Insight Logs. To learn more about logs, see [About Insights Logs](/zia/about-insights-logs).
Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. You can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Some filters support additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform string match, like **Threat Category** and others.
Some filter combinations that appear together in Insights Logs when applied, don't appear together in Insights. For example, the **Department** and **Location** filters appear together in Insights Logs when applied, but don't appear together in Insights.
Following are the Firewall Insights Log filters that you can select:
- **Action**: Use this filter to limit the data to specific firewall and IPS policy actions.
- **Allow**: Policy rule is set to allow the packets to pass through the firewall. This filter includes the traffic that might be blocked due to a web policy violation (as indicated in the Web Insights logs) after passing through the firewall module.
- **Allow due to insufficient app data**: While evaluating a Firewall Filtering policy rule containing a [Network Application](/zia/about-network-applications), the session terminates unexpectedly before the DPI determines the type of application (i.e., always before assessing the 13th packet and often between packets 2 and 6). The transaction is logged as "Allow due to insufficient app data". This also assumes that a higher-ranked firewall rule did not block the base level protocol, encryption, or high level protocol for the packets assessed before the session terminated. For the few packets that are allowed (likely more than 1 but less than 13) prior to determining the application, the policy reason is logged as "Allow due to insufficient app data".
- **Block/Drop**: Firewall policy rule is set to silently block packets that match the rule.
- **Block/ICMP**: Policy rule was set to drop all packets that match the rule and to send the client an ICMP error message of Type 3 (Destination Unreachable) and code 9 or 10 (network/host administratively prohibited).
- **Block/Reset**: Firewall policy rule is set to Block/Reset. For TCP traffic, the Zscaler service drops all packets that match the rule and sends the client a TCP reset. (A TCP packet with the "reset" (RST) flag is set to 1 in the TCPheader, indicating that the TCP connection must be instantly stopped.) For non-TCP traffic, same as Block/Drop.
- **IPS Drop**: IPS policy rule is set to silently block packets that match the rule.
- **IPS Reset**: IPS policy rule is set to Block/Reset. For TCP traffic, the Zscaler service drops all packets that match the rule and sends the client a TCP reset. (A TCP packet with the "reset" (RST) flag is set to 1 in the TCPheader, indicating that the TCP connection must be instantly stopped.) For non-TCP traffic, same as Block/Drop.
- **Dropped due to internal error**: This action is logged when the Firewall has received the user-side traffic but it fails to establish the internet-side connection, resulting in the traffic flow being dropped. This might occur when the Service Edge infrastructure is momentarily overused.
- **Bypassed due to missing config**: This action is logged when the ZIA Service Edge fails to establish a connection with the Zscaler Central Authority (CA), resulting in the traffic flow passing through Zscaler Firewall or DNS without policy application. This might occur when traffic flow from a specific user or location arrives at the Service Edge for the first time and a connection to the CA is required to apply policies.
- **Timed out while waiting for a config**: This action is logged when the ZIA Service Edge has established a connection with the CA but the requested configuration does not arrive from the CA within the expected time period (typically 5 seconds). This might occur when traffic flow from a specific user or location arrives at the Service Edge for the first time and a connection to the CA is established but there is no response from the CA within the expected time frame.
- **Application Segment**: Use this filter to view transactions associated with a specific [application segment](/zpa/about-applications).
- **Bypassed Session**: Use this filter to limit the data to traffic that has bypassed the Zscaler Client Connector.
- **Bypassed Session Event Time**: Use this filter to limit the data to traffic that has bypassed the Zscaler Client Connector within the specified time period.
- **Capture**: Use this filter to limit the data to view transactions that were captured into a PCAP file.
- **Client Destination IP**: Use this filter to limit the data about traffic associated with a specific client destination IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Client Destination Name**: For Advanced Firewall, use this filter to limit the data to traffic associated with a specific destination FQDN.
- **Client Destination Port**: Use this filter to limit the data to traffic associated with a specific client destination port.
- **Client Source IP**: Use this filter to limit the data about traffic associated with a specific client source IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Client Source Port**: Use this filter to limit the data to traffic associated with a specific client source port.
- **Client Tunnel IP**: Use this filter to limit the data to traffic associated with a specific client tunnel IP address.
- **Data Center**: Use this filter to limit the data to traffic associated with a specific data center.
- **Department**: Use this filter to limit the data to the traffic of a specific [department](/zia/about-departments). Use the Search function to find a specific department.
- **Dest Country**: Use this filter to limit the data to traffic associated with specific destination countries.
- **Device Hostname**: The hostname information from support devices. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device Model**: Use this filter to view transactions associated with a specific device model. Enter all or part of the device model in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Name**: Use this filter to view transactions associated with a specific device name. Enter all or part of the device name in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **Device OS Type**: Use this filter to view transactions associated with a specific device OS type. Enter all or part of the device OS type in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device OS Version**: Use this filter to view transactions associated with a specific device OS version. Enter all or part of the device OS version in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Device Owner**: Use this filter to view transactions associated with a specific device owner. Enter all or part of the device owner in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**. This filter is not available for admins with [device information obfuscation](/zia/obfuscating-device-information-admins) enabled.
- **DNAT Destination Name**: For Advanced Firewall, use this filter to limit the data to traffic associated with a specific NAT destination FQDN.
- **DNAT Rule Name**: Use this filter to limit the data to traffic associated with a specific [NAT Control](/zia/about-nat-control) rule. Choose the rules from the list.
- **Enrolled Device appversion**: Use this filter to view transactions associated with a specific enrolled device app version. Enter all or part of the enrolled device app version in the text field and an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **External Device ID**: Use this filter to view transactions associated with a specific external device ID. Enter all or part of the device model in the text field and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Flow Type**: Use this filter to limit the data to traffic by their flow type. Choose one of the following flow types:
- Direct
- Intranet
- Loopback
- Unclassified
- VPN
- VPN Tunnel
- ZIA
- ZPA
- **Forwarding Method**: Use this filter to limit the data to traffic associated with the type of forwarding method used. Choose from one of the following methods:
- Dedicated IP: Forwards the traffic to the destination server using the IP addresses dedicated to your tenant.
- Direct: Forwards the traffic directly to the destination server using the Zscaler service IP address.
- Geo IP: Forwards the traffic to the destination server with a source IP address mapped to the location of the originating request.
- Proxy Chaining: Forwards the traffic to a third-party proxy service.
- ZPA: Forwards the traffic to a Zscaler Private Access (ZPA) Connector through the Zscaler Private Access (ZPA) cloud.
- **Forwarding Rule**: Use this filter to limit the data to traffic associated with the type of forwarding rule used.
- **Gateway Destination IP**: Use this filter to limit the data to traffic associated with the gateway destination IP used.
- **Gateway Destination Port**: Use this filter to limit the data to traffic associated with the gateway destination port used.
- **Gateway Name**: Use this filter to limit the data to traffic associated with the gateway name used.
- **Inbound Bytes**: Use this filter to limit the data to packets sent from the server to the client that were within a specific size range. The corresponding column shows the total inbound bytes for aggregated sessions, which were limited to the selected filter range. Choose a predefined range or specify a custom range.
- **IPS Rule Name**: Use this filter to limit the data to specific rules in the IPS policy. Choose the rules from the list.
- **Location**: Use this filter to limit the data to a location's traffic. Choose a location from the list of internet gateway locations specified in the Locations page. The list includes Road Warrior, the default location for transactions that did not originate from a predefined location. This filter lists 200 results at a time. Use the Search function to find a specific location.
- **Location Group**: Use this filter to limit the data to a location group’s traffic. Choose a location group from the list. Use the Search function to find a specific location group.3
- **Location Type**: Use this filter to limit the data to a specific location type. The default option for this filter is **None**. The following location types appear under this filter:
- Corporate User Traffic Group
- Guest Wifi Group
- IoT Traffic Group
- Server Traffic Group
- Unassigned Locations
- Workload Traffic Group
- **NAT Action**: Use this filter to limit the data to specific NAT actions that were performed on the session.
- **Network Application**: Use this filter to limit the data to specific [network applications](/zia/about-network-applications). Choose the applications from the list.
- **Network Application Category**: Use this filter to limit the data to specific applications categories. Choose the applications from the list.
- **Network Service**: Use this filter to limit the data to specific [network services](/zia/about-network-services). Choose the network services from the list.
- **Outbound Bytes**: Use this filter to limit the data to packets that were received by the server within a specific size range. The corresponding column shows the total outbound bytes for aggregated sessions, which were limited to the selected filter range. Choose a predefined range or specify a custom range.
- **Rule Name**: Use this filter to limit the data to specific rules in the firewall policy. Choose the rules from the list.
- **Server Destination IP**: Use this filter to limit the data to traffic associated with a specific server destination IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Server Destination Port**: Use this filter to limit the data to traffic associated with a specific server destination IP port.
- **Server IP Category**: Use this filter to limit the data to traffic associated with a specific [URL category](/zia/about-url-categories).
- **Server Source IP**: Use this filter to limit the data to traffic associated with a specific server source IP address. Choose **Match **and enter an IP address, a range of IP addresses, or an IP address and netmask, as shown in the examples below the text box.
- **Server Source Port**: Use this filter to limit the data to traffic associated with a specific server source port.
- **Session Duration**: Use this filter to limit the data to traffic based on the session time.
- **Show Delayed Logs**: Use this filter to limit the data to traffic based on delayed logs.
- **Show Only Custom Signature Rules**: Use this filter to limit the data to traffic based on the custom IPS signature rules.
- **Source Country**: Use this filter to limit the data to traffic associated with specific source countries.
- **Advanced Threat Category**: Use this filter to limit the data to traffic associated with a specific threat category. [See a list of available advanced threat categories and a brief description.](#threat-cats)
- **Threat Name**: Use this filter to enter all or part of the threat name in the text field, and choose an operator such as: **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Not Null**, or **Is Null**.
- **Threat Severity**: Use this filter to view transactions associated with a specific threat severity. The default option for this filter is **None**. The following severities appear under this filter:
- Critical
- High
- Medium
- Low
- **Traffic Forwarding**: Use this filter to limit the data to traffic associated with a specific traffic forwarding mechanism. Choose from the following:
- GRE
- IPSec Tunnel
- Policy Based Forwarding (e.g., explicit system proxying, explicit PAC file redirection, or L2 redirection within a subnet)
- Zscaler Client Connector
- Zscaler Client Connector over GRE Tunnel
- Zscaler Client Connector over IPSEC Tunnel
- ZPA Microtunnels (M-Tunnels)
- **User**: Use this filter to limit the data to the traffic of specific [users](/zia/about-users). Choose the user names from the list.
- **Zscaler Client Connector Tunnel Version**: Use this filter to limit the data to traffic associated with the version of the Zscaler Client Connector Z-Tunnel.
- **ZIA Gateway Protocol**: Use this filter to limit the data to traffic associated with the gateway protocol.
- **ZIA Source IP**: Use this filter to limit the data to traffic associated with the source IP
- **ZIA Source Port**: Use this filter to limit the data to traffic associated with the source port.
[]
-
-
-
-
-
-
-
-
-
| **Threat Category** | **Description** |
| ------------------- | --------------- |
| Advanced Security | Threats not included in the other threat categories. |
| Adware/Spyware Sites | Adware or spyware displays malicious advertisements that can collect users' information without their knowledge. |
| Botnet Callback | Botnets are systems in which attackers have secretly installed their software. This software is designed to communicate periodically with a "command and control" center, and a master application instructs the infected computers to send spam, phishing email, or perform other malicious tasks. |
| Browser Exploit | Browser exploits are web browser vulnerabilities that can be exploited, including exploits for Internet Explorer and Adobe Flash. |
| Cross-site Scripting | Cross-site scripting (XSS) refers to vulnerabilities in web server applications that allow malicious users to inject their own code into the website. |
| Crypto Mining | Most organizations prefer to block crypto mining traffic prevent cryptojacking, malicious scripts or programs that secretly use the device to mine cryptocurrency. For example, JavaScript in a compromised website, banner, or ad can use the browser to mine cryptocurrency and harm the user's device. However, in some cases, blocking this traffic might cause certain sites that use crypto mining as a source of income to stop working. It might also interfere with legitimate attempts to use cryptocurrency for payments. |
| Denial of Service Attack | A Denial of Service attack is an attack where a computer or internet connection attempts to overload a system, network, or application. |
| Domain Generation Algorithm (DGA) Domains | This category refers to the domains that are suspected to be generated using domain generation algorithms (DGA). These algorithms are used in various malware families to periodically generate a large number of domain names that can be used by malware-infected devices to connect with command and control servers in order to circumvent the identification and shutting down of malicious domains. |
| Exploit | An exploit is an attack where known non-web (non-HTTP) vulnerabilities are exploited. |
| Malicious Content | Malicious content includes websites that attempt to download dangerous content to your browser when you visit them. Increasingly, this content is downloaded silently without the user's knowledge or awareness. Malicious sites include exploit kits, compromised websites, and malicious advertising. |
| Peer to peer | Peer to peer refers to internet resources that allow users to easily share files with each other. The danger is that users may illegally share copyrighted or protected content. |
| Phishing | Phishing sites are websites that mimic legitimate banking and financial sites (for example, Citibank.com, PayPal.com, and so on). Their purpose is to fool you into thinking you can safely submit bank account, password, and other personal information which criminals can use to steal your money. |
| Risky Behaviors | Includes IPS signatures that are considered risky but might have some legitimate usage (e.g., signatures for websockets-to-SSH detections as in the case of Chisel usage). Signatures in this threat category can cover a wide range of detections and might include legitimate traffic, as well. Therefore, organizations might want to exclude this threat category from being blocked for users by creating a higher order IPS rule with the Risky Behaviors threat category as a condition and the action set to Allow or Bypass IPS. |
| Suspected Spyware or Adware | Sites that display characteristics of spyware/adware sites |
| Suspicious Destinations | Suspicious destinations include the following URL categories:NudityPornographyAnonymizerFileHostSharewareDownloadWeb HostMiscellaneous or UnknownOther Miscellaneous |
| Unauthorized Communication | Unauthorized communications refer to IRC tunneling applications and "anonymizer" sites that are used to bypass firewalls and proxies. |
| WebSpam | Web spam includes web pages that pretend to contain useful information, to get higher ranking in search engine results or drive traffic to phishing, adware, or spyware distribution sites. |