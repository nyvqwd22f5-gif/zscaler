# About Threat Intelligence Decoys
Source: https://help.zscaler.com/deception/about-threat-intelligence-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531291.pdf

Threat Intelligence (TI) decoys provide analytics of an attacker's activity early in the reconnaissance phase of the kill chain. These decoys are unlisted and require reconnaissance to discover (e.g., DNS bruteforcing, enumeration of certificate transparency logs, etc.).
TI decoys detect the following MITRE ATT&CK techniques:
- Reconnaissance
- T1589.001: Gather Victim Identity Information: Credentials
- T1592: Gather Victim Host Information
- T1594: Search Victim-Owned Websites
- T1595: Active Scanning
- T1595.002: Active Scanning: Vulnerability Scanning
- Initial Access
- T1133: External Remote Services
- T1078: Valid Accounts
- T1190: Exploit Public-Facing Application
TI decoys provide the following benefits and allow you to:
- Generate organization-specific intelligence about reconnaissance attempts and subsequent attacks against your public-facing assets.
- Generate alerts with a strong signal-to-noise ratio by ignoring random internet noise. These alerts can be cross-referenced with logs from a non-decoy infrastructure to identify any suspicious activities against other legitimate public-facing assets.
Some key use cases for TI decoys are as follows:
- Targeted pre-attack reconnaissance of public-facing infrastructure.
- Stolen credentials or credential-stuffing attacks.
- Attempts to exploit business logic flaws.
- Attempts to discover information (e.g., searches for configuration and backup files).
About the Threat Intelligence Decoys Page
On the Threat Intelligence Decoys page (Deceive > Threat Intelligence Decoys), you can do the following:
- View a list of all deployed TI decoys. For each deployed decoy, you can view:
- **Sub-domain FQDN**:** **The subdomain FQDN in which the decoy is deployed, along with an icon that indicates the decoy's deployment status:
- ![Red decoy deployment status icon](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-red-status-icon.png)
– Decoy is not deployed.
- ![Green decoy deployment status icon](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-green-status-icon.png)
– Decoy is successfully deployed.
- ![Yellow decoy deployment status icon](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-yellow-status-icon.png)
– Decoy is partially deployed.
- ![Orange decoy deployment status icon](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-orange-status-icon.png)
– Decoy is not connected to an aggregator.
- ![Gray decoy deployment status icon](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-grey-icon.png)
– Decoy is disabled.
- **Network Name**: The name of the network in which the decoy is deployed.
- **Type**: The type of decoy application (**Static**, **Dynamic**, or **High Interaction**).
- **Public IP**: The public IP address assigned to the TI decoy.
- [Export TI decoy DNS configuration details](/deception/exporting-threat-intelligence-decoys-dns-configuration).
- [Create TI decoys based on recommendations](/deception/creating-threat-intelligence-decoy-based-recommendations).
- [Export TI decoy configurations](/deception/exporting-threat-intelligence-decoys-configuration).
- [Create a TI decoy](/deception/creating-threat-intelligence-decoy).
- [Edit or delete deployed TI decoys](/deception/editing-and-deleting-threat-intelligence-decoy).
![About the Threat Intelligence Decoys Page](/downloads/deception/deceive/threat-intelligence-decoys/about-threat-intelligence-decoys/zscaler-deception-about-threat-intelligence-decoys-5.png)