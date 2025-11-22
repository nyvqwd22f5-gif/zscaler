# About Application Access
Source: https://help.zscaler.com/zpa/about-application-access
PDF: https://help.zscaler.com/pdf/com/en/1483876.pdf

There are two ways to provide access to applications, through an application definition or by [application discovery](/zpa/about-application-discovery).
[]About Application Definitions
When [configuring an application segment](/zpa/about-application/onboard), you can define individual applications to change their settings (e.g., Double Encryption, Health Reporting, etc.) or configure different access policies for them. For example, if you want to allow only specific users access to the application marketing.safemarch.com and allow another group of users to access sales.safemarch.com, you can explicitly define each application. You can then configure policies referencing those applications individually. When configuring two or more application segments, ensure that there is no conflict in destination ports.
- [Example of conflicting application segments](#conflictExample)
Defining an Application
To [define an application](/zpa/about-application/onboard#tab1) within an application segment, you must enter one or more of the following:
- FQDN (e.g., marketing.safemarch.com)
[See image.](#FQDN)
- Local domain name (e.g., directory.safemarch.local)
[See image.](#localdomain)
- IP address (e.g., 192.0.2.0)
[See image.](#IPaddress)
- Wildcard domain (e.g., *.safemarch.com)
[See image.](#wildcard)
- Wildcard only (i.e., . and *.*)
[See image.](#wildcardonly)
Defining an application with a wildcard only requires approval from Zscaler, and it is not available for [application discovery](/zpa/about-application-discovery). Contact Zscaler Support for more information.
You can also [configure FQDNs or domain names and IP subnets](/zpa/about-application-discovery#config_appdiscovery) to enable application discovery.
For applications that users access using only the hostname (e.g., DFS), ensure that you [configure DNS search domains](/zpa/adding-dns-search-domains) so ZPA automatically adds the search domain to the hostname.
**[]**![Add Application Segment window with Domain or IP Address setting](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-fqdn_1.png)
[]![Add Application Segment window with Domain or IP Address setting](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-ipaddress_1.png)
[]![Add Application Segment window with Domain or IP Address setting](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-localdomainname_1.png)
[]![Add Application Segment window with a wildcard domain application](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-wildcard.png)
[]![Add Application Segment window with a wildcard only application](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-wildcard_0.png)
[]![Add Application Segment window with a wildcard only application](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-access/zpa-appaccess-wildcard2.png)
[If two or more application segments cover the same destination address, Zscaler Client Connector will attempt to match traffic to the more granular application segment. If there is no match in this application segment for the destination port, Zscaler Client Connector will bypass ZPA and send traffic direct. Consider the following configuration as an example of two conflicting application segments.]
- Application Segment 1
- FQDN: *.example.com
- Ports: TCP 1-65535 UDP 1-65535
- Application Segment 2
- FQDN: www.example.com
- Ports: TCP 8843
If a user navigates to www.example.com:80, the request resolves to the more specific FQDN in Application Segment 2, but fails at the closed port 80. Zscaler Client Connector does not forward traffic to Application Segment 1 and is dropped from ZPA. This can be resolved by ensuring ports are properly configured to allow access. For example:
- Application Segment 1
- FQDN: *.example.com
- Ports: TCP 1-65535 udp 1-65535
- Application Segment 2
- FQDN: www.example.com
- Ports: TCP 80