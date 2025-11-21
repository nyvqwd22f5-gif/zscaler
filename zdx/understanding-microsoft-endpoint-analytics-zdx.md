# Understanding Microsoft Endpoint Analytics for ZDX
Source: https://help.zscaler.com/zdx/understanding-microsoft-endpoint-analytics-zdx
PDF: https://help.zscaler.com/pdf/com/en/1413026.pdf

Microsoft Endpoint Analytics can help identify issues with user software or devices that might be impacting performance and reliability. After you integrate Microsoft Intune with Zscaler Digital Experience (ZDX), metrics are garnered from the Microsoft Intune API and mapped to individual ZDX users and devices to provide Endpoint Analytics scores and metrics.
To view Endpoint Analytics data, you should first configure the Intune application integration. To learn more, see [Configuring Microsoft Intune for ZDX](/zdx/configuring-microsoft-intune-zdx).
To access Endpoint Analytics, choose one of the following options to view the user details page:
- From the User Overview page, select one or more applications from the Applications filter drop-down menu and click **Apply. **Click the table cell for a user or device to view a page with user details.
- Search for a specific user in Search and view their page. To learn more, see [Using Search in the ZDX Admin Portal](/zdx/using-user-search-zdx-admin-portal).
Viewing User Details
The user details page provides the following Endpoint Analytics information for a specified user device:
- **Endpoint Analytics Score**: Reflects the weighted average of the [Startup Performance](#startup-performance) score and [Software Reliability](#software-reliability) score.
- **Health Status**: Shows the most recent status of the device, designated as **Unknown**, has **Insufficient Data**, **Needs Attention**, or is **Meeting Goals**.
- **Last Updated**: Indicates the date and time when metrics were last collected from the Microsoft Intune API. Although data is collected from the API every 3 hours, metrics might not repopulate every 3 hours within the UI. Some [Startup Performance](#startup-performance) events might take up to 24 hours to be displayed, and some [Software Reliability](#software-reliability) events might take up to 3 days to be displayed.
- **View Endpoint Analytics**: Accesses scores and metrics for [Startup Performance](#startup-performance) and [Software Reliability](#software-reliability).
![Link to View Endpoint Analytics from user details page](/downloads/zdx/analytics/users/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-user-details6.png)
[]Viewing Startup Performance Information
**Startup Performance** can help you assess the health and performance of a user's device over time, based on Endpoint Analytics scores, boot and sign-in times, and processes that might affect device startup.
[See image.](#startup-performance-full)
View the following information on the **Startup Performance** page:
- [Score Categories](#score-categories)
- [Score Over Last 14 Days](#score-14-days)
- [Boot History and Sign-in History](#boot-signin-history)
- [Top Ten Processes Impacting Startup](#top-processes)
[]The Endpoint Analytics scores are calculated on a scale from 0 (poor) to 100 (exceptional):
- **Startup Performance**: Reflects the weighted average time from system power-on to completion of a user's successful sign in.
- **Software Reliability**: Reflects the reliability of all installed applications and software, based on crash frequency and duration of usage.
![Endpoint Analytics Score Categories](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-score-categories.png)
[]Click a point in the graph within the previous 14 days to display **Startup Performance** scores, from 0 (poor or slow) to 100 (exceptional or fast):
- **Startup Score**: A weighted average of both **Core Sign-in Score **and **Core Boot Score**.
- **Core Sign-in Score**: An average based on the time when a user enters credentials to when the user accesses a rendered desktop, and CPU usage has fallen below 50% for at least 2 seconds.
- **Core Boot Score**: An average based on the time from system power-on to sign in.
![Endpoint Analytics Score for last 14 days](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-score-14-days.png)
[]Hover over a date within the past 14 days to view the average time it took (in seconds) for device bootup and sign in:
![Boot History and Sign-in History graphs](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-boot-signin-history.png)
[]View the top processes in which CPU usage might be running above 50% and impacting users:
- **Process Name**: The service or application name.
- **Vendor**: The associated software vendor.
- **Load Time** **(Seconds)**: The time interval from system power-on to when the desktop becomes responsive.
![Table that shows the top ten processes impacting startup](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-top-processes_0.png)
To learn more about **Startup Performance** insights and recommendations, see the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/analytics/startup-performance).
[]Viewing Software Reliability Information
**Software Reliability** can help identify potential problems with software and applications on user devices so you can troubleshoot the cause of the issues. The **Software Reliability Score**, history of software events, and details of those software events can collectively provide insight into the health status of individual devices.
[See image.](#sw-reliability-full)
View the following information on the **Software Reliability** page:
- [Software Events Over Last 14 Days](#events-14-days)
- [Software Events](#sw-events)
[]Hover over an event within the past 14 days to view the number of event types that occurred on that particular day:
![Graph that shows the number of software events occurred over past 14 days](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-events-14-days.png)
[]View details of software events that occurred within the past 14 days:
- **Event**: The type of application or software event.
- **Time**: The date and time when the event occurred.
- **Name**: The name of the associated service, application, or software being used.
- **Publisher**: The company that licenses the service, application, or software.
- **Version**: The numbered version of the service, application, or software.
![Table that shows software events by date and time](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-sw-events_0.png)
To learn more about **Software Reliability**, see the [Microsoft documentation](https://learn.microsoft.com/en-us/mem/analytics/app-reliability).
[]![Startup Performance drawer](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-startup-perf-fullscreen_1.png)
[]![Software Reliability drawer](/downloads/zdx/analytics/understanding-microsoft-endpoint-analytics-zdx/zdx-endpoint-analytics-sw-reliability-fullscreen2_0.png)