# About Evidence
Source: https://help.zscaler.com/deception/about-evidence
PDF: https://help.zscaler.com/pdf/com/en/1531374.pdf

When an attacker interacts with a decoy, Zscaler Deception generates evidence files. These files consist of evidence of an attack. You can use the evidence files as additional details to investigate the attack and gain insight into the attacker's tactics, techniques, and procedures (TTPs).
Evidence provides the following benefits and enables you to:
- Generate evidence files for events triggered by attackers interacting with your decoys. You can use the evidence files to investigate the attack, including the attacker's tactics, techniques, and procedures (TTPs).
- Analyze the evidence files by seamlessly integrating with Zscaler Sandbox and third-party sandbox solutions, and download analysis reports directly from the Zscaler Deception Admin Portal.
- Download the evidence files in their original format to analyze them externally.
- Export records of evidence files generated for individual attack events.
The Evidence page lists all the evidence log files. Depending on the decoy interaction, the evidence files are available in the following formats:
- Packet Capture (PCAP)
- Remote Desktop Protocol (RDP) recording files
- Indicators of Compromise (IOC)
You can send some of the evidence files (e.g., IOC or RDP) to the Zscaler Sandbox or a third-party sandbox to enrich attack information and download the analysis report.
About the Evidence Page
On the Evidence page (accessed from the [extended details](/deception/viewing-extended-details) page), you can do the following:
- View the list of evidence files and activity details.
- [Send an evidence file to a sandbox](/deception/sending-evidence-file-sandbox).
- [Download a sandbox report](/deception/downloading-sandbox-report).
- [Download evidence files](/deception/exporting-evidence-files).
- [Export evidence details](/deception/exporting-evidence-details).
-
[Delete evidence files](/deception/deleting-evidence-files).![About the Evidence page](/downloads/deception/investigate/about-evidence/About%20Evidence%20Page.jpg)
You can access the Evidence tab only through the Deception Admin Portal and Decoy Connector icons in the alert graph on the [Deception Dashboard](/deception/viewing-and-managing-zscaler-deception-dashboard).