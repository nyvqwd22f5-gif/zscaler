# Scheduling Reports
Source: https://help.zscaler.com/unified/scheduling-reports
PDF: https://help.zscaler.com/pdf/com/en/1497611.pdf

You can schedule standard and custom reports for regular distribution to specified recipients. To learn more about scheduled reports, see [About Scheduled Reports](/unified/about-scheduled-reports).
An organization can schedule up to 500 reports.
You can view and manage scheduled reports. A super admin can view and edit all scheduled reports. Other administrators can view and manage their own scheduled reports only.
To schedule a report:
- Do one of the following:
-
Go to **Analytics** > **Internet & SaaS** > **Analytics** > **Interactive Reports** > **Scheduled Reports**, and then click **Add**.
[See image.](#Scheduled_reports_add_icon)
-
Go to **Analytics** > **Internet & SaaS** > **Analytics** > **Interactive Reports**, select a report, and then click the **Schedule** icon.
[See image.](#Interactive_reports_schedule_icon)
- []In the **Add Scheduled Report** window:
- **Schedule Name:** Enter a unique name for the schedule.
- **Report: **Choose the report that you want to schedule.
- **Recipients:** Enter the email addresses of the recipients. Each email address must be on a separate line. You can send the report to up to 32 email addresses.
- **Status:** Select **Enabled** to activate the schedule.
- **Frequency:** Select a schedule as follows:
- Select **Daily** if you want the report for the previous day from 12:00:00 AM to 11:59:00 PM. The report is delivered to the specified recipients at the specified time.
- Select **Weekly** if you want the report delivered to the specified recipients every Monday at 9:00 AM.
- Select **Monthly** if you want the report delivered to the specified recipients on the first day of every month.
- **Sent at: **The time at which the report is to be sent.
-
**Time Zone:** Choose the time zone that the service uses when it generates the report.
[See image.](#add-scheduled-report)
-
Click** Save**. The service sends the report to the specified recipients, as scheduled.
The recipients receive an email with a link to the report. When the recipients click the link, they see the report in Print View.
Anyone who has the link can access the report. The link is valid for 15 days only.
For a daily report, the link displays the report for the time interval for which the report was scheduled. For example, if an administrator receives a scheduled report email for the current day data once a month, but does not open it for a week, the report displays data for the first of the month and not the date that the report was viewed.
Recipients can only view the report; they cannot edit it or navigate to any other area of the Admin Portal. If a recipient copies and pastes the URL of the report, the Admin Portal login page appears and the recipient is required to enter a valid username and password to log in.
[]![The Add Scheduled Report window and its fields](/downloads/zia/dashboard-analytics/reports/scheduling-reports/ZIA_Add_scheduled_reports_page_window.png)
![The Add icon in the Scheduled Reports tab](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/scheduling-reports/ZIA-6.1-Scheduled-Reports-Tab-Add.png)
[]
![The Schedule icon in a standard report page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/scheduling-reports/ZIA-6.1-Schedule-Report-Icon.png)
[]