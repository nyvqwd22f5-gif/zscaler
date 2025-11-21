# Viewing the Scanning Rule Details
Source: https://help.zscaler.com/zpc/viewing-scanning-rule-details
PDF: https://help.zscaler.com/pdf/com/en/1417201.pdf

You can view additional details of the vulnerability scanning rules and the scan schedule.
To view the vulnerability scanning rule details:
- Go to **Cloud Posture > Vulnerability Management**.
- Select the **Scanning Rules** tab.
[See image.](#scanruletab)
- Click the **Scan Rule Name** to view the following details:
- **Rule Details**: The details of that particular scanning rule.
- **Scan Rule Name**: The name of the vulnerability scanning rule.
- **Resource Type**: The type of cloud resource.
- **Scan Type**: The type of cloud storage service (Cloud Container Registries or Cloud Workload) that is being scanned.
- **Cloud**: The name of the cloud platform.
- **Resource Scope**: The resources being scanned.
- **Cloud Accounts**: The accounts that are included for scanning.
- **Cloud Regions**: The regions in which the cloud accounts reside.
- **Tags**: The list of tags associated with the accounts.
For EKS clusters, **Cluster Type** and **Clusters** that are included for scanning are displayed.
- **Scan Schedule**: The details of that particular scan schedule.
- **Occurence**: The scan schedule (Daily, Weekly, or Monthly).
- **Time**: The time when the recent scan was completed.
[See image.](#ruledrawer)
[![Scanning Rules tab](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-scanning-rule-details/zpc-scanrule-tab.png)
]
[![Scan rule drawer](/downloads/zpc/container-registries-workloads/vulnerability-management/viewing-scanning-rule-details/zpc-vm-scanruledrawer.png)
]