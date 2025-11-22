# Locating the Virtual IP Addresses for Internet & SaaS Public Service Edges
Source: https://help.zscaler.com/unified/locating-virtual-ip-addresses-internet-saas-public-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1495351.pdf

To locate the Virtual IP (VIP) addresses of the Internet & SaaS Public Service Edges for your GRE tunnels:
-
Go to config.zscaler.com/<Zscaler Cloud Name>/cenr.
You can find the name of your cloud in the URL your admins use to log in to the Zscaler service. For example, if an organization logs into admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net.** **So, you should go to config.zscaler.com/zscalertwo.net/cenr.
- Go to **Cloud Enforcement Node Ranges**.
-
Under **GRE Virtual IP**, find the VIPs of the two data centers closest to the organization's location. Choose one as the destination for your primary GRE tunnel and the other as the destination for your backup GRE tunnel.
For example, if you're located in London, scroll to the **EMEA** section of the table to find 165.225.80.34 (London) as your primary VIP and 185.46.212.34 (Amsterdam) as your secondary VIP.