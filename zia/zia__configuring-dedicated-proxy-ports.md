# Configuring Dedicated Proxy Ports
Source: https://help.zscaler.com/zia/configuring-dedicated-proxy-ports
PDF: https://help.zscaler.com/pdf/com/en/1399261.pdf

Your organization can subscribe to one or more ports, associate them with a [location](/zia/how-do-i-add-location), and then forward your remote user traffic to those ports. Forwarding remote users to your subscribed ports enables the Zscaler service to do the following:
- When [SSL Inspection](/zia/deploying-ssl-inspection) is enabled at the location, the service can apply all the SSL settings to remote user traffic, including the ability to exclude [URL categories](/zia/about-url-categories) and custom domains from decryption. Typically, the traffic of remote users is forwarded to port 9443 where the service does not apply the SSL exclusion settings. Additionally, this allows remote users to automatically authenticate using your SAML ID provider.
- Apply the location’s policies, instead of the default policy, to remote user traffic that cannot be authenticated, such as transactions that use unknown agents or non-HTTP protocols.
- Support FTP over HTTP for remote users, enabling the anti-virus engine of the service to scan content for viruses and spyware when a remote user’s browser connects to FTP sites and downloads files.
- Identify a remote user’s organization and display its logo on the login page. In addition, if SAML authentication is used, remote users are not prompted to enter their login name.
For enhanced security and to prevent unauthorized use of the subscribed ports, authentication must be enforced for the location associated with the ports. The service blocks traffic that it cannot authenticate, such as transactions that have an unknown user-agent or a non-HTTP protocol, if it is from an IP address that an authenticated user has not used.
When traffic from a known location arrives at a subscribed proxy port, the service applies the policies of the known location and not the location associated with the subscribed port.
Additionally, you can enable the service to map users to their external IP addresses as well so it can apply user-level policies to remote user traffic that it cannot authenticate.
Configuring Dedicated Proxy Ports
- Contact Zscaler Support in order to be subscribed to the proxy ports.
- After you receive the port numbers of the proxy ports from Zscaler, go to **Administration** > **Location Management**.
- [Add a new location](/zia/how-do-i-add-location) or [edit](/zia/how-do-i-edit-delete-or-duplicate-items-admin-portal) an existing location.
- In the **Add Location** or **Edit Location** window, under **Addressing**, choose the **Proxy Ports **you want to associate to the location.
- Under **Gateway Options**, select **Enforce Authentication**.
[See image.](#Image)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
After you configure the proxy ports on the ZIA Admin Portal, edit the [PAC file](/zia/what-pac-file) for your remote users in order to forward their traffic to the subscribed proxy ports.
[]![Edit Locations Page with Dedicated Proxy Ports Defined and Enforce Authentication Enabled](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/managing-locations/configuring-locations/configuring-dedicated-proxy-ports/zia-dedicatedproxyports-locations_0.png)