# Viewing Change Detection Issue and Remediation Details
Source: https://help.zscaler.com/itdr/viewing-change-detection-issue-and-remediation-details
PDF: https://help.zscaler.com/pdf/com/en/1531637.pdf

[Watch a video on Identity Change Detection.](https://fast.wistia.net/embed/iframe/37o4d4nbip)
When active changes in an Active Directory (AD) domain are detected and the impact is listed as Good, Bad, or Info, you can review the impact, view the issue details, and remediate issues.
To view issue and remediation details:
- Go to **ITDR** > **Dashboard **> **Active Directory Change Detection **> **Default**.
-
Select an AD domain from the **Result for** drop-down menu.
The changes detected in the AD environment are listed.
-
Double-click a change, or click the **View** icon under **Actions** to view the details.
[See image.](#itdrn-change-detection-view-issue-details)
The **Issue Details **window appears with the following details:
- **Change Date**: The date and time when a change is detected in the AD domain.
- **Issue Name**: The issue name.
- **Change**: The description of active changes.
- **Who is affected?**: The details of the account in which the change was detected.
- **Type of Risk**: The type of risk (e.g., **Delegation Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **What is the issue?**: The description of the issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **MITRE ATT&CK ID**: The MITRE ATT&CK technique ID (e.g., **T1558.003**, **T1078.002**, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK Tactics**: The type of MITRE ATTACK tactic (e.g., **Privilege Escalation**,** Credential Access**, etc.**)**.
- **Investigate**: Issue investigation details.
-
**Remediation**: The remediation description and assessment (**Easy**, **Moderate**, **Difficult**, etc.). For every remediation step, you can view:
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to remediation steps in Microsoft documentation.
[See image.](#itdr-change-detection-issue-details)
[]![Click the view icon](/downloads/itdr/dashboard/change-detection/viewing-change-detection-issue-and-remediation-details/itdr-change-detection-default-page_0.png)
[]![View AD change detection details](/downloads/itdr/dashboard/active-directory-change-detection/viewing-change-detection-issue-and-remediation-details/itdr-change-detection-view-issue-details-1.png)