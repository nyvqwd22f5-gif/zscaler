# About Browser Protection Profiles
Source: https://help.zscaler.com/zpa/about-browser-protection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1485621.pdf

Browser Protection profiles allow you to determine how traffic is inspected and managed for browser sessions. Each Browser Protection profile consists of selected browser and operating system attributes. After a Browser Protection profile has been created, then you need to create a Browser Protection policy to allow the related browsers and operating systems within the Browser Protection profile to be inspected.
Browser Protection profiles enhance your experience by enabling you to:
- Curate the attributes used to create a unique browser fingerprint for each user's browser access session (e.g., OS name, browser engine version, user agent string, geolocation, etc.).
- Exclude the attributes that should not be used to create a fingerprint.
After creating a Browser Protection profile, add it to a Browser Protection policy for the ZPA service to use. To learn more, see [About Browser Protection Policy](/zpa/about-browser-protection-policy).
About the Browser Protection Profile Page
On the Browser Protection Profile page (Configuration & Control > Security > Security Profiles > Browser Protection), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Browser Protection Profiles page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a Browser Protection profile.](/zpa/configuring-browser-protection-profiles)
- View a list of all Browser Protection profiles that were configured for your organization. You can see the name of each Browser Protection profile. When you expand the row, the following information is displayed:
- **Description**: The description of the Browser Protection profile if available.
- **Session Fingerprint Timeout**: The minimum time interval before collecting the next fingerprint for a domain associated with this Browser Protection profile session.
- **Criteria**: The browsers and operating systems selected for each Browser Protection profile.
- **Browser**: The browsers assigned to the Browser Protection profile.
- **Operating System**: The operating systems assigned to the Browser Protection profile.
- Expand all the rows in the table to see more information about each Browser Protection profile.
- [Edit a Browser Protection profile.](/zpa/editing-browser-protection-profiles)
- Delete a Browser Protection profile.
- Copy an existing Browser Protection profile, and use it to create a new Browser Protection profile.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [AppProtection Profiles](/zpa/about-inspection-profiles) page to manage your AppProtection profiles.
- Go to the [AppProtection Controls](/zpa/about-inspection-controls) page to view predefined controls and manage your [custom controls](/zpa/about-custom-controls).
![Browser Protection Profile page within the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/browser-protection-profiles/about-browser-protection-profiles/Browser%20Protection%20Profile%20page%20w%20steps_0.png)