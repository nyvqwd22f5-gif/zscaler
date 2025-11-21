# Locating the Virtual IP Addresses for ZIA Public Service Edges
Source: https://help.zscaler.com/zia/locating-virtual-ip-addresses-your-zia-public-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1400351.pdf

To locate the Virtual IP (VIP) addresses of the ZIA Public Service Edges for your GRE tunnels:
- Go to config.zscaler.com/<Zscaler Cloud Name>/cenr.
You can find the name of your cloud in the URL your admins use to log into the Zscaler service. For example, if an organization logs into admin.zscalertwo.net, then that organization's cloud name is zscalertwo.net.** **So, you should go to config.zscaler.com/zscalertwo.net/cenr. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
- Go to **Cloud Enforcement Node Ranges**.
- Under **GRE Virtual IP**, find the VIPs of the two data centers closest to the organization's location. Choose one as the destination for your primary GRE tunnel and the other as the destination for your backup GRE tunnel.
For example, if you're located in London, scroll to the **EMEA** section of the table to find 165.225.80.34 (London) as your primary VIP and 185.46.212.34 (Amsterdam) as your secondary VIP.
[See image.](#grevirtualip)
[]**![GRE Virtual IP.png](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/generic-routing-encapsulation-gre/gre-configuration-guide/locating-virtual-ip-addresses-your-zens/fivinjf2jrv7_aunxi30orjfjcfc6cxwaxdxltb5nd0bmaa3xitumcrjk43-vvio-0c5rnckm-y3fobecoaoy9mjuikrvk1giy0qnnnpkvatplmpkaffhmeqeogokq-fvlaj5iot.png)
**