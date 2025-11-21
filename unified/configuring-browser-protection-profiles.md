# Configuring Browser Protection Profiles
Source: https://help.zscaler.com/zpa/configuring-browser-protection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1485626.pdf

Within the ZPA Admin Portal, you can add [Browser Protection profiles](/zpa/about-browser-session-profiles) to use in Browser Protection Protection policies. For a complete list of ranges and limits for Browser Protection profiles, see [Ranges & Limitations](/zpa/ranges-limitations).
To add a Browser Protection profile:
- Go to **Configuration & Control** > **Security** > **Security Profiles** > **Browser Protection**.
- Click **Add Browser Protection Profile**.
The **Add Browser Protection Profile** window appears.
- In the **Add Browser Protection Profile** window, enter the following information:
- [Step 1: Details](#Geninfo)
- [Step 2: Criteria](#Criteria)
- [Step 3: Review](#Review)
- Click **Save**.
- []Enter the relevant details in the **General Information** section:
- **Name**: Enter a name for the Browser Protection profile. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- In the **Timeouts** section, enable **Continuous Fingerprint** to continuously monitor the users' browser access fingerprints assigned to this Browser Protection profile during a session. The default time limit for the timeout is 5 minutes and the maximum time limit is 24 hours. The time interval set is the minimum amount of time before the next fingerprint is captured again for a domain. **Continuous Fingerprint** is disabled by default.
- Click **Next**.
[See image.](#Geninfoimage)
- []Select the criteria that you want to assign to the Browser Protection profile in the **Criteria** section:
- **Browser**: Select the browser attributes you want to include in the Browser Protection profile.
- **Operating System**: Select the operating system attributes you want to include in the Browser Protection profile.
- **Collect Location**: Select the checkbox to capture the monitored user's geolocation.
If you select the checkbox, a notification appears.
![The Collect Location notification window ](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Notification%20Geo%20location.png)
- Click **Next**.
[See image.](#Criteriaimage)
[]Review your Browser Protection profile configurations.
[See image.](#Reviewimage)
[]![Enter general information details for a Browser Protection Profile in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/browser-protection-profiles/configuring-browser-protection-profiles/Add%20Browser%20Protection%20Profile%20window%20Step%201.png)
[]![Select the browsers and operating systems for the Browser Protection profile in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/browser-protection-profiles/configuring-browser-protection-profiles/Add%20Browser%20Protection%20Profile%20Step%202.png)
[]![Review information when creating a Browser Protection Profile in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Step%20three%20Review.png)