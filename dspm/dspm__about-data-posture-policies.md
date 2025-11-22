# About Data Posture Policies
Source: https://help.zscaler.com/dspm/about-data-posture-policies
PDF: https://help.zscaler.com/pdf/com/en/1477751.pdf

[Watch a video on Data Posture Policies.](https://fast.wistia.net/embed/iframe/pwx62y9unc)
Data Posture policies are queries or rules that DSPM defines to protect your cloud resources from potential threats and improve your cloud security posture. Policies provide guidelines for managing and protecting your organization's sensitive data and ensuring it is stored securely and only shared with authorized users.
DSPM scans the resources against the polices enabled in your Amazon Web Services (AWS) accounts, Azure subscriptions, and Google Cloud Storage; identifies where the sensitive data is located, vulnerabilities such as any misconfigurations, presence of malware, or if the resource is publicly exposed to the internet, and potential possibilities of breach. DSPM generates [alerts](/dspm/about-alerts) that help you prioritize an incident and quickly remediate the issue. The policies are grouped by [threat categories](/dspm/threat-categories).
DSPM offers predefined policies that are aligned with industry standard cybersecurity and compliance benchmarks such as [NIST](https://www.nist.gov/cyberframework), [GDPR](https://gdpr-info.eu/), [PCI](https://www.pcisecuritystandards.org/standards/), etc. You can create [custom policies](/dspm/creating-custom-policies) to meet your organization's requirements. DSPM also provides predefined policies that use advanced options to scan the data.
Data Posture policies provide the following benefits and enable you to:
- View all the policies offered by DSPM.
- Gain data posture overview based on whether the policies are passing or failing for your resources.
- Create custom security policies to meet your organization's compliance requirements.
- Enable or disable policies on resources.
About the Policies Page
On the Policy page (Policy > Data Posture Policies), you can do the following:
- View the policy details. For each policy, you can view:
- **Policy Name**: The policy title.
- **ID**: The unique identifier for the policy.
- **Severity**: The severity level (Critical, High, Medium, or Low) of the policy.
- **Policy Source**: Whether the policy is a predefined or a custom policy.
- **Primary Resource Type**: The type of resource on which the policy is applied.
- [List of supported resource types](#ds-rtypes)
- **Last Updated**: The date and time the policy was last updated.
- **Cloud**: The cloud type in which the resource is located.
- **Alerts**: The number of open alerts for this policy.
- **Created Date**: The date and time the policy was created.
- **Policy Category**: The category (Public Exposure, Data Loss, etc.) to which this policy belongs.
- **Policy Status**: The status (Enabled or Disabled) of the policy.
- [Create a custom policy](/dspm/creating-custom-policies).
- [Apply filters to view specific data](/dspm/using-filters).
- [Add additional filters](/dspm/using-filters).
- [Export and download the report in Excel format](/dspm/about-reports).
- Search for a specific policy.
- [Show or hide the columns](/dspm/using-tables).
- Select any of the following actions:
- **Edit**: [Edit a custom policy](/dspm/managing-policies).
- **Delete**: [Delete a custom policy](/dspm/managing-policies).
- **Enable**: [Enable a policy](/dspm/managing-policies). This option is available only when the policy is disabled.
- **Disable**: [Disable a policy](/dspm/managing-policies). This option is available only when the policy is enabled.
- **Duplicate**: [Clone a policy](/dspm/managing-policies).
-
**Change Severity**: Change the severity level of the policy.
You cannot edit, delete, or change the severity level for predefined policies.
- [Enable or disable the policy](/dspm/managing-policies).
- View the list of policy categories associated with the policy.
- Sort the column data.
- Click the policy name to view additional details. To learn more, see [Viewing Policy Details](/dspm/viewing-policy-details).
-
Select multiple policies to either enable or disable them.
[See image.](#ds-bulk)
![The list of policies and various actions that can be performed on them.](/downloads/dspm/policies/about-data-posture-policies/ds-policypagenew.png)
[]![Enable or disable multiple policies simultaneously](/downloads/dspm/policies/about-data-posture-policies/ds-policy-actions.png)
- []EC2 Instance
- RDS Cluster
- RDS Instance
- S3 Bucket
- SQL Server
- Storage Account
- Virtual Machine