# ZPA Leading Practices Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/zpa-leading-practices-guide
PDF: https://help.zscaler.com/pdf/com/en/1452301.pdf

The Zscaler Private Access (ZPA) Leading Practices Guide provides a set of best practices for configuring and deploying ZPA in an organization's network environment.
ZPA is a cloud service that provides seamless Zero Trust access to private applications running on a public cloud or within the data center. Zero Trust has become a popular model for secure user access to applications and resources using an approach that focuses on granular user-to-app segmentation.
With ZPA, applications are never exposed to the internet, making them completely invisible to unauthorized users. The service enables applications to connect to users via inside-out connectivity versus extending the network to them.
To learn more about ZPA, see [What is Zscaler Private Access?](/zpa/what-zscaler-private-access)
This document shares ZPA leading practice guidelines for a successful Zero Trust implementation.
Deploying ZPA App Connectors
App Connectors provide a secure authenticated interface between a customer’s servers and the Zscaler cloud. The following sections provide best practices for deploying and managing App Connectors.
High Availability and Scalability
When planning high availability and scalability:
- To guarantee high availability, administrators must ensure that App Connector groups are scaled to provide N+1 redundancy. A single App Connector can handle up to 500 Mbps (total inbound and outbound) throughput. You must add more App Connectors if you need more throughput.
For example, if you require 1 Gbps throughput, configure at least three App Connectors. Using the correct number of App Connectors to meet throughput needs ensures good user quality of service.
- Zscaler frequently automatically updates App Connectors during the life cycle of the ZPA service. Customers should select off-hour time slots for upgrade operations to minimize the impact on the service. ZPA cloud sequentially upgrades members of an App Connectors group to reduce service interruptions during the upgrade window.
To help maximize user experience:
- Zscaler leverages Machine Learning (ML) to properly optimize user-to-application connectivity. The ZPA cloud automatically balances all available connectors by taking into account many factors, such as proximity to users, availability, scale, etc. To ensure correct calculations and user-app assignments for App Connector groups, the administrator configures the following groupings when setting up ZPA:
- Connectors in a connector group must share the same geographic location (latitude and longitude). This ensures that path selection works as intended. Zscaler recommends using location-based connector groups all the time. Not using location-based connector groups adversely impacts location-sensitive apps. That is, Active Directory (AD) domain controllers used for distributed file servers (DFSs) and other AD services where the user is associated to a local instance.
- To ensure users are connected to a location-appropriate app, place all connectors at a location in the same connector group. For example, all connectors at site A are in connector group A, and all connectors at site B are in connector group B, etc.
- Zscaler recommends defining a connector group for each logical domain of applications. For example, define a separate connector group for a single AWS virtual private cloud (VPC), a single data center, and a data center segment that is isolated within a security boundary, etc.
- Connectors must resolve Domain Name Service (DNS) for applications that users access by hostname and must reach those applications on the appropriate TCP/UDP ports to deliver user traffic. Zscaler recommends verifying that App Connectors use network conditions that assure quick DNS resolution for internal applications. Non-optimal DNS resolutions by App Connectors often contribute to delays and degraded user experience.
- Connectors must have Internet Control Message Protocol (ICMP) access to servers. This provides an optimal path selection for UDP-based apps and is mandatory. Though not mandatory, Zscaler also recommends ICMP access for TCP-based apps (to help with troubleshooting).
- In general, it is not necessary to dedicate App Connector groups to each application server. However, Zscaler recommends dedicating an App Connector group to an application server used for highly sensitive and business-critical applications.
- Due to multichannel communication and encryption, Zscaler does not recommend forwarding the App Connector's outbound traffic via a ZIA Public Service Edge or Private Service Edge.
You can measure user experience using Zscaler Digital Experience (ZDX). To learn more, see [What is Zscaler Digital Experience](/zdx/what-is-zscaler-digital-experience).
Segmentation
Generally, organizations can take one of two broad approaches to segmentation rollout. Most organizations find the second of the two approaches a better fit.
- Day 0 Trust: The fastest way to achieve Zero Trust is to define every known Fully Qualified Domain Name (FQDN), IP address in application segments, and user group access policies mappings, and then to create access to each application segment in advance of rollout.
This approach requires innate knowledge of all organizational applications and risks blocking business activity for any applications or users missed as a part of the initial rollout configuration. Such blocks create negative employee sentiment around Zero Trust. This approach is waterfall-based rather than Agile-based and requires a large effort before realizing any benefits. Zscaler recommends an organization only use the Day 0 Trust approach if it is confident that it can enumerate all applications and corresponding user access patterns.
- Discovery-Based Zero Trust: A slower but less disruptive way to roll out Zero Trust is to allow all authenticated users access to any private application (very similar to a traditional client-based VPN). The organization defines a pattern-based application segment with a private app space and a permissive allow policy that provides authenticated users access (i.e., allowing authenticated users to access *.companyprivateapps.com). Organizations using discovery-based Zero Trust can replace their VPN from day one without creating user experience or productivity friction.
ZPA then discovers and surfaces applications that users access, which allows further application segment and access policy creation over time that are split from the catch-all pattern-based application segment.
|  | Day 0 Zero Trust | Discovery-Based Zero Trust |
| --- | ---------------- | -------------------------- |
| Pros | Minimizes security risk. | Minimizes organizational impact. |
| Cons | Long time to value. | Long time to 100% completion. |
Pre-Segmentation Checklist for Discovery-Based Zero Trust
The following provides guidance on how to effectively implement discovery-based Zero Trust.
Discovery-based segmentation success requires good visibility into application traffic data. Zscaler recommends that the following prerequisites are met before you proceed on segmentation:
- App Connectors are deployed for the majority of your applications.
- Zscaler Client Connector is deployed to most managed endpoints.
- A substantial portion (more than half) of your user base actively leverages ZPA to access private applications.
Application Discovery is a good first-feature when adopting ZPA. Configuring an application segment to employ application discovery using wildcards helps uncover the applications in your organization that users access.
To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
For Application Discovery, Zscaler recommends:
- Using dynamic server discovery in server groups whenever possible. By default, administrators should always use dynamic server discovery (though there might be some cases where it makes sense to configure servers manually).
- Verifying that the initial ZPA deployment (within the first 60 days in production) includes 60% of entitled users.
In this mode, ZPA allows all users access to any DNS-based service or server as long as their authentication is in order (similar to client-based VPN access). Application Discovery allows the administrator to follow user key trends and access habits, which is used to build user segmentation and application segmentation.
Administrators should define an application discovery deadline. After the deadline, application discovery is turned off. Define discovered applications within appropriate Application Segments based on the discovery phase findings, and remove wildcards while building granular policies for the specifically named applications. Turning off application discovery enforces least-privilege access for all discovered applications and any newly requested applications.
Zscaler recommends managing access via the discovered applications rule for a limited period (i.e., 60 or 90 days) or until a percentage of users are deployed (i.e, 60%) for each ZPA user group during the deployment phase. To learn more, see [About Application Discovery](/zpa/about-application-discovery).
Business-Critical Applications
Zscaler recommends that you build clear policies listing which user groups can access business-critical applications (any application that is essential for business continuity) immediately. Do not rely on access rules that match the applications discovered via wildcard matches. Before deployment, define which departments and user groups can access critical applications, and make sure the user segmentation is clearly visible to the identity provider (IdP) and shared with the ZPA infrastructure. That is, via System for Cross-domain Identity Management (SCIM).
After defining the App Segment relative to these business-critical applications, Zscaler recommends specific access policies similar to:
| Policy Name | Segment Group/App Segment | IdP Attribute | Action |
| ----------- | ------------------------- | ------------- | ------ |
| Allowing Business-Critical Apps for Engineering | business-critical-app1 | memberOf = engineering | Allow |
| Blocking Business-Critical Apps | business-critical-app1 | Any | Block |
You can limit business-critical application access to specific departments or business units during the initial ZPA deployment. After you take care of Engineering business-critical apps, move on to Sales, Marketing, etc.
For example, if only UK payroll employees should access a critical application, administrators must ensure that these users have the appropriate group memberships on the IdP and that those groups are pushed towards ZPA. Then they must add a policy similar to the following:
| Policy Name | Segment Group/App Segment | IdP Attribute | Action |
| ----------- | ------------------------- | ------------- | ------ |
| Allowing Payroll UK | critical-app-payroll-UK | memberOf = Payroll AND memberOf = UK | Allow |
| Blocking Payroll UK | critical-app-payroll-UK | Any | Block |
Remember that rule order matters. ZPA evaluates policy rules using the most specific application segment and a top-down, first-match principle.
For business-critical applications:
- Add posture checks very early in the process to ensure that access to these apps is allowed from only compliant corporate-managed devices.
- Add Client Forwarding rules to ensure access to these apps goes through ZPA, even if the user is on the local corporate network. This provides administrators full visibility while implementing the key Zero Trust principles. Only approved users from approved devices get access to the app. Leverage a Private Service Edge for local access to specific apps through ZPA. Review the [Zscaler Private Service Edge](#zscaler_private_service_edge) section later in this document.
- The default Timeout Policy rule specifies that all users have to authenticate every 7 days for any application. You can change the Authentication Timeout for critical apps (i.e., one hour or one day) to make sure that frequent authentication requests add an additional layer of protection (to protect against a user leaving their laptop unlocked and unattended, for example).
To learn more, see [About Access Policy](/zpa/about-access-policy).
Regular Applications (Non-Critical)
You can manage non-critical business applications during the initial deployment phase by matching the wildcard application segment or application discovery rule. Zscaler recommends a regular analysis (on a weekly basis) of the discovered applications to meet the deadline for only allowing defined applications. Leverage ZPA ML suggestions using the [Recommended Application Segments](/zpa/about-recommended-application-segments) options.
To improve security posture considerations for all users and all applications:
- Implement more specific and granular access rules, since controlling who can access what is a key principle of Zero Trust.
- Zscaler recommends implementing regular (weekly) policies for all discovered applications that look at who has access to what. Use a mix of the following two approaches:
- Who can access what. Identify the targeted user community. That is, third parties, mergers and acquisitions (M&A) users, etc., and determine the apps to which they need access.
- What is accessed by whom. Identify sensitive apps and who needs access.
- App discovery and granular policy can co-exist. Administrators can create a generic allow policy for app discovery, and then gradually layer more specific allow policies to restrict access for specific users or apps.
- The following is an example of granular policies layered over generic app discovery that locks down a user community to specific apps:
| Policy Name | Segment Group/App Segment | IdP Attribute | Action |
| ----------- | ------------------------- | ------------- | ------ |
| Allowing contractors apps for contractors | contractor-app | memberOf = contractor | Allow |
| Blocking anything else for contractors | Any | memberOf = contractor | Block |
| Allowing anything else | Any | Any | Allow |
These policies allow contractors access to the contractor-app group of application segments. When a contractor attempts to access another app outside of that group, the explicit block rule displays a notification informing the user that the connection cannot go through.
After the applications are discovered, the ZPA interface allows administrators to easily add the discovered applications, define their respective servers, and update the App Segment information. Administrators can leverage Zscaler's ML features, when available, to use the provided insights relative to the discovered applications.
To learn more, see [About Access Policy](/zpa/about-access-policy).
Policy Definition Proposal for Initial Deployment
The following is an example of how Access Policy rules can work during initial deployment, one month after deployment, and two months after deployment. This example follows the internally set timeline to stop relying on the autodiscovery rules.
Day 1:
| Policy Name | Segment Group/App Segment | IdP Attribute | Action |
| ----------- | ------------------------- | ------------- | ------ |
| Allowing specific business-critical apps for Engineering | business-critical-app1 | memberOf = engineering | Allow |
| Blocking specific business-critical apps | business-critical-app1 | Any | Block |
| Allowing specific business-critical apps for Sales | business-critical-app2 | memberOf = sales | Allow |
| Blocking specific business-critical apps | business-critical-app2 | Any | Block |
| […] |  |  |  |
| Allowing anything else | Any | Any | Allow |
Dedicated rules allow authorized users access to critical apps, and a wildcard rule handles the rest of the traffic and discovers other applications.
Day 30:
| Policy Name | Segment Group/App Segment | IdP Attribute | Action |
| ----------- | ------------------------- | ------------- | ------ |
| Allowing specific business-critical apps for Engineering | business-critical-app1 | memberOf = engineering | Allow |
| Blocking specific business-critical apps | business-critical-app1 | Any | Block |
| Allowing specific business-critical apps for Sales | business-critical-app2 | memberOf = sales | Allow |
| Blocking specific business-critical apps | business-critical-app2 | Any | Block |
| […] |  |  |  |
| Allowing contractors apps for contractors | contractor-app | memberOf = contractor | Allow |
| Blocking anything else for contractors | Any | memberOf = contractor | Block |
| […] |  |  |  |
| Allowing anything else | Any | Any | Allow |
At 30 days, the schedule adds granular policies for non-business-critical apps to cover specific use cases. The last wildcard rule that handles the remaining traffic is still in effect.
Day 60:
Remove the last wildcard rule that handles remaining traffic. All applications are discovered and granular policies implemented.
Request new applications through an established internal process.
Unmanaged Laptops or Contractor, Vendor, or Third-Party Users
To improve the security posture for unmanaged laptops or contractor/vendor/third-party users, Zscaler recommends using browser-based access to a limited number of applications. Browser-based access lets you deploy ZPA on devices without installing the Zscaler Client Connector. Zscaler recommends limiting access to certain specific applications only.
It is possible to use Browser Access with Multiple IdP support (i.e., employees are authenticated via the default IdP, and contractors are authenticated via a dedicated IdP). Critical apps accessed by unmanaged devices should use Isolation access for an additional security layer.
To help administrators with ease of management, many customers map one policy to one app segment, which creates more access policies than necessary.
App Segment Groups
App segment groups apply policies to multiple applications. For example, if you have 100 app segments needing the same policy treatment, you can create a policy with a single target rather than 100.
To improve the user experience:
- Do not send DNS traffic through ZPA, because DNS traffic creates DNS resolution problems. Administrators should avoid using TCP port 53 in any app segments.
- To determine if any App Segment uses TCP port 53, go to Diagnostics and filter for `Application: Server Port = 53`.
- Zscaler recommends that admins review any app segments with a health check set to None or Continuous and confirm the reasons for the setting. App segments set to None are reachable by any App Connector servicing an associated server group. App segments set to Continuous can create high loads while continuously monitoring infrequently, since there is a limit of 6k targets (a combination of the IP address and port) per Connector Group.
- Zscaler strongly discourages defining app segments with large IP ranges (i.e., 10.0.0.0/8). Administrators should use wildcard domains such as *.internal.corp.com or *.corp.com. These wildcards offer broad connectivity options. If admins have no choice for a wildcard domain range, Zscaler recommends setting a time limit on the IP range. After the time limit is exceeded, rely on discovered applications and recommended application segments to properly define the used applications and then remove this wildcard IP range.
[]Zscaler Private Service Edge
You can deploy a ZPA Private Service Edge to facilitate ZPA connectivity for:
- Users who connect to the local corporate network and access applications on the internal network.
- Remote users who access regional internal applications.
- Implementing a business continuity plan.
Admins should turn on ZPA for local users using the Private Service Edge in the office or branch using the Forwarding Profile on the Zscaler Client Connector.
When administrators add the Private Service Edge to the ZPA Admin Portal, assign the Trusted Networks criteria to the Private Service Edge group so that users connected to the trusted network are redirected to the Private Service Edge instead of a Public Service Edge.
When a Private Service Edge is configured for both types of users rather than an IP address, the admin should use an FQDN that resolves from the internet to the Private Service Edge's public IP address, and from the internal network to the Private Service Edge’s private IP address.
To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
SIEM/SOC Integration
Considerations for administrator ease-of-management:
- Zscaler recommends using dedicated connector groups configured for log streaming, separate from connector groups serving user traffic. This allows user traffic bursts to avoid disrupting log streaming (since ZPA traffic has a higher priority than log streaming).
- Zscaler recommends that admins configure the Log Receiver Log Stream Policy Session setting to reauthBlock. This setting excludes log entries for authentication timeouts.
Any large system with a frequent reauthentication policy generates tens or hundreds of log entries as users refresh their SAML assertions. This data is temporarily interesting and can be viewed in the web UI, but is generally not useful for long-term research, trending, and forensics. The value is usually outweighed by the cost of sending and storing all the log entries.
To learn more, see [About the Log Streaming Service](/zpa/about-log-streaming-service).