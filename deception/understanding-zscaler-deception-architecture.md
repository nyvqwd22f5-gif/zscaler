# Understanding the Zscaler Deception Architecture
Source: https://help.zscaler.com/deception/understanding-zscaler-deception-architecture
PDF: https://help.zscaler.com/pdf/com/en/1531262.pdf

Zscaler Deception is a threat-detection solution built on the Zero Trust architecture, which is designed for seamless integration with the Zscaler service and other parts of your security environment. Deception is cloud-delivered and scalable, and requires minimal on-premises computing.
Deception Standalone
The Deception standalone architecture includes the following key components:
![Zscaler Deception standalone architecture](/downloads/deception/getting-started/understanding-zscaler-deception-architecture/diagram_cloud-deception_architecture-standalone.png)
- Zscaler Deception Admin Portal: A cloud-hosted user interface (UI) hosted by Zscaler. It serves as the central point of management and analysis for the Deception service. Decoy Connector and software agents connect to it. You can use the portal to create and deploy decoys across assets in your environment. The portal also provides a powerful dashboard for deep analysis and orchestration of events.
- Decoy Connector: Lightweight virtual appliances that are hosted in your environment and can create decoy applications within multiple trunked virtual local area networks (VLANs) of your network. Decoy Connectors can be used as a secure relay for integration between the Deception Admin Portal and applications, such as Active Directory (AD), security information and event management (SIEM), firewalls, etc. in your network.
- Landmine: Software agent installed on endpoints, such as desktops or laptops on your network. These agents deploy decoy credentials, files, processes, and lures to other decoys at your endpoints.
When an adversary probes for vulnerabilities and breaks into your network, the decoys look like real assets. The moment the adversary interacts with a decoy, the decoy detects the threat and relays all the information to the Deception Admin Portal.
The Deception Admin Portal uses the ThreatParse engine, which is a proprietary technology built into the Deception dashboard. ThreatParse conducts natural language reconstruction of attacks, summarizes log information, and translates attacks into plain English that is easy to understand. ThreatParse also links this information to the MITRE ATT&CK  framework and includes a risk score assigned to adversaries that enables security teams to prioritize the most pressing threats first.
Based on the type and severity of the actions that the adversary performs, the Deception Admin Portal performs the following actions:
- Automates actions using built-in integrations.
- Sends high-fidelity alerts to specific personnel via phone, text messages, and emails.
- Forwards the events to other security tools, such as a firewall or an EDR to automatically isolate the affected asset.
Deception Integrated with ZPA
Deception integrated with Zscaler Private Access (ZPA) leverages the Zero Trust Network Access (ZTNA) solution that allows you to create decoy applications that look like they exist within your organization's environment, but leverage ZPA's technology to redirect adversaries to the Deception cloud.
Decoys that make use of ZPA provide better visibility, intelligence, and containment capabilities than their non-ZPA counterparts.
![Zscaler Deception integrated with ZPA architecture](/downloads/deception/getting-started/understanding-zscaler-deception-architecture/diagram_cloud-deception_architecture-with-ZPA-new.png)
Deception uses the ZPA service to deploy decoys in a dedicated Deception cloud. The Landmine agent deploys decoy credentials, files, processes, and lures to other decoys at your endpoints. These lures direct adversaries away from your legitimate assets and towards decoy applications.
You don't have to install any additional Decoy Connectors or make any changes to your network configurations to add deception to your environment.
When an adversary breaks into your network and interacts with a decoy, Deception leverages Zero Trust access policies to block traffic from the adversary to the legitimate applications and contains the adversary to one system. Deception builds a complete picture of the adversary using the user and device identity information from the ZPA service.
To learn more about ZPA architecture, see [Understanding the ZPA Cloud Architecture](/zpa/understanding-zpa-cloud-architecture).