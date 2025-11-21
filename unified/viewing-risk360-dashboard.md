# Viewing the Risk360 Dashboard
Source: https://help.zscaler.com/unified/viewing-risk360-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1526546.pdf

The Risk360 Dashboard (Analytics > Risk360) gives visibility and insight into your organization's risk score, contributed by various underlying factors such as exposed servers, recent malware outbreaks, segmentation posture, and data uploads to risky applications. Zscaler's architecture quantifies these events across 4 major categories, such as exposure of attack surfaces, asset compromise, lateral propagation, and sensitive data loss. You can study how your organization's risk score has changed over time and compare your score against industry peers. Different risk factors bear different weights on the score. For example, an active infection is more severe than a blocked access attempt to a blocked destination.
Dashboard Widgets
- [Organization Risk Score](#org-risk-score)
- [Risk Score Trend](#risk-score-trend)
- [Risk Event by Location](#risk-event-location)
- [Contributing Factors by Entity](#factors-by-entity)
- [Top 10 Factors](#top-10-factors)
- [High Impact Recommendations](#impact-recommendations)
[]The section shows the Zscaler-computed risk score for your organization and the industry peer average risk score. Your organization's risk score is an average risk score across 4 categories, i.e., External Attack Surface, Compromise, Lateral Propagation, and Data Loss. You can study how the risk score has changed over time and compare your score against your industry peers. The following severities appear for the score ranges:
- Low (0–25)
- Medium (26–50)
- High (51–75)
- Critical (76–100)
Hover over the dollar symbol to view the financial risk estimates. You can click **View Details **to further analyze it; you are redirected to the [Financial Risk](/unified/viewing-financial-risk) page.
[See image.](#risk-score)
[]The graph shows the Zscaler-computed and industry peer average risk score trend for the last 90 days. Hover over a point in the graph to view the risk score for that date. You can select to view the risk trend for a specific risk score type by using the checkboxes at the bottom of the graph.
[See image.](#trend)
Click **Key Events** to view significant events that contributed to your risk score in an enlarged view.
- [Enlarged View](#enlarged-view)
[]The map shows a category-based number of risky events from geolocation coordinates derived by looking at the client or server IP. As geo-IP lookups are only possible for a subset of overall risky events, the location visualizations represent a small fraction of overall risky events, but the map view allows you to visualize the geospatial distribution of risky events wherever possible. Hover over a location to view the number of risky events across each category. Use the mouse to drag within the maps or zoom in (+) and out (-). The bottom left of the section shows the top risky locations with the percentage of risky events in descending order.
[See image.](#location)
[]This section shows the total number of contributing factors from each entity. The circle chart shows the segregation across each category affected by these factors:
- **Workforce**: The factors contributing to the risk score due to risky user activity.
- **3rd Parties**: The factors contributing to the risk score due to activities by 3rd-party users (e.g., contract workers).
- **Applications**: The factors contributing to the risk score due to the usage of unsanctioned or less secure SaaS applications.
- **Assets**: The factors contributing to the risk score due to exposed organizational assets.
Hover over the circle chart to view the number of factors from each category and the percentage contribution to the total number of factors in that entity. You can click **View All **to further analyze it; you are redirected to the** **[Factors](/unified/about-factors) page.
[See image.](#entity)
[]View top 10 factors contributing to your organization's risk score. For each factor, you can view the following information:
- **Category**: The category the factor falls under.
- **Factor Name**: The name of the contributing factor affecting the risk score.
- **Your Score**: The score for the contributing factor. The total score for a factor depends on its severity (0 being a healthy score).
- **Last 30 Days**: The graph showing the last 30-day score trend for that factor.
- **Entities**: The entities affected by the factor.
- **Licensed?**: Whether you are subscribed to the required feature to implement the recommended action (**Y** for Yes and **N** for No).
- **Recommended Actions**: The recommended action required to lower the risk score.
You can click **View All **to further analyze it; you are redirected to the** **[Factors](/unified/about-factors) page.
[See image.](#top-factors)
[]The section shows top factors with high impact on your risk score and the recommendation to lower your organization's risk score. Each recommendation consists of the category name, the day it was discovered, the consequence of not implementing the recommendation, and the trend (if applicable). You can click **Explore **to further analyze a particular recommendation or click **View All** to view the list of all the recommended actions; you are redirected to the [Insights](/unified/viewing-risk-insights) page.
[See image.](#recommendations)
[]The **Risk Score Trend** graph shows the top 10 events impacting the risk score. Hover over an event to view the change in the risk score because of the event and the list of contributing [factors](/unified/about-factors) within the event.
The **Top 10 Events** section lists the top 10 events observed within the last 90 days. These events are numbered in the order of their occurrence. Click **View All Events** to go to the [Score Change Logs](/unified/about-risk360-score-change-logs) page, where you can view *all* the events that contributed to the risk score change in detail.
[See image.](#enlarged-view-img)
[]![Enlarged-View](/downloads/risk360/dashboard-analytics/about-dashboard-risk360/Risk360-enlarged-risk-trend-graph.png)
[]![Organization Risk Score Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-risk-score.png)
[]![Risk Score Trend Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-risk-score-trend.png)
[]![Risk Events by Location Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-risk-events-by-location.png)
[]![Contributing Factors by Entity Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-risk-factors-by-entity.png)
[]![Top 10 Factors Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-top-10-factors.png)
[]![High Impact Recommendations Section](/downloads/unified/analytics/unified-dashboards/risk/viewing-risk360-dashboard/Risk360-high-impact-recommendations.png)