# Understanding Business Insights Terminology
Source: https://help.zscaler.com/business-insights/understanding-business-insights-terminology
PDF: https://help.zscaler.com/pdf/com/en/1473086.pdf

This article lists Business Insights terms and their definitions to help you understand and interpret the metrics with the intended context and perspective.
Application Insights Terms
The following terms apply to Application Insights:
- **Active Users**: The number of active users for an app in the last 30 days. Active users have accessed or used the app at least once in the last 30 days.
- **Application Connector**: An application connector integrates with the SaaS provider to collect license and usage information for the app. Configuring a connector involves providing information to call the provider's APIs. To learn more, see [Onboarding SaaS Apps for Business Insights](/business-insights/onboarding-saas-apps-business-insights).
- []**Supported Apps**: Application connectors for supported apps can be configured in the Business Insights Admin Portal. With a connector configured, the insights for an app are more detailed. Currently, Business Insights supports connector integration for Okta, M365, Salesforce, ServiceNow, Slack, Box, Google, and GitHub.
- **Purchased Seats**: The number of seats purchased within a subscription plan. One seat is assigned to one user.
- **Assigned Seats**: The number of seats assigned to users from the purchased seats.
- **Data Source**: The source from where the application usage is discovered. Business Insights receives signals and data from 4 data sources: the Zscaler Internet Access (ZIA) service that acts as one of the input feeders, identity providers (IdPs) like Okta and Entra ID, SaaS application connector integrations (supported for apps such as Okta, M365, Salesforce, ServiceNow, Slack, Box, Google, and GitHub), and [custom application signatures](/business-insights/about-application-configuration).
- **Discovered Apps**: Apps whose usage is discovered within your organization's traffic. Zscaler can discover the usage of over 30K apps.
- []**Engagement Index**: This metric shows the application's engagement percentage. This calculation varies based on the following metadata availability:
- Without [Plan Details](/business-insights/viewing-application-details#plan): The percentage of active users in the last 30 days over the last 90 days for an app. For example, suppose you have 50 active users in the last 30 days and 100 in the last 90 days for Box. In that case, the engagement index is calculated by dividing the number of active users in the last 30 days by the number of active users in the last 90 days, and multiplying it by 100 (i.e., [50÷100]×100 = 50%).
- With [Plan Details](/business-insights/viewing-application-details#plan): The percentage of active users in the last 30 days over the number of purchased seats for an app. For example, suppose you have 50 active users in the last 30 days and 100 purchased seats for Box. In that case, the engagement index is calculated by dividing the number of active users in the last 30 days by the number of purchased seats, and multiplying it by 100 (i.e., [50÷100]×100 = 50%). If the data of the purchased seats is unavailable, the service replaces it with the number of assigned seats. If both the data are unavailable, the service defaults to the preceding calculation performed for apps without plan details. If multiple plans exist, the service shows the data for the plan with the lowest engagement index.
- []**Growth Trend**: The percentage increase or decrease in user activity for every 30 days. For example, if you have 50 active users in the last 30 days but 100 active users before the last 30 days, the growth trend is calculated by dividing the increase or decrease in the number of active users by the number of active users before the last 30 days, and multiplying it by 100 ([100−50]÷100×100 = decrease of 50%).
- **Capability**: An app capability is the service that it provides for its users. For example, **Video Conferencing **is a capability provided by Zoom and Webex.
- **Overlapping Apps**: Users using multiple apps with similar capabilities. For example, the usage of Slack and Microsoft Teams within your organization that have similar capabilities.
- **High Usage Apps:** Apps with over 80% active users for the month compared to the total number of active users.
- **Low Usage Apps:** Apps with less than 30% active users for the month compared to the total number of active users.
Workplace Insights Terms
The following terms apply to Workplace Insights:
- **Workplaces**: An organization's traffic ingress and egress points. There are two types of workplaces:
- **Inferred Locations**: These are individual [ZIA locations](/zia/about-locations) configured in the ZIA Admin Portal (a ZIA location can also consist of sub-locations) and inferred IP addresses that the Business Insights service concludes as the organization's workplace based on the amount of traffic, the number of users behind the IP address, and more assuring metrics.
- **Configured Offices**: These are the grouping of inferred locations into a configured office with metadata. To learn more, see [About Configured Offices](/business-insights/about-configured-offices).
- **Assigned Headcount**: The number of users assigned to an office.
- **Capacity**: The number of employees the office can accommodate.
- **Average Attendance**: The average attendance for an office site is calculated by dividing the total number of visits to the workplace by the total number of assigned headcount for the workplace, then multiplying it by 100.
- **Average Occupancy**: The average occupancy for a workplace is calculated by dividing the total number of visits to the workplace by the site capacity, then multiplying it by 100.