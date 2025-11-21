# Viewing Active Directory Detailed Findings and Recommendations
Source: https://help.zscaler.com/itdr/viewing-ad-issue-finding-recommendation-details
PDF: https://help.zscaler.com/pdf/com/en/1531627.pdf

Detailed findings and recommendations allow you to focus on the top priority issues for an Active Directory (AD) domain. You can view a list of the top 5 issues for an AD domain on the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard. These are issues and misconfigurations that have the highest impact on your risk score and are the easiest to remediate. You can view additional details about each issue and recommendations to further investigate and remediate the issue.
To view the issue details:
- Go to **ITDR** > **Dashboard **> **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-focus-area-select-ad-domain-timestamp)
The scan result for the AD domain appears.
-
Click **Detailed Findings and Recommendations**, or click an issue.
[See image.](#itdr-select-issue-focus-area)
The **Detailed Findings and Recommendations** page appears with the following information. Click a severity level (**Low**, **Medium**, **High**, or **Critical**) to filter the issues.
- The scanned AD domain name and scan time.
-
Issue and attack details:
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk (e.g., **Kerberos Abuse**, **Account Management**, **Credential Exposure**, etc.).
- **Severity**: The severity level (**Critical**, **High**, **Medium**, and **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, **Difficult**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., T1558.003, T1078.002, etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Privilege Escalation**, **Credential Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **References**: A link to National Cybersecurity Agency of France (ANSSI) checklist mapping. ANSSI is a French government organization that secures government information systems. For an issue, you can click the reference link to view ANSSI recommendations and best practices to understand the issue context and remediation.
-
**Who is affected?**: A list of user accounts and computers that are vulnerable to attack. Click a [user](/itdr/viewing-affected-active-directory-user-account-details) or [computer](/itdr/viewing-affected-active-directory-computer-details) to view the details.
You can use the **Actions** menu to [export the affected user account and computer details as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, click **Remediations** to [remediate AD issues](/itdr/running-remediation-actions-ad-identities), and click **Add Objects to Safelist** to [add the AD object to the safelist](/itdr/adding-active-directory-object-safelist).
[See image.](#itdr-ad-issue-details)
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
[See image.](#itdr-ad-single-remediation-details-recomm)
-
If there are multiple remediations for an issue, Zscaler ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- Videos that demonstrate how to remediate the issue.
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Remediation Script**: A script that you can [download and run](/itdr/downloading-and-running-remediation-script) in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation that provides the issue context and remediation details.
Click **Export Remediation Chart** to export the flowchart as an SVG file.
Click the** Add object to safelist** link in a remediation step to [add AD objects to the safelist](/itdr/adding-active-directory-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can then select the AD objects and click **Add Objects to Safelist**.
[See image.](#itdr-ad-remediation-flowchart-details-recomm)
[]![Select a scanned AD domain and timestamp](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-post-scan-domain-date-without-options.png)
[]![Select an issue](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-click-findings-recommend-issue-3.png)
[]![View AD issue findings and recommendations](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-click-findings-recommend-issue-details-6.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-click-findings-recommend-single-remediation-2.png)
[]![View remediation details](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-click-findings-recommend-remediation-flowchart-5.png)