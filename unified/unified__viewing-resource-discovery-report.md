# Viewing the Resource Discovery Report
Source: https://help.zscaler.com/unified/viewing-resource-discovery-report
PDF: https://help.zscaler.com/pdf/com/en/1516361.pdf

The Resource Discovery Report provides an overview into the instances discovered and the mapping between the instances based on the SaaS application selected. The SaaS applications are categorized based on the level of discovery that is allowed. To learn more, see [Instance Discovery Report](/unified/about-instance-discovery-report).
To view insights on the Resource Discovery Report page:
- From the Admin Portal, go to **Analytics** > **Internet & SaaS** > **Analytics > Instance Discovery Report**.
- Choose a time frame from the menu. The options available are last 1 day, last 7 days, last 15 days, last month, and last quarter.
-
Select the application you wish to view the Instance Discovery Report for from the drop-down menu.
The Instance Discovery Report with insights is displayed. To learn more, see [Instance Discovery Report](/unified/about-instance-discovery-report).
-
Click **Analyze More**.
The Resource Discovery Report page opens with data populated for the time frame and the SaaS application you selected in the previous steps. The SaaS applications are categorized based on the level of discovery that is allowed as:
- [Applications Supporting One Level of Discovery](#type1_apps)
- [Applications Supporting Two Levels of Discovery](#type2_apps)
- [Applications Supporting Three Levels of Discovery](#Type3_apps)
[See image.](#resource_discovery_flow_gif)
Additionally, you can take the following actions:
- [1. Time Frame](#timeframe)
- [2. Select Applications](#select_apps)
- [3. Search](#search)
- [4. Export Data](#export_data)
- [5. More Details](#more_details)
[]Click **More Details** in any of the columns to analyze further. The **Users **drawer displays details of the organization ID, project ID, resource type, domain name, workspace ID, domain name, site name, or tenant ID, in hierarchical order depending on the column you selected.
For example, for Google Cloud Platform, click **More Details** in the **Organizations**, **Projects**, or **Resources **column to analyze further. The **Users **drawer displays details of the organization ID, project ID, or resource type in hierarchical order depending on the column you selected. If you selected **More Details** on any of the resource cards, then the details are shown in the format: <organization ID>/<project ID>/<resource type>.
[]You can do the following in the **Users **window:
- **Select Users**: You can search and select one or more users. You can view the list of users who have accessed any of the instance types for a particular application.
- **Download CSV**: You can export the **Instance Discovery Report** data to a comma-separated value CSV file.
-
**View Logs**: You are redirected to the [Web Insights Logs](/unified/about-insights-logs-internet-saas) page, which shows the data filtered, for example for Google Cloud Platform, for organization ID (App Instance Level 1), project ID (App Instance Level 2), or resource type (App Instance Level 3). The data shown depends on the hierarchical level you select to view the details on the Resource Discovery Report page. To learn more about the filters, see [Web Insights Logs: Filters](/unified/web-insights-logs-filters). Click **Back to Original** to go to the **Instance Discovery Report** page.
[See image.](#web_insights)
- **User table**: This table displays the **User Name**, **Total Bytes**, **Download Bytes**, **No. of Transactions**, and **Last Accessed** columns. For example, for Google Cloud Platform, when you click the hyperlink in any user name, you are redirected to the [Web Insights Logs](/unified/about-insights-logs-internet-saas) page which is filtered by organization ID (App Instance Level 1), project ID (App Instance Level 2), or resource type (App Instance Level 3) with the user name. The data shown depends on the hierarchical level you select to view details on the Resource Discovery Report page. To learn more about the filters, see [Web Insights Logs: Filters](/unified/web-insights-logs-filters). You can click **Back to Original** to go to the **Instance Discovery Report** page.
**![This image shows the Web Insights Logs](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Users_more_details_view.png)
**
[]Download data in CSV format. The **Download **icon (![Download icon in the Drill Down View](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/about-endpoint-dlp-report-incidents/image%20(19).png)
) is available in every column. When you select an item in a column, the option to export as a CSV file is no longer available for that column.
[]Search by any instance type, such as organization ID, project ID, or resource type in the respective columns.
[]Choose a time frame from the menu to reset the existing data. The options available are last 1 day, last 7 days, last 15 days, last month, and last quarter.
[]Choose an application from the drop-down menu to reset the existing data.
[]![This image shows the Web Insights Logs](/downloads/zia/dashboard-analytics/reports/about-instance-discovery-report/Web_insights_logs.png)
[]![Resource Discovery Report workflow describes the flow of events for the report.](/downloads/zia/dashboard-analytics/reports/viewing-resource-discovery-report/Resource_Discovery_workflow.gif)
![Resource Discovery Report and its additional tabs.](/downloads/zia/dashboard-analytics/reports/viewing-resource-discovery-report/Resource_Discovery_Report_additional_tabs.png)
[]Either the **Domains **or** Tenants **cards are displayed** **depending on the SaaS application you selected in the Instance Discovery Report page. Each card in every column displays the number of transactions for the discovered instances. The percentage indicates the number of transactions for the discovered instance relative to the total number of transactions. The instance types and the associated applications that support level one type of instance discovery are as follows:
- Domains: Box, Google Drive, Gmail, Microsoft Outlook, Microsoft Teams, and OneDrive.
- Tenants: Salesforce and ServiceNow.
![Resource Discovery Report with the domains cards for Level 1 of instance Discovery.](/downloads/zia/dashboard-analytics/reports/viewing-resource-discovery-report/Resource_Discovery_Level_1_gmail.png)
[]For the applications that support two levels of instance discovery, select the card for which you wish to drill down the data, and subsequently, the level two column is updated based on the level one selection. Each card in every column displays the number of transactions for the discovered instances. The percentage indicates the number of transactions for the discovered instance relative to the total number of transactions. For example, for Slack, when you select any of the cards in the **Domains **column, you can drill down to the corresponding card in the **Workspaces **column, thereby showing the mapping between two instance types. The instance types and the associated applications that support level two type of instance discovery are as follows:
- Workspaces: Slack
- Sites: SharePoint
![Resource Discovery Report for level 2 type apps.](/downloads/zia/dashboard-analytics/reports/viewing-resource-discovery-report/Resource_Discovery_Level_2_Slack.png)
- []The **Organizations** column displays the list of organizations discovered for the application. Each organization** **card displays the number of transactions for the organization discovered. The percentage indicates the number of transactions for the organization relative to the total number of transactions.
- (Optional) Choose a time frame from the menu to reset the existing data. The options available are last 1 day, last 7 days, last 15 days, last month, and last quarter.
-
Select the organization for which you want to view the project data.
The **Projects **column displays the list of projects discovered from the selected organization. Each project card displays the number of transactions for the projects discovered. The percentage indicates the number of transactions for the projects relative to the total number of transactions.
-
Select the project for which you want to further drill down the data.
The **Resources **column is updated for the selected project. Each resource card displays the number of transactions for the resources discovered. The percentage indicates the number of transactions for the resource relative to the total number of transactions.
![Resource Discovery Report showing all the three levels of instances for Google Cloud Platform](/downloads/zia/dashboard-analytics/reports/viewing-resource-discovery-report/Resource_Discovery_Level_3_gcp.png)