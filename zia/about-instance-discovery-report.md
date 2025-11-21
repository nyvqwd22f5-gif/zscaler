# About the Instance Discovery Report
Source: https://help.zscaler.com/zia/about-instance-discovery-report
PDF: https://help.zscaler.com/pdf/com/en/1506326.pdf

The Instance Discovery Report provides visibility into the instances accessed by the users at the various levels of hierarchy for the SaaS applications.
The SaaS applications supported by this discovery and their associated level of instance discovery are listed in the table:
- [SaaS Applications and Associated Instance Level Discovery](#saas_instance_table)
The Instance Discovery Report provides the following benefits and enables you to:
- Analyze specific application instance usage at different levels in your organization.
- Gain visibility into tenants of different applications accessed by users, like workspaces for Slack and sites for SharePoint.
- Discover corporate and non-corporate tenants of SaaS applications and use them in tenant profiles and instance profiles, to enforce control through cloud app control and DLP policies.
To enable the Instance Discovery Report for your organization, contact your Zscaler Account team.
About the Instance Discovery Report Page
On the Instance Discovery Report page (Analytics > Instance Discovery Report), you can view insights into the various levels of instance discovery for SaaS applications. The widgets displayed in the report are based on the level of instance discovery for a specific SaaS application. By default, the Google Cloud Platform data is displayed in the report. The SaaS applications are categorized based on the level of discovery that is allowed, as follows:
- [Level One of Discovery](#app_instance_level1)
- [Level Two of Discovery](#app_instance_level2)
- [Level Three of Discovery](#level_3_apps)
On the Instance Discovery Report, for the applications supporting level three of discovery (Organization, Project, and Resource), you can do the following:
- []Filter the report for the last 1 day, last 7 days, last 15 days, last month, or last quarter.
- Select the SaaS application you wish to view the Instance Discovery Report for from the drop-down menu.
- **Overview**: This section gives a comprehensive view of the instances discovered for the application you selected. You can:
- **Total Organizations**: View the number of unique organizations discovered.
- **Total Projects**: View the number of unique projects discovered.
- **Total Resources**: View the number of unique resources discovered.
- **Total Bytes: **View total bytes of transactions to the discovered instances.
- **Total Users**: View the number of unique users accessing the discovered instances.
- **Analyze More**: Further analyze the instances in a detailed view in the [Resource Discovery Report](/zia/viewing-resource-discovery-report).
- **Instance Analytics**: View the trend for the number of instances discovered over the period of time selected for **Organizations**, **Projects**, or **Resources** in the form of a line chart.
- **Top Organizations**: View the transaction information for the top 10 organizations in the form of a bar chart. The data is represented for each organization ID. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Projects**: View the transaction information for the top 10 projects in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Resources**: View the transaction information for the top 10 discovered resources in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Users**: View the transaction information for the top users in the organization in the form of a bar. You can filter the data by **Organizations**, **Projects**, or **Resources**.
![The instance Discovery Report with Instance Analytics and other widgets for analysis.ets ](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Level_3_app_GCP_instance_discovery.png)
[]The level one instance types are:
- [Domain](#level_1_domain_apps)
- [Tenant](#level_1_tenants_apps)
[]
On the Instance Discovery Report, for the applications supporting one level of discovery, you can do the following:
- Filter the report for the last 1 day, last 7 days, last 15 days, last month, or last quarter.
- Select the SaaS application you wish to view the Instance Discovery Report for from the drop-down menu.
- **Overview: **This section gives a comprehensive view of the instances discovered for the application you selected. You can:
- **Total Domains**: View the number of unique domains discovered.
- **Download Bytes**: View the number of bytes downloaded from discovered instances.
- **Upload Bytes**: View the number of bytes uploaded from discovered instances.
- **Total Bytes: **View total bytes of transactions to the discovered instances.
- **Total Users**: View the number of unique users accessing the discovered instances.
- **Analyze More**: Further analyze the instances in a detailed view in the [Resource Discovery Report](/zia/viewing-resource-discovery-report).
- **Instance Analytics**: View the trend for the number of instances discovered over the period of time selected in the form of a line chart.
- **Top Domains**: View the analytics around the individual instances discovered in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Users**: View the transaction information for the top 10 users in the organization in the form of a bar chart.
![The Instance Discovery Report showing all the widgets for Level 1 of discovery with instance type - Domain.](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Level_1_app_Domains_Gmail_Instance_discovery.png)
[]On the Instance Discovery Report, for the applications supporting one level of discovery, you can do the following:
- Filter the report for the last 1 day, last 7 days, last 15 days, last month, or last quarter.
- Select the SaaS application you wish to view the Instance Discovery Report for from the drop-down menu.
- **Overview: **This section gives a comprehensive view of the instances discovered for the application you selected.
- **Total Domains**: View the total number of unique domains discovered.
- **Download Bytes**: View the number of bytes downloaded from discovered instances.
- **Upload Bytes**: View the number of bytes uploaded from discovered instances.
- **Total Bytes: **View total bytes of transactions to the discovered instances.
- **Total Users**: View the number of unique users accessing the discovered instances.
- **Analyze More**: Further analyze the instances in a detailed view in the [Resource Discovery Report](/zia/viewing-resource-discovery-report).
- **Instance Analytics**: View the trend for the number of instances discovered over the period of time selected.
- **Top Tenants**: View the analytics around the individual instances discovered in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Users**: View the transaction information for the top 10 users in the organization in the form of a bar chart.
![Instance Discovery Report showing the widgets Instant Analytics, Top Tenants, and Top Users ](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Level_1_Apps_Tenants_ServiceNow_instance_discovery.png)
[]The level two instance types are:
- [Domain > Workspace](#app_instance_level2_workspace)
- [Domain > Sites](#level_2_sites_apps)
[]On the Instance Discovery Report, for the applications supporting level two of discovery, you can do the following:
- Filter the report for the last 1 day, last 7 days, last 15 days, last month, or last quarter.
- Select the SaaS application you wish to view the Instance Discovery Report for from the drop-down menu.
- **Overview**: This section gives a comprehensive view of the instances discovered for the application you selected. You can:
- **Total Domains**: View the total number of unique domains discovered.
- **Workspaces:** View the number of unique workspaces discovered.
- **Upload Bytes**: View the number of bytes uploaded from discovered instances.
- **Total Bytes: **View total bytes of transactions to the discovered instances.
- **Total Users**: View the number of unique users accessing the discovered instances.
- **Analyze More**: Further analyze the instances in a detailed view in the [Resource Discovery Report](/zia/viewing-resource-discovery-report).
- **Instance Analytics**: View the trend for the number of instances discovered over the period of time selected in the form of a line chart. You can filter the data by **Domains** or **Workspaces**.
- **Top Domains**: View the analytics around the individual instances discovered in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Workspaces**: View the transaction information for the top 10 workspaces in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Users**: View the transaction information for the top 10 users in the organization in the form of a bar. You can filter the data by **Domains **or **Workspaces**.
![Instance Discovery Report shows the Instance Analytics, Top Domains, Top Workspaces, and Top Users .](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Level2_Slack_Instance_discovery_Updated1.png)
[]On the Instance Discovery Report, for the applications supporting level two of discovery, you can do the following:
- **Overview**: This section gives a comprehensive view of the instances discovered for the application you selected. You can:
- **Total Domains**: View the total number of unique domains discovered.
- **Total Sites:** View the total number of unique sites discovered.
- **Upload Bytes**: View the number of bytes uploaded from discovered instances.
- **Total Bytes: **View total bytes of transactions to the discovered instances.
- **Total Users**: View the number of unique users accessing the discovered instances.
- Select the SaaS application you wish to view the Instance Discovery Report for from the drop-down menu.
- **Analyze More**: Further analyze the instances in a detailed view in the [Resource Discovery Report](/zia/viewing-resource-discovery-report).
- **Instance Analytics**: View the trend for the number of instances discovered over the period of time selected in the form of a line chart. You can filter the data by **Domains **or **Sites**.
- **Top Domains**: View the analytics around the individual instances discovered. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Sites**: View the transaction information for the top 10 sites in the form of a bar chart. You can filter the data by the **Download Bytes**, **Number of Transactions**, **Total Bytes**, or **Upload Bytes**.
- **Top Users**: View the transaction information for the top users in the organization in the form of a bar. You can filter the data by **Domains **or **Sites**.
![Instance Discovery Report shows the Instance Analytics, Top Domains, Top Sites, and Top Users. ](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Level_2_Sharepoint_Sites_Instance_discovery_1.png)
| Application | Instance Level 1 Type | Instance Level 2 Type | Instance Level 3 Type |
| ----------- | --------------------- | --------------------- | --------------------- |
| Box | Domain | N/A | N/A |
| Google Cloud Platform | Organization | Project | Resource |
| Google Drive | Domain | N/A | N/A |
| Gmail | Domain | N/A | N/A |
| OneDrive | Domain | N/A | N/A |
| Microsoft Outlook | Domain | N/A | N/A |
| Microsoft Teams | Domain | N/A | N/A |
| Salesforce | Tenant | N/A | N/A |
| ServiceNow | Tenant | N/A | N/A |
| SharePoint | Domain | Site | N/A |
| Slack | Domain | Workspace | N/A |
[]