# Configuring MITM Attack Detection
Source: https://help.zscaler.com/deception/configuring-mitm-attack-detection
PDF: https://help.zscaler.com/pdf/com/en/1531485.pdf

You can configure your [internal network decoys](/deception/creating-internal-network-decoy) to detect MITM attacks, such as Link-Local Multicast Name Resolution (LLMNR) poisoning, NetBIOS Name Service (NBT-NS) poisoning, and multicast DNS (mDNS) poisoning.
To configure MITM attack detection on your network decoys:
- Go to **Deceive **> **Man-in-the-Middle Attack Detection**.
-
In the **Man-in-the-Middle Attack Detection **window:
-
Choose the techniques for which network decoys should send decoy name resolution requests:
- **LLMNR**: Enable to detect LLMNR poisoning by broadcasting decoy name resolution requests using LLMNR protocol from network decoys. LLMNR protocol is used for name resolution of hosts in the same local link in Windows environments. Responders to LLMNR queries listen to UDP port 5355.
- **NBT-NS**: Enable to detect NBT-NS poisoning by broadcasting decoy name resolution requests using NBT-NS protocol from network decoys. NBT-NS protocol is used for translating NetBIOS names to IP addresses in Windows environments. Responders to NBT-NS queries listen to UDP port 137.
- **mDNS**: Enable to detect mDNS poisoning by broadcasting decoy name resolution requests using mDNS protocol from network decoys. mDNS protocol is typically used on small networks that do not have a dedicated local name server. Responders to mDNS queries listen to UDP port 5353.
LLMNR and NBT-NS techniques are recommended for Windows environments, and the mDNS technique is recommended for environments consisting of macOS systems.
- **Broadcast Interval (In minutes)**: Specify the time interval (in minutes) to configure the frequency based on how often the network decoys should broadcast decoy name resolution requests.
-
**Hostnames**: Enter hostnames (one hostname per line) that should be used to generate decoy name resolution requests. If a list of hostnames is configured in this field, then a hostname is selected at random from this list for each request. If the field is left blank, then the Zscaler service automatically generates a hostname for each request.
Zscaler recommends configuring hostnames that can lure attackers to respond with malicious responses. For example, hostnames such as Admin-PC and DBSSERVER can lure attackers to send malicious responses.
When configuring hostnames, make sure that they are unique and are not assigned to any real hosts on the network.
-
**Select subnets**: Select the subnet in which you want to detect MITM decoys by using the respective decoy connectors.
MITM detection is not supported for decoys connected to Threat Intelligence Decoy Connectors, ZPA Decoy Connectors, and cloud-based Decoy Connectors. Hence, subnets associated with these Decoy Connectors are not listed.
[See image.](#zd-MITM-configuration)
- Click **Save**.
[]![A screenshot capturing the page for configruing MITM attack detection](/downloads/deception/deceive/mitm-decoys/configuring-mitm-attack-detection/zscaler-deception-MITM-attack-detection.jpg)