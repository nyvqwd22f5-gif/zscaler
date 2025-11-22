# Scheduling Reports to Export
Source: https://help.zscaler.com/uvm/scheduling-reports-export
PDF: https://help.zscaler.com/pdf/com/en/1529237.pdf

After [creating a report](/uvm/creating-reports), you can schedule the report to be automatically delivered to a specified email address or S3 bucket at regular intervals. This helps automate reporting workflows and ensures timely data delivery without manual effort. You can configure the report format, delivery frequency, recipients, and other delivery details as necessary. For details on additional methods for exporting reports, see [Manually Exporting Reports](/uvm/manually-exporting-reports) and [Triggering Report Export through an API](/uvm/triggering-report-export-through-api).
Newly created reports must be saved before they can be scheduled. To create a new report, see [Creating Reports](/uvm/creating-reports).
To schedule automatic report delivery:
-
Open the desired report and click the **Schedule Export** icon (![Scheduling Reports Icon](/downloads/uvm/explore/reports/scheduling-reports-export/schedule%20export%20icon.png)
) in the top-right corner of the page.
The **Schedule Export Details** window appears.
-
In the **Schedule Export Details** window:
- **Export Format**: Select the export format (**CSV**, **JSONL**, or **Excel**).
- **Active**: Enable to activate the scheduled export.
- **Compression**: From the drop-down menu, select a compression option (**None**, **ZIP File**, **ZST File**).
- **Delivery Method**: Select the delivery method for the report.
- **Email**: Enter one or more recipient email addresses (press `Enter` after each entry). Customize the email **Title** and **Message **content.
- **S3 - AWS S3**: Enter your connection credentials and destination path.
- **Slack**: Configure delivery settings (i.e., **Title**, **Channel Type**, **Channel**, and **Message **content).
- **Frequency and Time**: Set how often and when the report should run (**Daily**, **Weekly**, **Monthly**, or **Custom**).
- Click **Save**.
[See image.](#schedule-report-details-window)
After saving the export settings, save the report to complete the process in one of the following ways:
- Click **Save **to save the report. The report will be exported on schedule.
- From the **Save **drop-down menu, click **Save & Run **to save the report and immediately export it.
- From the **Save **drop-down menu, click **Save As New **to save your changes as a new report.
[]![schedule%20report%20details%20window%20actived.png](/downloads/uvm/analytics/reports/scheduling-reports-export/schedule%20report%20details%20window%20actived.png)
Troubleshooting Scheduled Reports
To monitor the progress and status of scheduled reports, on the Reports screen, hover over the relevant report and click the See Runs icon (![See Runs Icon](/downloads/uvm/explore/reports/scheduling-reports-export/see%20runs%20icon.png)
). The report's Runs page appears, where each row represents an individual report run.
You can customize the displayed columns to add relevant details for troubleshooting. To learn more, see [Managing Table Columns](/uvm/managing-table-columns).
From the Runs page, you can also hover over a run to [download the generated report file](/uvm/manually-exporting-reports), if available. Reviewing this file can help you verify the exported data and troubleshoot issues related to report output or configuration.