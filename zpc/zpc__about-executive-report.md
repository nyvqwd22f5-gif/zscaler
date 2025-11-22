# About the Executive Report
Source: https://help.zscaler.com/zpc/about-executive-report
PDF: https://help.zscaler.com/pdf/com/en/1456781.pdf

The Executive Report provides a summary of the assets deployed in your cloud accounts, risks and vulnerabilities associated with the assets, alerts generated for policy violations, open alerts classified by risk level, and much more.
The report is for executives (managers, VPs, etc.) to get a high-level overview of the security posture of the cloud accounts and the progress related to mitigating the security issues (policy violations, misconfigurations, etc.) associated with the accounts.
The executive report provides the following benefits and enable you to:
- Gain visibility into the assets deployed in your cloud accounts.
- View and mitigate the risks and vulnerabilities associated with the assets.
- Customize the report based on the requirements.
You can customize the executive report by changing the data, widget, and graph, for the required organizational units (cloud service providers, cloud accounts, or business units), and share the report in PDF format with the executives.
About the Executive Report Page
On the Executive Report (Analytics > Executive Report) page, you can do the following:
- View the following widgets:
- [Cloud Coverage](#cloud-coverage-widget)
- [Security Posture](#security-posture-widget)
- [Filter the executive report by the following parameters](/zpc/using-filters):
- **Business Units**: Apply this filter to view the report for one or more business units.
- **Clouds: **Apply the filter to view the report for one or multiple cloud service providers.
- **Accounts:** Apply the filter to view the report for one or multiple cloud accounts.
- Click **Customize View** and select the required parameters you want to view.
- [Schedule the report for regular distribution to specified recipients](/zpc/scheduling-executive-report).
- [Save the report that you've customized](/zpc/manage-saved-executive-reports).
- Export the report as a PDF file.
![Executive Reports Dashboard](/downloads/zpc/analytics/about-executive-report/zpc-executive-report-new.png)
- **[]Cloud Identities:** The number of identities during report generation.
- **Vulnerability Workloads Scanned:** The number of cloud workloads scanned for known vulnerabilities.
- **Vulnerability Containers Scanned: **The number of containers scanned within the container registries of the cloud service providers to detect known vulnerabilities.
- **Vulnerability Images Scanned:** The average number of images scanned to detect known vulnerabilities.
- **Assets & Accounts:** Graph that shows the number of onboarded accounts and assets for each cloud service provider.
[See image.](#asset-status)
- **[]Cloud Identities: **The number of [cloud identities](/zpc/about-cloud-identities) (Human, Non-Human).
- **Image Vulnerabilities:** The total number of vulnerabilities detected in the image based on severity (Critical, High, Medium, Low, Unknown).
- **Container Vulnerabilities:** The total number of vulnerabilities detected in the container.
- **Workload Vulnerabilities:** The total number of vulnerabilities detected in the workload based on severity (Critical, High, Medium, Low, Unknown).
- **Asset Status:** The total number of assets along with the status (Passed, Failed). Select the duration for which you want to view the asset status (Last 7 days, Last 15 days, Last 30 days).
[See image.](#assets-accounts)
By default, the status is displayed for the last 7 days.
- **Cloud Alerts:** The number of [Cloud Alerts](/zpc/about-alerts) per day along with the severity (Critical, High, Medium, Low) for the selected duration (Last 7 days, Last 15 days, Last 30 days).
[See image.](#cloud-alerts)
By default, the alerts are displayed for the last 7 days.
- **Open Alerts by Policy: **The total number of open alerts for the specific policy for the selected duration (Last 7 days, Last 15 days, Last 30 days). You can select up to five policies at a time.
[See image.](#open-alerts)
- **Compliance:** The compliance score for the specific benchmark for the selected duration (Last 7 days, Last 15 days, Last 30 days). You can select up to five benchmarks at a time.
[See image.](#compliance)
- **Top 10 Policies by Open Alerts:** The top 10 policies with open alerts. Policies with the highest number of open alerts are displayed first.
- **Top 10 Risky Accounts by Open Alerts:** The top 10 accounts at risk based on the highest number of critical alerts associated with each account.
- **Top 10 Failed Resources:** The top 10 failed resource types (S3, EC2, etc.). The assets with the highest number of failed resource types are displayed first.
- **Top 10 Accounts by Assets:** The top 10 accounts with the highest number of resources.
[![View the Cloud Coverage widget](/downloads/zpc/analytics/about-executive-report/cloud-coverage-ER.png)
]
[![View the Cloud Alerts](/downloads/zpc/analytics/managing-executive-reports/cloud-alerts.png)
]
[![View the Compliance](/downloads/zpc/analytics/about-executive-report/zpc-compliance.png)
]
[![View Open Alerts by Policy](/downloads/zpc/analytics/about-executive-report/zpc-report-policy.png)
]
[![View the Asset status](/downloads/zpc/analytics/viewing-executive-reports/asset-status.png)
]