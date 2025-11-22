# About API Protection Controls
Source: https://help.zscaler.com/unified/about-api-protection-controls
PDF: https://help.zscaler.com/pdf/com/en/1505526.pdf

API Protection controls provide inspection of API traffic by flagging transactions that include security violations such as social security numbers and credit card numbers. Zscaler doesn't store the details or actual numbers of this secure data; Zscaler instead identifies these transactions as a security violation category. You can view the analytics of these inspected APIs by going to the [API Protection Dashboard](/unified/viewing-api-protection-dashboard) and the [API Protection Diagnostics](/unified/accessing-api-protection-diagnostics) pages. All [AppProtection profiles](/unified/about-appprotection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtection is managed. You can create multiple API Protection controls to use within the same AppProtection profile by [designating application segments with API Protection](/unified/configuring-defined-application-segments).
API Protection controls enhance your experience by enabling you to:
- Protect APIs from the latest threats by inspecting API transactions for security violations.
- Gain detailed visibility on API data (users, methods, errors, and sensitive information handling) over a selected time frame.
Each API Protection control is identified with a unique number, defined with how the control operates, and associated with the level of concern. The API Protection controls are organized into categories:
- Security Misconfiguration
- Server Side Request Forgery
- Info Disclosure Controls
About the API Protection Controls Page
On the API Protection Controls page (Policies > Cybersecurity > Inline Security > Protection Controls > API Protection Controls), you can do the following:
- Expand all of the rows in the table to see more information about each predefined control.
- Filter the information that appears in the table.
- For each predefined control type, expand to view:
- **Control Number**: A number to differentiate each API Protection control. The table shows the controls in the order they were created, and the order cannot be changed. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the API Protection control. Select an AppProtection profile if you want to edit it.
- **Control Name**: The name of the API Protection control.
- **Severity**: The level of security concern the API Protection control has.
- **Control Action**: The action ZPA uses for this API Protection control.
- Go to the [ThreatLabZ Controls](/unified/about-threatlabz-controls) page to view the available predefined controls.
- Go to the [OWASP Predefined Controls](/unified/about-appprotection-profiles) page to view the available predefined controls.
- Go to the [Custom Controls](/unified/about-custom-controls) page to view the available custom controls.
- Go to the [WebSocket Controls](/unified/about-websocket-controls) page to manage your WebSocket predefined and custom controls.
![View the API Protection Control page in the ZPA Admin portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/about-api-protection-controls/Updated%20expand%20table%20view_0.jpg)