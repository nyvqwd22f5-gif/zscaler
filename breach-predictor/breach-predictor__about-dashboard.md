# About the Dashboard
Source: https://help.zscaler.com/breach-predictor/about-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1518451.pdf

The Zscaler Breach Predictor MITRE ATT&CK  Overview Dashboard is designed as a starting point in the Breach Predictor Portal, providing high-level information about your organization's current risk of a data breach. The Dashboard is divided into two main areas: the Overall Breach Probability score, and the MITRE ATT&CK  Overview charts and graphs. Within the Dashboard, you can use various charts and graphs to better understand your Overall Breach Probability score and to assess your organization’s placement within the MITRE ATT&CK  framework during a specified period.
Breach Predictor’s preemptive vision of security starts with the main Dashboard page, which contains the Overall Breach Probability score, prioritized policy recommendations to triage the biggest threats to your organization, and high-level charts and graphs to give you an instant read on the likelihood of a breach that can exfiltrate your organization's data. The score factors in your organization's placement in the MITRE ATT&CK  matrix, as well as the number of affected users. A higher Overall Breach Probability score indicates a higher risk of a data breach. The Sankey chart gives you quick visibility across users, stages, categories, and threat families.
[See image.](#main-dashboard-page)
If your organization is secured and no users are at risk during the specified time period, Breach Predictor shows a link to the Threat Landscape page so that you can see cutting-edge threat information curated by Zscaler ThreatLabz. The Threat Landscape page provides an overview of the top threats affecting organizations across the globe. To learn more, see [Analyzing Findings](/breach-predictor/analyzing-findings).
[See image.](#no-threats-image)
The Breach Predictor Dashboard provides the following benefits and enables you to:
- See a high-level overview of your organization's current risk of a data breach.
- View your organization's Overall Breach Probability score and a prioritized list of policy recommendations to remediate threats to your organization.
- Use various charts and graphs to understand how various malware threats are affecting your organization.
To learn more, see [Analyzing the Dashboard](/breach-predictor/analyzing-dashboard).
About the MITRE ATT&CK  Overview Dashboard Page
Use the charts and graphs in the Observed Users views on the Dashboard page (Breach Predictor Portal > Dashboard) to see patterns for groups of at-risk users, organized by MITRE ATT&CK  stage, malware category, and malware family. You can click the left and right arrows to toggle between Observed Users views to see the different charts and graphs that are available. Additionally, you can click Explore to open the Findings page to better understand which malware families are impacting your environment. To learn more, see [About the Threat Landscape](/breach-predictor/about-threat-landscape).
- [Observed Users View 1](#observed-users-1)
- [Observed Users View 2](#observed-users-2)
- [Threat Overview](#threat-overview)
[]![The Main Dashboard Page in Zscaler Breach Predictor src=](/downloads/breach-predictor/25.06/ZBP-AboutDashboard-MainDashboardPage.png)
[]![Breach Probability Score with No Threats Identified in Zscaler Breach Predictor](/downloads/breach-predictor/alerts-remediation/analyzing-attack-overview-dashboard/ZBP-Breach_Probability_Score_No_Threats.png)
[]The Sankey chart in the first Observed Users view uses a horizontal layout to present threat activity across users, stages, categories, and malware families.
In the Sankey chart within the Observed Users view 1, you can do the following:
- In the **Users** column, see an overview for the total users in your organization, as well as the number of users at risk of a data breach.
- In the **Stages** column, see the attack stage locations of the malware families affecting your users.
- In the **Category** column, see the classification groups for the malware families affecting your users.
- In the **Malware Family** column, see the names of the malware families affecting your users, as well as the severity score for each family.
![Observed Users View 1 in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-ObservedUsersView1.png)
[]The Sankey chart in the second Observed Users view uses a vertical layout to present threat activity across users, stages, categories, and malware families.
In the Sankey chart within the Observed Users view 2, you can do the following:
- In the **Total Users** column, see an overview for the total users in your organization, as well as the percentage change in users at risk of a data breach.
- In the **Events allowed** row, see the attack stage locations of the malware families affecting your users. Attack stages that have not been reached are not interactive.
- In the **Threat Category** row, see the classification groups for the malware families affecting your users.
- In the bottom row, see the names of the malware families affecting your users, as well as the number of users affected by each family.
![Observed Users View 2 in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-ObservedUsersView2.png)
[]The charts and graphs in the Threat Overview view present even more granular data about the threat families affecting your organization.
In the Sankey chart within the Threat Overview, you can do the following:
- In the **Top Users Impacted By Threats** Sankey chart, see the top users affected by the top malware threat. You can click user names or threat family names to see more detailed information.
- In the **Top Threats Across Attack Stages** radial chart, see the main attack stages for the threats affecting your users. You can click chart data to see more detailed information.
- In the **Allowed Policies over time** bar chart, see main policies that allowed the malware threats affecting your users. You can hover over chart data to see more detailed information.
- In the **Threats over time** bar chart, see the threat families that have affected your users during the selected period. You can hover over chart data to see more detailed information.
![Threat Overview in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-ThreatOverview.png)