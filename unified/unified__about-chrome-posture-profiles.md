# About Chrome Posture Profiles
Source: https://help.zscaler.com/unified/about-chrome-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1529462.pdf

A Chrome posture profile is a set of criteria that is evaluated on devices with Chrome Enterprise browser. Policies can be configured based on the device posture profile's evaluation. For example, you can specify an operating system as a posture type where the user has browser access to applications.
Chrome posture profiles provide the following benefits and allow you to:
- Determine access to Chrome Enterprise browser resources and public applications based on the configured device posture profile.
- Ensure a minimum security level is present before allowing access.
To begin [configuring access policies](/unified/configuring-access-policies) in the Admin Portal, you must first [define the posture profile](/unified/configuring-chrome-posture-profiles).
A posture evaluation occurs when a device experiences one of the following network changes:
- Reboots
- Joins or changes a Wi-Fi network
- Comes out of hibernation
- Moves from non-domain joined to domain-joined
- Moves from a Wi-Fi connection to an Ethernet connection.
Zscaler Client Connector evaluates Chrome posture profiles every 15 minutes. New connections are established based on updated security postures. Existing connections are not affected by updates to security postures.
About the Chrome Posture Profile Page
On the Chrome Posture Profile page (Policies > Access Control > Clientless > Chrome Posture Profile), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables#filterData).
- Hide the filters bar by clicking **Hide Filters**. Click **Show Filters** to display filters.
- Refresh the page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables#filterData).
- [Add a Chrome posture profile.](/unified/configuring-chrome-posture-profiles)
- Expand all displayed rows in the table to view more posture profile details.
- [View Chrome posture profile details.](#details)
- View a list of all configured device posture profiles. For each device posture profile, you can see:
- **Posture Name**: The name of the device posture profile.
- **Description**: The description of the device posture profile.
- **Actions**: The actions you can do for the device posture profile.
- [Modify the columns displayed in the table.](/unified/using-tables#hideColumns)
- [Edit a device posture profile.](/unified/managing-chrome-posture-profiles#edit)
- [Delete a device posture profile.](/zpa/maintaining-chrome-posture-profiles#delete)
- Display more rows or a different page of the table.
![Viewing the Chrome Posture Profile Page](/downloads/unified/policies/private-applications/access-control/clientless/browser-access/about-chrome-posture-profiles/unified-chrome-posture-profile.png)
[]
- **Browser Type**: The type of browser.
- **Browser Version**: The version of the browser.
- **Operating System**: The operating system of the device.
- **Key Trust Level**: The key trust level for authentication.
- **Disk Encryption**: The type of disk encryption used.
- **OS Firewall**: The type of firewall associated with the OS.
- **Secure Boot Mode**: The type of secure boot mode that occurs when you safely start up your device.
- **Screen Lock Secured**: The type of screen lock after a certain idle duration period.
- **Safe Browsing Protection Level**: The type of safe browsing protection level that sends warnings to protect your device from security threats.
- **CrowdStrike Agent**: Indicates whether CrowdStrike Agent is enabled or not. CrowdStrike Agent protects Chrome devices by providing visible threat detection.