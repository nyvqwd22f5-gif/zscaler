# Viewing Active Directory Computer Details
Source: https://help.zscaler.com/itdr/viewing-affected-active-directory-computer-details
PDF: https://help.zscaler.com/pdf/com/en/1531651.pdf

The [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard displays a list of the top 10 user accounts and computers (AD objects) that are at highest risk in the Active Directory (AD) domain. Having visibility of these 10 AD objects that are at highest risk helps you to prioritize what issues to focus on first. On the dashboard, you can click an AD computer to view additional details, such as failed posture checks and recent suspicious changes made to the AD computer. You can further investigate the issues and swiftly remediate the compromised computer to disrupt the attacker's operations.
On the AD computer details page, you can view the following information on each tab:
- [Summary](#itdr-aff-ad-comp-summary-tab)
- [Posture](#itdr-aff-ad-comp-posture-tab)
- [Change Detection](#itdr-aff-ad-comp-change-detect-tab)
[]Provides a snapshot of identity vulnerabilities in the AD computer. On the Summary page, you can do the following:
- View the name of the AD computer.
- View the following AD computer details:
- **Created On**: The date when the AD computer was created.
- **Identity Classification**: The AD computer type, such as privileged** **or service. A privileged AD computer has powerful permissions that allow the user to perform nearly any action in the AD. A service AD computer is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
- **Last Password Change**: The date when the password was last changed.
- **Critical Group Memberships**: The group membership of the critical AD group. ADs are primarily categorized into security and distribution groups. These groups have four different scopes, including universal, global, domain local, and local. Scope helps determine the areas in the AD domain where a group’s permissions can be enforced successfully. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups).
- View the total number of posture risks or misconfigurations the AD computer is exposed to. For example, Account control rights, Stale computer passwords, etc. Click **Review failed checks** to analyze the risk and quickly remediate the issue.
- View the total number of recent risky changes made to the AD computer that have a bad impact on the identity posture. Click **Review all changes** to investigate these recent risky changes and take appropriate steps to remediate issues.
- Take immediate action to contain an attack or threat via the ZIA and ZPA services. You can forward the attack details to ZIA and ZPA for automated containment. ZIA and ZPA inspect the attack details and block the attacks according to the defined policy.
[See image.](#itdr-aff-ad-comp-summary-image)
[]Provides visibility into the top risks in your AD computer. This helps you to prioritize what issues to focus on. You can view the following additional details about each risk to further investigate and remediate it. You can click a risk on the left pane to view the following information:
- Issue details:
- **Type of Risk**: The type of vulnerability risk (e.g., **Credential Exposure**, **Weak Permissions**, etc.).
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Moderate**, and **Low**).
- **Remediation**: The remediation assessment (e.g., **High**, **Moderate**, and **Easy**).
- **MITRE ATT&CK **: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  TACTICS**: The MITRE ATT&CK  tactic description (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **References**: A link to National Cybersecurity Agency of France (ANSSI) checklist mapping. ANSSI is a French government organization that secures government information systems. For an issue, you can click the reference link to view ANSSI recommendations and best practices to understand the issue context and remediation.
-
**Who is affected?**: The details of the AD computer that is vulnerable to attack.
You can use the **Actions** menu to [export the affected user account and computer details as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
- Remediation details: The remediation description and assessment (**Easy**, **Moderate**, or **Difficult**). For every remediation step, you can view:
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download](/itdr/downloading-and-running-remediation-script) and run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation. You can click the link to view guidance and best practices for remediation.
[See image.](#itdr-aff-ad-comp-posture-image)
[]Lists the recent risky or bad changes detected in the AD computer. It also provides additional issues and remediation details. For each change that is detected, you can view:
- Change details:
- **Change Date**: The date and time when a change is detected in the AD computer.
- **Issue**: The issues for which the change is detected (e.g., **Privileged account delegation**, **Unconstrained Delegation**, etc.).
- **Change**: The description of risky changes.
- **Impact**: Indicates that the change has a bad impact. The system administrators can review the bad impacts, view the issue details, and remediate the issues.
- **Classification**: The AD computer type, such as privileged** **or service. A privileged AD computer has powerful permissions that allow the user to perform nearly any action in the AD. A service ADcomputer is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
- Issue and remediation details: Click the **View** icon to view the following details:
- **Change Date**: The date and time when a change is detected in the AD computer.
- **Issue Name**: The issue name.
- **Change**: The description of risky change.
- **Who is affected?**: The details of the AD computer in which the change was detected.
- **Type of Risk**: The type of risk (e.g., **Delegation Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **What is the issue?**: The description of the issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **MITRE ID**: The MITRE ATT&CK  technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **Investigate**: Issue investigation details.
- **Remediation**: The remediation description and assessment (**Easy**, **Moderate**, **Difficult**, etc.). For every remediation step, you can view:
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation. You can click the link to view guidance and best practices for remediation.
[See image.](#itdr-aff-ad-comp-change-detection-image)
[]![View affected computer summary details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-computer-details/itdr-viewing-affected-ad-computer-details.png)
[]![View affected AD computer posture details](/downloads/itdr/dashboard/active-directory/viewing-affected-active-directory-computer-details/itdr-aff-ad-comp-posture-tab-2.png)
[]![View affected computer change detection details](/downloads/itdr/dashboard/viewing-affect-active-directory-computer-details/itdr-aff-ad-comp-change-detection-tab.png)