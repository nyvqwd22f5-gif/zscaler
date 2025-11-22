# Tunnel Insights Logs: Columns
Source: https://help.zscaler.com/cloud-branch-connector/tunnel-insights-logs-columns
PDF: https://help.zscaler.com/pdf/com/en/1420681.pdf

You can customize your tunnel logs using the columns. To learn more about logs, see [About Insights Logs](/cloud-branch-connector/about-insights-logs).
You can select the following Tunnel Insights Log columns to view:
- **Authentication Algorithm**: The authentication algorithm used for IPSec Phase 1 and Phase 2.
- **Authentication Type**: The method IPSec peers use to authenticate each other.
- **Bytes Received**: The total bytes of data Zscaler received through the tunnel from the organization in the one-minute sample interval.
- **Bytes Sent**: The total bytes of data Zscaler sent through the tunnel to the organization in the one-minute sample interval.
- **Cipher**: The ciphers used for the control and data channel of the tunnel.
- **Cipher Protocol**:The protocol that is used by the tunnel (i.e., TLS or DTLS).
- **Cloud Connector Instance**: The specific Zscaler software instance from which you want to view the DNS logs.
- **Data Center**: The data center associated with the tunnel.
- **Encryption Algorithm**: The encryption algorithm used to encrypt handshakes (IPSec Phase 1) and data (IPSec Phase 2).
- **Event Reason**: The reason that the status change occurred for a tunnel.
- **Event Time**: The date and time the event occurred.
- **IKE Phase 2 SPI**: The Security Parameter Index (SPI) for the IKE SA established in Phase 2.
- **Initiator Cookie**: The initiator's cookie value used during the IPSec IKE Phase 1 message exchange.
- **IPSec Protocol**: Protocols used in establishing the IPSec VPN tunnel.
- **Keep Alive Packets**: The Keep-Alive packet ensures that the SSL VPN connection remains open even when the device is inactive.
- **Life Bytes**: The total number of life bytes that is transmitted over an IPSec SA before it expires.
- **Location**: The location associated with the tunnel.
- **Log Time**: The date and time the event was logged.
- **Log Type**: The type of tunnel logs.
- **No.**: The item number.
- **P2 Policy Dest IP - End**: The end destination IP address specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Dest IP - Start**: The start destination IP address specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Dest Port - End**: The end destination port number specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Protocol**: The protocol specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Src IP - End**: The end source IP address specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Src IP - Start**: The start source IP address specified in the IPSec Phase 2 policy proposal.
- **P2 Policy Src Port - Star**t: The start source port number specified in the IPSec Phase 2 policy proposal.
- **Packets Received**: The total number of packets Zscaler received through the tunnel from the organization in the one-minute sample interval.
- **Packets Sent**: The total number of packets Zscaler sent through the tunnel to the organization in the one-minute sample interval.
- **Policy Direction**: The direction in which the IPSec Phase 2 policies (allowed subnets/ports/protocols) are proposed. The following directions appear under this column:
- Inbound: From the organization's IPSec gateway to Zscaler.
- Outbound: From Zscaler to the organization's IPSec gateway.
- **Responder Cookie**: The responder's cookie value used during the IPSec IKE Phase 1 message exchange.
- **Session ID**: A cryptographically generated random number that is unique per tunnel.
- **Source Port**: The port number of the tunnel from which the tunnel is initiated.
- **Tunnel Destination IP**: The destination IP address that the tunnel is destined to.
- **Tunnel Lifetime**: The time after an IKE expires for the IPSec VPN tunnel.
- **Tunnel Source IP**: The source IP address from which the tunnel is initiated.
- **Tunnel Status**: The status of the tunnel.
- **Tunnel Type**: The type of networking tunnel.
- **Vendor ID**: The vendor associated with the tunnel.