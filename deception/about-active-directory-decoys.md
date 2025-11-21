# About Active Directory Decoys
Source: https://help.zscaler.com/deception/about-active-directory-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531335.pdf

An Active Directory (AD) is a critical resource for managing the IT infrastructure in an organization. Adversaries use AD as a target to perform reconnaissance and identify critical resources, retrieve information, and perform lateral movement within the network.
Zscaler Deception provides a solution to detect threats that leverage AD. In the Deception Admin Portal, you can create AD decoy user and computer objects to detect enumeration activity or malicious access. These decoys detect attackers performing reconnaissance and privilege escalation.
AD decoys provide the following benefits and enable you to:
- Create and deploy various AD decoys, such as decoy service accounts, decoy privileged accounts, decoy dictionary usernames, and decoy *nix accounts.
- Detect attackers performing reconnaissance and privilege escalation using AD decoy users and computers.
- Reduce the attack surface by detecting and containing attackers interacting with AD decoys prior to lateral movement.
The AD decoys detect the following MITRE ATT&CK  techniques:
- Credential Access
- T1110 - Brute Force
- T1558 - Steal or Forge Kerberos Tickets
- Discovery: T1087.002: Account Discovery: Domain Account
The following are some key use cases:
- Decoy service account: Detects Kerberoasting attempts.
- Decoy privileged account: Detects privilege escalation techniques, such as brute force. Some privileged AD groups include administrators, domain admins, and enterprise admins. Configuring enticing descriptions like passwords or password hints helps detect the presence of any adversaries within the environment.
- Decoy dictionary usernames: Uses a popular list of usernames and passwords to detect brute force attacks.
- Decoy *nix account: Similar to Kerberoasting, adversaries can target domain accounts that do not require authentication to escalate privileges. Accounts that have authentication disabled are vulnerable to the AS-REP roasting attack.
About the Active Directory Decoys Page
On the Active Directory Decoys page (Deceive > Active Directory Decoys), you can do the following:
- [Create AD decoy users](/deception/creating-decoy-active-directory-user) and [run decoy deployment scripts](/deception/running-decoy-deployment-script-active-directory).
- [View AD decoy computer details.](/deception/viewing-active-directory-decoy-computers)
- [Configure and download trigger scripts](/deception/configuring-and-downloading-trigger-script).
- [Add AD domains and view AD domains managed by server agents](/deception/adding-active-directory-domain).
- Perform the following actions:
- **Add decoys**: [Add an AD decoy user](/deception/creating-decoy-active-directory-user).
- **Delete decoys**: Delete one or more AD decoy users.
- **Check decoys**: Verify if the AD decoy user is successfully deployed.
- **Upload Enumeration Detection JSON**: Upload the deployment JSON file. To learn more, see [Running the Decoy Deployment Script on an Active Directory](/deception/running-decoy-deployment-script-active-directory).
![About the AD Decoys page](/downloads/deception/deceive/active-directory-decoys/about-active-directory-decoys/zscaler-deception-about-ad-decoys-page-3.png)