# About Deceive
Source: https://help.zscaler.com/deception/about-deceive
PDF: https://help.zscaler.com/pdf/com/en/1531345.pdf

Deceive allows you to configure and deploy decoys to disrupt active attacks, create fake attack paths, and gain high-fidelity threat intelligence. You can deploy decoys across public-facing endpoints, network, cloud, and Active Directory (AD) to detect threats. You can also launch your deception campaign with ready-to-use decoys and focus on detecting threats instead of configuring a new solution. For a complete list of ranges and limits per Deceive feature, see [Ranges & Limitations](/deception/ranges-and-limitations).
The Deceive feature provides the following benefits and enables you to:
- Configure various types of decoys, such as network decoys, Threat Intelligence (TI) decoys, AD decoys, cloud decoys, and landmines.
- Create deception strategies based on your business and organizational requirements.
- Configure a deployment strategy to implement multiple deception strategies in your environment.
- Monitor and manage the health status of deployed decoys.
- Configure various deception settings, such as creating a blocklist based on IPs and ports, hashing passwords entered in application decoys, enabling name resolution of attackers' identity, and creating network decoy groups.
The key features of Deceive are:
- Stop lateral movement: Network decoys deployed in the network detect attackers attempting to move laterally and disrupt them.
- Disrupt ransomware: Decoys placed across your environment detect and slow down ransomware at every stage of the kill chain and limit its blast radius.
- Detect compromised users: Decoy passwords, cookies, sessions, and bookmarks to decoy applications detect compromised users when an attacker uses one of these deceptive assets.
- Detect prebreach threats: TI decoys detect prebreach threats that are specifically targeting your organization.
- Detect enumeration activity and malicious access: Decoy users in an AD detect enumeration activity and malicious access.
About the Deceive Menu
On the Deceive menu, you can do the following:
- Go to the [deceive summary page](/deception/about-deceive-summary) to view details of deployed decoys.
- Go to the [TI decoys](/deception/about-threat-intelligence-decoys) to create and manage TI decoys.
- Go to the [Deploy Strategy](/deception/about-deploy-strategy) page to create and manage deploy strategies.
- Find an option to configure [man-in-the-middle (MITM)](/deception/configuring-mitm-attack-detection) attack detection.
- Find options to create and manage [internal network decoys](/deception/creating-internal-network-decoy) and [Zero Trust network decoys](/deception/creating-zero-trust-network-decoy).
- Find options to create and manage [AD decoys](/deception/about-active-directory-decoys) and the associated resources, such as [triggers](/deception/configuring-and-downloading-trigger-script) and [domains](/deception/adding-active-directory-domain).
- Find options to set up cloud deception with [Microsoft Azure](/deception/about-cloud-deception-with-azure) and [Amazon Web Services](/deception/about-cloud-deception-with-aws).
- Find options to set up endpoint deception using [landmine decoys](/deception/about-landmine-decoys), including options to configure and manage [landmine policies](/deception/about-policies), [landmine agents](/deception/about-landmine-agents), settings to [deploy](/deception/about-landmine-settings) and [update](/deception/about-landmine-agent-update-phase-groups) landmine agents, and [safe processes](/deception/about-safe-processes).
- Go to [Deceive Settings](/deception/about-deceive-settings) to configure [blocklists](/deception/creating-blocklist), [hash passwords](/deception/storing-passwords-hashes), [hostname resolution settings](/deception/configuring-hostname-resolution-settings), and [network decoy groups](/deception/creating-network-decoy-group).
![About Deceive](/downloads/deception/deceive/about-deceive/zscaler-deception-about-deceive-menu_0.png)