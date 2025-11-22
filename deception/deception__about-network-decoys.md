# About Network Decoys
Source: https://help.zscaler.com/deception/about-network-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531280.pdf

Network decoys detect scanning and lateral movement activities in your network environment. They mimic real assets on your network. You can deploy network decoys in business-critical network segments that host production servers, demilitarized zones (DMZ), key applications, databases, and cloud environments. Zscaler recommends that you deploy at least two network decoys in each business-critical network segment.
Network Decoys provide the following benefits and enable you to:
- Create and deploy legitimate-looking decoys in your organization's network that mimic real assets in your business-critical network segments to lure attackers into interacting with realistic targets and gain insights into the attacker's tactics, techniques, and procedures (TTPs).
- Enhance your organization's threat detection and incident response systems using the data collected from the attacker's interactions with the network decoy.
You can create Internal and Zero Trust Network decoys:
- An Internal decoy allows you to create decoy applications within your organization's network. You can configure an Internal decoy with a hostname or FQDN that resembles systems on your network and a MAC address that matches a manufacturer or a vendor.
- A Zero Trust Network decoy uses Zscaler Private Access (ZPA) to create decoy applications that appear to exist within your organization's network. You can configure Zero Trust Network decoys with an FQDN to make them look like a part of your network.
You can also [configure services](/deception/configuring-services-network-decoy) such as Web, SSH, FTP, File Shares, etc. on these decoys to create realistic targets for attackers. This helps in influencing an attacker's behavior by luring them to one of the decoys and gaining a better understanding of their tactics, techniques, and procedures (TTPs).
You can [add Internal decoys to an active directory (AD)](/deception/adding-network-decoy-active-directory) as computer objects to make them look like legitimate domain-joined systems. This allows the detection of AD enumeration activity and improves the ability to detect AD-related exploits.
After a network decoy is deployed, it is displayed on the Network Decoys page.
About the Network Decoys Page
On the Network Decoys page (Deceive > Network Decoys), you can do the following:
- View a list of all deployed network decoys. For each deployed decoy, you can see:
- **FQDN and IP**:** **The FQDN and the IP address assigned to the decoy, along with an icon that indicates the network decoy's deployment status:
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
- **Personality**: The[ predefined decoy template](/deception/using-network-decoy-personalities-and-services) used to create a decoy, along with the services that the decoy is configured to run.
- **Network Decoy Groups**:** **The network group in which the decoy is deployed. Network decoy groups allow logical organization of network decoys, such as geographic location or system type.
- **Network Name**:** **The name of the network in which the decoy is deployed.
- Create an [Internal](/deception/creating-internal-network-decoy) or a [Zero Trust Network](/deception/creating-zero-trust-networks-decoy) decoy.
- [Export network decoy configurations](/deception/exporting-network-decoys-configuration).
- [Edit or delete deployed network decoys](/deception/editing-and-deleting-network-decoy).
![About the Network Decoys page](/downloads/deception/deceive/network-decoys/about-network-decoys/zscaler-deception-about-network-decoys-2.png)