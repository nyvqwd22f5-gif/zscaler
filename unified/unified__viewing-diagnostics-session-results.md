# Viewing Diagnostics Session Results
Source: https://help.zscaler.com/unified/viewing-diagnostics-session-results
PDF: https://help.zscaler.com/pdf/com/en/1495776.pdf

Diagnostics sessions can provide much more granular information to analyze any issues that your users might be facing. After a session is run, you can see the results by clicking the **View** icon in the session row.
Data for In Progress sessions is updated every minute. Completed Diagnostics sessions show complete session data. All other sessions show partial session data. If the session status is Expired, then no data is seen in the session report.
Diagnostics Session Results
To view Diagnostics session results:
- Click the Name of the session or the **View** icon in the In Progress or the History table. This displays the session information in the same tab.
- Click the **Open in a New Tab** icon to open session results in a new tab. You can use this feature to compare multiple session results.
You can then click the **Export PDF** button to export and save a PDF copy of the session information, as shown in the following image.
[See image.](#ExportPDF)
The session results provide the following details:
- General Diagnostic details include:
- **Name of the User**: This includes the name and email address of the user.
- **Session Type**: The type of session selected during configuration.
- **Status**: This lists the status of the session. To learn more, see [Understanding the Diagnostics Session Status](/unified/understanding-diagnostics-session-status).
- **Application**: The application the session was run on. If you had not chosen an application, this field is empty.
- **Device**: The device the session was run on. If you chose to toggle the Device Probing option off, nothing is listed. To learn more, see [Starting a New Diagnostics Session](/unified/starting-new-diagnostics-session).
- **End time**: This shows the date and time the session ended.
- Depending on what you chose during the session configuration, you see details for:
-
Application
- **Web Probe Metrics**: This section shows data for the Page Fetch Time, Server Response Time, DNS Resolve Time, and Availability. The name of the probe is also listed in parentheses. If you had not selected a Web probe while configuring a session, this section is not displayed. The start and end times of the graphs align with the times for the Diagnostics session.
-
**Cloud Path**: This section displays a graph where you can choose to view either Latency or Packet Loss from the drop-down menu. It shows the Hop View and the Command Line View of the path taken by the probe. You can click the **Zoom** icon to view details of the Cloud Path till the probe reached its destination. If you had not selected a Cloud Path probe while configuring a session, this section is not displayed. The Cloud Path also displays details such as tunnel information and differential latency. To learn more, see [Evaluating the Cloud Path](/unified/evaluating-cloud-path).
If you select a point on a graph, a tooltip with the appropriate metric, the date and time are displayed in all the charts. If there is no data for two consecutive time points, a gap in the charts is displayed. An error message in the chart indicates the issue.
Network applications do not have a web front end, and therefore, Web Probe Metrics are not available. ZDX Scores are calculated using latency with only a single Cloud Path probe. To learn more, see [About Applications](/unified/about-applications-0) and [Monitoring Applications](/unified/monitoring-applications-overview).
- Device
- **Device Health**: This sections displays graphs for CPU Usage, Wi-Fi Signal, Memory, Battery Level, Disk information, and Network information are displayed. Not all Device Health metrics are preselected; in the drop-down menu, you can select the elements you want to review. If you chose to disable the Device Probing while configuring the session, this section is not listed.
- **Top Processes**: This section lists the top processes that are consuming resources by Memory Usage, CPU Usage, Disk Usage, and Network Usage, with the Process ID in parentheses. If the Device Probing option is not selected during configuration, this section is not listed.
- **User Device Events**: This section shows the events for a device for the selected period of time. If the Device Probing option is disabled during configuration, this section is not listed.
The Diagnostics session results display information per options chosen during configuration.
[See image.](#SessionResults)
Saving the Session Report[]
You can access session information by clicking the **View** icon in the session row in the Diagnostics page. For information on data retention limits, see [Ranges and Limitations](/unified/ranges-limitations#diagnostics).
You can also choose to store the Diagnostics session report. Click the **Export PDF** button to convert the report into PDF format. You can then save the PDF report for future reference.
If you have View Only permission for Diagnostics details, you cannot use the Export PDF feature to save the results. To learn more, see [About Diagnostics](/unified/about-diagnostics).
[]![Viewing Deep Tracing session results](/downloads/zdx/diagnostics/viewing-diagnostics-session-results/ZDX-ViewingDiagnostics-1.png)
[]![Export PDF functionality for Deep Tracing](/downloads/tech-pubs-drafts/zdx-draft-articles/viewing-diagnostics-session-results-draft/ZDX-ViewingDiagnostics-ExportPDF.png)