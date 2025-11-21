# Understanding Zoom Call Quality for ZDX
Source: https://help.zscaler.com/zdx/understanding-zoom-call-quality-zdx
PDF: https://help.zscaler.com/pdf/com/en/1386321.pdf

Zoom Call Quality allows you to monitor actual one-to-one calls or meetings among two or more participants in a configured Zoom tenant. The ZDX Score for Call Quality can reflect either a Mean Opinion Score (MOS) average, or metric thresholds for latency, jitter, and packet loss. Call Quality works in parallel with Cloud Path probes, device metrics, and device events to help you identify issues that are unique to a device, application, or network.
Call Quality data is retrieved using the Zoom API, and data is captured in real time as a meeting is in progress. User and device information garnered from the API for call participants is mapped to ZDX users and devices. While incremental data is available for calls in progress, complete call data is available approximately 10 minutes after a call has ended.
To monitor calls or meetings with Zoom Call Quality, you'll first need to configure the application and onboard a Zoom API tenant or Zoom QSS tenant, as well as meet the feature prerequisites. To learn more, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
To access Zoom Call Quality monitoring, do one of the following from the ZDX Admin Portal:
- Go to **Applications **and click **Zoom Call Quality** in the Applications Overview page.
- Click the **Zoom Call Quality** application tile.
[See image.](#cqm-card)
Viewing Zoom Call Quality Data
From the Zoom Call Quality page, you can set filters for time range, Departments, Zscaler Locations, User Groups, Geolocations, Location Groups, and Last Mile ISPs to help assess Call Quality data. For time range, select a period between **2 Hours** and **48 Hours**, or a custom range to specify a date and time. The default time range is **2 Hours**. To learn more about application filters, see [Monitoring the Applications Overview](/zdx/monitoring-applications-overview).
The Zoom Call Quality page reports on Call Quality for all users participating in Zoom calls, and includes the following information:
- **ZDX Score Over Time**: The ZDX Score for Call Quality reflects the entire duration of a call for all users. The score is based on the MOS or metric thresholds. To learn more, see [Calculating the ZDX Score](#Calculating).
- **Regions by ZDX Score**: The Zoom meeting participant locations.
- **Impacted Meetings**: The meetings with low ZDX Scores, with the lowest ZDX Score at the top. Hover over any Meeting ID to view the time and length of that meeting.
- **Probe Status**: The metrics for Cloud Path probes configured for the Zoom Call Quality application. Only Cloud Path probes can be configured, as Web probes are not allowed for this application. The following image shows metrics calculated for a Cloud Path host discovered by ZDX Autosense, which can dynamically detect a destination IP address and provide an automated Cloud Path probe when you onboard a Zoom Call Quality tenant. To learn more, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
- **IP Address**: The destination IP address.
- **Domain Name**: The URL for the Cloud Path host.
- **Users**: The number of managed users in the call.
- **Devices**: The number of managed devices in the call.
[See image.](#zcq-tab)
Viewing Meetings Data
The Meetings page shows a list of meetings (including one-on-one calls) for your organization, sorted by date, based on your time range and filter settings:
Only meetings with two or more participants that last more than one minute are collected and displayed.
- **Zscaler Locations**: Your locations, as defined in ZIA. To learn more, see [About Locations](/zia/about-locations).
- **Users**: The names of your users participating in calls.
The table provides the following information for each meeting:
Meetings are not reported if none of the participants are monitored ZDX users for Call Quality. At least one meeting participant must be a monitored ZDX user. To learn more about configuring ZDX users for meetings, see [Configuring Zoom Call Quality for ZDX](/zdx/configuring-zoom-call-quality-zdx).
- **Meeting UUID**: The meeting's Universally Unique Identifier that can be used for troubleshooting purposes.
- **Meeting ID**: The meeting identifier visible to the end user. For confidentiality, this identifier is displayed in place of any meeting topic name.
- **ZDX Score:** The following Call Quality metrics are used to determine the score:
- **Latency**:** **The time taken to send a data packet from point A to point B, such as the hop between legs within the Cloud Path.
- **Jitter**: The variance in time delay between data packets over a network.
- **Packet loss**: When data packets that travel across a computer network fail to reach their destination.
The ZDX Score for Call Quality is calculated by one of the following methods, utilizing values for latency, jitter, and packet loss:
- Using the MOS (rated from 1 to 5, worst to best)
- Using metric thresholds
To learn more, see [Calculating the ZDX Score](#Calculating).
- **Mean Opinion Score**: The MOS average might be integrated into the ZDX Score to rate a call's quality.
- **Host**: The name of the meeting host.
- **Start Time and Duration**: The beginning and duration of the call, indicated by either the time of the entire call or a call in progress. Ongoing calls are shown as In Progress to indicate the call has not ended. Call data for meetings in progress is captured every 5 minutes.
- **Active Participants**: The number of participants as reflected in the session data. Participants who join a call from multiple devices or who leave and rejoin a call are counted per session. This number might differ from Active Participants in the Meeting Details summary, which shows the number of participants derived from the Zoom API.
- **Action**: Click the **View **icon to view meeting details.
Up to 1,000 meetings are displayed. Use the filters for time range, Zscaler Locations, and Users to help identify a particular meeting. You can also use the Search field by entering any character string or numbers for a Meeting ID, ZDX Score, MOS Score, Host, or Active Participants. Blank fields for the ZDX Score and MOS indicate that no score is available.
![Meetings data shown on Zoom Call Quality Meetings page](/downloads/zdx/analytics/applications/understanding-zoom-call-quality-zdx/zdx-zoom-uuid-meetings-page.png)
Due to the Zoom API rate limit of 60,000 per day, Zoom Call Quality might be impacted by other applications using the API, which could cause some meeting information to be unavailable.
Meeting Details
If you click a Meeting UUID, Meeting ID, or the associated **View **icon within the Meetings page, the following details are displayed:
- **Meeting Details**: Includes the host of the designated meeting. A MOS Score is displayed only if metrics for latency, jitter, and packet loss are all available for MOS input and MOS output.
- **Sessions and User Devices**: In addition to meeting start and duration times, ZDX Score, and MOS, you can also view the Session ID (this is the internal Zoom session ID), the device OS, IP Address, Geolocation, and the Audio type.
You can click usernames within the page to view ZDX details for user device, application, and metrics. However, details are not available for users and devices identified as follows:
- External users do not belong to the configured Zoom Call Quality tenant. These users might appear as an "External User" or have no username displayed. Zoom hides the names of external users for privacy reasons.
- Guest users are either not part of a Zoom tenant account or they haven't logged in to their account, but they participate in the Zoom meeting using their web browser. These users might appear as a "Guest User" or have no username displayed.
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
- If jitter range is above 30ms
- If packet loss is above 0.1%
Ranges above and below the threshold are assigned a corresponding metric-based score to help define whether the ZDX Score is rated Poor or Good. The ZDX Score is calculated by using the lowest metric-based score of two metrics, or the lowest metric-based score of one metric. For example, if latency is 550ms with a corresponding metric-based score of 30, and jitter is 26ms with a corresponding metric-based score of 70, the ZDX Score is based on the lower metric-based score, which is 30.
If all three metrics for latency, jitter, and packet loss are unavailable, the ZDX Score for Call Quality cannot be calculated and data is not displayed.
[]![Zoom Call Quality application card](/downloads/zdx/analytics/applications/understanding-zoom-call-quality-zdx/zdx-zoom-cqm-app-card.png)
[]![Viewing the Zoom Call Quality page](/downloads/zdx/analytics/applications/understanding-zoom-call-quality-zdx/zdx-autosense-zoom-cqm-reporting3.png)
[]![Example of Meeting Details page for Zoom Call Quality](/downloads/zdx/analytics/applications/understanding-zoom-call-quality-zdx/zdx-zoom-uuid-meetings-details.png)
[]![Meeting Monitoring Metrics graph](/downloads/zdx/analytics/about-zoom-call-quality-zdx/zdx-zoom-mmm2.png)