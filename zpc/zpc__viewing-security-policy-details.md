# Viewing Security Policy Details
Source: https://help.zscaler.com/zpc/viewing-security-policy-details
PDF: https://help.zscaler.com/pdf/com/en/1392541.pdf

ZPC displays a slew of information for each security policy it offers. You can view security policy details by clicking the policy ID on the Policies page. To learn more about security policies, see [About Security Policies](/zpc/about-security-policies).
The Security Policy Details page (Policies > Policy Name) displays information about each security policy in the following tabs:
- [Properties](#viewing-properties-tab)
- [Compliance](#viewing-compliance-tab)
- [Audit & Remediation](#viewing-audit-remediation-tab)
- [Alerts](#viewing-alerts-tab)
![Labeled tabs for the Security Policy Details page](/downloads/zpc/policies/about-security-policy-details/zpc-security-policy-details.png)
[]
The security policies properties offer information on policy details, when the policy was created and last updated, and threat details.
On the **Properties** tab, you can do the following:
- View the following **Policy Details**:
- **Policy Focus**: View whether the policy focuses on an asset or identity misconfiguration.
- **Policy Description**: View a brief explanation of what the security policy detects.
- **Asset Type**: View the asset types this security policy protects.
- **Policy Source**: View whether the security policy is predefined or a custom policy.
- **Last updated**: The timestamp for when the security policy was last updated.
- **Created**: View the ZPC administrator username who created the custom security policy.
- View the following **Threat Details**:
- **Category**: The security policy threat category (Ransomware, Misconfiguration, or Account Takeover).
- **Theme**: View the security policy theme (Compliance, Security Exposure, Security Events, or Blank).
- **MITRE ATT&CK**: The MITRE technique for the security policy.
![View the security policy properties tab on ZPC.](/downloads/zpc/policies/viewing-properties-tab/zpc-properties-tab.png)
[]
The Compliance tab offers compliance information for the selected security policy.
On the **Compliance** tab, you can view the following compliance details:
- **Compliance**: The compliance benchmark name.
- **Domain**: The compliance benchmark domain.
- **Control Section**: The control section of the compliance benchmark.
![View the compliance tab on policy details.](/downloads/zpc/policies/viewing-compliance-tab/zpc-compliance-tab.png)
[]
On the **Audit & Remediation** tab, you can view instruction procedures to audit and remediate the security policy:
![View the audit and remediation tab on policy details](/downloads/zpc/policies/viewing-audit-remediation-tab/zpc-audit-remediation-tab.png)
[]
The Alerts tab offers insight into the alerts generated on your cloud deployment for a specific security policy.
On the **Alerts **tab, you can do the following:
- Filter for alerts based on **Alert Status**.
- Search for alerts using the searchable columns.
- View the following alert details:
- **Alert ID**: Unique ID of the alert. Click to view the alert details. To learn more, see [About Alerts](/zpc/about-alerts).
- **Resource Name**: The resource name (**Identity Name** or **Asset Name**).
- **Alert Age**: The age of the alert (in days) from the last time the Alert Status was set to **Open**.
- **Last Updated**: The timestamp for when the alert was last modified.
- **Status**: The status (**Open**, **Closed**, or **Resolved**) of the alert.
- Modify the table and its columns. You can choose which columns appear on the alerts table. To learn more, see [Using Tables](/zpc/using-tables).
![View the alerts tab on security policy details on ZPC.](/downloads/zpc/policies/viewing-alerts-tab/zpc-alerts-tab.png)