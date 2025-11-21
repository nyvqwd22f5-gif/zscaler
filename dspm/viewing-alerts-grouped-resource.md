# Viewing Alerts Grouped by Resource
Source: https://help.zscaler.com/dspm/viewing-alerts-grouped-resource
PDF: https://help.zscaler.com/pdf/com/en/1478176.pdf

DSPM scans the cloud resources against the [policies](/dspm/about-data-posture-policies) enabled in your cloud infrastructure to identify vulnerabilities and generate alerts.
You can view all the resources in the cloud accounts for which alerts are generated. Additionally, you can view the risk level of the resources to prioritize the issue, the type of data store, number of open alerts, and the cloud type in which the resource is located.
On the Grouped by Resource tab (Alerts > Alert Views > Alerts), you can do the following:
- View the resource details. For each resource, you can view:
-
**Resource Name**: The name of the resource. Click to view additional details:
- **Alerts**: View the list of alerts generated for the resource. Click the **Alert ID** to [view additional details](/dspm/viewing-alert-details).
- **Risk Explorer**: View a [graphical representation](/dspm/viewing-data-inventory-graph) of the scan results.
- **Sensitive Data**: View the [sensitive data details](/dspm/viewing-sensitive-data-details).
- **Vulnerabilities**: View the [vulnerabilities detected](/dspm/viewing-vulnerability-details) in the resources. Vulnerabilities are displayed only for EC2 instances.
- **Access**: View the [access level permissions](/dspm/viewing-resource-access-levels) assigned to user entities to perform actions on the resources.
[See image.](#resourcedrawer)
- **Resource ID**: The unique identifier for the resource.
- **Resource Type**: The type of data store (**AWS EC2 instance**, **AWS S3 bucket**, etc.).
-
**Risk Level**: The risk level (**Critical**, **High**, **Medium**, and **Low**) of the resource.
The resource risk level depends on the highest risk level of the alerts generated for that resource. For example, if the resource has 10 alerts generated, and the risk levels of these alerts are High, Medium, and Low, then the resource risk level is High.
- **Number of Alerts**: The number of alerts generated for the resource.
- **Cloud Account**: The unique identifier of the cloud account (**AWS**, **Azure**, **GCP**, **Snowflake**, and **On-Premises**) in which the resource is located.
-
[Apply filters to view specific data.](/dspm/using-filters)
By default, resources with an open alert status are displayed.
- [Add additional filters.](/dspm/using-filters)
- Search for specific data in the searchable column (**Resource Name**). You can also export the search results with the applied filters and download the report as an Excel file.
- Export the data and [download the report](/dspm/about-reports) as an Excel file.
- Sort the column data.
- [Modify the table and its columns.](/dspm/using-tables)
![The grouped by resource tab with list of resources for which DSPM alerts are generated.](/downloads/dspm/alerts/alert-details/viewing-alerts-grouped-resource/dspm-grouped-by-resource-tab.png)
[]![The resource drawer with annotation around all the tabs.](/downloads/dspm/alerts/alert-details/viewing-alerts-grouped-resource/dspm-resource-drawer_2.png)