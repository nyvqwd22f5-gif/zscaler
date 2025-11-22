# Monitoring the Users Overview
Source: https://help.zscaler.com/unified/monitoring-users-overview
PDF: https://help.zscaler.com/pdf/com/en/1494506.pdf

The Users Overview page (Analytics > Digital Experience Monitoring > Users) provides information about the digital experience of users in your organization during the selected time frame. By default, Total Active Users and Total Active Devices are displayed in the overview.
[See image.](#image-fullpg)
The Users Overview allows you to:
- View user information: Select one or more applications in the Applications filter drop-down menu and click **Apply **to view user information in the ZDX Score User Distribution and the Users list. By default, no information is displayed in the ZDX Score User Distribution and the Users list until an application is selected. Applications chosen in the Users Overview are carried over to the user details page.
- View performance data over time: Use the Time Range filter to choose a specific time range to view data. The selected period applies to all data within the overview. The default time range is **2 Hours**.
- **Current**: View the most current ZDX Score captured within the previous 30 minutes.
- **2 Hours **to **48 Hours**: Specify a time interval between 2 hours and 48 hours as shown in the drop-down menu.
- **Custom**: Specify a custom time range. The start date must be within the last 14 days, and the minimum time range is 15 minutes. You can set any time range greater than 15 minutes in 5-minute increments.
-
Filter data: Click the filters to select options for Applications, Departments, Zscaler Locations, Geolocations, User Groups, Users, Location Groups, Last Mile ISPs, and Operating System. Each filter allows you to include or exclude individual options. Click **Select All Displayed** to select all options at once. These filters apply to only this page and do not apply to the Probes configuration page.
Any disabled applications in the Applications filter are shown in gray, and deleted applications are indicated with a strikethrough on the application name.
[See image.](#AllDisplayed)
- Understand user digital experience: Click the table cell for User or Devices in the User list table to view a page with details about the user's digital experience.
To view user information using filters:
- Determine which options to include or exclude from each of the filter drop-down menus:
- **Applications**: The applications used by users.
- **Departments**: Your departments, as defined in Internet & SaaS. To learn more, see [About Departments](/unified/about-departments).
- **Zscaler Locations**: Your locations, as defined in Internet & SaaS. To learn more, see [About Locations](/unified/about-locations).
- **Geolocations**: The geographic areas where your users are located.
- **User Groups**: The names of user groups in your organization.
- **Users**: The names of your users.
- **Location Groups**: The names of groups based on location in your organization.
- **Last Mile ISPs**: The Internet Service Providers (ISPs) to which your users are connecting.
- **Operating System**: The operating system versions installed on user devices in your organization.
- Click **Apply **after completing your selections.
- You can select other options in the Time Range filter to view data over a time period.
You can adjust the filters as needed or remove all of your filter selections by clicking **Reset**.
Reviewing Digital Experience Overview
To get a brief overview of your organization's digital experience, use the following:
- [Total Active Users and Total Active Devices](#totalactiveusers_devices)
- [ZDX Score User Distribution](#zdxscore)
[]Viewing User Information
The User list displays up to 100 users in the **Poor**, **Okay**, or **Good **ZDX Score category for the selected time period. By default, users with Poor, Okay, or Good scores are displayed under their respective tabs within the table and the page displays the Poor tab on loading. However, if there are no users with a specific score (e.g., Poor), then the table displays the next tab that applies to any users in your organization.
The **Download** icon (![Using the download CSV icon for current table view](/downloads/zdx/analytics/about-users-dashboard/zdx-download-csv-icon_0.png)
) allows you to download the current table view of listed users in CSV format for each ZDX Score category. If no users are listed for any ZDX Score category, the icon does not appear.
To further sort user information, use the filters on the page.
The table displays the following information about users and their digital experience:
- [User](#usercolumn)
- [ZDX Score](#zdxscorecolumn)
- [Zscaler Locations](#locationcolumn)
- [Geolocations](#geocolumn)
- [Devices](#devicescolumn)
- [Device Count](#devicecount)
[See image.](#image-userlist)
In the Users list, you can:
- Compare user details: Click the **Open in a New Tab** icon ( ![Open in a New Tab Icon ](/downloads/zdx/analytics/about-users-dashboard/OpeninaNewTabIcon.png)
) to open the user page in a new tab. You can compare multiple users using this option.
- View user details: Click the **View **icon ( ![Eye Icon to View Details ](/downloads/zdx/analytics/about-users-dashboard/ZDX_EyeIcon.png)
) to go to the user page and view user details.
- Start a Diagnostics session: Click the **Diagnostics** icon ( ![Deep Tracing Icon ](/downloads/zdx/analytics/about-users-dashboard/DTIcon.png)
) to start a session for a user.
To learn more about user details, see [Evaluating User Details](/unified/evaluating-user-details).
[]View the number of active users for a selected time period:
- A percentage indicates how the number of users has increased or decreased for the selected time period.
- A trending line visually indicates the rise or fall of the number of users over time.
Hover over any point on the line to see the number of users for a particular day and time.
![Total Active Users on the User Dashboard](/downloads/zdx/analytics/about-users-dashboard/zdx-userdashboard-totalactiveusers.png)
View the number of active devices for a selected time period:
- A percentage indicates how the number of devices has increased or decreased for the selected time period.
- A trending line visually indicates the rise or fall of the number of devices over time.
Hover over any point on the line to see the number of devices for a particular day and time.
![Total Active Devices on the User dashboard](/downloads/zdx/analytics/about-users-dashboard/zdx-userdashboard-totalactivedevices.png)
In some cases, you might see a pronounced dip at the end of the trending line. A tooltip for the dip indicates when complete data is not yet available from all connected devices, but should be available within approximately 10 minutes.
![Example of data ingestion delay](/downloads/zdx/analytics/about-users-dashboard/zdx-ingestion-delay1.png)
[]View how many users have a **Poor**, **Okay**, or **Good** ZDX Score in the selected time period. To learn more, see [About the ZDX Score](/unified/about-zdx-score).
![ZDX Score User Distribution ](/downloads/zdx/analytics/about-users-dashboard/ZDX_ZDXScore_UserDistribution_0.png)
[]The **User** column provides a list of users by their name. These names come from your identity providers configured in Internet & SaaS. To learn more, see [About Identity Providers](/unified/about-identity-providers).
You can click a name to see more information about each user. To learn more, see [Evaluating User Details](/unified/evaluating-user-details).
[]The **ZDX Score **column shows the user's ZDX Score from 1–100, with 1 being the lowest and 100 being the highest. It is an average score for the selected time period. To learn more, see [About the ZDX Score](/unified/about-zdx-score).
[]The **Zscaler Locations** column provides a list of the locations where the user accessed their device. These locations are defined in Internet & SaaS. To learn more, see [About Locations](/unified/about-locations).
Click a location name to view the Applications Overview with the data filtered by that defined location. To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
[]The **Geolocations** column lists all the areas where users accessed their devices for the selected time period.
Digital Experience Monitoring uses a device's location service to determine a user's location. It takes the longitude and latitude coordinates from the location service and compares them to Zscaler's geographic IP database. That information is then listed, by corresponding major cities and towns, in the Admin Portal.
If a user's latitude and longitude are closer to the center of another city, instead of their own city, the user's location might be misidentified as connecting from the neighboring city. If the location service is not enabled on the device, then Digital Experience Monitoring uses the device's IP address to determine the location.
Digital Experience Monitoring currently supports Windows, macOS, Android, and Chrome devices only (e.g., desktop, laptop).
Click a city to view the Applications Overview with the data filtered by those cities. To learn more, see [Monitoring the Applications Overview](/unified/monitoring-applications-overview).
[]The **Devices** column lists all the user's devices they used for the selected time period.
Click the device names to view more detailed information about the user's devices and applications accessed from the devices. To learn more, see [Evaluating User Details](/unified/evaluating-user-details).
[]The **Device Count** column lists the total number of devices associated with the user.
Click the user name or device names to view detailed information about the user's devices. To learn more, see [Evaluating User Details](/unified/evaluating-user-details).
[]![ZDX Users Dashboard](/downloads/zdx/analytics/users/monitoring-users-dashboard/zdx-user-overview-default5.png)
[]![Icons for user details](/downloads/zdx/analytics/users/monitoring-users-dashboard/zdx-device-count-icons3.png)
[]![Filter to select application](/downloads/zdx/analytics/users/monitoring-users-dashboard/zdx-user-overview-select-applications3.png)