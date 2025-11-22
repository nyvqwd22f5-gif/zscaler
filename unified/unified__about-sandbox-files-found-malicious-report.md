# About the Sandbox Files Found Malicious Report
Source: https://help.zscaler.com/unified/about-sandbox-files-found-malicious-report
PDF: https://help.zscaler.com/pdf/com/en/1497481.pdf

You must have Advanced Sandbox to view the Sandbox Files Found Malicious report.
The Sandbox Files Found Malicious report highlights unknown files that were sent to Sandbox for analysis and found to be malicious. You can click the file MD5 hash to see the [Sandbox Detail Report](/unified/viewing-sandbox-reports-and-data#about-sandbox-detail-report), view additional transaction information in [Web Insights](/unified/about-insights-logs), and export the report to a CSV file. You can view weekly reports from the last six months, not including the current week.
You can view the report in the Admin Portal by going to Analytics > Internet & SaaS > Analytics > Sandbox Activity Report and choosing Sandbox Files Found Malicious from the Sandbox Activity Report drop-down menu.
[See image.](#seeimage1)
About the Sandbox Files Found Malicious Report Page
On the Sandbox Files Found Malicious page (Analytics > Internet & SaaS > Analytics > Sandbox Activity Report), you can do the following:
- View the [Sandbox Activity Report](/unified/about-sandbox-activity-report).
- Choose the week to view the report for.
- Search and filter the transactions by keywords or phrases.
- Print the report.
- Export the displayed transactions to a PDF or CSV file.
- Schedule or manage email deliveries of the Sandbox Files Found Malicious report.
- **Add Schedule**: Schedule a weekly email delivery of the Sandbox Files Found Malicious report. The email contains a report preview and a link to the full report. To learn more, see [Scheduling the Sandbox Files Found Malicious Report Weekly Email](/unified/scheduling-sandbox-files-found-malicious-report-weekly-email).
- **Manage Schedule**: If you have scheduled a weekly email delivery, view the Scheduled Reports page to edit or delete the scheduled delivery. To learn more, see [About Scheduled Reports](/unified/about-scheduled-reports).
- View a list of files that were found to be malicious. For each file, you can see the following:
- **MD5**: The MD5 of a file that your organization has seen for the first time. Click to view the [Sandbox Detail Report](/unified/viewing-sandbox-reports-and-data#about-sandbox-detail-report).
- **Category**: The classified threat category of the file.
- **Threat Name**: The threat name found during Sandbox analysis. Click to view it in the [Zscaler Threat Library](https://threatlibrary.zscaler.com/).
- **File Type**: The file type for the file.
- **File Size**: The file size for the file.
- **Allowed Transactions**: The number of allowed transactions for the file before the file was found to be malicious. These transactions are [patient 0 events](/unified/configuring-patient-0-alert). The users' devices that successfully downloaded the malicious file might be compromised.
- **Blocked Transactions**: The number of blocked transactions for the file after the file was found to be malicious.
- **Analyzed On**: The time the Sandbox engine analyzed the file.
- View transactions of the file in [Web Insights Logs](/unified/about-insights-logs) for the selected week.
- [Modify the table and its columns](/unified/using-tables).
![Screenshot highlighting the features of the Sandbox Files Found Malicious report.](/downloads/zia/policies/sandbox/about-sandbox-files-found-malicious-report/ZIA-Sandbox-Files-Found-Malicious-Report-6_1.png?1615246868)
[]![The Sandbox Files Found Malicious option in the Sandbox Activity Report dropdown menu.](/downloads/zia/policies/sandbox/about-sandbox-files-found-malicious-report/zia-sandbox-files-found-malicious-option-6_1.png)