# About Defined Application Segments
Source: https://help.zscaler.com/unified/about-defined-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1492081.pdf

An *application* is a fully qualified domain name (FQDN), local domain name, or IP address that you define on a standard set of ports. Applications must be defined within an application segment.
To enable [application discovery](/unified/about-application-discovery), you can define an application as an FQDN in wildcard format or as an IP subnet.
An* application segment *is a grouping of defined applications, based upon access type or user privileges. So, features such as double encryption, health reporting, etc. are configured per application segment.
[See image.](#image_app)
Defining your applications in application segments enables you to:
- Restrict access to excess ports for the application, reducing the application’s attack surface.
- Leverage those application segments in access policies to restrict user groups that can access them, as well as reduce lateral movement.
- Apply advanced capabilities such as Browser Access, Isolation, AppProtection, and data loss prevention that you are licensed for.
Read about the following key configuration options available for your applications before configuring an application segment:
- [Application Access](/unified/about-application-access)
- [AppProtection](/unified/about-appprotection-applications)
- [Browser Access](/unified/about-browser-access)
- [Bypass](/unified/configuring-bypass-settings)
- [Double Encryption](/unified/about-double-encryption)
- [Health Reporting](/unified/understanding-health-reporting)
- [Privileged Remote Access (PRA)](/unified/about-privileged-portals)
About the Defined Application Segments Page
[]On the Defined Application Segments page (Policies > Access Control > Private Applications > App Segments), you can do the following:
- [Validate a client hostname.](/unified/validating-client-hostname)
If you are using a [Microtenant](/unified/about-microtenants), this option is hidden.
- [View and add DNS search domains.](/unified/adding-dns-search-domains)
DNS search domains are unique per customer. When configuring [Microtenants](/unified/about-microtenants), DNS search domains that are added in the default tenant are inherited across Microtenants.
- Expand all rows in the table to see more information about each application segment.
- [Set application segment configuration warnings.](/unified/setting-application-segment-configuration-warnings)
- [Add an application segment.](/unified/configuring-defined-application-segments)
- Download the configuration information for the application segments to a CSV file. The file lists the application segments based on the selected table filters.
- Go to the [AI-Powered Recommendations](/unified/about-ai-powered-recommendations-application-segments)page to view and manage recommended application segments.
- Go to the [Settings](/unified/configuring-ai-powered-recommendations-settings) page to add parameters to recommended application segment findings.
- Filter the information that appears in the table. By default, no filters are applied.
If you are using a Microtenant, then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the application segments configured within that specific Microtenant. The options for the filter are based on access type (**Global**, **Configured with Microtenant**, **Shared to this Microtenant**, and **Share from this Microtenant**). The only available operator for this filter type is **Equals**.
- View a list of all application segments that were configured for your organization. For each application segment, you can see:
- **Name**: The name of the application segment. When you expand the row for an application segment, you can [see more information.](#moreappsegmentdetails)
If an application segment is missing required settings, the incomplete configuration icon appears next to the name within the table. Edit it to resolve the configuration issues.
[See image.](#image_incompleteconfig)
If an application segment is Source IP Anchoring-enabled, the information icon appears next to the name within the table.
[See image.](#sipaicon)
- **Applications**: A list of up to three defined applications within the application segment. Browser Access enabled-applications are denoted by a;![Browser Access Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-browseraccess-globeicon_0.png)
icon. Privileged Remote Access-enabled applications are denoted by a ![Privileged Remote Access enabled icon](/downloads/zscaler-tech-pubs-style-guide/draft-articles/about-applications-draft-0/PRA%20icon.png)
icon. All other applications are denoted by a ![Zscaler Client Connector icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/ZAppIcon.png)
icon. If there are more than three applications, then only the number of defined applications appears.
For all applications, there is a link to view the **Application Segment** details with a list of all the applications for the application segment. [The details page includes:](#appdetails)
[See image.](#image_appsegdetails)
- **Status**: Indicates that the application segment is enabled or disabled.
- **Health Reporting**: Indicates whether health reporting for the application is **Continuous**, **On Access**, or **None**. To learn more, see [About Health Reporting](/unified/understanding-health-reporting).
- See a graphical view for how the application segment connects to other ZPA configuration objects (e.g., Segment group, Server groups, etc.)
You can edit any of the objects directly from the graphical view.
[See image.](#image_editgraph)
- Copy an existing application segment.
- Move the application segment in a Microtenant.>
The **Move **icon is only visible if there are one or more Microtenants available. If you are using a [Microtenant](/unified/about-microtenants), the **Share** icon appears. If you [share an application segment with another Microtenant](/unified/sharing-defined-application-segments), it appears as **Shared to** when you expand the application segment.
- Enable or disable Load Balance Server Groups.
- [Edit an existing application segment.](/unified/editing-defined-application-segments)
- Download the configuration information for an application segment to a CSV file.
- Delete an application segment.
Zscaler recommends you consider the following when deleting an application segment:
- If an application segment is referenced in a segment group and has a policy configured, the delete action is unavailable. An admin must manually review and remove the link to the policy to successfully delete the application segment. If an application segment is referenced by ZIA for Source IP Anchoring, the delete action is unavailable. A **Lock** icon (![Lock icon within the tables of the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-application-lock-icon.png)
) appears in its place. To learn more, see [About Source IP Anchoring](/unified/understanding-source-ip-anchoring).
- If an application segment is configured using Zscaler Deception, then the copy, edit, and delete options are unavailable.
![Using the Application Segments page within the ZPA Admin Portal](/downloads/unified/policies/private-applications/access-control/application-segments/about-applications/application-segments-page.png)
[]![Add Application Segment window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/Add%20Application%20Segment%20window.png)
- []**Description**: (Optional) Enter a description for the application segment.
- **Segment Group**: The segment group that the application segment is a member of.
- **Server Groups**: The server groups that the applications are hosted on.
- **Double Encryption**: Indicates whether [Double Encryption](/unified/about-double-encryption) is enabled or disabled for all applications. By default, if a Browser Access-enabled application was defined, **Double Encryption** is disabled.
- **Bypass**: Indicates whether users can bypass Private Applications to access applications.
- **Zscaler Client Connector can receive CNAME**: Indicates if Zscaler Client Connector receives CNAME DNS records from App Connectors.
- **Source IP Anchor**: Indicates if Source IP Anchoring is enabled or disabled for all applications.
- **ICMP Access**: Indicates if ICMP communication is enabled or disabled for all applications.
- **App Connector Closest to Application**: Indicates if the App Connector is [closest to the application](/unified/configuring-defined-application-segments#define-cmnconfig) (**Enabled**) or closest to users (**Disabled**).
- **Inspect Traffic with ZIA**: Indicates if the traffic for the application segments is enabled to be inspected.
- **Active Directory Inspection**: Indicates if the traffic for the application segment is inspected with Active Directory (AD) Protection protocols.
- **Auto App Protection**: Indicates if the traffic for the application segment is inspected with AppProtection protocols.
[]![Incomplete configuration warning on the Application Segments page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/Updated%20aboutapp%20icon%20screenshot_0.png)
- []**TCP Port Ranges**: The TCP port ranges being used to access applications.
- **UDP Port Ranges**: The UDP port ranges being used to access applications.
- **Certificate**: The certificate that matches the fully qualified domain the user accesses when using Browser Access, Isolation, or Privileged Remote Access.
- **Protocol**: The protocol that the application is using. Use **HTTP** or **HTTPS** for Browser Access and Browser Isolation. Use **VNC**, **SSH**, or **RDP** for Privileged Remote Access.
- **Server Port**: The web server port number used when a request is made to access a Browser Access-enabled or Privileged Remote Access-enabled application.
- **Use Untrusted Certificates**: Indicates whether [Use Untrusted Certificates](/unified/configuring-defined-application-segments) is enabled or disabled for a Browser Access-enabled or Privileged Remote Access-enabled application.
[]![Application Segment details](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/About%20Application%20Details%20commercial%20version.png)
[]![Edit object from Graphical View](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-segmentgroupspage-editingraphview.png)
[][![Information icon on the Application Segments page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/SIPA%20App%20Segment%20icon.png)
]