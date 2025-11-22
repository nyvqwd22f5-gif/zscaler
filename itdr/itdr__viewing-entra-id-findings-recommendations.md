# Viewing Entra ID Detailed Findings and Recommendations
Source: https://help.zscaler.com/itdr/viewing-entra-id-findings-recommendations
PDF: https://help.zscaler.com/pdf/com/en/1531752.pdf

The Detailed Findings and Recommendations allow you to focus on the top priority vulnerability issues for an Entra ID tenant. You can view a list of the top 5 issues for an Entra ID tenant on the Entra ID dashboard. These are issues and misconfigurations that have the highest impact on your risk score and are the easiest to remediate. You can view additional details about each focus area issue to further investigate and remediate the issue.
To view the focus area details:
- Go to **ITDR** > **Dashboard** > **Entra ID Posture**.
- On the **Entra ID Posture **dashboard:
- Select an Entra ID tenant from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-entra-id-focus-area-tenant-timestamp)
The scan result for the Entra ID tenant appears.
-
Click **Detailed Findings and Recommendations**,or click an issue.
[See image.](#itdr-entra-id-select-focus-area-issue)
The **Detailed Findings and Recommendations** page appears with the following information. Click a severity level (**Low**, **Medium**, **High**, or **Critical**) to filter the issues.
- The scanned Entra ID tenant name and scan time.
- Issue and attack details:
- **Issue**: The issue name.
- **Type Of Risk**: The type of risk (e.g., **Best Practice Violations**, **Insecure Collaboration Settings**, **Best Practice Violations**, etc.).
- **Severity**: The severity level (**Critical**, **High**, **Medium**, and **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, **Difficult**).
- **MITRE ATT&CK  Tactics**: The type of MITRE ATT&CK  tactic (e.g., **Lateral Movement**, **Initial Access**, etc.).
- **What is the issue?**: The description of the vulnerability issue with videos that demonstrate how an adversary performs the attack.
- **What is the impact?**: The consequences of the attack.
- **References**: You can click the reference link to view Microsoft documentation or any other reference document to understand the issue context and remediation.
-
**Who is affected?**: A list of affected identities that are vulnerable to attack.
You can use the **Actions** menu to [export the affected identities as a CSV file](/itdr/using-tables#itdr-export-table-csv-section) and [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table, click **Remediation** to [automatically remediate Entra ID issues](/itdr/running-remediation-actions-microsoft-entra-id-issues), and click **Add Objects to Safelist **to [add Entra ID objects to the safelist.](/itdr/adding-entra-id-object-safelist)
[See image.](#itdr-entra-id-details-recomm-issue-details)
- Remediation details:
-
If there is a single remediation for an issue, you can view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- **How to fix?**: Steps to manually remediate the issue.
- **Commands**: A command that you can run in PowerShell to remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation or any other reference document that provides remediation details.
[See image.](#itdr-entra-id-details-recomm-single-remediation)
-
If there are multiple remediations for an issue, Zscaler ITDR provides a flowchart that breaks down multiple steps into distinct workflows. The workflows in the flowchart are prioritized based on the most suitable remediation to the issue. The most appropriate remediation is listed first, followed by the less suitable ones. After you choose a workflow, you can click the link in an individual step or process to view:
- The remediation description and assessment (**Easy**, **Moderate**, **Difficult**).
- **How to fix?**: Steps to manually remediate the issue.
- **Caveats**: Warnings to consider before remediating the issue.
- **References**: A link to the Microsoft documentation or any other reference document that provides remediation details.
Click **Export Remediation Chart **to export the flowchart as an SVG file.
Click the **Add object to safelist** link in a remediation step to [add Entra ID objects to the safelist](/itdr/adding-entra-id-object-safelist). When you click the link, you are redirected to the **Who is affected?** table. You can select the Entra ID users or service principals and click **Add Objects to Safelist**.
[See image.](#itdr-entra-id-details-recomm-remediation-flowchart)
[]![Selecting an Entra ID tenant and timestamp](/downloads/itdr/dashboard/entra-id/viewing-entra-id-findings-recommendations/itdr-entra-id-post-scan-domain-date-without-options.png)
[]![Select an Entra ID issue](/downloads/itdr/dashboard/entra-id/viewing-entra-id-findings-recommendations/itdr-entra-id-findings-recomm-select-issue-5.png)
[]![View Entra ID issue details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-findings-recommendations/itdr-entra-id-findings-recomm-issue-details-6.png)
[]![View remediation details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-findings-recommendations/itdr-entra-id-findings-recomm-single-remediation-details-1.png)
[]![View Entra ID remediation details](/downloads/itdr/dashboard/entra-id/viewing-entra-id-findings-recommendations/itdr-entra-id-findings-recomm-remediation-flowchart-3.png)