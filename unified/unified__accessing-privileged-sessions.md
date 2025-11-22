# Accessing Privileged Sessions
Source: https://help.zscaler.com/unified/accessing-privileged-sessions
PDF: https://help.zscaler.com/pdf/com/en/1496476.pdf

To view the privileged session recordings for Privileged Remote Access (PRA), go to **Logs **>** Insights **> **Privileged Sessions**.
Privileged Sessions Tools
The Privileged Sessions page displays the following information and functionality:
- **Time Range Filter**: View Privileged Sessions data over a period between 1 Hour to 365 Days. To change the time range, click the **Calendar** menu and select a preset range or select **Custom Range**. If you use **Custom Range**, the start date must be within the last 365 days. The end date automatically sets to the system's current time. To change the time zone, click the current **Time Zone** button. This filter applies to all widgets on the Privileged Sessions page. By default, the detailed activity for all privileged session recordings is displayed for privileged sessions that occurred in the last 24 hours.
- **Play Offline Recording**: Available only on the Recordings page. Select this option to play privileged recordings that have already been downloaded.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information.
[See image.](#Tools)
Viewing Live Privileged Sessions
Privileged sessions that are currently live are displayed after navigating to the Privileged Sessions page (**Analytics** > **Privileged Sessions **> **Live**).
By default, the table displays the **Total** number of live privileged sessions. You can change this by choosing one of the following filters:
- **RDP**: The total number of live privileged sessions for privileged consoles that are RDP-enabled.
- **SSH**: The total number of live privileged sessions for privileged consoles that are SSH-enabled.
- **VNC**: The total number of live privileged sessions for privileged consoles that are VNC-enabled.
[See image.](#LiveTotal)
Filtering Live Privileged Sessions
On the Live page, you can apply filters or drill down further into the live privileged sessions data using the Query Builder. By default, no filters are applied.
To configure filters using the [Query Builder:](#LiveQuery)
- Click **Add Filters** and select a filter from the drop-down menu.
- Select an operator from the drop-down menu (e.g., **Contains**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the Contains operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., `137`; `138`; `139`). When configuring multiple text entries and using the **Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than** operator, the results show transactions starting from the smallest entry provided.
[See image.](#Livefilter)
- Click **Apply**.
To apply more filters, click **Add Filters** again or click the** Filter** icon (![zpa-filtericon.png](/downloads/zpa/dashboard-diagnostics/accessing-privileged-sessions/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then click **Apply**. To remove all filters, click **Clear All**.
The table displays the following data for live privileged sessions:
- **Connection**: Displays the date and time that the privileged session began.
- **Policy**: The privileged capabilities policy set for the user whose live privileged session it is.
- **Host**: The name of the user whose live privileged session is displayed.
- **Console**: The privileged console that the live privileged session is in.
- **Console Type**: The protocol (RDP, SSH, or VNC) enabled for the associated privileged console.
- **Actions**: These icons only show if they have been enabled for the privileged console associated with the live privileged session.
- **Monitor**: Click the **Monitor** icon to join the associated privileged session. Your administrator email is automatically added to the session, and a new tab is opened to connect to the live session using that email. It can take up to 30 seconds for the monitored session to be disconnected after the initial session is disconnected.
- **Share**: Click the **Share** icon to invite another user to the session.
- **Terminate**: Click the **Terminate** icon to delete the privileged approval associated with the user in the listed live privileged session. This ends the live privileged session. Ending the session also stops the session for any current participants. The **Terminate** option only appears if the user listed for the live privileged session has an associated privileged approval.
When a live privileged session is terminated using the **Terminate** icon on the Live page of Privileged Sessions within the Admin Portal, the Diagnostics logs do not display the participants.
If you expand a row, you can see the participants for the live privileged session. Only the 5 most recent participants are shown.
[See image.](#Participants)
Viewing Recordings
Recordings for privileged sessions are automatically displayed after navigating to the Privileged Sessions page (**Analytics** > **Privileged** **Sessions** > **Recordings**).
By default, the table displays the **Total** number of privileged session recordings. You can change this by choosing one of the following filters:
- **RDP**: The total number of privileged session recordings for privileged consoles that are RDP-enabled. The total byte size for the privileged session recordings for this privileged console type is also listed.
- **SSH**: The total number of privileged session recordings for privileged consoles that are SSH-enabled. The total byte size for the privileged session recordings for this privileged console type is also listed.
- **VNC**: The total number of privileged session recordings for privileged consoles that are VNC-enabled. The total byte size for the privileged session recordings for this privileged console type is also listed.
[See image.](#Totals)
Filtering Recordings
On the Recordings page, you can apply filters or drill down further into the recordings data using the Query Builder. By default, no filters are applied.
To configure filters using the [Query Builder:](#query)
- Click **Add Filters** and select a filter from the drop-down menu.
- Select an operator from the drop-down menu (e.g., **Contains**). The operators available are determined by the filter you are configuring.
- Select the fields from the drop-down menu or enter the values required for the filter. The field or value required is determined by the filter you are configuring.
Filters using the **Contains** operator allow a maximum of 7 entries. All filters using operators that require text input must use a semicolon (;) to separate multiple entries (e.g., `137`; `138`; `139`). When configuring multiple text entries and using the** Less Than** operator, the results show transactions starting from the largest entry provided. When configuring multiple text entries and using the **Greater Than **operator, the results show transactions starting from the smallest entry provided.
[See image.](#Filteroptions)
- Click **Apply**.
To apply more filters, click **Add Filters** again or click the** Filter **icon (![zpa-filtericon.png](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/txnUsersDiagnostics/zpa-filtericon.png)
) within the table. The filter query section within the page updates automatically to include the proper filter for the field name you selected, along with the applicable operator configuration for that field.
To remove an added filter, click the **Close** icon then click **Apply**. To remove all filters, click **Clear All**.
The table displays the following data for Privileged Sessions Recordings:
- **Connection**: Displays the date and time that the privileged session began recording.
- **Recording Duration**: The length of time that the privileged session was recorded.
- **Status**: The status of the privileged session recording.
- **Failed**: The recording cannot be created because the associated privileged session wasn't started due to invalid credentials or network issues.
- **Completed**: The associated privileged session is completed but the recording is not yet available.
- **Available**: The recording is available to download and view. This privileged session is not ready for streaming. Click the **Transcode Now** icon in the Actions column to move the recording to higher priority in the transcode queue.
- **Enqueued**: The recording is waiting in the queue with low priority to be transcoded.
- **Transcode Now**: The **Transcode Now** icon in the Actions column has been selected for this recording. The recording is at a higher priority to be transcoded in the queue.
- **Enqueued On Priority**: The recording is waiting in the queue as a higher priority to be transcoded.
- **Transcoding**: The recording file is currently being converted from a raw format to a streamable format.
- **Ready for Streaming**: The transcoding of the privileged session is complete and ready to view.
- **Transcoding Failed**: The transcoding process was unable to be completed for this recording.
- **Policy**: The privileged capabilities policy set for the recorded privileged console.
- **User**: The user who accessed the privileged console for that privileged session recording.
- **Console**: The privileged console that the privileged session was recorded in.
- **Console Type**: The protocol (RDP, SSH, and VNC) enabled for the recorded privileged console.
- **Actions**: The actions that you can take related to the privileged session recording.
- **Play**: Click the **Play** icon to play a recording.
- **Download**: When you click the **Download** icon, the recording is downloaded to the local system of the server. This option is available when [Session Recordings is set to Full Access when configuring an Admin role](/unified/configuring-administrator-roles).
- **Transcode Now**: Click the **Transcode Now** icon to begin formatting a raw privileged recording to streamable content. The status of the privileged recording updates to the **Transcode Now** status. This icon can only be selected when the privileged recording is in the **Available**, **Enqueued**, or **Transcoding Failed** status.
[See image.](#table)
Playing a Session Recording
When you expand the privileged session recording, some of the information from the Recordings table columns for that privileged session recording is displayed. If you select **Download**, similar to the **Download** icon in the Recordings table, the recording is downloaded to the local system of the server.
To play the privileged session recording:
- Click the **Play** icon in the Recordings table. If the recording is in **Ready for Streaming** status, then it starts to play. If it is in any other status besides** Failed**, **Completed**, or **Ready for Streaming**, follow the next steps to view the recording:
- Click **Select File**. A window with the file where the recordings are downloaded appears.
- Select the recording you want to play.
[See image.](#selectfile)
The play window appears on the page.
- To play the video, click the **Play** button in the bottom left corner of the screen. You can also pause the video and click the video player bar to watch at a certain point.
[See image.](#Playview)
You can share the video with admins who have access to the same tenant and have Session Recording enabled by copying the URL at the top of the video page. After the admin enters the URL, they are directly logged into the video page for that specific privileged session recording. If you want to direct them to a specific time in the recording, you can copy and share the permalink. When the user clicks the permalink, the video begins at the specified time rather than at the defaulted beginning time.
Any privileged session recordings that an admin doesn't have access to won't be viewable.
- []**Console**: See requests for a particular privileged console.
- **Policy**: See requests for a particular privileged capabilities policy rule.
- **User**: See requests for a particular user.
[]![Privileged Sessions tools on the Privileged Sessions page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-sessions/Time%20range.png)
[]![Privileged session recordings total widgets displayed on the Privileged Sessions page in the Admin Portal](/downloads/unified-privileged-sessions-recordings.png)
[]![Adding filters to the Privileged Sessions table on the Privileged Sessions page within the Admin Portal](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Privileged%20sessions%20filter.png)
[]![Privileged Sessions table on the Privileged Sessions page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/privileged-remote-access-monitoring/accessing-privileged-sessions/Updated%20table.png)
[]![Select File option for a Session Recording on the Session Recording page in the Admin Portal ](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Select%20File%20on%20the%20recording%20page.png)
[]![Playing a privileged console recording on the Session Recording page in the Admin portal ](/downloads/zpa/dashboard-diagnostics/about-clientless-access-diagnostics/Playing%20a%20recording.png)
[]![Live privileged sessions total widgets displayed on the Privileged Sessions page](/downloads/unified-privileged-sessions-live-total-widgets.png)
[]![Adding filters to the Privileged Sessions table on the Privileged Sessions page within the Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-privileged-sessions/Filters.png)
[]![Participants listed in an expanded live privileged session connection in the Live Privileged Sessions table on the Privileged Sessions page in the Admin Portal](/downloads/zpa/dashboard-diagnostics/accessing-privileged-sessions/Updated%20Live%20table_.png)
- []**Console**: See requests for a particular privileged console.
- **Policy**: See requests for a particular privileged capabilities policy rule.
- **User**: See requests for a particular user.