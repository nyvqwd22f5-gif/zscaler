# Understanding Original Source and Merged Entity Values
Source: https://help.zscaler.com/uvm/understanding-original-source-and-merged-entity-values
PDF: https://help.zscaler.com/pdf/com/en/1531091.pdf

Some rule setups in the Zscaler Security Operations (SecOps) platform support referencing both the original attribute values from your data sources and the unified values created through [unification](/uvm/what-data-unification). For example, when [creating asset compliance policies](/uvm/configuring-asset-compliance-policies) in Asset Exposure Management (AEM) to maintain an accurate asset inventory, you can check whether critical asset field values are accurate in your Configuration Management Database (CMDB) (e.g., in the ServiceNow CMDB original source).
Referencing original source values is not supported across all rule configuration setups.
The following table describes the difference between the Original Source Value and Merged Entity Value options:
| Field Type | Reference |
| ---------- | --------- |
| Original Source Value | The raw value retrieved from the original source (e.g., ServiceNow CMDB, CrowdStrike Vulnerabilities) prior to any data processing or deduplication |
| Merged Entity Value | The unified SecOps value, often merged from multiple sources |
The following diagram demonstrates how raw data from multiple sources (Original Source Values) is merged into a unified asset with standardized attributes (Merged Entity Values).
![merged vs unified value](/downloads/uvm/asset-exposure-management-aem/settings-aem/configuring-asset-compliance-policies/merged%20vs%20unified%20value.png)