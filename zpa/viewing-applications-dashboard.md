# Viewing the Applications Dashboard
Source: https://help.zscaler.com/zpa/viewing-applications-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1483451.pdf

The Applications dashboard provides information about applications in your organization.
![Applications dashboard in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-applications-dashboard.png)
Dashboard Tools
The Applications dashboard displays the following information and functionality:
- **Time Range Filter**: View application data over a period between **1 Hour** to **14 Days**, or you can select **Custom Range**. If you use a **Custom Range**, the start and end date must be within the last 14 days. The end can be configured to the selected time in hours and minutes. This filter applies to all widgets on the dashboard except **Discovered Applications **and **Recommended Application Segments by Confidence %**. By default, the dashboard displays information for events that occurred in the last hour.
Log information in the dashboard is limited to 14 days. For longer access to the logs, use the [Log Streaming Service (LSS)](/zpa/about-log-streaming).
- **Refresh icon**: Refresh the dashboard to reflect the most current information.
- **Recent Applications Accessed**: View the total number for this category at the top of the page, and then view its details in the widget below. This number is based on the applications accessed by users, and it includes all successful and unsuccessful transactions.
- **Discovered Applications**: View the total number for this category at the top of the page, and then view its details in the widget below. This number is based only on successful transactions.
- **Access Policy Blocks** and **Successful Transactions**: View the total numbers for these categories at the top of the page, and then view their details in the widgets below.
- **Chart Selection**: Select the charts you want to display. You need to select a minimum of 4 charts. All charts are selected by default.
![About the Applications Dashboard tools](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-about-the-applications-dashboard-tools1.png)
Widgets
The Applications dashboard provides the following widgets:
- [AI-Powered Recommendations by Attack Surface Reduction %](#rasc)
- [Recent Applications Accessed](#aa)
- [Top Applications by Bandwidth](#bw)
- [Top Errors](#toperrors)
- [Top Application Segments by Bandwidth](#appsegbandwidth)
- [Top Disaster Recovery App Segments by Bandwidth](#drappseg)
- [Top Policy Blocks](#toppolicyblocks)
- [Top Applications by Users](#au)
- [Applications Discovered in the Past 14 Days](#da)
- [App Configuration in Past 3 Months](#appconfigwidget)
If you are using the [Log Streaming Service (LSS)](/zpa/about-log-streaming), the Users dashboard includes information for a ZPA LSS Client user. This user represents the LSS service, not an actual user. Also, each log receiver is displayed as an application to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming ZPA LSS Client logs, see [Configuring a Log Receiver](/zpa/configuring-log-receiver#Step2).
[]This widget displays the total number of recommended application segments, grouped by their percentage of attack surface reduction. The attack surface reduction groups are broken up into 25% increments to show how many recommended application segments had higher attack surface reduction versus those that were lower. If you hover over the chart and click a specific section, a tooltip appears that specifies the attack surface reduction group for the percentage increment, the total number of AI-powered recommendations, and the percentage total. Clicking **View All** takes you to the [AI-Powered Recommendations](/zpa/about-ai-powered-recommendations-application-segments) page.
AI-Powered Recommendations must be activated to display the AI-Powered Recommendations by Attack Surface Reduction % widget and populate it with data. To activate this feature, click **Activate Recommendations** on the Application Management > Application Segments > AI-Powered Recommendations page.
![AI-Powered Recommendations by Attack Surface Reduction % Widget in the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/applications-users-monitoring/viewing-applications-dashboard/zpa-ai-powered-recommendations-by-asr-percentage2.png)
[]This widget displays real-time information about the total number of applications requested by users that were accessed in the selected time frame. The widget always uses the current time for its end time even if a custom time range with a different end time is selected.
![Applications Dashboard with Applications Accessed widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-about-applications-dashboard-recent-applications-accessed-widget.png)
- Click on an application to view more details in **Diagnostics**.
- Click the **Download** icon (![Download icon within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-dashboardwidgets-downloadicon.png)
) to export a CSV file containing information on the applications accessed for the selected time frame (i.e., Timestamp (in UTC), application (domain name or IP address), port number, and protocol).
[]This widget displays the top 10 applications that used the most bandwidth for your organization in the selected time frame. The percentage of total transactions for the top 10 applications by bandwidth appears in the top-right corner.
![Top Applications by Bandwidth widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-about-applications-dashboard-top-applications-by-bandwidth-widget.png)
- Hover over an application to view:
- **Name**:** **The application name.
- **Bandwidth**: The amount of bandwidth used by the application in the selected time frame, and the percentage that amount represents of the total bandwidth used by the 10 applications shown in the widget.
- Click on an application to view more details in **Diagnostics**.
[]This widget displays the top 10 application segments that used the most bandwidth for your organization in the selected time frame. The percentage of total transactions for the top application segments by bandwidth appears in the top-right corner.
![Top Application Segments by Bandwidth widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/topappsegbybandwidth.png)
[]This widget displays the top 10 disaster recovery-enabled application segments that used the most bandwidth for your organization in the selected time frame. If there was a disaster recovery-related incident during this time frame, it accounts for both the disaster recovery-related transactions and the regular transactions. The percentage of total transactions for the top disaster recovery-enabled application segments by bandwidth appears in the top-right corner.
![Top Disaster Recovery App Segments by Bandwidth widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/topdrappsegbybandwidth.png)
[]This widget displays the top errors experienced by users per connection status code, application, App Connector, and ZPA Private Service Edges over the selected time frame.
- [Connection Status Codes](#conn_status_codes)
- [Applications](#app_errors)
- [App Connectors](#conn_errors)
- [Service Edges](#se_errors)
[]You can hover over the connection status codes to:
- View the total number of transactions that occurred with this connection status code.
- View the percentage of errors where this connection status code occurred for the drilldown data displayed.
- Analyze by:
- **Applications**: This drills down and displays data on the applications impacted by the connection status code.
- **Connectors**: This drills down and displays data on the App Connectors impacted by the connection status code.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Top Errors widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-connection-status-codes-widget.png)
[]You can hover over the applications to:
- View the total number of transactions where the application error occurred.
- View the percentage of errors where this application error occurred for the drilldown data displayed.
- Analyze by:
- **Connectors**: This drills down and displays data on the App Connectors impacted by the application error.
- **Connection Status Codes**: This drills down and displays data on the connection status code applicable to the impacted application.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Top Errors widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-applications-widget.png)
[]You can hover over the App Connectors to:
- View the total number of transactions where the App Connector error occurred.
- View the percentage of errors for the drilldown data displayed for the App Connector.
- Analyze by:
- **Applications**: This drills down and displays data on the applications impacted by the App Connector error.
- **Connection Status Codes**: This drills down and displays data on the connection status code applicable to the impacted App Connector.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Top Errors widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-app-connectors-widget.png)
[]You can hover over the ZPA Private Service Edges to:
- View the total number of transactions for the error that occurred on the ZPA Private Service Edge.
- View the percentage of errors for the drilldown data displayed for the ZPA Private Service Edge.
- Analyze by:
- **Connectors**: This drills down and displays data on the App Connectors impacted by the ZPA Private Service Edge error.
- **Connection Status Codes**: This drills down and displays data on the connection status code applicable to the impacted ZPA Private Service Edge.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Top Errors widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-service-edges-widget.png)
[]This widget displays the top access policy and timeout policy blocks experienced by users over the selected time frame.
- [Access Policy Blocks](#accesserrors)
- [Timeout Policy Blocks](#policyblocks)
[]You can hover over the access policy block to:
- View the total number of transactions where the access policy block occurred.
- View the percentage of errors where this access policy block occurred for the drilldown data displayed.
- Analyze by:
- **Applications**: This drills down and displays data on the applications impacted by the access policy block.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Access Policy Blocks widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-top-policy-blocks-access-policy-blocks-widget.png)
[]You can hover over the timeout policy block to:
- View the total number of transactions where the timeout policy block occurred.
- View the percentage of errors where this timeout policy block occurred for the drilldown data displayed.
- Analyze by:
- **Applications**: This drills down and display data on the applications impacted by the timeout policy block.
- **Show in Logs**: To view more details in **Diagnostics** for the drilldown data that is displayed.
![Timeout Policy Blocks widget within Dashboard](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-top-policy-blocks-timeout-policy-blocks-widget.png)
[]This widget displays the top 10 applications accessed by your organization's users in the selected time frame. The percentage of total transactions for the top applications by users appears in the top-right corner.
![Top Applications by User widget ](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-about-applications-dashboard-top-applications-by-user-widget.png)
- Hover over an application to view:
- **Name**: The application name.
- **Number of User(s)**:** **The top 10 applications accessed by your organization's users in the selected time frame, and the percentage that number represents of the 10 applications shown in the widget.
- Click on an application to view more details in **Diagnostics**.
[]This widget displays the applications that ZPA has [discovered](/zpa/about-application-discovery) for your organization in the past 14 days, with the most recently discovered application listed first.
![Applications Dashboard with the Applications Discovered in the Past 14 Days widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-about-applications-dashboard-applications-discovered-in-the-past-14-days-widget1.png)
- Click on an application to view more details in **Diagnostics**. If the application has not been accessed in the last 14 days, you will not see data for the application in **Diagnostics**.
- Click the **Download** icon (![Download icon within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-dashboardwidgets-downloadicon.png)
) to export a CSV file containing information on the applications discovered in the last 14 days (i.e., application (domain name or IP address), port number, protocol, and internal application ID).
- To define a user access policy or change settings for an application (e.g., enable health monitoring or configure bypass settings), you can explicitly define an application by clicking on **Add Application Segment**, selecting the applications, and then clicking **Define Selected Applications**. To learn more, see [Defining a Dynamically Discovered Application](/zpa/defining-dynamically-discovered-application).
To learn more about application discovery, see [About Application Discovery](/zpa/about-application-discovery).
[]This widget displays the number of Defined Application Segments (orange) compared to the number of Discovered Applications (blue) in two-week increments over the past 3 months. Ideally for Zero Trust, the number of Defined Application Segments should be increasing while the number of Discovered Applications should be decreasing.
Hover over a graph bar to get detailed information for each two-week increment. Click a graph bar and then click View Recommended Apps to view the Recommended Application Segments page.
AI-Powered Recommendations must be activated to display the App Configuration in Past 3 Months widget and populate it with data. To activate this feature, click **Activate Recommendations** on the Application Management > Application Segments > AI-Powered Recommendations page.
![App Configuration in Past 3 Months widget](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/AppConfiguration-03.png)