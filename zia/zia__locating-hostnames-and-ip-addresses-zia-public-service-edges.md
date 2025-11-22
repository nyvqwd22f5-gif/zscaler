# Locating the Hostnames and IP Addresses for ZIA Public Service Edges
Source: https://help.zscaler.com/zia/locating-hostnames-and-ip-addresses-zia-public-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1399016.pdf

To locate the hostnames and IP addresses of the ZIA Public Service Edges for your IPSec VPN tunnels:
- Go to config.zscaler.com/<Zscaler Cloud Name>/cenr.
You can find the name of your cloud in the URL your admins use to log into the Zscaler service. For example, if an organization logs into admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net.** **So, you should go to config.zscaler.com/zscalertwo.net/cenr. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- Go to **Cloud Enforcement Node Ranges**.
- Under** VPN Host Name**, find the two data centers closest to the organization's location. Choose one as the destination for your primary IPSec VPN tunnel and the other as the destination for your backup IPSec VPN tunnel.
For example, if you're located in London, scroll to the **EMEA** section of the table to find lon3-vpn.zscalertwo.net (London) as your primary destination and amsterdam2-vpn.zscalertwo.net** **(Amsterdam) as your backup destination.
[See image.](#seeimage1)
- If you need the IP addresses of the ZIA Public Service Edges, resolve the hostnames of your primary and backup destinations.
[]**![Screenshot of the Amsterdam and London III VPN hostnames. ](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/ipsec/knowledge-base/locating-the-hostnames-and-ip-addresses-your-zens/amsterdam_and_london_iii_vpn_hostnames.png?1601385702)
**