# Kerberos Authentication Deployment Guidelines
Source: https://help.zscaler.com/zia/kerberos-authentication-deployment-guidelines
PDF: https://help.zscaler.com/pdf/com/en/1399561.pdf

Before you [deploy Kerberos](/zia/how-do-i-deploy-kerberos), review the following guidelines:
- To enforce Kerberos authentication, your organization must send its traffic to port 80, 443, or 8800.
- For known locations, the Zscaler service enforces Kerberos on all explicitly forwarded traffic it receives on port 8800, unless the location does not have authentication enabled. The SSL inspection settings and other settings are inherited from the location. If Kerberos isn't enabled for a location, but you would like some users from that location to use Kerberos, you can send their traffic to port 8800, as well. Ensure that remote users send their traffic to port 8800. The service doesn't perform SSL inspection on this traffic.
- Enabling Kerberos on a location enforces Kerberos authentication on all traffic that is explicitly forwarded to the service from that location and its dedicated proxy ports. Therefore, when Kerberos is enabled on a location, you can forward traffic to port 80 or 443, and the service still enforces Kerberos authentication.
- Authentication must be enabled on a location that deploys Kerberos authentication for some or all its users.
To learn more, see the [Kerberos requirements](/zia/about-kerberos-authentication#kerberos-requirements) for tasks you must complete before deploying Kerberos.
The service only supports Kerberos authentication for traffic that is forwarded to the service in explicit mode. It does not support Kerberos authentication for traffic forwarded to the service in transparent mode (i.e., traffic forwarded through a GRE or IPSec tunnel, and the browser isn't configured to use a PAC file to forward traffic), regardless of the location settings or destination port.
[]Kerberos Deployment Options
Kerberos can be used by itself or combined with other authentication mechanisms, depending on your business requirements. Following are some typical deployment scenarios and guidelines:
Using Kerberos for All Users in a Location
You can enable Kerberos for a location, requiring all its users to authenticate via Kerberos. To deploy Kerberos for all users in a location:
- Provision all users on the Zscaler service.
- Configure Kerberos and enable it for the location. See [Deploying Kerberos](/zia/how-do-i-deploy-kerberos). When you enable Kerberos on a location, the service automatically uses Kerberos to authenticate users from that location.
- Distribute the default Kerberos PAC file URL to all users in the location. The default Kerberos PAC file forwards traffic to port 8800, the default Kerberos port on ZIA Public Service Edges. Because Kerberos is enabled for the location, there is no need to send the traffic to port 8800. However, if you want to send the traffic to port 80 instead of port 8800, due to firewall constraints, copy the default Kerberos PAC file and replace the variables `${GATEWAY_HOST}:8800` with `${GATEWAY_HOST}:80` and `${SECONDARY_GATEWAY_HOST}:8800` with `${SECONDARY_GATEWAY_HOST}:80`. Or, if your organization subscribes to a dedicated proxy port, specify that port instead. To learn more, see [Using the Default Zscaler Kerberos PAC File](/zia/how-do-i-use-zscaler-kerberos-default-pac-file).
Using Kerberos for Some Users in a Location
If you want some users in a location to authenticate via Kerberos because the location already has a primary authentication mechanism (e.g, LDAP or SAML), you can distribute the default Kerberos PAC file URL to those users. To deploy Kerberos authentication for specific users, do the following:
- Provision the users who use Kerberos for authentication on the Zscaler service.
- Configure Kerberos, but don't enable it for the location. To learn more, see [Deploying Kerberos](/zia/how-do-i-deploy-kerberos).
- Distribute the default Kerberos PAC file URL to the appropriate users. To learn more, see [Using the Default Zscaler Kerberos PAC File](/zia/how-do-i-use-zscaler-kerberos-default-pac-file).
Using Kerberos for Remote Users
To use Kerberos authentication for remote users, ensure the remote users have the following requirements:
- Remote users must use DirectAccess to connect to the KDC Proxy. DirectAccess is only supported on Windows 7 Enterprise, Windows 7 Ultimate, and Windows 8 Enterprise editions. Windows 7 Professional and Windows 8 Professional don't support DirectAccess. There are no native clients for OS X and Linux. There are no native clients for OS X and Linux. Remote user access without DirectAcess might work for other VPN solutions.
- Edit the default Kerberos PAC file and distribute its URL to the remote users. Copy the default Kerberos PAC file and add a bypass for the KDC Proxy hostname. Retain the default destination port, port 8800, to ensure that remote user traffic is sent to that port on the ZIA Public Service Edge. If you want to send remote user traffic to a dedicated proxy port to enable the service to apply customized SSL settings:
- In the PAC file, specify the dedicated proxy port as the destination port.
- Ensure that Kerberos is enabled on the location associated with the dedicated proxy port.