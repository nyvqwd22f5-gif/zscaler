# About Diagnostics
Source: https://help.zscaler.com/unified/about-diagnostics
PDF: https://help.zscaler.com/pdf/com/en/1495706.pdf

Diagnostics in Digital Experience Monitoring can provide deeper granularity into process-level information for a user. During a Diagnostics session, information is collected every minute for the Web probe and Cloud Path probe, as well as device statistics.
Prerequisites
To start a Diagnostics session, ensure:
- You're running the minimum required versions of Zscaler Client Connector and ZDX Module.
- Your Digital Experience Monitoring subscription level supports Diagnostics. To learn more, see [Ranges & Limitations](/unified/ranges-limitations#diagnostics).
- Your admin role is configured for Diagnostics. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
If you still can't view the Diagnostics details in the Admin Portal, contact your Digital Experience Monitoring admin to check your permissions.
You can [start a Diagnostics session](/unified/starting-new-diagnostics-session) to analyze issues that a user, device, or application is facing. You can choose to run the session to monitor issues from 5 minutes to 60 minutes. You can [view session information](/unified/evaluating-diagnostics-session-information) on the Diagnostics page and also export it as a PDF file for reference and information sharing.
Diagnostics provides the following benefits and enables you to:
- Configure Diagnostics sessions to capture granular details (e.g., PCAP information, device statistics, or application information).
- Analyze, evaluate, and troubleshoot issues for a user, device, or application.
- Share the results and information of the Diagnostics session for reference by exporting it to a PDF file.
About the Diagnostics Page
On the Diagnostics page (Diagnostics), you can do the following:
- [View information on sessions in the In Progress table](/unified/evaluating-diagnostics-session-information).
- [View information on sessions in the History table](/unified/evaluating-diagnostics-session-information).
- [View Packet Capture (PCAP) information](/unified/evaluating-diagnostics-session-information) and copy specific PCAP information (e.g., Packet Capture Filter, Network Interface) to your clipboard.
- [View the individual Diagnostics session](/unified/evaluating-diagnostics-session-information) and export a PDF file of the results.
- Copy the details of the selected Diagnostics session and [start a new Diagnostics session](/unified/starting-new-diagnostics-session) with all details of an existing session copied. All fields are editable.
- End a session in the In Progress table.
- Delete a session by using the Delete icon. Deleting a session removes it from the Diagnostics page.
- [Start a new session.](/unified/starting-new-diagnostics-session)
To start a Diagnostics session, an active probe is required on the device. The active probe must run for a minimum duration of 30 minutes. To learn more, see [Configuring a Probe](/unified/configuring-probe).
![Diagnostics Page](/downloads/zdx/diagnostics/about-diagnostics/zdx-releasenote-diagnostics-android-chromeos-2_0.png)