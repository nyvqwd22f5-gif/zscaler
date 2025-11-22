# Security Policy Audit Report
Source: https://help.zscaler.com/unified/security-policy-audit-report
PDF: https://help.zscaler.com/pdf/com/en/1497506.pdf

The Security Policy Audit Report allows you to view your Security Policy settings and improve them by following best practices guidelines.
You can view the report in the Admin Portal by going to Analytics > Internet & SaaS > Analytics > Security Policy Audit Report.
[See image.](#report)
Report Sections
The report has three main sections:
- [Traffic Inspection](#traffic)
- [Threat Protection](#threat)
- [Security Exceptions](#security)
[]This section includes:
- **SSL Inspection**: This includes the percentage of encrypted traffic that is being inspected, the Revoked Server certificate, and the Untrusted SSL Server certificate.
- **Inbound/Outbound**: Inspected inbound and outbound traffic.
- **Protocol Inspection**: This includes the following protocols:
- Inspect HTTP
- Inspect FTP over HTTP
- Inspect FTP
- Inspect Tunneled HTTP
[See image.](#trafficpic)
[]This section includes:
- **Malware**: Types of malware include:
- Viruses
- Unwanted applications
- Trojans
- Worms
- Adware
- Spyware
- **Advanced Threats**: Types of Advanced Threats include:
- PageRisk
- Botnet
- Malicious Active Content protection
- Fraud protection
- Unauthorized Communication protection
- XSS
- Suspicious destination
- **Browser Control**: This includes checks and Allow All Browsers. It's recommended to enable **Checks & User Notifications **and to block older browsers.
The Browser Vulnerability Protection section is only applicable when you are using browser-based authentication.
- **Cloud Sandbox**: This includes Sandbox policies 1 through 4.
[See image.](#threatpic)
[]This section includes SSL exceptions and Malware/Advanced Threats exceptions.
[See image.](#securitypic)
Report Grading
The possible grades you can receive are A, B, C, or N/A, with C being the lowest. Your grade is impacted if you don't comply with the best practice guidelines. If you don't have a subscription for a certain area (e.g. Sandbox), then any non-compliance in that area won't impact your grade.
If you don't follow the best practice settings for the following areas and policies, your grade for non-compliance will be a C:
- [See table.](#table)
If you don't follow the best practice settings for all other areas, your grade for non-compliance will be a B.
[]
| Area | Policy | Best Practice Setting |
| ---- | ------ | --------------------- |
| Malware Protection: Traffic Inspection | Inspect Inbound Traffic | Enabled |
| Malware Protection: Traffic Inspection | Inspect Outbound Traffic | Enabled |
| Malware Protection: Protocol Inspection | Inspect HTTP | Enabled |
| Advanced Threats: Botnet | Command & Control Servers | Block |
| Advanced Threats: Botnet | Command & Control Traffic | Block |
| Advanced Threats: Malicious Active Content | Malicious Content & Sites | Block |
| Advanced Threats: Fraud Protection | Known Phishing Sites | Block |
| Advanced Threats: Fraud Protection | Suspected Phishing Sites | Block |
| Sandbox | Known malicious files from any URL category of any file type | Action = BlockALL FILE TYPESALL URL CATS |
| Sandbox | All other file type and URL category combinations | First Time Action = Allow and Scan |
[]![ Screenshot of the Security Policy Audit Report, including grades for each section.](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/security-policy-audit-report/zia-security-policy-audit-report.png?1603376735)
[]![ Screenshot of the Traffic Inspection section: SSL Inspection and Inbound/Outbound Traffic.](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/security-policy-audit-report/zia-traffic-inspection-report-section.png?1603376810)
[]![Screenshot of the Threat Protection section: Malware, Advanced Threats, Browser Control, and Cloud Sandbox](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/security-policy-audit-report/zia-threat-protection-report-section.png)
[]![Screenshot of the Security Exceptions section: SSL Exceptions and Security Exceptions](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/security-policy-audit-report/zia-_security-exceptions-report-section.png)