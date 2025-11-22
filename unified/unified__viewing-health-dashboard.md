# Viewing the Health Dashboard
Source: https://help.zscaler.com/unified/viewing-health-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1498041.pdf

The Health dashboard (Analytics > Reports > Private Applications > Health) provides widgets that display the health of your organization's application segments, App Connectors, and Private Service Edges.
[See image.](#img_healthdbrd)
Dashboard Tools
The Health dashboard displays the following information and functionality:
- **Search**: Search the dashboard for a specific application, App Connector, or Private Service Edge.
- **Refresh**: Refresh the dashboard to reflect the most current information for all widgets.
Widgets
The Health dashboard provides the following widgets:
- [Applications](#Applications)
- [App Connectors](#Connectors)
- [Private Service Edges](#svcedge)
[]Application health is checked and reported by the App Connectors your organization has deployed. This widget displays the health status of your applications depending on the Health Reporting setting you've configured for them. To learn more, see [About Health Reporting](/unified/understanding-health-reporting).
Below, you can learn more about the following topics:
- [Possible Application Health States](#status)
- [Widget Filters](#Filters)
- [Viewing Application Details](#details)
[]Below are the health states the widget displays for applications defined within application segments:
- **Up**: The applications are up and functioning as expected.
![5e4e5085-4010-4062-8dee-8d9d72781712_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/5e4e5085-4010-4062-8dee-8d9d72781712_display.png)
- **Down**: The applications are down and not accessible to users. This is most likely because a server that hosts the application is down or unhealthy.
![d3302f28-4c32-41c5-aa15-63d4bd634964_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/d3302f28-4c32-41c5-aa15-63d4bd634964_display.png)
- **Unhealthy**: The applications are unhealthy but still accessible to users. An application may have multiple servers that host it, and at least one of those servers is unhealthy or down. But because there's at least one server for the application that is up, users can access the application.
![6f2453c6-db6b-48cb-b300-ab0267a9a654_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/6f2453c6-db6b-48cb-b300-ab0267a9a654_display.png)
- **Unknown**: The application health is unknown. This status is shown only for applications associated to application segments configured with [Health Reporting set to On Access](/unified/configuring-defined-application-segments#HealthReportingAndCheck). It indicates that Private Applications have stopped reporting the health of this application because it has been more than 30 minutes since a user has accessed it. Private Applications report the health status as soon as a user accesses the application again.
![7d82c847-ac17-4b11-9413-4685216d5aa0_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/7d82c847-ac17-4b11-9413-4685216d5aa0_display.png)
If an application has not been accessed by a user or if an application segment was configured with Health Reporting set to On Access, then no state is displayed. Additionally, if an application has client hostname validation enabled to facilitate client-to-client remote assistance, then the application is not shown on the Health Dashboard. To learn more, see [Validating a Client Hostname](/unified/validating-client-hostname).
[]You can view or hide applications based on their health status with the **Health Status Filters**. You must select at least one filter option.
If there are more than 2,000 applications listed, the filters are not displayed.
![Application filters](/downloads/unified/analytics/private-applications/application-user-and-health-monitoring/viewing-health-dashboard/unified-privateapp-healthdashboard-applicationfliters.png)
[]For each application, you can view more information about the application in a variety of ways.
- You can hover over the application icon to view the following details:
- **Name**: The name of the application.
- **Port**: The port** **used by the application.
- **Protocol Type**: The protocol type** **used by the application.
- **Last Updated**: The timestamp showing the last time the App Connector reported the application's health status.
![fe1626dd-6a5a-49f5-a1eb-5179d1853694_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/fe1626dd-6a5a-49f5-a1eb-5179d1853694_display.png)
- You can hover over the application icon and click on the graph icon at the top-right. The graphical view that appears visually depicts the servers that host that application, and the App Connectors that provide access to those servers. If an application is down or unhealthy, the graphical view enables you to pinpoint the problem.
![Graphical view of ZPA objects from the Health Dashboard](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/zpa-healthdashboard-diagramview.png)
- You can click on an application to see servers that host that application. You can then drill down further; by clicking the arrow for a server, you can see the App Connectors that provide access to that server.
![Connected Applications to App Connectors on the Health Dashboard](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/applications-details-servers-01.png)
[]App Connector health is checked and reported by the Private Applications cloud. Below, you can learn more about the following topics:
- [Possible App Connector Health States](#cstatus)
- [Widget Filters](#cfilter)
- [Viewing App Connector Details](#cdetails)
[]Below are the health states the widget displays for App Connectors:
- **Up**: The App Connector is up and functioning as expected.
![559e4854-391f-4358-9289-8049c6bd7c9f_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/559e4854-391f-4358-9289-8049c6bd7c9f_display.png)
For App Connectors that are disabled but not yet processed as Down, a Disabled label appears below the App Connector.
[See image.](#img-disabledappconnector)
- **Down**: The App Connector is down and not functional.
![621d6488-2d39-4921-a3c8-a433836a6fa6_display.png](/downloads/zpa/documentation-knowledgebase/dashboards/health/621d6488-2d39-4921-a3c8-a433836a6fa6_display.png)
[]![Disabled App Connector in the Health Dashboard](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/app-connector-disabled-01.png)
[]You can view or hide App Connectors based on their health status with the **Health Status Filters**. You must select at least one filter option.
If there are more than 2,000 App Connectors listed, the filters are not displayed.
![App Connector filters](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/app-connector-filter-01.png)
[]For each App Connector, you can view more information about the App Connector in a variety of ways.
- You can hover over the App Connector icon to view the following details:
- **Name**: The name of the App Connector.
- **Last Updated**: The timestamp showing the last time the Private Applications cloud checked the health status.
- **Public IP**: The public IP address of the App Connector.
- **Private IP**: The private IP address of the App Connector.
- **Version**:** **The software version** **number of the App Connector.
- **CPU Utilization**: The CPU usage of the App Connector.
- **Memory Utilization**: The memory usage of the App Connector.
- **Up Time**:** **How long the App Connector has been enrolled and running.
- **Active Apps**: The number of applications currently active for this App Connector.
![App Connector details](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/app-connector-details-01.png)
[]Private Applications Private Service Edge health is checked and reported by the Private Applications cloud. Below, you can learn more about the following topics:
- [Possible Private Service Edge Health States](#sestates)
- [Widget Filters](#sefilters)
- [Viewing Private Service Edge Details](#sedetails)
[]Below are the health states the widget displays for Private Service Edges:
- **Up**: The Private Service Edge is up and functioning as expected.
![ZPA Private Service Edge health status is up](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/zpa-serviceedge-healthstatus-up.png)
For Private Service Edges that have been stopped but not yet processed as Down, a Disconnected label appears below the Private Service Edge.
- **Down**: The Private Service Edge is down and not functional.
![ZPA Private Service Edge health status is down](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/zpa-serviceedge-healthstatus-down.png)
[]You can view or hide Private Service Edges based on their health status with the **Health Status Filters**. You must select at least one filter option.
If there are more than 2,000 Private Service Edges listed, the filters are not displayed.
![Health Status Filters for ZPA Private Service Edges](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/PSE-filters-01.png)
[]For each Private Service Edge, you can view more information about it by hovering over the Private Service Edge icon to view the following details:
- **Name**: The name of the Private Service Edge.
- **Last Updated**: The timestamp showing the last time the cloud checked the health status.
- **Public IP**: The public IP address of the Private Service Edge.
- **Private IP**: The private IP address of the Private Service Edge.
- **CPU Utilization**: The CPU usage of the Private Service Edge.
- **Memory Utilization**: The memory usage of the Private Service Edge.
- **Up Time**: How long the Private Service Edge has been enrolled and running.
![ZPA Private Service Edge details on the Health dashboard](/downloads/zpa/dashboard-diagnostics/about-health-dashboard/pse-detail-01.png)
[]![Viewing Applications, Servers, and App Connectors in the Health dashboard within the ZPA Admin Portal](/downloads/unified/analytics/private-applications/application-user-and-health-monitoring/viewing-health-dashboard/unified-privateapp-healthdashboard.png)