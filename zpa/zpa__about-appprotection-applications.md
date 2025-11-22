# About AppProtection Applications
Source: https://help.zscaler.com/zpa/about-appprotection-applications
PDF: https://help.zscaler.com/pdf/com/en/1485031.pdf

When [creating an application segment](/zpa/configuring-application-segments), you can identify the web applications that require AppProtection before users can access those applications. This is done by using various levels and types of [custom](/zpa/about-custom-controls) and [predefined controls](/zpa/about-inspection-controls) in an [AppProtection profile](/zpa/about-inspection-profiles) before ZPA provides access. This provides another way to protect your applications from users that should not have access.
AppProtection application segments provide the following benefits and enable you to:
- Identify and select applications for protection against attacks related to OWASP predefined controls and zero-day threats.
- Configure HTTP/S ports and provide certificates for inspection of encrypted traffic.
When you define an application within an application segment and enable AppProtection for the application, Zscaler Client Connector access is automatically applied. This allows your users to request access to the application via any web browser that supports TLS 1.2 (with cipher suite ECDHE-RSA-AES128-GCM-SHA256) or via Zscaler Client Connector. ZPA supports HTTP and HTTPS protocols.
About the AppProtection Page
On the AppProtection page (Resource Management > Application Management > AppProtection), you can do the following:
- Expand all the rows in the table to see more information about each application.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all applications that were specifically configured for AppProtection within an application segment. For each application, you can see:
- **Name**: The name of the application. When expanded, the following information is displayed:
- **Segment Group**: The segment group that the application segment is a member of.
- **Server Groups**: The server groups that the application is hosted on.
- **Certificate**: The [certificates](/zpa/about-web-server-certificates) associated to the specified application.
- **Domain**: The fully qualified domain name (FQDN) associated to the application.
- **Status**: Indicates that the application segment is enabled or disabled.
- **Application Protocol**: The protocol (HTTPS or HTTP) used for the application.
- **Application Port**: The port number used for the application.
- [Edit an existing application segment](/zpa/about-application/edit).
- Delete an application.
- Go to the [Application Segments](/zpa/about-applications) page to add a new application segment or manage existing application segments.
- Go to the [Browser Access](/zpa/about-BrowserAccess) page to manage applications where Browser Access is enabled.
- Go to the [Privileged Remote Access](/zpa/about-privileged-remote-access-applications) page to manage applications where Privileged Remote Access is enabled.
- Go to the [Segment Groups](/zpa/about-applicationgroups) page to add a new segment group or manage existing groups.
![AppProtection page with AppProtection applications in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-inspection-applications/Inspec%20App%20page%20w%20steps_0.png)