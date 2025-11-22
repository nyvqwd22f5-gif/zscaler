# About Chrome Posture Profiles
Source: https://help.zscaler.com/zpa/about-chrome-posture-profiles
PDF: https://help.zscaler.com/pdf/com/en/1529370.pdf

A Chrome posture profile is a set of criteria that is evaluated on devices with Chrome Enterprise browser. Policies in ZPA can be configured based on the device posture profile's evaluation. For example, you can specify an operating system as a posture type where the user has browser access to applications.
Chrome posture profiles provide the following benefits and allow you to:
- Determine access to Chrome Enterprise browser resources and public applications based on the configured device posture profile.
- Ensure a minimum security level is present before allowing access.
To begin [configuring access policies](/zpa/configuring-access-policies) in the ZPA Admin Portal, you must first [define the posture profile](/zpa/configuring-chrome-posture-profiles).
A posture evaluation occurs when a device experiences one of the following network changes:
- Reboots
- Joins or changes a Wi-Fi network
- Comes out of hibernation
- Moves from non-domain joined to domain-joined
- Moves from a Wi-Fi connection to an Ethernet connection.
Zscaler Client Connector evaluates Chrome posture profiles every 15 minutes. New connections are established based on updated security postures. Existing connections are not affected by updates to security postures.
About the Chrome Posture Profile Page
On the Chrome Posture Profile page (Configuration & Control > Chrome Enterprise Browser), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters bar by clicking **Hide Filters**. Click **Show Filters** to display filters.
- Refresh the page to reflect the most current information.
- [Add a Chrome posture profile.](/zpa/configuring-chrome-posture-profiles)
- View a list of all configured device posture profiles. For each device posture profile, you can see:
- **Posture Name**: The name of the device posture profile.
- **Description**: The description of the device posture profile.
- **Actions**: The actions you can do for the device posture profile.
- Expand all or one posture profile to view more device posture profile details.
- [View Chrome posture profile details.](#details)
- [Modify the columns displayed in the table.](/zpa/using-tables#hideColumns)
- [Edit a device posture profile.](/zpa/maintaining-chrome-posture-profiles#edit)
- [Delete a device posture profile.](/zpa/maintaining-chrome-posture-profiles#delete)
- Display more rows or a different page of the table.
- Go to the [Settings](/zpa/configuring-chrome-enterprise-browser-connector-settings) page to configure the Chrome Enterprise Browser Connector settings.
![Access the Chrome Posture Profile page to begin managing your Chrome posture profiles](/downloads/zpa/browser-access/about-chrome-posture-profiles/ZPA-device-posture-page-4.png)
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