# Assessing Compliance
Source: https://help.zscaler.com/risk360/assessing-compliance
PDF: https://help.zscaler.com/pdf/com/en/1532479.pdf

The integration of various risk frameworks with Risk360 helps you identify, assess, mitigate, and monitor risk, ensuring informed decision-making and abiding by regulatory compliance mandated or recommended based on your organization's geography and industry.
The Risk360 service supports the following risk frameworks:
- [ISO27001](#iso-27001)
- [MITRE ATT&CK](#mitre-att&ck)
- [NIST CSF](#nist-csf)
- [NIST SP 800-53](#nist-sp-800-53)
- [DORA](#dora)
- [NIS2](#nis2)
Analyzing the Framework
The framework page (Frameworks > select a framework) shows all the control IDs and maps these IDs to your current Zscaler protections and provides you with a holistic, as well as in-depth analysis for each technique. The page also shows any policy misconfigurations that are refraining you from securing techniques that can be reconfigured to strengthen your security stance.
Each tile shows the name of the technique and the ID. When you click on a tile, it opens all the sub-techniques under it. The tiles highlighted in blue indicate that they are covered by Zscaler protection, and the green or red color at the right side of these tiles indicates whether the protection is configured correctly or not.
Overview
The Legend section provides the following overview:
- The donut chart shows the split between the number of techniques covered by Zscaler and those that are not. The center of the donut chart shows the total percentage of technique coverage.
- **Configurations**: This section shows the number of configurations or policies that are misconfigured and configured correctly for your organization.
- You can show or hide this section by using the arrow at the top right of this section.
[See image.](#legend)
Drawer View
Click on a technique or sub-technique to view the following information in a drawer view to the right side of the page:
- [Techniques](#drawer-tech)
- [Sub-Techniques](#drawer-subtec)
[]The ISO 27001 is a set of standards for establishing, implementing, maintaining, and continually improving an information security management system (ISMS) for any organization. This helps your organization become more resilient to cyber attacks, maintain data integrity, confidentiality, and availability, while also achieving significant cost savings.
[]MITRE ATT&CK is a cybersecurity framework funded by the US government that is used to detect, identify, and classify various tactics, techniques, and procedures (TTPs) used for cyber attacks by attackers. It helps you assess your organization's security posture and calculate the risk of a cyber attack.
The MITRE ATT&CK framework assumes the attacker's point of view to navigate through your organization's network. This helps in highlighting the attacker's journey from the point of access to a potential data exfiltration, among other harmful acts.
To learn more, refer to the [MITRE ATT&CK website](https://attack.mitre.org/).
[]The National Institute of Standards and Technology (NIST) cybersecurity framework (CSF) is a set of recommendations and processes that you can implement and follow to strengthen your organization's security posture against malicious attackers that also provides guidance on how to respond and recover from a security breach event.
The NIST CSF is considered a very high-standard risk management tool across the industry as it provides great value at any stage of your cybersecurity journey. The Risk360 service supports both versions of NIST CSF (1.1 and 2.0) in the Risk360 Admin Portal. You can use both versions of the framework to manage your organization's risk.
[]The National Institute of Standards and Technology (NIST) Special Publication (SP) 800-53 is a set of structured security and privacy controls applicable specifically to federal information systems and organizations. It provides guidance on how to implement, assess, and strengthen an organization's security posture against malicious attackers while also making them breach ready with respond and recovery catalogs. The NIST SP 800-53 helps federal agencies and organizations comply with the mandatory Federal Information Security Management Act (FISMA) and other applicable laws and regulations for security.
While NIST CSF provides a comprehensive set of best practices for organizations to follow, the NIST SP 800-53 provides specific security controls that must be implemented by federal agencies and organizations.
[]The Network and Information Security Directive 2 (NIS2) is a European Union (EU) law that aims to improve cybersecurity across member states. A set of firm requirements for organizations in essential sectors, including risk management, incident reporting, and supply chain security, to create a common, high level of network and information security throughout the EU.
To learn more, refer to the [NIS2 Directive Document](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32022L2555).
[]The Digital Operational Resilience Act (DORA), a European Union (EU) regulation for the financial sector that mandates strong cybersecurity resilience and risk management for financial entities and critical Information and Communication Technology (ICT) third-party providers.
To learn more, refer to the [DORA Directive Document](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32022R2554&from=EN).
- []The name of the technique, its ID, and the state of the sub-techniques (i.e., whether they are Zscaler-protected or not).
- **Details**: A link that opens the PDF file where the technique is explained in detail.
- **Description**: A description of the technique. This field name differs depending on the framework you're viewing (e.g., NIST Description and ISO 27001 Description)
- **Zscaler Comment**: A note on how Zscaler can help mitigate the risk from this attack technique by using one of Zscaler's progressive protection portfolios. This field shows no information if the mitigation strategy isn't available.
- **TTP to Zscaler Product Mapping**: Maps the attack technique to the Zscaler feature responsible for protecting against these attack techniques, whether the features that are responsible for protecting against these tactics, techniques, and procedures (TTPs) are licensed by your organization or not, and the Risk360 category that the TTP falls under.
- **TTP to Risk360 Factor Mapping**: Maps all the attack sub-techniques to the [Risk360 Factors](/risk360/about-factors) and shows the status of each sub-technique.
- **Notes**: Any notes that you added for the technique.
[See image.](#ttp-drawer)
- []The name of the technique, its ID, and the state of the sub-technique, whether they are covered by Zscaler protection or not.
- **Details**: A link that opens the PDF file where the technique is explained in detail.
- **Description**: A description of the technique. This field name differs depending on the framework you're viewing (e.g., NIST Description and ISO 27001 Description)
- **Zscaler Comment**: A note on how Zscaler can help mitigate the risk from this attack technique by using one of Zscaler's progressive protection portfolios. This field shows no information if the mitigation strategy isn't available.
- **TTP to 3rd Party Tools Mapping**: Shows whether the sub-technique is securely configured, misconfigured, or not covered by the any third-party security control policies.
[See image.](#subtech-drawer)
Hover-Over View
Hover over a technique or sub-technique tile to view the following information:
- Whether the protections against these attack techniques are misconfigured or configured correctly and if Zscaler protects your organization against this attack technique.
- **Zscaler Control**: The Zscaler feature that is responsible for helping protect against these attack techniques.
- **Related Risk360 Factors**: The [Risk360 Factors](/risk360/about-factors) that are related to the attack.
- **Licensed?**: Whether or not you are subscribed to the Zscaler feature that protects against these attacks.
- **Notes**: Any notes that you added for the technique.
[See image.](#hover-over-tile)
[]![Sub-technique Drawer in NIST SP 800-53 framework](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-800-53/Risk360-nist-sp-sub-technique-drawer.png)
[]![TTP Drawer in NIST SP 800-53 framework](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-800-53/Risk360-nist-sp-technique-drawer.png)
[]![Hover dialog in NIST SP 800-53 framework](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-800-53/Risk360-nist-sp-technique-hover.png)
[]![Legend Section in NIST SP 800-53 framework](/downloads/risk360/dashboard-analytics/analyzing-risk-nist-800-53/Risk360-NIST-SP-Legend.png)