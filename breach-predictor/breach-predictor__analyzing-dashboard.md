# Analyzing the Dashboard
Source: https://help.zscaler.com/breach-predictor/analyzing-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1518481.pdf

The Breach Predictor Dashboard is designed to present the vast amounts of data that Breach Predictor analyzes in an easy-to-understand format so that you have visibility into patterns for the threat activity in your organization. As a result, you're better able to spot trends that are affecting groups of users, instead of focusing on individual user logs. The Dashboard page is meant to be a jumping-off point in the Breach Predictor Portal, providing you a high-level understanding of your organization's overall chances of a security breach.
When you first log in to the Breach Predictor Portal, the Dashboard page is the first thing you see. It consists of the Overall Breach Probability score, prioritized policy recommendations, as well as Observed Users views and a Threat Overview, designed to provide you with an interactive overview of the threats affecting the users in your organization.
To learn more, see [About the Dashboard](/breach-predictor/about-dashboard).
Data about the malware families affecting your organization is divided into two main sub-pages on the Findings page, designed to provide a progressively greater level of detail:
- [Analyzing the Overall Breach Probability Score](#overall-bp-score)
- [Analyzing Data in the Observed Users Views](#observed-users-views)
[]The Overall Breach Probability score is designed to give you an instant read on the likelihood of a breach that can exfiltrate your organization's data. The score factors in your organization's placement in the MITRE ATT&CK  matrix, as well as the number of affected users. A higher Overall Breach Probability score indicates a higher risk of a data breach.
As soon as you've determined your Overall Breach Probability score, you can use the charts on the Dashboard page to examine which malware families are affecting the users in your organization.
[See image.](#bp-score-image)
[]![Overall Breach Probability Score in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-BreachProbabilityScore.png)
[]The Dashboard consists of two Observed Users views and a Threat Overview view, which provide various charts and graphs of the malware threats affecting your organization. You can specify the time frame for the data you see in the Sankey charts and graphs in each of the available views. As a general rule, you should use the following basic order of operations to examine the chart data. As you gather general information, keep in mind that Breach Predictor provides multiple options to [drill down for more information](/breach-predictor/analyzing-mitre-attckr-mapping-report).
- [Analyzing Data in Observed Users View 1](#observed-users-1)
- [Analyzing Data in Observed Users View 2](#observed-users-2)
- [Analyzing Data in the Threat Overview View](#observed-users-3)
[]
- In the first **Observed Users** Sankey chart, observe how many users are at risk vs. the total number of users in your organization.
[See image.](#observed-users-chart)
- From there, you can click each indicated stage to see how each malware family and malware category maps to each stage. Additionally, the listing for each malware family indicates the number of users affected by that family.
[See image.](#sankey-animated-gif)
- Click the arrow next to the **Observed Users** label to open the second **Observed Users** view.
[]![Observed Users View 1 in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ObservedUsersCallout_01.png)
[]![Observed Users View 1 Animated GIF in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ObservedUsersAnimated_01.gif)
[]
- In the second **Observed Users** Sankey chart, observe how many users are at risk in your organization, as well as any trends in the number of affected users.
[See image.](#observed-users-view-2-chart)
- From there, you can click the various data points in the chart to how the stages map to categories, and how categories map to threat families. You can also click the name of a threat family to see the attack path for that family.
[See image.](#sankey-view-2-animated-gif)
- Click the arrow next to the **Observed Users** label to open the third **Observed Users** view.
[]![Observed Users View 2 in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ObservedUsersView02.png)
[]![Observed Users View 2 Animated GIF in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ObservedUsersAnimated_02.gif)
[]
- In the **Threat Overview** view, you see charts and graphs that show more granular detail for the threats affecting your organization.
[See image.](#observed-users-view-3-chart)
- In each of the charts and graphs, you can click or hover your cursor to see details about each data point. You can click the data in the Sankey and radial charts to open more detailed information in other areas of the Breach Predictor Portal.
[See image.](#threat-overview-view-animated-gif)
[]![Observed Users View 3 in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ObservedUsersView03.png)
[]![Threat Overview View Animated GIF in Zscaler Breach Predictor](/downloads/breach-predictor/25.06/ZBP-AnalyzingDashboard_ThreatOvervdiwAnimated.gif)