# Analyzing Traffic Monitoring
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-traffic-monitoring
PDF: https://help.zscaler.com/pdf/com/en/1420531.pdf

The Traffic Monitoring page provides information on the name, group, location, throughput, and session data across services of your Cloud or Branch Connector. You can use the **Refresh **icon (![Refresh Icon on the Traffic Monitoring Page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/analyzing-traffic-monitoring/Refresh%20Icon.jpg)
) to refresh the dashboard to view the most recent information.
Analyzing the Traffic Monitoring Page
Location Filtering
You can filter Cloud Connectors under **AWS Regions** and **Azure**. You can filter Branch Connectors under **Branch Connector Locations**.
By default, the filter is set to **Any** which indicates that no filter is applied.
To apply filters:
- Select the locations from one of the filter drop-down menus.
- Click **Done** to confirm your selections.
- Click **Apply**.
You can adjust the filters as needed or remove all of them by clicking **Reset**.
[See image.](#traffic-monitoring-filters)
Widgets
The Traffic Monitoring page provides the following widgets:
- [Throughput Across Services](#throughtput-data)
- [Sessions Across Services](#session-data)
- [Geo View](#geo-view)
[]The Throughput Across Services chart displays all the throughput of the traffic flowing through ZIA, ZPA, Direct, and Log & Control for the Cloud and Branch Connector virtual machines (VMs) that are provisioned and deployed in your cloud or branch accounts. You can use the location filters to see the throughput only for the filtered cloud or branch account and location.
The throughput across services is displayed in Mbps. You can hover over the chart to see the Cloud and Branch Connectors throughput forwarded to ZIA, ZPA, or Direct.
[See image.](#traffic-monitoring-throughput)
[]The Sessions Across Services chart displays all the session count data of ZIA, ZPA, Direct, and Log & Control for the Cloud and Branch Connector VMs that are provisioned and deployed in your cloud or branch accounts. You can use the location filters to see the session counts only for the filtered cloud or branch account and location.
The sessions across services is displayed in Sessions. You can hover over the chart to see the Cloud and Branch Connectors session count forwarded to ZIA, ZPA, or Direct.
[See image.](#traffic-monitoring-sessions)
[]The Geo View provides the geographic locations of all Cloud and Branch Connectors provisioned and deployed on your Cloud or Branch accounts. The location filtering can be used to filter particular Cloud and Branch Connectors based on your requirements. The map displays the number of Cloud and Branch Connectors deployed in different regions. You can click the cluster to view all the Cloud and Branch Connectors in a particular region along with their cloud provider type (i.e., AWS, Azure, Branch Cloud). You can also click any Cloud and Branch Connector to view its throughput and session count data.
You can click and drag the map to view different regions. You can also zoom in and out of the map to better view regions of interest.
[See image.](#geo-view2)
Cloud & Branch Connector Monitoring Table
The table displays:
- **Name**: The name of the Cloud or Branch Connector.
- **Group**: The name of the group to which the Cloud or Branch Connector VM is assigned.
- **Location**: The location of the Cloud or Branch Connector Group.
- **ZIA (Throughput/Session)**: The throughput and the session data that are forwarded through the ZIA cloud.
- **ZPA (Throughput/Session)**: The throughput and the session data that are forwarded through the ZPA cloud.
- **Direct (Throughput/Session)**: The throughput and the session data that are forwarded directly.
Click the **View** icon to access the [Traffic Flow](/cloud-branch-connector/analyzing-traffic-flow) page, where you can see the throughput and session count forwarded to ZIA, ZPA, or Direct for the selected Cloud or Branch Connector.
![The Traffic Monitoring Table in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-monitoring/Traffic%20Monitoring%20Info%20Table%20C%26B%20Connector.jpg)
[]![Traffic Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-monitoring/Traffic%20Monitoring%20AWS%2C%20Azure%2C%20BRanch.jpg)
[]![Traffic Monitoring Throughput Across Services in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-monitoring/ThroughputAcrossServices_.png)
[] ![Traffic Monitoring Sessions Across Services in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-monitoring/SessionsAcrossServices_.png)
[] ![Geo View from the Cloud & Branch Connector Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-traffic-monitoring/GeoView_3.png)