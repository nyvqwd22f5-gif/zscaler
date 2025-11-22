# About Custom Controls
Source: https://help.zscaler.com/unified/about-custom-controls
PDF: https://help.zscaler.com/pdf/com/en/1492996.pdf

All [AppProtection profiles](/unified/about-appprotection-profiles) have a set of AppProtection controls that you can use to help you define how AppProtections are managed. To learn more, see [About AppProtection Controls](/unified/about-appprotection-controls).
Custom controls give you the flexibility to set and define the specific request and response elements (e.g., request header, response body, etc.) and the preferred action used to handle them. You can create multiple custom controls and use them within the same AppProtection profile.
Custom controls enhance your experience by enabling you to:
- Create highly tailored custom controls based on specific requests or response elements.
- Create the description, set the severity level, and set the default action for each custom control.
About the Custom Controls Page
On the Custom Controls page (Policies > Cybersecurity > Inline Security > Protection Controls), you can do the following:
- Go to the [ThreatLabZ Controls](/unified/about-threatlabz-controls) page to view the available predefined controls.
- Go to the [OWASP Predefined Controls](/unified/about-appprotection-profiles) page to view the available predefined controls.
- Go to the [WebSocket Controls](/unified/about-websocket-controls) page to manage your WebSocket predefined and custom controls.
- Expand all the rows in the table to see more information about each custom control.
- [Add a new Custom Control](/unified/configuring-custom-controls).
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all configured custom controls:
- **Control Number**: A number to differentiate each custom control. The table shows the controls in the order they were created, and the order cannot be changed. When expanded, the following information is displayed:
- **Description**: An explanation of how the control works.
- **Paranoia Level**: The associated level, which corresponds to the levels available in an AppProtection profile.
- **Used in AppProtection Profiles**: The AppProtection profiles using the custom control.
- **Expression**: The way the custom control is defined.
- **Name**: The name of the custom control.
- **Control Type**: A list of the elements that make up this custom control.
- **Severity**: The level of security concern the custom control has.
- **Control Action**: The action for this custom control.
- [Edit a custom control](/unified/editing-custom-controls).
- Delete a custom control.
When a custom control is in use by an [AppProtection profile](/unified/about-appprotection-profiles), it cannot be deleted.
![Viewing and managing custom controls](/downloads/unified/policies/private-applications/cybersecurity/appprotection-private-application-traffic-controls-profiles/custom-controls/about-custom-controls/unified-custom-controls-page.png)