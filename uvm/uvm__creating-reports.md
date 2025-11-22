# Creating Reports
Source: https://help.zscaler.com/uvm/creating-reports
PDF: https://help.zscaler.com/pdf/com/en/1527941.pdf

Reports provide a structured way to analyze and present data in the SecOps platform. You can create reports focused on key entities, such as tickets, assets, and findings, customizing them with relevant measurements and dimensions to highlight specific trends or areas of concern. Reports can be processed manually or scheduled for automatic delivery, helping you track progress, support audits, and keep stakeholders informed.
To create a report:
-
Go to **Explore** > **Reports**.
A list of your private reports and public reports you have access to appears.
[See image.](#explore-reports)
-
Click **New**.
A new report page appears.
-
In the top-left corner of the report, click the **Edit** icon.
The **Edit Report Details** window appears.
- In the **Edit Report Details** window:
- **Name**: Enter a unique name for the report.
-
**Viewers**: Set the report's viewer access.
- **Public**: Select this option to grant view access to all users in the account.
- **Selected Users**: Select users from the list to set them as viewers of the report.
To set the report as private and only visible to you, leave the **Viewers** drop-down menu blank.
-
**Editors**: Set the report's editor access.
- **Public**: Select this option to grant edit access to all users in the account.
- **Selected Users:** Select users from the list to set them as editors of the report. Users designated as editors override the **Viewers** setting.
To set the report as private and editable only by you, leave the **Editors** drop-down menu blank.
- **Pin to Apps**: (Optional) Select the application to which you want to pin the report. This allows you to easily find the report under **My Reports** on the app.
- Close the window.
- Select the data type for your report.
-
On the top of the page, set the date filter to either **Current** or **History**.
[See image.](#current-historical-toggle)
-
For historical** **reports, click the date filter to specify the desired date range. You can select a preconfigured range, create a custom range, or set a dynamic range. To learn more about historical data and dynamic range filters, see [Using Filters](/uvm/filtering-operational-views).
[See image.](#date-filter)
- Customize the report's displayed data and filters.
- [Configure the data displayed in the report.](#configure-data)
- [(Optional) Apply filters to the report.](#apply-filters)
- Save the report in one of the following ways:
- Click **Done **to save and close the report, redirecting you to the **Reports **page.
- Click **Save **to save the report. If scheduled, the report exports at the set time.
- From the **Save **drop-down menu, click **Save & Run **to save the report and immediately apply export settings, if configured.
- From the **Save **drop-down menu, click **Save As New **to save your changes as a new report.
Your saved report is accessible on the Explore > Reports page, where it can be accessed, viewed, and exported with all applied configurations.
You can take the following actions with reports:
- View reports directly in the SecOps platform.
- [Manually download reports](/uvm/manually-exporting-reports) as a file.
- [Schedule reports](/uvm/scheduling-reports-export) for automated delivery.
- [Trigger report exports](/uvm/triggering-report-export-through-api) programmatically through an API.
[]![explore > reports](/downloads/uvm/explore/reports/creating-reports/explorereports.png)
[]![date filter current > history toggle](/downloads/uvm/explore/reports/creating-reports/mceclip0.png)
- []Select the **Main Entity** type.
-
From the list on the left, select the dimensions and measurements to include in the report. To remove fields, either deselect them from the list or click the **Remove** icon next to the field name in the report. To learn more, see [Understanding Measurements & Dimensions](/uvm/understanding-measurements-dimensions).
After adding measurements and dimensions to the report, changing the main entity type or the data type (i.e., from **Current** to **History**) resets and discards your selections.
- (Optional) Adjust the table columns and sorting. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
[]![date filter for historical data](/downloads/uvm/explore/reports/creating-reports/mceclip1.png)
[]You can add filters to your report to customize it to your needs. The available filters vary depending on the report's **Main Entity**.
- Click **Add Filters **(if no filters are active) or **More **(if filters are already applied) at the top of the report and select the filter fields. You can use the search bar to refine the list.
- Filter options change according to the filter type (e.g., string, number, or date). To learn more, see [Using Filters](/uvm/filtering-operational-views).
-
To remove a specific filter's values, click the filter field and click **Clear Selection**.
[See image.](#clear-selection)
-
To remove all filters, click **Clear Filters**.
[See image.](#clear-filters)
[]![clear selection for a specific filter field](/downloads/uvm/explore/reports/creating-reports/b78d14c2-b4c6-4055-998c-4017be7d0cc6.png)
[]**![clear all filters](/downloads/uvm/explore/reports/creating-reports/bcffa4b6-d91f-4d8b-b207-c29f9f6ba1e7.png)
**
Reporting Examples
The following examples illustrate different types of reports you can create to support operational visibility, risk management, and data validation. Each report highlights a specific use case and suggests relevant fields to include.
- [Tickets Approaching SLA](#tickets-approaching-sla)
- [Ticket Remediation Rate by Application](#ticket-remediation-rate)
- [Asset Information and Tag Validation](#asset-validation)
[]To monitor tickets nearing their service level agreement (SLA) deadlines, create a report with the following fields:
- **Dimensions**: Ticket ID, Ticket Title, Ticket Severity
- **Measurements**: Ticket Severity Score, Ticket Status
Apply a filter on the **Ticket SLA** field and select the **Next 7 Days** option to focus on tickets at risk of breaching their SLA within the upcoming week.
[See image.](#next-seven-days)
[]![next seven days dynamic filter for tickets approaching SLA example report](/downloads/uvm/explore/reports/creating-reports/51fc24de-44fe-4beb-98bf-2a2855d0bb4f.png)
[]To track the remediation rate across business applications, set up a report with the following fields:
- **Dimension**: Asset Business Application
- **Measurements**: New Tickets Last 7 Days, Undetected Tickets Last 7 Days, Closed Tickets Last 7 Days
This configuration provides insight into ticket volume and remediation activity for each application over the past week.
[]To validate asset data and ensure critical asset tags are accurate, set the **Main Entity** to **Asset** and include the following dimensions:
- Asset Is Crown Jewel
- Asset Is Publicly Accessible
- Asset Owner ID
This report helps confirm whether asset tagging is complete and aligned with your organization's classification and ownership requirements.