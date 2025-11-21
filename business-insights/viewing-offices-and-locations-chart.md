# Viewing Offices and Locations in a Chart
Source: https://help.zscaler.com/business-insights/viewing-offices-and-locations-chart
PDF: https://help.zscaler.com/pdf/com/en/1486606.pdf

This article explains the data displayed on the Offices and Locations page (Workplace > Offices and Locations > Charts) in the Chart view.
[See image.](#charts)
To understand the data in a list or chart, see [About Offices and Locations](/business-insights/about-offices-and-locations) or [Viewing Offices and Locations on a Map](/business-insights/viewing-offices-and-locations-map).
Viewing Offices and Locations in a Chart
To analyze the data for a specific metric or time frame:
- **Export as PDF**: Download the data on the page as a PDF file.
-
**Time Range**: View workplace insights for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
[See image.](#timerange)
- Filter the insights by:
- **Name**: The name of the workplace. You can only select to view data for either the configured offices or inferred locations at one time.
- **Departments **or** Divisions**: The department filter is available unless you have at least one department mapping to a division on the [Department Mapping](/business-insights/about-department-mapping) page.
- **Departments**: The departments within your organization. This data is mapped from the ZIA Admin Portal SCIM. If the values are inaccurate, contact a ZIA admin.
- **Divisions**: The division that maps related departments.
-
**Days**: Specific days from the filtered time frame. Enable **Custom Dates **to select custom dates to include or exclude from the insights. By default, Saturdays and Sundays are excluded from the metrics.
[See image.](#days-filter)
- **User Types**: The type of users or employees visiting your organization. Selecting this filter doesn't filter the data unless you have defined user types for your organization in Business Insights. To enable this filter, contact Zscaler Support.
The page contains the following information:
Averages Section
This section contains the following widgets:
- **Average Occupancy**: The average occupancy in percentage and numbers for the filtered offices within the specified time frame. This is calculated by dividing the total number of visits to the workplaces by overall workplace capacities for the time period specified, then multiplying it by 100. You can view the total number of visits vs. the total possible capacity. The total possible capacity is determined by multiplying the capacity for all selected offices by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible capacity is 500. You can also view the percentage increase or decrease in occupancy vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Peak / Low Occupancy**: The peak and low occupancy percentage on a particular day and the number of office visits for the filtered workplaces within the specified time frame.
- **Average Attendance**: The average attendance for the workplaces within the specified time frame. This is calculated by dividing the total number of visits to the workplaces by the total number of assigned headcount for the workplaces, then multiplying it by 100. You can view the total number of visits vs. the total possible assigned headcount. The total possible assigned headcount is determined by multiplying the capacity for all selected offices by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible assigned headcount is 500. You can also view the percentage increase or decrease in attendance vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Average Visit Span**: The average time spent in the workplaces.
You can only view data for either the configured offices or inferred locations at one time. The metrics are calculated considering a 5-day work week.
[See image.](#averages-image)
The metrics for inferred location-based workplaces are estimated as the Business Insights service doesn't have precise metadata to provide accurate insight. Hence, Zscaler recommends [configuring offices](business-insights/configuring-offices) (providing metadata) for inferred location-based workplaces to view accurate insights.
[See image.](#estimated-metrics)
Occupancy Tab
This tab consists of the following sections:
The explanatory sentence at the top of sections is shown for the filtered time frame and not for the time frames it is compared with.
Occupancy by Day
The graph shows the occupancy comparison trend for the time frame specified. For example, if you filter the data for the current week, this graph shows the occupancy comparison with last week's data. You can:
- View the data in the graph in percentage or number of visits by selecting the respective options (i.e., **Percentage** or **Visits**).
- View the data for a specific time frame by selecting the checkboxes next to the graph (e.g., last week or current week).
- View the average occupancy for the office within the specified time frame, as well as the occupancy goal percentage (and the numerical value) configured for the office.
- Hover over a date in the graph to view the percentage increase or decrease in the occupancy and the average occupancy.
Occupancy by Day of the Week
This graph shows the occupancy percentage for each day of the week. This is calculated by dividing the number of visits to the workplaces on that day by the possible capacity of the workplaces, then multiplying it by 100. You can:
- View the data in the graph in percentage or number of visits by selecting the respective options (i.e., **Percentage** or **Visits**).
- View the data for a specific time frame by selecting the checkboxes at the bottom of the graph (e.g., last week vs. current week).
[See image.](#occupancy-tab-image)
Attendance Tab
This tab consists of the following sections:
The explanatory sentence at the top of sections is shown for the filtered time frame and not for the time frames it is compared with.
Attendance by Day
The graph shows the attendance comparison trend for the time frame specified. For example, if you filtered the data for the current week, this graph shows the attendance percentage comparison with last week's data. You can:
- View the data in the graph in percentage, number of visits, or days per week by selecting the respective options (i.e., **Percentage**, **Visits**, or **Days per Week**).
- View the data for a specific time frame by selecting the checkboxes next to the graph (e.g., last week vs. current week).
- View the average attendance for the office within the specified time frame, as well as the attendance goal percentage (and the numerical value) configured for the office.
- Hover over a date in the graph to view the percentage increase or decrease in attendance and the average attendance.
Attendance by Day of the Week
This graph shows the attendance percentage for each day of the week. This is calculated by dividing the number of visits to the workplaces on that day by the total number of possible assigned headcount of the workplaces, then multiplying it by 100. You can:
- View the data in the graph in percentage or number of visits by selecting the respective options (i.e., **Percentage** or **Visits**).
- View the data for a specific time frame by selecting the checkboxes at the bottom of the graph (e.g., last week vs. current week).
Attendance by Days per Week
The pie chart shows the percentage of users (and their count) who came to the workplaces less than a day to 7 days a week. The center of the pie chart shows the total number of users.
Attendance by Department
The bar chart shows the percentage of users coming into the workplace from the total number of assigned headcount for the workplace and the expected attendance for each department at the workplace. Select the **Show Unassigned Users** checkbox to view the data for users that are not assigned to a department.
[See image.](#attendance-tab-image)
[]![The Chart View of the Offices and Locations Page](/downloads/business-insights/getting-started/understanding-business-insights-terminology/Business-Insights-Offices-Locations-charts.gif)
[]![Averages Section in the Chart View](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-chart/Business-Inisghts-Workplace-Insights-page-Averages.png)
[]![Occupancy Tab in the Chart View](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-chart/Business-Inisghts-Offices-Locations-Occupancy-For-Workplaces_0.png)
[]![Attendance Tab in the Chart View](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-chart/Business-Inisghts-Offices-Locations-Attendance-tab-for-offices_0.png)
[]![Estimated Averages](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-chart/Business-Inisghts-Estimated-Averages-in-charts_0_1.png)
[]![Days Filter](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Workplace-Days-Filter.png)
[]![Time Range Filter](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-chart/Business-Insights-Timerange-filter.gif)