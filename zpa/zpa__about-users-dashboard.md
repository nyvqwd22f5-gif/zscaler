# About the Users Dashboard
Source: https://help.zscaler.com/zpa/about-users-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1483761.pdf

The Users dashboard provides information about user activity in your organization.
![Users Dashboard within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/Users.png)
Dashboard Tools
The Users dashboard displays the following information and functionality:
- **Time Range Filter**: View user data over a period between **1 Hour** to **14 Days**, or you can select **Custom Range**. If you use a **Custom Range**, the start and end date must be within the last 14 days. The end time can be configured to the selected time in hours and minutes. By default, the dashboard displays information for events that occurred in the last hour. This filter applies to all widgets on the dashboard except **Current Connected Users**, which displays users for up to the last 30 minutes.
Log information in the dashboard is limited to 14 days. For longer access to the logs, use the [Log Streaming Service (LSS)](/zpa/about-log-streaming).
- **Refresh Icon**: Refresh the dashboard to reflect the most current information.
- **Recent Users**: View the total number for this category at the top of the page, and then view its details in the widget below. This number is based on the users that accessed applications, and it includes all successful and unsuccessful transactions.
- **Current Connected Users**: View the total number for this category at the top of the page, and then view its details in the widget below. This number is based on the users who have logged into the Zscaler Client Connector and who are authenticated and connected to ZPA.
- **Policy Blocks**: View the total numbers for this category at the top of the page, and then view its details in the widget below.
****![Users Dashboard page within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-about-the-users-dashboard-tools1.png)
****
Widgets
The Users dashboard provides the following widgets:
- [Recent Users](#uaccess)
- [Current Connected Users](#ccu)
- [Users Blocked by Policies](#ubp)
- [Top Users by Applications](#tua)
- [Top Users by Bandwidth](#tcb)
- [Top Policies by Blocked Users](#tpb)
If you are using the [Log Streaming Service](/zpa/about-log-streaming) (LSS), the Users dashboard includes information for a ZPA LSS Client user. This user represents the LSS service, not an actual user. Also, each log receiver is displayed as an application, to reflect the data coming in from the service. To learn more, including how to stop the LSS service from streaming ZPA LSS Client logs, see [Configuring a Log Receiver](/zpa/configuring-log-receiver#Step2).
[]This widget displays real-time information about the total number of users that requested applications and successful machine tunnel connections over the selected time frame. The widget always uses the current time for its end time even if a custom time range with a different end time is selected.
For users accessing applications using Browser Access through unauthenticated HTTP preflight OPTIONS request, the username will appear as **ZPA BA Unauthenticated**. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments#BrowserAccess_NewAppSeg).
![Users Dashboard with Recent Users widget](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-recent-users-widget.png)
- Click the navigation tabs to view a list of users or machine tunnels.
- Click on a user or machine tunnel to view more details in **Diagnostics**.
- Click the **Download** icon (![Download icon within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-dashboardwidgets-downloadicon.png)
) to export a file (.csv) containing information on the users that accessed applications or successful machine tunnel connections with ZPA for the selected time frame (i.e., Timestamp (in UTC) and username).
[]This widget displays real-time information of users and machine tunnels currently connected to ZPA.
![Users Dashboard with Current Connected Users widget](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-current-connected-users-widget.png)
- Click on the navigation tabs to view a list of users or machine tunnels.
- Hover over a user or machine tunnel to view the following:
- **Logged In Time**:** **The time user logged in.
- **IP Address**:** **IP address of the user's device.
- **User Location**:** **Location user is connecting from.
- Click on a user or machine tunnel to view more details in **Diagnostics**.
- Click the **Download** icon (![Download icon within the ZPA Admin Portal](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/zpa-dashboardwidgets-downloadicon.png)
) to export a file (.csv) containing information on the users or machine tunnels that are currently accessing applications with ZPA for up to the last 30 minutes.
[]This widget displays users that have been blocked by your organization's configured policies in the selected time frame.
![Users Blocked by Policies widget](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-users-blocked-by-policies-widget.png)
- Hover over a user to view the following:
- **Name**: The username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- **# of Policy Blocks**: The number of times the user was blocked by a policy in the selected time frame and the percentage that number represents of the total number of times users were blocked by policies, as shown in the widget.
- Click on a user to view more details in **Diagnostics**.
[]This widget displays the top ten users of applications in the selected time frame. The percentage of total transactions for the top users by applications appears in the top right corner.
![Top Users by Application widget ](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-top-users-by-application-widget.png)
- Hover over a user to view the following:
- **Name**: The username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- **# of App(s)**: The number of applications accessed by the user in the selected time frame and the percentage that amount represents of the total number of applications the top ten users accessed, as shown in the widget.
- Click on a user to view more details in **Diagnostics**.
[]This widget displays the top ten consumers of bandwidth in the selected time frame. The percentage of total transactions for the top users by bandwidth appears in the top right corner.
![Top Users by Bandwidth widget](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-top-users-by-bandwidth-widget.png)
- Hover over a user to view the following:
- **Name**: The username. This is the NameID in the SAML assertion from the IdP and not the username entered in Zscaler Client Connector.
- **Bandwidth**: The amount of bandwidth consumed by the user in the selected time frame and the percentage that number represents of the total bandwidth consumed by the ten users shown in the widget.
- Click on a user to view more details in **Diagnostics**.
[]This widget displays the top ten policies that blocked users in the selected time frame.
![Top Policies By Blocked Users widget](/downloads/zpa/dashboard-diagnostics/about-users-dashboard/zpa-users-dashboard-top-policies-by-blocked-users-widget.png)
- Hover over a policy to view the following:
- **Name**: The policy name.
- **# of Policy Blocks**: The number of users the policy blocked in the selected time frame and the percentage that number represents of the total number of users blocked by the ten policies shown in the widget.
- Click on a policy to view more details in **Diagnostics**.