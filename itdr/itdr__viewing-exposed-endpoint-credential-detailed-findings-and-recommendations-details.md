# Viewing the Exposed Endpoint Credential Detailed Findings and Recommendations
Source: https://help.zscaler.com/itdr/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details
PDF: https://help.zscaler.com/pdf/com/en/1531846.pdf

Detailed findings and recommendations allow you to focus on the top exposed credential issues on the endpoints. You can view a list of the top 5 exposed credentials on the Endpoint Credential Exposure dashboard. These are issues that have the highest impact on your domain risk severity level. Having visibility into these riskiest exposed credentials helps you prioritize what to focus on first. If you fix these issues first, you can significantly lower the domain risk severity level.
To view details of the exposed credential issues:
- Go to **ITDR** > **Dashboard** > **Endpoint Credential Exposure**.
-
Select a date from the **As of Date** calendar to view the total number of issues on that scan date.
[See image.](#itdr-ece-dashboard-detailed-findings-date)
-
Click **Detailed Findings and Recommendations**,** **or click an issue.
[See image.](#itdr-ece-detailed-findings-select-issues)
The **Detailed Findings** page appears with the list of issues. You can:
- Click a severity level (**Low**, **Medium**, **High**, or **Critical**) to filter the issues.
-
Click **Actions **to [create a ServiceNow ticket](/itdr/creating-servicenow-ticket) to track and assess the issue.
[See image.](#click-actions)
Select an issue to view the following details:
- **Issue**: The name of the issue.
- **Type of Risk**: The [type of exposed credential](/itdr/viewing-endpoint-credential-exposure-issues) issue.
- **Severity**: The severity level of the issue (**Critical**, **High**, **Medium**, or **Low**).
- **Remediation**: The remediation assessment (**Easy**, **Moderate**, or **Difficult**).
- **MITRE ATT&CK  ID**: The MITRE ATT&CK  technique ID (e.g., **T1552.005, T1078.002, **etc.). Click the ID to view more details about the attack technique.
- **MITRE ATT&CK  TACTICS**: The type of MITRE ATT&CK  tactic (e.g., **Credential Access**,** Lateral Movement**, etc.).
- **What is the issue?**: The description of the issue.
- **What is the impact?**: The consequences of the attack.
- **Remediation**: The steps to remediate the issue.
- **References**: A link to the Microsoft documentation, where you can view guidance and best practices for remediation.
-
**Who is affected?**: The details of the identities with exposed credentials.
You can clean up credentials only if the feature is supported for this exposure. To learn more, see [Cleaning Up Exposed Endpoint Credentials](/itdr/cleaning-exposed-endpoint-credentials). You can use the **Actions** menu to [copy specific columns from the table](/itdr/using-tables#itdr-copy-columns-table-section) and download the [table as a CSV or JSON file](/itdr/using-tables#itdr-export-table-csv-section).
[See image.](#itdr-ece-detailed-findings-issue-details)
[]![Select a scan scan](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details/itdr-exposed-cred-privilege-detail-findings-date.png)
[]![Select an issue from Detailed Findings](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details/itdr-exposed-cred-privilege-detail-findings-click-issue.png)
[]![View exposed credential issue details](/downloads/itdr/dashboard/endpoint-credential-exposure/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details/itdr-exposed-cred-privilege-detail-findings-details.png)
[]
![The Actions drop-down menu with Create ServiceNow ticket option](/downloads/tech-pubs-drafts/itdr-draft-articles/viewing-exposed-endpoint-credential-detailed-findings-and-recommendations-details-draft/ece-actions-servicenow-ticket.png)