# Viewing Application Details
Source: https://help.zscaler.com/business-insights/viewing-application-details
PDF: https://help.zscaler.com/pdf/com/en/1473196.pdf

The Application Details page (Application > Inventory > click on the application) provides a complete analysis and metrics for the application that is currently being used within your organization. You can view the engagement index, active and inactive user data, application plan details, licensing insights, and risk and compliance data, among other metrics.
[See image.](#app-details)
The page contains an overview section and the following tabs:
- [Overview Section](#overview)
- [Engagement Index & Users Tab](#engagement)
- [Contracts Tab](#plan)
- [Licensing Insights Tab](#licensing-insights)
- [Risk & Compliance Tab](#risk)
[]In the **Overview **section, you can view:
- **Summary**: A brief description of the application.
- **Capability**: The various capabilities offered by the application. For example, Okta's capabilities include identity management, access control, two-factor authentication, etc.
- **Alternatives**: A list of alternative applications with similar capabilities.
- **Website**: The official website for the application.
- **Status**: The connection status between Business Insights and the application (i.e., whether the application is onboarded to Business Insights or not). For connector-integrated apps, the application connector's API connection is valid or expired.
- **Data Source**: The source from where the application usage is discovered (i.e., identity provider (IdP), Zscaler Internet Access (ZIA), by connector integration, or custom application signature such as **IDP**, **ZIA**, **CONNECTOR**,** **or** CUSTOM ZIA**).
- **Sanction Status**: Whether the application's use is sanctioned or not in your organization.
- **Risk Index**: The risk index assigned to the application. This setting for the app is configured in the ZIA Admin Portal. To learn more, see [About Cloud Applications](/zia/about-cloud-applications) and [About Shadow IT Report](/zia/about-shadow-it-report).
- **Tags**: The tags linked to the application. To learn more, see [About Application Tags](/business-insights/about-application-tags).
The top-right of the page displays the **Delete **or **Connect **option based on whether the application is connected for Business Insights computation or not. To remove the app connection, click **Delete**. Click **Connect** to go to the [Add Applications](/business-insights/onboarding-saas-apps-business-insights) page, where you can configure a connector for the app. These options are available for connector-supported apps only.
[See image.](#app-overview)
[]On the **Engagement Index & Users **tab, you can view:
Active and Inactive Users Graph
This graph shows the active vs. inactive user trend for the number of purchased license seats. Hover over a date on the graph to view the engagement index, number of purchased seats, and the number of active and inactive users along with their percentage increase or decrease. You can filter this tab for information for the last 30 days or 12 months.
[See image.](#active-inactive)
Users Table
The top of the **Users **table shows the number of purchased seats, assigned seats. Use the following operators to filter the table:
- Select the time frame for viewing the data from the last 30, 60, or 90 days (last month, 2 months, or 3 months for the ZIA table).
- Switch to view data from the tabs between** Active Users** or **Inactive Users**. By default, **Active Users** is selected.
- Search for a specific user in the table.
- Click **Export** to download the data for the preceding filters into a CSV file.
The table shows the top 100 records by user activity.
[See image.](#user-table-filter)
Depending on the application's data source—how the application usage is discovered within your organization (**IDP** or **ZIA**), if you have a connector configured with a [supported app](/business-insights/understanding-business-insights-terminology#supported-app) (**CONNECTOR**), or if you have a custom application signature configured (**CUSTOM ZIA**) —one of the following Users tables appears:
- [For ZIA Discovered or CUSTOM ZIA Apps](#zia-table)
- [For IDP Discovered Apps](#idp-table)
- [For CONNECTOR Apps](#connected-apps-table)
If you're viewing application details for Microsoft 365, the User field shows obfuscated data by default. To view usernames, enable the setting in the [Microsoft 365 admin center](https://admin.microsoft.com/). To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-US/microsoft-365/troubleshoot/miscellaneous/reports-show-anonymous-user-name).
[]
- **User**: The name of the user.
- **Email**: The user's email ID.
- **Department**: The department the user belongs to.
- **Total Bytes**: The total upload and download bytes by the user for the app.
- **Upload Bytes:** The total upload bytes by the user.
- **Download Bytes**: The total download bytes by the user.
- **No. of Transactions**: The number of transactions by the user for the application.
- **Last Active**: The date when the user last used the application.
[See image.](#user-zia)
[]
- **User**: The name of the user.
- **Email**: The user's email ID.
- **Department**: The department the user belongs to.
- **Last Active**: The date when the user last used the application.
[See image.](#user-idp)
[]
- **User**: The name of the user.
- **Email**: The user's email ID.
- **Department**: The department the user belongs to.
- **License Type**: The license type of the application that is assigned to the user. For example, Microsoft 365 offers enterprise plans such as E1, E3, E5, etc. based on customer requirements.
- **Last Active**: The date when the user last used the application.
[See image.](#user-connector)
[]Contracts Table
The **Contracts **table shows the list of contracts your organization is subscribed to for the application. For each contract, you can view:
- **Contract**: The name of the contract.
- **Item Name**: The name of the service in the contract.
- **End Date**: The end date of the application subscription.
- **Licensing Model**: The licensing model for the subscription (e.g., Per User, Per GB).
- **Quantity**: The number of users or GB of data opted in the subscription.
- **List Price**: The total price of the license.
- **Annual Price**: The annual price of the license.
Use the filter option to filter the table data. Click the **Add** icon to show or hide the filter options. Use the filter-based range icons for precise data filtration (i.e., greater than, less than, between, ends with, equal to, not equal to). Click a contract to see more information about it in the [Contracts drawer](/business-insights/viewing-contract-details).
[See image.](#contracts)
[]The **Licensing Insights** tab consists of a License Usage Funnel graph that shows the metrics for the license usage of the application. These metrics provide an understanding of the current license posture and help you manage them efficiently. You can view:
- **Purchased Seats**: The number of purchased seats for the application. The graph is split between different SKUs that you purchased for the application. Hover over the bar to view the number of purchased seats for each SKU.
- **Assigned Seats**: The number of seats assigned to users from the purchased seats. Hover over the bar to view the number of assigned seats for each SKU. This information is only applicable for connector-based datasource.
- **Active Users (Last 90 days)**: The number of active users for the assigned seats. Hover over the bar to view the number of active users for each plan.
You can filter this graph based on the data sources from the **Datasource** drop-down menu, or switch it between **Plans **and **Contract **views.
You can also select or deselect the line items you want to compare in the chart.
[See image.](#licensing)
[]The **Risk & Compliance** tab consists of the following sections:
**Basic**
You can see the following information about the application:
- **Headquarter**: The application company's headquarters location.
- **Employees**: The number of people employed in the application vendor company.
- **Year** **Incorporated**: The year when the application company was incorporated.
- **Application Category**: The application category that the application is categorized under.
- **Description**: A description of the application company.
**Hosting Information**
You can see whether the application has (Yes) or does not have (No) the following characteristics. A green thumbs up next to that answer means that this is the desirable answer. A red thumbs down means that this is not the desirable answer.
- [Hosting Characteristics](#hosting)
**Security**
You can see whether the application has (Yes) or does not have (No) the following characteristics. A green thumbs up next to that answer means that this is the desirable answer. A red thumbs down means that this is not the desirable answer.
- [Security Information](#security)
[See image.](#compliance)
- []Certifications
- Shows the applicable certifications for the application.
- Poor Terms of Service
- Yes = thumbs down
- No = thumbs up
- Data Breaches in the Last 3 Years
- Yes = thumbs down
- No = thumbs up
- Source IP Restrictions
- Yes = thumbs up
- No = thumbs down
- MFA Support
- Yes = thumbs up
- No = thumbs down
- Admin Audit Logs
- Yes = thumbs up
- No = thumbs down
- File Sharing
- Yes = thumbs down
- No = thumbs up
- Password Strength
- Yes = thumbs up
- No = thumbs down
- []SSL Pinned
- Yes = thumbs down
- No = thumbs up
- Data Encryption in Transit
- Yes = thumbs up
- No = thumbs down
- Evasive
- Yes = thumbs down
- No = thumbs up
- HTTP Security Header Support
- Yes = thumbs up
- No = thumbs down
- DNS CAA Policy
- Yes = thumbs up
- No = thumbs down
- Weak Cipher Support
- Yes = thumbs down
- No = thumbs up
- Valid SSL Certificate
- Yes = thumbs up
- No = thumbs down
- Published CVE Vulnerability
- Yes = thumbs down
- No = thumbs up
- SSL Cert Key Size
- Less than 2048 bits = thumbs down
- More than 2048 bits = thumbs up
- Vulnerable to Heartbleed
- Yes = thumbs down
- No = thumbs up
- Vulnerable to Poodle
- Yes = thumbs down
- No = thumbs up
- Vulnerable to Logjam
- Yes = thumbs down
- No = thumbs up
- Support for WAF
- Yes = thumbs up
- No = thumbs down
- Remote Access Screen Sharing
- Yes = thumbs down
- No = thumbs up
- Vulnerability Disclosure Policy
- Yes = thumbs up
- No = thumbs down
- Sender Policy Framework
- Yes = thumbs up
- No = thumbs down
- DomainKeys Identified Mail
- Yes = thumbs up
- No = thumbs down
- Domain-Based Message Authentication
- Yes = thumbs up
- No = thumbs down
- Malware Scanning Content
- Yes = thumbs up
- No = thumbs down
[]![Application Details Page](/downloads/business-insights/application-insights/viewing-application-details/Business-Insights-App-Details-Page_0.png)
[]![Application Overview Section](/downloads/business-insights/application-insights/viewing-application-details/Business-Insights-App-Details-Overview-section.png)
[]![Engagement Index & Users Tab in the Application Details page](/downloads/zia/dashboard-analytics/using-tables-zbi/Bussiness-apps-details-engagement-graph.png)
[]![Users Table](/downloads/business-insights/application-insights/viewing-application-details/Bussiness-Insights-Users-Table-ZIA.png)
[]![Users Table](/downloads/business-insights/application-insights/viewing-application-details/Bussiness-Insights-Users-Table-IdP.png)
[]![Users Table](/downloads/business-insights/application-insights/viewing-application-details/Bussiness-Insights-Users-Table-Connector.png)
[]![Licensing Insights Tab](/downloads/tech-pubs-drafts/business-insights-draft-articles/viewing-application-details-0/Business-Insights-Licensing-Insights-Tab.png)
[]![Risk & Compliance Tab](/downloads/zia/dashboard-analytics/using-tables-zbi/Bussiness-apps-detail-page-compliance.png)
[]![Users Table Filter](/downloads/business-insights/application-insights/viewing-application-details/Business-Inisghts-User-Table-Filters_0.png)
[]![Contracts Tab](/downloads/tech-pubs-drafts/business-insights-draft-articles/viewing-application-details-0/Business-Insights-Contracts-Tab.png)