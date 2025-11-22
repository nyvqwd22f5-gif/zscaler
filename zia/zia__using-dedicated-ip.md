# Using Dedicated IP
Source: https://help.zscaler.com/zia/using-dedicated-ip
PDF: https://help.zscaler.com/pdf/com/en/1468216.pdf

When organizations forward their network traffic to the Zscaler cloud, the IP address of the client devices is automatically translated (via Network Address Translation) into a Zscaler-managed IP address from a common pool due to the proxy architecture of Zscaler, before the traffic is forwarded to the destination. Although masking client devices' IP addresses behind Zscaler's IP addresses serves as one of the core tenets of Zero Trust Network Access (ZTNA), organizations in the enterprise landscape sometimes need to use their own IP addresses to authenticate and access certain resources.
For example, third-party SaaS applications and domains might use the source IP address of the traffic they receive as a filtering mechanism and restrict access based on the source IP address of the traffic. These applications require the traffic to originate from a preregistered unique IP address, which usually belongs to the organization. These applications deny access to user traffic that originates from other IP addresses within or outside the organization, such as the Zscaler data center's IP address that is not preregistered with the service.
In some cases, applications allow access only if the traffic originates from specific countries where Zscaler's data center might not be present. For example, some government sites hosted in a country might be accessible only from within that country, and if Zscaler does not have a data center within that country, the users of that country would not have access to those government sites.
In such scenarios, organizations might have to risk bypassing some traffic from the Zscaler service, creating a security gap. To overcome this issue, organizations can use GeoIP [forwarding policies](/zia/about-forwarding-policies) to forward traffic using IP addresses mapped to the location of the originating request.
In scenarios where the IP address of the source must be fixed and unique for an organization, you can use dedicated IP addresses. These dedicated source IP addresses can either be self-managed or provisioned by Zscaler for your organization.
Zscaler recommends using dedicated IP addresses only for applications that mandate IP-based authentication.
Zscaler offers the following solutions for organizations to use dedicated source IP addresses:
- [Zscaler-Managed Dedicated IP](/zia/understanding-zscaler-managed-dedicated-ip)
- [Customer-Managed Dedicated IP (or Source IP Anchoring)](/zia/understanding-source-ip-anchoring)
- [Private Service Edge](/zia/understanding-private-service-edge)
- [Virtual Service Edge](/zia/about-virtual-service-edges)