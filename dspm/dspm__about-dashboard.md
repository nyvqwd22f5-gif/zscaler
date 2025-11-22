# About the Dashboard
Source: https://help.zscaler.com/dspm/about-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1477746.pdf

The DSPM dashboard provides a high-level overview of your cloud accounts' data security posture. The dashboard includes interactive widgets, graphs, and charts that visually depict the number of resources that are scanned, sensitive data discovered, types of sensitive data, overall risk score for the data stores, number of DLP engines and dictionaries used to classify the sensitive data, geographic location of your cloud accounts along with the resources that contain the maximum amount of sensitive data, the severity of risk associated with the data, the number of alerts generated for each resource, etc. You can view the list of resources that are at high risk along with the total number of alerts generated for these resources. All of this data helps you prioritize and take the necessary action. From the dashboard, you can go to other pages (Alerts, Policies, Resource Inventory, etc.) to gather more context and information for further analysis. [See image.](#dashboard_gif)
When you log in and access the dashboard, you might see a notification about configuration issues while [onboarding cloud accounts](/dspm/about-cloud-accounts). This prevents DSPM from accessing the cloud accounts for scanning. Go to the [Cloud Accounts page](/dspm/resolving-onboarding-issues) to investigate and resolve the issues. [See image.](#config_issue)
The DSPM dashboard provides the following benefits and enables you to:
- Gather information about the sensitive data stored in your cloud resources (data stores).
- View the overall risk score for data stores and the risk score trend.
- View the geographic locations where the sensitive data is stored.
- View the DLP engines and dictionaries used to classify sensitive data.
- View the document types containing sensitive data.
- View the top resources that are at high risk.
- View the total number of alerts generated for each threat category.
The dashboard displays detailed information on the following tabs:
Risk
DSPM calculates the overall risk associated with the data stores along with the risk score trend and other granular details. To learn more, see [Viewing the Risk Scores](/dspm/viewing-risk-scores).
[See image.](#ds-db-risktab)
Data Discovery
The total amount of data that is discovered and scanned along with the sensitive data details. To learn more, see [Viewing the Statistics for Scanned Data](/dspm/viewing-statistics-scanned-data).
[See image.](#ds-db-ddtab)
AI Security
AI services and models that have access to resources containing sensitive data. To learn more, see [Viewing the Statistics for AI Service Details.](/dspm/viewing-the-statistics-for-ai-service-details)
[See image.](#ds-aisecuritytab)
[]
![Shows the AI services and models that access sensitive data.](/downloads/dspm/dashboard/about-dashboard/ds-ai-security.png)
[]
![The Risk tab shows the risk scores and alert details](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-dashboard/ds-risk.png)
[]
![The total amount of data scanned and details of the sensitive records](/downloads/dspm/dashboard/about-dashboard/ds-data-discovery.png)
[]![Configuration issue](/downloads/tech-pubs-drafts/dspm-draft-articles/about-dashboard-draft-0/Config%20Image_0.png)
[]![Viewing all the interactive elements on the dashboard](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-about-dashboard/ds-dspm-dashboard.gif)