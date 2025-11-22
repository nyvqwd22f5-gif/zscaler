# About Active Directory Posture
Source: https://help.zscaler.com/itdr/about-active-directory-posture-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1531624.pdf

[Watch a video on Scanning an Active Directory.](https://fast.wistia.net/embed/iframe/1uidumi112)
Misconfigurations, unintended excessive privileges, and vulnerabilities in the identity infrastructure are key attack vectors. Adversaries use stolen credentials to compromise users and leverage these misconfigurations and permissions in the identity infrastructure to escalate privileges and move laterally. Out of all the identity systems, the on-premises Active Directory (AD) is the most widely used.
The Active Directory Posture dashboard enables you to:
- Obtain visibility into misconfigurations and vulnerabilities that exist in your AD.
- View a unified domain risk severity that can be used for executive reporting and tracking.
- View remediation guidance to fix issues that reduce the risk score and make the AD less vulnerable to identity-based attacks, such as DCSync, DCShadow, AS-REP Roasting, etc.
About the Active Directory Posture Dashboard
The Active Directory Posture dashboard summarizes the state of your AD security posture. On the Active Directory Posture dashboard (ITDR > Dashboard > Active Directory Posture), you can do the following:
- Filter scan results by AD domain and timestamp.
- View the total number of issues discovered after assessing the computers and users (objects) in the AD domain.
- View the domain risk severity, categorized as **Critical**, **High**, **Medium**, or **Low**. Click **Risk Score** to view and download [the AD scan report](/itdr/viewing-vulnerability-report).
- View a list of the top 5 issues that are found in the AD. After the AD domain is scanned for various posture checks that are mainly focused on weak permissions, privilege escalations, insecure domain configuration etc., the issues and misconfigurations detected are listed. These are issues and misconfigurations that have the highest impact on your risk score and are the easiest to remediate. If you fix these issues first, you can significantly reduce your risk score. [Click an issue to view additional details](/itdr/viewing-issue-finding-recommendation-details).
- View a list of the top 10 [users](/itdr/viewing-affected-active-directory-user-account-details) and [computers](/itdr/viewing-affected-active-directory-computer-details) that have the highest risks in the AD. Having visibility of these 10 riskiest objects in your AD helps you to prioritize what to focus on first.
- View all of the AD issues categorized by severity in a bar chart. This gives you an overview of the risk composition of the AD. Click the chart to [view issue details](/itdr/viewing-active-directory-issues).
- View all of the AD issues categorized by risk in a donut chart. This gives you an overview of the types of risk most prevalent in AD. Click the chart to [view issue details](/itdr/viewing-active-directory-issues).
- View [active changes detected ](/itdr/about-itdr-change-detection)that provide near real-time visibility into new misconfigurations and security risks introduced to your AD. Double-click a change detection issue to [view issue and remediation details](/itdr/viewing-change-detection-issue-and-remediation-details).
- View the [Risk Reduction Roadmap](/itdr/viewing-active-directory-risk-reduction-roadmap) to see the current domain risk severity and set targets to systematically lower the risk severity by providing a prioritized and actionable remediation roadmap.
- View all of the AD issues mapped to MITRE ATT&CK  techniques and displayed on a kill chain. This widget enables you to get visibility into issues that can be exploited by adversaries during various stages of an attack. Click an issue mapped on the kill chain to [view issue details](/itdr/viewing-active-directory-issues).
- Download the [AD executive summary report](/itdr/downloading-itdr-active-directory-executive-report) and [Delta Scan report](/itdr/downloading-active-directory-delta-report).
- View and download the [AD posture scan report](/itdr/viewing-active-directory-posture-scan-report).
- View [AD remediation logs or history](/itdr/viewing-ad-remediation-history) details.
- Run an [on-demand scan](/itdr/triggering-demand-scan) for the selected AD domain whenever necessary.
- Include AD decoy users and computers in the AD posture scan.
- Delete an AD scan report. After you delete a scan report, all the posture results pertaining to that AD domain are deleted.
![About the Active Directory Posture dashboard](/downloads/itdr/dashboard/active-directory/about-identity-posture-dashboard/itdr-ad-posture-dashboard-12.png)