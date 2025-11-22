# Evaluating Diagnostics Session Information
Source: https://help.zscaler.com/zdx/evaluating-diagnostics-session-information
PDF: https://help.zscaler.com/pdf/com/en/1443581.pdf

Diagnostics sessions for your organization are displayed in the **In Progress** and the **History** tables. Sessions in both tables display the following information:
- **Expand**: This describes the Packet Capture (PCAP) information entered during configuration for the selected session.
- **Name**: The name entered for the session during configuration.
- **Session Type**: The type of session selected during configuration.
- **User**: The name and email address of the user are listed.
- **Device**: The device analyzed for the session.
- **Created Time**: The time the session was created by the ZDX admin.
- **Start Time**: The time that Zscaler Client Connector accepted the request and started collecting data.
- **Status**: The current session status differs depending on the table in which the session is listed. To learn more, see [Understanding the Diagnostics Session Status](/zdx/understanding-diagnostics-session-status).
- **Application**: The application being monitored for the session.
- **Created By**: The name and email address of the admin who created the session.
The following information is seen only in their respective tables:
- **Duration (minutes)**: How long the Diagnostics Session is, in minutes, in the **In Progress** table.
- **Probe Settings**: The type of probes used to monitor the Diagnostics Session in the **History** table.
- **End Time**: The time the session ended in the **History** table.
By default, the lists are sorted by the Start Time, displaying the session with the latest Start Time first. You can also sort the sessions by using the Sort arrows next to the column names.
![Diagnostics](/downloads/zdx/diagnostics/evaluating-diagnostics-session-information/evaluating-diagnostics.png)