# Application Discovery Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/application-discovery-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1420091.pdf

This guide describes the benefits of using Application Discovery and the steps necessary for configuring Zscaler Private Access (ZPA) to add Application Discovery to your security posture.
Two ways to access applications are through an explicit application definition or application discovery. When users request applications, Application Discovery lets ZPA discover them using specific domain names and IP subnets.
Configuring an application segment to allow for application discovery is useful when you want to learn about the applications used in your organization and the users accessing them. Application discovery works efficiently when the TCP and UDP port range specified for the domain or IP subnet is wide, and when the application policy allows access to a broad set of users. After discovering an application, you can define granular policies for your discovered applications to control access.
To learn more, see [About Application Discovery](/zpa/about-application-discovery).
Value of Deploying Application Discovery
Enabling Application Discovery for ZPA provides the following benefits:
- Helps to scope out the network and frequently accessed applications to implement least-privilege access policies early in the ZPA deployment stage.
- Ascertains if there are hidden applications so that you can restrict access if necessary.
Deployment Phase
The deployment phase initially sets up and integrates ZPA solutions into an existing network infrastructure. During the deployment phase, you configure Application Discovery to meet the needs of your infrastructure. The following sections discuss steps to deploy Application Discovery.
Prerequisites
For Application Discovery deployment, ZPA discovers an application only when a user requests access to it.
Deployment Steps
The following steps explain how to deploy Application Discovery:
- [Create an application segment](/zpa/configuring-application-segments) with a wider domain or subnet:
- Fully Qualified Domain Names (FQDNs) or Domain Names: Enter FQDNs and domain names in wildcard format (e.g., `*.``<FQDN or Domain Name>` or `.``<FQDN or Domain Name>`).
- IP Subnets: Enter IP subnets using the Classless Inter-Domain Routing (CIDR) notation (e.g., 10.0.0.0/24).
- Define wider TCP/UDP port ranges for applications excluding TCP and UDP 53 (DNS).
- (Optional) [Add DNS search domains](/zpa/about-applications/dnsDomains).
- [Configure access policies](/zpa/configuring-access-policies) that reference applications as a set rather than configuring policies for each application.
- Define the discovered applications from the [Discovered Application widget in the Applications dashboard](/zpa/defining-dynamically-discovered-application).
- Use the [bypass settings](/zpa/configuring-bypass-settings) to bypass selected applications from ZPA.
- After applications are discovered, define granular application segments and access policies to restrict access on a least-privilege access principle.
Considerations
Review the following considerations:
- Applications defined with only a wildcard, i.e., an asterisk (*), are not available for application discovery.
- On Access health reporting is available for only discovered applications.
- App Connector reports the application's health as soon as a user accesses it and for up to 30 minutes after the user has completed using it.
- ZPA does not apply the ports specified in the app segments that contain IP subnets or wildcards towards app segments that contain more specific IPs or FQDNs. You must specify the ports in the app segment that contain the IPs or FQDNs.
- When defining a new application segment, Zscaler recommends taking note of the following interaction between a wildcard domain and a specific host domain, where wildcard no longer means wildcard:
- You have an app segment defined by a wildcard (*.exapp.company.com).
- You add the app segment to an access policy.
- You create a new app segment (file.exapp.company.com).
The access policy does not cover the app segment in the third bullet. By defining the app segment (file.exapp.company.com) separately, you must add a new access policy because the application matches the specific app segment. ZPA always matches an application to the most specific app segment, even if that application could potentially match a wildcard app segment. For policy, ZPA evaluates the policy with the most specific app segment.
- For applications that users access using only the hostname; e.g., distributed file system (DFS), ensure that you configure [DNS search domains](/zpa/about-applications/dnsDomains) so that ZPA automatically adds the search domain to the hostname. This ensures that ZPA users accessing applications as non-FQDNs (i.e., host short names) have the domain suffixes appended, which causes an FQDN to be sent through for application discovery.
- If your identity provider (IdP) is defined as an application within an application segment, the [Authentication Timeout](/zpa/about-timeout-policy) for the IdP application must be set to Never. If an IdP domain overlaps with a domain configured for application discovery, you must bypass the IdP domain in ZPA to avoid user reauthentication failure.
- After 14 days, discovered application data is no longer listed in the [User Activity Diagnostics](/zpa/about-diagnostics/txnUsersDiagnostics).
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune Application Discovery in ZPA during operations to meet your infrastructure needs.
Prerequisites
For Application Discovery operation, complete the following prerequisites:
- Prepare an up-to-date list of domains, IP subnets, and ports currently enabled for application discovery.
- Define a deadline after which application discovery is turned off to enforce the least-privilege access principle for all discovered applications. Request new applications through an established internal process.
Common Troubleshooting Items
The following list describes common issues related to Application Discovery operation:
- Application is not being discovered or accessed:
- If not discovered, check if the following preconditions are met:
- The application was accessed within the last 14 days.
- The application discovery segment covers the ports used by the application in question.
- The specified application discovery criteria cover the destination URL or IP address.
- If discovered but not accessed, check for the following:
- Is there a more specific application segment that overrides policies set for the application discovery segment.
- Is there an [access policy](/zpa/configuring-access-policies) for the application segment that prevents the user from accessing the application.
- Does the [User Activity Diagnostics](/zpa/about-user-activity-diagnostics) and the [bypass settings](/zpa/configuring-bypass-settings) of the application segment show the application is forwarded to ZPA.
- Zscaler Client Connector requests reauthentication, but the reauthentication fails: If your identity provider (IdP) is defined as an application within an application segment, the Authentication Timeout for the IdP application must be set to Never. If an IdP domain overlaps with a domain configured for application discovery, you must bypass the IdP domain in ZPA to avoid user reauthentication failure.
Deployment Checklist
Zscaler recommends downloading the [Application Discovery Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/application-discovery-deployment-and-operations-guide/Application-Discovery-Deployment-Operations-Checklist.pdf) to help plan and implement Application Discovery: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/application-discovery-deployment-and-operations-guide/Application-Discovery-Deployment-Operations-Checklist.pdf)
Additional Information
For more application discovery information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](http://community.zscaler.com/).