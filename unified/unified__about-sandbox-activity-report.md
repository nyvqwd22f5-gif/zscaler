# About the Sandbox Activity Report
Source: https://help.zscaler.com/unified/about-sandbox-activity-report
PDF: https://help.zscaler.com/pdf/com/en/1497471.pdf

The Sandbox Activity Report highlights the [Sandbox policy action](/unified/configuring-sandbox-policy) taken for known and unknown files in your organization. Unknown files are files that the Sandbox encounters for the first time. Files known by cloud effect are files from any organization that the Sandbox analyzed and classified as malicious or benign.
The Sandbox Activity Report also highlights the threat categories, threat names, URL categories, and file types of known and unknown files after Sandbox analysis. You can view the data by transactions or specific files. You can view weekly reports from the last six months, not including the current week.
About the Sandbox Activity Report Page
On the Sandbox Activity Report page (Analytics > Internet & SaaS > Analytics > Sandbox Activity Report), you can do the following:
- View the [Sandbox Files Found Malicious report](/unified/about-sandbox-files-found-malicious-report) (requires the Advanced Sandbox).
- Choose the week to view the report for.
- View the data by **Transactions** or **Unique Files**. Transactions include all download attempts, even of the same file. Unique Files count each file once, regardless of the number of transactions.
- Print the report.
- Export the displayed transactions to a PDF or JSON file.
- Schedule or manage email deliveries of the Sandbox Activity Report.
- **Add Schedule**: Schedule a weekly email delivery of the Sandbox Activity Report. The email contains a report preview and a link to the full report. To learn more, see [Scheduling the Sandbox Activity Report Weekly Email](/unified/scheduling-sandbox-activity-report-weekly-email).
- **Manage Schedule**: If you have scheduled a weekly email delivery, view the Scheduled Reports page to edit or delete the scheduled delivery. To learn more, see [About Scheduled Reports](/unified/about-scheduled-reports).
- Show or hide the detailed explanations under the widgets.
- View the [widgets](/unified/about-widgets) in the report.
- [Widget List](#widget-list)
![Screenshot highlighting the Sandbox Activity Report features.](/downloads/zia/policies/sandbox/about-sandbox-activity-report/ZIA-Sandbox-Activity-Report-Features-6_1.png?1615246814)
- []**Unknown Files & Files Known by Cloud Effect**: Shows how many files were known benign or known malicious by cloud effect, or unknown and sent for Sandbox analysis.
-
**Policy Actions & Verdicts for Files Known by Cloud Effect**: Shows how many known benign or malicious files were allowed or blocked.
Known malicious files might have been allowed because you don't have the Advanced Sandbox subscription or the right [Sandbox rule](/unified/configuring-sandbox-policy) configured. Zscaler recommends investigating these files.
-
**Policy Actions & Verdicts for Unknown Files**: Shows how many files were found malicious after being sent for Sandbox analysis. A situation might occur where a file that has been quarantined could also be counted under **Allow & Scan** if the file was allowed while in quarantine. For example, user A has a quarantine Sandbox rule applied to them, and user B has an allow and scan rule applied to them. User A attempts to download an unknown file that is sent for Sandbox analysis because of the quarantine rule. While the unknown file is being analyzed, user B can download the same file because of the allow and scan rule. In this case, the file would be counted under **Quarantine** and **Allow & Scan**.
Malicious files downloaded due to the **Allow & Scan** policy action are [patient 0 events](/unified/configuring-patient-0-alert). Zscaler recommends investigating these files.
- **Threat Categories for Malicious Files Known by Cloud Effect**: Shows the threat categories of files that were known malicious by cloud effect.
- **Threat Categories for Unknown Files Found Malicious**: Shows the threat categories of files analyzed and found malicious.
- **URL Categories for Unknown Files**: Shows the URL categories for the destination URLs that were accessed to download unknown files that were sent for analysis.
- **URL Categories for Malicious Files Known by Cloud Effect**: Shows the URL categories for the destination URLs from which users attempted to download files that were known malicious by cloud effect. If you notice many malicious files coming from specific URL categories, consider modifying the [Sandbox policy](/unified/configuring-sandbox-policy) to quarantine files from those URL categories.
- **Threat Names for Unknown Files Found Malicious**: Shows the top threat names seen across all files analyzed and found malicious.
- **Threat Names for Malicious Files Known by Cloud Effect**: Shows the top threat names seen across all files that were known malicious by cloud effect.
- **File Types for Malicious Files Known by Cloud Effect**: Shows the files that were known malicious, by file type.
- **File Types for Unknown Files**: Shows the files analyzed and found malicious, by file type. If you notice specific file types being found malicious frequently, consider modifying the [Sandbox policy](/unified/configuring-sandbox-policy#first-time-action) to quarantine them.