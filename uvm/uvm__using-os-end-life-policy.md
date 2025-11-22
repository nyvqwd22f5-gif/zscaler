# Using the OS End of Life Policy
Source: https://help.zscaler.com/uvm/using-os-end-life-policy
PDF: https://help.zscaler.com/pdf/com/en/1531094.pdf

When [configuring asset compliance policies](/uvm/configuring-asset-compliance-policies) in the Asset Exposure Management (AEM) app, use the OS End of Life policy to track and flag assets running operating systems that have reached or are approaching the end of their supported lifecycle.
The OS End of Life policy uses lifecycle data sourced from the [Endoflife.date](https://endoflife.date/) database to retrieve operating system lifecycle dates. The operating systems currently supported for lifecycle monitoring include:
- [List of Supported Operating Systems](#supported-os-list)
For inquiries about unsupported operating systems, contact your Zscaler Account team.
Asset Population
First, set the policy's Asset Population (i.e., identify the group of assets required to comply with the OS lifecycle guidelines).
For OS End of Life policies, you can narrow the scope to assets that have been active recently and are running a supported operating system. For example, configure the asset population to include assets that were last seen within the last 7 days and the Asset Operating System field is set to Is Not Empty.
[See image.](#os-end-of-life-asset-population)
Policy Scenario
After defining the policy population, configure the conditions that determine when an asset violates the OS End of Life policy. An asset is considered noncompliant if its operating system is past a lifecycle milestone (e.g., end of life) or approaching it within a specific timeframe.
[See image.](#os-end-of-life-policy-scenario)
To configure these conditions, select the lifecycle date relevant to your policy from the drop-down menu:
- **End of Life Date**: The date when the operating system stops receiving updates and security patches.
- **End of Support Date**: The date when technical or customer support for the operating system ends.
- **Extended Support Date**: The date when the extended support period (if available) concludes for the operating system.
After selecting the lifecycle date, specify the compliance condition (i.e., set when you want the policy violation to be generated):
- **Has passed**: Generate a policy violation for assets with an operating system that has already reached the selected lifecycle expiration.
- **Is within the next **<timeframe>**:** Generate a policy violation for assets nearing the lifecycle expiration within a defined timeframe.
Each option targets a specific stage of the operating system lifecycle, requiring a separate policy for accurate monitoring.
- []Ubuntu
- Windows
- Windows Server
- Android
- MacOS
- Debian
- Amazon Linux (including Amazon Linux 2 and Amazon Linux 2023)
- CentOS
- Fedora
[]![OS End of Life Asset Population](/downloads/uvm/asset-exposure-management-aem/settings-aem/using-cmdb-hygiene-policy/aem%20policies%20os%20eol%20asset%20population.png)
[]![OS End of Life Violation Example](/downloads/uvm/asset-exposure-management-aem/settings-aem/using-cmdb-hygiene-policy/aem%20policies%20os%20eol%20policy%20scenario.png)