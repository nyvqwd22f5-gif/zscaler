# Viewing the API Protection Dashboard
Source: https://help.zscaler.com/unified/viewing-api-protection-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1505501.pdf

The API Protection dashboard provides information about the API Protection activity in your organization.
![Viewing the API Protection dashboard](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Protection%20Dashboard.png)
Dashboard Tools
The API Protection dashboard displays the following information and functionality:
- **Time Range Filter**: View AppProtection data over a period between **1 Hour** to **14 Days**, or you can select **Custom Range**. If you use a **Custom Range**, the start date must be within the last 14 days. The end date automatically sets to the system's current time. By default, the dashboard displays information for events that occurred in the last hour. This filter applies to all widgets on the dashboard.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information.
- **AppProtection Dashboard**: View the [AppProtection dashboard](/unified/viewing-appprotection-dashboard) for more information about AppProtection policy activity.
- **Browser Protection Dashboard**: View the [Browser Protection dashboard](/unified/viewing-browser-protection-dashboard) for information about browser sessions in your organization.
![About the API Protection Dashboard tools](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/Tools.jpg)
Widgets
The API Protection dashboard provides the following widgets:
- [Recent API Activities in Last 14 Days](#14days)
- [Recent Blocked APIs](#blocked)
- [Recent API Activity with Sensitive Information](#sensitive)
- [Recent API Traffic Violations](#control)
- [Recent API Methods](#methods)
- [API Error Responses](#errors)
- [Recent Users with Violations](#users)
[]The widget displays the top 10 most recent activities for the API in the last 14 days. They are listed from the most recent API activity at the top to the least recent API activity at the bottom.
![Top APIs Discovered in 14 days widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Recent%20APIs%20Discovered.jpg)
Hover over an API name to view the following:
- **Name**: The name of the API.
- **Number of Recent API Activities in last 14 Days**: The amount of times the API appeared in the past 14 days and the percentage of times the API appeared within the Top APIs Discovered in 14 Days category.
Click an API name and then click **View Logs** to be directed to log information matching that API in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]The widget displays the top 10 most recent blocked APIs within the selected time frame. They are listed from the most frequent blocked APIs at the top to the least frequent APIs at the bottom.
![Top Blocked APIs widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Blocked.jpg)
Hover over an API name to view the following:
- **Name**: The name of the API.
- **Number of Recent Blocked APIs**: The amount of times the API appeared within the selected time frame and the percentage of times the API appeared within the Number of Top Blocked APIs category.
Click an API name and then click **View Logs** to be directed to log information matching that blocked API in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]The widget displays the amount of recent API activity with sensitive information categories (US Social Security numbers, Brazilian CPF numbers, and credit card numbers) in the selected time frame. Zscaler does not store the details or specific information; only the sensitive information category and how frequently it appeared in the time frame are stored.
![Sensitive Information Disclosure widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Sensitive.jpg)
Hover over an area of the chart to view the following:
- Displays the percentage of sensitive information transactions that occurred within the selected time frame. Zscaler does not store the specific data for sensitive information, only the category type itself is stored.
- **Click for more information**: Click this option to show the **View Logs** option. Click **View Logs** to be directed to log data matching that disclosed sensitive information transaction in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics). Zscaler only displays the amount of transactions and does not store any details related to sensitive information.
[]The widget displays the top 10 most recent API traffic violations and their respective violations within the selected time frame. They are listed from the most frequent API traffic violations at the top to the least frequent violations at the bottom.
![Top API Control Violations widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Traffic.jpg)
Hover over an area of the chart to view the following:
- **Name**: The name of the API control and the associated violation.
- **Number of Recent API Traffic Violations**: The amount of times the violation with its related API traffic violation appeared within the selected time frame and the percentage of times the API control violation appeared within the Top API Traffic Violations category.
Click an API control name and then click **View Logs** to be directed to log information matching that API control in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]The widget displays the top 10 API methods (i.e., GET, POST, PUT, etc.) for APIs within the selected time frame. They are listed from the most frequent method used at the top to the least frequent method used at the bottom.
![Top Methods widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Mehods.jpg)
Hover over an area of the chart to view the following:
- **Name**: The name of the API method.
- **Number of Recent API Methods**: The amount of times the method was used within the selected time frame and the percentage of times the method appeared within the Recent API Methods category.
Click a method and then click **View Logs** to be directed to log information matching that API method in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]The widget displays the top 10 most recent API error responses within the selected time frame. They are listed from the most frequent API error responses at the top to the least frequent API error responses at the bottom.
![Top Errors widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Errors.jpg)
Hover over an area of the chart to view the following:
- **Name**: The name of the error.
- **Total Transactions**: The complete number of transactions for the selected error within the selected time frame.
- **Errors for this selection**: The total amount of that error type within the selected time frame and the percentage of times that error type appeared within the Top Methods category.
- **Analyze by**: Click **Top URLs** to gain deeper insight into the top URLs for a specific error type. This widget displays the top 10 URLs for a selected error type within the selected time frame. They are listed from the most frequent URLs at the top to the least frequent URLs at the bottom.
- **Name**: The name of the URL.
- **Total Transactions**: The complete number of error transactions for the selected URL within the selected time frame.
- **Errors for this selection**: The total amount of errors for the selected URL in the selected time frame and the percentage of times that the error for that URL appeared with the selected error type.
[See image.](#URL)
Click an error and then click **Show in Logs** to be directed to log information matching that API error in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]The widget displays the most recent users with violations within the selected time frame. They are listed from the most frequent users with violations at the top to the least frequent users with violations at the bottom.
![Top Users widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Users.jpg)
Hover over an area of the chart to view the following:
- **Name**: The IdP user name for the API user.
- **Total Transactions**: The complete number of transactions for that IdP user.
- **Analyze by**: Click **Top URLs** to gain deeper insight into the top URLs for a specific user. This widget displays the top 10 URLs for a selected user within the selected time frame. They are listed from the most frequent URLs at the top to the least frequent URLs at the bottom.
- **Name**: The name of the URL.
- **Total Transactions**: The complete number of transactions for the selected URL within the selected time frame.
[See image.](#topurluser)
Click an error and then click **Show in Logs** to be directed to log information matching that API error in [AppProtection Diagnostics](/unified/accessing-appprotection-diagnostics).
[]![Top URLs widget within the Top Errors widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Errors%20p2.jpg)
[]![Top URLs widget within the Top Users widget](/downloads/zpa/dashboard-diagnostics/appprotection-and-browser-protection-monitoring/viewing-api-protection-dashboard/API%20Prot%20Dash%20Users%20p2_0.jpg)