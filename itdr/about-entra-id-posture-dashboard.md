# About Entra ID Posture
Source: https://help.zscaler.com/itdr/about-entra-id-posture-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1531748.pdf

Misconfigurations, excessive privileges, weak authentication measures, and vulnerabilities in a Microsoft Entra ID tenant are a key attack vector. Adversaries use stolen credentials to compromise users and leverage these misconfigurations and permissions in the tenant to escalate privileges and move laterally. A security compromise of the tenant can destabilize the integrity of your identity management infrastructure.
After the Entra ID tenant is assessed for vulnerabilities, the results are displayed on a dashboard.
The Entra ID Posture dashboard enables you to:
- Obtain visibility into misconfigurations and vulnerabilities that exist in your Entra ID instance.
- View a unified tenant risk severity that can be used for executive reporting and tracking.
- View key assessment reports and recent changes to enhance the security posture of your Entra ID.
- View remediation guidance to fix issues that reduce the risk score and make the Entra ID less vulnerable to identity-based attacks, such as brute force, phishing, ransomware, etc.
About the Entra ID Posture Dashboard
The dashboard summarizes the state of your Entra ID security posture. On the Entra ID dashboard (ITDR > Dashboard > Entra ID Posture), you can do the following:
- Filter scan results by Entra ID tenant and timestamp.
- View the total number of issues discovered after assessing the users, service principals, and configurations in the Entra ID tenant.
- View the tenant risk severity, categorized as **Critical**, **High**, **Medium**, or **Low**. The risk posture gets better as the severity level decreases.
- View a list of the top 5 issues that are found in the Entra ID. After the Entra ID is scanned for various posture checks that are mainly focused on best practice violations, data loss, excessive privileges, etc., the issues and misconfigurations detected are listed. These are issues and misconfigurations that have the highest impact on your risk score and are the easiest to remediate. If you fix these issues first, you can significantly reduce your risk score. [Click an issue to view additional details](/itdr/viewing-entra-id-focus-area-details).
- View a list of the [top 10 identities](/itdr/viewing-top-vulnerable-entra-id-identities) that have the highest risks in the Entra ID tenant. Having visibility of these 10 riskiest identities in your Entra ID helps you to prioritize what to focus on first. You can drill down to a specific [affected identity](/itdr/viewing-affected-entra-id-identity-details) to investigate and remediate.
- View all the Entra ID issues categorized by severity in a bar chart. This gives you an overview of the risk composition of the Entra ID. Click the chart to [view issue details](/itdr/viewing-entra-id-issues).
- View all the Entra ID issues categorized by risk in a donut chart. This gives you an overview of the types of risk most prevalent in Entra ID. Click the chart to [view issue details](/itdr/viewing-entra-id-issues).
- View [active changes detected](/itdr/about-entra-id-change-detection-dashboard) that provide near real-time visibility into new misconfigurations and security risks introduced to your Entra ID. Double-click a change detection issue to [view issue and remediation details](/itdr/viewing-entra-id-change-detection-issue-and-remediation-details).
- View the [Risk Reduction Roadmap](/itdr/viewing-entra-id-risk-reduction-roadmap) to see the current risk severity of the Entra ID tenant and set targets to systematically lower the risk severity by providing an automated and prioritized remediation roadmap.
- View all the Entra ID issues mapped to MITRE ATT&CK  techniques and displayed on a kill chain. This widget enables you to get visibility into issues that can be exploited by adversaries during various stages of an attack. Click an issue mapped on the kill chain to [view issue details](/itdr/viewing-entra-id-issues).
- Download the ITDR Microsoft Entra ID [executive summary report](/itdr/downloading-zscaler-itdr-microsoft-entra-id-assessment-posture-report) and [Delta Scan report](/itdr/downloading-entra-id-delta-report) in the PDF and Excel format.
- View [Entra ID remediation logs or history](/itdr/viewing-entra-id-remediation-history) details.
- View and download the [Entra ID vulnerability report](/itdr/viewing-entra-id-vulnerability-report).
- Run an on-demand scan for the selected Entra ID tenant whenever necessary. After you [configure an Entra ID tenant for a vulnerability scan](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal), the scan is triggered at the scheduled time. If you don't want to wait till the scheduled time, you can[ trigger an on-demand scan](/itdr/triggering-demand-scan-active-directory) manually.
- Delete a scan report. After you delete the scan report, all the vulnerability results pertaining to that Entra ID tenant are deleted.
![About the Entra ID Posture dashboard](/downloads/itdr/dashboard/entra-id/about-entra-id-dashboard/itdr-about-entra-id-dashboard-12.png)