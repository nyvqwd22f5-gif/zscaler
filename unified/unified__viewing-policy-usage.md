# Viewing Policy Usage
Source: https://help.zscaler.com/unified/viewing-policy-usage
PDF: https://help.zscaler.com/pdf/com/en/1531250.pdf

Policy Usage insights provides you with a deeper understanding and details about the distribution of access policy rules used by users. These insights can help you assess and determine unused access policy rules for improvement consideration. The Policy Usage insights provide:
- A distribution of users and their associated access policy rules.
- Most used access policy rules.
- Least used access policy rules.
[See image.](#PolicyUsageGIF)
Policy Usage Report
The Policy Usage Report contains the following information:
-
The number of Access Policy Rules applied to the distribution of users.
- **Most Used Access Policy Rules**: Displays the number of most used access policy rules.
- **Unused Access Policy Rules**: Displays the number of the least used access policy rules. These include unused access policies.
The distribution of users is calculated based on the number of unique users (must be more than zero users) against each access policy rule. Then the distribution categorizes the users into 1 of 10 percentage bars based on their usage of the access policy rule. Each bar indicates a tenth percentage of access policy rules based on usage. You can click on a bar to view policy usage data based on that user group. The percentage is rounded to the nearest whole number.
-
**Current Report Information**: Displays the current report's information.
[See image.](#CurrentReportInformation)
- **Launch Tour**: Launches a series of guided steps on how to interact with the Policy Usage page.
-
**Run Report**: Generate the report to include data from the selected time range. The report automatically expires after 90 days. You cannot run the report if there is no more data to add when the report was recently updated.
Run Report is disabled for 72 hours before and after 12:00 AM on the first Saturday of every other month. Customers with the Segmentation Add-On can generate one report per day, and customers without the license can generate one report every 90 days.
[See image.](#RunReport)
[See image.](#PolicyUsageReportInformation)
Policy Usage Chart and Table
The Policy Usage chart and table provides the following information:
-
**Policy Usage Bar Chart**: Displays the distribution of policy usage from access policy rules. Select a bar to specify the access policy rules. The default is set to Unused Access Policy Rules.
[See image.](#BarChartSelection)
-
**Access Policy Rule Filter**: Select specific access policy rules for display.
[See image.](#AcessPolicyRuleFilter)
- **View Access Policy**: Allows you to access the [Access Policy](/unified/about-access-policy) page to manage the access policies.
- **Access Policy Rules Table**: Displays the following information for each access policy:
- **Access Policy Rule**: The name of the access policy rule.
- **Unique Users**: The number of unique users impacted by the access policy rule.
- **Transactions**: The number of Private Applications transactions going through the access policy.
- **Actions**: The available actions for the access policy rule.
- **Edit**: Edit the access policy rule in the **Edit Access Policy** window. To learn more, see [Editing Access Policies](/unified/editing-access-policies).
- **Policy Hit and User Details**: View the access policy rule's policy usage details. To learn more, see [Viewing Policy Usage Details](/unified/viewing-policy-usage-details).
[See image.](#PolicyUsagePage)
[]
![Policy Usage Page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsagePage-2.png)
[]
![Access Policy Rule Filter](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsage-AccessPolicyRuleFilter-1.png)
[]
![Bar Chart Selection](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsageBarChart-1.png)
[]
![Current Report Information](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsage-CurrentReportInformation.png)
[]
![Policy Usage Report Information](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsageInformation.png)
[]
![Policy Usage Page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsagePageGIF-1.gif)
[]
![Run a Report](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-policy-usage/ZPA-PolicyUsage-RunReport.png)