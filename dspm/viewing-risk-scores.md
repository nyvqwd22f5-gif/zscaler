# Viewing the Risk Scores
Source: https://help.zscaler.com/dspm/viewing-risk-scores
PDF: https://help.zscaler.com/pdf/com/en/1524376.pdf

Risk score is a numerical assessment to quantify your organization's security posture based on the vulnerabilities and threats detected in your cloud infrastructure. DSPM scans your cloud accounts for sensitive data and vulnerabilities, and presents the results along with other multiple security findings by severity. It also calculates the risk score and displays the details on the dashboard. This data helps you to prioritize the findings based on the severity of the risk and fix the issues immediately to protect the sensitive data.
Widgets
You can see the following widgets on the Risk tab. You can apply filters to view specific data by business units, accounts, clouds, accounts, and regions.
- [Risk Score](#ds-riskscorechart)
- [Risk Score Trend](#ds-risktrend)
- [Top Risk Data Stores](#ds-topdstores)
- [Open Alerts by Category](#ds-openalertschart)
![View the statistics for the overall risk score and trend on the dashboard](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-risk-scores-0/ds-risk.png)
[]View the overall risk score and the risk score range. A risk score is calculated based on multiple entities in the system (alerts, data stores containing sensitive data, etc.) and it shows the level of [security risk](/dspm/understanding-security-risk) associated with data stores. The overall risk score is calculated by aggregating the risk scores of all data stores. Hover over the **Info **icon to see the details. [See image.](#ds-riskscore-info)
[]View the chart that displays the changes in risk score trend over a specific period of 7, 15, 30, 60, and 90 days.
[]View the top 8 risky data stores along with the open alerts ranked by severity level.
- Click **See All** to view the resource details on the [Resource Inventory page](/dspm/about-resource-inventory).
- Click the arrow next to the resource name to see the impact, likelihood, and the alert descriptions. [See image.](#ds-riskimpact)
- Click the **Resource Name** to view the [Resource Inventory graph](/dspm/viewing-resource-inventory-graph).
- Click the** Alerts** to view the [alert details](/dspm/about-alerts).
[]View the total number of alerts generated for each [threat category](/dspm/threat-categories). Move the mouse over the bars in the graph to see the total number of alerts by severity. [See image.](#ds-alertsbyseverity) You can sort the data by **Total Alerts**,** Category Name**, and **Most Critical** alerts.
[]![The files that are highly impacted and the likelihood of the risks due to the impact](/downloads/dspm/dashboard/about-dashboard/ds-dboard-datastoredetails.png)
[]![The total numbers of alerts by severity](/downloads/dspm/dashboard/about-dashboard/ds-dboard-threatcategory.png)
[]
![View the risk score details](/downloads/tech-pubs-drafts/dspm-draft-articles/1-12-0-viewing-risk-scores-0/ds-risk%20score.png)