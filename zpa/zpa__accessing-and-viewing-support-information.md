# Accessing and Viewing Support Information
Source: https://help.zscaler.com/zpa/accessing-and-viewing-support-information
PDF: https://help.zscaler.com/pdf/com/en/1485056.pdf

This article describes how to add, view, and filter data from App Connectors and ZPA Private Service Edges. Using Support Information, you can create sessions that execute commands on App Connectors and ZPA Private Service Edges, and then filter and view the outputs of these sessions to assist in troubleshooting. For a complete list of ranges and limits for Support Information, see [Ranges & Limitations](/zpa/ranges-limitations#SupportInformation).
Accessing Support Information
To access Support Information, go to **Analytics** > **Support Information**.
By default, the data for all users is displayed for sessions that occurred in the last 14 days. You can perform the following actions on the Support Information page:
- To change the time range, click the time range drop-down menu. In the Calendar drop-down menu, you can select a preset date range or specify a custom start and end date. If you use the **Custom Range **option, the start date must be within the last 6 months.
- To change the time zone, select a new time zone using the time zone drop-down menu.
- To hide the filters on the page, click **Hide Filters**. Click **Show Filters** to show the filters.
- To add a session, click **Add**. To learn more, see the [Adding a Session](#AddingSession) section.
- To expand and collapse all sessions, click the **Expand All** and **Collapse All** icon.
- To refresh the **Support Information** tab, click the **Refresh **icon**.**
[See image.](#supportInformationTools)
[]
![Support Information Tools](/downloads/zpa/dashboard-diagnostics/accessing-and-viewing-support-information/zpa-support-information-page-tools-gif.gif)
Filtering Sessions
On the Support Information page, you can apply filters on the sessions. By default, no filters are applied.
To configure filters:
-
Click on any of the following filters from the drop-down menu:
- **Sessions**: See data by a specific session or multiple sessions.
- **Session Status**: See data by a specific status or multiple statuses.
- **App Connectors**: See data for a specific App Connector or multiple App Connectors.
- **App Connector Groups**: See data for a specific App Connector group, or multiple App Connector groups.
- **Private Service Edges**: See data for a specific ZPA Private Service Edge or multiple ZPA Private Service Edges.
- **Private Service Edge Groups**: See data for a specific ZPA Private Service Edge group or multiple ZPA Private Service Edge groups.
- **Private Cloud Controllers**: See data for a specific Private Cloud Controller or multiple Private Cloud Controllers.
- **Private Cloud Controller Groups**: See data for a specific Private Cloud Controller group or multiple Private Cloud Controller groups.
You cannot apply filters for App Connectors or App Connector groups, Private Service Edges or Private Service Edge groups, and Private Cloud Controllers or Private Cloud Controller groups at the same time.
- Select the fields from the drop-down menu or enter in the values required for the filter. The field value required is determined by the filter you are configuring.
[See image.](#FilteringSessions)
- Click **Apply**.
To apply more filters, click the desired drop-down menu and select the fields. Then click **Apply **to save your selections. To remove an added filter, click the **Close **icon for the field and then click **Apply**. To remove all filters from an individual drop-down menu, click **Clear All**. To reset the filter feature, click **Reset**. You can also save applied filters. To learn more, see [Using Tables](/zpa/using-tables#filterData).
[]**Adding a Session**
To add a session:
- Go to **Analytics **> **Support Information**.
-
Click **Add**.
Sessions that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
The **Add Session** drawer appears.
- Enter the following session information:
- **Name**: The name of the session.
- **App Connectors**: The name of the App Connectors that the data is collected from.
- **App Connector Groups**: The name of the App Connector groups that the data is collected from.
- **Private Service Edges**: The name of the ZPA Private Service Edges that the data is collected from.
- **Private Service Edge Groups**: The name of the ZPA Private Service Edge groups that the data is collected from.
- **Private Cloud Controllers**: The name of the Private Cloud Controllers that data is collected from.
- **Private Cloud Controller Groups**: The name of the Private Cloud Controller groups that data is collected from.
- **Commands**: The command of the session. To learn more, see [Sessions](#Sessions).
-
**Targets**: The destination FQDN or IP address of the session. Separate multiple hostnames with a comma (,) and ports with a colon (:). For example: test.com, example.com:80, example.com:443, 10.1.1.1:8080.
Multiple ports on the same FQDN or IP address require the same FQDN or IP address entered multiple times, separated by commas (e.g., example.com:80, example.com:443). Ports are not allowed for DNS lookup and restart commands.
- **Duration**: The duration for which the command is executed. The minimum duration is 30 seconds, and the maximum duration is 5 minutes. If no value is entered, the default duration is 1 minute. This field appears only when a PCAP command is selected.
- **Interface**: Enter a network interface name to limit the PCAP command to capture packets on a particular interface (e.g., eth0, eth1, eno). This field appears only when a PCAP command is selected.
If you are within a [Microtenant](/zpa/about-microtenants), you can only select App Connectors, App Connector groups, Private Service Edges, Private Service Edge groups, Private Cloud Controllers, and Private Cloud Controller groups that belong to you or are configured within the Microtenant.
[See image.](#AddingaSession)
- Click **Save**.
Viewing Sessions
Sessions are displayed in the table after adding a session.
[See image.](#SessionView)
The table of sessions provides the following information:
- [Number](#Number)
- [Sessions](#Sessions)
- [Start Time](#StartTime)
- [End Time](#EndTime)
- [Status](#Status)
- [Modified By](#modifiedBy)
- [Actions](#Actions)
[]The number of the session. Sessions are listed in descending order, from the newest to oldest session created.
[]Provides the following session information:
- **App Connectors**: See data for the App Connector groups associated with the App Connector. Click the **Download **icon (![Download icon](/downloads/zpa/dashboard-diagnostics/about-support-information/zpa-download-icon_0.png)
) to download a JSON file of the session results. Click the App Connector group to open the **Session Output** window and view the status of the commands on the App Connector.
- **Private Service Edges**: See data for the ZPA Private Service Edge groups associated with the ZPA Private Service Edge. Click the **Download **icon to download a JSON file of the session results. Click the ZPA Private Service Edge group to open the **Session Output** window and view the status of the commands on the ZPA Private Service Edge.
- **Private Cloud Controllers**: See data for the Private Cloud Controller groups associated with the Private Cloud Controller. Click the **Download** icon to download a JSON file of the session results. Click the Private Cloud Controller group to open the **Session Output** window and view the status of the commands on the Private Cloud Controller.
- **Commands**: Displays the command of the session.
- **Targets**: The destination FQDN or IP address. The maximum number of targets allowed is 10.
A maximum of one target is allowed per session for a PCAP command.
- **Duration**: The duration for which the command is executed. This is only applicable for the PCAP commands on App Connectors. The minimum duration is 30 seconds, and the maximum duration is 5 minutes. If no value is entered, the default duration is 1 minute.
Session Commands
The following table provides a list of commands:
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| Command | Description | Example Arguments | Valid Characters | Regular Expression Value |
| ------- | ----------- | ----------------- | ---------------- | ------------------------ |
| DNSLOOKUP AAAA RECORD | The DNS lookup command toresolve AAAA record. Ports are not specified in DNS lookup commands. | confluence.corp.com | Any alphanumeric without a port | ^[a-z0-9-_.]*[a-z]+[a-z0-9-_.]*?$ |
| DNSLOOKUP A RECORD | The DNS lookup command to resolve A record. Ports are not specified in DNS lookup commands. | jira.corp.com | Any alphanumeric without a port | ^[a-z0-9-_.]*[a-z]+[a-z0-9-_.]*?$ |
| DNSLOOKUP SRV RECORD | The DNS lookup command to resolve SRV record. Ports are not specified in DNS lookup commands. | confluence.corp.com | Any alphanumeric without a port | ^[a-z0-9-_.]*[a-z]+[a-z0-9-_.]*?$ |
| DROP DB RESTART PROCESS | The command to delete the local database in the Private Cloud Controller and to restart the Private Cloud Controller process. Canceling a restart command that is in the Processing state is not supported. Restart commands cannot be executed at the same time as a DNS lookup command or another restart command. | No valid arguments | N/A | N/A |
| RESTART PROCESS | The command to restart the App Connector, ZPA Private Service Edge, or Private Cloud Controller process. Canceling a restart command that is in a Processing state is not supported. Restart commands cannot be executed at the same time as a DNS lookup command or another restart command. | No valid arguments | N/A | N/A |
| RESTART SYSTEM | The command to restart the App Connector, ZPA Private Service Edge, or Private Cloud Controller. Canceling a restart command that is in a Processing state is not supported. Restart commands cannot be executed at the same time as a DNS lookup command or another restart command. | No valid arguments | N/A | N/A |
| ICMP PING | The Internet Control Message Protocol (ICMP) ping command to test reachability of a host on an Internet Protocol (IP) network. | Examples of valid arguments:Jira.corp.com1.1.1.1Google.com | Any alphanumeric without a port | ^[a-z0-9-_.]*[a-z]+[a-z0-9-_.]*(:[0-9]+)?$ |
| TCP PING | The Transmission Control Protocol (TCP) ping command to test reachability to a port, or range of ports, for a list of hostnames or IP addresses. | Examples of valid arguments:Jira.corp.com:801.1.1.1:443Google.com:443IP in IPv6 format with port: [2607:f8b0:400a:806:200]:80 | Any alphanumeric with optional port | ^[a-z0-9-_.]*[a-z]+[a-z0-9-_.]*(:[0-9]+)?$ |
| PCAP | The PCAP (Packet Capture or TCP Dump) command to capture network traffic. This allows admins to troubleshoot connectivity between an App Connector, ZPA Private Service Edge, or Private Cloud Controller and ZPA Public Service Edge, or between an App Connector, ZPA Private Service Edge, or Private Cloud Controller and applications. A maximum of one PCAP command per session is allowed. The maximum PCAP file size for a single session is 1 GB, while the maximum size of the individual PCAP files is 100 MB (e.g., if the PCAP capture is 350 MB, then three files are downloaded at 100 MB each, and then one file is downloaded at 50 MB). After the files are downloaded on the host machine, you may merge the files for analysis.After the PCAP session is complete, you can download the session output.To download the session output of the PCAP:Expand the PCAP session in the table.Click the App Connector, ZPA Private Service Edge, or Private Cloud Controller.The **Session Output** window appears.In the **Session Output** window, click the **Download **icon. | Examples of valid arguments:Interfaces: eth0 (optional)Application: jira.corp.com (optional)10.1.1.1 (optional)IP in IPv4 and IPv6 formats: [2607:f8b0:400a:806:200] and [2607:f8b0:400a:806:200]:80FQDN: Fully resolvable by the device as done by tcpdump. The maximum allowed characters is 51IP with port supported: 1.1.1.1:80FQDN with port: abc.com:80 | Any alphanumeric with optional port | N/A |
[]The time when the component starts executing commands. The time displayed is based on the time zone set. To set the time zone, click the time zone drop-down menu at the top of the page.
[]The time when the component finishes executing commands. The time displayed is based on the time zone set. To set the time zone, click the time zone drop-down menu at the top of the page.
[]Displays the status of the session. Sessions with a Pending or Processing status auto-refresh every 60 seconds to reflect the most current status.
Session Status
The following table provides a list of potential statuses:
| Status | Description |
| ------ | ----------- |
| Pending | Default status of a command when it’s first inserted into the database. Sessions can only be canceled when they’re in the Pending or Processing state. Canceling a restart command that is in a Processing state is not supported. |
| Processing | App Connector or ZPA Private Service Edge picked up the command for execution. |
| Completed | Command execution is successful. |
| Failed | Command execution failed. |
| Cancelled | Command that is sent to the App Connector or ZPA Private Service Edge is canceled. |
| Partially_completed | Part of the command has succeeded and part has failed. |
By default, all sessions are deleted after 14 days, regardless of the status of the session. Sessions that are in a Pending or Processing state are moved to a Cancelled state after 600 seconds (10 minutes), and continue to be moved every 10 minutes.
If an App Connector or ZPA Private Service Edge is in a disconnected state, then the status for that App Connector or ZPA Private Service Edge is always in a Failed state. If there is a session that contains some App Connectors or ZPA Private Service Edges in a disconnected state and some in a connected state, then the session status is Partially_completed. The final session status depends on the combined status of the entities.
Session commands can get rejected and move to a Failed state when an App Connector or ZPA Private Service Edge is in a paused state. The App Connector or ZPA Private Service Edge rejects and does not process any new incoming sessions until the paused state expires. To learn more, see [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors#pauseState) and [Troubleshooting ZPA Private Service Edges](/zpa/troubleshooting-zpa-private-service-edges#pauseState).
[]Displays the name of the ZPA tenant who modified the session.
[]Displays the following actions:
- **Redo**: Open the **Edit Session** window to edit the configuration of the session. Click **Save **to copy and apply the new configuration.
- **Download**: Download the session data in JSON format.
- **Comment**: Open the **Description **window to leave a comment on a session. Click **Save **to apply the comment.
- **Delete**: Delete a session.
[See image.](#ActionIcons)
[]![Filtering a Session](/downloads/tech-pubs-drafts/zpa-draft-articles/accessing-and-viewing-support-information-doc-59485/zpa-support-information-filter-chips.png)
[]![Add Session Drawer in the Support Information Page of the ZPA Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/accessing-and-viewing-support-information-doc-59485/zpa-support-information-add-session-drawer.png)
[]![Viewing Support Information](/downloads/tech-pubs-drafts/zpa-draft-articles/accessing-and-viewing-support-information-doc-59485-doc-57735/zpa-support-information-data-table.png)
[]![Action Icons for Support Information](/downloads/zpa/dashboard-diagnostics/about-support-information/zpa-support-information-actions.png)