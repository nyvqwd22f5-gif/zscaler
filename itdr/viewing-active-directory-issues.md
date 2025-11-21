# Viewing Active Directory Issues
Source: https://help.zscaler.com/itdr/viewing-active-directory-issues
PDF: https://help.zscaler.com/pdf/com/en/1531630.pdf

On the [Active Directory (AD) Posture](/itdr/about-active-directory-posture-dashboard) dashboard, you can view issue details grouped by:
- [Severity level](#itdr-view-issue-details-sev-type)
- [Risk type](#itdr-view-issue-details-risk-type)
- [MITRE ATT&CK technique exposure](#itdr-view-issue-details-mitre-attck)
[]To help you prioritize which issues to fix first, the AD Posture dashboard categorizes the issues using risk scores in its scans and reports. The issues are categorized into four severity levels (**Critical**,** High**, **Medium**, and **Low**) and are represented as a bar chart on the AD Posture dashboard. The bar chart illustrates the distribution of issues across these severity levels in the AD domain. The chart provides an overview of the risk composition of the AD. You can drill down into a specific issue on the chart to further investigate and remediate it.
[See image.](#itdr-view-iss-det-sev-chart-image)
[]A donut chart provides an overview of the types of risk most prevalent in the AD domain. You can drill down to a specific risk type on the chart to further investigate and remediate the issue.
Zscaler ITDR detects the following risk types in an AD domain:
- **Insecure Kerberos Configuration**: Weak Kerberos configurations allow adversaries to impersonate AD account credentials.
- **Insecure Permissions**: Insecure permissions lead to data breaches, privilege escalation, or malware exploitation.
- **Certificate Authority Misconfiguration**: Certificate authority misconfigurations compromise the integrity of the public key infrastructure (PKI) leading to unauthorized issuance of certificates and potentially compromising the entire AD domain.
- **Insecure Password Account And Group Management**: Insecure or default passwords and failing to enforce strong password policies leads to unauthorized access or privilege escalation.
- **Domain Controller Risk**: Domain Controller (DC) risks such as weak security configurations, outdated patches, etc. allow adversaries to gain control over the AD domain and compromise the entire network.
[See image.](#itdr-view-iss-det-risk-any-chart-image)
[]A kill chain maps AD issues to the following MITRE ATT&CK techniques. You can drill down into a specific issue on the kill chain to further investigate and remediate the issue:
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
[See image.](#itdr-view-iss-det-mitre-attck-image)
To view the issue details:
- Go to **ITDR** > **Dashboard **> **Active Directory Posture**.
-
On the **Active Directory Posture **dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
The scan result for the AD domain appears.
-
Click one of the following:
- **Severity**
- **Risk Analysis**
- **MITRE ATT&CK Technique Exposure**
The issues page appears.
- Select an issue to view the following information:
-
Issue and attack details:
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk (e.g., **Kerberos Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, or **Difficult**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **References**: A link to National Cybersecurity Agency of France (ANSSI) checklist mapping. ANSSI is a French government organization that secures government information systems. For an issue, you can click the reference link to view ANSSI recommendations and best practices to understand the issue context and remediation.
-
**Who is affected?**: A list of user accounts and computers that are vulnerable to attack. Click a [user](/itdr/viewing-affected-active-directory-user-account-details) or [computer](/itdr/viewing-affected-active-directory-computer-details) to view the details.
You can use the **Actions** menu to [export the affected user account and computer details as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, click **Remediations** to [remediate AD issues](/itdr/running-remediation-actions-ad-identities), and click **Add Objects to Safelist** to [add the AD object to the safelist](/itdr/adding-active-directory-object-safelist).
[See image.](#itdr-view-issue-all-info-image)
- Remediation details:
-
If there is a single remediation for an issue, you can view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download and run](/itdr/downloading-and-running-remediation-script) in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-view-single-rem-details-image)
-
If there are multiple remediations for an issue, ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download and run](/itdr/downloading-and-running-remediation-script) in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
[See image.](#itdr-view-mul-rem-details-image)
Click **Export Remediation Chart** to export the flowchart as an SVG file.
Click the** Add object to safelist** link in a remediation step to [add AD objects to the safelist](/itdr/adding-active-directory-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can then select the AD objects and click **Add Objects to Safelist**.
[]![View Severity chart](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-sev-bar-chart-1.png)
[]![View Risk Analysis chart](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-risk-anyl-chart-1.png)
[]![View MITRE ATT&CK technique mapping](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-mitre-attc-1.png)
[]![View issue details](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-all-info.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-rem-single.png)
[]![View multiple remediation details](/downloads/itdr/dashboard/active-directory-posture/active-directory-posture-details/viewing-ad-issue-details-grouped-severity-type/itdr-view-issue-details-rem-multiple.png)