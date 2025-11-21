# Using the CMDB Hygiene Policy
Source: https://help.zscaler.com/uvm/using-cmdb-hygiene-policy
PDF: https://help.zscaler.com/pdf/com/en/1531092.pdf

When [configuring asset compliance policies](/uvm/configuring-asset-compliance-policies) in the Asset Exposure Management (AEM) app, use the CMDB Hygiene policy is used to track assets in your CMDB (e.g., ServiceNow CMDB) and alerts on missing or conflicting asset information.
Asset Population
First, set the policy's Asset Population. For CMDB hygiene policies, the asset population typically includes those currently documented in your CMDB. You can further narrow down the scope to a specific subset of assets that you want to monitor for incomplete or inaccurate records.
[See image.](#cmdb-hygiene-asset-population)
Policy Scenario
After defining your policy population, specify what constitutes a violation of the policy. First, identify critical fields in your CMDB (e.g., Asset Owner ID). The two common cases where an asset is considered noncompliant are if it's missing a value, or if it contains conflicting values in these critical fields. Configure a policy to address and flag each scenario separately, as each scenario might require unique scoring settings, violation titles, and violation descriptions.
Missing Field
The Missing Field policy scenario is used to flag assets that lack critical information in your CMDB. For example, flag an asset if it's missing a value in the Asset Owner ID field in your ServiceNow CMDB.
[See image.](#cmdb-hygiene--missing-values)
Conflicting Values
The Conflicting Values policy scenario is used to flag assets that contain conflicting, inconsistent, or inaccurate information (e.g., if an asset contains more than one unique value in the Asset Owner ID field).
When certain values are not indicative of a conflict, you can exclude them from consideration. For example, if an asset's owner ID field is populated with a valid owner name from one source, but with Unknown from another source, you can exclude Unknown to ensure that only genuine data inconsistencies are flagged.
[See image.](#cmdb-hygiene--conflicting-values)
[]![aem policies cmdb hygiene asset population](/downloads/uvm/asset-exposure-management-aem/settings-aem/using-os-end-life-policy/aem%20policies%20cmdb%20hygiene%20asset%20population.png)
[]![aem policies cmdb hygiene policy scenario missing](/downloads/uvm/asset-exposure-management-aem/settings-aem/configuring-asset-compliance-policies/aem%20policies%20cmdb%20hygiene%20policy%20scenario%20missing.png)
[]![aem policies cmdb hygiene policy scenario conflicting](/downloads/uvm/asset-exposure-management-aem/settings-aem/configuring-asset-compliance-policies/aem%20policies%20cmdb%20hygiene%20policy%20scenario%20conflicting.png)