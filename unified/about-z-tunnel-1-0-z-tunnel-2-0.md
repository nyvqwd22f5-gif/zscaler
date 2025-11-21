# About Z-Tunnel 1.0 & Z-Tunnel 2.0
Source: https://help.zscaler.com/unified/about-z-tunnel-1-0-z-tunnel-2-0
PDF: https://help.zscaler.com/pdf/com/en/1495021.pdf

The Zscaler service uses a lightweight, HTTP tunnel called the Zscaler Tunnel (Z-Tunnel) to forward traffic to the Internet & SaaS Public Service Edges. When a user connects to the web, Zscaler Client Connector establishes the Z-Tunnel to the closest Internet & SaaS Public Service Edge, and forwards the web traffic through the tunnel so that the Internet & SaaS Public Service Edge can apply the appropriate security and access policies. Zscaler offers two versions of the Z-Tunnel.
To learn how to migrate from Z-Tunnel 1.0 to Z-Tunnel 2.0, see [Migrating from Z-Tunnel 1.0 to Z-Tunnel 2.0](/unified/migrating-z-tunnel-1-0-z-tunnel-2-0).
Z-Tunnel 1.0
Z-Tunnel 1.0 forwards traffic to the Zscaler cloud via CONNECT requests, much like a traditional proxy. Version 1.0 sends all proxy-aware traffic or port 80/443 traffic to the Zscaler service, depending on the forwarding profile configuration.
To use Z-Tunnel 1.0, select Z-Tunnel 1.0 when [configuring a forwarding profile](/unified/configuring-forwarding-profiles-zscaler-client-connector) with **Tunnel** mode and the packet filter driver is enabled.[]
Z-Tunnel 2.0
For Z-Tunnel 2.0, use a NAT device that uses a single IP for all connections from a single device. Otherwise, you’ll encounter load-balancing issues where control and data connections land on different Zscaler SME servers, and Z-Tunnel 2.0 fails to establish and falls back to Z-Tunnel 1.0.
Z-Tunnel 2.0 has a tunneling architecture that uses DTLS or TLS to send packets to the Zscaler service. Because of this, Z-Tunnel 2.0 is capable of sending all ports and protocols.
To use Z-Tunnel 2.0:
- Deploy Zscaler Client Connector 2.0.1 (and later) to your users.
- Select **Z-Tunnel 2.0 **when [configuring a forwarding profile](/unified/configuring-forwarding-profiles-zscaler-client-connector) with **Tunnel** mode and the packet filter driver is enabled.
- Configure bypasses for** Z-Tunnel 2.0** in the [Zscaler Client Connector app profile](/unified/configuring-zscaler-client-connector-app-profiles). To learn more, see [Best Practices for Adding Bypasses for Z-Tunnel 2.0](/unified/best-practices-adding-bypasses-z-tunnel-2-0).
To learn more about deploying Z-Tunnel 2.0, see [Best Practices for Deploying Z-Tunnel 2.0](/unified/best-practices-deploying-z-tunnel-2-0).