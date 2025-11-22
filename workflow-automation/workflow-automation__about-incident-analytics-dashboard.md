# About the Incident Analytics Dashboard
Source: https://help.zscaler.com/workflow-automation/about-incident-analytics-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1450021.pdf

The Incident Analytics dashboard gives high-level visibility and insight into your organization's [Data Loss Prevention (DLP) incidents](/zia/about-incidents). It allows you to monitor and analyze incident data from a single location at an organizational level. This dashboard provides a variety of information about the incidents over a specified timeframe, such as the time taken to triage and resolve incidents, previous and current incident counts, and the cumulative number of new and resolved incidents, etc.
Through this dashboard, admins with full workflow access can monitor all the incidents that have occurred in the organization and view the list of admins responsible for those incidents. Admins with restricted workflow access can only monitor the incidents assigned to them. They can't view the incidents assigned to other admins.
The Incident Analytics dashboard provides the following benefits and enables you to:
- View a summary of DLP incidents that have occurred in your organization.
- View, monitor, and analyze incidents from a single location.
- Take appropriate actions based on the data displayed on the dashboard about the incidents.
- Discover insights about the processing and remediation of incidents.
About the Incident Analytics Dashboard
On the Incident Analytics dashboard (Dashboard), you can do the following:
- Export the incident analytics to a PDF file. You can export all incident analytics available on the page, or use the filter criteria to modify the incident analytics displayed on the page and then export that information.
- Select a time range for what to display on the Incident Analytics dashboard. By default, this page displays incident analytics for the current calendar week (Sunday through Saturday). The time range filter applies to all widgets. Time ranges are:
- Hours
- Current Hour
- Last Hour
- Last 2 Hours
- Last 6 Hours
- Last 12 Hours
- Days
- Curent Day
- Last Day
- Weeks
- Current Week
- Last Week
- Months
- Current Month
- Last Month
- Custom Date Range
- Filter the incident data to show on the dashboard. If you choose the User Name attribute or Client IP attribute for obfuscation, you cannot filter the incident data on the dashboard using these obfuscated attributes. To learn more about obfuscation settings, see [Managing Account Settings](/workflow-automation/managing-account-settings) and [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Reset all the applied filters.
- View the following information about your incidents:
- **All**: Displays the total number of incidents that have occurred in your organization.
- **Open**: The number of open incidents for the selected time range.
- **Resolved**: The number of resolved incidents for the selected time range.
- **New Incident Rate (Per Day)**: The rate of new incidents per day for the selected time range.
- **Resolved Incident Rate (Per Day)**: The rate of resolved incidents per day for the selected time range.
- View analytics information about your incidents in the following widgets:
- [Time to Triage/Resolve](#time-to-triage-resolve-widget)
- [Incident by Status](#incident-status-widget)
- [Top 10 Incidents By Rule](#incidents-rule-chart)
- [Top 10 Incidents By Dictionary](#incidents-dictionary-chart)
- [Top 10 False Positive Incidents By Rule](#false-positive-incidents-by-rule-widget)
- [Top 10 False Positive Incidents By Dictionary](#false-positive-incidents-by-dictionary-widget)
- [New and Resolved Incidents Over Time](#new-and-resolved-incidents-over-time-widget)
- [Top 10 DLP Admins](#top-dlp-admins-widget)
- [Top 10 Users](#top-10-users)
[]Displays a bar chart of the time taken to triage and resolve incidents for the selected time range. The chart shows the following data:
- **Time to Triage**: The time taken in hours from the occurrence of an incident to its assignment to an admin.
- **Time to Resolve**: The time taken in hours for the admin to mark an incident as resolved.
On the chart, the darker blue bars signify the current incident time for incidents in the time range selected. The lighter blue bars signify the previous incident time for incidents using the previous time range that is equivalent to the time range selected. For example, if you select Current Month for the time range, this chart displays the time taken to triage and resolve incidents for the current month and the previous month. The actual time is displayed at the top of each bar in hours. You can also hover over the bars to view the current and previous incidents.
[See image.](#time-triage-resolve-image)
[]Displays a bar chart of incidents by their status for the selected time range. The chart shows the following statuses:
- New
- Open
- Escalated
- Resolved
On the chart, the darker blue bars signify the current incident count, and the lighter blue bars signify the previous incident count. The actual number of incidents is displayed at the top of each bar. You can also hover over the bars to view the current and previous incident counts.
[See image.](#incident-by-status-image)
[]Displays a list of the 10 DLP policy rules with the largest number of resolved incidents that are marked as false positives for each rule. You can also hover over a DLP rule to see the number of incidents associated with that rule.
[See image.](#false-positive-dlp-rule-image)
[]Displays a list of the 10 DLP dictionaries with the largest number of resolved incidents that are marked as false positives for each dictionary. You can also hover over a DLP dictionary to see the number of incidents associated with that dictionary.
[See image.](#false-positive-dlp-dictionary-image)
[]Displays a Pareto chart with the number of new and resolved incidents for the selected time range. The chart shows the following data:
- New Incident Count
- Cumulative New Incident Count
- Cumulative Resolved Incident Count
On the chart, the light blue bar shows the count of new incidents, the blue line shows the cumulative new incident count, and the green line shows the cumulative resolved incident count for each day during the selected time range.
You can also hover over the chart to view the number of new incidents, the cumulative number of new incidents, and the cumulative number of resolved incidents for a specific date.
[See image.](#new-resolved-incidents-chart-image)
[]This table is only available to admins with full workflow access permission.
Displays a table listing the 10 DLP admins with the most incidents assigned to them. For each admin, you can view the following information:
- **Assigned Admin**: The login ID for the admin.
- **New Incidents**: The number of incidents with new status assigned to the admin.
- **Resolved Incidents**: The number of incidents that the admin has resolved.
- **Average Resolution Time (Hours)**: The average time in hours that the admin took to resolve an incident.
[See image.](#top-dlp-admins-table-image)
[]Displays a list of the 10 most violated DLP policy rules with the DLP rule name and the number of incidents generated against each rule. You can also hover over a DLP rule to see the number of incidents associated with that rule.
[See image.](#top-10-incidents-rule-image)
[]Displays a list of the 10 most violated DLP dictionaries with the DLP dictionary name and the number of incidents generated against each dictionary. You can also hover over a DLP dictionary to see the number of incidents associated with that dictionary.
[See image.](#top-10-incidents-dictionaries-image)
[]Displays a table listing the 10 DLP end users with the most incidents associated with them. For each end user, you can view the following information:
- **User Email**: The email ID of the end user. When you click the user email link, you are redirected to the Incidents page, which displays only the incidents created by that end user. The user filter is automatically applied in the Filters section. If you applied other filters before clicking the user email link, those filters remain applied, as well.
- **Total Incidents**: The total number of incidents associated with the end user.
- **New Incidents**: The number of incidents with new status associated with the end user.
- **Escalated Incidents**: The number of incidents escalated to the end user's manager or approver.
- **Critical Incidents**: The number of critical priority incidents associated with the end user.
- **High Incidents**: The number of high-severity incidents associated with the end user.
[See image.](#top-10-users-image)
[]![Viewing the Time to Triage/Resolve Widget on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Time-to-Triage.png)
[]![Viewing the Incident by Status Widget on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Incident-by-Status.png)
[]![Viewing the Top 10 False Positive Incidents By Rule Chart on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Top-10-False-Positive-Rules.png)
[]![Viewing the Top 10 False Positive Incidents By Dictionary Chart on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Top-10-False-Positive-Dictionary.png)
![Viewing the Top 10 Incidents By Rule Chart on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Top-10-Incidents-by-Rule.png)
[]
![Viewing the Top 10 Incidents By Dictionary Chart on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Top-10-Incidents-by-Dictionary.png)
[]
[]![Viewing the New and Resolved Incidents Over Time Widget on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-New-Resolved-Incidents-Over-Time.png)
[]![Viewing the Top DLP Admins Table on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-DB-Top-10-DLP-Admins.png)
![Viewing the Top 10 Users Table on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-Dashboard-Top-10-Users.png)
[]
![Viewing information on the Incident Analytics dashboard](/downloads/workflow-automation/data-protection/dashboard/about-incident-analytics-dashboard/WA-Incident-Analytics-Dashboard-UI.png)