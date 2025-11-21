# About Endpoint Data Scan
Source: https://help.zscaler.com/zia/about-endpoint-data-scan
PDF: https://help.zscaler.com/pdf/com/en/1479101.pdf

Endpoint Data Scan provides visibility into sensitive data stored locally within all the endpoints connected to your organization's traffic. You can view various metrics for each endpoint and the users connected to these endpoints. The report is generated daily for all sensitive data and doesn't require any additional configuration or scheduling. If you want to further investigate endpoint scan results for a specific user, see [About User Investigation](zia/about-user-investigation).
The Endpoint Data Scan provides the following benefits and enables you to:
- Gain visibility into scan data for endpoints connected within your organization.
- Analyze activities and incidents performed on sensitive data from various perspectives such as departments, DLP engines, AI & ML categories, file type, users, etc.
About the Endpoint Data Scan Page
On the Endpoint Data Scan page (Analytics > Endpoint Data Scan > Endpoint Data Scan), you can do the following:
- Export the data into a PDF file.
- Filter the data for a specific department.
- View:
- **Users with Sensitive Data**: The number of users with sensitive data in their devices.
- **Total Files Scanned**: The total number of files scanned on the endpoints and their accumulated size.
- **Files with Sensitive Data**: The number files with sensitive data from the scanned files and their accumulated size.
- View a list of top users with sensitive data. For each user, you can view:
- **Sensitive Data: **Filter the data based on Sensitive Data types such as DLP Engines or AI & ML Categories.
- **Export: **Export all the data in a CSV format.
- **User**: The email address of the user.
- **Department**: The name of the department that the user belongs to.
- **User Risk Profile**: The risk profile assigned to the user (Low, Medium, High, or Critical). Zscaler analyzes your organization's user behavior trends and builds a risk profile dynamically by assigning User Risk Score to each user. To learn more, see [Understanding User Risk Score](/zia/understanding-user-risk-score).
-
**Endpoint Name**: The name of the endpoints connected to the user's device. You can view the total number of endpoints connected to the user's device next to the device name. Click the number to open a window that shows the total number of files scanned and the number of sensitive files discovered from each endpoint.
[See image.](#list-of-endpoints)
- **Sensitive Files Discovered**: The total number of sensitive files discovered from all endpoints connected to the user's device.
-
**Sensitive File Range Distribution**: The piechart shows the percentage split between users with low, medium, and high number of sensitive files. Hover over the chart to view the number of users with low, medium, or high numbers of sensitive files. The categorization of users within these ranges is visible at the bottom of the chart.
You can also edit the range composition. Click the **Edit** icon to specify the Medium range. The Low and High ranges are automatically set correspondingly. For example, If you set Medium as 25 and 100, users with less than 25 sensitive files are considered Low and users with over 100 sensitive files are considered High.
- **Top DLP Engines**: The graph shows the trend for sensitive files discovered for top DLP engines for the last 14 days. Hover over a DLP engine graph to view the total number of sensitive files discovered for any given day. Click **View All **to open a window showing all the DLP engines and the number of sensitive files discovered for each DLP engine in a descending order.
- **Top AI & ML Categories**: The graph shows the trend for sensitive files discovered for top AI & ML categories for the last 14 days. Hover over the graph to view the number of files discovered for that day. Click **View All **to open a window showing all the available AI & ML categories and the number of sensitive files discovered for each category in a descending order.
- **Departments**: This section shows sensitive files discovered for each department in a descending order within the last 14 days.
- **Sensitive Data Trend**: The graph shows the trend for the sensitive files discovered for top DLP engines for the last 14 days. Hover over a date to view the number of endpoints scanned, total sensitive files discovered, and the split between each DLP engine. This graph does not show data if filters are applied.
-
**Distribution by File Type**: This section shows the number of sensitive files discovered by the file type (e.g., PDF, TXT, ZIP, etc.). Click **View All** to view a list of all file types and the number of sensitive files discovered for each file type in a descending order.
[See image.](#file-type-distribution)
![Endpoint_data_scan.png](/downloads/zia/policies/endpoint-data-loss-prevention/about-endpoint-data-scan/Endpoint_data_scan.png)
[]![List of Endpoints for a User](/downloads/zia/policies/endpoint-data-loss-prevention/about-endpoint-data-scan/ZIA-6.2r-List-of-Endpoints-for-User.png)
[]![Distribution by File Type](/downloads/zia/policies/endpoint-data-loss-prevention/about-endpoint-data-scan/ZIA-6.2r-Sensitive-Files-by-Type_0.png)