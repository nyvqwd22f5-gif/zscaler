# About Landmine Decoys
Source: https://help.zscaler.com/deception/about-landmine-decoys
PDF: https://help.zscaler.com/pdf/com/en/1531328.pdf

[Watch a video on Creating Landmine Decoys and Policies](https://fast.wistia.net/embed/iframe/c3w5mose6l).
Landmine decoys look like valuable assets ripe for exfiltration. They can be decoy files, credentials, and application lures on endpoints. When adversaries access these decoys, Zscaler Deception sends alerts about the adversary's presence. You can use the [Deception dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard) to analyze an adversary's behavior, hunt for threats across the network, or block access.
Landmine decoys can detect the following types of attacks:
- Defense Evasion
- T1562.001: Impair defenses – Disable or modify tools
- Impact
- T1489: Service stop
- T1485: Data destruction
- Credential Access
- T1552.001: Unsecured credential – Credentials in files
- T1557.001: Man-in-the-Middle – Link-local multicast name resolution (LLMNR) poisoning and server message block (SMB) relay
- Collection
- T1005: Data from local system
Landmine decoys provide the following benefits and enable you to:
- Protect endpoints against ransomware attacks such as attempts to encrypt files and credentials stealing at every stage of the kill chain.
- Intercept adversaries who have bypassed traditional perimeter-based defenses and limit their ability to find targets or move laterally.
You can create landmine decoys based on policies. A landmine agent fetches these policies and verifies if they apply to an endpoint, and then deploys the decoys. You can create a base policy that enables a simple detection mechanism or an advanced base policy that enables advanced detection mechanisms to detect adversarial techniques.
About the Landmine Page
On the Landmine page (Deceive > Landmine), you can do the following:
- Configure landmine [policies](/deception/about-policies) with selection criteria and modules.
- Install landmine [agent](/deception/about-landmine-agents) or agentless installers.
- Customize the landmine installer [settings](/deception/about-landmine-settings).
- Release software update in a [phased](/deception/about-landmine-agent-update-phase-groups) rollout.
-
Configure [safe processes](/deception/about-safe-processes).
![About the Landmine page](/downloads/deception/deceive/landmine-decoys/about-landmine-decoys/zscaler-deception-about-landmine-1.png)