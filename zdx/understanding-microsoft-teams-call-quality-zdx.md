# Understanding Microsoft Teams Call Quality for ZDX
Source: https://help.zscaler.com/zdx/understanding-microsoft-teams-call-quality-zdx
PDF: https://help.zscaler.com/pdf/com/en/1386191.pdf

Microsoft Teams Call Quality allows you to monitor actual one-to-one calls or meetings among two or more participants in a configured Microsoft Teams tenant. The ZDX Score for Call Quality can reflect either a Mean Opinion Score (MOS) average, or metric thresholds for latency, jitter, and packet loss. Call Quality works in parallel with Cloud Path probes, device metrics, and device events to help you identify issues that are unique to a device, application, or network.
When a call has ended, Call Quality data is retrieved using the Microsoft Graph API. Currently, the Microsoft Graph API only provides data for the entire call after the call has completed, and does not provide incremental data while a call is in progress. User and device information garnered from Microsoft for call participants is mapped to ZDX users and devices.
To monitor calls or meetings with Microsoft Teams Call Quality, you first must configure the application and meet the feature prerequisites. To learn more, see [Configuring Microsoft Teams Call Quality for ZDX](/zdx/configuring-microsoft-teams-call-quality-zdx).
To access Microsoft Teams Call Quality monitoring, do one of the following from the ZDX Admin Portal:
- Go to **Applications **and click **Microsoft Teams** **Call Quality** in the Applications Overview page.
- Click the **Microsoft Teams Call Quality** application card.
[See image.](#cqm-card)
Viewing Microsoft Teams Call Quality Data
From the Microsoft Teams Call Quality page, you can set filters for time range, Departments, Zscaler Locations, User Groups, Geolocations, Location Groups, and Last Mile ISPs to help assess Call Quality data. For time range, select a period between 2 Hours and 48 Hours, or a custom range to specify a date and time. The default time range is 2 Hours. To learn more about Department and Location filters, see [Monitoring the Applications Overview](/zdx/monitoring-applications-overview).
The Microsoft Teams Call Quality page reports on the Call Quality for all users participating in Microsoft Teams calls, and includes the following information:
- **ZDX Score Over Time**: The ZDX Score for Call Quality reflects the entire duration of a call for all users. The score is based on the MOS or metric thresholds. To learn more, see [Calculating the ZDX Score](#Calculating).
- **Regions by ZDX Score**: The Microsoft Teams meeting participant locations.
- **Impacted Meetings**: The meetings with low ZDX Scores, with the lowest ZDX Score at the top. Hover over any Meeting ID to view the time and length of that meeting.
- **Probe Status**: The metrics for Cloud Path probes configured as part of the Microsoft Teams Call Quality application. Web probes are not allowed for this application. The following image shows metrics calculated for a Cloud Path host discovered by ZDX Autosense, which can dynamically detect a destination IP address and provide an automated Cloud Path probe when you onboard a Microsoft Teams Call Quality tenant. To learn more, see [Configuring Microsoft Teams Call Quality for ZDX](/zdx/configuring-microsoft-teams-call-quality-zdx).
- **IP Address**: The destination IP address.
- **Domain Name**: The URL for the Cloud Path host.
- **Users**: The number of managed users in the call.
- **Devices**: The number of managed devices in the call.
[See image.](#mtcq-tab)
Viewing Meetings Data
The Meetings page shows a list of meetings (including one-on-one calls) for your organization, sorted by date, based on your time range and filter settings:
- **Zscaler Locations**: Your locations, as defined in ZIA. To learn more, see [About Locations](/zia/about-locations).
- **Users**: The names of your users participating in calls.
The table provides the following information for each meeting:
Meetings are not reported if none of the participants are monitored ZDX users for Call Quality. At least one meeting participant must be a monitored ZDX user. To learn more about configuring ZDX users for meetings, see [Configuring Microsoft Teams Call Quality for ZDX](/zdx/configuring-microsoft-teams-call-quality-zdx).
- **Meeting ID**: You can click any meeting ID to view meeting details. For confidentiality, the internal meeting ID is displayed, and not the actual meeting topic name.
- **ZDX Score**: The following Call Quality metrics are used to determine the score:
- **Latency**:** **The time taken to send a data packet from point A to point B, such as the hop between legs within the Cloud Path.
- **Jitter**: The variance in time delay between data packets over a network.
- **Packet loss**: When data packets that travel across a computer network fail to reach their destination.
The ZDX Score for Call Quality is calculated by one of the following methods, utilizing values for latency, jitter, and packet loss:
- Using the MOS (rated from 1 to 5, worst to best)
- Using metric thresholds
To learn more, see [Calculating the ZDX Score](#Calculating).
- **Mean Opinion Score**: The MOS average might be integrated into the ZDX Score to rate a call's quality.
- **Host**: The name of the meeting host.
- **Start Time and Duration**: The length of the entire call. Partial data for meetings in progress is not captured. Call data from the Microsoft Graph API might take 15 minutes to 1 hour to be available after a meeting has ended.
- **Active participants**: The number of participants as reflected in the session data. Participants who join a call from multiple devices or who leave and rejoin a call are counted per session. This number might differ from Active Participants in the Meeting Details summary, which shows the number of participants derived from the Microsoft Graph API.
- **Action**: Click the **View **icon to view meeting details.
Up to 1,000 meetings are displayed. Use the filters for time range, Zscaler Locations, and Users to help identify a particular meeting. You can also use the Search field by entering any character string or numbers for a Meeting ID, ZDX Score, MOS Score, Host, or Active Participants. Blank fields for the ZDX Score and MOS indicate that no score is available.
![Table data for meetings](/downloads/zdx/analytics/applications/understanding-microsoft-teams-call-quality-zdx/zdx-autosense-teams-meetings-table.png)
Meeting Details
If you click a meeting name or its associated **View **icon within the Meetings tab, the following details are displayed:
- **Meeting Details**: Includes the host of the designated meeting. A MOS Score is displayed only if metrics for latency, jitter, and packet loss are all available for MOS input and MOS output.
- **Sessions and User Devices**: In addition to meeting start and duration times, ZDX Score, and MOS, you can also view the Session ID (this is the internal Microsoft Teams session ID), the device OS, IP Address, Geolocation, and the Audio type. Some IP addresses shown might be truncated by Microsoft for privacy reasons.
You can click usernames within the page to view ZDX details for user device, application, and metrics. However, details are not available for users and devices identified as follows:
- External users who do not belong to the configured Microsoft Teams Call Quality tenant. These users might appear as an "External User" or have no username displayed. Microsoft hides the names of external users for privacy reasons.
- Guest users who are either not part of a Microsoft Teams tenant account or they haven't logged in to their Microsoft Teams account, but participate in the Teams meeting using their web browser. These users might appear as a "Guest User" or have no username displayed.
- Some ZIA users might not have ZDX enabled, and therefore, their user details are unavailable.
- Some user devices might not map to a corresponding registered ZDX device.
- Some ZDX users are not being monitored for Call Quality.
- Insufficient information is available to map a user to a ZDX device.
[See image.](#meeting-details)
Meeting Monitoring Metrics
Metrics for your meetings are included within the user details page. The values for Audio, Video, and Sharing Quality are displayed as follows:
- **Latency**: Range starts at 0ms
- **Jitter**: Range starts at 0ms
- **Average Loss**: 0 to 100%
- **Max Loss**: 0 to 100%
To learn how the latency, jitter, and packet loss values are used to determine the ZDX Score, see [Calculating the ZDX Score](#Calculating).
[See image.](#mmm)
[]Calculating the ZDX Score
The ZDX Score for Call Quality is calculated by one of the following methods:
- [Mean Opinion Score](#calculating-mos)
- [Metric Thresholds](#calculating-thresholds)
[]If metrics for latency, jitter, and packet loss are all available for calculation, the MOS is used to determine the ZDX Score. MOS uses a transmission rating factor (R-Factor) that generates range levels it derives from those particular metrics. The range levels help determine the ZDX Score for Call Quality as Poor, Okay, or Good.
The range levels for MOS are as follows:
- If the MOS is 0 to 3.6, the ZDX Score = Poor.
- If the MOS is greater than 3.6 but less than 4.34, the ZDX Score = Okay.
- If the MOS is 4.34 or greater, the ZDX Score = Good.
[]If only one or two of the metrics is available for calculation, metric thresholds are used to determine the ZDX Score.
The ZDX Score is rated Poor when metrics exceed their respective thresholds:
- If the latency range is above 500ms
- If the jitter range is above 30ms
- If packet loss is above 0.1%
Ranges above and below the threshold are assigned a corresponding metric-based score to help define whether the ZDX Score is rated Poor or Good. The ZDX Score is calculated by using the lowest metric-based score of two metrics, or the lowest metric-based score of one metric. For example, if latency is 550ms with a corresponding metric-based score of 30, and jitter is 26ms with a corresponding metric-based score of 70, the ZDX Score is based on the lower metric-based score, which is 30.
If all three metrics for latency, jitter, and packet loss are unavailable, the ZDX Score for Call Quality cannot be calculated and data is not displayed.
[]![Application card for Microsoft Teams Call Quality ](/downloads/zdx/analytics/applications/understanding-microsoft-teams-call-quality-zdx/zdx-teams-cqm-app-card.png)
[]![Microsoft Teams Call Quality page](/downloads/zdx/analytics/applications/understanding-microsoft-teams-call-quality-zdx/zdx-autosense-teams-meetings-mtcq.png)
[]![Page that shows meeting details](/downloads/zdx/analytics/applications/understanding-microsoft-teams-call-quality-zdx/zdx-teams-cqm-meetings-details-page2.png)
[]![Example of Meeting Monitoring Metrics graph](/downloads/zdx/analytics/about-microsoft-teams-call-quality-zdx/zdx-msteams-cqm-mmm4.png)