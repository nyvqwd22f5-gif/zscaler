# Deployment Scenarios for SSL Inspection
Source: https://help.zscaler.com/zia/deployment-scenarios-ssl-inspection
PDF: https://help.zscaler.com/pdf/com/en/1401941.pdf

Zscaler's SSL Inspection can be deployed in different scenarios. The following scenarios show how the service applies SSL Inspection based on traffic source and whether authentication or other features are enabled.
- [HTTPS Traffic from Known Locations](#Known-Locations)
- [HTTPS Traffic from Remote Users](#Road-Warriors)
Be aware of whether you protect HTTPS traffic by deploying SSL Inspection or by blocking specific HTTPS traffic, the ZIA Admin Portal must first identify the host in an HTTPS request through an explicit or transparent [proxy mode](/zia/what-proxy-mode).
The Zscaler service supports TLS 1.0, 1.1, and 1.2. When SSL Inspection is enabled, the service inspects all SSL/TLS sessions, regardless of version.
[]When an organization’s traffic is forwarded from a known location (an internet gateway configured in the Zscaler service portal), the Zscaler service applies [URL Filtering](/zia/about-url-filtering) and [Cloud App Control](/zia/about-cloud-app-control) policies as described in the following list, depending on whether user authentication is enabled.
- **Authentication Enabled**: Zscaler recommends this configuration because it enables the service to enforce granular URL and Cloud App Control policies at the user level.
- **Authentication Disabled**: The service applies location-based URL and Cloud App Control policies. It cannot apply any user or group policies because authentication is disabled. Ensure that the appropriate location is specified in the Location setting of the URL and Cloud App Control policies.
[]There are some extra steps needed when dealing with remote users, or users from an unknown location. Following are some options:
Zscaler Client Connector
The recommended option is to install and use Zscaler Client Connector on the client machines of your remote users.
Dedicated Proxy Port
If your organization has subscribed to a dedicated port and has getaway locations created using the dedicated port, your organization’s users might forward traffic to Zscaler on said port.
Whether SSL traffic should be inspected or not is something that can be defined by the location configuration. As the port is unique to the organization, it would be used as an identifier to apply your organization's SSL and authentication bypasses.
However, if the first transaction from a user is from an unregistered IP and is an HTTPS request, the identity of the user is unknown and to accept the traffic the transaction needs to be authenticated. This is to ensure Zscaler is not used as an open proxy by unauthorized users.
If the organization has Show Notifications enabled under Policy > SSL Inspection > Policy for SSL Inspection in the ZIA Admin Portal, then the transaction is intercepted and checked for a valid authentication cookie. If the cookie is not present, the user is redirected for authentication. After authentication, the traffic is accepted by Zscaler and appropriate policies applied.
The user would need to have appropriate root certificates installed on the user’s browsers to avoid certificate warnings.
If the organization has Show Notifications disabled, then the transaction is dropped. The user would need to access an HTTP page and provide a valid authentication cookie or go through the authentication process before accessing the HTTPS page.
TCP Port 9443
Users can connect to ZIA Public Service Edges on port 9443 and all HTTPS connections are subject to SSL Inspection. The drawback of this method is that the capability to bypass certain traffic based on URLs and URL categories from SSL scanning and authentication is lost.
Users should also have the appropriate SSL certificate installed. If it is not installed and a user forwards traffic to port 9443, the browser displays certificate warnings.
TCP Port 80/443/9400/9480
Remote users might forward traffic to Zscaler on ports 80/443/9400 and 9480. However, there are a few issues to be aware of:
- SSL traffic is not intercepted and policies are not implemented on SSL traffic.
- If the first transaction from an unregistered IP address and is on HTTPS, the transaction is blocked. The user would need to access an HTTP page and provide a valid authentication cookie or go through the authentication process before accessing the HTTPS page.
- SSL and authentication bypass is not applied.
TCP Port 8800
Remote users might use port 8800 to forward traffic to Zscaler, and ZIA Public Service Edges attempt to authenticate the user using the Kerberos method of authentication. The organization might choose to inspect HTTPS traffic by enabling Enable SSL Inspection for Remote Users with Kerberos under Policy > SSL Inspection.