# Adding DNS Gateways
Source: https://help.zscaler.com/zia/adding-dns-gateways
PDF: https://help.zscaler.com/pdf/com/en/1451571.pdf

In the ZIA Admin Portal, you can configure a list of DNS Gateways with primary and secondary DNS services offered by your third-party DNS providers. By using DNS Gateways, you can also control the protocols over which DNS traffic can reach the configured services.
A maximum of 254 DNS Gateways are supported for an organization. To learn more, see [Ranges & Limitations](/zia/ranges-limitations).
To add a DNS Gateway:
- Go to **Administration** > **Proxies & Gateways** > **DNS Gateways**.
- Click **Add DNS Gateway**.
-
The **Add DNS Gateway** window appears.
In the **Add DNS Gateway** window:
- **Name**: Enter a unique name for the DNS Gateway. Only alphanumeric characters are allowed and the name cannot exceed 255 characters.
- **Protocol**: Select the protocols that must be used to connect to the DNS service. You can select from DNS over HTTP (DoH), UDP, and TCP.
-
**Primary DNS Server**: Enter the IP address or the Fully Qualified Domain Name (FQDN) of the primary DNS service provided by your third-party DNS service provider.
For DoH queries (i.e., when DoH is selected as the protocol), a customized URL path is additionally supported with the FQDN and IP address of the DNS server. When a custom path is specified, the `dns-query` string must be explicitly appended to the URL path. For example, `doh.dnsserver.com/path/to/destination/dns-query` or `192.0.2.1/path/to/destination/dns-query`.
Depending on the protocols selected for the gateway, the following fields appear and you can optionally fill out the port information:
- **UDP Port**: Specify the port number for UDP if the primary DNS service uses a non-default port. The default port is 53.
- **TCP Port**: Specify the port number for TCP if the primary DNS service uses a non-default port. The default port is 53.
- **DoH Port**: Specify the DNS over HTTPS (DoH) port in the primary DNS service. The default port is 443.
-
**Secondary DNS Server**: (Optional) Enter the IP address or the Fully Qualified Domain Name (FQDN) of the secondary DNS service provided by your third-party DNS service provider. Although a secondary DNS service is optional, configuring it ensures the high availability of the DNS service if the primary DNS service fails.
For DoH queries (i.e., when DoH is selected as the protocol), a customized URL path is additionally supported with the FQDN and IP address of the DNS server. When a custom path is specified, the `dns-query` string must be explicitly appended to the URL path. For example, `doh.dnsserver.com/path/to/destination/dns-query` or `192.0.2.1/path/to/destination/dns-query`.
Depending on the protocols selected for the gateway, the following fields appear and you can optionally fill out the port information:
- **UDP Port**: Specify the port number for UDP if the secondary DNS service uses a non-default port. The default port is 53.
- **TCP Port**: Specify the port number for TCP if the secondary DNS service uses a non-default port. The default port is 53.
- **DoH Port**: Specify the port number for DNS over HTTPS if the secondary DNS service uses a non-default port. The default port is 443.
- []**Failure Behavior**: Select an action that must be performed if the configured DNS service is unavailable or unhealthy:
- **Return Error Response**: Return an appropriate error code (SERVFAIL) to the client. If only the primary DNS service is configured, then the error code is sent if the primary DNS service fails. If both primary and secondary DNS services are configured, the error code is sent if both services are unavailable to serve the requests. To learn more, see [DNS Insights Logs: Columns](/zia/dns-insights-logs-columns).
- **Allow and Ignore DNAT Rules**: The DNS request is sent to the originally requested DNS resolver (not specified in the DNS Gateway) using the same protocol as the original user request without applying any DNAT rules configured.
-
**Redirect to Zscaler Trusted Resolver**: Send the DNS requests to Zscaler Trusted DNS Resolver.
- The Zscaler Trusted DNS Resolver can be reached over TCP or UDP, so this failure behavior appears in the drop-down menu only when these protocols are selected. This option is not available when the DoH protocol is selected.
- While this configuration allows you to forward your DNS traffic to Zscaler Trusted DNS Resolver as failover behavior, you can also resolve all your DNS traffic using Zscaler Trusted DNS Resolver. [See the supported mechanisms.](#forward-DNS-traffic-to-ZTR)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[See image.](#add-dns-gateway-window)
The following image shows the gateway configuration when the failure behavior is selected as Redirect to Zscaler Trusted Resolver.
[See image.](#dns-gateway-forward-to-ZTR)
A custom URL path in the FQDN or IP address of DNS servers is supported only for DoH queries.
- The length of the custom path (including the `dns-query` string) cannot exceed 1,024 characters.
- The JSON API for DoH queries `https://doh.dnsserver.com/path/to/destination/resolve?` is not supported.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations). The custom path is not applicable to TCP and UDP queries and cannot be specified while either of these protocols is selected. However, if you are selecting all three protocols and including a custom path, the custom path would still only apply to DoH queries.
- []To forward your standard DNS traffic (destination port: 53), you can use the predefined Zscaler Trusted DNS Resolver NAT Control rule. To learn more, see [About NAT Control](/zia/about-nat-control).
- To forward your DoH traffic, you can configure a DNS filtering rule with a matching rule criteria, select an appropriate rule action, and associate the default Zscaler Trusted DNS Resolver gateway. To learn more, see [About DNS Gateways](/zia/about-dns-gateways).
[]![A screenshot of the Add DNS Gateway window](/downloads/zia/documentation-knowledgebase/policies/firewall/firewall-policy-resources/adding-dns-gateways/add-dns-gateway.png)
[]![DNS gateway with failure behavior to forward to Zscaler Trusted Resolver](/downloads/zia/policies/firewall/firewall-policy-resources/adding-dns-gateways/DNS-gateway-failure-behavior-forward-to-ZTR.png)