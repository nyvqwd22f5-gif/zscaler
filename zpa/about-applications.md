# About Applications
Source: https://help.zscaler.com/zpa/about-applications
PDF: https://help.zscaler.com/pdf/com/en/1483556.pdf

An *application* is a fully qualified domain name (FQDN), local domain name, or IP address that you define on a standard set of ports. Applications must be defined within an application segment.
To enable [application discovery](/zpa/about-application-discovery), you can define an application as an FQDN in wildcard format or as an IP subnet.
An* application segment *is a grouping of defined applications, based upon access type or user privileges. So, ZPA features such as double encryption, health reporting, etc. are configured per application segment.
[See image.](#image_app)
Defining your applications in application segments enables you to:
- Restrict access to excess ports for the application, reducing the application’s attack surface.
- Leverage those application segments in access policies to restrict user groups that can access them, as well as reduce lateral movement.
- Apply advanced capabilities such as Browser Access, Isolation, AppProtection, and data loss prevention that you are licensed for.
Read about the following key configuration options available for your applications before configuring an application segment within ZPA:
- [Application Access](/zpa/about-application-access)
- [AppProtection](/zpa/accessing-application-protocol-diagnostics)
- [Browser Access](/zpa/about-BrowserAccess)
- [Bypass](/zpa/configuring-bypass-settings)
- [Double Encryption](/zpa/understanding-double-encryption)
- [Health Reporting](/zpa/understanding-health-reporting)
- [Privileged Remote Access (PRA)](/zpa/about-privileged-portals)
About the Defined Application Segments Page
[]On the Defined Application Segments page (Resource Management > Application Management > Application Segments > Defined Application Segments), you can do the following:
-
[Validate a client hostname.](/zpa/validating-client-hostname)
If you are using a [Microtenant](/zpa/about-microtenants), this option is hidden.
-
[View and add DNS search domains.](/zpa/adding-dns-search-domains)
DNS search domains are unique per customer. When configuring [Microtenants](/zpa/about-microtenants), DNS search domains that are added in the default tenant are inherited across Microtenants.
- [Add an application segment.](/zpa/configuring-application-segments)
- Select the [Show Recommendation Before Editing](/zpa/editing-application-segments#ShowRecommendation) option.
- Open the **Column Menu** to:
- Expand all rows in the table to see more information about each application segment. Alternatively, you can click on the **Expand** icon next to the name to see more information about the selected application segment.
- [Set application segment configuration warnings.](/zpa/setting-application-segment-configuration-warnings)
- Download the configuration information for the application segments to a CSV file. The file lists the application segments based on the selected table filters.
-
Filter the information that appears in the table. By default, no filters are applied.
If you are using a Microtenant, then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the application segments configured within that specific Microtenant. The options for the filter are based on access type (**Global**, **Configured with Microtenant**, **Shared to this Microtenant**, and **Share from this Microtenant**). The only available operator for this filter type is **Equals**.
- View a list of all application segments that were configured for your organization. For each application segment, you can see:
-
**Name**: The name of the application segment. When you expand the row for an application segment, you can [see more information.](#moreappsegmentdetails)
If an application segment is missing required settings, the yellow **Caution** icon (![Yellow Caution Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-yellow-caution-icon.jpg)
) appears next to its name within the table. Edit the application segment to resolve the configuration issues. If an application segment is Source IP Anchoring-enabled, the **Information** icon (![Information Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-information-icon.jpg)
) appears next to its name within the table.
-
**Applications**: A list of up to three defined applications within the application segment. Browser Access enabled-applications are denoted by a **Browser Access** icon (![Browser Access Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-browser-access-icon.jpg)
). Privileged Remote Access-enabled applications are denoted by a **Privileged Remote Access **icon (![zpa-privileged-remote-access-icon.jpg](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-privileged-remote-access-icon.jpg)
). All other applications are denoted by a **Zscaler Client Connector** icon (![Zscaler Client Connector Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-zscaler-client-connector-icon.jpg)
). If there are more than three applications, then only the number of defined applications appears.
For all applications, there is a link to view the **Application Segment** details with a list of all the applications for the application segment. [The details page includes:](#appdetails)
[See image.](#image_appsegdetails)
- **Status**: Indicates that the application segment is enabled or disabled.
- **Health Reporting**: Indicates whether health reporting for the application is **Continuous**, **On Access**, or **None**. To learn more, see [About Health Reporting](/zpa/about-health-check-and-reporting#AboutHealthReporting).
-
[View a configuration graph of connected objects.](/zpa/pselabel/viewing-configuration-graphs)
- Copy an existing application segment.
-
[Move the application segment to a Microtenant.](/zpa/moving-defined-application-segments)
The **Move** icon is only visible if there are one or more Microtenants available. If you are using a [Microtenant](/zpa/about-microtenants), the **Share** icon (![Share Icon](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-share-icon.jpg)
) appears. If you [share an application segment with another Microtenant](/zpa/sharing-defined-application-segments), it appears as **Shared to** when you expand the application segment.
- [View policy usage details.](/zpa/viewing-policy-usage-details)
- [Edit an existing application segment.](/zpa/editing-application-segments)
- Download the configuration information for an application segment to a CSV file.
- Delete an application segment.
Zscaler recommends you consider the following when deleting an application segment:
- If an application segment is referenced in a segment group and has a policy configured, the delete action is unavailable. An admin must manually review and remove the link to the policy to successfully delete the application segment. If an application segment is referenced by ZIA for Source IP Anchoring, the delete action is unavailable. A **Lock** icon (![Lock icon within the tables of the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/zpa-application-lock-icon.png)
) appears in its place. To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring).
- If an application segment is configured using Zscaler Deception, then the copy, edit, and delete options are unavailable.
- Depending on your ZPA Admin Portal subscriptions, you can see the following pages:
- [Browser Access](/zpa/about-BrowserAccess): Manage applications where Browser Access is enabled.
- [Segment Groups](/zpa/about-applicationgroups): Add a new segment group or manage existing groups.
- [AppProtection](/zpa/about-appprotection-applications): Manage applications where AppProtection is enabled.
- [Privileged Remote Access](/zpa/about-privileged-remote-access-applications): Manage applications where Privileged Remote Access is enabled.
- [AI-Powered Recommendations](/zpa/about-ai-powered-recommendations-application-segments): View and manage AI-powered recommendations for application segments.
![Application Segments page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/applications/about-applications/ZPA-Defined-Application-Segments-Page-5.png)
[]![Add Application Segment window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/Add%20Application%20Segment%20window.png)
- []**Description**: (Optional) Enter a description for the application segment.
- **Segment Group**: The segment group that the application segment is a member of.
- **Server Groups**: The server groups that the applications are hosted on.
- **Double Encryption**: Indicates whether [Double Encryption](/zpa/about-double-encryption) is enabled or disabled for all applications. By default, if a Browser Access-enabled application was defined, **Double Encryption** is disabled.
- **Bypass**: Indicates whether users can [bypass ZPA](/zpa/how-do-i-configure-and-corporate-network-settings) to access applications.
- **Zscaler Client Connector can receive CNAME**: Indicates if Zscaler Client Connector receives CNAME DNS records from App Connectors.
- **Source IP Anchor**: Indicates if [Source IP Anchoring](/zia/about-source-ip-anchoring), for use with Zscaler Internet Access (ZIA), is enabled or disabled for all applications.
- **ICMP Access**: Indicates if [ICMP communication](/zpa/configuring-application-segments#define-clientconnector) is enabled or disabled for all applications.
- **App Connector Closest to Application**: Indicates if the App Connector is [closest to the application](/zpa/configuring-application-segments#define-cmnconfig) (**Enabled**) or closest to users (**Disabled**).
- **Inspect Traffic with ZIA**: Indicates if the traffic for the application segments is enabled to be inspected with ZIA.
- **Active Directory Inspection**: Indicates if the traffic for the application segment is inspected with [Active Directory (AD) Protection protocols](/zpa/accessing-ad-protection-diagnostics).
- **Auto App Protection**: Indicates if the traffic for the application segment is inspected with [AppProtection protocols](/zpa/accessing-application-protocol-diagnostics).
- []**TCP Port Ranges**: The TCP port ranges being used to access applications.
- **UDP Port Ranges**: The UDP port ranges being used to access applications.
- **Certificate**: The certificate that matches the fully qualified domain the user accesses when using Browser Access, Isolation, or Privileged Remote Access.
- **Protocol**: The protocol that the application is using. Use **HTTP** or **HTTPS** for Browser Access and Browser Isolation. Use **VNC**, **SSH**, or **RDP** for Privileged Remote Access.
- **Server Port**: The web server port number used when a request is made to access a Browser Access-enabled or Privileged Remote Access-enabled application.
- **Use Untrusted Certificates**: Indicates whether [Use Untrusted Certificates](/zpa/about-application/onboard#tab1) is enabled or disabled for a Browser Access-enabled or Privileged Remote Access-enabled application.
[]![Application Segment details](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-applications/About%20Application%20Details%20commercial%20version.png)