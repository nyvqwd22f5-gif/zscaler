# About ThreatLabZ Controls
Source: https://help.zscaler.com/zpa/about-threatlabz-controls
PDF: https://help.zscaler.com/pdf/com/en/1485491.pdf

All [AppProtection profiles](/zpa/about-inspection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtections are managed. AppProtection controls are grouped by HTTP predefined controls that come from ThreatLabZ or [Open Web Application Security Project (OWASP)](/zpa/about-inspection-controls) and predefined controls for WebSocket. Custom controls can be created for [HTTP](/zpa/about-custom-controls) or [WebSocket](/zpa/about-websocket-controls).
ThreatLabZ controls enhance your experience by enabling you to:
- Protect internal applications from the latest threats by providing up-to-date controls written and maintained by Zscaler's expert security team that address emerging attack vectors and vulnerabilities.
- Understand the severity, description, and recommended default action for each type of attack that ThreatLabZ controls protect against.
The ThreatLabZ predefined controls currently available in the ZPA Admin Portal are created by the Zscaler Security team to address confirmed Common Vulnerabilites and Exposures (CVEs). Each predefined control is identified with a unique number, defined with how the control operates, and associated with a level of concern.
[]About the ThreatlabZ Controls Page
On the ThreatLabZ Controls page (Configuration & Controls > Security > AppProtection Controls > ThreatLabZ Controls), you can do the following:
- View more information about the predefined controls.
- Expand all of the rows in the table to see more information about each predefined control.
- Filter the information that appears in the table.
- For each predefined control type, expand to view:
- **Control Number**: A number identifying the predefined control. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Info URL**: A link to the security portal describing the predefined control.
- **Used in AppProtection Profiles**: The AppProtection profiles using the predefined control.
- **Name**: The name of the predefined control.
- **Severity**: The level of severity for the control number. The severity levels are **Low**, **Medium**, **High**, and **Critical**.
- **Version**: The current version of the ThreatLabZ predefined control.
- **Control Action**: What action occurs when the predefined control is in use.
- Go to the [OWASP Predefined Controls](/zpa/about-inspection-profiles) page to view the available predefined controls.
- Go to the [Custom Controls](/zpa/about-custom-controls) page to manage your custom controls.
- Go to the [WebSocket Controls](/zpa/about-websocket-controls) page to manage your WebSocket predefined and custom controls.
- Go to the [API Controls](/zpa/about-api-protection-controls) page to view your API controls.
- Go to the Security Profiles page to create and manage [AppProtection Profiles](/zpa/about-appprotection-policy) and [Browser Protection Profiles](/zpa/about-browser-protection-profiles).
![ThreatLabZ Controls page in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/about-threatlabz-controls/About%20ThreatLabZ%20Controls%20page.png)