# Viewing Entra ID Issues
Source: https://help.zscaler.com/itdr/viewing-entra-id-issues
PDF: https://help.zscaler.com/pdf/com/en/1531753.pdf

On the [Entra ID Posture](/itdr/about-entra-id-posture-dashboard) dashboard, you can view issue details grouped by:
- [Severity level](#itdr-entra-id-view-iss-det-severity)
- [Risk type](#itdr-entra-id-view-iss-det-risk)
- [MITRE ATT&CK technique exposure](#itdr-entra-id-view-iss-det-mitre-attack)
[]To help you prioritize which issues to fix first, the Entra ID Posture dashboard categorizes the issues using risk scores in its scans and reports. The issues are categorized into four severity levels (**Critical**, **High**, **Medium**, and **Low**) and are represented as a bar chart on the Entra ID Posture dashboard. The bar chart illustrates the distribution of issues across these severity levels in the Entra ID domain. The chart provides an overview of the risk composition of the Entra ID. You can drill down into a specific issue on the chart to further investigate and remediate it.
[See image.](#itdr-view-entra-id-iss-det-sev-chart-img)
[]A donut chart provides an overview of the types of risk most prevalent in the Entra ID tenant. You can drill down to a specific risk type on the chart to further investigate and remediate the issue.
Zscaler ITDR detects the following risk types in an Entra ID tenant:
- **Best Practice Violations**: Security best practices help you to secure your environment in the Entra ID tenant. For example, enabling security defaults, enforcing multi-factor authentication (MFA), limiting guest user permissions, revoking deprecated user roles, limiting the number of global administrators to less than 5, etc. Violating these best practices could lead to data breaches, system compromise, non-compliance with data protection, and operational disruptions.
- **Hybrid Environment Risk**: The Entra ID hybrid-joined devices feature enables you to join your on-premises Active Directory (AD) with an Entra ID tenant. Hybrid environments pose security risks, such as unauthorized access, compliance issues, and data breaches.
- **Insecure Privilege Management: **Entra ID has privileged roles and permissions that are used to manage users, modify credentials, authenticate policies, or access restricted data. Insecure privileged role assignments can lead to elevation of privilege and leaks. If undetected, this can lead to serious consequences, including compliance violations, unauthorized access, and data breaches.
- **Access Control Issues**: Access control issues in Entra ID include users receiving inappropriate access levels, missing critical permissions, or misconfigured roles. Issues like lack of MFA or poorly managed application permissions can leak sensitive data for unauthorized access.
- **Weak Authentication Measures**: Weak authentication mechanisms or misconfigured access controls in Entra ID can lead to unauthorized access to sensitive data and resources. Administrators without MFA requirements have a higher risk of compromise. They are severely unprotected against phishing and password brute force attacks.
[See image.](#itdr-view-entra-id-iss-det-risk-chart-img)
[]A kill chain maps Entra ID issues to the following MITRE ATT&CK techniques. You can drill down into a specific issue on the kill chain to further investigate and remediate the issue:
- [Reconnaissance](https://attack.mitre.org/tactics/TA0043/)
- [Resource Development](https://attack.mitre.org/tactics/TA0042/)
- [Initial Access](https://attack.mitre.org/tactics/TA0001/)
- [Execution](https://attack.mitre.org/tactics/TA0002/)
- [Persistence](https://attack.mitre.org/tactics/TA0003/)
- [Privilege Escalation](https://attack.mitre.org/tactics/TA0004/)
- [Defense Evasion](https://attack.mitre.org/tactics/TA0005/)
- [Credential Access](https://attack.mitre.org/tactics/TA0006/)
- [Discovery](https://attack.mitre.org/tactics/TA0007/)
- [Lateral Movement](https://attack.mitre.org/tactics/TA0008/)
- [Collection](https://attack.mitre.org/tactics/TA0009/)
- [Command and Collection (CnC)](https://attack.mitre.org/tactics/TA0011/)
- [Exfiltration](https://attack.mitre.org/tactics/TA0010/)
- [Impact](https://attack.mitre.org/tactics/TA0040/)
[See image.](#itdr-view-entra-id-iss-det-mitre-att-image)
To view the issue details:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
-
On the **Entra ID Posture **dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
The scan result for the Entra ID tenant appears.
-
Click one of the following:
- **Severity**
- **Risk Analysis**
- **MITRE ATT&CK technique exposure**
The issues page appears.
- Select an issue to view the following information::
-
Issue and attack details:
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk (e.g., **Hybrid Risk**, **Privilege Leak**, **Data Loss**, etc.).
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, or **Difficult**).
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., P**rivilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue.
- **What is the impact?**: The consequences of the attack.
- **References**: Click the reference link to view the Microsoft documentation or any other reference document to understand the issue context and remediation.
-
**Who is affected?**: A list of affected identities that are vulnerable to attack.
You can use the **Actions** menu to [export the affected identities as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, and click **Remediation** to [remediate Entra ID issues](/itdr/running-remediation-actions-microsoft-entra-id-issues).
[See image.](#itdr-view-entra-id-iss-det-all-issues)
-
Remediation details
-
If there is a single remediation for an issue, you can view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-entra-id-view-iss-det-single-rem)
-
If there are multiple remediations for an issue, ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-entra-id-issue-det-mul-rem)
Click **Export Remediation Chart** to export the flowchart as an SVG file.
Click the** Add object to safelist** link in a remediation step to[ add objects to the safelist](/itdr/adding-entra-id-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can then select the AD objects and click **Add Objects to Safelist**.
[]![View the Entra ID Severity chart](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details/itdr-entra-id-issue-det-sev-chart.png)
[]![View Entra ID Risk analysis chart](/downloads/itdr/dashboard/entra-id/entra-id-posture-details/viewing-entra-id-issue-details-grouped-risk-type/itdr-entra-id-issue-det-risk-chart.png)
[]![View Entra ID MITRE ATT&CK kill chain](/downloads/itdr/dashboard/entra-id-posture/entra-id-posture-details/viewing-entra-id-issue-details/itdr-entra-id-issue-det-mitre-attack-1.png)
[]![View Entra ID issue details](/downloads/itdr/dashboard/entra-id-posture/entra-id-posture-details/viewing-entra-id-issue-details/itdr-entra-id-issue-det-all-issues-1.png)
[]![View Entra ID remediation details](/downloads/itdr/dashboard/entra-id-posture/entra-id-posture-details/viewing-entra-id-issue-details/itdr-entra-id-issue-det-single-rem.png)
[]![View the Entra ID remediation flowchart](/downloads/itdr/dashboard/entra-id-posture/entra-id-posture-details/viewing-entra-id-issue-details/itdr-entra-id-issue-det-mul-rem.png)