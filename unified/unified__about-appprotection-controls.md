# About AppProtection Controls
Source: https://help.zscaler.com/unified/about-appprotection-controls
PDF: https://help.zscaler.com/pdf/com/en/1492916.pdf

All [AppProtection profiles](/unified/about-appprotection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtections are managed. AppProtection controls are grouped by predefined controls that come from ThreatLabZ, Open Web Application Security Project (OWASP), and WebSocket, or custom WebSocket or HTTP controls. To learn more, see [About ThreatLabZ Controls](/unified/about-threatlabz-controls), [About Custom Controls](/unified/about-custom-controls) and [About WebSocket Controls](/unified/about-websocket-controls).
AppProtection controls enhance your experience by enabling you to:
- Protect internal applications from all types of attacks in the OWASP predefined controls with SQL injection, cross-site scripting (XSS), and more.
- Understand the severity, description, and recommended default action for each type of attack related to OWASP predefined controls.
Each OWASP predefined control is identified with a unique number, defined with how the control operates, and is associated with the level of concern. The predefined controls are organized into various categories:
- Preprocessors
- Environment and Port Scanners
- Protocol Issues
- Request Smuggling or Response Split or Header Injection
- Local File Inclusion
- Remote File Inclusion
- Remote Code Execution
- PHP Injection
- Cross-Site Scripting (XSS)
- SQL Injection
- Session Fixation
- Deserialization
- Issues Anomalies
[]About the OWASP Predefined Controls Page
On the OWASP Predefined Controls page (Policies > Cybersecurity > Inline Security > Protection Controls > OWASP Predefined Controls), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the OWASP Predefined Controls page to reflect the most current information.
- Go to the [ThreatLabZ Controls](/unified/about-threatlabz-controls) page to view the available predefined controls.
- Go to the [Custom Controls](/unified/about-custom-controls) page to manage your custom controls.
- Go to the [WebSocket Controls](/unified/about-websocket-controls) page to manage your WebSocket predefined and custom controls.
- Go to the [Active Directory Controls](/unified/about-active-directory-controls) page to manage your Active Directory controls.
- View more information about the predefined controls.
- Filter the information that appears in the table by version. By default, the version is set to OWASPP_CRS/4.8.0. Some predefined controls are unavailable in older versions. If you are using Anomalies or Web Shells OWASP predefined control groups, you can experience download latency. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/unified/using-tables).
- Expand all the rows in the table to see more information about each predefined control.
- For each predefined control type, expand to view:
- **Control Number**: A number identifying the predefined control. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the predefined control.
- **Control Name**: The name of the predefined control.
- **Severity**: The level of severity for the control number. The severity levels are **Low**, **Medium**, **High**, and **Critical**.
- **Control Action**: What action occurs when the predefined control is in use.
- [Modify the columns displayed in the table.](/unified/using-tables)
![Viewing the OWASP Predefined Controls page ](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles/about-appprotection-controls/unified-owasp-predefined-controls-page_0.png)