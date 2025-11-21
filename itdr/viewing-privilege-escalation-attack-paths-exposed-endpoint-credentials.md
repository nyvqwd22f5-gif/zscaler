# Viewing Privilege Escalation Attack Paths for Exposed Endpoint Credentials
Source: https://help.zscaler.com/itdr/viewing-privilege-escalation-attack-paths-exposed-endpoint-credentials
PDF: https://help.zscaler.com/pdf/com/en/1531746.pdf

Compromised credentials are the easiest privileged attack vector for an adversary to navigate an environment, gain administrator or root privileges, and then elevate their access rights to gain control over more sensitive systems.
The following credential misconfigurations in an identity can lead to privilege escalation:
- Non-adherence to the principle of least privilege (e.g., domain users are made part of the local administrator’s group).
- Misconfiguration in user account control settings (e.g., the ConsentPromptBehaviourAdmin value is set to 0).
- Security misconfiguration in AutoLogon (e.g., default credentials for admin or auto-logon credentials for an admin).
You can view the privilege escalation attack paths for exposed endpoint credentials, investigate the vulnerability, and remediate the issues.
To view the privilege escalation attack paths for exposed endpoint credentials:
- Go to **ITDR **> **Dashboard** > **Endpoint Credential Exposure**.
- Select the **Privilege Escalation Path** tab.
- Select a date from the **As of Date** calendar to view the exposed credential issues on that scan date.
[See image.](#itdr-exposed-credential-privi-esc-path)
-
The exposed credential issues and the details of privilege escalation attack paths are listed with the following information. Click a severity level (**Low**, **Medium**, **High**, or **Critical**) to filter the issues.
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk (e.g., **Privilege Escalation**, **Admin Auto Logon Credentials**, **AWS Credentials Exposure**, etc.).
- **Severity**: The severity level of the risk (**Critical**, **High**, **Medium**, or **Low**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  Tactics**: The type of the MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **Remediation**: The remediation description and steps.
- **References**: You can click the reference links to view the Microsoft documentation to understand the issue context and remediation.
-
**Who is affected?**: A list of systems that are vulnerable to attack.
You can [clean up exposed endpoint credentials](/itdr/cleaning-exposed-endpoint-credentials). You can use the **Actions** menu to [copy specific columns in the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [system credentials as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
[See image.](#itdr-exp-cred-privi-esc-path-details)
[]![Select a scan date](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-privilege-escalation-attack-paths-exposed-endpoint-credentials/itdr-exposed-cred-privilege-esc-path-1.png)
[]![View privileged attack paths for exposed credentials](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-privilege-escalation-attack-paths-exposed-endpoint-credentials/itdr-exposed-cred-privilege-esc-path-details-2.png)