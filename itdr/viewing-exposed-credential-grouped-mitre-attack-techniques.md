# Viewing Exposed Endpoint Credential Issues Grouped by MITRE ATT&CK  Techniques
Source: https://help.zscaler.com/itdr/viewing-exposed-credential-grouped-mitre-attack-techniques
PDF: https://help.zscaler.com/pdf/com/en/1531745.pdf

You can view the details of exposed endpoint credential issues grouped by the following MITRE ATT&CK  techniques. You can drill down to a particular issue to understand the adversarial tactics and techniques, investigate the vulnerability, and remediate the issues.
- [Initial Access](https://attack.mitre.org/tactics/TA0001/)
- [Execution](https://attack.mitre.org/tactics/TA0002/)
- [Persistence](https://attack.mitre.org/tactics/TA0003/)
- [Reconnaissance](https://attack.mitre.org/tactics/TA0043/)
- [Privilege Escalation](https://attack.mitre.org/tactics/TA0004/)
- [Defense Evasion](https://attack.mitre.org/tactics/TA0005/)
- [Credential Access](https://attack.mitre.org/tactics/TA0006/)
- [Discovery](https://attack.mitre.org/tactics/TA0007/)
- [Lateral Movement](https://attack.mitre.org/tactics/TA0008/)
- [Command and Collection (CnC)](https://attack.mitre.org/tactics/TA0011/)
- [Exfiltration](https://attack.mitre.org/tactics/TA0010/)
- [Impact](https://attack.mitre.org/tactics/TA0040/)
- [Collection](https://attack.mitre.org/tactics/TA0009/)
- [Resource Development](https://attack.mitre.org/tactics/TA0042/)
To view the exposed endpoint credential issue details grouped by MITRE ATT&CK  techniques:
- Go to **ITDR **> **Dashboard** > **Endpoint Credential Exposure**.
- Select the **MITRE ATT&CK ** **Exposures** tab.
-
Select a date from the **As of Date** calendar to view the total number of exposed credential issues on that scan date.
[See image.](#itdr-exposed-cred-mitre-attack-date)
The exposed credential issues grouped by MITRE ATT&CK  techniques are listed under the tabs (**All**, **Initial Access**, **Execution**, etc.).
-
Click a tab to view the following exposed credential issues and remediation details. Click a severity level (**Low**, **Medium**, **High**, or **Critical**) to filter the issues.
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk or exposure type (e.g., **Privilege Escalation**, **Admin Auto Logon Credentials**, **AWS Credentials Exposure**, etc.).
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  Tactics**: The type of the MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **Remediation**: The remediation description and steps.
- **References**: You can click the reference links to view the Microsoft documentation to understand the issue context and remediation.
-
**Who is affected?**: A list of identities with exposed credentials that are vulnerable to attack.
You can [clean up the exposed endpoint credentials](/itdr/cleaning-exposed-endpoint-credentials). You can use the **Actions** menu to [copy specific columns in the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [exposed credentials as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
[See image.](#itdr-exposed-cred-mitre-attack)
[]![Select a scan date](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-credential-grouped-mitre-attack-techniques/itdr-exposed-credentials-by-mitre-attack-date-3.png)
[]![View exposed endpoint credentials by MITRE ATT&CK techniques](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-credential-grouped-mitre-attack-techniques/itdr-exposed-credentials-by-mitre-attack-4.png)