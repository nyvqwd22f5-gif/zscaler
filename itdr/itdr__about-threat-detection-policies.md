# About Threat Detection Policies
Source: https://help.zscaler.com/itdr/about-threat-detection-policies
PDF: https://help.zscaler.com/pdf/com/en/1531680.pdf

The threat detection module actively monitors endpoints in real time to identify identity-based attacks and sends these events to the Zscaler ITDR Admin Portal. It provides visibility into entitlement misuse, credential exposure, and privilege escalation activities in an Active Directory (AD) domain. You can configure threat detection policies and specify a selection criterion to apply to an endpoint. The endpoint agent fetches the threat detection policy from the ITDR Admin Portal and applies it to the endpoints based on the selection criterion.
About the Threat Detection Page
On the Threat Detection page (ITDR > Manage > Threat Detection), you can do the following:
- View a list of threat detection policies. For each policy, you can view:
-
**Name**: The name of the threat detection policy.
Landmine policies in Zscaler Deception that have ITDR Active Directory capabilities enabled are migrated to threat detection policies in ITDR. These policies have a unique ID appended to the policy name. You can [edit](/itdr/managing-endpoint-policy) the name as required.
[See image.](#policy-name)
- **Selection Criterion**: The [selection criterion](/itdr/specifying-selection-criterion) specified for the policy.
- **Policies**: The number of [ITDR attack detection modules](/itdr/configuring-active-directory-threat-detection-module) configured for the policy.
- [Delete selected policies](/itdr/managing-threat-detection-policy).
- [Evaluate policies](/itdr/evaluating-threat-detection-policies).
- [Create a threat detection policy](/itdr/creating-threat-detection-policy).
- [Edit or delete policies](/itdr/managing-threat-detection-policy).
![About the Threat Detection page](/downloads/itdr/threat-detection-policies/about-threat-detection-policies/itdr-manage-threat-detection.png)
[]![The name of a migrated policy in the Threat Detection page](/downloads/itdr/threat-detection-policies/about-threat-detection-policies/itdr-threat-detection-note-new_3.png)