# Understanding Health Reporting
Source: https://help.zscaler.com/zpa/understanding-health-reporting
PDF: https://help.zscaler.com/pdf/com/en/1483861.pdf

When [configuring an application segment](/zpa/about-application/onboard#tab1), you can specify if the App Connector will check the health of the defined applications and report on it.
For Extranet, the health score represents the health of an IPSec connection between the extranet resource's (partner) data center and the Zscaler cloud. It is a cumulative score of all the components and functions for that connection. You can have multiple connections between an extranet resource and the Zscaler cloud. Each extranet resource can have multiple locations, and each location can have multiple tunnels to the Zscaler cloud. The health of the application itself is not evaluated.
If you enable Health Reporting, the App Connector checks the application reachability to the server on each TCP and UDP port specified in the application segment configuration. Depending on how the application is defined, the App Connector checks the reachability in different ways:
- FQDN: The App Connector checks reachability to all the IP addresses that are returned as part of the DNS resolution.
- IP address: The App Connector only checks reachability to the IP address.
- TCP access: The App Connector performs a check using TCP 3-way handshake to determine application reachability.
- UDP access: The App Connector first performs ICMP-based checks to determine application reachability. It follows with a TCP-based check if the ICMP check is unsuccessful.
For example, there is an application segment with the application jira.lanukcorp.com that has the following settings:
- IP address: 10.1.1.1
- TCP ports: 80
- UDP ports: 3389
If jira.lanukcorp.com resolves to 10.1.2.1 and 10.1.2.2, the App Connectors for this application perform reachability checks to 10.1.2.1:80, 10.1.2.2:80, 10.1.1.1:80, 10.1.2.1:3389, 10.1.2.2:3389, and 10.1.1.1:3389.
If the application reachability check is successful, the App Connector reports the application’s health status as Up to the ZPA Central Authority (CA). ZPA then uses this information to decide if an App Connector should be used for accessing a requested application. ZPA can randomly select any App Connector in an App Connector group if at least one App Connector in the group has successfully reported reachability to the requested application.
When the App Connector identifies the health status of the application, it reports this information to the ZPA Central Authority (CA). For Health Reporting, you can choose how often the App Connector reports the health status of an application.
App Connectors limit the number of checks to 20 checks per second. If the App Connector has to perform 20 checks, these are done in one second. However if the App Connector has to perform 6,000 checks, it takes 300 seconds to perform these checks. Zscaler recommends configuring applications so that an App Connector does not have to perform more than 6,000 checks. To learn more, see [Monitoring App Connector Performance](/zpa/monitoring-connector-performance#appreach).
The settings for Health Reporting are as follows:
- [Continuous](#continuous)
- [On Access](#onaccess)
- [None](#none)
If Multimatch is enabled, Health Reporting on an application segment can only be set to On Access or None. To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
To learn more about the health status of an application, see [About the Health Dashboard](/zpa/about-dashboard/health).
[]The App Connector continuously performs checks and reports the reachability status of the application. You cannot configure continuous health reporting for:
- Application segments configured with more than 10 ports.
- Applications segments configured for [application discovery](/zpa/about-application-discovery) (i.e., applications with domain names in wildcard format or IP subnets, such as *.safemarch.com or 10.122.0.0/16).
[]The App Connector attempts to report the reachability status of the application when a user attempts to access the application. The App Connector continues to check and report the application’s reachability status for up to 30 minutes after the last user accesses it. During this limited time frame, you can view the health status of the application on the [Health dashboard](/zpa/about-dashboard/health).
When the App Connector reports the health of the application, it displays the health status as Up or Down depending on whether the application is accessible or not. When the App Connector stops reporting the health of the application, its health status is displayed as Unknown with a question mark icon.
![Health Check Unknown icon](/downloads/zpa/documentation-knowledgebase/applications/applications/about-health-check-and-reporting/ttwz9yddh65ktgmjjb4d_7oov6xnbvbpgruynpsft90pm3ibsyuci-boxoxuulxnmh7b56nr3j0z1xzrni-kenfmcmfrlkj_ooysyi2m0iseskmgwe03azkhjjh7fhfx5e2xeaso.png)
If an application has client hostname validation enabled to facilitate client-to-client remote assistance, then the application is not shown on the Health Dashboard. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
[]The App Connector does not check and report reachability to the application. ZPA assumes the application is always reachable through the App Connector, and it can select this App Connector to provide access to the requested application.
Use this setting for one of the following reasons:
- You want to reduce the number of checks performed by an App Connector.
- An application is expected to always be reachable.
- You are connecting to an extranet application.