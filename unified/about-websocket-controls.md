# About WebSocket Controls
Source: https://help.zscaler.com/zpa/about-websocket-controls
PDF: https://help.zscaler.com/pdf/com/en/1485201.pdf

All [AppProtection profiles](/zpa/about-inspection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtections are managed. To learn more, see [About AppProtection Controls](/zpa/about-inspection-controls).
The WebSocket controls currently available in the Zscaler Private Access (ZPA) Admin Portal are WebSocket predefined controls and WebSocket custom controls. WebSocket predefined controls are automatically populated in the portal. You can create WebSocket custom controls and use them within a new or existing AppProtection profile. Custom controls give you the flexibility to set and define the specific request and response elements (e.g., max fragments per message, max payload size, etc.) and the preferred action used to handle them.
WebSocket controls allow you to inspect your WebSocket protocol traffic. The data is sent from ZPA to the application server or from the application server to ZPA. The WebSocket TCP connection remains open until it is closed by either ZPA, a client, or the application server.
WebSocket controls enhance your experience by enabling you to:
- Protect internal applications from common attacks associated with WebSocket controls.
- Understand the severity, description, and recommended default action for each type of attack related to WebSocket controls.
The WebSocket predefined controls are organized into various categories:
- WebSocket Handshake Headers Check
- WebSocket Framing Errors
- Frame Type Verification
- Client Mask Bit Verification
- Server Unmask Bit Verification
To verify the handshake header values (i.e., Upgrade and Connection), leverage the existing HTTP custom controls.
About the WebSocket Controls Page
On the WebSocket Controls page (Configuration & Control > Security > AppProtection Controls > WebSocket Controls), you can do the following:
- Expand all the rows in the table to see more information about each Websocket control.
- [Add a new WebSocket custom control](/zpa/configuring-websocket-controls).
- View a list of all configured WebSocket controls:
- **Control Number**: A number to differentiate each WebSocket control. The table shows the controls in the order they were created, and the order cannot be changed. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the WebSocket control. Select an AppProtection profile if you want to edit it.
- **Name**: The name of the WebSocket control.
- **Category**: Whether the WebSocket control is a custom control or a predefined control.
- **Severity**: The level of security concern the WebSocket control has.
- **Control Action**: The action ZPA uses for this WebSocket control.
- [Edit a WebSocket custom control](/zpa/edit-websocket-controls).
- Delete a custom control.
When a WebSocket control is in use by an [AppProtection profile](/zpa/about-inspection-profiles), it cannot be deleted.
- Go to the [ThreatLabZ Controls](/zpa/about-threatlabz-controls) page to view the available predefined controls.
- Go to the [OWASP Predefined Controls](/zpa/about-inspection-profiles) page to view the available predefined controls.
- Go to the [Custom Controls](/zpa/about-custom-controls) page to view the available custom controls.
- Go to the [API Controls](/zpa/about-api-protection-controls) page to view your API controls.
- Go to the Security Profiles page to create and manage [AppProtection Profiles](/zpa/about-custom-controls) and [Browser Protection Profiles](/zpa/about-browser-protection-profiles).
![WebSocket Controls page for Inspection Controls in the ZPA Admin Portal](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/websocket-controls/about-websocket-controls/About%20WebSocket%20page_0.png)