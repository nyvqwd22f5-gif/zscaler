# Configuring Network Segments
Source: https://help.zscaler.com/unified/configuring-network-segments
PDF: https://help.zscaler.com/pdf/com/en/1532361.pdf

Within the Admin Portal, you can create [Network segments](/unified/about-network-segments). For a complete list of ranges and limits, see [Ranges & Limitations](/unified/ranges-limitations).
To add a new Network segment:
- Go to **Infrastructure **>** Private Access > Component **>** VPN (For Legacy Apps **>** Network Segments**.
- Click **Add Network Segment**.
The** Add Network Segment** drawer appears.
- In the **Add Network Segment** drawer:
- **Name**: Enter the name for the Network segment.
- **Description**: (Optional) Enter a description for the Network segment.
- **LAN IP Address**: Enter the IP subnet that you want to associate with this Network segment.
- **FQDN**: Enter an FQDN to associate with this Network segment. This option appears if you select the **FQDN** option under **Users Access Application by**.
- **DNS Server**: Enter a DNS server. This option appears if you select the **FQDN** option under **Users Access Application by**.
- **Network Connector Group**: Select the Network Connector group you want to assign this Network segment to.
![Create a Network segment on the Network Segment page](/downloads/zpa/configuring-vpn-segments/zpa-vpn-add-network-segments_0.png)
- Click **Save**.