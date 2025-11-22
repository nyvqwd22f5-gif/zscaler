# About Application Discovery
Source: https://help.zscaler.com/unified/about-application-discovery
PDF: https://help.zscaler.com/pdf/com/en/1492181.pdf

You can enable application discovery so that when users request applications, they can be discovered using specific domain names and IP subnets. Configuring an application segment to allow for application discovery is useful when you want to learn about the different applications used in your organization and the users accessing them. For example, if you have a set of applications that end in the same domain name (e.g., safemarch.com), you can configure access policies that reference those applications as a set, rather than configuring policies for each application.
Application discovery works efficiently when the TCP and UDP port range that's specified for the domain or IP subnet is wide, and when the application policy allows access to a broad set of users.
When users request access to an application that matches the domain or IP subnet, the Zscaler Client Connector on the user's device redirects the request to the App Connectors that are configured for that application. Depending on whether the application is requested using a domain or IP address, the App Connectors either do a DNS lookup or check for IP reachability to process the request. If the request is successful, the user can access the application and see it listed in the Discovered Applications widget on the [Applications dashboard](/zpa/about-dashboard/appsDashboard) (Analytics > Reports > Private Applications > Applications).
![Discovered Applications Widget within Dashboard](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-discovery/zpa-discoveredappswidget.png)
The Discovered Applications widget displays the time the application was discovered if it occurred within the last 14 days. You can also click on the discovered application and view more details about the application request, such as the user who accessed it and which TCP or UDP ports were used.
An application is only discovered when a user requests access to it. There isn’t a service running in the background that constantly scans the network for new applications. After an application is discovered, you can define granular policies for your discovered applications to control access.
[]Configuring Application Discovery
To configure application discovery [within an application segment](/unified/configuring-defined-application-segments), you must enter one or more of the following:
- [FQDNs or Domain Names](#FDQN)
- [IP Subnets](#IPsubnet)
Applications defined with only a wildcard (i.e., *) are not available for application discovery.
You can only choose On Access health reporting for discovered applications. The App Connector reports the health of the application as soon as a user accesses the application and for up to 30 minutes after the user has completed using it. During this time frame, the current status of the application can be viewed on the [Health dashboard](/unified/viewing-health-dashboard). After 30 minutes, the application's health status changes to Unknown and is updated as soon as a user accesses the application again.
If you want to create a policy for a discovered application or configure specific settings for it (e.g., choosing Continuous health reporting), you can define the discovered application from the Discovered Application widget in the Applications dashboard. To learn more, see [Defining a Dynamically Discovered Application](/unified/defining-dynamically-discovered-application).
If you want to configure application discovery but have a few applications you don't want to make accessible through Private Applications, you can use the Bypass field to disable access to those applications. To learn more, see [Configuring Bypass Settings](/unified/configuring-bypass-settings).
[]You can enter domain names and fully qualified domain names (FQDN) in wildcard format:
- *.<FQDN or Domain Name>
- .<FQDN or Domain Name>
For example, if your applications end with the domain name safemarch.com, enter either:
- *.safemarch.com
- .safemarch.com
[See image.](#FQDNimg)
When a user requests an application that ends in that domain name (e.g., benefits.safemarch.com), the requested application is discovered because of your configuration and applies the policy you set.
If you are enabling application discovery for domains, consider matching the DNS Search Domains for your organization. This ensures that users accessing applications as non-FQDNs (i.e., host shortnames) have the domain suffixes appended, which causes an FQDN to be sent through for application discovery. To learn more, see [Adding DNS Search Domains](/unified/about-applications).
[]You can enter IP subnets using the 10.0.0.0/24 format.
[See image.](#IPsubnetimg)
When a user requests an application with the IP address 192.0.0.17, the application is discovered because of the IP subnet added above.
[]![Configuring application discovery using fully qualified domain names (FQDNs)](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-discovery/zpa-appdiscovery-fqdn.png)
[]![Configuring application discovery using IP subnets](/downloads/zpa/documentation-knowledgebase/applications/application-segments/about-application-discovery/zpa-appdiscovery-ipsubnet.png)