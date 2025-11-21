# Forwarding Traffic Based on User's Location Using PAC Files
Source: https://help.zscaler.com/zia/forward-traffic-based-on-users-location
PDF: https://help.zscaler.com/pdf/com/en/1398651.pdf

You can [use PAC files to forward your traffic to the Zscaler service](/zia/how-do-i-use-default-pac-files-forward-traffic-zia). When the Zscaler service receives traffic, it checks whether the traffic is from a known location (a location that is configured in the ZIA Admin Portal), or from an unknown location (remote user traffic). Typically, traffic from a known location is sent to port 80, where the service performs SSL inspection according to the location's policies, and remote user traffic is forwarded to port 9443, where the service always performs SSL inspection.
The exemption of URL and URL categories is applicable only for traffic generated from known locations and not for remote user traffic.
If your users work from your corporate office and work remotely, you might want to add an argument to the PAC file so that the browser forwards your traffic to a different port on the ZIA Public Service Edge , depending on the user's location.
- [Using Fixed Gateway IP Addresses](#fixedgatewayipadd)
- [Using Device IP Addresses](#deviceipadd)
- [Using DNS](#usingdns)
To learn more about writing PAC files, including guidelines, see [Best Practices for Writing PAC Files](/zia/best-practices-writing-pac-files) and [Writing a PAC File](/zia/writing-pac-file).
Zscaler recommends creating a copy of the default PAC file and customizing it, as necessary.
[]If each of your locations has a fixed gateway IP address, you can write an argument in the PAC file stating that if the PAC file receives traffic from the fixed IP addresses, the browser forwards that traffic to port 80. Otherwise, the PAC file forwards traffic to port 9443.
This option is accurate and independent from your computer configuration. However, you must update the list of gateway IP addresses in the PAC file when there are changes to your locations.
To use this option, replace the IP addresses in the following lines with your own gateway IP addresses. Then add the lines to the PAC file you are using:
/*Creating an array which will contain all known gateway IP */
var allGateways= [
"192.0.2.0/24",
"198.51.100.0/24",
"203.0.113.0/24"
];
if (allGateways.indexOf("${SRCIP}")>=0)
return "PROXY ${GATEWAY}:80; PROXY ${SECONDARY_GATEWAY}:80; DIRECT";
else
return "PROXY ${GATEWAY}:9443; PROXY ${SECONDARY_GATEWAY}:9443";
[]Every device that connects to the internet has an IP address. You can write an argument in the PAC file stating that if the IP address of a user's device falls within your corporate subnetwork, the browser forwards traffic to port 80. Traffic from IP addresses that are not in the subnetwork is forwarded to port 9443.
This option is simple and quick to execute, as it only relies on your computer configuration. However, your private IP address range may overlap with other company networks, such as a Wi-Fi hotspot at a coffee shop.
In this example, the subnetworks are **10.10.1.0/24**, **172.16.1.0/24**, and **192.168.1.0/24**. To use this option, replace the subnetworks in the following lines with your own. Then add the lines to the PAC file you are using:
/* If client IP falls in corporate subnet send traffic on regular port 80 */
if (
isInNet(myIpAddress(), "10.10.1.0", "255.255.255.0")||
isInNet(myIpAddress(), "172.16.1.0", "255.255.255.0")||
isInNet(myIpAddress(), "192.168.1.0", "255.255.255.0")||
)
return "PROXY ${GATEWAY}:80; PROXY ${SECONDARY_GATEWAY}:80; DIRECT";
else
return "PROXY ${GATEWAY}:9443; PROXY ${SECONDARY_GATEWAY}:9443;
[]You can determine the location of a user by referencing an internal DNS server. You can write an argument in the PAC file stating that if an IP address was resolved by an internal DNS server, the browser forwards traffic to port 80. Traffic from IP addresses that were not resolved by an internal DNS server is sent to port 9443.
This option is efficient and works as long as your DNS resolution is the same across all of your company locations. However, it may slow down browsing to the internet if your DNS servers do not respond quickly enough.
This method of identifying the user location does not work if the remote user is connected to a VPN and if the hostname is resolved using the internal DNS server over the VPN.
In this example, the internal DNS server is **DNS.safemarch.com**. To use this option, replace the internal DNS server in the following lines with your own. Then add the lines to the PAC file you are using:
/*Creating a variable hostIP and populating it with the IP address obtained by resolving DNS.safemarch.com*/
var hostIP= dnsResolve("DNS.safemarch.com");
/* If the value of the variable hostIP is not equal to 10.35.3.43 i.e. internal server, send traffic through Zscaler on port 9443 which would enforce SSL scanning else send traffic on regular port 80 */
if (hostIP !== "10.35.3.43")
return "PROXY ${GATEWAY}:9443; PROXY ${SECONDARY_GATEWAY}:9443; DIRECT";
else
return "PROXY ${GATEWAY}:80; PROXY ${SECONDARY_GATEWAY}:80; DIRECT";