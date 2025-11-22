# Viewing Alerts Grouped by Policy
Source: https://help.zscaler.com/dspm/viewing-alerts-grouped-policy
PDF: https://help.zscaler.com/pdf/com/en/1478171.pdf

DSPM scans the cloud resources against the [policies](/dspm/about-data-posture-policies) enabled in the AWS accounts, Azure subscriptions, or GCP projects to identify vulnerabilities and generate alerts.
You can view all the predefined and custom policies for which alerts are generated. Additionally, you can view the severity level of the policy to prioritize the issue, number of open alerts, and the cloud type in which the resource is located.
On the Grouped by Policy page (Alerts > Alert Views > Alerts), you can do the following:
- View the policy details. For each policy, you can view:
-
**Policy Name**: The policy title. Click to view additional details:
- **Cloud**: The cloud type (**AWS**, **Azure**, **GCP**, **Snowflake**, and **On-Premises**) in which the resource is located.
- **State**: The status (**Enabled** or **Disabled**) of the policy.
- **Severity**: The severity level (**Critical**, **High**, **Medium**, or **Low**) of the policy.
[See image.](#additional-info-policy)
You can also view the following tabs:
- **Alerts**: View the [alert details](/dspm/viewing-alert-details) generated for the policy.
- **Policy Overview**: View the [policy details](/dspm/viewing-policy-details).
- **Remediation**: View the [remediation steps](/dspm/viewing-remediation-details) to resolve the alert.
[See image.](#policydrawer)
- **Severity**: The severity level (**Critical**, **High**, **Medium**, and **Low**) of the policy.
- **Policy Category**: The [threat category](/dspm/threat-categories) (**Public Exposure**, **Data Loss**, etc.) to which the policy belongs.
- **Resource Type**: The type of data store (**AWS EC2 instance**, **AWS S3 bucket**, etc).
- **Number of Alerts**: The number of alerts generated for the policy.
- **Cloud**: The cloud type (**AWS**, **Azure**, **GCP**, **Snowflake**, and **On-Premises**) in which the resource is located.
-
[Apply filters to view specific data.](/dspm/using-filters)
By default, policies with an open alert status are displayed.
- Add additional filters.
- Search for specific data in the searchable column (**Policy Name**). You can also export the search results with the applied filters and download the report as an Excel file.
- Export the data and [download the report](/dspm/about-reports) as an Excel file.
- Sort the column data.
- [Modify the table and its columns.](/dspm/using-tables)
![The grouped by policy tab with the list of policies for which DSPM alerts are generated.](/downloads/dspm/alerts/alert-details/viewing-alerts-grouped-policy/dspm-grouped-by-policytab.png)
[]![The policy drawer with annotations around the available tabs.](/downloads/dspm/alerts/alert-details/viewing-alerts-grouped-policy/dspm-policy-drawer_0.png)
[]![The policy drawer with annotation around additional details.](/downloads/dspm/alerts/alert-details/viewing-alerts-grouped-policy/dspm-policy-drawer-additionaldetails.png)