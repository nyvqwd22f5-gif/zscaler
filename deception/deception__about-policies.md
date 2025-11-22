# About Landmine Policies
Source: https://help.zscaler.com/deception/about-policies
PDF: https://help.zscaler.com/pdf/com/en/1531298.pdf

Landmine decoys are configured based on policies. You can add a policy and specify a selection criterion. The policy is applied only if the criterion matches the endpoint. After the selection criterion is specified, you can configure deception modules for the policy (e.g., file decoys, processes, lures, etc.).
Landmine policies provide the following benefits and enable you to:
- Configure custom criteria to deploy landmine decoys only on those endpoints that match the criteria.
- Lure attackers with sophisticated and legitimate-looking decoys, such as file decoys, processes, lures, etc.
Landmine policies are additive, which means you can configure a default policy that applies to all of the endpoints, and then layer specific policies on top of it based on your business use case requirements. The Zscaler Deception Admin Portal evaluates policies for each endpoint and deploys the applicable decoys. For a complete list of ranges and limits per landmine policy feature, see [Ranges & Limitations](/deception/ranges-and-limitations).
For example, assume that you have configured landmine policies as follows:
| Policy Name | Selection Criterion | Deception Modules |
| ----------- | ------------------- | ----------------- |
| John | User = john | A file decoy (password.xlsx) |
| Laptop | Hostname = laptop-1 | A decoy Chrome credential (webmail02) |
| Default | Catch All | A decoy process (mcafee.exe) |
The decoys that are deployed on endpoints are as follows:
| User | Hostname | Applicable Policies | Deception Modules Deployed on Endpoints |
| ---- | -------- | ------------------- | --------------------------------------- |
| bob | desktop-1 | Default | A decoy process (mcafee.exe) |
| bob | laptop-1 | Default and Laptop | A decoy process (mcafee.exe) and decoy Chrome credential (webmail02) |
| john | desktop-1 | Default and John | A decoy process (mcafee.exe) and file decoy (password.xlsx) |
| john | laptop-1 | Default, John, and Laptop | A decoy process (mcafee.exe), file decoy (password.xlsx), and decoy Chrome credential (webmail02) |
After a landmine policy is configured, it is displayed on the Policies page.
About the Landmine Policies Page
On the Policies page (Deceive > Landmine > Policies), you can do the following:
- View a list of landmine policies. For each policy, you can view:
- **Name**: The name of the landmine policy.
- **Agentless**: A filter to view agentless policies. The options are **All **(default),** True**, and **False**. The **X** icon indicates that the policy applies to a full agent variant of the landmine, and the check mark icon (![Check mark icon on the Policies page](/downloads/deception/product-documentation/deceive/endpoint-decoys/policies/about-policies/zscaler_deception-check-mark-icon-policy.png)
) indicates that the policy applies to the agentless variant of the landmine.
- **Selection Criteria**: The [selection criterion](/deception/creating-landmine-policy) specified for the policy.
- **Policies**: The various deception modules configured for the policy.
- [Delete selected landmine policies](/deception/managing-landmine-policies).
- [Evaluate policies](/deception/evaluating-landmine-policies).
- [Create landmine policies](/deception/creating-landmine-policy).
- [Manage policies](/deception/managing-landmine-policies).
![About the Landmine Policies Page](/downloads/deception/deceive/landmine-decoys/policies/about-policies/deception-landmine-policy-about-page.png)