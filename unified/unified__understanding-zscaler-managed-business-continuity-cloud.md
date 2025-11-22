# Understanding Zscaler-Managed Business Continuity Cloud
Source: https://help.zscaler.com/unified/understanding-zscaler-managed-business-continuity-cloud
PDF: https://help.zscaler.com/pdf/com/en/1531055.pdf

This feature is in limited availability. To learn more, contact your Zscaler Account team.
Critical outages of cloud services, such as Zscaler data centers, might lead to interruption of business activities, resulting in financial and productivity issues, and damage to the company’s reputation. To maintain traffic flow during outages, organizations are focusing on business continuity planning (BCP) to ensure critical services are available at all times.
To support business continuity planning for organizations, Zscaler offers a secure service, Business Continuity Cloud, that allows users to access the internet and private applications when the Internet & SaaS and Private Applications clouds are unreachable. The Business Continuity Cloud is a fully isolated and dedicated private cloud that is hosted in a third-party data center to ensure cyber and data protection during critical failures. This private cloud maintains your organization's entire traffic flow, adhering to the configured Zscaler policies, eliminating the need to maintain on-premises business continuity infrastructure.
This service has two components: a private data plane and a private control plane. The private data plane leverages the functionalities of Internet & SaaS Private Service Edges and Private Applications Private Service Edges. The private control plane leverages the Zero Trust Exchange (ZTE) components, such as Private Policy Cache and Private PAC Server for Internet & SaaS, and Private Cloud Controllers for Private Applications.
Failure scenarios of Zscaler cloud can be classified as follows:
- **Blackouts**: Blackout scenarios include data center outages or severe connectivity issues in which organizations cannot forward traffic to the impacted Zscaler data center.
- **Brownouts**: Brownout scenarios include unexpected technical issues or internet failure that could be caused by events such as physical damage to the internet cable.
-
**Critical Failure**: Critical failure scenarios include global Zscaler cloud outages or other issues with Internet & SaaS and Private Applications' clouds. Though the probability of a critical failure is low, it could severely affect organizational operations.
The Business Continuity Cloud service mainly helps organizations stay connected and protected during critical failure scenarios, where public clouds are unreachable.
To subscribe to the Business Continuity Cloud service, contact your Zscaler Sales Representative.
The following sections provide more details on the Internet & SaaS and the Private Applications business continuity mode:
- [Internet & SaaS Business Continuity Cloud](#internet-saas-bcc)
- [Private Applications Business Continuity Cloud](#private-applications-bcc)
[]The Internet & SaaS Business Continuity Cloud leverages the functions of the Internet & SaaS Private Service Edges and extends its capabilities by adding a Private Policy Cache service and Private PAC Server during business continuity mode.
- **Internet & SaaS Private Service Edge**: Internet & SaaS Private Service Edges provides the functionality of Internet & SaaS Public Service Edge. The Business Continuity Cloud service provides dedicated private cloud infrastructure to ensure consistent security policies are applied to an organization’s traffic during critical events.
- **Private Policy Cache**: The Private Policy Cache stores full policy configurations for the organization and updates them regularly, ensuring they are accessible during critical outages. It is integrated into the existing Internet & SaaS Private Service Edges to apply the last known good policies to the traffic flow during failover to the private cloud.
- **Private PAC Server**: The Private PAC Server helps clients retrieve PAC files and reroute traffic to back up private cloud infrastructure during failures.
The following prerequisites and limitations apply to the business continuity mode:
- [Prerequisites](#internet-saas-pre)
- [Limitations](#internet-saas-limits)
[]The Internet & SaaS Business Continuity Cloud only supports Zscaler Client Connector Z-Tunnel 1.0, PAC files and GRE tunnel connectivity. The following limits apply:
-
Only GRE tunnels with [cookie authentication](/unified/about-zscaler-cookies) disabled continue to work seamlessly in business continuity mode. No additional configuration is required in the Admin Portal.
If you have [cookie authentication](/unified/about-zscaler-cookies) enabled, you need to configure GRE tunnels with a separate source IP address, and have cookie authentication disabled for Business Continuity Cloud for each user location.
- IPSec tunnels are not supported in business continuity mode.
- Zscaler Tunnel (Z-Tunnel) 2.0 is not supported in business continuity mode.
- Configuration limitations:
- New user authentication or new user enrollment is not supported in business continuity mode.
- Any recent organizational policy updates might not take immediate effect. Only the last known good policy configurations apply to outgoing traffic in business continuity mode.
- After a public cloud software upgrade, the Business Continuity Cloud upgrade is intentionally delayed to provide additional isolation against upgrade-related issues. This results in a delayed update of any new organization policies or configurations for fault isolation reasons.
[]Ensure that the following prerequisites are met for Internet & SaaS business continuity:
- The end users' machines are running Zscaler Client Connector versions 4.6 and later for Windows.
- Zscaler disaster recovery is enabled in the Admin Portal for end users.
- All security policies are configured before entering business continuity.
- The GRE tunnel locations are configured with authentication disabled to support business continuity.
- (optional) A customer-hosted PAC server is available for hosting the Internet & SaaS DR PAC file to redirect traffic to the Internet & SaaS Private Service Edge.
[]The Private Applications Business Continuity Cloud leverages the functions of the Private Applications Private Service Edges, App Connectors, and Private Cloud Controller to ensure continued access to private applications in business continuity mode. To learn more, contact your Zscaler Account team.
For prerequisites and limitations, see [Understanding Business Continuity](/unified/understanding-business-continuity).
- **Private Applications Private Cloud**: Private Applications Private Clouds are the logical grouping of Private Cloud Controller groups, App Connector groups, Private Applications Private Service Edge groups, and log receivers. It helps with uninterrupted access to applications without any manual intervention in business continuity mode. To learn more, see [About Private Clouds](/unified/about-private-clouds).
- **Private Applications Private Service Edge**: Private Applications Private Service Edges and App Connectors leverage private clouds and Private Cloud Controller when the Private Applications cloud is unavailable. The Private Applications Private Service Edges contacts the Private Cloud Controller associated with the private cloud for the control channel, configuration updates, and logging.
- **Private Cloud Controller**: Private Cloud Controller work with the Private Applications Private Service Edges to keep services running when the Private Applications cloud is unavailable. In business continuity mode, the Private Cloud Controller helps download and distribute customer configurations and redirect traffic to the private cloud. To learn more, see [About Private Cloud Controllers](/unified/about-private-cloud-controllers).