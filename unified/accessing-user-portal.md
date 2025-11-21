# Accessing a User Portal
Source: https://help.zscaler.com/zpa/accessing-user-portal
PDF: https://help.zscaler.com/pdf/com/en/1484411.pdf

A ZPA user portal can display links to applications that your end users are authorized to access, as well as links to public applications or websites that your organization commonly uses.
After an end user logs in to a user portal and is authenticated via single sign-on (SSO), an Acceptable Use Policy (AUP) can be displayed before they can access it. If an AUP is displayed, your end users must read and accept the policy terms.
The user portal for Browser Access is dependent on the Default Timeout Policy rule's authentication timeout.
[See image.](#AUP-Img)
After an end user logs in, the user portal home page appears. A list of all applications available to them are displayed based on the access policies for the application segments, which can be launched directly from the portal. Any applications with a policy rule set to **Deny** are not visible to the end user.
ZPA User Portal Features
![Example ZPA User Portal](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-example.png)
Any messages from a ZPA admin can be displayed at the top of the page, and can be dismissed by an end-user if they click the **Close** icon.
End-user can click on a link to launch an application. The user portal displays the following application link types, which are denoted by an icon:
- ![Zscaler Client Connector icon](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-zappicon.png)
- private (i.e., internal) applications that can only be accessed via the Zscaler Client Connector.
- ![Browser Access icon](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-baicon.png)
- private web applications that can be accessed via your web browser (i.e., Browser Access).
- ![Public link icon](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-publicicon.png)
- public (i.e., Software-as-a-Service) web applications or other public websites.
![Example application links on a user portal](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-example2.png)
By default, all link types are displayed but an end-user can filter the list using the drop-down menu. [See image.](#AllTypesMenu-Img)
If a link is displayed but is inactive (i.e., grayed out), then an end-user cannot launch it directly from the portal and might require a native client for that specific application (e.g., SSH, RDP, etc.). In addition to the native client, the end-user also needs to have Zscaler Client Connector (Z App) installed and enrolled on that device. To learn more, see [What is the Zscaler Client Connector?](/z-app/what-zscaler-app) and [End User Guides](/z-app/end-user-guides). If they do not have Zscaler Client Connector installed, you can give them the ability to **Download Zscaler Client Connector** from the portal. To learn more, see [About Zscaler Client Connector Download Links](/zpa/about-zscaler-app-download-links). [See image.](#ZAppLinkGrayedOut-Img)
[]![Example AUP page for a ZPA user portal](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-aupexample.png)
[]![All Types drop-down menu within a ZPA user portal](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-alltypesmenu.png)
[]![Grayed out application link with Download Zscaler Client Connector button in a user portal](/downloads/zpa/user-portal/accessing-user-portal/zpa-userportal-example3.png)