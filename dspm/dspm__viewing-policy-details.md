# Viewing the Policy Details
Source: https://help.zscaler.com/dspm/viewing-policy-details
PDF: https://help.zscaler.com/pdf/com/en/1478166.pdf

Data posture policies are queries that looks for vulnerabilties or misconfigurations in the data stores and detect any potential possibilities of a data breach. You can view the details of policies that are used to query data stores in AWS, Azure, and GCP cloud resources. You can see the policy description, the query used to define the policy, remediation steps, and options to disable or clone the policy. To learn more, see [About Data Posture Policies](/dspm/about-data-posture-policies).
To view the policy details:
- Go to **Policy** > **Data Posture Policies**.
-
Click the required **Policy Name**.
[See image.](#ds-ppage)
A drawer appears with the following tabs:
- [Policy Overview](#ds-ptab)
- [Remediation](#ds-rtab)
-
Click the **Actions** menu and choose to disable or clone a policy.
[See image.](#ds-options)
[]On the **Policy Overview** tab, you can view:
- **Policy Details**:
- **Policy Rationale**: A brief explanation about what the policy detects.
-
**MITRE**: The MITRE techniques that are related to the detected issue. Click the number to view all the associated MITRE techniques.
[See image.](#ds-mitre)
- **Policy ID**: The unique identifier for the policy.
- **Policy Category**: The threat category to which the policy belongs.
- **Resource Type**: The type of data store (EC2, Storage Account, RDS Instance, etc.)
- **Compliance Framework**: The list of compliance frameworks that are applicable for this policy.
-
**Policy Query**: The details of the query used to create this policy. You can view the query only for custom policies.
You cannot view policies that are temporarily hidden. [See image.](#policy_with_hidden_query)
[See image.](#ds-overviewtab)
[]On the **Remediation** tab, you can see the remediation steps to resolve the issue detected in the resource.
[See image.](#ds-remedytab)
[]![The policy rationale for an Azure virtual machine](/downloads/dspm/data-posture-policies/viewing-policy-details/ds-policyoverviewtab_0.png)
[]![Remediation steps to resolve the misconfiguration in the Azure virtual machine](/downloads/dspm/data-posture-policies/viewing-policy-details/ds-policy-remediation.png)
[]![Select to disable or clone the policy](/downloads/dspm/data-posture-policies/viewing-policy-details/ds-policypage-actions.png)
[]![Click any policy name to view the policy details](/downloads/dspm/data-posture-policies/viewing-policy-details/ds-policypage.png)
[]![List of MITRE techniques that are applicable for the policy](/downloads/dspm/data-posture-policies/viewing-policy-details/ds-policy-mitre.png)
[]![The Policy Overview tab with information at the end about why a query for the policy is temporarily hidden. ](/downloads/dspm/data-posture-policies/viewing-policy-details/Logica%20policy_new_2.png)