# Viewing Compliance Security Policy Details
Source: https://help.zscaler.com/zpc/viewing-compliance-security-policy-details
PDF: https://help.zscaler.com/pdf/com/en/1467306.pdf

ZPC displays a slew of information for each compliance security policy it offers. You can view the compliance security policy details by selecting a policy from the [benchmark details](/zpc/viewing-benchmark-details) page.
The Compliance Security Policy Details page (Benchmark details > Policy ID) displays information about each compliance security policy in the following tabs:
- [Policy](#compliance-policy)
- [Compliance](#compliance-details)
- [Audit & Remediation](#compliance-audit-remediation)
- [Assets](#compliance-assets)
[]
The compliance security policy offers information on policy details, who created the policy, and when the policy was created and last modified.
On the **Policy** tab, you can do the following:
- View the following **Policy Details**:
- **Cloud**: The cloud service provider (CSP) the security policy protects.
- **Severity**: Static value signaling the severity of policy failure. The value can be **Critical**, **High**, **Medium**, or **Low**.
- **Asset Types**: The asset types relevant to the compliance security policy.
- **Allow Skip**: Whether the policy is skipped or not. Allow Skip is enabled by default and lets developers skip the policy in their code repository or CI/CD tool by adding skip comments. If it's disabled, the policy cannot be skipped even if the developers add skip comments.
- **State**: Whether the policy is enabled or disabled.
- **Type**: Whether the policy is predefined by ZPC or is a custom security policy.
- **MITRE ATT&CK**: The MITRE ATT&CK ID for the compliance security policy.
- **Policy Description**: The policy description.
- **Recommendations**: View ZPC's recommendations to ensure you are compliant with the policy.
- View the following **Updates**:
- **Created By**: Whether the policy was created by Zscaler or by a ZPC Admin.
- **Created On**: When the policy was created.
- **Last Modified**: When the policy was last updated.
![View the policy tab for compliance policies.](/downloads/zpc/cloud-posture/compliance/viewing-compliance-security-policy-details/zpc-compliance-policy-details-policy-tab.png)
[]
The Compliance tab offers compliance information for the selected security policy.
On the **Compliance** tab, you can view the following compliance details:
- **Compliance**: The compliance benchmark name.
- **Domain**: The compliance benchmark domain.
- **Control Section**: The control section of the compliance benchmark.
![View the compliance tab for compliance policies.](/downloads/zpc/cloud-posture/compliance/viewing-compliance-security-policy-details/zpc-compliance-policy-details-compliance-tab.png)
[]
On the **Audit & Remediation** tab, you can view instruction procedures to audit and remediate the security policy.
![View the audit & remediation tab for compliance policies.](/downloads/zpc/cloud-posture/compliance/viewing-compliance-security-policy-details/zpc-compliance-policy-details-audit-remediation-tab.png)
[]
The Assets tab offers insight into the assets relevant to the selected compliance security policy.
On the **Assets** tab, you can do the following:
- Filter for assets based on **Asset Status**.
- Search for assets using the searchable columns.
- View the following asset details:
- **Asset Name**: View the asset name. Select the asset name to view the asset details. To learn more, see [Viewing Cloud Asset Details](/zpc/viewing-cloud-asset-details).
- **Alert ID**: View the alert ID for the asset. Select the alert ID to view the alert details. To learn more, see [Viewing Alert Details](/zpc/viewing-alert-details).
- **Asset ID**: View the asset ID.
- **Status**: View the asset status.
- Ignore or include an asset. To learn more, see [Configuring a Compliance Ignore Filter](/zpc/configuring-compliance-ignore-filter).
![View the assets tab for compliance policies.](/downloads/zpc/cloud-posture/compliance/viewing-compliance-security-policy-details/zpc-compliance-policy-details-assets-tab.png)