# Enforcing User-Based URL Policies on HTTPS Traffic
Source: https://help.zscaler.com/zia/enforcing-user-based-url-policies-https-traffic
PDF: https://help.zscaler.com/pdf/com/en/1400801.pdf

The Zscaler service can enforce user-based URL policies on HTTPS traffic in different ways.
Enable SSL Inspection
When SSL inspection is enabled, the Zscaler service decrypts SSL transactions and has full visibility of the HTTP traffic in the SSL tunnel (with URI and the Zscaler cookie representing the user), so it can enforce user policies. To learn more, see [About SSL Inspection](/zia/about-ssl-inspection).
If you use this option:
- The location must have authentication enabled.
- You should enable SSL inspection or the location or forward the location's traffic to Zscaler on port 9443.
Enable IP Surrogate
If enabling SSL interception is not a feasible option for your organization, you can use the [IP surrogate](/zia/what-surrogate-ip) feature, which enables the Zscaler service to map a user to a device IP address so it can apply the user's policies.
Kerberos Authentication
Zscaler supports authentication using Kerberos, an industry standard security protocol. Unlike the other supported authentication mechanisms, Kerberos does not use cookies for authentication. It is a ticket-based authentication protocol that is widely used to authenticate users to network services. The service can enforce granular user, group and department policies on proxied  HTTPS transactions, without having to decrypt the HTTPS transactions. To learn more, see [About Kerberos Authentication](/zia/about-kerberos-authentication).
Be aware of the following guidelines:
- The location must have authentication and Kerberos enabled.
- Use a PAC file to forward traffic to the Zscaler service. The service supports Kerberos authentication only for traffic forwarded in explicit mode. It does not support Kerberos for traffic forwarded in transparent mode; that is, traffic forwarded through a GRE or IPSec tunnel and the browser is not configured to use a PAC file to forward traffic. To learn more, see [Using the Default Zscaler Kerberos PAC File](/zia/using-default-zscaler-kerberos-pac-file).
- [Provision](/zia/choosing-provisioning-and-authentication-methods) users on the Zscaler service. Kerberos is an authentication mechanism. It is not a provisioning method, like SAML or LDAP synchronization. Users must be provisioned on the Zscaler service before they can use Kerberos for authentication.
- Ensure the configured DNS server can resolve the Zscaler service hostnames (Zscaler PAC servers, Central Authority (which hosts the Zscaler Key Distribution Center (KDC)), and ZIA Public Service Edges ). If this is not possible from the location, then your organization must conditionally forward Zscaler cloud domain resolution to the Zscaler DNS servers.