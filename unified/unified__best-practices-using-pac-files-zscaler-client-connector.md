# Best Practices for Using PAC Files with Zscaler Client Connector
Source: https://help.zscaler.com/unified/best-practices-using-pac-files-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1495746.pdf

To prevent outages, Zscaler strongly recommends that you roll out all PAC file changes to a small set of users before deploying changes to all users.
A PAC file is a text file used for directing traffic to a proxy server. A PAC file can also be used to bypass traffic or direct traffic to a specific proxy (i.e., traffic splitting). To learn more about PAC files, see [Understanding PAC Files](/unified/understanding-pac-files).
Zscaler Client Connector uses PAC files in the [Forwarding Profile](/unified/configuring-forwarding-profiles-zscaler-client-connector) and in the [App Profile](/unified/configuring-zscaler-client-connector-app-profiles). The Forwarding Profile PAC file is used to direct system, browser, and application traffic to Zscaler Client Connector. When Zscaler Client Connector receives traffic, the App Profile is used to direct that traffic to the Zscaler cloud. Zscaler Client Connector directs traffic to the closest data center according to the App Profile PAC file by changing the proxy return statement to the IP address of the geographically closest data center.
If the primary and secondary data center from the PAC file both fail, Zscaler Client Connector will attempt to connect to gateway.<cloudname>.net, unless the **Fallback to gateway domain** setting is disabled.
This article provides best practices for using PAC files with Zscaler Client Connector.
- If you experience slowness when using Zscaler Client Connector:
- Check if the data center has any issues.
- Run traceroute to check for possible ISP issues.
- From the App Profile PAC file, check for and remove the functions **dnsResolve()**, **isResolvable()**,** **and **isInNet()**.
- Check if any network firewalls or network scanning is interfering with traffic.
- Check for possible server issues by browsing to a website without a proxy, with the PAC file only, and with Zscaler Client Connector.
- Check if another process, such as GPO, is also applying proxy settings. This can conflict with Zscaler Client Connector and cause performance issues on the device.
- Bypass domains by using the **shExpMatch** function on the **host **variable. For example:
Bypassing a domain:
if (shExpMatch(host, "safemarch.com")) return "DIRECT";
Bypassing a domain and all of its subdomains:
if (shExpMatch(host, "safemarch.com") || shExpMatch(host, "*.safemarch.com")) return "DIRECT";
- Apply bypasses in the Admin Portal by** **configuring bypasses in the SSL bypass list and in the Authentication Bypass list. If you have traffic that you do not want to reach the Zscaler cloud, and it must be bypassed on the client itself, you must configure bypasses in the PAC files used for Zscaler Client Connector.
- If you are using Zscaler Client Connector version 1.4 or later, you can configure multiple Internet & SaaS Public Service Edge gateway destinations based on the destination the user is trying to access. For example, if you want traffic for internal hosts to go to a specific data center, but all other traffic to go to the geographically closest data center, define two return statements with the respective Internet & SaaS Public Service Edge gateway IP addresses. For example:
var InternalHosts = /(remote\.mydomain\.com|mail\.mydomain\.com)/;
if (InternalHosts.test(host))
{
return "PROXY 104.129.192.43:80; PROXY 104.129.198.34:80; DIRECT";
}
return "PROXY ${GATEWAY}; PROXY ${SECONDARY_GATEWAY}:9400; DIRECT";
}
For optimal performance, do not define more than two return statements that contain Zscaler Client Connector gateway IP addresses.
Following are the best practices for using PAC files with different forwarding methods:
- [Tunnel](#tunnel)
- [Tunnel with Local Proxy](#tunnel-with-local-proxy)
- [Enforce Proxy](#enforce-proxy)
[]To configure the following PAC files with **Tunnel** mode:
- [Forwarding Profile PAC File](#tunnel-forwarding-profile)
- [App Profile PAC File](#tunnel-app-profile)
[]In **Tunnel** mode, you must only use the Forwarding Profile PAC file to bypass traffic away from Zscaler Client Connector or to tunnel traffic to Zscaler Client Connector. Do not use it to tunnel traffic to the Zscaler cloud.
In **Tunnel** mode, a Forwarding Profile PAC file is commonly used to get web traffic on nonstandard ports. For example:
if ( shExpMatch(url,"*:8080") ||
shExpMatch(url,"*:8081"))
return "PROXY ${ZAPP_LOCAL_PROXY}";
else
return "DIRECT";
If you choose **Tunnel** mode when configuring the Forwarding Profile, select **Apply on Network Change** or **Never **for the **Proxy Action Type**.
- When you select **Apply on Network Change**, Zscaler Client Connector** **applies proxy settings when the network changes once and does not enforce them.
- When you select **Never**, Zscaler Client Connector does not apply any PAC file configurations to the system.
In an IPv6 environment, IPv6 bypasses are required for Private Applications apps in the App Profile PAC file when the Forwarding PAC is configured to send traffic to the Zscaler Client Connector listener.
Routes and filters are used to direct browser, system, or application traffic to Zscaler Client Connector. Zscaler Client Connector intercepts any traffic heading to port 80 and port 443.
[]In **Tunnel** mode, the App Profile PAC file directs traffic that Zscaler Client Connector received to the Zscaler cloud. Using the PAC file, Zscaler Client Connector chooses the data center and tunnels the traffic to it with the Connect Tunnel method. If the PAC file contains exceptions for traffic, Zscaler Client Connector sends that traffic directly to the destination server.
When using the App Profile PAC file for **Tunnel** mode, you must:
- Configure exceptions in the PAC file for traffic that needs to be bypassed.
- Keep the PAC file as simple as possible.
The following is an example of App Profile PAC file for **Tunnel** mode:
[TunnelMode_App_Profile_PAC_Example.pac](/downloads/zia/TunnelMode_App_Profile_PAC_Example.pac)
[]To configure the following PAC files with **Tunnel with Local Proxy** mode:
- [Forwarding Profile PAC File](#twlp-forwarding-profile)
- [App Profile PAC File](#twlp-app-profile)
[]In **Tunnel with Local Proxy** mode, the Forwarding Profile PAC file is responsible for directing system, browser, and application traffic to Zscaler Client Connector.
When using the Forwarding Profile PAC file for **Tunnel with Local Proxy** mode, you must:
- Use this PAC file for configuring exceptions. Configuring an exception in the PAC file allows you to bypass traffic so that it does not reach Zscaler Client Connector.
- Ensure that the proxy return statement has the following macro:
return "PROXY ${ZAPP_LOCAL_PROXY}";
When Zscaler Client Connector downloads this PAC file, it replaces the macro with a loopback IP address and the port that Zscaler Client Connector is listening to. Then Zscaler Client Connector applies this PAC file to the system, browser, and applications.
If traffic does not follow the Forwarding Profile PAC file, it does not reach Zscaler Client Connector and the Zscaler cloud. Instead, the traffic is sent directly.
In an IPv6 environment, IPv6 bypasses are required for Private Applications apps in the App Profile PAC file when the Forwarding PAC is configured to send traffic to the Zscaler Client Connector listener.
The following is an example of a Forwarding Profile PAC file for **Tunnel with Local Proxy** mode:
[LPMode_Fwding_Profile_PAC_Example.pac](/downloads/zia/LPMode_Fwding_Profile_PAC_Example.pac)
[]In **Tunnel with Local Proxy **mode, the App Profile directs traffic (that Zscaler Client Connector received) to the Zscaler cloud. Zscaler Client Connector directs traffic to the closest data center according to the App Profile PAC file by changing the proxy return statement to the geographically closest data center IP address.
When using the App Profile PAC for **Tunnel with Local Proxy** mode, you must keep the PAC file as simple as possible.
The following is an example of App Profile PAC file for **Tunnel with Local Proxy** mode:
[LPMode_App_Profile_PAC_Example.pac](/downloads/zia/LPMode_App_Profile_PAC_Example.pac)
[]In **Enforce Proxy** mode, Zscaler Client Connector acts similarly to a GPO pushing a PAC file on the system. Zscaler Client Connector enforces the Forwarding Profile PAC file on your machine.