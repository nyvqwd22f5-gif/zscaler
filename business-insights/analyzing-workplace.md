# Analyzing a Workplace
Source: https://help.zscaler.com/business-insights/analyzing-workplace
PDF: https://help.zscaler.com/pdf/com/en/1487641.pdf

The Workplace Details page shows various metrics such as occupancy, attendance, and footfall details for a workplace. To view the insights for a workplace, go to the Offices and Locations page (Workplace > Offices and Locations) and click on a workplace name, or go to the Workplace Insights page (Workplace > Workplace Insights) and click **View Details** for the workplace you want to view.
To analyze the Workplace Details page:
- **Export as PDF**: Download the data on the page as a PDF file.
-
**Time Range**: View workplace details for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
[See image.](#timerange)
- Filter the insights by:
- **Departments **or** Divisions**: The department filter is available unless you have at least one department mapping to a division on the [Department Mapping](/business-insights/about-department-mapping) page.
- **Departments**: The departments within your organization. This data is mapped from the ZIA Admin Portal SCIM. If the values are inaccurate, contact a ZIA admin.
- **Divisions**: The division that maps related departments.
-
**Days**: Specific days from the filtered time frame. Enable **Custom Dates **to select custom dates to include or exclude from the insights. By default, Saturdays and Sundays are excluded from the metrics.
[See image.](#days-filter)
- **User Types**: The type of users or employees visiting your organization. Selecting **User Types** doesn't filter the data unless you have defined user types for your organization in Business Insights. To enable this filter, contact Zscaler Support.
The page contains the following information:
Averages Section
This section contains the following widgets:
- **Average Occupancy**: The average occupancy in percentage for the workplace within the specified time frame. This is calculated by dividing the total number of visits to the workplace by the workplace capacity for the time period specified, then multiplying it by 100. You can view the total number of visits vs. the total possible capacity. The total possible capacity is determined by multiplying the workplace capacity by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible capacity is 500. You can also view the percentage increase or decrease in occupancy vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Peak / Low Occupancy**: The peak and low occupancy percentage on a particular day and the number of office visits for the workplace within the specified time frame.
- **Average Attendance**: The average attendance for the workplace within the specified time frame. This is calculated by dividing the total number of visits to the workplace by the total number of assigned headcount for the workplace, then multiplying it by 100. You can view the total number of visits vs. the total possible assigned headcount. The total possible assigned headcount is determined by multiplying the workplace capacity by the number of official working days within the time frame selected. For example, if your capacity is 100 and there are 5 official working days, the possible assigned headcount is 500. You can also view the percentage increase or decrease in attendance vs. the previous period of the same time (e.g., Month over Month (MoM), Week over Week (WoW), or Quarter over Quarter (QoQ)).
- **Average Visit Span**: The average time spent in the workplace.
The metrics are calculated considering a 5-day work week.
[See image.](#averages-image)
The metrics for inferred location-based workplaces are estimated as the Business Insights service doesn't have precise metadata to provide accurate insight. Hence, Zscaler recommends configuring offices (providing metadata) for inferred location-based workplaces to view accurate insights.
[See image.](#estimated-data)
Occupancy Tab
This tab consists of the following sections:
The explanatory sentence at the top of sections is shown for the filtered time frame and not for the time frames it is compared with.
Occupancy by Day
The graph shows the occupancy comparison trend for the time frame specified. For example, if you filter the data for the current week, this graph shows the occupancy comparison with last week's data. You can:
- View the data in the graph in percentage or numerical values by selecting the respective options (i.e., **Percentage** or **Value**).
- View the data for a specific time frame by selecting the checkboxes next to the graph (e.g., last week or current week).
- View the average occupancy for the office within the specified time frame, as well as the occupancy goal percentage (and the numerical value) configured for the office.
- Hover over a date in the graph to view the percentage increase or decrease in the occupancy and the average occupancy.
Occupancy by Day of the Week
This graph shows the occupancy percentage for each day of the week. This is calculated by dividing the number of users who came into the workplace on that day by the capacity of the workplace, then multiplying it by 100. You can:
- View the data in the graph in percentage or numerical values by selecting the respective options (i.e., **Percentage** or **Value**).
- View the data for a specific time frame by selecting the checkboxes at the bottom of the graph (e.g., last week vs. current week).
Footfall by the Time of the Day
This section shows the hourly footfall information for the workplace for the filtered time frame averaged for 7 days of the week if you select to view monthly data. Hover over an hour bar to view the day and date information, and the total number of employees present in the workplace during that hour, followed by the split between departments.
In this section, you can:
-
Click the **Export **button to download the footfall data as a CSV file. This option is available when the **Time Range** filter at the top of the page is selected as **Last 7 days** or **Week**.
[See image.](#export-footfall)
-
Click an hour bar to view the total user footfall for each department.
[See image.](#department-window)
-
Select to view the footfall data for any 1 of the 3 months in this section if the **Time Range** filter at the top of the page is selected for 3 months.
[See image.](#footfall-filter)
[See image.](#occupancy-tab-image)
Attendance Tab
This tab consists of the following sections:
The explanatory sentence at the top of sections is shown for the filtered time frame and not for the time frames it is compared with.
Attendance by Day
The graph shows the attendance comparison trend for the time frame specified. For example, if you filtered the data for the current week, this graph shows the attendance percentage comparison with last week's data. You can:
- View the data in the graph in percentage, numerical values, or days per week by selecting the respective options (i.e., **Percentage**, **Value**, or **Days per Week**).
- View the data for a specific time frame by selecting the checkboxes next to the graph (e.g., last week vs. current week).
- View the average attendance for the office within the specified time frame, as well as the attendance goal percentage (and the numerical value) configured for the office.
- Hover over a date in the graph to view the percentage increase or decrease in attendance and the average attendance.
Attendance by Day of the Week
This graph shows the attendance percentage for each day of the week. This is calculated by dividing the number of users who came to the workplace on that day by the total number of users assigned to the workplace, then multiplying it by 100. You can:
- View the data in the graph in percentage or numerical values by selecting the respective options (i.e., **Percentage** or **Value**).
- View the data for a specific time frame by selecting the checkboxes at the bottom of the graph (e.g., last week vs. current week).
Attendance by Days per Week
The pie chart shows the percentage of users (and their count) who came into the workplace less than a day to 7 days a week. The center of the pie chart shows the total number of users.
Attendance by Department
The bar chart shows the percentage of users coming into the workplace from the total number of users assigned to the workplace and the expected attendance for each department at the workplace. Select the **Show Unassigned Users** checkbox to view the data for users that are not assigned to a department.
[See image.](#attendance-tab-image)
[]
![Estimated Averages section showing various workplace-related numbers](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Estimated-Averages-in-charts_0_0.png)
[]![Averages Section showing various workplace-related numbers](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Workplace-Insights-page-Averages.png)
[]![Export option in Footfall by the Time of the Day section](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Export-Footfall-Data_0.png)
[]![User count for each department ](/downloads/business-insights/workplace-insights/analyzing-office-site/Business-Inisghts-department-window.png)
[]![Footfall Section Filter for 3 Months](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Occupancy-Tab-Footfall-Time-Filter.png)
[]![Occupancy Tab for Workplace](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Insights-Occupancy-Tab.png)
[]![Attendance tab showing attendance data for the workplace](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Offices-Locations-Attendance-tab.png)
[]![The Days filter for analyzing a workplace](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Inisghts-Workplace-Days-Filter.png)
[]![Time Range Filter](/downloads/business-insights/workplace-insights/analyzing-workplace/Business-Insights-Timerange-filter.gif)