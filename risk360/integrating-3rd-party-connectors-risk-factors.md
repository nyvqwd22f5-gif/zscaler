# Integrating 3rd-Party Connectors for Risk Factors
Source: https://help.zscaler.com/risk360/integrating-3rd-party-connectors-risk-factors
PDF: https://help.zscaler.com/pdf/com/en/1529546.pdf

The Risk360 service's integration with Zscaler Data Fabric helps in providing better security and a risk assessment that creates a holistic risk quantification environment observed for Zscaler and other third-party technologies. Data Fabric ingests Zscaler and third-party data sources and then harmonizes, deduplicates, correlates, and enriches the ingested data that is used in the Risk360 service for risk quantification. You can configure connectors in the Data Fabric to ingest third-party data sources.
The following out-of-the-box risk factors based on third-party data sources are available in the Risk360 Admin Portal with a connector configuration:
| Factor Name | Connector Name |
| ----------- | -------------- |
| CrowdStrike - Zero Trust Score | CrowdStrike Crowdscore |
| CrowdStrike - Endpoint Security CrowdScore | CrowdStrike Crowdscore |
| CrowdStrike - Unsupported Devices | CrowdStrike Environment Assets |
| CrowdStrike - Unmanaged Devices | CrowdStrike Environment Assets |
| CrowdStrike - End-of-Life Operating System | CrowdStrike Environment Assets |
| CrowdStrike - Critical Domain Users Having High Privileges | CrowdStrike Identity Protection - Domain Users |
| CrowdStrike - Identity Protection for Active Directory | CrowdStrike Identity Protection - Security Assessment |
| CrowdStrike - Critical and High Incidents | CrowdStrike Incidents |
| CrowdStrike - High Severity XDR Detections | CrowdStrike Alerts |
| Critical and High Severity Vulnerabilities | CrowdStrike VulnerabilitiesQualys VulnerabilitiesTenable Vulnerability ManagementRapid7 InsightVMWiz Vulnerability FindingsMicrosoft Defender for Endpoints - Vulnerabilities |
| Highly Exploitable Vulnerabilities | CrowdStrike VulnerabilitiesQualys VulnerabilitiesTenable Vulnerability ManagementRapid7 InsightVMWiz Vulnerability FindingsMicrosoft Defender for Endpoints - Vulnerabilities |
| Unaddressed Critical and High Severity Vulnerabilities | CrowdStrike VulnerabilitiesQualys VulnerabilitiesTenable Vulnerability ManagementRapid7 InsightVMWiz Vulnerability FindingsMicrosoft Defender for Endpoints - Vulnerabilities |
Reach out to your Zscaler Account team to define and implement custom risk factors not listed in the preceding table to serve your organization's specific requirements.
Refer to the following deployment guides for configuring connectors in Zscaler Data Fabric to implement the preceding factors:
- [Configuration Guides](#config-guides)
[](/zscaler-technology-partners/zscaler-and-microsoft-services-deployment-guide)
[](/zscaler-technology-partners/zscaler-and-crowdstrike-deployment-guide)[](/zscaler-technology-partners/zscaler-and-qualys-deployment-guide)[](/zscaler-technology-partners/zscaler-and-tenable-deployment-guide)[](/zscaler-technology-partners/zscaler-and-wiz-deployment-guide)[](/zscaler-technology-partners/zscaler-and-rapid7-deployment-guide)
| Connector | Configuration Guide |
| --------- | ------------------- |
| Microsoft Defender for Endpoints - Vulnerabilities | Zscaler UVM and Microsoft Services Deployment Guide |
| CrowdStrike IncidentsCrowdStrike AlertsCrowdStrike Environment AssetsCrowdStrike Vulnerabilities | Zscaler and CrowdStrike Deployment Guide |
| Qualys Vulnerabilities | Zscaler UVM and Qualys Deployment Guide |
| Tenable Vulnerability Management | Zscaler UVM and Tenable Deployment Guide |
| Wiz Vulnerability Findings | Zscaler UVM and Wiz Deployment Guide |
| Rapid7 InsightVM | Zscaler and Rapid7 Deployment Guide |
[]