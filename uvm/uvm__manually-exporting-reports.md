# Manually Exporting Reports
Source: https://help.zscaler.com/uvm/manually-exporting-reports
PDF: https://help.zscaler.com/pdf/com/en/1529238.pdf

After [creating a report](/uvm/creating-reports), you can access the saved report on the Explore > Reports page. From there, you can manually export the report by downloading it directly from the Reports page. Manually downloading reports can be useful for quick reviews, one-time analyses, or sharing data without setting up automation. For details on automated exporting methods, see [Scheduling Reports to Export](/uvm/scheduling-reports-export) and [Triggering Report Export Through an API](/uvm/triggering-report-export-through-api).
There are two methods for manually downloading the report:
- [Exporting as CSV](#export-as-csv)
- [Downloading the Report](#download-report-file)
[]You can export reports directly within the report page by clicking the **Export as CSV** icon, located at the top right of the report.
[See image.](#export-as-csv-icon)
This method is ideal for smaller datasets. There is a limit of 100K rows; reports with more than 100K rows export only the first 100K. For larger datasets, consider the Download Report File option.
[]![Export as CSV icon located at the top right of the report](/downloads/uvm/explore/reports/creating-reports/3ddb66b7-dd21-4a6b-8ade-5de2a964e2ea.png)
[]To export reports with over 100K rows of data, or to export reports in one of the three available formats (CSV, JSONL, EXCEL):
- Schedule the report, or locate an existing scheduled report.
-
On the **Reports** page, hover over the report and click the **See Runs** icon.
[See image.](#reports-see-runs)
- Click the latest run.
- Click **Download Report File**.** **This downloads the report in the format configured in the scheduled report.
[See image.](#download-report-file-button)
You must run the report at least once before the download option is available. To run the report, hover over the report and click the **Rerun** icon.
[See image.](#rerun-report)
[]**![See Runs icon when hovering over a report](/downloads/uvm/explore/reports/creating-reports/bbec0ae0-b508-47ba-948c-cd1fb0052cd5.png)
**
[]**![Download Report File button in the report's expanded run](/downloads/uvm/explore/reports/creating-reports/bd7443d4-bd02-4c02-bbdb-ef44a8127cb6.png)
**
[]**![Rerun icon when hovering over a report](/downloads/uvm/analytics/reports/scheduling-reports-export/hover%20over%20report%20rerun%20icon.png)
**