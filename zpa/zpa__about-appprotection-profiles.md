# About AppProtection Profiles
Source: https://help.zscaler.com/zpa/about-appprotection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1485006.pdf

AppProtection profiles allow you to determine how traffic is inspected and managed. Each AppProtection profile uses a paranoia level if using [API controls](/zpa/about-api-protection-controls), [ThreatLabZ predefined controls](/zpa/about-threatlabz-controls), [Open Web Application Security Project (OWASP) predefined controls](/zpa/about-inspection-controls), or [WebSocket predefined controls](/zpa/about-websocket-controls). Predefined controls are a selection of the controls to establish the requirements for AppProtection, and what action is taken for those controls. You can use your own [WebSocket custom controls](/zpa/about-websocket-controls) or [HTTP custom controls](/zpa/about-custom-controls). Or you can use the [ThreatLabZ predefined controls](/zpa/about-threatlabz-controls), [OWASP predefined controls](/zpa/about-inspection-controls), [API controls](/zpa/about-api-protection-controls) or [WebSocket predefined controls](/zpa/about-websocket-controls). There is also flexibility to have the same action for all the controls, or a different action for each control in the AppProtection profile.
AppProtection profiles enhance your experience by enabling you to:
- Create a comprehensive security profile by selecting controls from multiple categories (OWASP predefined controls, HTTP custom controls, WebSocket controls, API controls, and ThreatLabZ controls).
- Assign a specific action to take in the event of malicious traffic (Allow, Block, or Redirect).
[]Using the Default AppProtection Profile Template
A default AppProtection profile is included with the setup of your ZPA account. It is located in the AppProtection profile table and is named OWASP Top-10 for Visibility. Use the default profile as a template for custom AppProtection profiles. The default profile can't be edited or deleted. Its Paranoia Level is set to 1. You can also use this default profile in an AppProtection policy.
[See image.](#Default)
Some controls are excluded from the default AppProtection profile for higher efficacy. All other controls included in this profile must have their action set to Allow.
After creating an AppProtection profile, add it to an AppProtection policy for the ZPA service to use. To learn more, see [About AppProtection Policy](/zpa/about-inspection-policy).
About the AppProtection Profile Page
On the AppProtection Profile page (Configuration & Control > Security > Security Profiles > AppProtection), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the AppProtection Profiles page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add an AppProtection profile](/zpa/configuring-inspection-profiles).
- View a list of all AppProtection profiles that were configured for your organization. You can see the name of each AppProtection profile. When you expand the row, the following information is displayed:
- **Description**: The description of the AppProtection profile, if available.
- **Paranoia Level**: The associated level which corresponds to the levels available in the AppProtection controls.
- **Used in AppProtection Controls**: The predefined and custom controls in use by the AppProtection profile. When you select the level listed, you can view the following information for each predefined control:
- **Control Number**: A number identifying the predefined control.
- **Control Name**: The name of the predefined control.
- **Control Action**: What action occurs when the predefined control is in use.
- **Control Exception**: **Exceptions** is listed if an exception has been added to a predefined control. You can click **Exceptions** to view the details for that specific exception in the **Edit Exceptions** window in a read-only format.
[See image.](#exception)
- Expand all the rows in the table to see more information about each AppProtection profile.
- [Edit an AppProtection profile](/zpa/edit-inspection-profiles).
- Delete an AppProtection profile.
You can't edit or delete the default AppProtection profile. To learn more, see [Default AppProtection Profile](#deftemplate).
- Copy an existing AppProtection profile, and use it to create a new AppProtection profile.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Browser Protection profiles](/zpa/using-zscaler-help-browser) page to manage your Browser Protection profiles.
- Go to the [AppProtection Controls](/zpa/about-inspection-controls) page to view predefined controls and manage your [custom controls](/zpa/about-custom-controls).
![Default AppProtection Profile template included on the AppProtection Profile page](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/about-appprotection-profiles/AppProtection%20Profile%20page%20w%20steps_0.png)
[]![Default AppProtection Profile template included on the AppProtection Profile page](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/about-inspection-profiles/Default%20AppProtection%20Profile.png)
[]![Used in AppProtection Controls window on the AppProtection Profile page](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/about-appprotection-profiles/Used%20in%20AppProtection%20Controls%20window_0.png)