# About AppProtection Profiles
Source: https://help.zscaler.com/unified/about-appprotection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493086.pdf

AppProtection profiles allow you to determine how traffic is inspected and managed. Each AppProtection profile uses a paranoia level if using [ThreatLabZ predefined controls](/unified/about-threatlabz-controls), [Open Web Application Security Project (OWASP) predefined controls](/unified/about-appprotection-controls), or [WebSocket predefined controls](/unified/about-websocket-controls). Predefined controls are a selection of the controls to establish the requirements for AppProtection, and what action is taken for those controls. You can use your own [WebSocket custom controls](/unified/about-websocket-controls) or [HTTP custom controls](/unified/about-custom-controls). Or you can use the [ThreatLabZ predefined controls](/unified/about-threatlabz-controls), [OWASP predefined controls](/unified/about-appprotection-controls), or [WebSocket predefined controls](/unified/about-websocket-controls). There is also flexibility to have the same action for all the controls, or a different action for each control in the AppProtection profile.
AppProtection profiles enhance your experience by enabling you to:
- Create a comprehensive security profile by selecting controls from multiple categories (OWASP predefined controls, HTTP custom controls, WebSocket controls, and ThreatLabZ controls).
- Assign a specific action to take in the event of malicious traffic (Allow, Block, or Redirect).
All AppProtection profiles automatically have some [predefined ones](/unified/about-appprotection-controls#predefinedcontrols) enabled from the Preprocessors category. These controls are 200002, 200003, and 200004. They have a default action of Block, and this action cannot be removed or changed. If you are using ThreatLabZ predefined controls and WebSocket predefined controls, the default action is Allow for the Preprocessors category.
[]Using the Default AppProtection Profile Template
A default AppProtection profile is included with the setup of your ZPA account. It is located in the AppProtection profile table and is named OWASP Top-10 for Visibility. Use the default profile as a template for custom AppProtection profiles. The default profile can't be edited or deleted. Its Paranoia Level is set to 1. You can also use this default profile in an AppProtection policy.
[See image.](#Default)
Some controls are excluded from the default AppProtection profile for higher efficacy. All other controls included in this profile must have their action set to Allow.
After creating an AppProtection profile, add it to an AppProtection policy for the ZPA service to use. To learn more, see [About AppProtection Policy](/unified/about-appprotection-policy).
About the AppProtection Profile Page
On the AppProtection Profile page (Policies > Cybersecurity > Inline Security > Protection Profiles > AppProtection), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the AppProtection Profiles page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables).
- [Add an AppProtection profile](/unified/configuring-appprotection-profiles).
- View a list of all AppProtection profiles that were configured for your organization. You can see the name of each AppProtection profile. When you expand the row, the following information is displayed:
- **Description**: The description of the AppProtection profile if available.
- **Paranoia Level**: The associated level, which corresponds to the levels available in the AppProtection controls.
-
**Used in AppProtection Controls**: The predefined and custom controls in use by the AppProtection profile. When you select the level listed, you can view the following information for each predefined control:
- **Control Number**: A number identifying the predefined control.
- **Control Name**: The name of the predefined control.
- **Control Action**: What action occurs when the predefined control is in use.
- **Control Exception**: **Exceptions **is listed if an exception has been added to a predefined control. You can click **Exceptions **to view the details for that specific exception in the **Edit Exceptions** window in a read-only format.
[See image.](#exception)
- Expand all the rows in the table to see more information about each AppProtection profile.
- Copy an existing AppProtection profile, and use it to create a new AppProtection profile.
- [Edit an AppProtection profile](/unified/editing-appprotection-profiles).
-
Delete an AppProtection profile.
You can't edit or delete the default AppProtection profile. To learn more, see [Default AppProtection Profile](#deftemplate).
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
- Go to the [Browser Protection profiles](/unified/about-browser-protection-profiles) page to manage your Browser Protection profiles.
![Viewing or managing AppProtection Profiles within the AppProtection page](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles/appprotection-private-application-traffic-profiles/about-appprotection-profiles/experience-center-AppProtection-page.png)
[]![Viewing the default AppProtection Profile](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles/appprotection-private-application-traffic-profiles/about-appprotection-profiles/experience-center-AppProtection-default-profile.png)
[]![Used in AppProtection Controls window on the AppProtection Profile page](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/about-appprotection-profiles/Used%20in%20AppProtection%20Controls%20window.png)