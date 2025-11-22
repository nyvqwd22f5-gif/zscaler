# Analyzing Workplace Insights
Source: https://help.zscaler.com/business-insights/analyzing-workplace-insights
PDF: https://help.zscaler.com/pdf/com/en/1487706.pdf

Workplace Insights provides metrics related to workplaces and their workforces across the globe for an organization. This information can be used to view actionable insights and efficiently manage your workplaces. There are two types of workplaces: inferred locations and configured offices.
- Inferred Locations are [Zscaler Internet Access (ZIA) locations](/zia/about-locations) configured in the ZIA Admin Portal (a ZIA location can also consist of sub-locations) and inferred IP addresses that the Business Insights service concludes as the organization's workplace based on the amount of traffic, the number of users behind the IP address, and more assuring metrics.
- Configured Offices are the grouping of inferred locations into a configured office with metadata. To learn more, see [About Configured Offices](/business-insights/about-configured-offices).
Workplace Insights provides the following benefits and enables you to:
- View the organization's workforce locations and their insights.
- Manage your workplace more effectively.
- Make business-critical decisions, like opening, shutting down, and optimizing offices.
[See image.](#workplace-insights)
Zscaler recommends configuring offices (providing metadata) for inferred location-based workplaces to get accurate insights. After you update office metadata, it is reflected in Workplace Insights after the daily service scan.
Analyzing Workplace Insights
To analyze the Workplace Insights page (Workplace > Workplace Insights), use the following operators to filter the data for your viewing requirements:
- **Export as PDF**: Download the data on the page as a PDF file.
-
**Time Range**: View workplace insights for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
[See image.](#timerange)
- Filter insights by:
- **Type**: The type of workplace (**Offices** or **Inferred Locations**). For **Geolocation**, select the workplaces based on the type selected. Business Insights automatically assigns names for inferred location workplaces that are based on IP addresses and retains the name assigned in the ZIA Admin Portal for [ZIA location](/zia/about-locations)-based workplaces. You can only select to view data for either the configured offices or inferred locations at one time.
-
**Days**: Specific days from the filtered time frame. Enable **Custom Dates** to select custom dates to include or exclude from the insights. By default, Saturdays and Sundays are excluded from the metrics.
[See image.](#days-filter)
- **Departments **or** Divisions**: The department filter is available unless you have at least one department mapping to a division on the [Department Mapping](/business-insights/about-department-mapping) page.
- **Departments**: The departments within your organization. This data is mapped from the ZIA Admin Portal SCIM. If the values are inaccurate, contact a ZIA admin.
- **Divisions**: The division that maps related departments.
- **User Types**: The type of users visiting your organization. Selecting user types doesn't filter the data unless you have defined these user types for your organization in Business Insights. To enable this filter, contact Zscaler Support.
[See image.](#filters)
The page contains the following sections:
Overall Averages
This section contains the following widgets:
- **Average Occupancy**: The average occupancy in percentage and numbers for the filtered offices within the specified time frame. This is calculated by dividing the total number of visits to the workplaces by overall workplace capacities for the time period specified, then multiplying it by 100. You can view the total number of visits vs. the total possible capacity. The total possible capacity is determined by multiplying the capacity for all selected offices by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible capacity is 500. You can also view the percentage increase or decrease in occupancy vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Peak / Low Occupancy**: The peak and low occupancy percentage on a particular day and the number of office visits for the filtered workplaces within the specified time frame.
- **Average Attendance**: The average attendance for the workplaces within the specified time frame. This is calculated by dividing the total number of visits to the workplaces by the total number of assigned headcount for the workplaces, then multiplying it by 100. You can view the total number of visits vs. the total possible assigned headcount. The total possible assigned headcount is determined by multiplying the capacity for all selected offices by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible assigned headcount is 500. You can also view the percentage increase or decrease in attendance vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Average Visit Span**: The average time spent in the offices.
You can only view data for either the configured offices or inferred locations at one time. The metrics are calculated considering a 5-day work week.
[See image.](#workplace-insights-averages)
If you've filtered the data for inferred offices, the data in this section are estimated as the Business Insights service doesn't have precise metadata to provide accurate insight. Click **Upload data to view insights** and provide metadata to view accurate insights. You're redirected to the [Configured Offices](/business-insights/about-configured-offices) page.
[See image.](#average-estimated)
Attendance by Days per Week
This graph shows the attendance percentage (and the actual numbers) for each day of the week. This is calculated by dividing the number of visits to the workplace on that day by the total number of headcount assigned to the workplace.
[See image.](#attendance)
Top Cities
This section shows the top cities by the number of employees and the frequency of their office visits (remote, less than or equal to 2 days a week, more than 2 days a week). Hover over a bar to view the number of employees at each frequency indicated by a unique color. You can also download the data to a CSV file by clicking the **Export **(![Business-Insights-Workplace-Insights-Top-Cities-Export-CSV.png](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Workplace-Insights-Top-Cities-Export-CSV.png)
) icon.
[See image.](#top-cities)
Top Offices
Switch between **Least Used** and **Most Used** to view the workplaces with least and most occupancy and attendance, respectively. For each workplace widget, you can see:
- The name of the workplace.
- The city, state or province, and country where the workplace is located.
- The type of workplace whether a configured office or inferred location.
- **Average Attendance**: The average attendance for the workplace for the filtered time frame.
- **Average Occupancy**: The average occupancy for the workplaces within the filtered time frame.
- **See Details**: Click to view additional details for the workplace. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace).
Click **View All** to see all the workplaces on the [Offices and Locations](/business-insights/about-offices-and-locations) Page.
[See image.](#workplace-insights-least-used-sites)
Map View
Switch between **Geography** and **Remote User Density** to view the following insights:
- [Geography](#geography)
- [Remote User Density](#density)
[See image.](#workplace-insights-globe)
To understand the terms used in Business Insights, see [Understanding Business Insights Terminology](/business-insights/understanding-business-insights-terminology).
[]View the distribution of workplaces across the globe. You can zoom in and out using your mouse or the icons at the bottom-right corner. Click a workplace to view:
- The name of the workplace.
- The city, state or province, and country where the workplace is located.
- The type of workplace, whether a configured office or inferred location.
- **Average Attendance**: The average attendance for the workplace for the filtered time frame.
- **Average Occupancy**: The average occupancy for the workplace for the filtered time frame.
- **See Details**: Click to view additional details for the workplace. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace).
If you don't see a configured office on the map, metadata for that office is missing. Make sure you specify the city, state or province, and country information when configuring offices to locate the configured office on the map.
You can only select to view data for either the configured offices or inferred locations at one time.
[]View locations across the globe for remote users. Zoom in and out using your mouse or the icons at the bottom-right corner. You can view:
- The total number of remote users across the globe.
- **Potential Sites Opportunities**: A list of cities with the number and percentage of remote users where you can consider opening an office.
- The total number of remote users working from the country by hovering over a country.
- Countries with darker gray signifying more remote users compared to lighter-shaded countries with fewer remote users.
-
Workplaces that show the following information when you hover over them:
- The name of the workplace.
- The city, state or province, and country where the workplace is located.
- The type of workplace, whether a configured office or inferred location.
- **Average Attendance**: The average attendance for the workplace for the filtered time frame.
- **Average Occupancy**: The average occupancy for the workplace for the filtered time frame.
Click on the workplace to view additional details. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace).
[]![Workplace Insights Page](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Workplace-Insights_0.png)
[]![Fitlering Options for the Workplace Insights](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Inisghts-Workplace-Insights-Filters.png)
[]![The Averages Section in Workplace Insights](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Inisghts-Workplace-Insights-page-Averages_0.png)
[]![Estimated Averages](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Inisghts-Workplace-Insights-estimated-averages_0.png)
[]![Attendance by Days per Week Section](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Workplace-Insights-Page-Attendance_0.png)
[]![Top Cities Section in Workplace Insights Page](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Workplace-Insights-Top-Cities.png)
[]![Map View in Workplace Insights](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Maps.gif)
[]![Least Used Office Sites Section in Workplace Insights](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Top-Offices_0.gif)
[]![Days Filter](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Days-Filter.gif)
[]![Time Range Filter](/downloads/business-insights/workplace-insights/analyzing-workplace-insights/Business-Insights-Timerange-filter_0.gif)