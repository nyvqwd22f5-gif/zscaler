# About Applications
Source: https://help.zscaler.com/zsdk/about-applications
PDF: https://help.zscaler.com/pdf/com/en/1508981.pdf

An application is an FQDN, local domain name, or IP address that you define on a standard set of ports. Applications must be defined within an application segment.
To enable [application discovery](/zpa/about-application-discovery), you can define an application as an FQDN in wildcard format or as an IP subnet.
An* *application segment is a grouping of defined applications, based upon access type or user privileges. So, features such as double encryption and health reporting are configured per application segment.
Defining your applications as application segments provides the following benefits and enables you to:
- Restrict access to ports not included in your defined application segment, reducing the application’s attack surface.
- Leverage application segments to configure access policies to restrict user groups that can access them, as well as reduce lateral movement.
Read about the following key configuration options available for your applications before configuring an application segment:
- [Application Access](/zpa/about-application-access)
- [Bypass](/zpa/how-do-i-configure-and-corporate-network-settings)
- [Double Encryption](/zpa/about-double-encryption)
- [Health Reporting](/zpa/about-health-check-and-reporting#AboutHealthReporting)
About the Defined Application Segments Page
[]On the Defined Application Segments page (Resource Management > Application Management > Application Segments > Defined Application Segments), you can do the following:
-
[Validate a client hostname.](/zpa/validating-client-hostname)
[See image.](#image_validatemenu)
- [Add an application segment.](/zsdk/defining-and-managing-application-segments)
- Access the Application Segments menu.
- [Functions of the Application Segments Menu](#menuApplicationSegments)
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all application segments that were configured for your organization. For each application segment, you can see the following information:
- **Name**: The name of the application segment. When you expand the row for an application segment, you can [see more information.](#moreappsegmentdetails)
-
**Applications**: Lists up to three defined applications within the application segment. Applications are denoted by a **Zscaler Client Connector** icon (![Zscaler Client Connector Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-zscaler-client-connector-icon.jpg)
). If there are more than three applications, then only the number of defined applications appears.
For all applications, there is a link to view the **Application Segment** details with a list of all the applications for the application segment.
- [Application Segment Details](#appdetails)
[See image.](#image_appsegdetails)
- **Status**: Indicates that the application segment is enabled or disabled.
- **Health Reporting**: Indicates whether [health reporting](/zpa/about-health-check-and-reporting#AboutHealthReporting) for the application is **Continuous**, **On Access**, or **None**.
- [View a configuration graph of connected objects.](/zsdk/viewing-configuration-graphs)
- [Copy the application segment.](/zsdk/defining-and-managing-application-segments)
- [Edit the application segment.](/zsdk/defining-and-managing-application-segments)
- Download a CSV file with information on the selected application segment.
- [Delete an application segment.](/zsdk/defining-and-managing-application-segments)
- Go to the [Segment Groups](/zsdk/about-segment-groups) page to add a new segment group or manage existing segment groups.
![Add or configure application segments on the Application Segments page](/downloads/zsdk/applications/about-applications/ZSDK-Application-Defined-ApplicationSegments-Overview-2-1.png)
[]
If an application segment is missing the required settings, the **Incomplete Configuration** icon (![Yellow Caution Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-yellow-caution-icon.jpg)
) appears next to its name. Edit the application segment to resolve the configuration issues. If an application segment is Source IP Anchoring-enabled, the **Information** icon (![Information Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-information-icon.jpg)
) appears next to its name.
- **Description**: (Optional) Enter a description for the application segment.
- **Segment Group**: The segment group that the application segment is a member of.
- **Server Groups**: The server groups that the applications are hosted on.
- **Double Encryption**: Indicates whether [Double Encryption](/zpa/about-double-encryption) is enabled or disabled for all applications. By default, if a Browser Access-enabled application was defined, **Double Encryption** is disabled.
- **Bypass**: Indicates whether users can [bypass ZSDK](/zpa/configuring-bypass-settings) to access applications.
- **Client Connector can receive CNAME**: Indicates whether Zscaler Client Connector receives CNAME DNS records from App Connectors.
- **Source IP Anchor**: Indicates whether [Source IP Anchoring](/zia/about-source-ip-anchoring), for use with Zscaler Internet Access (ZIA), is enabled or disabled for all applications.
- **ICMP Access**: Indicates whether [ICMP communication](/zpa/configuring-application-segments#define-clientconnector) is enabled or disabled for all applications.
- **App Connector Selection Method**: Indicates whether the App Connector is [closest to the application](/zpa/configuring-application-segments#define-cmnconfig) (**Enabled**) or closest to users (**Disabled**).
[]
- **TCP Keepalive**: Zscaler recommends keeping this setting as **Disabled**.
- **TCP Port Ranges**: The TCP port ranges being used to access applications.
- **UDP Port Ranges**: The UDP port ranges being used to access applications.
[]
-
**Expand All**: Expand all rows in the table to see more information about each application segment.
You can opt to expand one row by clicking the **Expand** icon of the application segment's name.
- **Set Application Warnings**: You can enable or disable configuration warnings for the Defined Application Segments page. To learn more, see [Setting Application Segment Configuration Warnings](/zpa/setting-application-segment-configuration-warnings).
- **Download as CSV**: Download the configuration information for the application segments to a CSV file. The file lists the application segments based on the selected table filters.
[See image.](#image_applicationsegmentmenu)
[]
![View the selected application segment details](/downloads/zsdk/application-management/about-applications/ZSDK-ApplicationSegments-Details.png)
[]
![Open the column menu to view the Client Hostname Validation option](/downloads/zsdk/applications/application-management/about-applications/ZSDK-Validations-Menu_outline.png)
[]
![Open the Application Segments column menu to configure how you view the Application Segments list.](/downloads/zsdk/applications/application-management/about-applications/ZSDK-ApplicationSegments-Menu_outline.png)