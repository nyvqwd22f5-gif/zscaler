# Understanding the Zscaler Sandbox Report
Source: https://help.zscaler.com/deception/understanding-zscaler-sandbox-report
PDF: https://help.zscaler.com/pdf/com/en/1531418.pdf

The Zscaler Sandbox Report displays the attack lifecycle, event killchain, malware behavior, and payload intent. It maps the information to the MITRE ATT&CK framework. You can leverage this report to enrich security operation workflows and strengthen your defenses throughout the security stack.
The Zscaler Sandbox Report page displays the following information:
- **Classification**: The threat type of the analyzed file, such as Benign, Malicious, and Suspicious with the associated threat score. The file is further categorized as follows:
- **Benign**: A known non-malicious file.
- **Adware**: A known malicious file that automatically renders advertisements and installs adware.
- **Anonymizer**: A known malicious file that contains anonymizers and P2P clients.
- **Malware**: A known malicious file that behaves like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware.
- **File Properties**: File properties such as the file size, digital certificates used to sign in to the file, MD5, SHA1, and SSDEEP hash details.
- **Exploits**: List of exploits detected, if any.
- **Network**: Information on which network connections were initiated and the network objects of the evidence file, if any.
- **Persistence**: Information on the persistence mechanism created by the evidence file.
- **Security Bypass**: The techniques used to bypass traditional security scanners and sandboxes.
- **Spyware**: The techniques spyware processes use to learn about the system and spy on the user.
- **Stealth**: The techniques used to hide the process from the user and systems trying to identify the malware.
- **System Summary**: Information related to the system and process.![About the Zscaler Sandbox Report](/downloads/deception/investigate/about-zscaler-sandbox-report/zscaler-deception-sandbox-report.png?1663838507)
You can click **Download Report** to download the report to your local system in the JSON format.