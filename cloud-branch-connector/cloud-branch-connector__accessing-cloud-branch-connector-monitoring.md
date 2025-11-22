# Accessing Cloud & Branch Connector Monitoring
Source: https://help.zscaler.com/cloud-branch-connector/accessing-cloud-branch-connector-monitoring
PDF: https://help.zscaler.com/pdf/com/en/1420526.pdf

The Cloud & Branch Connector Monitoring page provides information on the name, group, location, geolocation, and status of your Cloud and Branch Connector virtual machines (VMs) deployed in your cloud or branch accounts. You can use the **Refresh **icon to refresh the dashboard to view the most recent information.
Accessing the Cloud & Branch Connector Monitoring Page
On the Cloud & Branch Connector monitoring page, you can view and configure location filtering, widgets, and the Cloud & Branch Connector monitoring table.
Location Filtering
You can filter Cloud Connectors under **AWS Regions**, **Azure**, and **GCP**. You can filter Branch Connectors under **Branch Connector Locations**. By default, the filter is set to Any, which indicates that no filter is applied.
To apply filters:
- Select the locations from one of the filter drop-down menus.
- Click **Done** to confirm your selections.
- Select **Apply**.
You can adjust the filters as needed or remove all of them by clicking **Reset**.
[See image.](#Branch-Cloud-Monitoring-Filters)
Widgets
The Cloud & Branch Connector Monitoring page provides the following widgets:
- [Deployment Status](#deployment-status)
- [Active Status](#active-status)
- [Geo View](#geo-view)
[]The deployment status chart displays the number of Cloud and Branch Connectors deployed over the filtered locations. The locations can be filtered according to the cloud or branch account (i.e., AWS, Azure, VMware).
Deployment statuses include:
- **Deployed (Filtered)**: This shows only the Cloud and Branch Connectors that are deployed in your filtered locations.
- **Deployed**: This shows all the Cloud and Branch Connectors that are available and deployed on your cloud or branch account.
- **Not Deployed**: This shows all the Cloud and Branch Connectors that are available but not deployed on your cloud or branch account.
You can hover over the chart to see the number of deployed and non-deployed Cloud and Branch Connectors.
[See image.](#Branch-Cloud-Monitoring-deployment)
[]The active status chart displays the number of Cloud and Branch Connectors that are active or inactive over the filtered locations. The locations can be filtered according to the cloud or branch account (i.e., AWS, Azure, VMware).
Activity statuses include:
- **Active**: This shows all active Cloud and Branch Connectors that are deployed in your filtered locations.
- **Inactive**: This shows all inactive Cloud and Branch Connectors that are deployed in your filtered locations.
You can hover over the chart to see the number of active and inactive Cloud and Branch Connectors.
[See image.](#Branch-Cloud-Monitoring-active)
[]The **Geo View** provides the geographic locations of all Cloud and Branch Connectors deployed on your cloud or branch accounts. The location filtering can be used to filter particular Cloud and Branch Connectors based on your requirements. The map displays the number of Cloud and Branch Connectors deployed in different regions. You can click the cluster to view all the Cloud and Branch Connectors in a particular region along with their cloud provider type (i.e., AWS, Azure, VMware). You can also click any Cloud or Branch Connector to view more information such as Deployment Type, Group, Availability Zone, etc. If a Cloud or Branch Connector is inactive, the reason for the connector's inactive status is displayed.
You can click and drag the map to view different regions. You can also zoom in and out of the map to better view regions of interest.
[See image.](#Branch-Cloud-Monitoring-geoview)
Cloud & Branch Connector Monitoring Table
The table displays:
- **Name**: The name of the Cloud or Branch Connector.
- **Type**: The cloud provider type, hypervisor host, or hardware device.
- **Group**: The name of the group to which the Cloud or Branch Connector VM is assigned.
- **Location**: The location of the Cloud or Branch Connector Group.
- **Geo Location**: The physical location of the Cloud or Branch Connector when deployed.
- **Auto Scaling**: The status of auto scaling (i.e., **True** or **False**).
- **Status**: The status of the Cloud Connector (i.e., **Active** or **Inactive**).
- **HA Status**: The high availability (HA) status of the Branch Connector. This column applies to Branch Connector only.
- **VM Size**: The size of the virtual machine (i.e., **Small** or **Medium**).
- More information about the Cloud and Branch Connectors. Click the **View** icon to access the [Cloud Connector Details](/cloud-branch-connector/analyzing-cloud-connector-details) or [Branch Connector Details](/cloud-branch-connector/analyzing-branch-connector-details) page, where the general, management, and traffic forwarding information for the selected Cloud or Branch Connector is available.
[See image.](#Branch-Cloud-Monitoring-table)
[]![Cloud & Branch Connector Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/accessing-cloud-branch-connector-monitoring-draft-doc-48230/Accessing%20CB%20Monitoring.png)
[]![Cloud & Branch Connector Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-branch-cloud-connector-monitoring/Cloud-Conn-branch-cloud-connector-monitoring-deployment.png)
[]![Cloud & Branch Connector Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-branch-cloud-connector-monitoring/Cloud-Conn-branch-cloud-connector-monitoring-active.png)
[]![Geo View from the Cloud & Branch Connector Monitoring page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/about-branch-cloud-connector-monitoring/GeoView_CloudConnector2.png)
[]![Cloud & Branch Connector Monitoring table in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/accessing-cloud-branch-connector-monitoring-draft-doc-48230/Accessing%20CB%20Monitoring%20table.png)