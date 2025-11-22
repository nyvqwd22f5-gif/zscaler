# About All Applications
Source: https://help.zscaler.com/business-insights/about-all-applications
PDF: https://help.zscaler.com/pdf/com/en/1473246.pdf

The All Applications page shows the list of apps whose usage is discovered within your organization. The list includes discovery from all the data sources like identity providers (IdPs), Zscaler Internet Access (ZIA) traffic, connector integrations, and custom application signatures.
The All Applications page provides the following benefits and enables you to:
- View all the apps whose usage is discovered within your organization.
- Analyze application data for their engagement index, growth trends, and capability, among many other vital metrics.
- [Onboard applications](/business-insights/onboarding-saas-apps-business-insights) to view richer business insights for them.
About the All Applications Page
On the All Applications page (Applications > All Applications), you can do the following:
- Filter the data for specific parameters.
- [View available filters.](#fitlers)
- Download the data on the page as a CSV file.
- Search the data for a specific application.
- View a list of discovered applications.
- [View elements for each application.](#columns-fields)
- [Modify the table and its columns](/business-insights/using-tables-business-insights).
- [Edit the subscription information for the app](/business-insights/viewing-application-details#plan).
- [Onboard an app to Business Insights](/business-insights/onboarding-saas-apps-business-insights).
Use the arrows at the bottom of the page to go to the next page. You can also select the number of entries you want to view on a page (15, 50, or 100 rows).
![All Applications Page](/downloads/business-insights/application-insights/about-all-applications/Business-Insights-All-Applications-Page_2.png)
- []Capability
- Engagement Index
- Active Users
- Data Source
- Growth Trend
- ACV
- Risk Index
- Departments
- Alternatives
- Purchased Seats
- Sanction Status
- Contract Start Date
- Contract End Date
- Tags
- []**Application**: The name of the application. Click on the application to go to the [Viewing Applications Details](/business-insights/viewing-application-details) page, where you can view the application-specific metrics.
- **Capability**: The various capabilities offered by the application. For example, Okta's capabilities include identity management, access control, two-factor authentication, etc.
- **Data Source**: The source from where the application usage is discovered (i.e., identity provider (IdP), Zscaler Internet Access (ZIA), by connector integration, or custom application such as **IDP**, **ZIA**, **CONNECTOR**,** CUSTOM ZIA**).
- **Engagement Index**: The percentage of active users in the last 30 days over the last 90 days for an app. For example, if you have 50 active users in the last 30 days and 100 in the last 90 days for Box, the engagement index is calculated by dividing the number of active users in the last 30 days by the number of active users in the last 90 days, and multiplying it by 100 (i.e., [50÷100]×100 = 50%).
- **Growth Trend**: The percentage increase or decrease in user activity for every 30 days. For example, if you have 50 active users in the last 30 days but 100 active users before the last 30 days, the growth trend is calculated by dividing the increase or decrease in the number of active users by the number of active users before the last 30 days, and multiplying it by 100 ([100−50]÷100×100 = decrease of 50%).
- **Active Users**: The number of active users for the app.
-
**Tags**: The tags linked to the contract. Click the **Add **icon to link the contract to a manual tag, create a new tag category, or go to the [Application Tags](/business-insights/about-application-tags) page.
[See image.](#tags-column)
- **Purchased Seats**: The number of seats purchased in the app subscription.
- **Assigned Seats**: The number of seats assigned to the users within your organization.
- **Spend**: The total spent on the application by your organization.
- **Contract Start Date**: The date when the application subscription commenced.
- **Contract End Date**: The date when the application subscription ends.
- **Risk Index**: The risk index assigned to the application. This setting for the app is configured in the ZIA Admin Portal. To learn more, see [About Cloud Applications](/zia/about-cloud-applications) and [About Shadow IT Report](/zia/about-shadow-it-report).
- **Sanctioned**: Whether the application's use is sanctioned or not in your organization.
- **Alternatives**: A list of alternative applications with similar capabilities.
- **Top Departments**: The top departments by app usage. The departments are listed with the number of active users (in parentheses) in ascending order for the last 30 days of app usage.
[]![Tags Column in the All Applications Page](/downloads/business-insights/application-insights/about-all-applications/Business-Insights-Tagging-Drop-Down.png)