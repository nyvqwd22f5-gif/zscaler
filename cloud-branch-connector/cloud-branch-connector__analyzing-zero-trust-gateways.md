# Analyzing Zero Trust Gateways
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-zero-trust-gateways
PDF: https://help.zscaler.com/pdf/com/en/1516906.pdf

The Zero Trust Gateway page provides information on the name, location, entitlement status, and health status of your Zero Trust Gateway. You can use the **Refresh **icon (![Refresh Icon on the Traffic Monitoring Page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/analyzing-traffic-monitoring/Refresh%20Icon.jpg)
) to refresh the dashboard to view the most recent information.
Understanding the Zero Trust Gateway Page
Location Filtering
You can filter gateways using the drop-down menu in the **AWS Regions** section.
By default, the filter is set to **Any**, which indicates that no filter is applied.
To apply filters:
- Select the locations from the filter drop-down menu.
- Click **Done** to confirm your selections.
- Click **Apply**.
You can adjust the filters as needed or remove all of them by clicking **Reset**.
[See image.](#locationfiltering)
Widgets
The Zero Trust Gateway page provides the following widgets:
- [Entitlement Status](#entitlementstatus)
- [Health Status](#healthstatus)
- [Geo View](#geoview)
Zero Trust Gateway Monitoring Table
After the **Geo View** section, the monitoring table displays the following information about your gateways:
- **Name**: The name of the gateway.
- **Type**: The cloud provider type. Only AWS is supported.
- **ID**: The ID of the gateway.
- **Region**: The region associated with the gateway.
- **Location**: The location associated with the gateway.
- **Geo Location**: The physical location of the gateway when deployed.
- **Service Status**: The service status of the gateway (i.e., **Healthy**, **Unhealthy**, or **Not Available**).
- **Availability Zones**: The number of availability zones associated with the gateway.
- **Endpoints**: The number of endpoints associated with the gateway.
![The Zero Trust Gateway Monitoring table in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-zero-trust-gateways/zerotrustgatewaydashboardtable_0.png)
[]
The **Entitlement Status** chart displays the number of availability zones in which you can deploy Zero Trust Gateway instances. For example, if you have two regions, and each region has three availability zones and two gateways, the number of deployed entitlements is 6. **Total Entitled** shows the total number of availability zones that you are licensed for.
You can use the location filters to see the entitlement status only for the filtered gateways and locations.
[See image.](#entitlement)
[]
The **Health Status** chart displays the health status of deployed gateways. You can use the location filters to see the health status only for the filtered gateways and locations.
[See image.](#health)
[]
The **Geo View** displays the geographic locations of all Zero Trust Gateways deployed. You can use location filtering to show only particular gateways based on your requirements. The map displays the number of gateways deployed in different regions. You can click the cluster to view all the gateways in a particular region along with their cloud provider type. Only Amazon Web Services (AWS) is supported. You can also click any gateway to view more information (i.e., **Deployment Type**, **Name**, **Region**, **Location**, **Endpoints**, and **Service Status**). If a gateway is inactive, the reason is displayed.
You can click and drag the map to view different regions. You can also zoom in and out of the map to better view regions of interest.
[See image.](#geo)
[]
![The Zero Trust Gateway location filtering options in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-zero-trust-gateways/zerotrustgatewaydashboard.png)
[]
![A pie chart in the form of circle around the words "100 Total Entitled." The chart shows a yellow section labeled 66 and a green section labeled 34. A color guide indicates that green represents Deployed and yellow represents Available.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-zero-trust-gateways/entitlementstatus.png)
[]
![A pie chart in the form of a circle around the words "34 Total Deployed." The chart shows a green section labeled 34 and an unlabeled red section. A color guide indicates that green represents Healthy and red represents Unhealthy.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-zero-trust-gateways/healthstatus.png)
[]
![The Zero Trust Gateway geo view in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-zero-trust-gateways/geoview.png)