# Understanding Extranet Application Support
Source: https://help.zscaler.com/zia/understanding-extranet-application-support
PDF: https://help.zscaler.com/pdf/com/en/1508696.pdf

Zscaler Extranet Application Support leverages both ZIA and Zscaler Private Access (ZPA) to provide organizations with a secure way to access resources that are not secured with the Zscaler service. It also allows your business partners to access applications secured with the Zscaler service on your organization's network. This is typically accomplished by building site-to-site VPN tunnels that present several challenges including:
- Preventing lateral threat movement.
- Limiting access to authorized apps.
- Multiple solutions are needed for on-premises and remote employees.
- Organizations looking to access resources from multiple partners face additional organizational and financial difficulty.
Zscaler Extranet Application Support enables bidirectional resource access between your organization and a partner through secure [IPSec tunnels](/zia/understanding-ipsec-vpns) without requiring partners to install any additional hardware or software.
Extranets are created on the [Extranet page](/zia/about-extranet) in the ZIA Admin Portal and then assigned to [locations](/zia/about-locations). Each extranet has traffic selectors and DNS servers specified for it. A traffic selector is an IPSec traffic-steering rule for forwarding traffic between tunnels. Each traffic selector can contain multiple IP address ranges and uses the industry standard IKEv2 protocol. You can select specific traffic selectors and DNS servers when assigning an extranet to a location or use defaults that are designated during configuration.
ZIA facilitates the creation and management of extranets, and ZPA manages user access to extranet resources. Extranet resources can be designated in ZPA when configuring [server groups](/zpa/configuring-server-groups) and [application segments](/zpa/configuring-application-segments). You can [configure access policies](/zpa/configuring-access-policies) to manage extranet applications.
Traffic Flow for Extranet Application Support
The typical traffic flow for users accessing extranet resources is:
- A user with Zscaler Client Connector initiates their connection to an extranet application. User eligibility is checked by a ZPA Public Service Edge.
- After the user is authorized, the ZPA Public Service Edge sends a request to a ZIA Public Service Edge which forwards the request through an IPSec tunnel to the extranet partner's IPSec gateway.
- The request is forwarded to the designated DNS server and then sent through the right tunnel to the partner data center based on the designated traffic selector.
- After DNS resolution, the application payload is sent by the ZIA Public Service Edge back to the ZPA Public Service Edge.
- ZPA forwards the application payload to the Zscaler Client Connector user.
![Flow diagram for organization to partner resource access](/downloads/zia/traffic-forwarding/extranet/understanding-extranet-application-support/ZIA-understanding-extranet-organization-to-partner.png)
The typical traffic flow for partners accessing resources on your organization's network is:
- The partner user initiates a DNS resolution request over the IPSec tunnel.
- If the DNS request is valid, the ZIA Public Service Edge sends an ephemeral DNS response back to the partner user.
- The partner user's traffic is forwarded to the Zero Trust Exchange (ZTE) through the IPSec tunnel.
- The partner user's traffic is inspected by ZIA policies and validated by the ZPA access policy.
- The application is delivered to the partner from your organization's data center through the App Connector, ZTE, and IPSec tunnel.
![Flow diagram for partner to organization resource access](/downloads/zia/traffic-forwarding/extranet/understanding-extranet-application-support/diagram_ZIA_understanding-extranet_partner-org-flow.png)