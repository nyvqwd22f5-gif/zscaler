# Configuring AppProtection Profiles
Source: https://help.zscaler.com/unified/configuring-appprotection-profiles
PDF: https://help.zscaler.com/pdf/com/en/1493121.pdf

Within the Admin Portal, you can add [AppProtection profiles](/unified/about-appprotection-profiles) to use in [AppProtection policies](/unified/about-appprotection-policy). For a complete list of ranges and limits for AppProtection profiles, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To add an AppProtection profile:
- Go to **Policies **>** Cybersecurity **>** Inline Security **>** Protection Profiles **>** AppProtection**.
- Click **Add**.
The **Add AppProtection Profile** window appears.
- In the **Add AppProtection Profile** window, enter the following information:
- [Step 1: Profile Details](#details)
- [Step 2: Select Controls](#controls)
- [Step 3: Paranoia Level and Execution Order](#paranoia-execution)
- [Step 4: Override Actions](#overrides)
- [Step 5: Review](#review)
- Click **Save**.
- []Enter the relevant details in the **General Information** section:
- **Name**: Enter a name for the AppProtection profile. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description.
- Click **Next**.
[See image.](#img-details)
[]![Enter general information details for an AppProtection Profile in the Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Add%20App%20Prof%20Step%201.png)
- []On the **Select Controls** tab, choose from the [OWASP Predefined Controls](/unified/about-appprotection-controls), [Custom Controls](/unified/about-custom-controls), [ThreatLabZ Controls](/unified/about-threatlabz-controls), [WebSocket Controls](/unified/about-websocket-controls), and [API Controls](/unified/about-api-protection-controls) you have defined. Use the latest version of OWASP predefined controls.
All AppProtection profiles automatically have some [OWASP predefined controls](/unified/about-appprotection-controls) from the Preprocessors category enabled. They have a default action of Block, and you cannot override the action. You can view the Preprocessors in the expanded view of the OWASP predefined controls table.
Rule 920274 blocks traffic containing characters beyond a restricted set. Most browsers and applications may include headers containing characters not included in this character set. This may result in blocking a large number of non-malicious requests.
If you select ThreatLabZ Controls, you can select the checkbox that allows Zscaler to automatically add any new ThreatLabZ predefined controls to the AppProtection profile that is published. If the checkbox isn’t selected, the ThreatLabZ predefined controls need to be manually added to the AppProtection profile.
[See image.](#checkbox)
- (Optional) If you want to create an exception for a predefined control, select the **Add** icon under the exceptions column next to a specific OWASP predefined control to include an exception. The **Add Exceptions** window appears. The control number and control name are displayed. Exceptions allow you to modify predefined controls to bypass requests that trigger false positives. You can choose from the following exceptions:
- In the **Variables** section, select variables from the drop-down menu. Select a variable match to start with, end with, contain, or be equal to the established variable value. Enter the value that you want to set for the variable exception. You can select up to 5 variable-based exceptions.
- In the **Domains** section, select a domain match to start with, end with, contain, or be equal to the established domain value. Enter the value that you want to set for the domain exception. You can select up to 5 domain-based exceptions.
- In the **Paths** section, select a path to start with, end with, contain, or be equal to the established path value. Enter the value that you want to set for the path exception. You can select up to 5 path-based exceptions.
-
(Optional) If you created an exception, click **Save**.
After you save the exception, Exceptions is then listed next to the predefined control instead of the Add icon. You can edit an exception in the [Edit AppProtection Profile](/unified/editing-appprotection-profiles) window. On the [AppProtection Profile page](/unified/about-appprotection-profiles), expand an AppProtection profile in the table to view the exception details as read only.
You can add exceptions to a maximum of 20 OWASP predefined controls.
[See image.](#exception)
- Click **Next**.
[See image.](#img-selectcontrols)
[]![In the Add Inspection Profile window on the Paranoia Level and Execution Order tab, select the checkbox to automatically add new ThreatLabZ predefined controls](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-inspection-profiles/select%20controls%20threatlabz%20option.png)
[]![Select predefined and custom controls for an AppProtection Profile in the Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Add%20App%20Prof%20Step%202.png)
[]![Add exception rules to a predefined control](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Read%20only%20exceptions.png)
[]Custom controls (either HTTP or WebSocket) have a paranoia level of 1.
- Choose a Paranoia Level from 1 to 4 with 1 being the highest level of concern and 4 being the least level of concern.
Higher paranoia levels execute checks using a wide net of matches that increases the potential for false positives. Lower paranoia levels execute checks using a precise set of matches resulting in fewer chances of false positives.
[See image.](#img-paranoialevels)
- Review the **Execution Order**. No further action is required.
If you select custom (HTTP or WebSocket) and predefined controls (ThreatLabZ, OWASP, WebSocket, or API), API controls are executed first, then ThreatLabZ controls, then custom controls, then other predefined controls (OWASP and WebSocket).
- Click **Next**.
[See image.](#tab3full)
[]![Select a paranoia level for predefined controls for an Inspection Profile in the Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/step%203%20paranoia%20level.jpg)
[]![In the Add AppProtection Profile window on the Paranoia Level and Execution Order tab, select the checkbox to automatically add new ThreatLabZ predefined controls](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/Step%203.jpg)
[]You can set up the AppProtection policy to perform no override actions (**None**) or various types of override actions (**Common** and **Specific**). This can be as exact as setting a different action for inspecting transaction traffic on each previously selected ThreatLabZ control, OWASP predefined control, WebSocket control, custom control, and API control.
If using the **Common** or **Specific** override action options, consider initially setting the default action to **Allow** for rules with a higher paranoia level. This provides visibility without denying access.
- Select if you want to allow the AppProtection policy to override controls to perform a different action for inspecting traffic:
- [Common](#common)
- [Specific](#specific)
- [None](#none)
- Click **Next**.
[]Choose one of the standard override options for all of the API controls, ThreatLabZ Controls, OWASP predefined controls, WebSocket controls, and/or all custom controls:
- **Allow**: The user is allowed to proceed with the current URL.
- **Block**: The user receives a 403 response code.
- **Redirect**: The user receives a different URL. Enter an alternative URL that the user will be redirected to.
- []Select the specific API controls, ThreatLabZ controls, OWASP predefined controls, WebSocket controls, and/or custom controls where you want to set override actions.
If you subscribe to automatic updates for ThreatLabZ controls, you can only use the **Common** override option.
- Choose one of the override options for each control selected:
- **Allow**: The user is allowed to proceed with the current URL.
- **Block**: The user receives a 403 response code.
- **Redirect**: The user receives a different URL. Enter an alternative URL that the user is redirected to.
Access to an IP-based application fails when it is linked to an AppProtection profile using the 920350 rule and Block action.
[See image.](#img-specificoverride)
[]![Set override action for a specific control in an AppProtection Profile in the Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/step%204.jpg)
[]No override action occurs for any of the controls. This is the default option.
[]Review your AppProtection profile configurations.
[See image.](#Reviewtab)
[]![Review information when creating an AppProtection Profile in the Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/appprotection-private-application-traffic-profiles-formerly-inspection/configuring-appprotection-profiles/step%205.jpg)