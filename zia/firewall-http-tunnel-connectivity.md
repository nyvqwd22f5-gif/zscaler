# Firewall HTTP Tunnel Connectivity
Source: https://help.zscaler.com/zia/firewall-http-tunnel-connectivity
PDF: https://help.zscaler.com/pdf/com/en/1401616.pdf

Zscaler recommends using GRE/IPSec tunnel connectivity from branch or headquarter location gateway devices. For remote users, the recommendation is to install Zscaler Client Connector to connect to the Zscaler service. Zscaler Client Connector should be implemented when users are off network using HTTP CONNECT tunnels to forward their traffic.
With HTTP CONNECT tunnels, there are two 5-tuples associated with the traffic: the outer IP and the inner IP address. Zscaler removes the HTTP CONNECT request from the outer tunnel and then applies the firewall policies to the request inside the HTTP CONNECT tunnel independently. This means that any 5-tuple that results in a blocking policy blocks the corresponding session.
To ensure your organization is configured to allow connectivity to the Zscaler service, you must leverage the following predefined Zscaler network services and IP groups to your organization’s policies:
- A predefined network service: Zscaler Proxy Network Service - This includes all proxied network services (e.g., TCP 21, 80, 443, 9400, 9480, etc.) and the subscription to a DPPC port.
- A predefined IP category: Zscaler Proxy IPs - It includes all ZIA Public Service Edge service IPs in a particular cloud, local IPs of the particular ZIA Public Service Edge, and global service IPs.
- A predefined Firewall policy rule: Zscaler Proxy Traffic - This is available to match the Zscaler Proxy IPs category and the Zscaler Proxy Networking Service.
Zscaler Client Connector version 2.0 or later uses DTLS/TLS tunnels to forward traffic, and it doesn't support Zscaler Proxy Traffic rule.