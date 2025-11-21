# Viewing Alert Details
Source: https://help.zscaler.com/zpc/viewing-alert-details
PDF: https://help.zscaler.com/pdf/com/en/1433926.pdf

Alert drawers provide additional information related to the alerts, such as metadata, security policies, asset properties and tags, compliance benchmarks, remediation procedures, and much more. This information enables you to get detailed insight into the alerts for investigation and remediation.
To view the alert details:
- In the left-side navigation, select **Alerts**.
- On the **Alerts** page, click the **Cloud Alerts** or **IaC Alerts** tab.
[See image.](#alerttabs)
- Click any **Alert ID** to view:
- [Cloud Alert Details](#viewing-alert-clouddetails)
- [IaC Alert Details](#viewing-alert-iacdetails)
[]The Cloud Alert drawer has the following tabs:
- **Properties**: View the alert and policy details, and the metadata.
- Click the identity name to view the [cloud identity details](/zpc/viewing-cloud-identity-details) or click the resource name to view the [cloud asset details](/zpc/viewing-cloud-asset-details).
- Click the ID to view the [security policy details](/zpc/viewing-security-policy-details).
If an alert is associated with a [trusted IP list](/zpc/about-trusted-ips), a link is provided against the trusted IP attribute to navigate to the associated trusted IP list on the Trusted IP Management page. [See image.](#trusted-ip-link)
[See image.](#alert-properties)
- **Timeline**: View the history of the alert that includes the following details:
- The timestamp for when the alert was created.
- The timestamp for when the alert status was updated.
- The description of the action that triggered the alert status change.
- The ZPC user who performed the action on the alert.
The alert data is captured every 5 minutes. By default, the alert history is displayed for the last month. You can export the alert data as an Excel file and [download the report](/zpc/downloading-reports). You can also [filter the data](/zpc/using-filters) to focus on specific information.
[See image.](#alert-timeline-tab)
- **Remediation**: View the remediation procedure, recommendations, and audit procedure.
[See image.](#remediation)
- **Compliance**: View the [compliance](/zpc/about-compliance) benchmark name, type, version, domain, and control number.
[See image.](#compliance)
- **Tags**: View the resource name and key-value pairs.
[See image.](#tags-tab)
[See image.](#alert-tabs)
For a detailed description of each attribute, see [Alert Attributes](/zpc/alert-attributes).
[]The IaC Alert drawer has the following tabs:
- **Alert Details**: View the alert data, IaC repository data, and the violating resource. Click **View Code** to see the lines of code in the resource. [See image.](#iaccode)
Some repository details are not displayed for Jenkins Pipeline scans due to a limitation in processing.
- **Remediation**: View the remediation and audit procedure.
[See image.](#iac-details)
For a detailed description of each attribute, see [Alert Attributes](/zpc/alert-attributes).
[![View the IaC alerts drawer](/downloads/zpc/alerts/viewing-alert-details/zpc-iacalert-drawer.png)
]
[![IaC code](/downloads/zpc/alerts/viewing-alert-details/zpc-iaccode.png)
]
[![View the Alert Properties](/downloads/tech-pubs-drafts/zpc-draft-articles/draft-about-alert-rules/zpc-alert-properties-tab.png)
]
[![Select the Cloud Alerts or IaC Alerts tab](/downloads/zpc/alerts/alert-details/viewing-alert-details/zpc-alert-tabs.png)
]
[![View the Alert Timeline tab](/downloads/zpc/alerts/alert-details/viewing-cloud-alerts-grouped-policy/zpc-cloud-alerts-timeline-tab.png)
]
[![View the Alerts Compliance tab](/downloads/tech-pubs-drafts/zpc-draft-articles/viewing-alert-details/zpc-alerts-compliance-tab.png)
]
[![View the Alerts Remediation tab](/downloads/tech-pubs-drafts/zpc-draft-articles/viewing-alert-details/zpc-alerts-remediation-tab.png)
]
[![View the Cloud Alert drawer](/downloads/tech-pubs-drafts/zpc-draft-articles/draft-about-alert-rules/zpc-cloud-alert-tabs.png)
]
[![View the Alert Tags tab](/downloads/tech-pubs-drafts/zpc-draft-articles/viewing-alert-details/zpc-alert-tags.png)
]
[![View the Trusted IP Management page](/downloads/zpc/alerts/alert-details/viewing-alert-details/zpc-alerts-trusted-ip-link.gif)
]