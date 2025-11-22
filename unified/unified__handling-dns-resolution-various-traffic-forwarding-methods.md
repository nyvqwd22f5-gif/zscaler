# Handling DNS Resolution for Various Traffic Forwarding Methods
Source: https://help.zscaler.com/unified/handling-dns-resolution-various-traffic-forwarding-methods
PDF: https://help.zscaler.com/pdf/com/en/1495221.pdf

The following table provides information on how Zscaler handles DNS resolution for various traffic forwarding methods:
-
-
[](/unified/configuring-zscaler-client-connector-app-profiles)
| Traffic Forwarding Method | DNS Resolution Handling |
| ------------------------- | ----------------------- |
| Explicit Proxy (PAC forwarded traffic) | Zscaler performs DNS resolution for the proxied traffic. However, for the traffic that is exempted based on the PAC file, the DNS resolution is performed locally at the client side. |
| Transparent Proxy (GRE and IPSec traffic) | Zscaler performs DNS resolution only if the server is configured on the client side and if it is one of the following:A public DNS server, such as Cloudflare, Infoblox, or OpenDNS, etc.A private DNS server hosted on the internet, such as AWS or AzureIf not, the DNS resolution is performed locally at the client side before forwarding the traffic to Zscaler. |
| All traffic forwarded to Zscaler through any port or protocol | Zscaler performs the DNS resolution for the clients. Zscaler might use DNS servers running within the data centers or use a third-party DNS service for DNS resolution. |
| Zscaler Client Connector traffic in tunnel mode with local proxy | Zscaler performs DNS resolution for the proxied traffic. However, for the traffic that is exempted based on the App Profile's PAC file or Forwarding Profile's PAC file, the DNS resolution is performed locally at the client side. |
| Zscaler Client Connector traffic in tunnel mode | A DNS resolution is first performed locally at the client side for all the traffic. Then, Zscaler performs a second DNS resolution for the proxied traffic. However, for the traffic that is exempted based on the App Profile's PAC file or based on VPN gateway bypasses, the result of the initial client side DNS resolution is used. |
| Zscaler Client Connector traffic in Z-Tunnel 2.0 mode | If a public DNS (i.e., DNS server in Destination Include Range) is used, Zscaler performs the DNS resolution for the clients. Then the traffic is either proxied or bypassed based on the Destination Include/Exclude Range, Z-Tunnel 2.0 Domain-Based bypass configurations, or based on VPN gateway bypasses.If a local DNS (i.e., DNS server in Destination Exclude Range) is used, the DNS resolution is performed locally at the client side. Then the traffic is either proxied or bypassed based on the Destination Include/Exclude Range, Z-Tunnel 2.0 Domain-Based bypass configurations, or based on VPN gateway bypasses. For the proxied traffic, Zscaler has an option to redo the DNS resolution.To learn more about domain inclusion and exclusion for DNS requests, see the DNS section for your platform in Configuring Zscaler Client Connector App Profiles. |