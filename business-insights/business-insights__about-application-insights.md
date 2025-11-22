# About Application Insights
Source: https://help.zscaler.com/business-insights/about-application-insights
PDF: https://help.zscaler.com/pdf/com/en/1473191.pdf

Application Insights provides a holistic overview of the applications that are currently being used across your organization. The page can be interactively used to switch between the data and metrics for discovered applications, overlapping applications, and cost savings for each application.
Application Insights provides the following benefits and enables you to:
- Analyze application data for their usage, active and inactive users, and costs, among many other vital metrics.
- View applications with similar capabilities and the number of overlapping users for them to help you streamline apps for your users.
- Analyze the applications' efficiency matrix to help you save costs by removing unwanted licenses and applications.
About the Applications Insights Page
The Applications Insights page (Applications > Applications Insights) is divided into three tabs:
- [Discovered Apps](#discovered-apps)
- [Overlapping Apps](#overlapping-apps)
- [Cost Savings](#cost-savings)
[]The Discovered Apps page (Applications > Applications Insights> Discovered Apps) shows data about applications whose usage is discovered within your organization. On this page, you can do the following:
- View the **Discovered Applications Trend** graph that shows the trend for the number of high- and low-usage applications, along with the number of newly discovered applications for the last 12 months. Hover over the graph to view the data for each month. High-usage apps have over 80% active users for the month compared to the total number of active users. Low-usage apps have less than 30% active users for the month compared to the total number of active users.
- Click **View All **to go to the All Applications page, where you can view the complete list of applications currently being used within your organization.
- Click **Connect App **to onboard applications with Business Insights that have connector integration support. To learn more, see [Onboarding SaaS Apps for Insights](/business-insights/onboarding-saas-apps-business-insights).
- []View a list of the top 10 discovered applications. For each application, you can view:
- **Application**: The name of the application. Click on the application to go to the [Viewing Applications Details](/business-insights/viewing-application-details) page, where you can view the application-specific metrics.
- **Capability**: The various capabilities offered by the application. For example, Okta's capabilities include identity management, access control, two-factor authentication, etc.
- **Active Users (last 30 days)**: The number of active users in the last 30 days.
- **Engagement Index**: The percentage of active users in the last 30 days over the last 90 days for an app. For example, if you have 50 active users in the last 30 days and 100 in the last 90 days for Box, the engagement index is calculated by dividing the number of active users in the last 30 days by the number of active users in the last 90 days, and multiplying it by 100 (i.e., [50÷100]×100 = 50%).
- **Growth Trend**: The percentage increase or decrease in user activity for every 30 days. For example, if you have 50 active users in the last 30 days but 100 active users before the last 30 days, the growth trend is calculated by dividing the increase or decrease in the number of active users by the number of active users before the last 30 days, and multiplying it by 100 ([100−50]÷100×100 = decrease of 50%).
-
**Data Source**: The source from where the application usage is discovered (i.e., identity provider (IdP), Zscaler Internet Access (ZIA), by connector integration, or custom application signature such as **IDP**, **ZIA**, **CONNECTOR**,** CUSTOM ZIA**).
Business Insights discovers app usage via your IdP, ZIA traffic, custom apps, and direct connector configurations. Hence, you might see multiple entries for the same application tenant with different **Data Source** values.
- **Spend**: The total spent on the application by your organization.
- **Sanctioned**: Whether the application's use is sanctioned or not in your organization.
- **Contract Start Date**: The date when the application subscription commenced.
- **Action**: The actions available for the application.
- [Modify the table and its columns](/business-insights/using-tables-business-insights).
- [Edit the subscription details for an application](/business-insights/viewing-application-details#plan).
- [Onboard the application to Business Insights](/business-insights/onboarding-saas-apps-business-insights). If you select an application that has connector integration support, the configuration page shows two options: either configure an application connector, or skip the connector configuration to set up the application subscription details and use the insights provided by other data sources (IdP or ZIA).
![Discovered Apps](/downloads/business-insights/application-insights/viewing-application-details/Business-Insights-Discovered-Apps_0.png)
[]The Overlapping Apps page (Applications > Applications Insights > Overlapping Apps) shows overlapping application usage based on the application capabilities. For example, Zoom and Webex have similar capabilities. However, users in your organization might be using either or both. On this page, you can do the following:
-
Switch the data view between capability cards or tabular format.
[See image.](#card-view)
- Search for a specific app or capability.
- View a list of all the application capabilities. For each category, you can view:
- **Capability**: The name of the capability.
- **Overlapping Users**: The number of overlapping users who are using at least one of the applications listed for the capability.
- **Applications**: The applications that are currently being used within your organization with similar capabilities.
- Click the arrow icon of a capability to go to the [Application Overlap Details](/business-insights/viewing-application-overlap-details) page, where you can view capability-specific metrics.
![Overlapping Apps](/downloads/business-insights/application-insights/viewing-application-details/Business-Insights-Overlapping-Apps.png)
[]![Switching View in Overlapping Apps Page](/downloads/business-insights/application-insights/viewing-application-details/Business-Insights-Overlapping-Apps-Switching-Views.gif)
[]The Cost Savings page (Applications > Applications Insights > Cost Savings) shows the opportunity to save money from each app. By default, when you use the service initially, applications have an estimated cost populated for them until you enter or edit the costs for the apps. The Zscaler-estimated costs (**Spend**) are underlined. These estimates are conservative and take into account the premium solutions of the SaaS providers (i.e., enterprise) with over 50% discounts, and also take the deployment scale into consideration. The greater the deployment scale, the greater the discount. On this page, you can do the following:
- View the **SaaS Efficiency Matrix **graph that shows the applications placement based on the license usage percentage and its expense to your organization, and indicates applications with greater savings opportunities in the bottom right of the graph. Hover over an application to view its cost and usage percentage.
- View a list **Top 50 Cost Savings Applications**. For each application, you can view:
- **Application**: The name of the application
- **Cost Savings**:** **The cost-saving opportunity for the application by removing inactive users from the application. Cost savings for Zscaler-estimated costs are indicated with an asterisk (*).
- **Spend**: The total amount spent on the application subscription in US dollars.
- **Data** **Source**: The source from where the application usage is discovered (i.e., IdP, ZIA traffic, or connector integration such as **IDP**, **ZIA**, or **CONNECTOR**).
- **Active Users**: The number of active users for the application.
- **Inactive Users**: The number of inactive users for the application.
- **Action**: The actions available for the application.
- [Edit the subscription details for an application](/business-insights/viewing-application-details#plan).
- [Onboard the application to Business Insights](/business-insights/onboarding-saas-apps-business-insights). If you select an application that has connector integration support, the configuration page shows two options: either configure an application connector, or skip the connector configuration to set up the application subscription details and use the insights provided by other data sources (IdP or ZIA).
- Click on an application to go to the [Applications Details](/business-insights/viewing-application-details) page.
![Cost Saving in the Inventory Page](/downloads/business-insights/application-insights/about-application-inventory/Bussiness-Cost-saving-app.png)