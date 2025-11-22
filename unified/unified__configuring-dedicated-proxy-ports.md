# Configuring Dedicated Proxy Ports
Source: https://help.zscaler.com/unified/configuring-dedicated-proxy-ports
PDF: https://help.zscaler.com/pdf/com/en/1488301.pdf

Your organization can subscribe to one or more ports, associate them with a [location](/unified/configuring-locations), and then forward your remote user traffic to those ports. Forwarding remote users to your subscribed ports enables the Zscaler service to do the following:
- When [SSL Inspection](/unified/deploying-ssl-inspection) is enabled at the location, the service can apply all the SSL settings to remote user traffic, including the ability to exclude [URL categories](/unified/about-url-categories) and custom domains from decryption. Typically, the traffic of remote users is forwarded to port 9443 where the service does not apply the SSL exclusion settings. Additionally, this allows remote users to automatically authenticate using your SAML ID provider.
- Apply the location’s policies, instead of the default policy, to remote user traffic that cannot be authenticated, such as transactions that use unknown agents or non-HTTP protocols.
- Support FTP over HTTP for remote users, enabling the anti-virus engine of the service to scan content for viruses and spyware when a remote user’s browser connects to FTP sites and downloads files.
- Identify a remote user’s organization and display its logo on the login page. In addition, if SAML authentication is used, remote users are not prompted to enter their login name.
For enhanced security and to prevent unauthorized use of the subscribed ports, authentication must be enforced for the location associated with the ports. The service blocks traffic that it cannot authenticate, such as transactions that have an unknown user-agent or a non-HTTP protocol, if it is from an IP address that an authenticated user has not used.
When traffic from a known location arrives at a subscribed proxy port, the service applies the policies of the known location and not the location associated with the subscribed port.
Additionally, you can enable the service to map users to their external IP addresses as well so it can apply user-level policies to remote user traffic that it cannot authenticate.
Configuring Dedicated Proxy Ports
- Contact Zscaler Support in order to be subscribed to the proxy ports.
- After you receive the port numbers of the proxy ports from Zscaler, go to **Infrastructure **>** Internet & SaaS **>** Traffic Forwarding **>** Location Management**.
- [Add a new location](/unified/configuring-locations) or edit an existing location.
- In the **Add Location** or **Edit Location** window, under **Addressing**, choose the **Proxy Ports **you want to associate to the location.
- Under **Gateway Options**, select **Enforce Authentication**.
- Click **Save** and activate the change.
After you configure the proxy ports on the Admin Portal, edit the [PAC file](/unified/understanding-pac-files) for your remote users in order to forward their traffic to the subscribed proxy ports.