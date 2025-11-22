# ZIA & Application Layer Gateway Enabled Applications
Source: https://help.zscaler.com/zia/zia-and-application-layer-gateway-enabled-applications
PDF: https://help.zscaler.com/pdf/com/en/1400876.pdf

The best practice for customers using forwarding methods such as IPSec, GRE, or Zscaler Tunnel (Z-Tunnel) 2.0 (for remote users) is generally to send all ports and protocols through their tunnels. However, there are some protocols that currently cannot be fully handled by ZIA Public Service Edges. These protocols require an application layer gateway (ALG) feature in order to be state fully tracked across control and bearer channels.
About ALG
Some protocols use separate data and control channels for transmission. The control channel can contain information about ephemeral TCP/UDP ports used by the data channel and information about client or server IP addresses. In general, the ALG allows the network device to check the application payload in order to convert the network layer address information. It also allows for synchronization between multiple streams or sessions of data between two hosts exchanging data. Additionally, it recognizes application-specific commands and offers granular security controls over them.
To learn more about ALGs, refer to [RFC 2694 DNS Extensions to Network Address Translators (DNS_ALG)](https://tools.ietf.org/html/rfc2694).
Zscaler service and Traffic Requiring the ALG Feature
The Zscaler service supports and applies the ALG feature automatically to the following protocols:
- FTP (passive)
- PPTP
- RTSP
Traffic forwarded to the protocols that are not fully supported by an ALG (like SIP, H.323, H.248, VOIP, and TFTP) might need to be bypassed from Zscaler by changing the configuration when setting up your forwarding methods such as IPSec, GRE, or Z-Tunnel 2.0 (for remote users).