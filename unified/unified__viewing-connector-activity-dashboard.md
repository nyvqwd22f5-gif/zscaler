# Viewing the Connector Activity Dashboard
Source: https://help.zscaler.com/unified/viewing-connector-activity-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1517171.pdf

The Connector Activity dashboard provides an overview of Cloud Connector and Branch Connector activity in your organization.
Filtering
Click **Cloud Connectors** or **Branch Connectors** to toggle between viewing activity for each type of connector.
**Filter data**: Click the filters in the top left to limit the data shown. Each filter allows you to include or exclude individual options.
- **Geolocation**: The geographic area where the Cloud Connector or Branch Connector is located.
- **Status**: The status of the Cloud Connector or Branch Connector (i.e., **Active **or **Inactive**).
- **Connector Type**: The type of Branch Connector (i.e., **Physical **or **Virtual**).
- **Connector Location**: The named location of a Cloud Connector or Branch Connector.
After you make your selection, click **Apply **to update the dashboard with your selections. To remove all applied filter selections, click **Reset**.
[See image.](#connector-filters-image)
Dashboard Widgets
- [Traffic Volume Across Service](#traffic-volume)
- [Session Across Service](#session-service)
- [Connectors](#connectors)
[]This ring chart shows the throughput of the traffic flowing through the Cloud Connectors or Branch Connectors that are provisioned and deployed in your cloud or branch accounts. You can hover over segments of the chart to view data for each type of traffic:
- **Internet**: The throughput forwarded through the Internet & SaaS cloud.
- **Private**: The throughput forwarded through the Private Applications cloud.
- **Direct**: The throughput forwarded directly.
- **Log & Control**: The throughput forwarded through the Log and Control gateway.
[See image.](#traffic-volume-image)
[]This ring chart shows the session count data for the Cloud Connectors or Branch Connectors that are provisioned and deployed in your cloud or branch accounts. You can hover over segments of the chart to view the session count for each type of data:
- **Internet**: The session count data forwarded through the Internet & SaaS cloud.
- **Private**: The session count data forwarded through the Private Applications cloud.
- **Direct**: The session count data forwarded directly.
- **Log & Control**: The session count data forwarded through the Log and Control gateway.
[See image.](#session-service-image)
[]This table provides a list of Cloud Connectors or Branch Connectors with selected details. Use **Search **to narrow the results.
- **Name**: The name of the Cloud Connector or Branch Connector.
- **Type**: The type of Branch Connector (i.e., **Physical **or **Virtual**).
- **Group**: The group to which the Cloud Connector or Branch Connector is assigned.
- **Location**: The named location of this Cloud Connector or Branch Connector.
- **Geolocation**: The geographic area where this Cloud Connector or Branch Connector is located.
- **Autoscaling**: The status of autoscaling (i.e., **True **or **False**).
- **Status**: The status of this Cloud Connector or Branch Connector (i.e., **Active **or **Inactive**).
- **HA Status**: The high availability status of the Branch Connector.
- **VM Size**: The size of the virtual machine for a Cloud Connector (i.e., **Small **or **Medium**).
- **Model**: For a physical Branch Connector, the type of hardware device (e.g., **ZT800**); **Virtual **for a virtual connector.
[See image.](#connectors-image)
Click any row in the table to see complete details about a Cloud Connector or Branch Connector.
- To learn more about the Cloud Connector details shown, see [Analyzing Cloud Connector Details](/unified/analyzing-cloud-connector-details). You can also view these details by going to **Infrastructure > Connectors > Cloud > Cloud Connector Monitoring**.
- To learn more about the Branch Connector details shown, see [Analyzing Branch Connector Details](/unified/analyzing-branch-connector-details). You can also view these details by going to **Infrastructure > Connectors > Edge > Branch Connector Monitoring**.
[See image.](#connector-details-image)
[]![Applying filters on the Connectors dashboard](/downloads/unified/analytics/unified-dashboards/networking/viewing-connector-activity-dashboard/connectors-filters.gif)
[]![Chart showing Traffic Volume Across Service widget on the Connector Activity dashboard](/downloads/unified/analytics/unified-dashboards/networking/viewing-connector-activity-dashboard/connector-traffic-volume.png)
[]![Chart showing Session Across Service on the Connector Activity dashboard](/downloads/unified/analytics/unified-dashboards/networking/viewing-connector-activity-dashboard/connector-sessions.png)
[]![Table showing list of Connectors on the Connector Activity dashboard](/downloads/unified/analytics/unified-dashboards/networking/viewing-connector-activity-dashboard/connections.png)
[]![Table showing list of Connectors on the Connector Activity dashboard](/downloads/unified/analytics/unified-dashboards/networking/viewing-connector-activity-dashboard/connector-details.png)