# About Tunnel Information in the Cloud Path
Source: https://help.zscaler.com/unified/about-tunnel-information-cloud-path
PDF: https://help.zscaler.com/pdf/com/en/1495081.pdf

In the Cloud Path section in the Users Dashboard, you can view the flow of traffic through the applicable tunnels as per the configured policies.
Tunnel Types
Tunnels in Digital Experience Monitoring are of two types:
- The client connects to the Internet & SaaS Public Service Edge using Z-Tunnel 1.0 or Z-Tunnel 2.0. To learn more, see [About Z-Tunnel 1.0 and Z-Tunnel 2.0](/unified/about-z-tunnel-1-0-z-tunnel-2-0).
- The client connects using a location tunnel such as GRE or IPSec. To learn more, see [Understanding Generic Routing Encapsulation (GRE)](/unified/understanding-generic-routing-encapsulation-gre).
The tunnels that you can see in the Cloud Path section are:
- GRE Tunnel
- IPSec Tunnel
- Z-Tunnel 1.0
- Z-Tunnel 1.0 over IPSec
- Z-Tunnel 1.0 over GRE
- Z-Tunnel 2.0
- Z-Tunnel 2.0 over GRE
- Z-Tunnel 2.0 over IPSec
- Direct Request: This bypasses the tunnel and goes directly. In this case, no tunnel graphic will be displayed in the GUI.
![Tunnel Information in Cloud Path ](/downloads/zdx/analytics/tunnel-information-cloud-path/ZDX_TunnelInfo.png)