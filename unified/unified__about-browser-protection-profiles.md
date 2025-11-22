# About Browser Protection Profiles
Source: https://help.zscaler.com/unified/about-browser-protection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493161.pdf

Browser Protection profiles allow you to determine how traffic is inspected and managed for browser sessions. Each Browser Protection profile consists of selected browser and operating system attributes. After a Browser Protection profile has been created, then you need to create a Browser Protection policy to allow the related browsers and operating systems within the Browser Protection profile to be inspected.
Browser Protection profiles enhance your experience by enabling you to:
- Curate the attributes used to create a unique browser fingerprint for each user's browser access session (e.g., OS name, browser engine version, user agent string, geolocation, etc.).
- Exclude the attributes that should not be used to create a fingerprint.
After creating a Browser Protection profile, add it to a Browser Protection policy for Private Applications to use. To learn more, see [About Browser Protection Policy](/unified/about-browser-protection-policy).
About the Browser Protection Profile Page
On the Browser Protection Profile page (Policies > Cybersecurity > Inline Security > Protection Profiles), you can do the following:
- Go to the[ AppProtection Profiles](/unified/about-appprotection-profiles) page to manage your AppProtection profiles.
- Expand all the rows in the table to see more information about each Browser Protection profile.
- [Add a Browser Protection profile.](/unified/configuring-browser-protection-profiles)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all Browser Protection profiles that were configured for your organization. You can see the name of each Browser Protection profile. When you expand the row, the following information is displayed:
- **Description**: The description of the Browser Protection profile if available.
- **Session Fingerprint Timeout**: The minimum time interval before collecting the next fingerprint for a domain associated with this Browser Protection profile session.
- **Criteria**: The browsers and operating systems selected for each Browser Protection profile.
- **Browser**: The browsers assigned to the Browser Protection profile.
- **Operating System**: The operating systems assigned to the Browser Protection profile.
- Copy an existing Browser Protection profile, and use it to create a new Browser Protection profile.
- [Edit a Browser Protection profile.](/unified/editing-browser-protection-profiles)
- Delete a Browser Protection profile.
![View and manage the protection profiles on the Browser Protection page](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles/browser-protection-profiles/about-browser-protection-profiles/unified-browser-protection-profile-page.png)