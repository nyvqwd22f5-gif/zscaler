# Scheduling Application Reports
Source: https://help.zscaler.com/business-insights/scheduling-application-reports
PDF: https://help.zscaler.com/pdf/com/en/1483171.pdf

You can schedule activity reports for applications and distribution to various email recipients and Workflow Automation.
To schedule a report:
- Go to **Analytics** > **Reports** > **Application Reports.**
-
Click **New Scheduled Report**.
[See image.](#new-report-button)
The **Add Scheduled Report** page appears.
- On the **Add Scheduled Report** page:
- **Name**: Enter a name for the report (e.g., `Slack Inactivity Report`).
- **Report Enabled**: Enable or disable the report.
- **Application**: Select the applications for which you want to schedule the report. The applications are listed with their data source inside the parentheses.
- **Who - Users Tracked**: Select the users you want included and excluded from the report.
- **Included Users**: Select the users for whom you want to view the activity or inactivity report.
- **All**: Select this option to include all your organization's users in the report.
- **Subset**: Select the users, departments, or both that you want included in the report. You can select up to 128 users and departments.
- **Excluded Users**: Select the users you want to exclude from the report. Click **Exclusion List** to view the list of exclusions or to add and enable new exclusions for the report.
- **No Exclusions**: Select this option if you don't want to add any exclusions to the report.
-
**Apply Exclusions**: Select one or both of the following options:
- **Exclusion List**: Select this option to exclude the users and departments configured in the [exclusion list](/business-insights/about-exclusion-list). Exclusions are associated with only those scheduled reports where the applications configured in both the scheduled report and the exclusion match.
- **Custom**: Select this option to add custom users and departments to exclude from the report. Select the** Users** and **Departments** you want excluded from the report from the drop-down menus.
Any modification to the exclusion list affects all the scheduled reports where **Exclusion List** is applied. To exclude report-specific users, Zscaler recommends enabling the **Custom** option and selecting users and departments.
- **What - Action Cadence**: Select the report type you want to schedule:
- **Inactivity Period**: Select this option to generate the inactivity report for the application.
- **Activity** **Period**: Select this option to generate the activity report for the application.
- **Cadence**: Select the time frame for which you want to generate the report from **1 day**, **30 days**, **60 days**, or **90 days**.
- **When - Delivery Schedule**: Select the report generation and delivery schedule from **Daily**, **Weekly**, **Monthly**, or **Quarterly**. You can view the date the next report is due to be generated for each schedule.
-
**How - Delivery Method**: Select the delivery method of the report. You can select one or both of the following options:
- **Workflow Automation**: Select this option to integrate the report with [Workflow Automation](/workflow-automation/what-workflow-automation). To test the Workflow Automation integration, enter the recipients' email addresses and click **Submit Test**. The recipients receive a test email confirming successful integration.
- **Email**: Select this option and enter the email addresses of the recipients that receive the report via email.
[See image.](#add-report)
The following GIF shows how to set the criteria to run scheduled reports every week on Adobe Creative Cloud's user inactivity for the last 90 days for all users in your organization. Apply the exclusion list with a custom exclusion of the Contractor department via email delivery.
[See image.](#example-criteria)
-
Click **Save**.
The report is successfully scheduled. You can view the scheduled report on the [Application Reports](/business-insights/about-application-reports) page.
[]![Scheduling a Report](/downloads/business-insights/scheduling-reports/Business-Insights-Scheduling-Report.gif)
[]![Add Scheduled Report Page in Business Insights Admin Portal](/downloads/business-insights/reports/scheduling-reports/Business-Insights-Add-Scheduled-Report-Page.png)
[]![New Schelduled Report button on the Application Reports page](/downloads/tech-pubs-drafts/business-insights-draft-articles/scheduling-application-reports-55631/Business-Inisghts-New-Application-Report-Button.png)