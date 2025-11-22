# Viewing the Meetings Dashboard
Source: https://help.zscaler.com/unified/viewing-meetings-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1498756.pdf

The Meetings dashboard provides an overview of the performance of meetings and videoconferencing applications in your organization.
Filtering
-
**Time Range**: Use the Time Range filter in the upper right to choose a specific time range between 2 hours and 48 hours in which to view data. Select **Custom** to select a specific time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
The selected period applies to all data within the dashboard. The default time range is **2 Hours**.
-
**Filter data**: Click the filters in the top left to limit the data shown. Each filter allows you to include or exclude individual options.
- **Applications**: The meeting applications in your organization.
- **Departments**: Your departments. To learn more, see [About Departments](/unified/about-departments).
- **Zscaler Locations**: Your locations. To learn more, see [About Locations](/unified/about-locations).
- **User Groups**: The names of user groups in your organization.
- **Geolocations**: The geographic areas where your users are located.
- **Location Groups**: The names of groups based on location in your organization.
- **Last Mile ISPs**: The Internet Service Providers (ISPs) to which your users are connecting.
- **Operating System**: The operating systems used in your organization,
Click **Apply **to update the dashboard with your selections. To remove all filter selections, click **Reset**.
Meetings
This table shows all the meetings that occurred in your organization for the selected time range and filters:
- **Meeting ID**: The unique identifier of the meeting.
- **Application Name**: The name of the meeting application used for this meeting.
- **MOS Score**: The Mean Opinion Score of the meeting, on a scale of 1 (worst) to 5 (best). MOS is calculated based on metrics such as latency, jitter, and packet loss.
- **Host**: The user who hosted the meeting.
- **Start Time**: The beginning time of the meeting.
- **Active Participants**: The number of participants as reflected in the session data. Participants who join a call from multiple devices or who leave and rejoin a call are counted per session.
[See image.](#meetings-list-image)
Click any meeting row to see additional details about that meeting:
- **Meeting Details**: Includes the unique identifier of the meeting, the host, number of participants, start and end times, and the ZDX Score, which is derived from the MOS Score.
- If the MOS is 0 to 3.6 the ZDX Score is **Poor**.
- If the MOS is greater than 3.6 but less than 4.34, the ZDX Score is **Okay**.
- If the MOS is 4.34 or greater, the ZDX Score is **Good**.
- **Participants**: The list of users, the Session ID (this is the internal meeting session ID), the user's start and end times, their device OS, IP Address, Geolocation, and individual MOS and ZDX scores. Some information may not be available for all participants (such as if the user does not have Digital Experience enabled).
[See image.](#meetings-details-image)
[]![Meetings list on the Meetingsdashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-meetings-dashboard/meetings-list.png)
[]![Meetings Detail on the Meetings dashboard](/downloads/unified/analytics/unified-dashboards/digital-experience/viewing-meetings-dashboard/meetings-details.png)