# Understanding Proxy Mode
Source: https://help.zscaler.com/unified/understanding-proxy-mode
PDF: https://help.zscaler.com/pdf/com/en/1495276.pdf

You can use Explicit proxy mode or Transparent proxy mode to forward your traffic to the Zscaler service.
Explicit Mode
[]In explicit mode, a browser is configured to send its traffic directly to an Internet & SaaS Public Service Edge. The user either manually configures the browser’s settings or configures the browser to use a PAC file to send traffic to a Service Edge. When the browser sends an HTTPS request, it inserts the Service Edge IP address as the destination IP address in the IP header and sends the HTTP CONNECT method request directly to the Service Edge, before it initiates the SSL handshake.
The CONNECT request includes the requested domain, as shown in the following command, allowing the Zscaler service to immediately identify the destination host.
HTTP      270 CONNECT mail.google.com:443 HTTP/1.1
Transparent Mode
[]In transparent mode, the browser is not configured to send traffic to a Service Edge. Instead, the traffic is directed to a Service Edge through some other means, such as a GRE or IPSec tunnel configured at your organization’s router. In this case, the destination IP address in the IP header of the request contains the IP address of the destination server. The entire HTTP message is encrypted, including the headers, the request load, and the response load. The actual hostname and domain name being accessed are not visible.
The Service Edge identifies the destination host in one of the following ways:
- Using the Server Name Indication (SNI) extension if the initial HTTPS request (client hello) includes SNI, which is an extension to the TLS protocol. The SNI includes the requested hostname.
[See image.](#Image)
Most browsers use SNI when a server uses a common certificate for multiple sites. For example, Service Edge might use SNI to apply a policy to block traffic to drive.google.com, but allow traffic to mail.google.com and google.com. All sites use a common *.google.com certificate.
- Using the server certificate sent by the destination server during the SSL handshake, if the HTTPS request does not include the SNI extension.
[][![Screenshot of an HTTPS request that includes the Server Name Indication extension for transparent mode](/downloads/zia/traffic-forwarding/understanding-proxy-mode/ZIA_understanding_proxy-mode_sni_extension_transparent_mode.png)
]