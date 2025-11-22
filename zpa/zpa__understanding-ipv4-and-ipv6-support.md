# Understanding IPv4 and IPv6 Support
Source: https://help.zscaler.com/zpa/understanding-ipv4-and-ipv6-support
PDF: https://help.zscaler.com/pdf/com/en/1485421.pdf

Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6) are Internet Protocols (IPs) used to route traffic between systems on a network. Zscaler Private Access (ZPA) supports IPv4 for TCP-, UDP-, and ICMP-based connections, and supports IPv6 for only TCP-based applications.
[App Connectors](/zpa/about-connectors) and [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges) are dual stack aware, meaning IPv4 and IPv6 run simultaneously alongside each other.
The following IP use cases are supported for ZPA:
- [IPv4 Endpoint Accessing an IPv4 Application](#Ipv4toIpv4app)
- [IPv4 or IPv6 Endpoint Accessing an IPv6 Application](#Ipv4orIpv6toIpv6app)
- [IPv6 Endpoint Accessing an IPv4 Application](#Ipv6toIpv4app)
[]An IPv4 endpoint through Zscaler Client Connector to access an IPv4 application on a server is supported for TCP-, UDP-, and ICMP-based connections.
[]An IPv4 or an IPv6 endpoint through Zscaler Client Connector to access an IPv6 application on the server is partially supported. Only TCP-based connections are supported for direct IPv6 communications from an App Connector to a server. UDP-based connections are not supported. Users can access IPv6 applications defined using a FQDN or hostname if they are using browser-based connections or Zscaler Client Connector.
[]An IPv6 endpoint through Zscaler Client Connector to access an IPv4 application on the server is supported for TCP-, UDP-, and ICMP-based connections.