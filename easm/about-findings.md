# About Findings
Source: https://help.zscaler.com/easm/about-findings
PDF: https://help.zscaler.com/pdf/com/en/1503591.pdf

EASM scans the internet to identify and track your organization's internet-facing assets and the risks associated with them to provide a comprehensive view into your organization's external attack surface. Following the discovery process, the assets are investigated to identify the risks associated with them, such as undetected vulnerabilities, misconfigurations, and compliance violations. The risk parameters identified in the assets are populated in the EASM Admin Portal as findings along with actionable insights and recommendations for individual findings. This enables you to take corrective measures to eliminate threats and vulnerabilities by prioritizing risks that impact business-critical assets or operations.
Findings provide the following benefits and enable you to:
- Gain comprehensive insights on vulnerabilities, misconfigurations, and compliance violations associated with your internet-facing assets, allowing you to prioritize corrective actions for the most critical risks that could impact your organization's operations.
- Access detailed insights, including risk scores, threat severity, and remediation recommendations, to effectively address vulnerabilities and strengthen your organization's security posture against potential threats.
The findings include a range of asset-based risks and vulnerabilities. Examples of risk findings include but are not limited to Common Vulnerabilities and Exposures (CVEs), TLS/SSL misconfigurations or outdated versions, expired digital certificates, domain registration expiration, exposed VPN appliances, insecure HTTP headers, internet-facing sensitive services (e.g., RDP, VNC, SSH, Telnet, SNMP). EASM provides insightful information into these findings and how to remediate risks in the associated assets. In addition, it provides extensive information on vulnerabilities, such as the threat severity, likelihood of exploitation, a risk score computed for the finding, comprehensive details on the origin of the vulnerability, exploitation mechanisms, impact level, and recommendations for risk remediation obtained from multiple sources, and more. You can access all of this information centrally from the Findings page on the EASM Admin Portal.
For a summary of your findings based on key metrics, see [Insights Overview dashboard](/accessing-interacting-insights-overview-dashboard).
About the Findings Page
On the Findings page (Insights > Findings), you can do the following:
- View the list of risk findings associated with the assets inventoried for the selected organization. For each finding, you can view:
- **Name**: An identifier for the finding sourced from the scan or assigned by EASM in some cases. Depending on the type of finding, this field can contain a wide variety of identifiers, such as CVE ID, VPN, Self-Signed Certificate, etc.
- **Category**: The category assigned to the finding from Exposure, Misconfiguration, and Vulnerability.
- **Status**: The status assigned to the finding from Not Verified, Verified, Disputed, Risk Accepted, and Resolved.
- **Risk Score**: A computed risk score for the finding by Zscaler based on multiple vectors such as threat severity, likelihood, and impact.
- **Impacted Asset**: The asset in which the finding was detected during the scan.
- **First Seen**: The timestamp when the finding was first identified in a scan.
- **Last Seen**: The timestamp when the finding was last observed in a scan.
- [Click a finding record to view comprehensive details about the finding.](/easm/understanding-finding-details)
- [Filter the findings data based on specific parameters such as Status, Risk Level, Last Seen, Category, and Type.](/easm/filtering-customizing-findings-page)
- [Modify the table and its columns.](/easm/filtering-customizing-findings-page)
- [Download the list of all findings tracked in the assets associated with the selected organization into a CSV file.](/easm/downloading-findings)
- Search for a finding by name.
- Select a different organization for which you want to view the findings. The default organization is automatically selected when the Findings page is accessed.
- View the timestamp when the findings data was last updated.
![Findings page in EASM that shows a list of risk findings associated with the assets discovered as part of the organization's attack surface](/downloads/easm/insights/about-findings/about-findings-page.png)