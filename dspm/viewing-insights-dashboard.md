# Viewing the Insights Dashboard
Source: https://help.zscaler.com/dspm/viewing-insights-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1509736.pdf

The Insights dashboard provides an overview of the top issues detected by DSPM across your cloud environment, focusing on sensitive data. You can view potential threats and posture issues at a glance and drill down to view additional details. Similar issues identified across AWS, Azure, and GCP are combined and displayed in each tile. You can see the threat category, total number of alerts, and the overall severity.
DSPM provides the following insights:
[List of Insights](#list-of-predefined-insights)
On the Insights dashboard (Analytics > Insights), you can do the following:
- View the list of issues. Click any tile to view the [list of alerts](/dspm/about-alerts). For each issue, you can see:
- The issue summary.
-
The [threat category](/dspm/understanding-threat-categories) is represented by an icon. Hover over the icon to see the name of the threat category.
[List of icons](#threatcategories)
- The number of [open alerts](/dspm/alert-status).
- The risk level (Critical, High, Medium, or Low) of the issue.
- Apply [filters](/dspm/using-filters) to view specific data.
- Sort issues based on the risk level or number of alerts.
![The Insights dashboard displaying filters and a list of issues identified by DSPM.](/downloads/dspm/analytics/insights/viewing-insights-dashboard/dspm-insights-dashboard.png)
[]![dspm-public-exposure.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-public-exposure.png)
![dspm-data-governance.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-data-governance.png)
![dspm-malicious-access.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-malicious-access.png)
![dspm-data-loss.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-data-loss.png)
![dspm-risky-credentials.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-risky-credentials.png)
![dspm-external-users.png](/downloads/dspm/analytics/insights/about-insights-report/dspm-external-users.png)
| Threat Category | Icon |
| --------------- | ---- |
| Public Exposure |  |
| Data Governance |  |
| Malicious Access |  |
| Data Loss |  |
| Risky Credentials |  |
| External Users |  |
[]
| Insight | Description |
| ------- | ----------- |
| Buckets shared with external accounts/users | Storage buckets that are shared with users or accounts outside the organization. |
| Data stores allowing high privilege access from external accounts | Data stores that can be accessed by users or accounts with high privileges. |
| Data stores containing critical vulnerabilities | Data stores that contain critical or unpatched vulnerabilities that could allow external attack. |
| Publicly exposed sensitive data stores | Data stores containing sensitive data that are publicly exposed, putting the sensitive data at risk for unauthorized access. |
| Sensitive data stores can be accessed by users with risky credentials | Data stores that can be accessed by users with risky credentials, such as unrotated keys, unchanged passwords, weak passwords, etc. |
| Sensitive data stores susceptible to ransomware attack | Data stores that are at risk for ransomware attack |
| Sensitive data stores with no backup | Data stores that do not have backup enabled. |
| Sensitive data stores with partial/no logging | Data stores that have partial logging enabled or that do not have logging enabled. |
| Sensitive data stores with potential data loss | Data stores that lack security controls, which could lead to potential data loss. |
| Sensitive data stores with weak or no data retention policy | Data stores that have either a weak data retention policy configured or there is no data retention policy. |
| Sensitive data stores with weak or no encryption | Data stores that have weak or no encryption enabled. |
| Sensitive data stores with no tags | Data stores that do not have any tags. |
| Sensitive data stores prone to advanced attacks | Data stores containing sensitive data that are prone to advanced attacks. |
| Sensitive data stores accessible by misconfigured AI services | Data stores containing sensitive data that can be accessed by AI services. |