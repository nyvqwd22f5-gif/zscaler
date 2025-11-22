# About Active Directory Controls
Source: https://help.zscaler.com/unified/about-active-directory-controls
PDF: https://help.zscaler.com/pdf/com/en/1517871.pdf

The Active Directory controls currently available in the ZPA Admin Portal are predefined controls that are enforced by [enabling Active Directory in an application segment](/unified/configuring-defined-application-segments#protectsteps). The supported protocols are Kerberos, SMB, and LDAP. Active Directory controls are displayed on the Active Directory Controls page. You can add Active Directory controls to an [AppProtection profile](/zpa/about-appprotection-policy). An AppProtection profile defines how the Active Directory controls and other [AppProtection controls](/unified/about-appprotection-controls) are managed. You can view the Active Directory control inspection results on the [Active Directory Protection dashboard](/unified/viewing-active-directory-protection-dashboard).
Active Directory controls enhance your experience by enabling you to:
- Protect internal applications from the latest threats by inspecting Active Directory-enabled application segment transactions for security violations.
- Gain detailed visibility on Active Directory data (users, errors, suspicious activity, and AppProtection control and profile violations) over a selected time frame.
About the Active Directory Controls Page
On the Active Directory Controls page (Configuration & Controls > Security > AppProtection Controls > Active Directory Controls), you can do the following:
- Filter the information that appears in the table.
- Expand all of the rows in the table to see more information about each Active Directory control.
- For each Active Directory type, expand to view:
- **Control Number**: A number to differentiate each Active Directory control. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the Active Directory control.
- **Name**: The name of the Active Directory control.
- **Severity**: The level of severity for the control number. The severity levels are **Low**, **Medium**, **High**, and **Critical**.
- **Control Action**: What action occurs when the Active Directory control is in use.
- Go to the [ThreatLabZ Controls](/unified/about-threatlabz-controls) page to view the available ThreatLabZ controls.
- Go to the [OWASP Predefined Controls](/unified/about-appprotection-controls) page to view the available OWASP predefined controls.
- Go to the [Custom Controls](/unified/about-custom-controls) page to view the available Custom controls.
- Go to the [WebSocket Controls](/unified/about-websocket-controls) page to view the available WebSocket controls.
- Go to the [API Controls](/unified/about-api-protection-controls) page to view the available API controls.
- Go to the Security Profiles page to create and manage [AppProtection Profiles](/unified/about-appprotection-policy) and [Browser Protection Profiles](/unified/about-browser-protection-profiles).
![Active Directory Controls page in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/about-threatlabz-controls/Active%20Directory%20Controls%20page%20w%20steps.png)