# About AppProtection Controls
Source: https://help.zscaler.com/zpa/about-appprotection-controls
PDF: https://help.zscaler.com/pdf/com/en/1484976.pdf

All [AppProtection profiles](/zpa/about-inspection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtections are managed. AppProtection controls are grouped by predefined controls that come from ThreatLabZ, Open Web Application Security Project (OWASP), and WebSocket, or custom WebSocket or HTTP controls. To learn more, see [About ThreatLabZ Controls](/zpa/about-threatlabz-controls), [About Custom Controls](/zpa/about-custom-controls) and [About WebSocket Controls](/zpa/about-websocket-controls).
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
On the OWASP Predefined Controls page (Configuration & Control > Security > AppProtection Controls > OWASP Predefined Controls), you can do the following:
- View more information about the predefined controls.
- Expand all the rows in the table to see more information about each predefined control.
- Filter the information that appears in the table. By default, the version is set to OWASP_CRS/4.8.0. Some predefined controls are unavailable in older versions. If you are using Anomalies or Web Shells OWASP predefined control groups, you can experience download latency.
- For each predefined control type, expand to view:
- **Control Number**: A number identifying the predefined control. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the predefined control.
- **Control Name**: The name of the predefined control.
- **Severity**: The level of severity for the control number. The severity levels are **Low**, **Medium**, **High**, and **Critical**.
- **Control Action**: What action occurs when the predefined control is in use.
- Go to the [ThreatLabZ Controls](/zpa/about-threatlabz-controls) page to view the available predefined controls.
- Go to the [Custom Controls](/zpa/about-custom-controls) page to manage your custom controls.
- Go to the [WebSocket Controls](/zpa/about-websocket-controls) page to manage your WebSocket predefined and custom controls.
- Go to the [API Controls](/zpa/about-api-protection-controls) page to view your API controls.
- Go to the Security Profiles page to create and manage [AppProtection Profiles](/zpa/about-appprotection-policy) and [Browser Protection Profiles](/zpa/about-browser-protection-profiles).
![Inspection Controls and the OWASP Predefined Controls page in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/about-appprotection-controls/About%20AppProtection%20Controls%20page_0.png)