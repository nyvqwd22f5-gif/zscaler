# About AppProtection Applications
Source: https://help.zscaler.com/unified/about-appprotection-applications
PDF: https://help.zscaler.com/pdf/com/en/1492151.pdf

When [creating an application segment](/unified/configuring-defined-application-segments), you can identify the web applications that require AppProtection before users can access those applications. This is done by using various levels and types of [custom](/unified/about-custom-controls) and [predefined controls](/unified/about-appprotection-controls) in an [AppProtection profile](/unified/about-appprotection-profiles) before access is provided. This provides another way to protect your applications from users that should not have access.
AppProtection application segments provide the following benefits and enable you to:
- Identify and select applications for protection against attacks related to OWASP predefined controls and zero-day threats.
- Configure HTTP/S ports and provide certificates for inspection of encrypted traffic.
When you define an application within an application segment and enable AppProtection for the application, Zscaler Client Connector access is automatically applied. This allows your users to request access to the application via any web browser that supports TLS 1.2 (with cipher suite ECDHE-RSA-AES128-GCM-SHA256) or via Zscaler Client Connector. Private Apps support HTTP and HTTPS protocols.
About the AppProtection Page
On the AppProtection page, you can do the following:
- Expand all the rows in the table to see more information about each application.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all applications that were specifically configured for AppProtection within an application segment. For each application, you can see:
- **Name**: The name of the application. When expanded, the following information is displayed:
- **Segment Group**: The segment group that the application segment is a member of.
- **Server Groups**: The server groups that the application is hosted on.
- **Certificate**: The [certificates](/unified/about-web-server-certificates) associated to the specified application.
- **Domain**: The fully qualified domain name (FQDN) associated to the application.
- **Status**: Indicates that the application segment is enabled or disabled.
- **Application Protocol**: The protocol (HTTPS or HTTP) used for the application.
- **Application Port**: The port number used for the application.
- [Edit an existing application segment](/unified/editing-defined-application-segments).
- Delete an application.
![AppProtection page with AppProtection applications in the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-inspection-applications/Inspec%20App%20page%20w%20steps_0.png)