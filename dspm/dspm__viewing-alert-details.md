# Viewing Alert Details
Source: https://help.zscaler.com/dspm/viewing-alert-details
PDF: https://help.zscaler.com/pdf/com/en/1477791.pdf

You can view additional details of alerts such as alerts summary, description, why the alert is in a specific status, etc. This information allows you to investigate the alerts in detail and remediate the issue.
To view the alert details:
- Go to **Alerts** > **Alert Views** > **Alerts**.
- Select the **All Alerts** tab.
-
Click the **Alert ID**.
A drawer appears with the following tabs:
- [Alert Details](#alert-details)
- [Sensitive Data](#sensitive-data)
- [Malware](#malwaretab)
- [Remediation](#remediation)
You can also access the alert drawer from the [Grouped by Policy](/dspm/viewing-alerts-grouped-policy) tab, [Grouped by Resource](/dspm/viewing-alerts-grouped-resource) tab, [Dashboard](/dspm/about-dashboard), and the [Resource Inventory](/dspm/about-resource-inventory) page.
[See image.](#alert-drawer-tabs)
-
Click the **Actions** menu to [snooze, resolve, or reset](/dspm/managing-alerts) the alert.
[See image.](#actionresolve)
[]On the **Alert Details** tab, you can view:
- **Summary**: The [policy](/dspm/about-data-posture-policies) for which the alert was generated.
- **Description**: A brief explanation of what the policy detects.
- **Created Date**: The date and time the alert was created.
- **Last Updated**: The date and time the alert was last updated.
- **Alert Age**: The number of days the alert was in an open state.
-
**MITRE ATT&CK**: The MITRE ATT&CK technique and ID (e.g., **Vulnerability Scanning (T1595)**, **Data Destruction (T1485)**). Click the number to view all the associated MITRE techniques.
[See image.](#mitrenumbers)
- **Policy ID**: The unique identifier of the policy. Click to view the [policy details](/dspm/viewing-policy-details).
- **Policy Severity**: The severity (**Critical**, **High**, **Medium**, or **Low**) of the policy.
-
**Resource Name**: The name of the resource. Click to view [additional details](/dspm/viewing-alerts-grouped-resource) of the resource in the resource drawer.
By default, you are directed to the [Risk Explorer](/dspm/viewing-data-inventory-graph) tab to view the [Resource Inventory](/dspm/viewing-resource-inventory-graph) graph.
- **Policy Category**: The [threat category](/dspm/threat-categories) (e.g., **Data Loss**, **Public Exposure**) to which the policy belongs.
- **Compliance Benchmark**: The compliance benchmark (e.g., **GDPR**, **HIPAA**) associated with the policy. Click the number to view all the associated compliance benchmarks.
- **Compliance Category**: The compliance categories (e.g., **Data Protection (3)**, **Data Recovery (11)**) associated with the policy. Click the number to view all the associated compliance categories.
- The [graphical representation](/dspm/viewing-alert-graph) of the alert.
[See image.](#alert-drawer)
[]On the **Sensitive Data** tab, you can view the details of the [sensitive data](/dspm/viewing-sensitive-data-details) such as the list of files containing sensitive data, the DLP engines used to classify data, etc.
[See image.](#sensitivedatatab)
This tab is visible only when alerts are generated for policies that detect sensitive data in data stores.
[]On the **Remediation** tab, you can view the [remediation steps](dspm/viewing-remediation-details) to resolve the issue in the cloud service provider (CSP).
[See image.](#remediation-tab)
[]On the **Malware** tab, you can view the [malware details](/dspm/viewing-malware-details) detected in your cloud resources, such as file name, file path, malware name, etc.
[See image.](#malwaredetails)
This tab is visible only when alerts are generated for policies that detect malware in data stores.
[]![The alert drawer with Alert Details, Sensitive Data, and Remediation tabs.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-alert-details-drawer_1.png)
[]![The alert drawer with Alert Details, Sensitive Data, and Remediation tabs.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-alert-drawer-tabs.png)
[]![The Remediation tab listing the steps to remediate the selected alert.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-remediation-tab_0.png)
[]![The Actions menu listing resolve and snooze actions.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-alert-drawer-actions.png)
[]![The sensitive data tab listing all the details of the sensitive data associated with the alert.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-alert-drawer-sensitivedata-tab.png)
[]![The malware tab listing all the malware details of the cloud resource.](/downloads/dspm/alerts/alert-details/viewing-alert-details/dspm-viewing-malware-details.png)
[]![List of MITRE techniques with technique ID displayed after clicking on the numbers.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-alert-details/dspm-mitre-numbers.png)