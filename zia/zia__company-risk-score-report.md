# About the Company Risk Score Report
Source: https://help.zscaler.com/zia/company-risk-score-report
PDF: https://help.zscaler.com/pdf/com/en/1400691.pdf

The Company Risk Score Report allows organizations to monitor and assess their organizational, location, and user-level risk exposure. The report analyzes the various factors that contribute to an organization's risk score, which can include recent malware outbreaks, risky user behavior, and other suspicious factors. Administrators can study how their users' and company's risk score has changed over time and compare their score against their industry peer and Zscaler cloud averages.
Risk scores are calculated for each user, location, and company. Each user's behavior is analyzed against three groups of risk factors: pre-infection behavior (e.g., blocked access to malicious destinations or content), post-infection behavior (beaconing or command, and control communications), and suspicious behavior (e.g., data leak policy blocks). Risky behavior has an effect on the score for up to 7 days from occurrence. Different risk factors also bear different weights on the score. For example, an active infection is more severe than a blocked access attempt to a blocked destination. Unauthenticated users are excluded from calculations since transactions can't be associated with an identity.
Applicable Conditions When Accessing the Company Risk Score Report
The following conditions apply when accessing the Company Risk Score report:
- Risk scores are calculated only for organizations with Advanced Threat Protection (Available in the ZIA Business bundle and higher or sold separately).
- Risk scores are calculated on a 7-day moving window of risk events.
- For a risk score to be calculated, there needs to be at least 100 "risky" users in the 7-day window. If there aren't at least 100 authenticated users in the organization, each of whom had at least one "risky" transaction within that window, then the risk score isn't computed for that day.
- The risk score is not calculated for a duration when the total percentile of risky users is less than 1 percentile of the total risky users.
- When there is insufficient user activity in a given day, the company risk score is recorded as "0".
- A daily company risk score of "0" is included in the running company risk score calculation, resulting in a reduction of the company risk score value.
- We're continuously refining the algorithms used to calculate your Company Risk Score and to make the report more useful to you.
Company Risk Score Report provides the following benefits and enables you to:
- Configure stronger policies by monitoring your organization, location, and user-level risk exposure.
- Study users' and company's risk scores change over time to determine the effectiveness of various policy configurations.
- Compare the risk scores against your industry peers and Zscaler cloud averages to understand your position against potential attacks.
About the Company Risk Score Report Page
On the Company Risk Score Report page (Analytics > Company Risk Score), you can view the following widgets:
- **Your Risk Score Trend**: This graph displays your risk score during a span of 7, 15, and 30 days. The trend isn't computed if there is a low number of authenticated users.
- **Current Risk Score**: Your organization’s risk score, your industry vertical's average risk score, and the average risk score of all organizations. You can filter the graph by the following individual events or all of them:
- Low (0–25)
- Medium (26–50)
- High (51–75)
- Critical (76–100)
- **Events Contributing to the Risk Score**: This graph displays the events that contributed to the risk score during a span of 7, 15, and 30 days. You can filter the graph for all events or individual events such as:
- **Active Infections**: Shows transactions that are suspected botnet callbacks.
- **Suspicious Activity**: Shows transactions that are potentially malicious.
- **Threats Blocked**: Shows transactions blocked because they are more likely to result in an infection.
- **Events Contributing to Current Risk Score**: This graph displays the events that contributed to your current risk score.
- **Top Advanced Threats Trend**: This graph displays the top advanced threats during a span of 7, 15, and 30 days.
- **Top Advanced Threats**: This graph displays the current top advanced threats in percentages.
- **Distribution of Your User Risk Scores**: This graph displays the percentage distribution of the risk scores for your authenticated users.
- **Distribution of Risk Scores for Your Industry**: This graph displays your risk score and the percentage of organizations with the same score in your industry vertical. The **Show Summary **option reveals the percentage of peer organizations with higher risk scores than yours.
- **Distribution of Risk Scores for All Orgs**: This graph displays your risk score and the percentage of all cloud organizations with the same score. The **Show Summary **option reveals the percentage of cloud organizations with higher risk scores than yours.
- **Top Risky Users**: The top risky users in your organization. Conduct further investigation of their activity. Click on a user, and you are redirected to the [User Risk Report](/zia/user-risk-report) page.
- **Top Risky Locations**: The top risky locations based on transactions by authenticated users. Conduct further investigation to ensure that all your users remain secure. This section won't be computed if there is a low number of authenticated users.
- **Top Locations with Unauthenticated Transactions**: The risk score is computed based on authenticated user traffic. These locations have a high number of unauthenticated transactions and cannot have a risk score computed.
![This image displays the Company Risk Score Report.](/downloads/zia/dashboard-analytics/reports/company-risk-score-report/Company_risk_score_report.png)