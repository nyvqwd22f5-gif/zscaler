# About Attack Surface Report
Source: https://help.zscaler.com/zia/attack-surface-report
PDF: https://help.zscaler.com/pdf/com/en/1401996.pdf

The Attack Surface Report provides you with the details of your organization's exposed applications and servers to a public network, such as the internet, and their possible exploitation.
As part of our efforts to centralize risk management via the Risk360 service, the Attack Surface Report is no longer accessible from the ZIA Admin Portal. However, you can request this report only once by contacting your Zscaler Account team. To analyze and access this report on a regular basis, subscribe to Zscaler's Risk360 service. To learn more, see [What Is Risk360?](/risk360/what-risk360) and [Zscaler Risk360](https://www.zscaler.com/products-and-solutions/zscaler-risk-360).
The Attack Surface Report provides the following benefits and enables you to:
- Access exposed assets to the public network for potential exploitation.
- Discover unintentional configurations that can result in your organiation's security breach.
This report captures the following vulnerabilities and exposures:
- [Known Vulnerabilities](#known-vulnerabilities)
- [SSL/TLS Risks](#ssl-tls-risks)
- [Exposed Servers](#exposed-servers)
- [Namespace Exposure](#namespace-exposure)
- [Public Cloud Instances](#public-cloud-instance)
About the Attack Surface Report Page
On the Attack Surface Report page (Analytics > Attack Surface Report), you can do the following:
- [Notify about the latest available report](/zia/configuring-attack-surface-report-notification).
- View the domain name.
- View a list of all the available reports. For each report, you can see the following:
- **Report Name**: The name of the attack surface report.
- **Date**: The date and time at which the report was made available. You can sort this column.
- **Action**: Displays the downloadable file formats available for the report.
- Download the report either in PDF, PPT, or CSV format.
You can download the reports for the last 12 months.
![Screenshot of the Attack Surface Report page.](/downloads/tech-pubs-drafts/zia-draft-articles/attack-surface-report/ZIA-6.1r-Attack-Surface-Report-Page_0.png)
[]This section of the report displays a list of servers exposed to the internet and their existing known vulnerabilities. For each server, you can see the following information:
- Name
- IP
- Product
- Vulnerabilities
- Score
- Severity
The Vulnerabilities column displays the known common vulnerabilities and exposures (CVE) IDs associated with the servers.
[]This section of the report displays a list of servers that support older versions of SSL/TLS protocol that are currently at risk. For each server, you can see the following information:
- Name
- IP and Port
- Supported TLS Versions
[]This section of the report displays a list of servers running within your organization's network, currently exposed to the internet. For each server, you can see the following information:
- Name
- IP and Port
- ASN
- Product
[]This section of the report displays a list of server names that might reveal the functionality of the servers or any internal information.
[]This section of the report displays the public cloud instances managed by your organization, currently exposed to the internet. For each public cloud instance, you can see the following information:
- Name
- IP and Port
- Cloud