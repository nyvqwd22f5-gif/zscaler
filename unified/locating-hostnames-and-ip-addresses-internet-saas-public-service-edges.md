# Locating the Hostnames and IP Addresses for Internet & SaaS Public Service Edges
Source: https://help.zscaler.com/unified/locating-hostnames-and-ip-addresses-internet-saas-public-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1495426.pdf

To locate the hostnames and IP addresses of the Internet & SaaS Public Service Edges for your IPSec VPN tunnels:
- Go to config.zscaler.com/<Zscaler Cloud Name>/cenr.
You can find the name of your cloud in the URL your admins use to log in to the Zscaler service. For example, if an organization logs into admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net.** **So, you should go to config.zscaler.com/zscalertwo.net/cenr.
- Go to **Cloud Enforcement Node Ranges**.
- Under** VPN Host Name**, find the two data centers closest to the organization's location. Choose one as the destination for your primary IPSec VPN tunnel and the other as the destination for your backup IPSec VPN tunnel.
For example, if you're located in London, scroll to the **EMEA** section of the table to find lon3-vpn.zscalertwo.net (London) as your primary destination and amsterdam2-vpn.zscalertwo.net** **(Amsterdam) as your backup destination.
- If you need the IP addresses of the Internet & SaaS Public Service Edges, resolve the hostnames of your primary and backup destinations.