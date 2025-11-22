# About Discovered Locations
Source: https://help.zscaler.com/business-insights/about-discovered-locations
PDF: https://help.zscaler.com/pdf/com/en/1486496.pdf

The Discovered Locations page provides data for ZIA locations and inferred IP addresses. [Zscaler Internet Access (ZIA) locations](/zia/about-locations) are configured in the ZIA Admin Portal (a ZIA location can also consist of sub-locations) and inferred IP addresses that the Business Insights service concludes as the organization's workplace based on the amount of traffic, the number of users behind the IP address, and more assuring metrics.
The Discovered Locations page provides the following benefits and enables you to:
- View metrics for all your ZIA locations and inferred IP addresses.
- Manage your workplace more effectively by mapping the discovered locations to offices.
- View the data from multiple perspectives, such as maps, charts, tables, etc. to effectively make business-critical decisions.
You can view the metrics on this page as a list, chart, or map. This article shows the data displayed in the listed form. To understand the data in a map or chart, see [Viewing Offices and Locations in a Map](/business-insights/viewing-offices-and-locations-map) and [Viewing Offices and Locations in a Chart](/business-insights/viewing-offices-and-locations-chart).
About the Discovered Locations Page
On the Discovered Locations page (Workplace > Offices and Locations > Discovered Locations), you can do the following:
- View the metrics on this page as a **List**, **Map**, or **Chart**.
- Download the data on the page as a CSV file.
- Filter the data of the entire page for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
- Filter the insights by **Type **and **Geolocation**, **Days**, **Departments **or **Division**, or **User Types**. A workplace with an undefined city, state, or country is categorized as an Unknown City, State, or Country, respectively. Click **Reset Filters **to remove any applied filters. Selecting **User Types** doesn't filter the data unless you have defined user types for your organization in Business Insights. To enable and use this feature, contact Zscaler Support.
- Search for a workplace.
- [Configure an office](/business-insights/configuring-office).
- Select multiple offices for bulk operation (e.g., mapping to office).
- View a list of discovered locations for your organization.
- [View elements for each discovered location.](#discovered-elements)
- [Modify the column menu](/business-insights/using-tables-business-insights).
- [Configure a new office for this location](/business-insights/configuring-office).
- Ignore the location from analytics.
- Go to the [Offices](/business-insights/about-offices) page to view and manage configured offices.
![The Offices and Locations Page](/downloads/business-insights/workplace-insights/about-offices-and-locations/Business-Insights-Discovered-Locations-page.png)
To understand the terms used in Business Insights, see [Understanding Business Insights Terminology](/business-insights/understanding-business-insights-terminology).
- []**Name**: The name of the workplace. Click on the workplace name to view workplace-specific metrics. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace). If you don't see data for the workplace, hover over the **Error** icon (![Business-Inisghts-tooltip-icon.png](/downloads/tech-pubs-drafts/business-insights-draft-articles/about-offices-and-locations/Business-Inisghts-tooltip-icon.png)
) next to the workplace name to see the reason (e.g., the office is not configured correctly, metadata is not added, the office was configured less than 24 hours ago, etc.) for troubleshooting purposes.
- **IP Addresses**: The IP addresses associated with the workplace.
- **City**: The city where the workplace is located. The city is mapped from the ZIA location configuration from the ZIA Admin Portal for ZIA location-based workplaces. If the value is not specified, Zscaler relies on the MaxMind lookup to locate the city's IP address. For configured offices, this is mapped from the city value specified when configuring offices.
- **State**: The state in which the workplace is located.
- **Country**: The country in which the workplace is located.
- **Attendance**: The attendance percentage for the workplace for the filtered timeframe. This is calculated by dividing the total number of visits to the workplace by the total number of possible assigned headcount for the workplace, then multiplying it by 100. This value is estimated for inferred locations.
- **Occupancy**: The occupancy percentage for the workplace for the filtered timeframe. This is calculated by dividing the total number of visits to the workplace by the total capacity of the workplace, then multiplying it by 100. This value is estimated for inferred locations.
- **Visits Per Day**: The average unique visits per day for the location.
- **Percent Mapped**: The percentage of locations, sub-locations, and IP addresses mapped to the office from the limit.
- **Office Mappings**: The office mapped for this location.