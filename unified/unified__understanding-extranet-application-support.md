# Understanding Extranet Application Support
Source: https://help.zscaler.com/unified/understanding-extranet-application-support
PDF: https://help.zscaler.com/pdf/com/en/1518651.pdf

Zscaler Extranet Application Support leverages both Internet & SaaS and Private Applications to provide organizations with a secure way to access resources that are not secured with the Zscaler service. Some organizations need to access resources from partners or offshore development centers that are not using the Zscaler service. This is typically accomplished by building site-to-site VPN tunnels that present several challenges including:
- Preventing lateral threat movement.
- Limiting access to authorized apps.
- Connectivity challenges and multiple solutions needed for on-premises and remote employees.
- Organizations looking to access resources from multiple partners face additional organizational and financial difficulty.
Zscaler Extranet Application Support enables your organization to access partner resources through secure [IPSec tunnels](/unified/understanding-ipsec-vpns) without requiring partners to install any hardware or software.
Extranets are created on the [Extranet page](/unified/about-extranet) in the Admin Portal and then assigned to [locations](/unified/about-locations). Each extranet has traffic selectors and DNS servers specified for it. A traffic selector is an IPSec traffic-steering rule for forwarding traffic between tunnels. Each traffic selector can contain multiple IP address ranges and uses the industry standard IKEv2 protocol. You can select specific traffic selectors and DNS servers when assigning an extranet to a location or use defaults that are designated during configuration.
Internet & SaaS facilitates the creation and management of extranets, and Private Applications manages user access to extranet resources. Extranet resources can be designated in Private Applications when configuring [server groups](/unified/configuring-server-groups) and [application segments](/unified/configuring-defined-application-segments). You can [configure access policies](/unified/configuring-access-policies) to manage extranet applications.
Traffic Flow for Extranet Application Support
The typical traffic flow for users accessing extranet resources is:
- A user with Zscaler Client Connector initiates their connection to an extranet application. User eligibility is checked by a Private Applications Public Service Edge.
- After the user's eligibility is confirmed, the Private Applications Public Service Edge sends a request to an Internet & SaaS Public Service Edge which forwards the request through an IPSec tunnel to the extranet partner's IPSec gateway.
- The request is forwarded to the designated DNS server and then sent through the right tunnel to the partner data center based on the designated Traffic Selector.
- After DNS resolution, the application payload is sent by the Internet & SaaS Public Service Edge back to the Private Applications Public Service Edge.
- Private Applications forwards the application payload to the Zscaler Client Connector user.
![Extranet Traffic Flow](/downloads/zia/traffic-forwarding/extranet/understanding-extranet-application-support/ZIA_Diagram_Extranet_Understanding_App-Support_flow.svg)