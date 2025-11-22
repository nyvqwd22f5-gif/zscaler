# Using the Tool Coverage Policy
Source: https://help.zscaler.com/uvm/using-tool-coverage-policy
PDF: https://help.zscaler.com/pdf/com/en/1531093.pdf

When [configuring asset compliance policies](/uvm/configuring-asset-compliance-policies) in the Asset Exposure Management (AEM) app, use the Tool Coverage policy to monitor critical security tool coverage (e.g., Zscaler Client Connector or CrowdStrike EDR) and generate violations for noncompliant assets.
Asset Population
First, set the policy's Asset Population (i.e., identify the group of assets that are required to have a particular tool installed).
For example, when creating a policy for an EDR tool, you can narrow down your asset population to include only Workstations and Servers, and thus exclude Cloud assets which are not expected to have EDR. You can also exclude old or decommissioned assets that are not expected to be covered by an EDR tool, by narrowing the asset population down to assets that have been seen in the last 14 days.
Schematically, you're looking for assets that were last seen in the last 14 days AND Asset Types that contain Workstation OR Server.
[See image.](#tool-coverage-asset-population)
Policy Scenario
After defining your policy population, specify what constitutes a violation of the policy. For tool coverage policies, an asset is considered noncompliant if it's not covered by a critical tool in your environment. This generates a policy violation that you can then track and remediate.
Using the Tool Coverage policy template, configure the following conditions:
- Specify the source that should have covered the asset (e.g., CrowdStrike Vulnerabilities for tracking CrowdStrike EDR coverage), within a certain number of days (e.g., last 14 days).
-
Specify a field that indicates lack of coverage (e.g., the Asset Has EDR field returns FALSE).
[See image.](#tool-coverage-policy-scenario)
For more complex policy scenarios not supported by the template, use the Advanced policy scenario setup to define custom conditions.
[]![aem policies tool coverage asset population](/downloads/uvm/asset-exposure-management-aem/settings-aem/configuring-asset-compliance-policies/aem%20policies%20tool%20coverage%20asset%20population.png)
[]![aem policies tool coverage policy scenario](/downloads/uvm/asset-exposure-management-aem/settings-aem/configuring-asset-compliance-policies/aem%20policies%20tool%20coverage%20policy%20scenario.png)